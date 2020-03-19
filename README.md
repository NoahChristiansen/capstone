# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: TMDB US Box Office Prediction


<img src="./images/capstone_pic.jpg" width="600px">

(Artist: Serbinka From Shutterstock)

### Table of Contents:

- [Problem Statement](#Problem-Statement)
- [Outside Research](#Outside-Research)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Sources](#Sources)

---

### Problem Statement

According to the [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/), in 2019, there was about 1.24 billion Movie Tickets sold in the United States. Given that information, one could now assume that there must be a great deal of money going to the Movie Industry. So how do we, as Movie Lovers, determine this amount of cash flow? We will have to focus on the Movie's revenue. In other words, **can we predict a Movie's United States Box Office revenue?**

We could use a [dataset](https://www.kaggle.com/c/tmdb-box-office-prediction/data) with over 7,000 past films from [The Movie Database](https://www.themoviedb.org/) created on the Kaggle website that has selected features. In particular, those features are cast, crew, plot keywords, budget, posters, release dates, languages, production companies, countries and others. Then we select the appropriate features to train various regression models with custom hyperparameters. Afterwards, we will use our models' $R^2$ scores to determine the best model to answer this inquiry. In other words, our goal is to assist production compaines with deciding how they should invest to gain a return. 


---

### Outside Research

On [The Movie Database](https://www.themoviedb.org/) website, Moive Seekers can gain a lot of information about moives and television shows. If we want to gain access to details about a particular movie, we can either click on the movie's poster or search it up on the website's database. Once we have access to a particular movie, we are able to see the title, poster, user score, overview, full cast & crew, status, original language, runtime, budget, genres, key words, content score, and revenue if already released. Also, we are able to see reviews and create discussions about a particular movie. In other words, it is a Movie Lovers dream. With that in mind, most of these factors can help us with determining how much money a movie will make after it is out in the United States Box Office. 

To emphasize, according to [Movies: What determines the success of a movie (by box office revenue)?](https://www.quora.com/Movies-What-determines-the-success-of-a-movie-by-box-office-revenue), many factors can determine the Box Office success of a film such as the popularity of the film's content, the current popularity of the film's genre, the current popularity of the film's stars, the strength of the film's marketing campaign, and the strength of the film's distribution as well as its release schedule. As a result, popularity and budgeting seem like key factors that can influence a movie's revenue. 

In addition, "Movies: What determines the success of a movie (by box office revenue)?" states that factors such as weather, holidays, distracting news events can limit the film's audience during the critical opening weekend. In that case, datetime seems like a key factor that also can influence a movie's revenue.

Also, "Movies: What determines the success of a movie (by box office revenue)?" states awareness of the film based upon it being adapted from a popular book or news story. For this reason, genres seem like a key factor that also can influence a movie's revenue. 

Lastly, according to [Study explores what really makes a movie successful](https://phys.org/news/2017-11-explores-movie-successful.html), a key determinant of Box Office success is the number of screens where a movie is released. Thus, movie production companies need to budget for their advertisement as well. In this case, does the production company have enough money to sell to locations where movies are being shown, or have enough for advertising? For this reason, production companies seem like a key factor that also can influence a movie's revenue. 

In sum, we will use this research to assist us on understanding our data fully throughout this Data Science Process.

---

### Executive Summary

We began by importing the training dataset from the Kaggle's website. We renamed the dataset to movies because we wanted to clearly identify our objective from our problem statement. In the movies dataset, it had twenty four feature columns including our target variable `revenue` of a particular movie.

We began our data cleaning by dropping all the movies that were not made in the United States because we wanted to shape our dataset to answer our problem statement. Then we dropped the unrelated features that were not correlated with our problem statement. Also, we dealt with missing values and fixed the datetime feature. We extracted data from specific features as well because we noticed that some of our categorical features were in a dictionary format and we wanted some of those values as features in our dataset. Afterwards, we one-hot encoded on the categorical data. However, there would of been too many features in our dataset from creating these binary features, thus, we regulated some binary features. We created eight new features as a result. Lastly, we saved our clean movies dataset for future use.

Next, we were able to do some exploratory data analysis. First, we checked the summary statistics. Then we investigated the target variable `revenue` to see how it behaved; we looked at its distribution. As a result from our summary statistics analysis, we investigated selected univariate distributions. These univariate distributions were only the original numerical features because it was easier to see these distributions than our "created" numerical features. Then using a set of selected features, we explored correlations between these selected features and the target variable. We only selected an amount of features because not all of the binary features are ideal to see visually. To actually visually explore the other binary features, we looked at it's frequency counts. Afterwords, we investigated the datetime features to see if there were trends because of time. Lastly, we determined the outliers in our dataset.

Before we modeled, we needed to do some preparation. We began by creating our X features and y. Then, we train-test split. Lastly, we determined the baseline scores. We used the DummyRegressor model to obtain these values.

Finally, we were able to model. We modeled various regression models. We modeled Linear Regression with default hyperparameters and Ridge Regression, Lasso Regression, BaggedRegressor, & RandomForestRegressor with tuned hyperparameters. Then we supplemented the models with visualizations. We graphed the predictive values with respected to the actual values and explored some of the models' coefficients. 

In the end, we focused on the $R^2$ scores, RMSE metrics, and the bias-variance tradeoff from each model to determine which model was the best to answer our problem statement.

---

### Data Dictionary

We had an [original data dictionary](https://www.kaggle.com/c/tmdb-box-office-prediction/data), yet, we did create new features into our datasets. Lets create a new dictionary. 


|Feature|Datatype|Discription|
|---|---|---|
|budget|int64|The amount money spend to make and advertise the movie.|
|original_title|object|The movie's original name.|
|popularity|float64|The likeability score for the movie. This is out of 100 percent.|
|release_date|datetime64[ns]|The date the movie was released to the public.|
|runtime|float64|The full amount of the movie's runtime in minutes.|
|title|object|The name of the movie now.|
|month_release_date|int64|The month the movie was release to the public.|
|year_release_date|int64|The year the movie was release to the public.|
|disney_production_company|int64|The list of Disney own production companies.|
|twenty_century_fox_production_company|int64|The list of Twenty Century Fox own companies.|
|warner_bros_production_company|int64|The list of Warner Bros own compaines.|
|nbcuniversal_production_company|int64|The list of NBCUniversal own compaines.|
|sony_pictures_production_company|int64|The list of Sony Pictures own compaines.|
|paramount_pictures_production_company|int64|The list of Paramount Pictures own compaines.|
|top_twenty_influential_actors|int64|The list of the top twenty influential actors in the industry.|
|top_twenty_keywords|int64|The list of the top twenty keywords individuals use to identify movies.|
|genres_dummies|int64|Dummy features of the `genres` feature. Genres are various forms of categories or classifications or groups of movies.|
|status_dummies|int64|Dummy features of the `status` feature. Status tells us if the movie was released, rumored, or in post-production.|
|crew_departments_dummies|int64|Dummy features of the `crew_departments` feature. Crew departments are various departments that worked on a movie.|
|revenue|int64|The amount of money the movie has made after being released to the public.|


---

### Conclusions and Recommendations

|Model|Training $R^2$ Score|Testing $R^2$ Score|RMSE Training|RMSE Testing|
|---|---|---|---|---|
|Baseline|0.000|-0.002|13889519|169751452|
|Linear|0.617|0.604|85935229|106672431|
|Ridge|0.617|0.591|86004081|108497311|
|Lasso|0.617|0.600|85935229|107705049|
|ElasticNet|0.616|0.600|86056471|108778885|
|BaggingRegressor|0.944|0.700|32899455|94545011|
|RandomForestRegressor|0.800|0.671|62142378|97225529|


All of the regression models surpassed the baseline accuracy. Therefore, the best model was the **RandomForestRegressor** Model. According to the testing $R^2$ score, the RandomForestRegressor was able to manage well with unknown data. However, the model was still overfit because it had low bias and high variance.

Despite the overfitting, this model can be use to predict the revenue of a US movie given that we know the selected features of that particular movie. The top two features that production companies should consider to focus on to get a return on their investments should be the `budget` and `popularity` features. This is the case because these features were consistently the top two correlated features with the target variable. Also, production companies should consider investing in `genre_adventure` because that movie genre was our outliers with extremely high revenue and it was the third highest coefficient in our regularized models. 

Yet, the RandomForestRegressor still had its limitations. We can not fully interpret it because it does not predict beyond the range of the training data. Also, it created an overfit on our dataset because it cannot handle the noise. In other words, additional noise features could hindered our models results.

We can improve our model's $R^2$ scores, if we further tuned our hyperparameters, and eliminated more outliers.

In the end, we still have lingering questions we need to ask:
- Can we use a Convolutional Neural Network on the image data as part of a transfer learning process to engineer additional features in our prediction model?
- Can we feature engineer our features and target variable to optimized our predict model results? I.e. taking the logarithm.
- Will this model still be valid 5 years from now when consumer preferences/trends change when it comes to movies? Given that we already seen different trends throughout the decades in our EDA.

---

### Sources

- [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/)
- [TMDB Box Office Prediction](https://www.kaggle.com/c/tmdb-box-office-prediction/data) 
- [The Movie Database](https://www.themoviedb.org/)
- [Movies: What determines the success of a movie (by box office revenue)?](https://www.quora.com/Movies-What-determines-the-success-of-a-movie-by-box-office-revenue)
- [Study explores what really makes a movie successful](https://phys.org/news/2017-11-explores-movie-successful.html)
- [Google Web Interface and Search Language Codes](https://sites.google.com/site/tomihasa/google-language-codes)
- [IMDB website](https://www.imdb.com/)
- [Boom or Bust? Factors that Influence Box Office Revenue](https://medium.com/@nealsivadas/boom-or-bust-factors-that-influence-box-office-revenue-c8e4442d141f)
- [EVERY COMPANY DISNEY OWNS: A MAP OF DISNEY'S WORLDWIDE ASSETS](https://www.titlemax.com/discovery-center/money-finance/companies-disney-owns-worldwide/)
- [List of assets owned by 21st Century Fox](https://en.wikipedia.org/wiki/List_of_assets_owned_by_21st_Century_Fox)
- [List of assets owned by WarnerMedia](https://en.wikipedia.org/wiki/List_of_assets_owned_by_WarnerMedia)
- [List of assets owned by NBCUniversal](https://en.wikipedia.org/wiki/List_of_assets_owned_by_NBCUniversal)
- [Sony Pictures Entertainment Motion Picture Group](https://en.wikipedia.org/wiki/Sony_Pictures_Entertainment_Motion_Picture_Group)
- [Paramount Pictures](https://www.wikiwand.com/en/Paramount_Pictures)
- [Movie Keywords From The Numbers](https://www.the-numbers.com/movies/keywords#keyword_overview=od1)
- [Here Are The 20 Richest Actors In The World & Their Net Worth](https://moneyinc.com/richest-actors-in-the-world-in-2019/)
- [Fourth Pirates Of The Caribbean Is Most Expensive Movie Ever With Costs Of 410 Million Dollars](https://www.forbes.com/sites/csylt/2014/07/22/fourth-pirates-of-the-caribbean-is-most-expensive-movie-ever-with-costs-of-410-million/#5072a4eb364f) 
- [Why Wonder Woman Is The Best DCEU Movie So Far](https://www.cinemablend.com/news/1666420/why-wonder-woman-is-the-best-dceu-movie-so-far)
- [Average movie length](https://www.google.com/search?q=the+average+movie+length&rlz=1C5CHFA_enUS877US877&oq=the+average+movie&aqs=chrome.1.69i57j0l7.7070j0j7&sourceid=chrome&ie=UTF-8)
- [Best Business Decisions Made by Actors](https://www.investopedia.com/financial-edge/0912/actors-who-got-a-share-of-film-profits.aspx) 
- [Advice from Robert Downey Jr](https://www.newyorker.com/culture/cultural-comment/advice-for-robert-downey-jr-avengers-ultron-cultural-genocide) 
- [Quantitative analysis of the evolution of novelty in cinema through crowdsourced keywords](https://www.nature.com/articles/srep02758)
- [10 Reasons Why Everyone Has Seen a Superhero Movie](https://medium.com/framerated/10-reasons-why-superhero-films-are-so-popular-2ce69d2d93ea)
- [Popular Sci-Fi Films: What Makes Them So Great?](https://vusf.wordpress.com/2015/11/13/popular-sci-fi-films-what-makes-them-so-great/)
- [Hollywood’s Obsession with Blockbusters](https://hbr.org/2013/06/hollywoods-obsession-with-blockbusters)
- [Genre trends in global film production](https://stephenfollows.com/genre-trends-global-film-production/)
- [Who earns more: a director or an actor of a movie?](https://www.quora.com/Who-earns-more-a-director-or-an-actor-of-a-movie)
- [Rethinking the Seasonal Strategy](https://www.newyorker.com/magazine/2015/02/23/rethinking-seasonal-strategy)
- [Dump months](https://en.wikipedia.org/wiki/Dump_months)
- [How Are Movie Release Dates Chosen?](https://entertainment.howstuffworks.com/how-are-movie-release-dates-chosen2.htm)