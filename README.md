# Leicester-City-2015-16-Title-Winners-Monte-Carlo-Simulation-

## Technologies Used
- Jupyer Notebook (Python)
- soccerdata
- requests
- pandas
- numpy

## Description
This Project uses elo scores (obtained from ClubElo.com) to simulate the 2015/16 Premier League Season in which Leicester City beat the odds, winning the Premier League. Famously, bookmakers were offering odds at the start of the season of 5000/1 for Leicester to win the Premier League (implied probability ~ 0.02%).

In this project, I simulated the season 100,000 times to see how (un)likely Leicester winning the Premier League was. My model was quite a bit more generous to Leicester City, giving them title winning odds of ~0.131% (or 131/100,000). By no means, however, do I believe my model is better at predicting league table positions than the complex ones used in the gambling industry. 

## 1. 2015/16 Premier League Fixtures 
Obtained the fixture list for the 2015/16 Season using the Premier League's API. 

## 2. Elo scores of each PL team at the start of the season 
Obtained each Premier League team's elo score the day before the season started. 

## 3. Draw Probabilites 

### 3.2 Estimating Draw Function Parameters from Previous Seasons 
Estimated draw function parameters based on the previous 5 Premier League Seasons. 

Parameters: 
- Low-draw probability (the lowest draw probability that can occur)
- High-draw probability (the highest draw probability that can occur)
- Steepness (how quickly the function decays between these bounding probabilities)

The parameters were estimated by observing the rate at which draws occured for 'binned' elo differences. (e.g. opponents with a small elo difference, 0-50, drew at a rate of ~31%, whereas more unequal opponents, say an elo difference of 200-250, were less likely to draw, with a rate of ~22%) 

Based on these observed draw rates, a model was fit to the data, providing the optimal parameters for the function. 

### 3.3 Draw Probability Function for the model using parameter estimates
Draw probability function created using the paramters obtained previously. 

## 4. Elo functions
Functions: 
- Win Probability based on elo scores
- Single match simulation 
- Update elo scores based on simulated match outcome and expected outcome

(**NOTE:** in the single match simulation, a **_very_** rudimentary goals model was incoporated for the sole purpose of settling tie-breakers in the final table, where teams have the same number of wins and draws. The actual goal values should be largely ignored)

## 5. League Simulation(s)
Functions: 
- Simulate a single season
- Monte Carlo Simulation - Simulates the league thousands of times, recording the league winners after each iteration. 
