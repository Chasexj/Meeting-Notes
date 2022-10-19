# Project: Traffic Classification and Potential New Project

Discussion:

1. We have the coarse-grained preliminary results on costs associated with different feature subsets for TLS traffic classification. How do we develop a comprehensive study building on top of it? Refer to the Big Picture Stuff in the issue.
   
   1. https://github.com/noise-lab/service-recognition/issues/28
   2. We do not want to enter another endless experiment loop, when is enough?

2. Next steps on the DNS censorship project.
   
   1. A working ML-based dashboard?
   
   2. Transferability of ML models onto other countries?

3. Potential new project idea: Processing protocol standards via a NLP approach to discern potential non-interoperabilities issues among different implementations of the same protocol.
   
   1. Example: FRRouting, Bird, and Cisco implementations of the OSPF protocol often result in bugs/failures when they are running in parrallel.
   
   2. Such failures are often due to the fact that, because standards are human-writing, different implementations can conflicting understandings regarding ambiguous specifications in the standards.
   
   3. https://src.acm.org/binaries/content/assets/src/2022/xi-jiang.pdf
   
   4. https://dl.acm.org/doi/pdf/10.1145/1823844.1823849
   
   5. 2009 global internet slowdown: Cisco routers could not correctly handled the long Autonomous System (AS) Path from MikroTik routers used by Supronet (a Czech Republic ISP), causing Cisco routers to experience repeated reboots and slowing down Internet traffic significantly.
