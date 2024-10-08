
# Artificial Intelligence
## Unit 1


An **agent** is anything that can be viewed as perceiving the environment through sensors and acting upon that environment through actuators.\

What is rational at any given time depends on 4 things:
1. The performance measure that defines the criterion of success
2. The agent's prior knowledge of the environment
3. The actions that the agent can perform
4. The agent's percept sequence to date

For each possible percept sequence, a **rational agent** should select select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and the built in knowledge of the agent.\

##### Specifying the task environment
We use PEAS (Performance metric, Environment, Actuators, Sensors).

### Properties of task Environments
1. Fully vs Partially Observable
2. Single vs Multi Agent
3. Deterministic vs Stochastic
4. Episodic vs Sequential
5. Static vs Dynamic
6. Discrete vs Continuous
7. Known vs Unknown (Refers to the designers knowledge, not the environment)

### Search Problems
A search problem can be defined formally as:
1. State Space: A set of possible states that the environment can be in. 
2. Initial State
3. Goal State
4. Actions available to the agent
5. Transitional model, i.e, what each action does
6. Action Cost function

### Uninformed Search Algorithms

The search data structure to store a node in the search space tree is :\
- node.**STATE**: Stores the current state
- node.**PARENT**: Stores the parent state
- node.**ACTION**: Stores the action done on the parent that reached the current state
- node.**PATH-COST**: Cost from initial state to current state.

The data structure used to store the frontier is:
- priority queue
- FIFO queue
- LIFO queue

##### Measuring problem solving performance
- Completeness
- Cost optimality
- Space complexity
- Time complexity
#### Best First Search
The next node is decided by evaluating the cost function and choosing the best possible choice. Can revisit, unlike greedy best first search.

#### Breadth First Search

#### Dijkstra

#### Depth First Search

#### Depth Limited Search

#### Iterative Deepening Search

#### Bidirectional Search
Starts search from initial state -> goal state and from goal state -> initial state simultaneously in the hope that the 2 paths intersect.

### Comparison of uninformed search strategies


| Criterion    | Breadth-First | Uniform-Cost        | Depth-First | Depth-Limited | Iterative-Deepening | Bidirectional |
| ------------ | ------------- | ------------------- | ----------- | ------------- | ------------------- | ------------- |
| Complete     | Yes           | Yes                 | No          | No            | Yes                 | Yes           |
| Optimal Cost | Yes           | Yes                 | No          | No            | Yes                 | Yes           |
| Time         | $$b^d$$       | $$b^{1 + [C^*/e]}$$ | $$b^m$$     | $$b^l$$       | $$b^d$$             | $$b^{d/2}$$   |
| Space        | $$b^d$$       | $$b^d$$             | $$bm$$      | $$bl$$        | $$bd$$              | $$b^{d/2}$$   |

# Machine Learning
## Unit 3

A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P if its performance at task in T as measured by P improves with experience E.

The types of Machine Learning are:
1. Supervised Learning
	1. Classification
	2. Regression
2. Unsupervised Learning
	1. Clustering
	2. Association Analysis
3. Reinforcement Learning

##### Comparison of Various Machine Learning Techniques

| Supervised                                             | Unsupervised                                                           | Reinforcement                                                  |
| ------------------------------------------------------ | ---------------------------------------------------------------------- | -------------------------------------------------------------- |
| Used for Classifying                                   | To find pattern                                                        | Rewards - if guessed correctly                                 |
| Labelled training data                                 | Unknown and unlabeled data                                             | Model learns and updates itself through rewards and punishment |
| Classification and Regression                          | Clustering and Association analysis                                    | No such types                                                  |
| Naive Bayes, KNN, LR, SVM                              | Kmeans, PCA, DBSCAN, apriori                                           | Q-Learning, Sarsa                                              |
| Handwriting Recognition, stock market prediction, etc. | Market based analysis,<br>recommender system, customer<br>segmentation | Self driving cars, intelligent robots                          |
| Simple to understand                                   | More difficult to understand and implement                             | Most complex                                                   |

#### Descriptive and Predictive Modeling

**Descriptive**: Determines similarities in the data and to find existing patterns.
Ex: Clustering, Association, Anomaly detection

Predictive: It uses the supervised learning functions which are used to
predict the target value.
Ex: Regression, Decision Trees, and NN

