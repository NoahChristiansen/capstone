# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone: TMDB Box Office Prediction


<img src="./images/capstone_pic.jpg" width="600px">

(Artist: Serbinka From Shutterstock)

### Table of Contents:

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Sources](#Sources)

---

### Problem Statement

According to the [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/), in 2019, there was about 1.24 billion Movie Tickets sold in the North American Region. If you think about it, that was just a fraction of what the Worldwide Tickets sales were in 2019. Given that information, one could now assume that there must be a great deal of money going to the Movie Industry. So how do we, as Movie Lovers, determine this amount of cash flow? We will have to focus on the Movie's revenue. In other words, **can we predict a Movie's Worldwide Box Office revenue?**

We could use a [dataset](https://www.kaggle.com/c/tmdb-box-office-prediction/data) with over 7,000 past films from [The Movie Database](https://www.themoviedb.org/) that has selected features. In particular, those features are cast, crew, plot keywords, budget, posters, release dates, languages, production companies, countries and others. Then we select the appropriate features to train various regression models with custom hyperparameters. Afterwards, we will use our models' accuracy scores to determine the best model to answer this inquiry.

---

### Executive Summary

We began by importing the two data sets, training and testing, from The Movie Database. We have two datasets because our training dataset needed to be fitted on our testing dataset to be able to evaluate our model. Both datasets have twenty three feature columns of a particular movie. However, the training data set had an additional column called revenue which was our target variable.

Once, we looked through the dataframes, we did some data cleaning. We dropped unrelated features, dealt with missing values, fixed datatypes, and extracted data from specific features. Then, we inspected that our observations were not complete for our modeling, so we decided to completely change our datasets into numerical data. We used one-hot encoding for the selected categorical features and used a numerical rating structure for other selected features. After cleaning our datasets, we were ready to do some exploratory data analysis.

In our exploratory data analysis we used our training data set because it has the target variable to compare to. We checked for the summary statistics and as a result, we visualized selected features' distributions. Then, we investigated the correlation of each original numerical feature and mapped features with respect to our target variable. In other words, we used visualizations to see these particular correlations. Finally, we determined the outliers.

Next, we were able to preprocess. From our exploratory data analysis, we featured engineered. (explain here) Then, we created our X feature & target variable and did a train-test split. Lastly, we determined the basline score to compare to our models' results.

Finally, we were able to model. We modeled various regression models. We modeled (what models?) In the end, we focused on accuracy score and the bias-variance tradeoff from each model to determined which model was the best to answer our problem statement.

---

### Conclusions and Recommendations


---

### Sources

- [Domestic Movie Theatrical Market Summary 1995 to 2020](https://www.the-numbers.com/market/)
- [TMDB Box Office Prediction](https://www.kaggle.com/c/tmdb-box-office-prediction/data) 
- [The Movie Database](https://www.themoviedb.org/)
- [Google Web Interface and Search Language Codes](https://sites.google.com/site/tomihasa/google-language-codes)