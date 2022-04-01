### 9/23/2021
* Run filtering on multiple processor to speed up job (DONE)
* Run nprintml on both unfiltered and DNS-filtered flows (DONE)
* Concrete definition of a flow (DONE)
### 9/27/2021
* Nprint cannot parse pcapng-Script to convert pcapng to pcap (DONE)
* pcapng to pcap conversion can be done using tshark -F option (DONE)
### 9/29/2021
* More classes. (DONE)
### 10/12/2021
* Per IP labeling on 4 classes (DONE)
### 11/3/2021
* no ipv4
* video vs audio vs web vs non-related, more classes (DONE)
* feature importance in autogluon pipeline (DONE)
### 11/15/2021
* Experiments on packet selections (DONE)
* Conferencing apps (DONE)
### 11/17/2021
* Meet data, same server from Google (DONE)
* Class of others to prove classier’ effectiveness (DONE)
* Reproduce Renata’s results (Done)
* Feature Importance (DONE)
* Capability of subcategories in services/applications
* non bi-directional flows.
* Systems: Cost (memory usage, packet loss, dropping packets (simulate), model time execution), scalability, different types of services may have different reliability on packet selections, prioritize what’s important. 
### 12/8/2021
* Feature importance needed to explain high scores (DONE)
* a super lightweight model that muxes to other models would be interesting (DONE)
### 1/5/2022
* Assess different previous works, do previous features still work, SoA technique and what has changed, the sharing of the larger infrastructure and the encryption of DNS. (1) Flattening of the internet breaks ip-based and dns-based identification and (2) earlier works do not reflect current...  (In progress)
* Changing of the servers (correlate tcp options to servers).
* https://github.com/inria-muse/video_collection

### 1/19/2022
* Two class same server - feature importance changes? (need to collect new traffic because youtube and meet are collected at different locations) (In progress)
* Technical contribution for the paper (Discussed, not of high concern, more about showing such a method works)
* Which deadline/goal to meet? nsdi (2022-04-20), conext (June), sigmetrics (august), ACM Multimedia, EuroSys (october)
* More classes: Breaking down the model./Minimum requirements for difference classification tasks./Streaming,conferencing, other traffic, web browsing, social media (etc). (In progress: DNS fectched, parsing issue...)
* Cost of different models: memory usage (Partially DONE on macro and 4class), packet loss (Partially DONE on 4class), model time execution (Partially DONE on macro and 4class and conf_stream_other). observe in real time: scaling up can be costly, calculation
* https://www.unb.ca/cic/datasets/vpn.html

### 1/26/2022 and 2/8/2022
* More classes: Breaking down the model./Minimum requirements for difference classification tasks./Streaming,conferencing, other traffic, web browsing, social media (etc). (In progress: DNS fectched, parsing issue...) (DONE..? Not enough)
* Inference cost. (DONE)
* Seperate pipeline to compare feature sets
* Looking at initial handshakes and script for feature selection, exclusion of payload? (DONE)
* Normal DNS on Chrome configure (DONE)
* Type of paper? What to aim for, systems paper (summarize progress, questions). (Conclusion: systems paper)
* Note on the other similar paper: bad data set, lack of reasoning of the results from a systems/networks perspective, no illustration of why the high prediction results --> We can do better.

### Discussion
* Thoughts on narrowed direction: (motivation: internet flattening/centralization) -> (solution: machine learning based application identification) -> (application: traffic prioritization for low latency networks on the ISP level)
* Questions to address:
* * What is the trade-off that we want to optimize (latency sensitivities are different for application, the overall goal is to optimize the overall latency-based QoS service in various networks conditions such as high bandwidth utilization.)
* * For different applications, we need to measure the current latency on average, then using optimization we can find the target latency and compare them.
* * What kind of instrument/capability does ISP have on traffic prioritization.
* * Do we want to implement a demo (simulator or emulator) or a tool (real-time prioritization if we are clear about which part of the ISP we are going to implement it on and get real-world results)? 
* * Paper on switch priority queuing.
* * Traffic centralization / flattening
* * Inference time vs different conditions, how well does the model work in real time (offline first).
