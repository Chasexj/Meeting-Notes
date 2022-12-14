# Project: Traffic Classification and Censorship Dashboard

Traffic Classification Discussion:

1. Currently pipeline experience similar system costs (in terms of space complexity) for different numbers of flows:
   
   1. SWAP/RAM not cleared?
   
   2. Try one flow at a time to see if things are different.

2. Training is going to be done in the cloud or off router, do we only care about inferencing costs excluding training?

3. Resource is dominated by encoding and preprocessing, should the inference speed be the aggregation of the entire process from encoding, preprocessing to inferencing?
   
   1. Maybe Nprint is ehausting all available resource: verify by experiments on VM and we want to find minimum requirements for different models/features.

4. When system resource is low, preprocessor and model may still work but just very slow, how to we account for this in terms of picking the optimal model?

Dashboard for censorship: https://github.com/np-tokumei/ML-assisted-DNS-censorship-detection/issues/57



Notes from meeting:
