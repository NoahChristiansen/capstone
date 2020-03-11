# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: TMDB Box Office Prediction


<img src="./images/capstone_pic.jpg" width="600px">

(Artist: Serbinka From Shutterstock)

### Table of Contents:

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Sources](#Sources)

---

### Problem Statement

According to the [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/), in 2019, there was about 1.24 billion Movie Tickets sold in the North American Region. If you think about it, that was just a fraction of what the Worldwide Tickets sales were in 2019. Given that information, one could now assume that there must be a great deal of money going to the Movie Industry. So how do we, as Movie Lovers, determine this amount of cash flow? We will have to focus on the Movie's revenue. In other words, **can we predict a Movie's Worldwide Box Office revenue?**

We could use a [dataset](https://www.kaggle.com/c/tmdb-box-office-prediction/data) with over 7,000 past films from [The Movie Database](https://www.themoviedb.org/) that has selected features. In particular, those features are cast, crew, plot keywords, budget, posters, release dates, languages, production companies, countries and others. Then we select the appropriate features to train various regression models with custom hyperparameters. Afterwards, we will use our models' $R^2$ scores to determine the best model to answer this inquiry. In other words, our goal is to assist production compaines with deciding how they should invest to gain a return. 


---

### Executive Summary

We began by importing the two data sets, training and testing, from The Movie Database. We have two datasets because our training dataset needed to be fitted on our testing dataset to be able to evaluate our model. Both datasets have twenty three feature columns of a particular movie. However, the training data set had an additional column called revenue which was our target variable.

Once, we looked through the dataframes, we did some data cleaning. We dropped unrelated features, dealt with missing values, fixed datatypes, and extracted data from specific features. Then, we inspected that our observations were not complete for our modeling, so we decided to completely change our datasets into numerical data. We used one-hot encoding for the selected categorical features and used a numerical rating structure for other selected features. As a result, we had to feature engineered. After cleaning our datasets, we were ready to do some exploratory data analysis.

In our exploratory data analysis we used our training dataset because it had the target variable to compare to. We first checked for the summary statistics. Then, we investigated the target variable by exploring it's distribution. Then, as a result from our summary statistics analysis, we investigated selected univariate distributions. Then, we investigated correlations from selected features with the target variable. Then, we will explored the binary features' frequency count. Then, we investigated datetime features to see if time was an important factor. Finally, we determined the outliers.

Next, we were able to preprocess. We began by making sure the columns in each dataset equal to one another to be able to model. Then, we created our X features and y. Then, we train-test split. Then, we scaled our data for future use. Lastly, we determined the baseline score.

Finally, we were able to model. We modeled various regression models. We modeled Linear Regression with default hyperparameters, GridSearch on Ridge Regression, GridSearch on Lasso Regression, GridSearch on DecisionTreeRegressor, BaggedRegressor with default hyperparameters, GridSearch on RandomForestRegressor, GridSearch on AdaBoostRegressor, GridSearch on GradientBoostingRegressor, GridSearch on SVR, and GridSearch on VotingRegressor. 

In the end, we focused on the $R^2$ scores and the bias-variance tradeoff from each model to determine which model was the best to answer our problem statement.

---

### Data Dictionary

We had an [original data dictionary](https://www.kaggle.com/c/tmdb-box-office-prediction/data), yet, we did create new features into our datasets. Lets create a new dictionary. 


|Feature|Datatype|Discription|
|---|---|---|
|budget|int64|The amount money spend to make and advertise the movie.|
|original_language|int64|The language the movie's audio was originally in.|
|original_title|object|The name of the movie originally.|
|popularity|float64|The likeability score for the movie.|
|release_date|datetime64[ns]|The date the movie was released to the public.|
|runtime|float64|The full amount of time of the movie in minutes.|
|title|object|The name of the movie now.|
|month_release_date|int64|The month the movie was release to the public.|
|year_release_date|int64|The year the movie was release to the public.|
|disney_production_company|int64|The list of Disney own production companies.|
|twenty_century_fox_production_company|int64|The list of Twenty Century Fox own companies.|
|warner_bros_production_company|int64|The list of Warner Bros own compaines.|
|nbcuniversal_production_company|int64|The list of NBCUniversal own compaines.|
|sony_pictures_production_company|int64|The list of Sony Pictures own compaines.|
|paramount_pictures_production_company|int64|The list of Paramount Pictures own compaines.|
|top_twenty_keywords|int64|The list of the top twenty keywords individuals use to identify movies.|
|genres_dummies|int64|Dummy features of the `genres` feature. Genres are various forms of categories or classifications or groups of movies.|
|production_countries_dummies|int64|Dummy features of the `production countries` feature. Production countries are where movies were filmed at.|
|spoken_languages_dummies|int64|Dummy features of the `spoken_languages` feature. Spoken languages is the available audio the movie can be in.|
|status_dummies|int64|Dummy features of the `status` feature. Status tells us if the movie was released, rumored, or in post-production.|
|crew_departments_dummies|int64|Dummy features of the `crew_departments` feature. Crew departments are various departments that worked on a movie.|
|revenue|int64|The amount of money the movie has made.|


---

### Conclusions and Recommendations

|Model|GridSearched?|Training $R^2$ Score|Testing $R^2$ Score|RMSE Training|RMSE Testing|
|---|---|---|---|---|---|
|Linear|No|0.645|0.598|84910471|87509208|
|Ridge|Yes|0.639|0.602|85120645|86915069|
|Lasso|Yes|0.635|0.592|85569841|88053334|
|DecisionTreeRegressor|Yes|0.695|0.509|78257044|96578933|
|BaggingRegressor|No|0.928|0.624|38084630|84472032|
|RandomForestRegressor|Yes|0.945|0.666|33188275|79669234|
|AdaBoostRegressor|Yes|0.456|0.316|104506239|113999743|
|GradientBoostingRegressor|Yes|0.831|0.670|58259591|79246015|
|SVR|Yes|-0.140|-0.140|151216244|147152906|
|VotingRegressor|Yes|0.940|0.667|34994469|79548504|


Most of the regression models surpassed the baseline accuracy. However, SVR was not able to and in effect, could on be considered for answering our problem statement. Therefore, the best model was the **VotingRegressor** Model. We were able to combined three emsemble models: BaggingRegressor, RandomForestRegressor, and GradientBoostingRegressor in this algorithm. According to the testing $R^2$ score, the VotingRegressor was able to manage well with unknown data. However, the model was still overfit because it had low bias and high variance.

Despite the overfitting, this model can be use to predict the revenue of a movie given that we know the selected features of that particular movie. The two top features that production companies should consider to focus on to get a return on their investments should be the `budget` and `popularity` features. This is the case because these features were consistently the top two correlated features with the target variable. 

Yet, the VotingRegressor still had its limitations. We can not fully interpret it because we are only given back the average from various models. Also, if we use the wrong ensemble method for setting up the model, we will not improve our scores. In other words, we have to determine the models we use based off the bias-variance trade off to really benefit from the VotingRegressor. 

In addition, our model can improve it's $R^2$ score if we further tuned our hyperparameters and eliminated more outliers. 

In the end, we still have some recommend questions we need to ask:
- Which models will actually benefit from using the VotingRegressor?
- How can we factor in personal finances from individuals to predict revenue? 
- Will this model still be valid 5 years from now when consumer preferences/trends change when it comes to movies?
- Futhermore, will franchise movies become an important factor?
- Will we be able to determine "experience" as a potential feature for future models?


---

### Sources

- [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/)
- [TMDB Box Office Prediction](https://www.kaggle.com/c/tmdb-box-office-prediction/data) 
- [The Movie Database](https://www.themoviedb.org/)
- [Movies: What determines the success of a movie (by box office revenue)?](https://www.quora.com/Movies-What-determines-the-success-of-a-movie-by-box-office-revenue)
- [Study explores what really makes a movie successful](https://phys.org/news/2017-11-explores-movie-successful.html)
- [IMDB website](https://www.imdb.com/)
- [Boom or Bust? Factors that Influence Box Office Revenue](https://medium.com/@nealsivadas/boom-or-bust-factors-that-influence-box-office-revenue-c8e4442d141f)
- [Google Web Interface and Search Language Codes](https://sites.google.com/site/tomihasa/google-language-codes)
- [EVERY COMPANY DISNEY OWNS: A MAP OF DISNEY'S WORLDWIDE ASSETS](https://www.titlemax.com/discovery-center/money-finance/companies-disney-owns-worldwide/)
- [List of assets owned by 21st Century Fox](https://en.wikipedia.org/wiki/List_of_assets_owned_by_21st_Century_Fox)
- [List of assets owned by WarnerMedia](https://en.wikipedia.org/wiki/List_of_assets_owned_by_WarnerMedia)
- [List of assets owned by NBCUniversal](https://en.wikipedia.org/wiki/List_of_assets_owned_by_NBCUniversal)
- [Sony Pictures Entertainment Motion Picture Group](https://en.wikipedia.org/wiki/Sony_Pictures_Entertainment_Motion_Picture_Group)
- [Paramount Pictures](https://www.wikiwand.com/en/Paramount_Pictures)
- [Movie Keywords From The Numbers](https://www.the-numbers.com/movies/keywords#keyword_overview=od1)
- [The average movie length](https://www.google.com/search?q=the+average+movie+length&rlz=1C5CHFA_enUS877US877&oq=the+average+movie&aqs=chrome.1.69i57j0l7.7070j0j7&sourceid=chrome&ie=UTF-8)