#### Types of Data Attributes

1. Qualitative
	1. Nominal: Variables with no inherent order or ranking. Ex: Blood group, gender, race.
	2. Ordinal: Variables with ordered series. Ex: Low/Middle/High income
	3. Binary: Only 2 possible values. Ex: Pass/Fail, Yes/No
2. Quantitative:
	1. Discrete: Based on counts. Ex: Number of students in a class
	2. Continuous: Can be measured on a continuum or a scale. Ex: Length, height



#### Underfitting vs Overfitting

| To avoid Underfitting (High Bias) | To avoid Overfitting (High Variance) |
| --------------------------------- | ------------------------------------ |
| Increase model complexity         | Increase the training data           |
| Train for longer                  | Less complex model                   |
| Increase the number of features   | Remove less relevant features        |
| Decrease regilarization           | L1/L2 regularization                 |
| Choose a difference model         | Ensembling                           |

#### Evaluating Performance

Correlation Matrix

| True Positive  | False Positive |
| -------------- | -------------- |
| False Negative | True Negative  

$$
Accuracy = \frac{TP + TN}{TP + FP + FN + TN}
$$

Sensitivity measures the proportion of positive cases that were correctly classified\
Specificity measures the proportion of negative cases that were correctly classified

$$
Sensitivity = \frac{TP}{TP + FN}
$$

$$
Specificity = \frac{TN}{TN + FP}
$$

Precision measures the proportion of positive identification that are correct
$$ 
Precision = \frac{TP}{TP + FP}
$$

Recall measures the number of actual positives that were correctly identified
$$
Recall = \frac{TP}{TP + FN}
$$

F-Measure is the harmonic mean of precision and recall

$$
F-Measure = \frac{2 * Precision * Recall}{Precision + Recall}
$$

Kappa value of a model indicated the adjusted model accuracy

$$
k = \frac{Observed Agreement - Expected Agreement}{1 - Expected Agreement}
$$

where Observed Agreement is the Accuracy and 

$$
Expected Agreement = \frac{(TP * FP + TP * FN) + (TN * FN + TN * FP) }{TP + FP + FN + TN}
$$


## Unit 4

### Adaboost Algorithm Steps

Set initial weights for each column = 1 / Number of points
Repeat for each column in the dataset
REMEMBER THAT it's always -alpha if correctly classified and plus alpha if negatively classified
#### Step 1
Compare expected classification value with actual value

#### Step 2
Calculate error 

$$
e_i = \sum incorrectly classified weights
$$

#### Step 3
Calculate weight of weak classifier

$$
\alpha_i = \frac{1}{2} \frac{ln(1 - e)}{e}
$$

#### Step 4
Calculate Normalizing Factor

$$
Z = \sum wt * e^{-\alpha if correctly classified} and \sum wt * e^{\alpha if incorrectly classified}
$$

#### Step 5
Update weights

$$
New weight = weight * e^{-\alpha} 
$$

if correct and 

$$
New weight = weight * e^{\alpha} 
$$
if incorrect


## UNIT 5 - CLUSTERING

### Types of clustering

##### 1. Partitioning
Divides into k non hierarcihcal group, clustering is based in centroid based method. \
Distance between the data points of one cluster is minimum \
Distance between the another clusters is maximum.

##### 2. Hierarchical


##### 3. Exclusive
Every data point is its own cluster

##### 4. Overlapping
Object can belong to more than 1 cluster at the same time

##### 5. Fuzzy
Each belong to every cluster with a membership weight between 0 and 1

##### 6. Complete
Every object is assigned a cluster

##### 7. Partial Clustering
Not every object is assigned a cluster (Noise prevention)

### Types of Clusters

##### 1. Well separated
Each point is closer to all the points in its cluster than to any other point in any other cluster


### Solutions to initial centroid problem
1. Multiple Runs
2. Sample and use hierarchical clustering to determine initial centroids
3. Select more than k initial centroids and select best among the initial centroids
4. Post-Processing
5. Bisecting K-Means

Pre-Processing: 
1. Normalize the data
2. Eliminate Outliers

Post-Processing:
1. Eliminate small clusters as they may be outliers
2. Split clusters with high SSE
3. Merge clusters with low SSE