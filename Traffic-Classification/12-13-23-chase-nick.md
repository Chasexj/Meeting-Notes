# Project: LLM for router configuration

Previous Experiments: Can LLMs learn the structure/semantics of routing configuration language
Results: Yes, the masking and next-line prediction accuracies are both high.

## How much does this contribute to misconfiguration detection in routing configurations?
State-of-the-art solutions for misconfiguration detection in routing configurations (particularly in **access control lists** and **route-maps**):

Universal Assumption: Routing configurations should be relatively uniform across all routers belonging to the same network, thus rare events/outliers are most likely to be the root cause of misconfigurations if the assumption holds.

Derived methods:
1. *SelfStarter*: Iteratively parses routing configurations to derive metatemplates for routing configurations, any routing configurations that deviate from the metatemplate are flagged as potential misconfigurations. <img width="500" alt="Screenshot 2023-11-15 at 12 02 31 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/818bb650-d91b-4a7a-b9b5-0dc2af84982d" style="border: 2px solid black;"><img width="500" alt="Screenshot 2023-11-15 at 12 03 43 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/1f4c5609-b105-44ef-8472-5b8141bd8b30" style="border: 2px solid black;">

2. *Campion*: pair-wise comparison of routing configurations, finding the range of prefixes that have diverging configurations. <img width="500" alt="Screenshot 2023-11-15 at 12 07 28 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/dd01becf-d18d-45a8-a108-26474e68d7ba" style="border: 2px solid black;">

3. ,etc.

Conclusion: this may be a good enough way to detect misconfigurations if the assumption holds, given contexts where there exists no ground truth.

## Discussion: Is there a better application of LLM to assist routing configurations?
1. Translation from high-level instruction to explicit configuration changes (motivated by the recent rise in general code generation from GPT):
   
   e.g.,

   > 'Create a new IP prefix list NETS that matches all IPs from 10.9.0.0/16: 16-32, and deny all routes to these IPs'
   
   > 'ip prefix-list NETS permit 10.9.0.0/16 le 32; route-map POL deny 10; match ip address NETS'

   **Challenges**:
   
   *Automated Translation*: Developing a system that can accurately translate high-level, often abstract networking instructions into specific configuration commands for different types of network devices (like Cisco, Juniper, etc.).
   
   *Understanding Context*: Ensuring the system comprehends various networking contexts and applies the correct configuration logic accordingly. This is missing from a lot of existing intention-based configuration translation work: they localize the configuration generation without much reference to the rest of the configurations. Domain knowledge specifically: what are these contexts?

   *Cross-Vendor Compatibility*: Addressing the challenge of translating instructions into commands compatible with different vendors' devices, each with their unique syntax and capabilities.

   *Error Handling and Validation*: Implementing robust error handling and validation mechanisms to ensure that generated configurations are not only syntactically correct but also logically sound and safe to deploy. Reinforcement learning by validation using misconfiguration detection tools?

   **Applications**:
   
   *Efficiency in Network Management*: Reducing the time and effort required to configure network devices, thereby increasing operational efficiency.

   *Error Reduction*: Minimizing human error in network configuration, leading to more reliable network operations.

   *Educational Tool*: Assisting in teaching networking concepts by providing real-time examples of how high-level concepts translate into actual device configurations.

   *Misconfiguration Checking*: Given comments in the configuration file, automated verification against intended changes.

   **Recent Methods**:
   <img width="500" alt="Screenshot 2023-11-15 at 1 03 25 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/dae9dc95-bff3-4ae3-a50c-d848543f12e6">
   *Ambiguity in Natural Language*: The inherent ambiguity of natural language poses significant challenges in accurately interpreting the operator's intent. Although Lumi contains a feedback module this still requires extensive operator-module interactions. Advanced language models like GPT, with their deep understanding of context and semantics, could better handle such ambiguities, leading to more accurate interpretation of intents with fewer operator interactions. *Complexity in Handling Multi-Step Interactions (similar to Ambiguity in Natural Language)*: LUMI's system architecture involves multiple steps like information extraction, intent assembly, and confirmation. A more integrated approach using GPT could streamline these processes, making the system more efficient and user-friendly.

   *Limited Flexibility in Entity Recognition*: LUMI relies on a hierarchical set of entities for information extraction, which may not cover all possible network-related concepts or terms. More importantly, these entities need to be predefined and manually configured. GPT models, with their extensive training on diverse datasets, could potentially recognize a broader range of entities and concepts in an automated fashion through embeddings, offering greater flexibility and accuracy. *Handling of Complex and Varied Expressions (similar to Limited Flexibility in Entity Recognition)*: The system's ability to handle complex and varied natural language expressions may be limited. GPT models, with their advanced language understanding capabilities, could potentially interpret a wider range of expressions and nuances in language more effectively.

   *Dependency on Extensive Training Data*: LUMI's effectiveness depends on the availability of extensive training data for its NER (Named Entity Recognition) module. In contrast, GPT models, pre-trained on vast corpora, require less domain-specific training data to achieve high levels of understanding and accuracy.

   Limited Learning Capabilities from User Feedback: While LUMI learns from operator-provided feedback, its learning mechanism is relatively basic (revised instructions add new key-item pair and retrain NER from scratch). Advanced language models like GPT can incorporate more sophisticated learning algorithms (fine-tuned, contextual understanding, continual learning, etc.), potentially leading to quicker adaptation and improvement based on user interactions.
   
