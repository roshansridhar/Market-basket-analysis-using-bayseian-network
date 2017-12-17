# Market basket analysis using bayseian network
Using Instacart data on customer orders over time to predict which previously purchased products will be in a user’s next order. 
Data: https://www.instacart.com/datasets/grocery-shopping-2017

## Topic: Repeat buyer prediction for E-Commerce
 
#### Problem Statement: 
Create a Bayesian Belief network to analyze the behavior of the customers, and predict their next purchase, along with the order in which they are bought in that transaction
 
#### Data: 
We used “The Instacart Online Grocery Shopping Dataset 2017” dataset for our project. The dataset consists of 75,000 users and 49,000 products. For each product, we are given the aisle and department in which they are located. For each user, we are given the history of their past ‘x’ transactions (where x can be anywhere between 5 and 100), the order in which each product is purchased in those transactions, and whether a particular product is reordered or not by that particular user.


#### Methodology: 
Our goal is to predict  

![alt text](https://latex.codecogs.com/gif.latex?P%20%28reordered%20%3D%201%20%7C%20e%29)  

Where reordered = 1 indicates that the product was reordered, given e. The random variable ‘e’ is the event where  
Add to cart order = ‘atco1’  
Aisle = ‘aisle_id’  
Number of times reordered = ‘recount_c’  

![alt text](https://latex.codecogs.com/gif.latex?p%28e%5C%20%7C%5C%20reordered%29%5C%20%3D)
![alt text](https://latex.codecogs.com/gif.latex?p%28atco1%5C%20%7C%5C%20reordered%29%5C%20*%5C%20p%28aisle%5C_id%5C%20%7C%5C%20reordered%2C%5C%20atco1%29%5C%20*%5C%20p%28recount%5C%20%7C%5C%20reordered%2C%5C%20atco1%29)  
               
![alt text](https://latex.codecogs.com/gif.latex?p%28e%5C%20%7C%5C%20reordered%29%5C%20%3D%5C%20atco%5C_fac%5C_p%5C%20*%5C%20aisle%5C_fac%5C_p%5C%20*%5C%20recount%5C_fac%5C_p)   

Using Bayes’ Theorem, we calculate the posterior probability using:  
![alt text](https://latex.codecogs.com/gif.latex?p%28reordered%5C%20%7C%5C%20e%29%5C%20%3D%5C%20%5Cfrac%7Bp%28e%5C%20%7C%5C%20reordered%29%7D%7Bp%28e%29%7D%5C%20*%5C%20p%28reordered%29)

We can replace the equality with a proportionality with the following formula:  
![alt text](https://latex.codecogs.com/gif.latex?p%28reordered%5C%20%7C%5C%20e%29%5C%20%5Cpropto%20%5C%20p%28e%5C%20%7C%5C%20reordered%29%5C%20*%5C%20p%28reordered%29)  

Once the posterior is calculated, it becomes our new prior.   
![alt text](https://latex.codecogs.com/gif.latex?Posterior%5C%20%5Cpropto%5C%20p%28e%5C%20%7C%5C%20reordered%29%5C%20*%5C%20Prior)  

For our first order, we get the prior calculating an informed prior using the formula:  
![alt text](https://latex.codecogs.com/gif.latex?Prior%5C%20%3D%5C%20%5Cfrac%7BNumber%5C%20of%5C%20reorders%7D%7BNumber%5C%20of%5C%20orders%7D)
