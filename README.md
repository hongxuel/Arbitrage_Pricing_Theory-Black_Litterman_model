# Arbitrage_Pricing_Theory-Black_Litterman_model    
I practiced Arbitrage Pricing Theory and Black-Litterman model using S&P500 stocks data, S&P500 index and US dollar index.  
## APT(Part1)  
a. Calculate historical factor monthly returns for the following factors based on Arbitrage Pricing Theory.  
&emsp;1. Equity market factor. Using S&P500 index return as equity market return proxy. (Data from SPX_DXY_MonthlyReturns)  
&emsp;2. US Dollar factor. Using DXY Index returns as proxy. (Data from SPX_DXY_MonthlyReturns)  
&emsp;3. Sector factor. (Note: I leave one sector out to make sure proper running of Fama Macbeth regression. I leave out the sector of UTIL.)  
&emsp;4. Size factor. At each month-end reconstitution date, I use the same company market cap data (column D on SP500Stocks) for simplicity. (Note: size exposure for a company should be sector neutral, i.e., the z-score of the log(mkt_cap) should be w.r.t. peer companies within the same sector.)   
b. Check for each factor their historical returns are significant or not (based on T-stat).  
c. Using the last month in the back-test, i.e., 12/31/2018.  
&emsp;1. All factor portfolios are long-short neutral portfolio, i.e., the total weights sum to 0.  
&emsp;2. For any factor portfolio, it has unit exposure to its own factor, but zero exposure to all other factors in the model.   
## BLM(Part2)  
From Part1, I have located 10 sector factor returns, i.e., 10 monthly return time series. I practice Black-Litterman model with the following assumptions:  
(1) For the 10 sector factors, equlibrium expected monthly returns (Pi) are assumed to equal historical average monthly returns.  
(2) Using historical monthly return covariance matrix. (the covariance matrix Sigma)  
(3) Uncertainty metric tau for the prior distribution of the factor expected returns equals 0.05.  
(4) Assuming I have the views as follows:  
&emsp;&emsp;View 1: Sector ENER will have return of 0.20% in next month.  
&emsp;&emsp;View 2: Sector FINA will outperform Sector INDU by 0.05% in next month.  
&emsp;&emsp;View 3: Sector INFT and Sector HLTH will outperform Sector REAL and Sector STPL by 0.30% in next month. (Assuming equal weighting on both long and short legs)  
5) Assuming view uncertainty for each view portfolio equals the historical variance of each view portfolio.(omega1=tau*p1*Sigma*p1')  
a. Without active views, given Pi (from 1) and Sigma (from 2), locate the optimal portfolio of the 10 sectors which has the highest expected return and at the same time its annualized volatility no greater than 10%.(Note: this is an opitmization problem with only one constraint on the total variance of the portfolio. Also notice that I need to transform the annualized vol to monthly vol.)  
b. Now I incorporate the active views on 4 using Black-Litterman model.  
&emsp;1. I show the updated factor expected return distribution and compare it with the original one, i.e., calculate nu, which is the update return vector; and (H^-1+Sigma), which is the updated covariance matrix.  
&emsp;2. Make observations on how active views impact updated returns.  
&emsp;3. Re-run the optimization as in a, but with the new return vector and covariance matrix. Compare the updated optimal portfolio (the weight vector) with the solution from a.
