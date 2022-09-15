# Project: Traffic Classification and Automated Censorship Detection

Discussion:

1. Walk through the slides, and address any questions that Nick might have.
   
   1. https://github.com/np-tokumei/ML-assisted-DNS-censorship-detection/tree/master/slides/Darpa_Slides
   2. Reminder to maybe disregard the OONI and Satellite comparison for the PI meeting.

2. Inquire about a potential venue to submit the IoT data collection paper.
   
   1. [[2110.00060] Automating Internet of Things Network Traffic Collection with Robotic Arm Interactions](https://arxiv.org/abs/2110.00060)

3. Discussion on todo on traffic classification:
   
   1. Recap: Our results show that we can rely on a small set of features to yield good classification results to improve efficiency. At the same time, we can improve feature set durability and reduce retraining frequency by locating features that are (1) remaining informative across datasets, i.e. low concept drift, and (2) have similar value distributions across datasets, i.e. low data drift.
   2. Method: 
      1. Obtain feature importance for two datasets
      2. Compute sum of the normalized feature importance across two datasets (This step is to spot features that are becoming less helpful or even harmful to the models, thus preventing concept drift)
      3. Rank the importance-summed features and pick combinations of the most influential features in a “pick M from N fashion”: Given N number of top-ranked features, pick a combination of M features.
      4. Set a performance threshold (e.g. >90%) and find all “qualifying” permutations that satisfy this threshold.
      5. Compute the data drift score on all qualifying permutations and select one with the highest resistance to data drift.
      6. Implementation details: 
         1. We are collecting and using social media datasets to verify data drifts and concept drifts.

   
   3. Todos:
      1. We need to collect datasets on different locations to verify that our selected sets of features are indeed working as we claim.
      2. Literature review on "why not just retrain"? Some directions to look into: labeling is becoming costly and less feasible. Time cost for retraining. Etc.
      3. We can show that the set of features extracted from certain datasets also scales to additional datasets that may contain different types of services/applications. (but on the same encryption type.)
      4. Establish a metric for selecting the optimal set of features: how do we rigorously combine f1/accuracy/precision with data drift metrics?
      5. Aside from the so-said optimal model, we can also provide trade-offs between performance and drifts which allows for implementers to decide on their choices of features based on these trade-offs.
      6. Figure out how to try more permutations systematically.
      7. Decision on how feature importance and drift scores are calculated for fields in a principal fashion.
      
   4. Potential answers to some important questions, with to-dos to justify these answers:
      1. Is using two datasets sufficient for analyzing data drifts? Yes, because although such drift is occurring from one dataset to another, the actual fields that are experiencing the drifts are relatively consistent - show by experimental results.
      2. Is using two datasets sufficient for analyzing concept drifts (i.e. removing fields that are becoming non-informative or even harmful to the models)? Yes, We are not claiming that the selected set of features will stay resilient to concept drifts all the time, same goes with data drift-resilient features. When performance drops, re-evaluation of the datasets to re-select the set of features is required, but our goal is to make models last for as long as possible without having to do such re-evaluations. And we do not need to keep all the datasets and using just their stats should be sufficient enough to re-compute the feature sets - show with experimental results.
      3. Why not just retrain with all features? Retraining cost is high, especially in high-bandth scenarios, this includes costs in both storing all the features and finding the set of optimal features every time when retraining is needed. We can effectively reduce the system costs associated with retraining by dedicating to only retraining on the selected set of few stable features, here we can use Retina as an example system that is capable of such selected traffic capturing. At the same time, even when retraining is easy, there are still costs associated with it, and we can reduce the frequency of retraining by introducing the notion of data drift into consideration when selecting the select of optimal features. - show with experimental results, might be hard to do.
      4. How is our selection of features different from just looking at feature importance? Our cross-analysis between datasets and model drift considerations is beyond just simple feature importance. We can provide examples where simply considering feature importance fails - feature importance is changing across datasets, and data drift is affecting performance despite the set of features being important.
