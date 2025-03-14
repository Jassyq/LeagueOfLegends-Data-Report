# LeagueOfLegends-Data-Report

## Final project of wi25 dsc80 at UCSD. This project uses the 2024 league of legends professional tier one leagues across the world

#### By Jiahe Jason Qin

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

## Univariable plot

description

'import plotly.express as px'
'df = px.data.iris()'
'fig = px.scatter(df, x="sepal_width", y="sepal_length", color="species")'
'fig.write_html("assets/my-plot.html", include_plotlyjs="cdn")'
'mv my-plot.html assets/'

<iframe
  src="assets/my-plot.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
