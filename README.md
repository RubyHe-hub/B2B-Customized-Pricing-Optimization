# B2B-Customized-Pricing-Optimization
Proper discounts could attract more customers, increase sales, and thus increase total revenue. In this case, we would like to optimize the discounts for a B2B company to increase the total expected revenue. The dataset we used contains 1505 records, including information about product type, discount amount, promotion time periods etc. Models are trained on the first 1200 records and the rest is used for evaluation of our result. The expected revenue is calculated by the formula below.

R=Prob(Y=1│p,d)×(p-d)

p refers to the price of the product, d represents the discount amount and Prob(Y=1|p,d) is the conversion rate on the basis of the specified price and discount. According to the formula, it’s obvious that two factors should be analyzed. One is the conversion rate, the other is the discount amount. 

We first estimated the conversion rate by applying the logit model to predict whether the promotion would lead to loss or profit. In this prediction, seven variables are analyzed, including discount, original price, new logo and four product type indicators. Then conversion rate is calculated based on the result we got above. Next, using these results, discount amount is optimized on to maximize total revenue.
However, regressing on the whole dataset regardless of their types may lead to inaccurate prediction of conversion rate. To test if conversion rates are significantly different across different types, we did chi-square tests. Results show that conversion rate is highly related to types. Thus, we decided to run regression on each category. Because of the exceptionally limited records of direct-cloud products, instead of regressing on four types, we decided to regress on pairs: Partner vs. Direct, Cloud vs On-prem, New Logo vs. Old Logo.
The evaluation metrics of the optimization is the expected revenue increase rate. The formula is as below. 

Expected revenue increase rate=  (Revenue after optimization)/(Actual revenue)  ×100%



We also checked time series and found the conversion rate follows the same pattern, which is called the ‘end-of-the-quarter’ effect. 
