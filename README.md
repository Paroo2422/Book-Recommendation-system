# Product-Recommendation-system using Amazon customer reviews
![image](https://user-images.githubusercontent.com/80713174/169184357-47f03182-c514-45e0-a9c5-7937e8976a6b.png)
Credit: eDesk

When we see a list of movies, we like, suggested on Netflix, when our favorite apps show us all the products we like and would love to purchase, when YouTube shows you a list of videos to watch next, you wonder is it magic that these apps or websites read you so well. Well, the answer is that they actually learn your likes and dislikes. They learn people like you, people with similar taste. They then use this knowledge to suggest you with bunch of things you would like to listen to, shop or watch. These are the Recommendation systems. All the magic happening behind the scenes is done by machine learning, or more specifically, recommendation systems that use algorithms, to find similar items and similar customers, based on their behavior, and recommend items which the specific customer should like. There are different aspects the algorithm can be trained to use to build a better recommendation. The ratings, similar interest in 2 or more individuals or the review written on a purchased product. Ratings is commonly used, but I have used review given by a customer for the product and use it to get sentiment

## Data Source
The data is collected from the following sources:
Amazon Review Data (2018) https://nijianmo.github.io/amazon/index.html#sample-review  
Since the data is large, I will be planning to use review data, where a product has 5 or more reviews ("Small" subsets for experimentation – 5-core).
There are two datasets to consider, one is the review and ratings information for a product by a customer, with primary key as the product ID.
The product details is present in a meta dataset with the primary key of product ID and other product details. We will be merging these two datasets for the project.

## Data Wrangling
We will need overall, reviewerID, asin, reviewerText further to work on our model. We can select other features like reviewerName, but we already have reviewerID, so this feature is not necessary.
The duplicated values for a productid and customerID combination was dropped. The column values were renamed appropriately and unwanted columns were dropped.
The meta dataset was included to have only productid, product title, brand, image URL columns. The review dataset was included to have only productid, reviewerID, reviewer name, review text, summary and rating.

## Models Used
The sentiment analysis for the review text data was done using 3 packages: Vader, TextBlob and Flair.
The Vader, TextBlob and Flair scores when compared with the ratings, the Vader and TextBlob sentiment analysis looks pretty decent compared to flair sentiment analysis. The range of sentiment score for flair is large. The former 2 packages look more promising.

For the recommendation system design, I tried 3 different models: KNN, Matrix Factorization and Neural Network.
The short model with 3 layers, gives us a better MSE compared to baseline model with 5 dense layers for neural network model.  This can also be seen in the above NN performance graph. The base line model seemed to overfit even when dropout layers were added. Also, when compared to Matrix factorization, the MSE for Neural network model is small. 
KNN and NN model can be used to predict the recommendation of products.
For detailed code, see the notebooks folder to follow along the work.

## Leranings
The neural network model would work better with big data. Even adding a dropout layer, did not let us recommend products perfectly. I would like to work with a bigger amazon review dataset.

The review text is a combination of satisfaction with the product, deliver, condition of the product. I would like to see these impact on the ratings given for the product.



