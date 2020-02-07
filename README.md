# WOE-and-LR
Traditional Credit Scoring/Underwriting Model consisits of with Information Value (IV), Weight of Evidence (WOE), Logistic Regression(LR)

In the big data era, one of the major challenging is to deal with massive features. In subprime financial market, thousands of variables are collected from credit bureau like TransUnion, Experian, Equifax, and etc. The raw datasets usually contain 1000 variables to 7000 variables. 

Traditional credit scoring using information value to select variables, it can be improved through introducing machine learning based feature selection methods. The optimal binning strategies for information value are impossible for thousands of varaibles.  Our proposed method has been validated in the real credit data like personal loan and auto loan. It boosts the KS performance 30% on average compared to traditional models. 

Due to the strictly requirement if regulation and interpretability, we only use gradient boost tree in feature selection, we believe the excellent feature engineering can achieve similar performance with gradient boost tree by using logistic regression. 

The purpose of this repository is to create a pipeline of python codes including data preprocessing, feature selection, feature engineering, modeling, scorecard and evaluation. 


1. Data Preprocessing includes a variety of statistical analysis, e.g. Univariate analysis, Bi-variate analysis, distribution 

2. Feature Selection: LightGBM, Xgboost, CatBoost. We 
    We only recommend CatBoost when there are many categorical variables since it takes long time to run on CPU. The author claimed it run much faster on GPU but I never have chance to validate it. Hyperparameter: Bayesian Optimization

3. Feature Engineering: OneHotEncoder, missing value imputation, Weight of Evidence, Special value. 
    special value cause significant shift in logistic regression. e.g. Experian used the largest number as special value, like 96, 97, 98,99 or 996,997,998, 999. However, the special value usually represents no trades or no activities which is similar to value 0.  
    missing value: we have seen performance of missing values change over years since these bureaus can collect more data for users. 
    
4. Modeling: Logistic Regression with regularization (e.g. L1 and L2)
   Stepwise LR with Backward Sequential Feature Selection

5. Scorecard: user-defined parameters: Factor, pdo (Points to double the odds), offset

6. Evaluation: KS and AUC, correlation, P value and VIF (Variance inflation factors). They are old-school statistics but your boss will like them
