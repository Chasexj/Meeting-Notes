# Project: Traffic Classification and SAGE Extension

Traffic Classification Discussion and feed back:

Plan is to set up a VM where the bootstrapping, adpative model selection, and inferencing is going to take place. All models will be stored in the VM. We will replay traffic from a local machine to the VM to evaluate the behavior of the adaptive classifier. There will be two variables: (1) number of flows to pass into the VM and (2) system resource available due to external processes.

    What we have done:

        1. Rewrote the bootstrapping function to reduce model search space compared to exhaustive search, given any value of levels of feature space reduction intensity.

        2. Wrapping up implementation of the adaptive model selector, including function to obtain current overall system resource usage, computing model resource bottleneck, and dynamically switching models on command.

    What we need to do:

        1. Set up the VM.

        2. Figure out how  to exactly replay the traffic, scp raw pcap flow?

        3. Experiment to see if the model system measurements vary based on the number of flows in the overall dataset used for training and testing.

    Questions:

       What's a sign that rebootstrapping is required when we don't have ground truth?

        How is classification done in practice? One flow a time or in bulk?

Show results on SAGE.
