# Balanced-Gradient-Forests-with-quantile-classifier
Improving ecological community modeling by accounting for class imbalance in each Random Forests (RF) model within gradient forests, to collates the split-point improvements in impurity, and uses these to convert predictor variables into a biologically-informed importance scale.

# Introduction
Imbalanced data, or the class imbalanced problem, refers to classification settings involving two classes where the ratio of the majority class to the minority class is much larger than one (e.g. a imbalanced ratio of 6649/988 = 6.73 where there are 6649 species presences and 988 absences).

# Bayes decision rule
Class imbalanced data seriously hinders the classification performance of learning algorithm such as RF because their decisions are based on the Bayes rule, a widely used method in machine learning. Essentially, it is used because it is the decision rule that minimizes misclassification error, which at first seems like a good property. However, this is problematic for imbalanced data since misclassification error is often minimized by classifying most (if not) all of the data as belonging to the majority class. For example, there are 99 species presence and 1 absences, predicting 100 occurrences as presences returns 100% True Positive Rate and 99% overall accuracy (99/100).


