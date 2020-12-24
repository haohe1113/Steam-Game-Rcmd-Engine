# Recommended For You  
## Steam-Based Game Recommendation Engine  
![intro](steam_intro.jpg)  

# Introduction  
Steam is the world's most popular PC Gaming hub, with over 6,000 games and a community of millions of gamers. With a massive collection that includes everything from AAA blockbusters to small indie titles, great discovery tools are a highly valuable asset for Steam. In this project, we developed a game recommendation engine based on [Steam user data](https://www.kaggle.com/tamber/steam-video-games). This engine recommends games to users based on how much time they spent playing previous games and their similarity to other video game players. In other words, it predicts which games a user is likely to spend the most time playing. This prediction would allow for user-specific video game advertising.   

# Approch  
* Exploratory Analysis: [MDS](https://github.com/haohe1113/Steam-Game-Rcmd-Engine/blob/master/Marketing_MDS_Data_Cleaning.ipynb) and [K-means](https://github.com/haohe1113/Steam-Game-Rcmd-Engine/blob/master/steam_market_segmentation.ipynb) to cluster/segment users and games into groups.  
* Heuristics to segment customers using hours played as a metric for ratings:  
    - User-based collaborative filtering.  
    - Game-based collaborative filtering.  
* Matrix Factorization to solve problems created by collaborative filtering.

*Please click through the links above to see our code & analysis for each step.*  

# Outcomes Display  
## 1. Collaborative Filtering  
We explored user-based and game-based collaborative filtering algorithms for the recommendation engine.  
**User-based collaborative filtering(UB-CF)** is based on an assumption that similar gamers have similar tastes in games. If gamer A and gamer B have played very similar games in the past and they rated games by very similar scores, UB-CF will recommend games that A enjoys playing recently to B. 
**Game-based collaborative filtering(GB-CF)** however, instead of looking for similar gamers to make recommendations, recommends games which are similar to games that the player loves. While UB-CF focuses on the correlations among players, GB-CF calculates correlations among games to search for games a player might want to play next.  
To test the two algorithms, we recruited 30 test users and asked them to rate a list of games they played before. According to their reflections on the recommendations made by the two algorithms, UB-CF has better performance overall.  
[ubcf-rmcd]  
As you can see above, from the test run,  based on their gaming history, our engine recommended `Alien Swarm` to Justin and `Half-Life 2` to Manan which, according to the two gamers, are both very meaningful recommendations. However, the engine failed to make recommendation to me (Hao) since I don't play on Steam very much. This failure exposed a shortcoming of UB-CF that it requires a significant amount of games played to produce recommendations, which is not friendly to new Steam users. However, new users are in fact the most critical targets for such recommendation system in order to cultivate user stickness. Therefore the shortcoming of UB-CF (as well as GB-CF) is fatal when it comes to real-life business application.  

## 2. Matrix Factorization 
In an effort to solve the problem of collaborative filtering algorithm, we turned our eyes to **Matrix Factorization** alogrithm which will work even if only a few games played is provided. Plus, matrix factorization has better computing efficiency than collaborative filtering. 
Nevertheless, according to the reflections from our test users, their satisfaction level on matrix factorization based recommendation engine is lower than its collaborative filtering counterpart. It turns out that matrix factorization algorithm is prone to recommend generally popular games (like `Dota 2` in our dataset) when you keep adding gaming history as input.  
[mf-rmcd]  
As you can see here, while matrix factorization made it to recommend `Call of Duty: Modern Warfare 3` to me based on my short gaming history, it recommended `Dota 2` to both Justin and Manan, which according to the two gamers, looks like a less customized and thus less attractive recommendation than the previous ones made by collaborative filtering.  
"It looks like an ad for everyone." Manan said after seeing the `Dota 2` recommendation made for him.  

## Conclusion and More  
To sum up, while **Matrix Factorization** algorithm is easier to be applied to new users, **UB-CF** produces better recommendation quality when a significant amount of games played are inputed. In conclusion, we recommend a combination of **Matrix Factorization** and **UB-CF** where the former will be used only if the latter failed to make recommendations as the final solution for Steam game recommendation. Other than that, we planed to create a dashboard for our recommendation engine and set up more test runs. We will keep updating this page.

