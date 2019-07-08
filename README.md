# Movie-lens-Analysis-and-Rating-Prediction
## 01 Introduction
In this project, we use the movie lens dataset contains 1 million ratings from 6000 users on 4000 movies to build a movie 
recommender system to predict the rating of a movie. The ratings data has 1000209 observations and 4 columns: UserID, MovieID,
Rating and Timestamp. We split the observations into train data that contains about 60% rows of the observations and test data
that contains about 20% of the user-movie pairs from the ratings.dat from the MovieLens 1M dataset.

## 02 Methodology
### Model 1: Collaborative Filtering (CF) Method with User-based (UBCF)
We train a recommender system and make prediction on the test data. First, we create a utility matrix and normalize the utility
matrix with Z-score method. Z-scoring is that additionally divides each user’s rating by its standard deviation. After 
normalizing the rating matrix R we acocunt for individual row bias of each user and make sure that all ratings are scaled 
similarly. Then we apply the recommender system with UBCF method and obtain a short summary of the model. nn parameter sets 
the neighborhood of most similar users to consider for each user profile. We set nn = 25 so the ratings profiles of the 25 
nearest neighbors will be the basis for making predictions on a users unrated items profile. For per item, we calculate the 
average of ratings by each user’s 25 most similar users. Weight the average ratings based on similarity score of each user 
whose rated the item and similarity score equals weight. We use the test data we split above to make the prediction and the 
RMSE is 1.03389.

### Model 2: Collaborative Filtering (CF) Method with Item-based (IBCF)
Item-based CF approach is very similar to user-based. But in this one, similarity is computed between items, not users. 
Assumption is that users will prefer items similar to other items they like. As with item-based CF, we have used center method
to normalize the rating matrix and Cosine similarity metric. We set k = 350 so the ratings profiles of the 350 nearest 
neighbors will be the basis for making predictions on a item. IBCF doesn’t need to access the initial data. For each item, 
the model stores the k-most similar, so the amount of information is small once the model is built. After running IBCF we 
obtain the test rating based on the UserID and MovieID to find ratings in the rec_list. We apply the recommender system with 
most method and obtain a short summary of the model. After using predict() function we acquired the fitted values for the test
data and the RMSE is 1.324066.

## 03 Conclusion
Comparing the two models UBCF and IBCF we applied in the recommender system, UBCF needs to access the initial data and keep in
the memory so it doesn’t work well in a big rating matrix. Also, UBCF needs more computing power and time since building the 
similarity matrix. However, UBCF’s accuracy is proven to be slightly more accurate than IBCF.
