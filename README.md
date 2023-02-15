# Gradient-Descent-and-Stichastic-Gradient-Descent

Before the implementation of these two methods it's better to get familiar with their algorithms:

## **Gradient Descent**
Gradient descent (GD) is an iterative first-order optimisation algorithm used to find a local minimum/maximum of a given function. This method is commonly used in machine learning (ML) and deep learning(DL) to minimise a cost/loss function (e.g. in a linear regression). Due to its importance and ease of implementation, this algorithm is usually taught at the beginning of almost all machine learning courses.

Gradient descent algorithm does not work for all functions. There are two specific requirements. A function has to be: **differentiable** and **convex**.

The steps of the algorithm are:

1. Find the slope of the objective function with respect to each parameter/feature. In other words, compute the gradient of the function.

2. Pick a random initial value for the parameters. 

3. Update the gradient function by plugging in the parameter values.

4. Calculate the step sizes for each feature as : step size = gradient * learning rate.

5. Calculate the new parameters as : new params = old params - step size

6. Repeat steps 3 to 5 until gradient is almost 0.

### Learning Rate
The “learning rate” mentioned above is a flexible parameter which heavily influences the convergence of the algorithm. Larger learning rates make the algorithm take huge steps down the slope and it might jump across the minimum point thereby missing it. So, it is always good to stick to low learning rate such as 0.01. It can also be mathematically shown that gradient descent algorithm takes larger steps down the slope if the starting point is high above and takes baby steps as it reaches closer to the destination to be careful not to miss it and also be quick enough.

## **Stochastic Gradient Descent**
There are a few downsides of the gradient descent algorithm. We need to take a closer look at the amount of computation we make for each iteration of the algorithm.

Say we have 10,000 data points and 10 features. The sum of squared residuals consists of as many terms as there are data points, so 10000 terms in our case. We need to compute the derivative of this function with respect to each of the features, so in effect we will be doing 10000 * 10 = 100,000 computations per iteration. It is common to take 1000 iterations, in effect we have 100,000 * 1000 = 100000000 computations to complete the algorithm. That is pretty much an overhead and hence gradient descent is slow on huge data.

Stochastic gradient descent comes to our rescue!! “Stochastic”, in plain terms means “random”. SGD randomly picks one data point from the whole data set at each iteration to reduce the computations enormously. It is also common to sample a small number of data points instead of just one point at each step and that is called “mini-batch” gradient descent. Mini-batch tries to strike a balance between the goodness of gradient descent and speed of SGD.



### Goal: 
We aim to implement a binary classifier which can recognize whether a digit is '2' or '7'. We label digit '7' to Y=1 and for digit '2' we have Y=-1. By this assumption that we have two classes we can use the below function as cost function:

![image](https://user-images.githubusercontent.com/125180530/219015288-94255f23-2e4f-4b7d-8a85-d78b3c4c2736.png)

By using the following assumption we can calculate gradients:

![image](https://user-images.githubusercontent.com/125180530/219015547-b720adf3-bb43-49ff-9bec-a463eea28c9f.png)

* Now consider zero for initial values of 'w' and 'b'. For both train and test data we plot the cost function values versus iterations for different values of learning rates. 

* Considering the following formula, we can calculate the predicted label of a data and compare it to its actual label. Then, we can report accuracy values for both train and test data. 

* Now we want to implement stochastic gradient descent. So, for better comparison between GD and SGD, it's better to repeat both previous parts for batch size = 1 and batch size = 100. 

### Conclusion
SGD is faster than GD because the process of updating parameters is done with a fewer number of data. For example, in this project we update parameters with 1 data and 100 data although in gradient descent we use all data to update 'w' and 'b'. It's worth saying that updating parameters with a number of data can result in greater varaince. This can culminate in fluctuations in J function to reach its minimum value which is observable in the plots in the code file. 
