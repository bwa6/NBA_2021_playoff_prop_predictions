# NBA_2021_playoff_prop_predictions
predicting how many points an NBA player will score in a game

With the NBA playoffs set to begin on 5-18-21, I decided to develop an algorithm to predict how many points a player will score in a game.  I like to place prop bets on 'monkey knife fight,' which is a betting website for prop bets (i.e. betting on player stats).  I decided to take advantage of my improved machine learning skillset to develop an algorithm to make effective predictions.

In the accompanying Jupyter Notebook, NBA predictions.ipynb, I applied web scraping to basketballreference.com to collect stats on every player in every game during the 2021 season (nearly 21,000 rows of data).  I also scraped the same website to get data on team stats for the 2021 season.  I used all of this data to generate a pandas data frame on stats in four categories:
1) the team's stats averaged over the last week,
2) the opponent's stats averaged over the last week,
3) the player's stats averaged over the last week,
4) the player's stats averaged over the entire season up until the game of interest.

Using these stats (100 features in total), I applied a regression analysis using ridge, lasso, support vector, and random forest regression.  I combined these four models into a voting regressor to get a final prediction.  In this case, I am interested in predicting how many points a player will score in a game.

I could not find datasets on over/under lines for how many points individual players would score each game, so it is difficult to assess the accuracy of my model.  However, I will look at the over/under lines at monkeyknifefight.com every day throughout the playoffs to collect data over time to compare to my model prediction.

For example, if the over/under for Lebron James is scoring 26 points, and my model predicts 29 points, I would choose the 'over.'  I will bet fake money on the prop bets in which my model is most confident (i.e. largest discrepancies between over/under line and model prediction) to determine the accuracy of my model.  To determine how much to bet, I will get the approximately normal distribution of the difference between actual scores and predicted scores on my test data.  I will measure the probability under the cumulative distribution function at the point where monkey knife fight has set the over/under line to determine the probability of successfully winning the bet.  Since you have to correctly predict a pair of over/unders, I will multiply the probability of correct predictions for each over/under to get the probability of winning the whole bet.  With a payout of 3x, I need to be correct 33% of the time to break even, so I will only bet when the probability of winning is greater than 0.33 and bet more money as the probability increases according to the formula 800*p^4 where p is the proability of winning the bet.

Stay tuned for updates to this README to learn how my model performed. I attached the predictions for the first four games of the playoffs in the excel file called playoff_prop_bets.  I will fill this file out over the course of the playoffs to determine whether the model can help me win fake money on monkey knife fight.

The purpose of this project is to showcase my skills in web scraping, data cleaning, model development, and (eventually) model assessment.
