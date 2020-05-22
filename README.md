# COMP6200 Practicals 2020 S1


COMP6200 Data Science Portfolio 
===========================

Portfolio 1
=========
**About and Dataset

My first portfolio is all about export of Ryde data from Strava, an online social network site for cycling and other sports.
This data is a log of every ride since the start of 2018 and contains summary data like the distance and average speed.
The exported data is a CSV file so that's easy to read.
The second dataset comes from an application called Golden Cheetah which provides some analytics services over ride data.

**Tasks Completed

=>) Combine these two data frames using the join method of Pandas.

1.) Remove rides with no measured power (where device_watts is False) - these are commutes or MTB rides.

2.) Let's look at the distributions of some key variables: time, distance, average speed, average power, TSS. We need to check are they normally distributed? or Skewed?

3.) Explore the relationships between the following variables. Are any of them corrolated with each other? Can we explain any relationships we observe?

4.) Some of the rides are designated as "Race" in the workout_type field, these are where I am racing and you might expect that these would be the most challenging rides. Normalised Power (NP) is a good measure of how hard a ride is. Explore the values of NP for races vs the overall set of rides to see if this hypothesis is supported. We have to check here, are races more challenging than rides in general?

5.) Let's generate a plot that summarises the number of km ridden each month over the period of the data. Overlay this with the sum of the Training Stress Score and the average of the Average Speed to generate an overall summary of activity.

**Challenge

1.) What leads to more kudos? Is there anything to indicate which rides are more popular? Explore the relationship between the main variables and kudos. Show a plot and comment on any relationship you observe.

2.) Generate another summary graph but one that shows the activity over a given month, with the sum of the values for each day of the month shown. So, if there are two rides on a given day, the graph should show the sum of the distances for these rides.

**Procedures Followed

*The first goal is to conver time/zone in Sydney so that both datase match in timezone.
*The next step is to keep only those rows of data that appear in both data frames so that we have complete data for every row. For this we need to use inner join function.
*After thus, taking device_watts == 1 so that all the True values should be displayes.
*Variables are plotted in histogram format so that we can know that which variables are Skewed? or Normal distribited?
* In this portfolio, I am also using correlation function to visualize the relationsships between the variables using pairplot and heatmap.
Elapsed_time looks like Skewed Right, distance looks like Skewed Right, Average Speed looks like left skewed, average_watts looks like Normal Distributed, TSS looks like Skewed Right
*Important used functions are Groupby function and mean function. We are doing this to know the power of NP for race and ride.
*Plot that summarises the number of km ridden each month over the period of the data for year 2018.
*Plot that summarises the number of km ridden each month over the period of the data for year 2019.


Portfolio 2
=========
**About

In portfolio 2, We are curious to analyse and visualise the most recent topic Coronavirus disease 2019 (COVID-19).
Coronavirus disease (COVID-19) is caused by the Severe acute respiratory syndrome Coronavirus 2 (SARS-CoV-2) and has had a worldwide effect.
On March 11 2020, the World Health Organization (WHO) declared it a pandemic, pointing to the over 118,000 cases of the coronavirus illness in over 110 countries and territories around the world at the time.

**Dataset

we are representing confirmed cases of COVID-19 af all the countries of the world using Johns Hopkins University. Data is disaggregated by country, regions (and sometimes states). 
This dataset includes time series data tracking the number of people affected by COVID-19 worldwide, including:
Total number of confirmed cases of COVID-19
Total number of people who have reportedly died while sick with Coronavirus
Total number of people who have reportedly recovered from it
But, here I am going to represent my portfolio only of total number of confirmed cases of COVID-19.
The other data we are also using for total population count from United Nations population Dynamicspage.

**Work Explanation

Data is fetching through URL because we want updated data daily basis. It is sourced from this upstream repository maintained by the amazing team at Johns Hopkins University center.
We have droped some unwanted columns and normalized that data.
Firstly, We choose to visualise confirmed cases of country Australia only using Loc function. Then, Our goal is to see COVID-19 confirmed cases comparison between countries. So, I am selecting five significant outbreaks countries such as Australia, China, Italy, US, and United Kingdom and plotting their data on the same graph to reproduce this visualisation.
A very useful visualisation shows the data for different countries aligned from the time that they have 100 confirmed cases. To create this figure, I need to take only the part of each time series after the value is greater than or equal to 100 and then plotting this starting at 0 on the x-axis. We are using here iloc function to retrive the index label of a data frame from where the cases is greater than and equal to 100 for all five countries.
We are using ilox function because we don't know the exact index for the confirmed cases of each country greater than 100. So iloc function heps to fecth the condition easily.

**Normalization:

Here, we want to visualise the number of cases per million people in the population.
Note, to use the population data I have to make sure that the country names match up in the different data sets. I am using replace function to modify the data and trying to matching the countries name from both population and grouped data sets. We are doing this so that we can take Totalpopulation columsns from population data set and confirmed cases from grouped data set.

**Prediction

An exponential curve has the equation  𝑦=𝑒𝑚𝑥 . It can be converted to a linear relationship by taking the logarithm of each side:  𝑙𝑜𝑔(𝑦)=𝑚𝑥 . This means that we can fit a linear regression model to the data as long as we take the log of the number of cases.
Selecting a country with a clear exponential curve (for example, the US) and building a linear regression model to predict the log of the number of case. Also, testing how well the model fits the data.
Now, We will fit lInearRegression model to USA and China Data.
Now, we are going to check china's number of cases growth if china had not acted to slow the spread of cases.


Portfolio 3
=========
**About

This Portfolio will use a set of book summaries from CMU Book Summaries Corpus. This contains a large number of summaries (16,559) and includes meta-data about the genre of the books taken from Freebase. Each book can have more than one genre and there are 227 genres listed in total.
Our goal in this portfolio is to take this data and build a predictive model to classify the books into one of the five target genres. We will need to extract suitable features from the texts and select a suitable model to classify them. We will build at least one model but We could build two and compare the results.

**Data

CMU Book Summary Dataset
Data is made available in tab-separated format but has no column headings. We can use read_csv to read this but we need to set the separator to \t (tab) and supply the column names. The names come from the ReadMe file.

**Procedures

To simplify the problem of genre prediction we will select a small number of target genres that occur frequently in the collection and select the books with these genre labels. This will give us one genre label per book.

**Tasks

The first task is to read the data. It is made available in tab-separated format but has no column headings. We can use read_csv to read this but we need to set the separator to \t (tab) and supply the column names. The names come from the ReadMe file.

We next filter the data so that only our target genre labels are included and we assign each text to just one of the genre labels. It's possible that one text could be labelled with two of these labels (eg. Science Fiction and Fantasy) but we will just assign one of those here.

**Modeling:

Firstly, we need to clean out text data as removing special characters or values and then using split function or tokenize it. Then we also need to remove stopwords.

**Methods:

We will use LabelEncoder to normalize labels. It can also be used to transform non-numerical labels (as long as they are hashable and comparable) to numerical labels. 
Transform labels back to original encoding. Transforms text to feature vectors that can be used as input to estimator. vocabulary_ Is a dictionary that converts each token (word) to feature index in the matrix, each unique token gets a feature index.
Then I applied logistic regression to pridict the model and fit the data in xtrain and ytrain so that I can evaluate accoracy score.
tfidfVectorizer is used to count the words. It helps us to knw the term frequency and inverse document frequency.
