# Introduction

League of Legends is one of the most popular games of all time, with millions of players engaging in competitive matches daily. Each game unfolds uniquely, but certain in-game events and conditions can influence how long a match will last. Factors like gold differences, champion selections, early-game objectives, and team compositions all play a role in determining whether a game ends quickly or stretches into the late stages.
In this project, we aim to analyze key variables and their impact on game length. By leveraging data from past matches, we will identify patterns and build predictive models to estimate how long a given game is likely to last. Understanding these correlations can provide strategic insights for players and enhance overall game analysis.

# lol dataframe

This is the cleaned dataframe after removing unnecessary columns that is not relevent to the driving question

| Column            | Description                                     |
| ----------------- | ----------------------------------------------- |
| `'gameid'`        | The gameid for a specific game                  |
| `'golddiffat_'`   | The gold difference at \_ minutes               |
| `'xpdiffat_'`     | The experience difference at \_ minutes         |
| `'csdoffat_'`     | The cs difference at \_ minutes                 |
| `'gamelength'`    | The length of the game in minutes               |
| `'league'`        | The league's name which the game took place     |
| `'totalkillsat_'` | total amount of kills in the game at \_ minutes |

<p></p>

# lol df

| gameid           | golddiffat10 | xpdiffat10 | csdiffat10 | golddiffat15 | xpdiffat15 | csdiffat15 | golddiffat20 | xpdiffat20 | csdiffat20 | golddiffat25 | xpdiffat25 | csdiffat25 | gamelength | league | totalkillsat10 | totalkillsat15 | totalkillsat20 | totalkillsat25 |
| :--------------- | -----------: | ---------: | ---------: | -----------: | ---------: | ---------: | -----------: | ---------: | ---------: | -----------: | ---------: | ---------: | ---------: | :----- | -------------: | -------------: | -------------: | -------------: |
| LOLTMNT99_132542 |         1364 |        557 |         17 |         2293 |        949 |         23 |         4248 |       2138 |         50 |        12741 |      10827 |         79 |       24.1 | TSC    |              6 |              9 |             15 |             27 |
| LOLTMNT99_132665 |           88 |        625 |         17 |           75 |       1092 |         12 |          777 |       2722 |         24 |         1459 |       3393 |         25 |      35.37 | TSC    |              5 |             14 |             19 |             28 |
| LOLTMNT99_132755 |         2583 |       1718 |         40 |          561 |        410 |         36 |         1528 |        722 |         40 |         1092 |       2266 |         32 |      34.98 | TSC    |              5 |              8 |             14 |             17 |
| LOLTMNT99_131849 |         1260 |        512 |         33 |         2860 |       1199 |         34 |         2735 |       1738 |         24 |         1327 |       5586 |         12 |       42.6 | TSC    |              5 |             11 |             15 |             23 |
| LOLTMNT99_131977 |         1191 |        963 |         44 |          592 |       1346 |         44 |         3319 |       3808 |         25 |         7225 |       9212 |         19 |      29.65 | TSC    |              6 |             13 |             19 |             25 |

<p></p>

# General Plots

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
></iframe>

## pivot table

This table shows the average difference in stats at the 25 min mark for each region that made it to the 2024 worlds, except LPL which do not have complete data.

| League | CS Diff @25 | Gold Diff@25 | XP Diff@25 |
| ------ | ----------- | ------------ | ---------- |
| LCK    | 49.42       | 4963.75      | 5322.68    |
| LCS    | 46.34       | 4724.95      | 4963.20    |
| LEC    | 51.41       | 4711.63      | 5202.10    |
| PCS    | 54.99       | 5905.65      | 5609.44    |
| PCS    | 54.99       | 5905.65      | 5609.44    |
| CBLOL  | 40.82       | 4618.18      | 4900.09    |

<p></p>

# Missingness Assessment

This is a table containing the top 5 most missing columns after counting all the missing values

