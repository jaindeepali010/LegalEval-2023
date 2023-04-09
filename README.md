# LegalEval-2023
# This repository shows the implementation of our proposed approach while participating in SemEval-2023: Task 6: LegalEval: Understanding Legal Texts

Our paper titled as "*NITS_Legal at SemEval-2023 Task 6: Rhetorical Roles Prediction of Indian Legal Documents via Sentence Sequence Labeling Approach*", in *Proceedings of the 17th International Workshop on Semantic Evaluation (SemEval-2023)* is recently accepted. We will soon share the link of the paper once it is online.

**Dataset details:** The dataset provided for this task includes 247 training document-summary pairs, 30 development document-summary pairs, and 50 documents for testing. The sentences present in these documents are classified into 13 different rhetorical role classes: Preamble (PREAMBLE), Facts (FAC), Ruling By Lower Court (RLC), Issues (ISSUE) Argument by Petitioner (ARG PETITIONER), Argument by Respondent (ARG RESPONDENT), Analysis (ANALYSIS), Statute (STA), Precedent Relied (PRE RELIED), Precedent Not Relied (PRE NOT RELIED), Ratio of the decision (Ratio), Ruling By Present Court (RPC), None (NON).

**Baseline Implementation:** Sentence-level classification

Firstly, in order to establish a baseline set of results, a simple sentence classification notebook is presented with filename: Baseline.ipynb 

**Proposed Approach 1:** Sentence Sequence Labeling Approach: This notebook is presented with filename:Sentence_Sequence_Labeling_Approach.ipynb

**Description of our approach:** The primary idea for model development that has been proposed in this work, is a sentence-sequence classification based idea, where a local-context based dataset is built for model training. This dataset is built with a sentence window size of 5, where we hoped to train a sentence-sequence classification model that can learn from it's local context. The reason for restricting the window size to 5 sentences is due to the resource constraints as well as the extremely lengthy nature of legal documents.

**During Prediction:** During inference we consider two different ways of recovering the sentence level labels: considering the middle sentence in an input sequence as the sentence of interest for recording it's label and considering the last sentence as the sentence of interest. These two approaches are called as the $M_{SS-Mid}$ and $M_{SS-End}$ respectively.

*One important observation from the dataset is that the sentence labels are having a high degree of class-imbalance. Such kind of imbalanced data often causes deep learning models to ignore the minority classes and perform poorly during inference.*

**Proposed Approach 2:** Oversampling Approach: This notebook is presented with filename:Sentence_Sequence_Labeling_Approach.ipynb

**Description of our approach:** Firstly, we decide to keep only one copy of any 5-sentence sample where at least one of the labels is a dummy label for a 0-vector sentence. Secondly, for all the other types of samples, we utilize the normalized frequencies of each class to calculate the exact number of times we will oversample them. This oversampling technique gives rise to two new variants of the proposed approach, which are referred to as $M_{SSO-Mid}$ and $M_{SSO-End}$.
