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

   
2. Configuration translation between routing vendors:
   
   e.g.,<img width="500" alt="Screenshot 2023-11-15 at 12 19 37 PM" src="https://github.com/Chasexj/Meeting-Notes/assets/47127634/b8f63a60-8fc2-4daa-b63b-bbc3ed2f4aa8">
