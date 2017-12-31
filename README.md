# Machine-Learning-Notes-
Notes form Machine Learning 
Regularized Linear Regression

Note: [8:43 - It is said that X is non-invertible if m ≤ n. The correct statement should be that X is non-invertible if m < n, and may be non-invertible if m = n.

We can apply regularization to both linear regression and logistic regression. We will approach linear regression first.

Gradient Descent

We will modify our gradient descent function to separate out θ0 from the rest of the parameters because we do not want to penalize θ0.

Repeat {    θ0:=θ0−α 1m ∑i=1m(hθ(x(i))−y(i))x(i)0    θj:=θj−α [(1m ∑i=1m(hθ(x(i))−y(i))x(i)j)+λmθj]}          j∈{1,2...n}
The term λmθj performs our regularization. With some manipulation our update rule can also be represented as:

θj:=θj(1−αλm)−α1m∑mi=1(hθ(x(i))−y(i))x(i)j
The first term in the above equation, 1−αλm will always be less than 1. Intuitively you can see it as reducing the value of θj by some amount on every update. Notice that the second term is now exactly the same as it was before.

Normal Equation

Now let's approach regularization using the alternate method of the non-iterative normal equation.

To add in regularization, the equation is the same as our original, except that we add another term inside the parentheses:

θ=(XTX+λ⋅L)−1XTywhere  L=⎡⎣⎢⎢⎢⎢⎢⎢011⋱1⎤⎦⎥⎥⎥⎥⎥⎥
L is a matrix with 0 at the top left and 1's down the diagonal, with 0's everywhere else. It should have dimension (n+1)×(n+1). Intuitively, this is the identity matrix (though we are not including x0), multiplied with a single real number λ.

Recall that if m < n, then XTX is non-invertible. However, when we add the term λ⋅L, then XTX + λ⋅L becomes invertible.
