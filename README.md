# Bayesian Hurdle Quantile Regressions

The R code is for the article "A Bayesian Hurdle Quantile Regression Model for Citation Analysis with Mass Points at Lower Values". This research focuses on two challenges for the analysis of citation counts by quantile regression (QR): discontinuity and substantial mass points at lower counts, such as zero, one, two, and three. In this research, an update of a Bayesian two-part Hurdle QR model was introduced to scientometrics to address these problems. The usefulness and applicability of the method were illustrated based on both simulated and real citation count data.

## Simulation stydy
For simulation study, samples with sizes of 500, 1000 and 3000 are simulated from continuous log-normal distribution (LN) with mean(2−0.2∗x1 +0∗x2 +ε) and standard deviation 0.4 where x1 ∼LN(2,2), x2 ∼ N (0.5, 0.5), and ε ∼ N (0, 1). The log-normal distribution was chosen because it approximates the typical distribution of citation counts. The floor function was used for the simulated values less than 4 to simulate substantial mass points at 0, 1, 2 and 3. The intercept value of 2 and the coefficient −0.2 of x1 were chosen so that approximately 45% of the data will be zeros and 75% of the data less than 3, similar to much citation count data. Bayesian QR and Bayesian two-part QR models with hurdle at 0, and with hurdle at 3 will be fitted. The objective is to compare Bayesian QR with the QR parts of the two-part models with hurdles at 0 and 3. In the following, for each sample size and for each quantile level

 1. The Bayesian QR model is fitted to the whole data. 
 2. Then the quantile level of the corresponding quantile value is found in the data in which the zeros are excluded and the Bayesian QR model is fitted, (i.e. the QR part of the two-part model with hurdle at 0).
 3.  Next, the quantile value corresponding to the quantile level is found in the data in which all substantial mass points (including 0,1,2, and 3) are removed and the Bayesian QR model is fitted for the corresponding quantile (this model is the QR part of the two-part model with hurdle at 3). 
 
 This process is repeated 100 times for each sample size, and for 4 specific quantiles of 0.75, 0.85, 0.90, and 0.95 (of the whole data) separately. For each combination
 1. The prediction error of each model
 2. The mean squared error of the parameters’ estimates (intercept excluded)
 3. The width of the credible intervals for both independent variables x1 and x2 
 are computed. The function ** jags ** from the R-library ** R2jags ** which is based on Gibbs sampler was used for MCMC computation corresponding to the Bayesian QR models. In this function, three chains will run. For each chain, 10000 iterations with burn-in 1000 and thinning number of 90 were considered. All the R code for this simulation is available in the file of ** R_Code_Simulation.r **.





