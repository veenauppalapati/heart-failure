# heart-failure
This is project 2 for Rutgers AI bootcamp
Dr. House wants to know, can we predict heart disease with a model?
![image](https://github.com/user-attachments/assets/f63eff0e-f375-4dac-bc59-60a0b214b15b)


## Decision Trees and Decision Tree Ensembles 
The second file "Failing_hearts.ipynb" performs the same preprocessing of the dataset in order to test the performance of decision tree and decision tree ensemble classifiers. 

Parameters of each classifier such as the number of estimators, which determines the total trees the ensemble uses, are iterated through in for loops and their accuracies recorded and compared. 
As ensembles can be complex and take long to fit/test, the python library tqdm is used to generate a timing for the iteration which the user can take into account when deciding on the range and step of the for loop used.
The scores per each parameter are then plotted using matplotlib to generate a graph such as the one below:

![image](https://github.com/user-attachments/assets/9aa8db40-d9d8-45df-af99-306d37db6680)

Graphs are generated for each change in parameter and each ensemble tested, an example for the DecisionTreeClassifier is shown below:

DecisionTreeClassifier: a standard decision tree 
  1. parameter changed: Minimum Leaf Samples

![image](https://github.com/user-attachments/assets/7ad4fa31-a352-401a-95dd-78109abcccb5)

 2. parameter changed: Minimum Sample Split

![image](https://github.com/user-attachments/assets/d7188c40-75f5-40dc-b3e2-5606818d2e20)

For additional graphs and combinations check "Failing_hearts.ipynb". 
The ensembles and trees tested for fit are:

DecisionTreeClassifier: a standard decision tree

GradientBoostingClassifier: the ensemble is formed by regression trees which are fit on the negative gradient of the loss function. 

AdaBoostClassifier: first an original classifier is fit on the data and then copies are fit on the data, the weights of failed classifications are adjusted. Idea is that classifications which are often wrong are focused on more. 

RandomForestClassifier: Randomized decision tree classifiers are fit on sub-samples of the data except the trees use 'best split strategy' in order to prune badly performing trees. Averaging of the trees are done to generate a prediction.

ExtraTreesClassifier: Similarly to RandomForestClassifier, randomized extra trees are fit, except on the whole data and then tested on sub-samples of the data during fitting. Averaging of the trees are then done to generate a prediction. 

HistGradientBoostingClassifier: A faster version of GradientBoostingClassifier.

The parameters tested when used as a parameter for the ensemble/classifier are:

number of estimators: the number of decision trees used in the ensemble

min_sample_leaf: the minimum number for a node to be a leaf

min_sample_split: the minimum number required to split an internal node

learning_rate: the rate at which the classifiers update

max_leaf_nodes: limits the number of leaf nodes

max_bins: maximum number of bins to use to bin each feature array 

min_impurity_decrease: causes a split in the node if it causes a decrease of impurity >= to this value

In our fitting we found the best performing classifier to be the RandomForestClassifier due to both its good generalization and best testing accuracy score. The graphs for the RandomForestClassifier generated using the above method are used to create a range starting point for a final optimization of combined changes in parameters iterated through via multiple nested for loops. 

### Citations
Heart disease dataset from kaggle https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction
scikit-learn.org
