# Project: Traffic Classification and SAGE Extension

Traffic Classification Discussion and feed back:

1. Re-identified key research questions and contributions, see slides 81-85. 
   
   1. [Service Recognition - Google Slides](https://docs.google.com/presentation/d/1H8DuVWTaylKYb9JGSsarL4SaPZNMmQtujGFEkh-rcS8/edit#slide=id.g18252b94f32_0_0)
      
      https://github.com/noise-lab/service-recognition/issues/28
      
      

2. Feature subset search space optimization by bound and formalization of adaptive classifier.
   
   1. https://github.com/noise-lab/service-recognition/blob/main/adaptive_classifier.pdf

SAGE extension:

1. Key observation: ambiguous specifications doesn't necessarily cause issue.

2. There is no rationale to spend resources to narrow down ambiguities that are not causing problems.

3. Research Question:
   
   1. Can we identify ambiguities that are not necessarily harmful?
   
   2. Can we verify these non-harmful ambiguities indeed do not cause issues in real implementations?

4. Approach:
   
   1. Reproduce SAGE.
   
   2. When enconutering multiple logic forms (i.e ., interpretations from CCG), check if there exists dependecy of the logic forms in elsewhere.
      
      1. If yes: this is an ambiguity that can indeed cause chain effects.
      
      2. If not, having different configurations of the ambiguity does not introduce problems and hence shouldn't be worried about.
   
   3. Evaluation:
      
      1. For determined non-harmful ambguities, produce unit tests and show that different logics forms lead to the passing of the unit tests regardless.
