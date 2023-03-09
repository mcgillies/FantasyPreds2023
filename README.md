# FantasyPreds2023
MLB fantasy predictions for the 2023 season
# Full Rankings [here](2023FantasyBaseballRankings.csv)
## Batter Rankings [here](HitterRankings.csv)
## Pitcher Rankings [here](PitcherRankings.csv)

In this exploration I will use metrics and advanced statistics in order to predict the fantasy statistics of MLB players in the 2023 season. I have utilized multiple datasets from baseball savant (https://baseballsavant.mlb.com) and Razzball (https://razzball.com/) in order to complete this analysis. Due to the fact that this model utilizes primarily metrics and not true results, the predicitons will be biased towards players with advanced "tools", such as exit velocity and strikeout rate. Therefore the predicitions will likely represent the true ceiling of each player, with regression likely. The primary data was constructed by taking metrics and advanced statistics from 2018-2021 and per game fantasy scores from 2019-2022 for qualified batters. The "year" column represents the year that the fantasy average occurred, and the metrics in each row are representative of the year prior to what the data indicates. This is done in order to utilize metrics and statistics from 2022 in order to predict fantasy points in 2023. The model will be created to predict fantasy points per game (hitters) or fantasy points per inning pitched (pitchers). The data will be preprocessed and applied to multiple types of regression models to obtain the model and parameters with the most accurate predictions. Once the model is complete and is able to effectively predict the fantasy score per game, I will apply predictions for number of games played / innings pitched in 2023 to compute an entire season prediction. Predictions for games played / innings pitched will be taken from Razzball. Team factors will also be applied to account for the differentiating results in different ballparks. Pitcher rankings are incoming!

### Pitcher Rankings
The pitcher projections will consist of training a regression model to predict the fantasy score per innings for all categories of pitchers (starters, relievers and closers). However fantasy points per inning will be calculated solely on individual statistics (Hits, Walks, Strikeouts, Innings Pitched and Earned Runs), as team related statistics (Wins, Losses, Saves, Holds) are very situation dependent and should not be used in future predictions. In order to account for these team related statistics, I will utilize Razzball's predictions for wins, losses, saves and holds and add these predictions into the results from the model. Once again team factor will be calculated and applied by standardizing team performance. This will account for team performance and opportunities for wins, losses, etc. along with accounting for the impact of ballpark dimensions and climate. Innings pitched for 2023 will also be taken from Razzball and applied to the per inning predictions to produce the final predictions for the 2023 season.


#### Team Factor
##### Batters [here](TeamFactor.ipynb):
Data from baseball savant and razzball is used to calculate "Team factor". Team factor consists of the average fantasy points per game for each team from 2022 standardized to a normal distribution. Abnormalities in the usual standardization of a Normal(0,1) distribution are in place in order to prevent extreme transformation on the final prediction, as the standard deviation is decreased significantly and the mean is centered at 1. Team factor is simply meant to allow for a slight influence on the team (surrounding players and park) that each player is on for the final predictions. Changes to the Blue Jays, Tigers and Mets ballpark dimensions are accounted for with an approximate estimate on how these changes will impact offensive production.

##### Pitchers [here](PitchTeamFactor.ipynb):
Similarily to team factor calculations for batters, pitcher team factor will standardize the average fantasy points per inning in 2022 to a normal distribution with mean at 1 and a very small standard deviation (~0.1). Unlike the model creation, fantasy points per inning will include team-based statistics such as wins, losses, saves and holds. These statistics are actually a crucial aspect of team factor, as we would like to account for the difference in opportunities to accumulate these statistics between teams. Once again, changes to the Blue Jays, Tigers and Mets ballpark dimensions are accounted for with an approximate estimate on how these changes will impact offensive production, and in turn pitching production. 
