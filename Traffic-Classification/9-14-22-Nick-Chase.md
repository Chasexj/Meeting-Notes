# Project: Traffic Classification and Automated Censorship Detection

Discussion:

1. Walk through the slides, address any question that Nick might have.
   
   1. https://github.com/np-tokumei/ML-assisted-DNS-censorship-detection/tree/master/slides/Darpa_Slides
   2. Reminder to maybe disgard the OONI and Satellite comparision for the PI meeting.

2. Inquire about potential venue to submit the IoT data collection paper.
   
   1. [[2110.00060] Automating Internet of Things Network Traffic Collection with Robotic Arm Interactions](https://arxiv.org/abs/2110.00060)

3. Discussion on todo on traffic classification:
   
   1. Recap: Our results show that we can rely on a small set of features to yield good classification results to improve efficiency. At the same time, we can improve feature set durability and reduce retraining frequency by locating features that are (1) remaining informative across datasets, i.e. low concept drift and (2) have similar value distributions across datasets, i.e. low data drift.
   
   2. We need to collect datasets on different locations to verify that our selected sets of feature are indeed working as we claim.
   
   3. Literature review on "why not just retrain"? Some directions to look into: labeling is becoming costly and less feasible. Time cost for retrain. Etc.
   
   4. We can show that the set of features extract from certain datasets also scales to additional datasets that may contain different types of services/applications. (but on the same encryption type.)
   
   5. Establish a metric for selecting the optimal set of features: how do we rigorously combine f1/accuracy/precision with data drift metrics?
