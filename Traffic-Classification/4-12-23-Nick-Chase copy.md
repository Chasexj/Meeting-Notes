### SIGKDD Rebuttal Review

https://docs.google.com/document/d/1lYgVJ5xgUiBL9BZy4glib0mV9IQhD2H-Jf5j7nMDW58/edit#

**Rebuttal**
**Summary of responses and revisions**
We thank the reviewers for their thorough and insightful evaluations of our paper. We are pleased that multiple reviewers found the paper to be well-written, clear, and engaging (xbSS, PfPA, fvD8, njZH), with an interesting and novel application of ML models (xbSS, PfPA). We appreciate the recognition of our efforts in creating and open-sourcing valuable datasets (PfPA, fvD8, njZH), as well as the acknowledgment of our rigorous and systematic methodology (fvD8, njZH) that led to promising findings (fvD8) and important contributions (njZH). We are glad that the reviewers noted the strengths of our ML pipeline, including the selection and exclusion of features (fvD8), the comparison of both supervised and unsupervised settings (fvD8), and our exploration of model explainability (fvD8). It is encouraging that our work on DNS censorship detection was considered novel, important, and relevant to the conference (PfPA, fvD8).

If the paper is accepted, we commit to revising both the main body and Appendix based on the reviewers' suggestions. We would like to highlight that both the code and data are available now at https://github.com/noise-lab/automated-dns-censorship, and there is also an interactive dashboard at https://grafana.chasejiang.com/d/3cepZdcVk/mice-ml-based-censorship-detection?orgId=1. 

We will rearrange relevant results and explanations from the Appendix to the main body as appropriate. Below, we list the key revisions and additional experiments we will make to the paper, tagged by each reviewer id:

1. Emphasize aspects of data source comparisons and model learning capability in the Introduction (xbSS).

2. Clarify the imbalanced dataset concern and provide explanations in Section 3.2 (xbSS).

3. Include more information on our interactive dashboard deployment and discuss additional models (PfPA).

4. Add more details on the applicability of the solution, GFWatch granularity, and generalization to other countries (fvD8).

5. Further explanation of data and measurement details, US probes, reproducibility, and related work (fvD8).

6. Incorporate revisions related to feature engineering and audience choice (njZH).

7. Update hyperlinks to the open-source datasets, ML pipelines, and the interactive dashboard (fvD8, njZH).

**Common concerns**

1. Justification for claims and model choices (xbSS, fvD8, PfPA)
   
   1. Comparison of ML model trained on individual datasets
   
   2. Include additional models
   
   3. Detail on the choice of models

2. Improve reproducibility and technical details (xbSS, fvD8)
   
   1. Add details on downsampling or other mechanisms to address class imbalance
   
   2. More detail on data collection, filtering, and feature selection
   
   3. Share code, parameters, and experiment setup

3. Address limitations and applicability (fvD8, njZH)
   
   1. Discuss system's ability to handle dynamic nature of censorship ecosystem
   
   2. Explore the application of models to other countries with censorship
   
   3. Consider more complex features and additional discussion on feature engineering

4. Selection bias and label reliability (PfPA, fvD8)
   
   1. Address potential selection bias from Satellite and OONI
   
   2. Explain how clean records are obtained and verify their reliability

5. Related work and dataset release (fvD8, njZH)
   
   1. Add more discussion to existing literature
   
   2. Update dataset hyperlinks for public use

### Group Meeting
Noah request - Start at 11:15 for this week?
First May: Phil Roberts, from 