# AI-driven solutions for the restaurant industry 

### Introduction

In the US alone, restaurants waste 25bn pounds of food every year before it reaches the consumers plate and independent restaurants are a large driver of this. This is crucial for an industry that operates with very low profit margins of 3% to 6% on average. 

### Project description
In this project we have partnered with Burnt (https://burnt.squarespace.com), whose mission is to help restaurants automate their back-of-house operational flow: recipe management, inventory forecasting, analysis and optimization of costs. In this project, we will use real-world time series data from restaurants to forecast the total revenue and menu item sales based on different factors such as day of the week, weather, holidays etc. This will help to optimize ordering decisions for maximum efficiency.

### Data Collection
The dataset provided by Burnt, consists on real-world sales data for restaurant 'XYZ' located in lower Manhattan, New York. We refer to this restaurant as 'XYZ' to maintain confidentiality. The columns are:
- Item Id: Identifyer the item sold (String)
- Item Name: Name of the item sold (String)
- Date: Date and timestamp the item was sold (datetime64)
- Category_id: Identifyier for the item Category (String)
- Quantity: Quantity sold (Integer) 
- Price: Price of item sold (Real)

### Restaurant analytics
Analysis of total revenue:
- Revenue consistently increases from Monday to Saturday, indicating higher customer activity as the week progresses.
- The majority of revenue is generated at night, followed by the afternoon, while mornings contribute the least.
- Spring is the most profitable season, accounting for 31.6% of total revenue, while summer and fall contribute roughly 23% each. Winter contributes with aroung 20% of total revenue.
- April and May of 2023 were the busiest months, refelcting peak sales activity.
<img width="911" alt="Screenshot 2025-03-03 at 1 17 01 PM" src="https://github.com/user-attachments/assets/5318b3f0-8f0f-4ed8-a26a-717c7501325b" />
  <img width="911" alt="Screenshot 2025-03-03 at 1 19 11 PM" src="https://github.com/user-attachments/assets/b2cdabe4-bf8d-42ea-9387-7008ae522953" />
<img width="918" alt="Screenshot 2025-03-03 at 1 19 32 PM" src="https://github.com/user-attachments/assets/deb84636-faf0-4473-85ea-182ea6c8aaed" />
<img width="922" alt="Screenshot 2025-03-03 at 1 19 23 PM" src="https://github.com/user-attachments/assets/5ca391ca-7909-4eb2-ad04-ac2765f8472d" />

Revenue breakdown by Category

The top revenue-generating categories are:
- Cocktails: 22.6% of total revenue
- Pasta dishes: 20.2%
- Wines: 15.5%
- Appetizers: 10.1%
<img width="754" alt="Screenshot 2025-03-03 at 1 22 53 PM" src="https://github.com/user-attachments/assets/1d6d62e4-eee4-4d08-b098-57df169f6b4f" />

### Modelling of total daily sales
For our modelling we will use SARIMA (Seasonal AutoRegressive Integrated Moving Average) model. We first identified our data displays weekly seasonality. The optimal model parameters where found by doing a grid search and selecting those that lead to the lowest AIC (Akaike Information Criterion). The best model found was ARIMA(5,1,0)(2,0,2)[7] with AIC=5033.657 .


<img width="1168" alt="Screenshot 2025-03-03 at 1 46 04 PM" src="https://github.com/user-attachments/assets/ae9b913c-9503-48bb-bfdd-2faacf79c6ab" />

<img width="1163" alt="Screenshot 2025-03-03 at 1 48 09 PM" src="https://github.com/user-attachments/assets/60eb42cd-5b70-4961-b228-e08f1e836c92" />

<img width="1150" alt="Screenshot 2025-03-03 at 1 48 32 PM" src="https://github.com/user-attachments/assets/85ba3bc0-cc44-4a69-a630-31a36a5e9719" />

### Feature Selection and Engineering
We considered different features:
- Weather features: average temperature on the day and whether it rained () or not (). Obtained through the meteostat API.
- Weekend indicator variable: Not a weekend (0) or weekend (1).
- Holiday indicator variable: Not a holiday (0) or a holiday (1).
We assessed the correlation of these features with the quantity sold. For example there is a strong correlation between weekend and quantity sold for Latte.

<img width="776" alt="Screenshot 2025-03-03 at 2 25 39 PM" src="https://github.com/user-attachments/assets/e206bd2c-a6d9-44ea-90f7-3dbaa0b61e51" />




### Movelling of menu items
For the modelling of menu items we will first perform a test to differentiate between items that show seaosnlity and those that do not.
### Conclusions and future directions

  
