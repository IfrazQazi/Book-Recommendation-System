# Book-Recommendation-System

# INTRODUCTION:

During the last few decades, with the rise of YouTube, Amazon, Netflix, and many other such web services, recommender systems have taken more and more place in our lives. From e-commerce (suggest to buyers articles that could interest them) to online advertisement (suggest to users the right contents, matching their preferences), recommender systems are today unavoidable in our daily online journeys.

In a very general way, recommender systems are algorithms aimed at suggesting relevant items to users (items being movies to watch, text to read, products to buy, or anything else depending on industries).

Personal recommendation systems have been emerged to conduct effective search which

related books based on user rating and interest. The proposed system used the K-NN K-NN Cosine Distance function to measure distance and Cosine Similarity function to find Similarity between the books clusters. We also implemented a SVD system that gives us good recommendations.

# OBJECTIVE:

Recommender systems are really critical in some industries as they can generate a huge amount of income when they are efficient or also be a way to stand out significantly from competitors.
The objective of the project is to build a book recommendation system for users based on popularity and user interests.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Dataset Information

The dataset consists of three tables:

Books, Users, and Ratings

## Books Dataset
The book's dataset has 271360 rows and 8 columns.

ISBN is unique book number

Book-Title (It is the title of the books)

Book-Author (The author of the book)

Year-Of-Publication (It is the year when book was published)

Publisher (It is the name of the publisher)

Image-URL-S (It is URL of the books categorizing it as small)

Image-URL-M (It is URL of the books categorizing it as medium)

Image-URL-L (It is URL of the books categorizing it as large)

## Users Dataset

User's dataset  has  278858 rows and 3 columns

User-ID- is unique ID of a user

Location-it has location of a users

Age- its age of the users

## rating Dataset

The Books-Rating dataset has 1149780 rows and 3 columns.

User-ID- is unique ID of a user

ISBN is unique book number

Book-Rating - it consist ranting of the book given by users

 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Data Cleaning and Pre-Processing

The dataset consists of three tables; Books, Users, and Ratings. Data from all three tables are cleaned and preprocessed separately as defined below briefly:
 
## For Books Table:

Drop all three Image URL features.

Check for the number of null values in each column. There comes only 3 null values in the table. Replace these three empty cells with ‘Other’.

Check for the unique years of publications. Two values in the year column are publishers. Also, for three tuples name of the author of the book was merged with the title of the book. Manually set the values for these three above obtained tuples for each of their features using the ISBN of the book.

Convert the type of the years of publications feature to the integer.

By keeping the range of valid years as less than 2022 and not 0, replace all invalid years with the mode of the publications that is 2002.

Upper-casing all the alphabets present in the ISBN column and removal of duplicate rows from the table.

## For Users Table:

Check for null values in the table. The Age column has more than 1 lakh null values.

Check for unique values present in the Age column. There are many invalid ages present like 0 or 244.

By keeping the valid age range of readers as 10 to 90, replace null values and invalid ages in the Age column with the mean of valid ages.

The location column has 3 types of values city, state, and country. These are split into 3 different columns named; City, State, and Country respectively. In the case of null value, ‘other’ has been assigned as the entity value.

Removal of duplicate entries from the table.

## For Ratings Table:

Check for null values in the table.

Check for the Rating column and User-ID column to be an integer.

Removal of punctuation from ISBN column values and if that resulting ISBN is available in the book dataset only then consider otherwise drop that entity.

Upper-casing all the alphabets present in the ISBN column.

Removal of duplicate entries from the table.

# Exploratory Data Analysis:

Top 10 Book Publishers:

