# IPO Success Prediction
By: Lorela Blaka


# Background


An IPO is when a private company transitions to public by offering shares to the public market. Companies looking to IPO must hire investment banks, who act as brokers during the IPO process, to help guage demand, price, and sell the stock to investors. These companies must also meet the requirements by the SEC to hold an IPO. 

IPOs are a great opportunity for growth as it allows a company to raise capital from public investors much faster and at greater volumes. 


# Motivation
Normally, hot IPOs are not that telling of the "success" of a company down the line. The scatterplot below shows the weak relationship between opening day performance and average month 7 performance. Hot IPOs are mainly an indication of the short term hype that was built around it at the time of the first issue. Consequently, there tends to be a pricing / trading disparity with these types of stocks. To mitigate this problem, is there a way to make IPO stock success more predictable? 

![download](https://user-images.githubusercontent.com/59107548/139280040-e9b78f4a-69e4-4afd-a5dc-c48c63c584a5.png)


# Data  
The data comes from Yahoo Finance, IPO Scoop, and Warrington College of Business. Roughly 3,800 traditional IPOs were analyzed for the first model and 1,500 for the second model. 


# Methods 


IPO success (dependent variable) is defined as meeting one of these two requirements:
1. Enterprise value to revenue ratio (top 25th percentile or above 4.27x)
2. Gross margin (top ~80th percentile or above 65%)

The previous definition of success was defined by opening day performance. It was later changed to consider company financials, since a higher positive change of opening and closing price can indicate IPO underpricing, which is an underwriter's strategy for increasing their own returns, not the company’s. 


Also  a major reason a company goes public is to raise capital from public investors much faster and at greater volumes. This should directly positively impact metrics like the enterprise value to revenue ratio and gross margin.

Below are the sectors ranked by success based on this definition: 
<img width="782" alt="Screen Shot 2021-10-28 at 10 49 13 AM" src="https://user-images.githubusercontent.com/59107548/139280722-6c373da2-4d78-4d36-b7ba-97b739ba2542.png">

First Model Features:
1. Sector:  is it Healthcare, Financial Services, etc.?
2. Rollup: is the company a result of the merge of smaller companies?
3. Dual: is it a multiple-share class IPO?
4. VC Backed: is it VC backed? 
5. Internet: is it a tech IPO?
6. Years to IPO: difference between founding year and IPO year
7. Opening day performance: percentage difference between opening price and closing price on the IPO day

Second Model Features:
1. All First Model features
2. Month 7 performance: average percentage difference between opening prices and closing prices of month 7


This is a visual representation of the data set, and how the data sources were combined: 

<img width="815" alt="data_outline" src="https://user-images.githubusercontent.com/59107548/139172469-e1ed96b5-413e-4db5-997f-49471bd2ce03.png">

The Removed data included only SEC data, and was removed because the dataset reduced to only a few hundred rows when merging the SEC data. 


# Results

As aforementioned, the difference between my two models is Model 2 includes Month 7 Avg Change. For each dataset, I ran a Gridsearch for both Random Forest and XGBoost classifiers to find the optimal hyper parameters. Tested the hyper parameters, and found that Random Forest performed better for the first dataset, and XGBoost performed better for the second dataset. 

For model validation, I focused on how precise my model was at predicting successes our of the total amount of times it predicted successes (macro precision score). 

Model 1 Results: 
On the unseen data, the Random Forest Model was accurate at predicting postives (successes) 75.4% of the time: 

![model1](https://user-images.githubusercontent.com/59107548/139172606-c3d5e797-a978-4555-952e-64f5beed3b36.png)

Model 2 Results: 
On the unseen data, the XGBoost Model was accurate at predicting postives (successes) 62.9% of the time: 

![model2](https://user-images.githubusercontent.com/59107548/139172623-ff6b4bda-debb-45e5-845e-0fd03547a89f.png)

# Conclusion & Future Steps
Predicting IPO success is difficult but not impossible. These models have some level of predictive power to prove that. However, there are definitely ways to improve this project. First and foremost, expanding the dataset to increase model complexity is needed -- both at the row level and feature level. Previous studies have proved that the timing of an IPO and geopolitical factors have great impact on IPO success. Features to represent this attribute might improve the model. Also, adding an investment managers categorical column might improve the model as well, since different investment managers exceute IPOs differently. Another consideration is to expand the dataset to include international companies. This would be a much later iteration of the project however. Lastly, redefining success to include a more consistent timeline is also important. While the definition is clear in this project; this data set includes older IPOs, but defines their success based off of recent financial history. This was the tradeoff for including more rows in the model.  

