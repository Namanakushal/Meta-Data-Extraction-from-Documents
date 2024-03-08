# Meta-Data-Extraction-from-Documents
## Extracting Data from Rental Agreements with NLP

This document outlines the process of building an AI/ML model to extract key data points from rental agreements in PDF format.

**1. Business Requirement**

The goal is to develop a model that can automatically extract specific information from rental agreements, including:

* Agreement Value
* Agreement Start Date
* Agreement End Date
* Renewal Notice (Days)
* Party One (Landlord)
* Party Two (Tenant)

**2. Machine Learning Approach - Named Entity Recognition (NER)**

This problem can be addressed using Named Entity Recognition (NER), a subfield of Natural Language Processing (NLP). NER identifies and classifies predefined categories of information within text data. Here, we want to recognize entities like dates, names, and numbers.

**3. Approaches Explored**

Three approaches were evaluated for building the NER model:

**Approach 1: Spacy Pattern Matching**

* This approach attempted to identify entity locations using pre-defined patterns in the Spacy library.
* However, only 21% of entities were accurately captured due to limitations of pattern matching for complex documents.

**Approach 2: Pseudo-Annotated Data with Pre-Trained Model**

* This approach utilized a pre-trained NER model on similar data sets.
* Training data was "pseudo-annotated" by the model itself. This means the model made predictions on unlabeled data, which were then used for training.
* While recall (the proportion of relevant entities identified) on the pseudo-annotated data decreased compared to Approach 1, predictions on unseen validation data improved.
* This suggests the model learned from the broader context of the agreements.

**Approach 3: Manually Annotated Training Data**

* This approach involved manually labeling entities in training and validation documents using the Spacy annotator tool.
* Fine-tuning the Spacy NER model on this data did not yield significant improvements in recall or prediction accuracy.
* This could be due to challenges in manual annotation of complex legal documents.

**4. Conclusion**

* Approach 2, using a pre-trained model with pseudo-annotated data, emerged as the most promising approach.
* Further improvement might be possible by:
    * **Improving Date Annotation:** More accurate date entity recognition could enhance Approach 3's performance.
    * **Exploring Advanced Techniques:** Investigating other NLP techniques like Bidirectional Encoder Representations from Transformers (BERT) could potentially lead to better results.

**Next Steps**

* Based on these findings, it's recommended to refine Approach 2 by:
    * Focusing on accurate date entity recognition for Approach 3.
    * Investigating advanced NLP techniques for potential improvements.
* It's also crucial to evaluate the model's performance on a larger dataset to confirm its generalizability.
