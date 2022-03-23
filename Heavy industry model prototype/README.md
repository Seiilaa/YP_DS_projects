# Video game market analysis

- Analyzed  video game market tendentions until 2016
- In this data identified patterns that determine the success of the game.
- Determined life cycles of video game platforms
- Compared behaviors of the players from different regions  
- Plotted charts to visualize the findings

## Code and resources used

**Python Version:** 3.10.2
**Packages:** pandas, numpy, matplotlib, seaborn, scipy

## Data description
All data is stored in the games.csv file

-   Name — game title
-   Platform — platform
-   Year_of_Release
-   Genre
-   NA_sales — sales in North America (millions of copies)
-   EU_sales
-   JP_sales
-   Other_sales — sales in other countries (millions of copies)
-   Critic_Score — score given by the video game critics (max 100)
-   User_Score — user score (max 10)
-   Rating — rating given by ESRB (Entertainment Software Rating Board). This rating determines the age category for the game.

## Task description

Analyze the video game market tendentions using data until 2016 and identify patterns that determine success of the game.
These findings will be used by the video game retailer to predict potentially popular products and plan future advertising campaigns around those.

## Data cleaning
-   Found and processed missing values in the categorical variables
-   Checked data for duplicates
-   Changed data types to prepare data for further analysis training

## Data analysis
-   Grouped data by the year of release. Excluded years before 1994 as there is no much data about the games released back than. 
-   Analyzed sales across different platforms.
    -   Determined life cycles of the video game platforms
    -   Determined what platforms are currently popular on the market
    -   Compared distributions of sales across different platforms
-   Analyzed critic and user scores
    -   Studied correlations between critic and users scores and game sales.
-   Analyzed video game genres
-   Created a portret of a typical customer from the NA, EU and JP regions
-   Compared players the way players judge video games across different platforms and genres.

## Results
1. Successful video game consoles have a life cycle of 8 to 12 years with annual sales peaking around the middle of that period.
2. Released in 2013 the PS4 and XOne are still gaining popularity and we can expect these platforms to continue to be popular until 2023-2025.
3. Currently PS4 show higher average sales compared to XOne.
4. Additionally the retailer should expect to see some sales on Nintendo 3DS. The sales are declining but considering the nature of the Nintendo games, new releases will most likely be sold pretty well in 2017. 
5. Critic score could be used in combination with other factors to predict the game success. This can't be said about user score.
7. Players in diffrent regions prefer different genres and platforms. In NA X360 is the leading platform while in the EU both PS3 and X360 are popular In Japan top selling modern platofrm is Nintendo 3DS. X360 isn't popular in Japan.

The recommendation for the retailer would be to focus on emerging new generation consoles PS4 and XOne while also selling new releases for Nintendo 3DS especially in Japan. 
The retailer should take into account that players from different regions prefer different game genres and platforms.