## Introduction

League of Legends is one of the most popular games of all time, with millions of players engaging in competitive matches daily. Each game unfolds uniquely, but certain in-game events and conditions can influence how long a match will last. Factors like gold differences, champion selections, early-game objectives, and team compositions all play a role in determining whether a game ends quickly or stretches into the late stages.
In this project, we aim to analyze key variables and their impact on game length. By leveraging data from past matches, we will identify patterns and build predictive models to estimate how long a given game is likely to last. Understanding these correlations can provide strategic insights for players and enhance overall game analysis.

## lol dataframe

This is the cleaned dataframe after removing unnecessary columns that is not relevent to the driving question

| Column           | Description                                     |
| ---------------- | ----------------------------------------------- |
| `'gameid'`       | The gameid for a specific game                  |
| `'golddiffat_'`  | The gold difference at \_ minutes               |
| `'xpdiffat_'`    | The experience difference at \_ minutes         |
| `'csdoffat_'`    | The cs difference at \_ minutes                 |
| `'gamelength'`   | The length of the game in minutes               |
| `'league'`       | The league's name which the game took place     |
| `'totalkillsat_` | total amount of kills in the game at \_ minutes |

<p></p>

## Univariable plot

This histogram shows the distribution of all the gamelength in minutes in the dataset.
We can see that the majority of the games is between 28-32 minutes and the graph is right skewed meaning there are less games that last longer.

<iframe
  src="assets/plots/uni1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Bivariable plot

### plot 1

This graph shows the relationship between game length in minutes and experience difference at 15 minutes between both teams. We can see that there is a negative linear correlation between the two variables.

<iframe
  src="assets/plots/bi.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### plot 2

This graph shows the relationship between game length in minutes and gold difference at the 15 minute mark. We can see that there is somewhat of a negative linear correlation similar to the plot above.

<iframe
  src="assets/plots/bi2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### plot 3

This graph shows the relationship between game length in minutes and cs difference at the 15 minute mark. We can also see that there is a visible negative linear correlation between the two variables.

<iframe
  src="assets/plots/bi3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>\

### pivot table

This table shows the average difference in stats at the 25 min mark for each region that made it to the 2024 worlds, except LPL which do not have complete data.

| League | CS Diff @25 | Gold Diff@25 | XP Diff@25 |
| ------ | ----------- | ------------ | ---------- |
| LCK    | 49.42       | 4963.75      | 5322.68    |
| LCS    | 46.34       | 4724.95      | 4963.20    |
| LEC    | 51.41       | 4711.63      | 5202.10    |
| PCS    | 54.99       | 5905.65      | 5609.44    |
| PCS    | 54.99       | 5905.65      | 5609.44    |
| CBLOL  | 40.82       | 4618.18      | 4900.09    |
