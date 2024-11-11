# Balanced-Gradient-Forests-with-quantile-classifier
Improving ecological community modeling by accounting for class imbalance in each Random Forests (RF) model within gradient forests, to collates the split-point improvements in impurity, and uses these to convert predictor variables into a biologically-informed importance scale.

# Introduction
Imbalanced data, or the class imbalanced problem, refers to classification settings involving two classes where the ratio of the majority class to the minority class is much larger than one (e.g. a imbalanced ratio of 6649/988 = 6.73 where there are 6649 species presences and 988 absences).

# Bayes decision rule
Class imbalanced data seriously hinders the classification performance of learning algorithm such as RF because their decisions are based on the Bayes rule, a widely used method in machine learning. Essentially, it is used because it is the decision rule that minimizes misclassification error, which at first seems like a good property. However, this is problematic for imbalanced data since misclassification error is often minimized by classifying most (if not) all of the data as belonging to the majority class. For example, there are 99 species presence and 1 absences, predicting 100 occurrences as presences returns 100% True Positive Rate and 99% overall accuracy (99/100).

More formally, let $`Y∈{0,1}`$ denote the two-class outcome and let $`p(x)=P(Y=1∣X=x)`$ be the classification probability for the minority group. The Bayes rule classifies cases to class label 1 if the classification probability is 1/2 or larger,


$\δB(x)=I\left\{\p(x)≥1/2\right\}$.

The problem is that $`p(x)`$ is small in imbalanced problems. This forces the Bayes decision rule to classify all cases to class label 0 as the IR increases. Indeed, in the limit:


$`δB(x)=I(p(x)≥1/2)→0,if p(x)→0`$.


This seemingly works out for the Bayes decision rule, because [as will be shown in equation (1)] this yields a misclassification error rate of zero.

# Formal definition of imbalanced
**Definition 1:** The imbalance ratio (IR) is defined as $`IR=N0/N1`$ where $`N0`$ and $`N1`$ denote the cardinality of the majority and minority samples, respectively. A data set is imbalanced if $`IR > 1`$.

For example, the $`IR`$ in our previous example was 6.73. This is actually only moderately high and in practice it is possible to encounter data with much higher values. In fact, we will examine a simulation setting where the value is allowed to be 100.

**Definition 2:** A minority class example is safe, borderline, or rare if 0 to 1, 2 to 3, or 4 to 5 of its 5 nearest neighbors are of the majority class, respectively.

The percentage of minority class samples that are rare plays an important role in the performance of a classifier.

**Definition 3:** The data is marginally imbalanced if $`p(x)≪1/2`$ for all $`x∈X`$ where $`p(x)=P(Y=1|X=x)`$.

Thus, marginally imbalanced data is data for which the probability of the minority class is close to zero throughout the feature space.

Definition 4: The data is conditionally imbalanced if there exists a set $`A⊂X`$ with nonzero probability, $`P(X∈A)>0`$, such that $`P(Y=1|X∈A)≈1`$ and $`p(x)≪1/2`$ for $`x∉A`$.
In contrast to marginally imbalanced data, conditional imbalancedness occurs when the probability of the minority class is close to 1 given the features lie in a certain set, and approximately zero otherwise. In both cases, it is assumed that the minority class is rare.


Note: math edition can be found from: 
https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions and
https://gist.github.com/modenaxe/e7debe3dcb727f99248139f7d31fac57