![newplot (9)](https://user-images.githubusercontent.com/60994606/158520285-f34a0874-49ad-4ba0-aef5-2f9a413a9df6.png)

From the graph above we can see the top 10 publishers and among them Harlequin publishers are the publishers of most books

Top 10 Book Authors:

![newplot (10)](https://user-images.githubusercontent.com/60994606/158520384-630e5c46-7a9f-4ffe-9ac2-ef77c434590a.png)

From the graph above we can see the top 10 Author

Number of book publish per year :

![newplot (11)](https://user-images.githubusercontent.com/60994606/158520531-66bcd99b-51be-4701-a74d-7ff627882aa4.png)

From the above graph we can see that most of the books are published between 1980-2000

Age Distribution :

![image](https://user-images.githubusercontent.com/60994606/158520767-df210edb-5561-44f5-b497-cfdab25a4811.png)

Majority of the readers were of the age bracket 20-35.

Top 10 Country having highest number of reader:

![newplot (12)](https://user-images.githubusercontent.com/60994606/158520896-54e3b827-5e5e-406e-9910-4bbc71e5c244.png)

As we can see from above plot most of the readers are from USA

Top 10 Cities in the World having highest number of reader:

![newplot (16)](https://user-images.githubusercontent.com/60994606/158521015-75f73753-377b-4e2e-9a53-a773480b043c.png)

Here we can see that unlike cities in the United States, we have the largest number of readers here in London, followed by Barcelona.

Rating Given by All Users:

![image](https://user-images.githubusercontent.com/60994606/158521165-21ddb4ba-0cae-4493-bf05-d105fd84c263.png)

The ratings are very unevenly distributed, and the vast majority of ratings are 0 .As quoted in the description of the dataset - BX-Book-Ratings contains the book rating information. Ratings are either explicit, expressed on a scale from 1-10 higher values denoting higher appreciation, or implicit, expressed by 0.Hence segregating implicit and explicit ratings datasets.

Rating given by all users in explicit ratings dataset:

![image](https://user-images.githubusercontent.com/60994606/158521250-7fa21801-8e0e-4361-8b62-a3b7451c2cca.png)

It can be observe that higher ratings are more common amongst users and rating 8 has been rated highest number of times

Top 15 books:

![newplot (17)](https://user-images.githubusercontent.com/60994606/158521407-7f71f312-5002-4118-853e-53710551733b.png)

The book that received the most rating counts in this data set is The Lovely Bones: A Novel

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Algorithms Implemented:

Popularity Based Recommendation :

We have sorted the dataset according to the total ratings each of the books have received in non-increasing order and then recommended top n books.

![Screenshot 2022-03-01 09 35 36](https://user-images.githubusercontent.com/60994606/158522120-c48f9001-985e-48cb-8969-0193d2c1c86a.png)

User-Item Collaborative Filtering Recommendation

Collaborative Filtering Recommendation System works by considering user ratings and finds cosine similarities in ratings by several users to recommend books. To implement this, we took only those books' data that have at least 50 ratings in all.

![image](https://user-images.githubusercontent.com/60994606/158522289-a993b52a-7304-4713-b6e9-36064fab6fd7.png)

 Correlation Based Recommendation
 
For this model, we have created the correlation matrix considering only those books which have total ratings of more than 50. Then a user-book rating matrix is created. For the input book using the correlation matrix, top books are recommended.

![image](https://user-images.githubusercontent.com/60994606/158522432-34c53a60-260f-4b7f-afd5-1725613fcc29.png)

Nearest Neighbor Based Recommendation

To train the Nearest Neighbors model, we have created a compressed sparse row matrix taking ratings of each Book by each User individually. This matrix is used to train the Nearest Neighbors model and then to find n nearest neighbors using the cosine similarity metric.

![image](https://user-images.githubusercontent.com/60994606/158522547-b5eeaa66-5c2f-4fe5-9551-753e4ec5a61e.png)

 Content Based Recommendation
 
This system recommends books by calculating similarities in Book Titles. For this, TF-IDF feature vectors were created for unigrams and bigrams of Book-Titles; only those books' data has been considered which are having at least 80 ratings.

![image](https://user-images.githubusercontent.com/60994606/158522670-5331dbea-8447-4bc1-b715-c7473c1545ba.png)

Hybrid Approach (Collaborative+Content) Recommendation

A hybrid recommendation system was built using the combination of both content-based filtering and collaborative filtering systems. A percentile score is given to the results obtained from both content and collaborative filtering models and is combined to recommend top n books.

![image](https://user-images.githubusercontent.com/60994606/158522890-4e2e26d0-acb0-4d45-af34-79f631d2d092.png)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Conclusion:

In EDA, the Top-10 most rated books were essentially novels. Books like The Lovely Bone and The Secret Life of Bees were very well perceived.

Majority of the readers were of the age bracket 20–35 and most of them came from North American and European countries namely USA, Canada, UK, Germany and Spain.

If we look at the ratings distribution, most of the books have high ratings with maximum books being rated 8. Ratings below 5 are few in number.

Author with the most books was Agatha Christie, William Shakespeare and Stephen King.

For modeling, it was observed that for model based collaborative filtering SVD technique worked way better than NMF with lower Mean Absolute Error (MAE) .

Amongst the memory based approach, item-item CF performed better than user-user CF because of lower computation requirements .

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Libraries Used:

ipython-notebook - Python Text Editor

sklearn - Machine learning library

seaborn, matplotlib, Plotly - Visualization libraries

numpy, scipy- number python library

pandas - data handling library
