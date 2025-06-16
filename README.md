We have a categorical target vector and want to remove uninformative features, If the features are categorical, calculate a chi-square (χ 2 ) statistic between each feature and the target
vector, If the features are quantitative, compute the ANOVA F-value between each feature and the target vector, Instead of selecting a specific number of features, we can also use SelectPercentile to select the top
n percent of features, Chi-square statistics examines the independence of two categorical vectors. That is, the statistic is the
difference between the observed number of observations in each class of a categorical feature and what
we would expect if that feature was independent (i.e., no relationship) with the target vector, where Oi
is the number of observations in class i and Ei
is the number of observations in class i we
would theoretically expect if there were no relationship between the feature and target vector.
A chi-squared statistic is a single number that tells you how much difference exists between your
observed counts and the counts you would expect if there were no relationship at all in the population.
By calculating the chi-squared statistic between a feature and the target vector, we obtain a
measurement of the independence between the two. If the target is independent of the feature variable,
then it is irrelevant for our purposes because it contains no information we can use for classification. On
the other hand, if the two features are highly dependent, they likely are very informative for training our
model.
To use chi-squared in feature selection, we calculate the chi-squared statistic between each feature and
the target vector, then select the features with the best chi-square statistics. In scikit-learn, we can use
SelectKBest to select the features with the best statistics. The parameter k determines the number of
features we want to keep - and filters out the least informative features.
It is important to note that chi-square statistics can only be calculated between two categorical vectors.
For this reason, chi-squared for feature selection requires that both the target vector and the features are
categorical. However, if we have a numerical feature we can use the chi-squared technique by first
transforming the quantitative feature into a categorical feature. Finally, to use our chi-squared approach,
all values need to be non-negative.
Alternatively, if we have a numerical feature we can use f_classif to calculate the ANOVA F-value
statistic with each feature and the target vector. F-value scores examine if, when we group the numerical
feature by the target vector, the means for each group are significantly different. For example, if we had
a binary target vector, gender, and a quantitative feature, test scores, the F-value score would tell us if
the mean test score for men is different than the mean test score for women. If it is not, then test score
doesn’t help us predict gender and therefore the feature is irrelevant.
