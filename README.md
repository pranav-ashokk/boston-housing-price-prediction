# Boston Housing Price Prediction
This project (among a couple others) is considered the 'Hello World' of machine learning. Throughout this project, I learned how to follow a standard machine learning project workflow for a supervised regression problem. However, this workflow is applicable to any type of machine learning problem.

## Workflow
1) Define the problem
2) Collect the Data
3) Clean/Process the Data
4) Data Exploration and Visualization
5) Develop a Model
6) Analyze the Model's Performance

## 1) Define the problem
I would like to find a way to realistically evaluate the price of a house in Boston based on specific observations. A supervised regression model would be ideal for this situation.

The model will be given various data (features) from houses that were sold in Boston. From this data, the model should then predict the selling price of a new house in the city before it is sold based on the various features it has. In this situation, the target feature is therefore the selling price of a house in Boston.

## 2) Collect the Data

## 3) Clean and Process the Data
In order to use the collected data in a supervised regression model, I first had to clean the dataset. I preprocessed the data as follows:

- I only used the features that I felt were the most essential ('RM', 'LSTAT', 'PTRATIO', and 'MEDV'). This helps avoid overfitting the data.

- I removed the data points that contained a 'MEDV' value of 50.0. These are likely censored/missing values or have been capped at this number.

- I created a function that finds outliers in the data. I found one outlier that was more than 4 standard deviations from the mean, and removed that data point entirely. This data point had a 'RM' value of 3.561.

- I scaled the prices of the houses by 21000 (multiplicatively) to adjust for 35 years of market inflation.

## 4) Data Exploration and Visualization
I calculated some basic statistics on the prices such as the minimum, maximum, mean, median, and standard deviation. 

![](https://i.ibb.co/cJmFsSp/boston-housing-5.png)

### Inferences and Assumptions
The fundamental use of data science is to help us test our inferences or assumptions that we have on a certain situation by looking into the data. Therefore, I wanted to come up with some assumptions on the features and the model in general before developing the model itself. 

- Houses with a higher 'RM' value (number of rooms), will likely have a higher 'MEDV' (price) value. This assumption would mean that 'RM' and 'MEDV' are directly proportional variables.

- Houses that have a lower 'LSTAT' value (lower class workers) will likely be worth more. If the people are higher class workers and made more money, they likely have a higher purchasing power, resulting in a more expensive home. This would mean that 'LSTAT' and 'MEDV' are inversely proportional variables.

- Lastly, houses with a lower 'PTRATIO' (less students to teachers ratio), will also likely be worth more. I am assuming this because an educational facility with more teachers to focus their attention on the students will likely be a hot spot for families who are looking for houses. This assumption would mean that 'PTRATIO' and 'MEDV' are inversely proportional variables.

To really visualize the data and help me gain insight into the data, I created both a pairplot and a correlation matrix. These plots helped me really connect the features to the target feature as well as how they work collecticely and independently to affect the target feature's outcome. 

### Pairplot
![](https://i.ibb.co/FHZhmgy/boston-housing-2.png)

### Correlation Matrix (Using a heat map)
![](https://i.ibb.co/9hprX5Q/boston-housing-2-1.png)

## 5) Develop a model
To measure the quality of the model, I first had to define a performance metric. For this project, I defined my performance metric as the coefficient of determination, otherwise known as R^2. 

The coefficient of determination is often very useful for regression analysis. The values for R^2 range from 0 to 1. An R^2 value of 0 means that there is no correlation between the predicted value from the model and the actual value. An R^2 value of 1 means that the predicted value from the model is the exact same as the actual value. The closer towards 1 the R^2 value is, the more accurate and "better" the model is.

I then split the data into training and testing subsets. I also shuffled the data into a random order when I split the data because this removes and bias in the ordering of the data. 

## 6) Analyze the Model's Performance
I used decision tree regression to create the models. This is an algorithm that continuosly splits and tests the the dataset until it reaches the final node (prediction). 

I plotted a few diferent learning curves for models with different 'max_depth' parameters and training set sizes. Changing these parameters essentially allowed me to observe how the model's complexity affects performance. It helped me distinguish between an overfitting model (high bias), an underfitting model (high variance), and a model that works very well (low bias and variance).

![](https://i.ibb.co/xswL0fp/boston-housing-4.png)

Then, I made a graph for a decision tree model that has been trained and validated on the training data using different maximum depths. There are two complexity curves - one for training and one for validation. The shaded regions represent the uncertainty/variance in the curve. 

![](https://i.ibb.co/ZVj2Bzv/boston-housing-1.png)


