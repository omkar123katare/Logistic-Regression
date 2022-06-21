# Logistic-Regression

Condition to apply grafient descent: Our dataset must be linearly classifiable.![WhatsApp Image 2022-06-10 at 7 32 43 PM](https://user-images.githubusercontent.com/92416952/173082929-27a5239d-af5f-479b-b32d-5e060c815197.jpeg)
For one Dependendent Variable and one Independent Variable classification of data is done using a classifiying line.
For one Dependent Variable and Two Indepepndent variables classification of data is done using a classifying plane.
For one Dependent Variable and more than 2 Independent variables classification of data is done using a classifying hyperplane.


## Approach 1 for logistic regression - Perceptron Trick
step1. Start with a random line for classification
step2. Randomly select a point in loop and check if the line is able to correctly classify the point or not.
step3. If the point is correctly classified by the point, then there will be no change in the equation of line.
step4. If the point is incorrectly classified by the line, then there will be change in the equation of the classifying line.

### For some epochs, classifying line does not move. Why?
Because, for those epochs, randomly selected row was correctly classified. Change in line i.e. slope values for different features happend only if the randomly selected point is incorrectly classified.

### Problems in perceptron trick-
Perceptron trick does not give us the accurate classification line. It stops as soon as it has correctly classfied the training data points.
i.e. here W slope matrix is updated only for misclassified data points.

## Approach 2 for logistic regression - Sigmoid function
In this approach, not only incorrectly classified points, but also correctly classfied points guide the classification line or plane or hyperplane to its optimum position. Here slope values of features not only change for incorrectly classified points, but also for correctly classfied points. Incorrectly classfied points pull the line or plane or hyperplane towards that point and corrclty classfied points push this classification boundary away from itself. This magnitude of push or pull depends on the distance of this randomly chosen point from the classification line or plane or hyperplane.
In this approach formula for perceptron trick is tweaked a little. Here predicted dependent variable value is passed throgh sigmoid function instead of step function. This is done so as to achieve non zero value of adjustment term for correctly clasified poins.
Now, because of sigmoid function any numerical value will lie in the range between 0 and 1.
Due to this, for any random row, predicted value is passed through the sigmoid fucntion. This creates a gradient lines plot on both sides of classification line. This gradient value also denotes probability value of the point being classifed as one of the classes.

### Problem in sigmoid method-
Because the data points are selected randomly for each epoch, we cannot tell with conviction if the obtained weight values for all the features are the optimum values or not. 

## Appproach 3 for logistic regression - Gradient dscent
We apply gradient descent to our loss fucntion to get its minimum value.

### Loss function- 
#### Maximum likelyhood- product of all the probabilities - 
Model for which this product is greater, it the better model.
#### Issue with maximum likelihood - 
probability values (i.e. sigmoid output) are always between 0 and 1. So, when number of columns in a dataset are large, the maximum likelihood value becomes very small. 
#### Solution -
Taking log of these probaility values and adding them.
#### Issue with this solution -
Probability values ( output of sigmoid fucntion is always between 0 and 1. In this range the the log values are always negative. Hence all terms will have neagtive sign.
#### Multiply each term with a negative sign -
This final wquation we obtained is called cross entropy. As we have multiplied whole thing with -1 sign, we need to minimize the cross entropy. 
#### Issue with this formula -
Here probability values for a row belonging to a particular class are obtained. But, the problem is that we need to put the probability of a row belonginto a class to which it actually belongs. 
To deal with this problem, we modify the cross entropy formula so as to get the probability of a point belonging to a class to which it actually belongs.

The final average loss function can be represented as- 

### Derivative of Sigmoid function - 

### Gradient descent in matrix form -

## Classification metrics -
1. Accuracy score
2. Confusion matrix a.Type I error. b.Type II error
c. Precision d. recall
#### Problem with imbalanced dataset
When to choose precsion and when to choose accuracy as classification metric?
e. F1 score

## Softmax regression (multinomial logistic regression) -
When classification is to be done into more than two classes, we need to use softmax regression.
Here formula used is different. Here we obtain probability values of a data point belonging to all the different classes. For whichever class the probability value is greater, that data point is classified into that class.

Formula for loss function of logistic regression is tweaked to obtain formula for loss function if softmax regression.

## Polynomial Features in logistic regression - 
If our data is not linearly classifiable, we can use polynomial logistic regression. Here also we transform the feature values according to degree of polynomial that we want to train. This increases the number of columns to be trained to number columns in dataset * degree of polynomial.

## Logistic regression - Hyperparameters
1. Penalty : what regularization to be used ? ('l1','l2,'elsticnet','none')default is 'l2'(lasso regularization) regularization
2. dual : 'primal' if rows > columns ; 'dual' if rows < columns
3. tol : tolerance value
4. C : 1/shrinkage_coefficient 
5. class_weight : used if the dataset to be trained is imbalanced.
6. solver : we can choose from different solvers for ( required penalty + type of classification + nature of data ) combination.
7. max_iter : int, default : 100, Number of epochs
8. multiclass : Depending on the numbe rof classed in which classification is to be made. ('auto','ovr','multinomial') [in 'ovr' we can choose different models for each class] 
9. l1_ratio : If elastic net regularization is selected, we need to specify its own hyper parameter.

