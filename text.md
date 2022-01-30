<center> <H1> Wrangle Report </H1> </center>

# Introduction

The dataset consist of three sources, first source from tweets archive of Twitter user @dog_rates (WeRateDogs), is a pre wrangled and cleaned data provided by UDACITY. The other is image prediction file with dogs breeds classification.  The third source is a tweeter archive as json file, also provided by UDACITY for students that Tweeter API access wasn't not approved.

File list:

1. twitter-archive-enhanced.csv
2. image-predictions.tsv
3. tweet-jason.txt

 # Wrangling Process


 ## Preliminary data visualization and inspection.

Searching for gross errors,  Datasets were first inspected using a spreadsheet software and text editors.

### twitter-archive-enhanced.csv

<div> <center>
<img src="enhace_LO_vis.png" alt="Drawing" style="width: 400px;"/>
</center>
</div>

<center>figure 01 - Preliminary visualization twitter archive enhanced.</center>

#### Findings:
 - found dog names as "a"
 - Missing Values Tagged as None and Nan
 - consistent with comman separated file format

### image-predictions.tsv

<div> <center>
<img src="imagepred_LOcalc.png" alt="Drawing" style="width: 400px;"/>
</center>
</div>

<center>figure 02 - Preliminary visualization image prediction file.</center>

#### Findings:
 - file in a good shape
 - consistent with tab separated file format

 ### tweer-json.txt

 <div> <center>
 <img src="jason_file_gedit.png" alt="Drawing" style="width: 400px;"/>
 </center>
 </div>

 <center>figure 03 - Preliminary visualization tweeter jason file.</center>

 #### Findings:
  - file in a good shape
  - consistent with jason file format


  ## Data Gathering with Pandas.

The three files were loaded into Pandas dataframe without any occurrence.

1. twitter-archive-enhanced.csv -> df1
2. image-predictions.tsv -> df2
3. tweet-jason.txt -> df3

## Data Assessing using Pandas


Dataframe where programmatic assessed and inspected using Pandas functions and results  with additional findings for data quality and tidiness issues.

### Findings

#### General issues

1.  Check is all df3(json file) is in df1

#### Quality issues

1. Wrong Data types: (df1)


|Column | type |
| ----- | ----- |
| in_reply_to_status_id | float64 |
| in_reply_to_user_id | float64 |
| timestamp| object |
| retweeted_status_id |float64|
| retweeted_status_user_id | float64 |
| retweeted_status_timestamp| object |


2.Lines with "Stage of" Dogs with more than one classification

3. Dog names column as 'None' (string) istead of Nan (null object) for missing Data

4. Retweets rows

5. In reply rows

6. Error getting the rate numbers like 5 instead 13.5, 75 instead 9.75, etc

7. Tweets with "This is a ---" geting Dog name as "a"

8.Not necessary Columns (df1)
- source
- in_reply_to_status_id
- in_reply_to_user_id
- retweeted_status_id
- retweeted_status_user_id
- retweeted_status_timestamp

9. Remove unnecessary columns 'doggo', 'floofer',  'pupper', 'puppo',  'stg_count'

10. Missing values handling

### Tidiness issues
1. Text Column with text and pictures URL (df1)

2. Stage of dogs in Columns (df1)

## Cleaning Data

### General Issue 01
Dataframe df3 where found entire at the df1. So df2 where left out of merging.

### Quality issue - 01
Types where fixed for appropriated.

### Quality issue - 02
Rows with more than one dog stage were removed

### Quality issue - 03
Normalized all missing value representation to np.Nan for later missing value metrics and handling.

### Quality issue - 04
Retweets rows dropped.

### Quality issue - 05
In reply rows dropped

### Quality issue - 06
Fixed number errors with proper rounding.

### Quality issue - 07
Name column entry equal 'a' and changed for NaN.

### Quality issue - 08
Dropped unnecessary columns.

### Quality issue - 09
Dropped unnecessary columns after fixing tidiness issues.

### Quality issue - 10
Filled all missing values with 'Unkown'

### Tidiness issue - 01

### Tidiness issue - 02
Created new Dog Stage column with correspondent stage.


## Storing final Result.

Final Data Set is stored in csv format as "twitter_archive_master.csv".

With file md5sum:  _c5c52abbc9a75d2e0150b2ccd7a7e5fd_

<div> <center>
<img src="final_dataframe.png" alt="Drawing" style="width: 400px;"/>
</center>
</div>

<center>figure 04 - Final data frame info.</center>
