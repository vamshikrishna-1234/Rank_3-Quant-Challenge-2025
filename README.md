# Rank_3-Quant-Challenge-2025
My work in the Quant Challenge 2025 securing global Rank 3, organized in collaboration with Five Rings

 We performed a careful, principled experimentation, Iterative refinements rather than "black box" tweaking which led us to a good R2 score, Detailed Methodology of our work:
 
 QR_Data_Analysis.ipynb:
 1)We first started with an in-depth Exploratory Data Analysis, there was not much pre-processing required except the null values in O and P column - we used forward fill to fill the null values, since the values may be event-driven or sentiment data, which will logically change when a news comes up, thus maintaining logical temporal continuity without introducing bias. 
 
 2)We plotted features vs targets and prepared a list of the correlations between these targets and features, we decided to go for 2 different models since correlations of Y1 and Y2 are distinct with different features, (Y1 is most correlated to G,J,H columns and Y2 is most correlated to columns A,K,D). Also we discovered that tree based model can capture the patterns and non-linearities well because the plots seemed to be formed based on conditions/decisions on the feature set.
 
 QR_Randomforest_Tree_Performance_checker.ipynb
 3)We started with a simple Random forest Regressor and found that its performing very well compared to LSTM, RNN and Neural Networks, so we tried all tree based models like XGBoost, LGBM, ExtraTree Regressor etc, found that LGBM is giving best 3-cross validation score on the train data.
 
 Part1_Final_Submission_QR_Track.ipynb
 4)So, we performed a grid search on a parameter list of a two LGBM models (one for Y1 and other for Y2) using 3-cross validation score and maintaining early stopping on each fold, thus we found the best parameters which gave a very good R2 score for two LGBM models, this took us to the Top3 of the leaderboard.
 
 QR_Extensive_manual_tuning.ipynb, Part2_of_Final_Submission.ipynb:
 5)We performed manual tuning on the parameters given by the grid search to further improve the performance, so we introduced L1 and L2 regularization here to get the best parameters without overfitting on the train data, we never did a 80/20 split for validation since it only generalizes the model parameters to 20% of the train data and may over fit on it, we instead used 3-cross validation score to not overfit the model on any part of the train set.