|                | Missing Count | Missing Percentage |
| :------------- | ------------: | -----------------: |
| golddiffat25   |          1970 |            20.1061 |
| xpdiffat25     |          1970 |            20.1061 |
| csdiffat25     |          1970 |            20.1061 |
| totalkillsat25 |          1970 |            20.1061 |
| golddiffat20   |          1411 |            14.4009 |

<p></p>

## Not Missing At Random (NMAR) Analysis

I believe that the missingess of columns such as gold/xp/cs diff at x minutes all have the potential to be NMAR since it can be understood that games from certain days or region just do not have the data present. This reasoning is also backed up by the missingness table for the top 5 most missing values which the top four have the same percetange of missingness.

## Assessment of Missingness

Since there are four columns with the same amount of missingness, I chose 'totalkillsat25' as the variable I was most interested in. I want to test out whether the column is MAR or NMAR.
To test the hypothesis, a permuitation test is performed to evaluate if the missingness of 'totalkillsat25' is affected by the column 'league' which represents the region, and 'gameid' the id for each game.

**Null Hypothesis (H0):** The missingness of 'totalkillsat25' does not depend on 'league' and 'gameid'

<p></p>

**Alternative Hypothesis (H1):** The missingness of 'totalkillsat25' does depend on 'league' and 'gameid'

<p></p>

**Test Statistic:** Total variation distance (TVD)

<p></p>

**Significance Level (α):** 0.05

<p></p>

if the p-value is less than α, we reject H0, indicating that the missingness of the 'totalkillsat25' column is dependent on the specific column. Otherwise, we fail to reject H0.

| Column         | p-value | Dependent on Missingness (p < 0.05)? |
| -------------- | ------- | ------------------------------------ |
| totalkillsat25 | 0.0     | True                                 |
| gameid         | 1.0     | False                                |

<iframe
  src="assets/plots/missing1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/plots/missing2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
Based on the results of the permutation test, it can be determined that the missingness of 'totalkillsat25' is infact influenced by different regions in 'league' but not individual 'gameid'

# Hypothesis Testing

I want to see if kills in the early game, 10 minutes, actually affect the game length since pro play is more strategy heavy rather than simply killing your opponents.
**Null Hypothesis (H0):** The total number of kills at the 10 minute mark, 'totalkillsat10' has no effect on the duration of the game, 'gamelength'

<p></p>

**Alternative Hypothesis (H1):** A higher total number of kills at the 10 minute mark,'totalkillsat10' leads to a shorter game duration, 'gamelength'

<p></p>

**Test Statistic:** Pearson Correlation Coefficient

<p></p>

**Significance Level (α):** 0.05

<p></p>

Since both 'totalkillsat10' and 'gamelength' are continuous and appromiximately linear, I chose the pearson test to find the correlation between the two variables and whether that correlation is significant.
The pearson correlation value I got was around -0.09, signifying a very small negative correlation, and a p-value of around 2.45e-16.
Since the p-value is less than our threshold of 0.05, we reject our null hypothesis and that we are 95% confident that there is a small negative correlation between 'totalkillsat10' and 'gamelength'.

# Framing a Prediction Problem

I plan to predict how long will a game last in minutes given the amount of kills at a certain time period.
Since there was a significant correlation between 'totalkillsat10' and 'gamelength', I figured that if we use all information in 'totalkillsat*' where * can be 10,15,20,or 25 it is possible to predict how long a game ends.

To evaluate the model’s performance, I will use the **mean squared error (MSE)** as the metric. MSE is suitable because it penalizes larger prediction errors more heavily, ensuring that my model minimizes substantial deviations from actual gametime. I also used the **R-squared value** to measure how well the features collectively explain the variance in average game times.

# Baseline Model

The baseline model is a **basic linear regression model** that predicts 'gamelength' using 'totalkillsat10' which was found as having a significant correlation in the previous section. Both 'totalkillsat10' and 'gamelength' are quantitative variables which means there was no need for any sort of enconding. The model gave the equation _y = -0.1507x + 32.8376_ where y is 'gamelength' and x is 'totalkillsat10'. It can be observed that most of the predictions are going to be somewhere around the 30-35 minute mark. After calcuating **mse** and **R^2**, which were around 27.455 and 0.009. Therefore I can conclude that this is a terrible model because the mse is 27 minutes which is unbelievably high and a extremely low R^2 also means that we can barely explain any sort of variance whatsoever.

