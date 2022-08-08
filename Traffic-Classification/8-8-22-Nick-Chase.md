# Project: Traffic Classification

Discussion:

1. What are we submitting to the IAB workshop:
   
   1. https://github.com/noise-lab/service-recognition/issues/20

2. Discussion on incorporating Retina with traffic classification:
   
   https://zakird.com/papers/retina.pdf
   
   1. Talk to Gerry about what measurement do we want to record?
      
      1. Memory usage over time?
      
      2. Besides inference time and memory usage, what are somethings that ISP value in real time traffic classification

3. What's the specific details that we want to implement to verify for feature robustness?
   
   1. Currently we have decided to systematically verify if the selected set of features are robust by training models on "old" dataset and selecting the most important features and then testing such models on a "new" dataset to verify the models' performance.
   
   2. Doing so only allows us to check if using the set of features can produce good results, but don't provide detail in what features are not robust, thoughts on this?
