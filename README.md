# Recommended For You  
## Steam-Based Game Recommendation Engine  
![intro](steam_intro.jpg)  

# Introduction  
Steam is the world's most popular PC Gaming hub, with over 6,000 games and a community of millions of gamers. With a massive collection that includes everything from AAA blockbusters to small indie titles, great discovery tools are a highly valuable asset for Steam. In this project, we developed a game recommendation engine based on [Steam user data](https://www.kaggle.com/tamber/steam-video-games). This engine recommends games to users based on how much time they spent playing previous games and their similarity to other video game players. In other words, it predicts which games a user is likely to spend the most time playing. This prediction would allow for user-specific video game advertising.   

# Approch  
* MDS and K-means to cluster/segment users and games into groups  
* Heuristics to segment customers using hours played as a metric for ratings  
    - User-based collaborative filtering  
    - Game-based collaborative filtering  
* Matrix Factorization to solve problems created by collaborative filtering  