# Final Model

### Improving on the basic model

Upon the production of an inaccurate baseline model,

1. I decided to include more relevent variables such as _'csdiffat\_'_ and _'golddiffat\_'_ in addition to _'totalkillsat\_'_ since the bloodiness level don't always represent a faster game because either teams might lose the same amount of members every fight which will cause a close game that'll last longer. Having additional information like cs difference and gold difference will allow the model to give a more accurate representation of the game time since larger experience and gold difference can represent how ahead the team is from the enemy team in a game.
2. All the _'totalkillsat\_'_ columns were already engineered before performing the baseline model from columns like _'killsat\_'_ and _'opp_killsat'_ from the original dataset to give an overall summary of the amount of kills in each game by time.
3. I also engineered columns 'has\_*x*min' using **column transformer** where x represents the time 10,15,20,25 to label each game to reduce misinputs like when a game ended before 25 minutes but was still used to predict games which lasted longer than 25 minutes.

### Hyperparameter Tuning with `GridSearchCV`

To improve my multiple linear regression model, I performed a hyperparameter tuning using `GridSearchCV` to test different values for four hyperparameters: `n_estimators`, which is the number of decision trees, `max_depth`, depth of the trees, `min_samples_split`, which controls when a node should split into two branches, and `min_samples_leaf` that sets the minimum number of samples that must be present in a leaf node. The best model hyperparameters turned out to be `n_estimators=200`, `max_depth=5`,`min_samples_split=10`,`min_sample_leaf=2`. From these, I can infer that the model overfitted or took too much while going in depth during the training stage.
After this hyperparameter tuning, I recalculated my metric and saw an improvement in the **R^2 value increased to 0.36** from the old 0.009, while the **mse decreased to 17.73 from 27.45**. Although the R^2 value is still on the lower end, it is a significant improvement from my old model. Looking at the coefficients, the highest 3 are:

1. 'golddiffat25': 0.4044
2. 'xpdiffat25': 0.0447
3. 'totalkillsat25': 0.0102

'golddiffat25' has a significantly bigger coefficient than the rest of the variables which indicate that gold differences are more important than other differences and the bloody level of a game. This make sense since every decision a pro team make in the game is to net themselves more gold than their opponent.

# Fairness Analysis

To further put our final model to the test, we analyzed the fairness of our model by comparing its performance on short versus long reviews. Since we are using linear regression, we chose the **difference in R^2** as our test statistic. This helps us assess whether the model performs differently for short and long reviews. Our analysis uses a permutation test to determine if any observed differences in performance are likely due to random chance. We divided our data into 2 groups: reviews with a length less than or equal to the median review length & reviews with a length greater than the median review length. This is done to test if our model may perform differently on shorter or longer reviews.

**Null Hypothesis (H0)**: The model is fair. The precision for both games played in the LCK and games played in other regions.

<p></p>

**Alternative Hypothesis (H₁)**: The model is unfair. The precision for games played in the LCK is different than the games played in other regions.

<p></p>

**Test Statistic:** Difference in R^2

<p></p>

**Significance Level (α):** 0.05

<p></p>

After running a permutation test 1000 times, the **observed R^2 Difference was -0.0379** and our **p-value was 0.224.** The observed R^2 difference of -0.0379 indicates that the model performed slightly worse on matches from the lck compared to matches from other regions. However, this difference is very small and, given the p-value of 0.224, it is not statistically significant.
Since the p-value is greater than our 0.05, we **fail to reject** the null hypothesis. Therefore, based on the permutation test, there is no significant difference in model performance between games played in the lck and games played in other regions. We can safely conclude that our model **appears to be fair**, at least based on regions, since its R^2 performance does not differ significantly between the lck and other regions.
