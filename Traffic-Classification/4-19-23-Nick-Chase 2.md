### Chat with Gerry on AC-DC and Retina Variation

AC-DC assumes batching where as in Retina's current implementation is not assuming - hence the higher model inferencing time.

Stanford team implementation uses scikit learn with high time complexity, this is already addressed with reduced model inference time-complexity.

Working with Gerry - how to do real-time inference fast with one flow at a time prediction? Challenge - AC-DC balances the tade-off between accuracy and efficiency, can we take another approach to minimize this trade-off by using extremely simple but accurate model with stream-lined feature feeding.

### Measurement without endpoints (IMC'23 Submission)

We have retrieved the pcap with labels of censorship status, can we run ML pipeline to discern packet-level features that are not derived and informative for censorship detection?

### Stable-Diffusion

CMU team and NSDI poster both recently published related work (but on GAN-based method). 

Stanford team also had similar idea but never consolidated it.

We have preliminary result and the pipeline design - work towards HotNets submission