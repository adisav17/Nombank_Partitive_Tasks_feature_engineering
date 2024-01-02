# Nombank_partitive_tasks

This project is part of work done on Nominal Semantic Role Labeling at NYU under Prof. Adam Meyers. 


We incorpate parse tree based heuristic path features and evaluate their ulity in the prediction of semantic role labels for Nombank.

The build_features file will create a set of input features in the percentage and part folders. We will add parse tree based features and heuristic based features to enhance our input space. 
For the compressed feature dictionary or access to a google drive/ colab environment, please mail as14634@nyu.edu. 

The notebooks will demonstrate the creation, training and evaluation of models for the %/partitive tasks. We experiment with adaboost and logisitic regression.    

We use the following heuristic paths which correlate with ARG1, for some given word in association with a noun predicate. 

(1) If the path is from the support verb to a preceding ARG1, use the path ↑S↓NP↓Noun.
(2) For the path from the support verb to a following ARG1, use ↑VP↓NP↓Noun.
(3) From a predicate noun to a preceding ARG1 (with no support verb), use ↑NP↓NP.
(4) For paths from a predicate noun to a following ARG1, derive the path from the sequence of BIO tags from the predicate noun to the ARG1.

As an example, we elaborate on heuristic (1).
Consider every word w_j in a given input sentence S[w_1,..,w_n] with an output label ARG1 for word w_i and support verb w_s.  If i<s,and if the path P from w_s to w_j is ↑S↓NP↓Noun, then, we estimate j to be having a high likelihood of being i.    
