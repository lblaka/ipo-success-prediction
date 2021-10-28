# IPO Success Prediction
By: Lorela Blaka


# Background


An IPO is when a private company transitions to public by offering shares to the public market. Companies looking to IPO must hire investment banks, who act as brokers during IPO process, to help guage demand, price, and sell the stock to investors. These companies must also meet the requirements by the SEC to hold an IPO. 

IPOs are a great opportunity for growth as it allows a company to raise capital from public investors much faster and at greater volumes. 


# Motivation
Normally, hot IPOs are not that telling of the "success" of a company down the line. It's mainly an indication of the short term hype that was built around it. Consequently, there tends to be a pricing / trading disparity with these types of stocks. To mitigate this problem, is there a way to make IPO stock success more predictable? 


# Data  
The data comes from Yahoo Finance, IPO Scoop, and Warrington College of Business. Roughly 3,800 traditional IPOs were analyzed for the first model and 1,500 for the second model. 


# Methods 

IPO success is defined as meeting one of these two requirements:
1. Enterprise value to revenue ratio (top 25th percentile or above 4.27x)
2. Gross margin (top ~80th percentile or above 65%)


First Model Features:
1. Sector:  is it Healthcare, Financial Services, etc.?
2. Rollup: is the company a result of the merge of smaller companies?
3. Dual: is it a multiple-share class IPO?
4. VC Backed: is it VC backed? 
5. Internet: is it a tech IPO?
6. Years to IPO: difference between founding year and IPO year
7. Opening day performance: percentage difference between opening price and closing price on the IPO day

Second Model Features:
<br> ..include all first model features and:
<br> 8. Month 7 performance: average percentage difference between opening prices and closing prices of month 7

This is a picture of the data set, and how the data sources were combined: 

<img width="815" alt="data_outline" src="https://user-images.githubusercontent.com/59107548/139172469-e1ed96b5-413e-4db5-997f-49471bd2ce03.png">



# Results

Model 1 Results: 
The Random Forest Model was accurate at predicting postives (successes) 77% of the time: 

![model1](https://user-images.githubusercontent.com/59107548/139172606-c3d5e797-a978-4555-952e-64f5beed3b36.png)

Model 2 Results: 
The XGBoost Model was accurate at predicting postives (successes) 77% of the time: 

![model2](https://user-images.githubusercontent.com/59107548/139172623-ff6b4bda-debb-45e5-845e-0fd03547a89f.png)

# Conclusion & Future Steps
Predicting IPO success is difficult but not impossible. These models have some level of predictive power to prove that. However, there are definitely ways to improve this project which include: 

Expand dataset by features and rows
<br> 1. Enhance features to represent “timing” better
<br> 2. Add investment managers feature
<br>Expand to international companies 
<br>Redefine Success to include more consistent timeline