3. Configuration translation between routing vendors:
   
   e.g.,<img width="500" alt="Screenshot 2023-11-15 at 12 19 37 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/b8f63a60-8fc2-4daa-b63b-bbc3ed2f4aa8">

## Target Task: Automated New Neighbor BGP Routing Configuration via LLM

**Two issues with STOA methods**:

*Automation/Editing Tools (1): Ansible, Puppet, Junos...*:
1. Both manual configuration and templates still require an operator to go in there and fill in the configurations or change the variables, which requires an understanding of the context of the configurations which is time-consuming and error-prone.
2. Generalizability, different vendors need different templates/tools/syntax, whereas an LLM can learn this automatically without extensive domain knowledge.
   
*Semi-Generative/Satisfaction-Problem-Oriented Tools (2): CPR, NetComplete, Snowcap, Aura...*:
1. Still need formal specifications of configurations/policies, then have a hand-written formal model (boolean equations, satisfiability problem) that translates from highly-level policies to low-level configurations.
2. A bit better generalizability, but need a model to encapsulate the semantics of the language.

*What we are implementing*:
1. Fine-tuned an LLM model to a specific network in a Markchov-chained manner. Example training scenario: (1) Router Identifier + New Neighbor IP/Description -> Group Assignment, Import/Export policies; (2) Router Identifier + New Neighbor IP/Description + Group Assignment + Import/Export policies -> Route Map / Access List Assignment; (3) Router Identifier + New Neighbor IP/Description + Group Assignment + Import/Export policies + Route Map / Access List Assignment -> I/E Policy, AL Details; (4) ... til configuration completion.
2. High-level: (1) Simplistic Input; (2) Comprehensive Output (based on the context of the original configuration file)
3. How to update the model on the go?
*What we want to show*:
1. LLMs are effective in understanding network configuration context and 'accurately' produce configurations, thus avoiding the need for manual examination and manual interference in both updating templates or formal models, We can do this by simply masking away the last part of the neighbor configuration and compare the output.
2. We can show that the LLM can be applied to different vendors: both junipter and Cisco, in an automated fashion and produce output accurately.

(1) User Study: Providing manual specification, formal specification, or LLM instruction. Metrics (1) user preference, (2) time cost, and (3) accuracy/quality.

(2) Accuracy/quality/completeness of the LLM compared to formal specifications.
