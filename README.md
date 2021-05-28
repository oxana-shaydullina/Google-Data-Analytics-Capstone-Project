This analysis is the Case Study: 'How Does a Bike-Share Navigate Speedy Success?' from the [Google Data Analytics Certificate](http://grow.google/dataanalytics/), originally based on the case study ['Sophisticated, Clear, and Polished’: Divvy and Data Visualization](https://artscience.blog/home/divvy-dataviz-case-study) by Kevin Hartman.

## Scenario
I am a junior data analyst working in the marketing analyst team at Cyclistic, a fictional bike-share company in Chicago. The director of
marketing Lily Moreno believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my
team wants to understand how casual riders and annual members use Cyclistic bikes dierently. From these insights, the team
will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve
my recommendations, so they must be backed up with compelling data insights and professional data visualizations.

## Background
- In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that
are geotracked and locked into a network of 692 stations across Chicago.</br>
- Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One
approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and
annual memberships. 
    - Customers who purchase single-ride or full-day passes are referred to as <b>casual riders</b></br>
    - Customers who purchase annual memberships are <b>Cyclistic members</b></br>

#### =============
#### PHASE 1: ASK
#### =============

## Business Task
<p>Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the
pricing flexibility helps Cyclistic attract more customers, <b>Moreno believes that maximizing the number of annual members will be
key to future growth</b>. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very
good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and
have chosen Cyclistic for their mobility needs.</p>
<p><b>Moreno has set a clear goal</b>: Design marketing strategies aimed at converting casual riders into annual members. In order to do
that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual
riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in
analyzing the Cyclistic historical bike trip data to identify trends.</p>
<p><b>Three questions will guide the future marketing program</b>:</br>
1. How do annual members and casual riders use Cyclistic bikes dierently?</br>
2. Why would casual riders buy Cyclistic annual memberships?</br>
3. How can Cyclistic use digital media to influence casual riders to become members?</p>

Moreno has assigned me the first question to answer: <b>How do annual members and casual riders use Cyclistic bikes differently</b>?

Answering the above question will help company understand the key differences in their customer behaviors and adapt the marketing strategy targetted towards casual members so that they can be converted into an annual members.

## Key Stakeholders
- <b>Cyclistic</b>: A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself
apart by also oering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with
disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8%
of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to
work each day.
- <b>Lily Moreno</b>: The director of marketing and my manager. Moreno is responsible for the development of campaigns and
initiatives to promote the bike-share program. These may include email, social media, and other channels.
- <b>Cyclistic marketing analytics team</b>: A team of data analysts who are responsible for collecting, analyzing, and reporting
data that helps guide Cyclistic marketing strategy. I joined this team six months ago and have been busy learning about 
Cyclistic’s mission and business goals — as well as how I, as a junior data analyst, can help Cyclistic achieve them.
- <b>Cyclistic executive team</b>: The notoriously detail-oriented executive team will decide whether to approve the
recommended marketing program.

#### =================
#### PHASE 2: PREPARE
#### =================

## Sources
The data source used for analysis: previous 12 months (May 2020 to April 2021) of [Cyclistic’s historical trip data](https://divvy-tripdata.s3.amazonaws.com/index.html). The datasets have a different name because Cyclistic is a fictional company. The data has been made available by Motivate International Inc. under this [license](https://www.divvybikes.com/data-license-agreement). This is a public data that can be used to explore how different customer types are using Cyclistic bikes. However, using riders’ personally identifiable information is prohibited, meaning 
that it's not possible to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service
area or if they have purchased multiple single passes.</br>

Data is stored in a form of 12 separate zip files containing a CSV file each. 

Data passess the <b>ROCCC</b> test with a score of 4+/5:</br>
    <b>R</b>eliable - qualified yes, as it cannot be proven that the data was unbiased as the data did not have more information on the participants (age, sex, location, physical condition). Therefore further analysis is done with the assumption that the data generated reflects the overall population.</br>
    <b>O</b>riginal - yes, as the data is provided by the first party, so the its original data source is located.</br>
    <b>C</b>omprehensive - yes, as the data covers detailed trip information for the last 12 months including the location, date, time, customer type.</br>
    <b>C</b>urrent — yes, as the data is available till the last month of the current year, so it's up to date.</br>
    <b>C</b>ited — yes, as it's known where the data is retrieved from.</br>
  
#### =================
#### PHASE 3: PROCESS
#### =================  
  
## Tools
There are more than 1 million rows in total so Excel/Google Sheets are probably not the best tool for this task. Excel is limited to just over 1 million rows and Google Sheets stops at 150k. SQL seems like a better choice, but since I'm going to create final visualizations to share my findings and effectively communicate to the executive team, a separate tool would be needed. 

So the choices of tool are between R and Tableau. While R is great for doing comprehensive data analysis, Tableau Desktop is much easier to process and analyze the data, especially coupled with Prep Builder. It also produces the most compelling and sophisticated vizzes. 

Let's rock that data!

## Wrangle data and combine into a single file

Download previous 12 months (May 2020 to April 2021) of [Cyclistic’s historical trip data](https://divvy-tripdata.s3.amazonaws.com/index.html).

Unzip the files.

Create a folder on your desktop or Drive to house the files. Check appropriate file naming conventions: it should describe the content, creation date, and version of a file in its name. Rename `202104-divvy-tripdata.csv` to `202104_Cyclistic_tripdata_v1.csv`. Repeat for the rest of the files.

Create subfolders for the csv files so that there is a copy of the original data. Move the downloaded files to the appropriate subfolder.

Upload 12 csv files into Prep Builder. 

Observe there are 13 columns in each of them:

| Field name         | Field description                                            |
|--------------------|--------------------------------------------------------------|
| ride_id            | Primary Key                                                  |
| rideable_type      | Type of bike: classic_bike, docked_bike, electric_bike       |
| started_at         | Start date of the ride in a format mm/dd/yyyy hh:mm:ss AM/PM |
| ended_at           | End date of the ride in a format mm/dd/yyyy hh:mm:ss AM/PM   |
| start_station_name | Start station name                                           |
| start_station_id   | Start station ID                                             |
| end_station_name   | End station name                                             |
| end_station_id     | End station ID                                               |
| start_lat          | Start lattitude                                              |
| start_lng          | Start longitude                                              |
| end_lat            | End lattitude                                                |
| end_lng            | End longitude                                                |
| member_casual      | Type of rider: member, casual                                |


Compare the columns names and data types; as they are consistent, a union can be created to combine data into a single source for further investigation.

Create a union using <b>Wildcard</b>: in the <b>Input</b> pane select the <b>Multiple Files</b> tab, and then select <b>Wildcard</b> union. Leave <b>Matching Pattern</b> blanc, so all csv files are included. Make sure you use all data instead of sample amount: in the <b>Input</b> pane select <b>Data Sample</b> tab and click <b>Use all data</b> radio button.

## Inspect dataset to look for incongruencies

Add a Clean step.

What catches the eye first is a considerable amount of <b>nulls</b>, i.e. the absence of a values in a data field in `start_station_name`, `start_station_id`, `end_station_name`, and `end_station_id` fields: from 149K to 171K rows. 

<img width="827" alt="Screenshot 2021-05-26 at 16 54 49" src="https://user-images.githubusercontent.com/63780030/119673812-5949e280-be44-11eb-8c40-fbf08a2214b9.png">

However, it's up to 5% of total 4M rows. Such amount of missing values is not high enough to skew analysis, so go ahead and filter out particular rows with nulls, since it does not have a high weightage on the dataset.

Since it's bike trips data, calculate the duration and the distance for each trip as it is not in the dataset.

Find how much time in minutes the rider needs to cover 1 km by counting their pace:

`pace_min_km` using `ROUND([trip_duration_in_min]/[trip_distance_in_km],2)`

Add the following calculated fields: 

`trip_distance_in_km` using `ROUND(DISTANCE(MAKEPOINT([start_lat],[start_lng]),MAKEPOINT([end_lat],[end_lng]),"km"),2)`

`trip_duration_in_hrs` using `DATEDIFF('hour',[started_at],[ended_at])`

`trip_duration_in_min` using `DATEDIFF('minute',[started_at],[ended_at])`

Find out the month for further analyzing seasonal pattern of the trips:

`started_at_month` using `DATENAME('month',[started_at])`

Find out the day of the week for further analyzing the trip pattern during weekdays:

`started_at_weekday` using `DATENAME('weekday',[started_at])`

Observe newly created fields for standing out values. 

Don't exclude nulls from `pace_min_km` field as the pace will be zero if the riders returned the bike to the same station because of zeros in `trip_distance_in_km` field (which is, again, calculated as a difference between geo coordinates):

<img width="407" alt="Screenshot 2021-05-27 at 13 23 26" src="https://user-images.githubusercontent.com/63780030/119810457-ba2df500-beee-11eb-81e2-8e834fc093bf.png">

Exclude negative values from `trip_duration_in_hrs` and `trip_duration_in_min` as a trip cannot have a negative duration:

<img width="403" alt="Screenshot 2021-05-27 at 14 46 09" src="https://user-images.githubusercontent.com/63780030/119820580-48f43f00-befa-11eb-9eea-24865623b24c.png">

Inspect dataset to find more possible discrepances.

Some rides last enormous amount of time (more than 24 hours). It could be events when bikes were taken out of docks and checked for quality by Cyclistic, or just incorrectly collected data. Leave it as is.

Groom and polish the dataset a bit more: rename `member_casual` field to `rider_type`, `rideable_type` to `bike_type`.

At last, remove `File Path` column as it's automatically generated by Prep Builder and won't be needed for further analysis. 

Observe the final structure of the dataset:

| Field name           | Field description                                            |
|----------------------|--------------------------------------------------------------|
| pace_min_km          | Pace in min per km                                           |
| trip_distance_in_km  | Ride distance in km                                          |
| trip_duration_in_hrs | Ride duration in hours                                       |
| trip_duration_in_min | Ride duration in minutes                                     |
| started_at_month     | Start month of the ride                                      |
| started_at_weekday   | Start weekday of the ride                                    |
| ride_id              | Primary Key                                                  |
| bike_type            | Type of bike: classic_bike, docked_bike, electric_bike       |
| started_at           | Start date of the ride in a format mm/dd/yyyy hh:mm:ss AM/PM |
| ended_at             | End date of the ride in a format mm/dd/yyyy hh:mm:ss AM/PM   |
| start_station_name   | Start station name                                           |
| start_station_id     | Start station ID                                             |
| end_station_name     | End station name                                             |
| end_station_id       | End station ID                                               |
| start_lat            | Start lattitude                                              |
| start_lng            | Start longitude                                              |
| end_lat              | End lattitude                                                |
| end_lng              | End longitude                                                |
| rider_type           | Type of rider: member, casual                                |


Add an Output step and save the dataset `202005-202104_Cyclistic tripdata_v2.hyper` into appropriate folder.

#### =================
#### PHASE 4: ANALYZE
#### =================  

Open the dataset in Tableau desktop.

Double check the dataset and make neccesary adjustments: assign <b>Geographical Role: Longitude</b> to the fields `start_lng` and `end_lng`.

Go ahead and make the following diagrams for conducting descriptive analysis:

- Calculate the average ride duration for members vs casual riders by day of week
- Calculate the average ride duration for members vs casual riders by month
- Calculate the number of rides for members vs casual riders by day of week
- Calculate the number of rides for members vs casual riders by month
- Explore different seasons to make some initial observations
- Group the rides into six bins using the below formula to add a calculated field for analyzing the trip duration distribution: 

```
IF [Trip Duration In Min] < 5 THEN "<5 Min"
    ELSEIF [Trip Duration In Min] < 15 THEN "<15 Min"
    ELSEIF [Trip Duration In Min] < 30 THEN "<30 Min" 
    ELSEIF [Trip Duration In Min] < 60 THEN "<1 Hours" 
    ELSEIF [Trip Duration In Hrs] < 2 THEN "<2 Hours" 
    ELSEIF [Trip Duration In Hrs] < 5 THEN "<5 Hours" 
    ELSE ">5 Hours" 
END
```
- 





#### ===============
#### PHASE 5: SHARE
#### ===============

Now create sophisticated and polished [viz]() to share the findings. 

Follow these steps:

1. Take out a piece of paper and a pen and sketch some ideas for how you will visualize the data.
2. Once you choose a visual form, open your tool of choice to create your visualization — in this case, Tableau.
3. Create your data visualization in a form of dashboard, remembering that contrast should be used to draw your audience’s attention to the
most important insights. Use artistic principles including size, color, and shape.
4. Ensure clear meaning through the proper use of common elements, such as headlines, subtitles, and labels.
5. Refine your data visualization by applying deep attention to detail.
6. Ensure your work is accessible.

#### =============
#### PHASE 6: ACT
#### =============





All done! Congrats! 🥳 
