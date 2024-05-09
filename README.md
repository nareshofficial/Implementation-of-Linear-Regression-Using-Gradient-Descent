# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required library and read the dataframe.

2.Write a function computeCost to generate the cost function.

3.Perform iterations og gradient steps with learning rate.

4.Plot the Cost function using Gradient Descent and generate the required graph.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: NARESH
RegisterNumber:  212223040127
*/
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data=pd.read_csv("ex1.txt",header=None)
plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def computeCost(X,y,theta):
    m=len(y) 
    h=X.dot(theta) 
    square_err=(h-y)**2
    return 1/(2*m)*np.sum(square_err) 

data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))
computeCost(X,y,theta) 

def gradientDescent(X,y,theta,alpha,num_iters):
    m=len(y)
    J_history=[] #empty list
    for i in range(num_iters):
        predictions=X.dot(theta)
        error=np.dot(X.transpose(),(predictions-y))
        descent=alpha*(1/m)*error
        theta-=descent
        J_history.append(computeCost(X,y,theta))
    return theta,J_history

theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1")

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Gradient Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def predict(x,theta):
    predictions=np.dot(theta.transpose(),x)
    return predictions[0]

predict1=predict(np.array([1,3.5]),theta)*10000
print("For Population = 35000, we predict a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("For Population = 70000, we predict a profit of $"+str(round(predict2,0)))
```
## Output:
PROFILE PREDICTION
![308782105-5d6e3ac5-f8b1-4e73-b433-6697f51f71bc](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/3fd4744a-cce2-4b06-a67c-5d75edc7a961)

Function:
![308782233-0faf5afd-fa49-4d20-b7e5-5ad223278a9a](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/5fd054e0-09fc-4a76-a408-19ef48d7c4c3)

Gradient descent:
![308783411-74811aed-d411-423c-8d1f-5b5e4ca2cbb9](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/4595d750-ea24-4b9f-9ef6-f07d50863dd2)

cost function using gradient descent:
![308782429-e6873033-1c67-4b0a-87d7-ec6d6643e61b](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/ca537586-f65f-49d6-8fd0-4b72b4b87169)

linear regression using profile prediction:
![308782535-95675739-0f42-4f8c-b660-8ee7c40afef4](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/fffd888c-cac3-4a41-8b16-5bc340464f15)

profile presiction for the population of 35000:
![308782655-ac1e96c6-b4e3-4216-8a60-877e6f9ff5d0](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/17ec5df0-03e8-428b-998d-0917605f3cf4)

##profile prediction for the population of 70000:
![308782822-2d0918f6-11d2-441f-80f9-04baa1772352](https://github.com/nareshofficial/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/155141830/a03023c8-2bdc-443e-8441-f1d8ca5225da)







## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
