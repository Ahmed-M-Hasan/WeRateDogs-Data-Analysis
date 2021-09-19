# WeRateDogs Data Analysis
## by Ahmed M. Hassan

## Introduction

This project is part of Udacity Data Analyst Nano-Degree. The project provide hands-on experience on a typical ETL operation where data is collected from various sources with different methods. Then, the data is assesed and the issues detected are resolved. After that, the final data set is stored in a database. Finally, the final clean data set is analyzed to reach insights supported with visuals using Pandas and Matplotlib.

## Data Wrangling

 Data form three different resources are wrangled and loaded into Pandas dataframes. The three data gathering techniques used in this project are:
- Manually downloded flat files
- Query Twitter API using tweepy library
- Programatically downloaded file using requests library

## Data Assessing

The three created dataframes are visually and programmatically assessed for quality and tidiness issues. The following issues were identified
#### Quality issues
##### `twitter_archive` dataframe
`timestamp` column has a data type of a string while it should be a datetime object.<br>
`timestamp` column doesn't have proper timestamp structure.<br>
`retweeted_status_timestamp`column has a data type of a string while it should be a datetime object.<br>
`twitter_id` column has a `int64` data type where it should be a string.<br>
`retweeted_status_id` shows some tweets that shows retweets violating the schema rule of this database (only original tweets).<br>
`in_reply_to_status_id` shows some tweets that shows retweets violating the schema rule of this database (only original tweets).<br>
`rating_numerator` column is equal to zero in two tweets.<br>
`rating_denominator` column has values that needs further investigation. values greater than 10(20 tweets) & values equal to zero.<br>
`name` column has names that can't be dog names. all of these names starts with a lowercase character except None entry.<br>
`twitter_id` contains some records that doesn't have images which violates dataframe schema.<br>
`expanded_urls` has missing records.<br>
##### `twitter_eval` dataframe
`twitter_id` column has a `int64` data type while it should be a string.<br>
##### `twitter_ann` dataframe
`twitter_id` column has a `int64` data type while it should be a string.<br>
`twitter_id` column has records representing retweets or replies. This issue was detected during cleaning process.<br>

#### Tidiness issues
##### `twitter_archive` dataframe
`doggo`, `floofer`, `pupper` & `puppo` column names are values. column name should be a variable not values.<br>
`text` column has a text and url in it. every column should have one variable<br>
##### `twitter_eval` dataframe
this dataframe forms a single observational unit with  `twitter_archive` dataframe.<br>
##### `twitter_ann` dataframe
the structure of the dataframe is not tidy. `p*`, `P*_conf`, `P*_dog` can be re-arranged to represent more clear variables.<br>

## Data Cleaning
The previous data quality and tidiness issues previously discovered in the three dataframes are resolved in this section. The data cleaning process starts with copy the initial state of all dataframes. Then, each issue is resolved in a define, code and test schema. The first part of this schema defines the issues and how it will be solved. The second part is coding the solution and run this code. Finally, the data is reviewed to ensure the desired modification has been made.

## Data Analysis
The clan dataset is further analyzed to deliver useful insights. Three main attributes were investigated and visualized in this analysis
- The `WeRateDogs` monthly account activity in terms of number of tweets and the engagement achieved monthly. The engagement was evaluated based on the number of retweets and favorites
- The effect of various parameters on the acount rating of the dogs. The parameters involved were the dog stage, breed and the number of images of the dog 
- The effect of the last three parameters on the number of tweets and favorites (i.e. account engagement) was also investigated.

##  Conclusions
The performed analysis allowed the following insights to be identified.
- December, 2015 is the month with the highest number of total retweets per month. This is the second month after the account was created
- Since then, the account shows nearly a stable trend of number of retweets. But, the monthly count of the favorites is showing an increasing trend since June, 2016.
- The trend of the number of the count of monthly retweets and favorites per tweet is showing an increasing trend. This suggests that the account owner(s) managed to keep and increase their tweets engagement on the platform
- Increasing the number of image up to three doesn't correlate with high account dog rating. Four image tweets usually has higher rating. Meanwhile, increasing number of image has significant effect on tweets engagement, i.e. the number of retweets and favorites
- `doggo_puppo` dogs has the highest account rating and tweets engagements
- `standard_poodle` is the dog breed with the highest number of retweets
- `saluki` is the dog breed with highest number of favorites and `WeRateDogs` account rating