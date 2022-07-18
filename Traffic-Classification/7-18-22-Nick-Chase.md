# Project: Traffic Classification

Issues: https://github.com/noise-lab/service-recognition/issues

Previous week results:

1. Results on found robust features for each type of encryption techniques.

2. Model performances if we only use the top 5 robust features.

Discussion:

1. How is the idea of establishing a efficient classifier by:
   
   1. classifying traffic based on encryption type.
   
   2. after encryption type has been classified, further classifying the traffic into different applications using features that are specifically informative for traffic under that encryption type.
   
   The advantage of this would be that:
   
   1. we do not need to rely on one classifier for all types of traffic which can lead to potentially sacrifise on accuracy.
      
      If a good idea, then
      
      a) we need to see whether it is possible to classify encryption type.
      
      b) What's the performance improvement in terms of system cost?
      
      c) how much does performance degrade (or maybe even improve) when we don't use all features?
      
      d) design flexible classifier that allows for adjustment in terms of utilization of amount of features
