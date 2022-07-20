# Analysis_on_We_RateDog_twitter_Dataset
## Project: Wrangling and Analyze Data

## <u>Introduction</u>
> This is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog.
- therefore this project covers `Gathering Data`, `Acess`, `Clean` Visualize and Draw insights

# Image prediction Dataset metadata
    -> tweet_id: the unique number for each tweet
    -> jpg_url: Link/url of the dog's image
    -> img_num: the image number with respect to the prediction eg. numbered 1 to 4
    -> p1: 1st prediction for the image in the tweet
    -> p1_conf: how confident the algorithm is in its 1st prediction
    -> p1_dog: whether or not the 1st prediction is a breed of dog
    -> p2: 2nd prediction for the image in the tweet
    -> p2_conf: how confident is the 2nd prediction
    -> p2_dog: whether or not the 2nd prediction is a breed of dog
    -> p3: 3rd prediction for the image in the tweet
    -> p3_conf: how confident is  the 3rd prediction
    -> p3_dog: whether or not the 3rd prediction is a breed of dog


# Quality issues

### <u>Image predictions Table </u>
1. the dataset contains duplicated values on the jpg_url column

2. Erroneous datatype on the `tweet_id` (int instead of float)

### <u>twitter_archive_enhanced</u>

3. has null columns

4. inconsistency in values of the name column eg. a

5. remove `HTML` from the source to make it clean

### <u>Twitter archive table</u>

6. drop columns not needed for our analysis
7. Erroneous datatypes in these columns (tweet_id, rating_denominator,rating_numerator, in_reply_to_status_id, in_reply_to_user_id, timestamp, retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp)
8. Missing values in 'name' and dog stages represented as 'None'
- Some records have more than on dog stage
- Missing URLs in expanded_urls
- Source column is in HTML-formatted string, not a normal string
- Error in dog names (e.g a,an,actually) are not a dog's name.
- text column includes a text and a short link.

# Tidiness issues

### <u>Image predictions Table </u>

- Image predictions table should be added to twitter archive table

### <u>twitter_archive_enhanced</u>

1. The four spacies of dog(doggo, floofer, pupper, puppo) should be joined in a single column named species 

### <u>tweet_json table</u>
1. Join `twitter_archive_enhanced`, `Image predictions` and `tweet_json` tables

# Cleaning Aproach!
### Define
- remove duplicated values on the image prediction dataset
- remove the HTML formating on the source column in twitter_archive_clean table
### define
- change the Datatype of the `tweet_id`, for the tree datasets
- chnage the `timestamp` on the twitter_archive_clean to datetime

#### From the twitter_archive_clean
- Drop retweeted_status_timestamp", "retweeted_status_user_id","retweeted_status_id", "in_reply_to_user_id", "in_reply_to_status_id"
- convert the four columns containing the stages of dog into one single column (doggo, floofer, pupper, puppo)
- Drop the four columns and use the newly created column (stage)
- corect the name errors and replace none with Nan

## From the `tweet_json_clean` Table
##### Clean off the HTML formating on th `source` column
change the `ID` datatype from int to Object
##### drop the folowing on the  `tweet_json_clean` table
>since some of them are almost/totally empty and some of them are not really important eg. (retweeted & favourited) since we already have the retweeted counts and the favourite counts
- in_reply_to_status_id 
- in_reply_to_status_id_str
- in_reply_to_user_id
- in_reply_to_user_id_str
- in_reply_to_screen_name
- user
- geo
- coordinates
- place
- contributors
- retweeted
- favourited
- retweeted_status              
- quoted_status_id             
- quoted_status_id_str            
- quoted_status 
>change the `id` column name to tweet_id for easy analysis

## Code
