## The basic model
Linear regression is the minimisation of the function defined by: <br>
J(\beta) = 1/n (\sum_{i=1}^{n} (y_i - \hat{y}_i)^2) <br>
where y_i is the observed values and \hat{y}_i is our predicted value, this minimises the squared error of our prediction, thus the smaller the value of this function, the more accurate our model is. <br>
The loss is then defined by:  <br>
y-\hat{y} <br>
## Why do we use squared?
This penalises larger errors more <br>
Smooth and differentiable which is ideal for an optimisation problem <br>
## The algebra behind the coding 
### The normal equation: <br>
When we write: <br>
LinearRegression().fit(X,y) <br>
The code is really doing: <br>
\beta = (X^{T}X)^{-1}X^{T}y <br>
from the equation : <br>
y = \beta X + \epsilon <br>
X^{T}X captures the relationship between the features and the inverse "undoes" this structure, multiplying by X^{T}y aligns with the target values  <br>
\beta are unknown parameters, y are our observed values, X is the data we have (such as features), and \epsilon is random noise, which we cannot consider <br>
by solving this equation, we are minimising the squared error from an exact solution of beta, we do not know what the true beta is, however we can predict beta and thus plug into the equation: <br>
\hat{y} = \hat{\beta} X <br>
We cannot know true beta exactly since we have random noise \epsilon which is unpredictable to us.
<br>
### Gradient Descent: <br>
\beta := \beta - \alpha \grad J <br>
J is the cost function, or the error function we would like to minimise, while \alpha is the learning rate. After deriving the gradient of J, we come to: <br>
\beta := \beta - \alpha (2/n) X^{T}(X \beta - y) <br>
The learning rate is a crucial part of this method, if it is too small, then convergence is too slow, if it is too large then it may overshoot the minimum and diverge away. <br>
If the cost function is convex, gradient descent will find the global minimum, which luckily,  linear regression IS a convex problem. <br>
#### Types of gradient descent
1. Batch gradient descent:
   - Uses all data, stable but slow 
3. Stochastic Gradient Descent:
   - Uses 1 data point at a time, which is noisy but fast 
3. Mini batch gradient descent:
   - Uses small batches of data 

## Python example: <br>
When we run the scikit.learn linear model, LinearRegression.fit(X,y), the code: <br>
1. augments X with a columns of 1s <br>
2. uses either SVD (Singular Value Decomposition) or QR decomposition to calculate (X^{T}X)^{-1}, (since this is too unstable directly)* <br>
The model stores coefficients and intercepts separately <br>

## Key assumptions
1. Linearity
   - Relationship is linear
3. Independence
   - Errors are not correlated
5. Homoscedasticity
   - Constant variance of errors
7. No multi-collinearity
   - No features are redundant 
9. Normal errors (for inference)

## Geometric Insight
Linear regression is the projection of y onto the column space of X, where X is a space, and linear regression finds the closest point in that space to y, where the closest points are the predictions 

## Where linear regression breaks
1. Non-linear relationships
2. Outliers
3. Correlated features  -> unstable coefficients













