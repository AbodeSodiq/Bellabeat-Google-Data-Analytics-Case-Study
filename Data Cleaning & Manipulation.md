## SQL Analysis with BigQuery
### Introduction
> In this case study I  analyze smart device usage data to gain insight into how consumers use non-Bellabeat smart devices, determine trends, and give high-level recommendations for how these trends can inform Bellabeat's marketing strategy based on those finding using SQL queries in BigQuery. All the code snippets provided below are written in SQL.
### Data cleaning and manipulation
> New **daily_activities_info** table created
`````
CREATE TABLE `case-study-capsone.smart_device_usage.daily_activities_info` 
AS
SELECT
  id,
  ActivityDate,
  TotalSteps,
  TotalDistance,
  TrackerDistance,
  Calories
FROM `case-study-capsone.smart_device_usage.daily_activities`
`````
![Daily activity info table](https://github.com/AbodeSodiq/Bellabeat-Google-Data-Analytics-Case-Study/blob/main/Tables/Daily_activity_info.png)

> The three columns in the uploaded **heartrate_seconds_merged** from FItbase data appeared merged in one column named **string_field_0** which was then splitted. Average daily heartrate table was created.
##### Separate merged heartrate column
````
CREATE TABLE `case-study-capsone.smart_device_usage.heartrate_second` AS 
SELECT
    SPLIT(string_field_0, ',')[OFFSET(0)] AS Id,
    SPLIT(string_field_0, ',')[OFFSET(1)] AS dateandtime,
    SPLIT(string_field_0, ',')[OFFSET(2)] AS value
FROM
  `case-study-capsone.smart_device_usage.heartrate_seconds`
    
## Create daily_heatrate table
### split date and time column
CREATE TABLE `case-study-capsone.smart_device_usage.daily_heartrate` 
AS
SELECT
    Id,
    value AS heartrate_seconds,
    SPLIT(dateandtime, " ")[OFFSET(0)] AS date
FROM
    (SELECT
      SPLIT(string_field_0, ',')[OFFSET(0)] AS Id,
      SPLIT(string_field_0, ",")[OFFSET(1)] AS dateandtime,
      SPLIT(string_field_0, ',')[OFFSET(2)] AS value
    FROM
      `case-study-capsone.smart_device_usage.heartrate_seconds`)
````

##### Cast table
`````
SELECT
    Id,
    value AS heartrate_seconds,
    PARSE_DATE('%m/%d/%Y', SPLIT(dateandtime, " ")[OFFSET(0)]) AS date
    FROM
    (SELECT
      SAFE_CAST(SPLIT(string_field_0, ',')[OFFSET(0)] AS INT64) AS Id,
      SPLIT(string_field_0, ",")[OFFSET(1)] AS dateandtime,
      SAFE_CAST(SPLIT(string_field_0, ',')[OFFSET(2)] AS INT64) AS value
    FROM
    `case-study-capsone.smart_device_usage.heartrate_seconds`)
`````
    
> final createed table without first row 
`````
CREATE TABLE `case-study-capsone.smart_device_usage.daily_heartrate_seconds`
AS
SELECT
    Id,
    value AS heartrate_seconds,
    PARSE_DATE('%m/%d/%Y', SPLIT(dateandtime, ' ')[OFFSET(0)]) AS date
FROM (
    SELECT
        SAFE_CAST(SPLIT(string_field_0, ',')[OFFSET(0)] AS INT64) AS Id,
        SPLIT(string_field_0, ',')[OFFSET(1)] AS dateandtime,
        SAFE_CAST(SPLIT(string_field_0, ',')[OFFSET(2)] AS INT64) AS value
    FROM
        `case-study-capsone.smart_device_usage.heartrate_seconds`
    WHERE
        NOT STARTS_WITH(string_field_0, 'Id,Time,Value')
)
`````
> Average heartrate with ROUND UP
````
CREATE TABLE `case-study-capsone.smart_device_usage.daily_avg_heartrate` AS
SELECT 
  t1.Id,
  t1.date AS Date, 
  CEIL(AVG(t1.heartrate_seconds)) AS Avg_heartrate
FROM `case-study-capsone.smart_device_usage.daily_heartrate_seconds` AS t1
GROUP BY 
  t1.Id,
  t1.date
ORDER BY 
  t1.Id
 ````
![Daily_avg_heartrate](https://github.com/AbodeSodiq/Bellabeat-Google-Data-Analytics-Case-Study/blob/main/Tables/Daily_avg_heartrate.png)

> A Temporary General Table was created by joining tables together

A temporary merged table created 
````
CREATE TABLE `case-study-capsone.smart_device_usage.daily_activity_temp` AS 
SELECT
  Table1.id AS Id,
  Table1.ActivityDate AS Date,
  ROUND(Table1.TotalDistance, 1) AS Total_Distance,
  ROUND(Table1.TrackerDistance, 1) AS Tracker_Distance,
  Table1.TotalSteps AS Total_Steps,
  Table2.WeightKg AS Weight_kg,
  Table4.Total_sleep_records,
  Table4.Total_time_in_bed,
  Table1.Calories AS Calories_burn,
  Table2.BMI,
  Table3.Avg_heartrate
FROM `case-study-capsone.smart_device_usage.daily_activities_info` AS Table1
LEFT JOIN 
  `case-study-capsone.smart_device_usage.weight_info` AS Table2 
ON
  Table1.id = Table2.Id AND
  Table1.ActivityDate = Table2.Date
LEFT JOIN 
  `case-study-capsone.smart_device_usage.daily_avg_heartrate` AS Table3
ON
  Table1.id = Table3.Id AND
  Table1.ActivityDate = Table3.Date
LEFT JOIN 
  `case-study-capsone.smart_device_usage.daily_sleep` AS Table4 
ON
  Table1.id = Table4.Id AND
  Table1.ActivityDate = Table4.Sleep_day
ORDER BY
Table1.id
````
![Daily activity temporary table](https://github.com/AbodeSodiq/Bellabeat-Google-Data-Analytics-Case-Study/blob/main/Tables/Daily_activity_temp.png)

> Another column with a Unique User_id for each User ID number for easy identification was created. The User_id is from User_1 to User_33
##### Assign User_id to each id_number
````
WITH NumberedUsers AS (
  SELECT
    id AS Id_Number,
    Date,
    Total_Distance,
    Tracker_Distance,
    Total_Steps,
    Weight_kg,
    Total_sleep_records AS Total_Sleep_Records,
    Total_time_in_bed AS Total_Time_in_Bed,
    Calories_burn AS Calories_Burn,
    BMI,
    Avg_heartrate AS Avg_Heartrate,
    DENSE_RANK() OVER (ORDER BY id) AS rank
  FROM
   `case-study-capsone.smart_device_usage.daily_activity_temp`
)

SELECT
  'User_' || CAST(rank AS STRING) AS User_Id,
    Id_Number,
    Date,
    Total_Distance,
    Tracker_Distance,
    Total_Steps,
    Weight_kg,
    Total_sleep_records AS Total_Sleep_Records,
    Total_time_in_bed AS Total_Time_in_Bed,
    Calories_burn AS Calories_Burn,
    BMI,
    Avg_heartrate AS Avg_Heartrate
FROM
  NumberedUsers;
````
![User id 1-33 for each user id number table]()

> Final **General table** created
````
CREATE TABLE `case-study-capsone.smart_device_usage.smart_usage_daily_data`
AS
WITH NumberedUsers AS (
  SELECT
    id AS Id_Number,
    Date,
    Total_Distance,
    Tracker_Distance,
    Total_Steps,
    Weight_kg,
    Total_sleep_records AS Total_Sleep_Records,
    Total_time_in_bed AS Total_Time_in_Bed,
    Calories_burn AS Calories_Burn,
    BMI,
    Avg_heartrate AS Avg_Heartrate,
    DENSE_RANK() OVER (ORDER BY id) AS rank
  FROM
   `case-study-capsone.smart_device_usage.daily_activity_temp`
)

SELECT
  'User_' || CAST(rank AS STRING) AS User_Id,
    Id_Number,
    Date,
    Total_Distance,
    Tracker_Distance,
    Total_Steps,
    Weight_kg,
    Total_sleep_records AS Total_Sleep_Records,
    Total_time_in_bed AS Total_Time_in_Bed,
    Calories_burn AS Calories_Burn,
    BMI,
    Avg_heartrate AS Avg_Heartrate
FROM
  NumberedUsers;
````
![Smart usage daily data table](https://github.com/AbodeSodiq/Bellabeat-Google-Data-Analytics-Case-Study/blob/main/Tables/Smart_usage_daily_data.png)

> Calories_burn column length confirmation
###### 1
````
SELECT 
  LENGTH(CAST(Calories_Burn AS STRING)) AS lenght_burn
  FROM `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
````
###### 2
````
SELECT 
  LENGTH(CAST(Calories_Burn AS STRING)) AS lenght_burn
  FROM `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
  WHERE 
    LENGTH(CAST(Calories_Burn AS STRING)) <4
````
> Average steps and calories burn was calculated
###### average step by each users
````
CREATE TABLE `case-study-capsone.smart_device_usage.Avg_User_Steps`
AS  
SELECT
  User_Id,
  CEIL(AVG(Total_Steps)) AS avg_step
FROM `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
GROUP BY
  User_Id
````
> Average_calories_burn
````
CREATE TABLE `case-study-capsone.smart_device_usage.Avg_User_Calories`
AS
SELECT
  User_Id,
  CEIL(AVG(Calories_Burn)) AS avg_calories
FROM `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
GROUP BY
  User_Id
````
> Average steps and calories were merged
##### Merged Steps and Calories 
````
CREATE TABLE `case-study-capsone.smart_device_usage.Avg_steps_calories`
AS
SELECT 
  table1.User_Id,
  avg_step,
  avg_calories
FROM 
  `case-study-capsone.smart_device_usage.Avg_User_Steps` AS table1
LEFT JOIN
  `case-study-capsone.smart_device_usage.Avg_User_Calories` AS table2
ON
 table1.User_Id = table2.User_Id
ORDER BY 
  CAST(SUBSTRING(User_id, 6) AS INT64)
> Fitness tracker data was filtered. Minimum and maximum year was confirmed to understand the data better and it's impact on my recommendation
````
[Average steps & average calories table](

> fitness_tracker
````
CREATE TABLE `case-study-capsone.smart_device_usage.fitness_tracker`
AS
SELECT
  Company_name,
  Device_name,
  Release_year,
  Accelerometer,
  Gyroscope,
  Magnetometer,
  Barometer,
  GPS,
  PPG
FROM
  `case-study-capsone.smart_device_usage.fitness_tracker_company` 
WHERE
  Form_factor = 'tracker'
ORDER BY Release_year
````
![Fitness tracker table](https://github.com/AbodeSodiq/Bellabeat-Google-Data-Analytics-Case-Study/blob/main/Tables/Fitness_tracker.png)

> Minimum and maximum year
````
SELECT
  MIN(Release_year) AS min_value,
  MAX(Release_year) AS max_value
FROM
  `case-study-capsone.smart_device_usage.fitness_tracker_company` 
WHERE
  Release_year IS NOT NULL AND Release_year != 'NA'
## Calculation
> Difference between total tracker distance and tracker distance
````
> Sum of Tracker & total_distance
````
SELECT
  SUM(Total_Distance) AS sum_total_distance,
  SUM(Tracker_Distance) AS sum_tracker_distance
FROM
`case-study-capsone.smart_device_usage.smart_usage_daily_data`
````
> With total row
````
SELECT
  SUM(Total_Distance) AS sum_distance,
  SUM(Tracker_Distance) AS sum_tracker,
  IFNULL(User_Id, 'Total') AS User_I
FROM
  `case-study-capsone.smart_device_usage.smart_usage_daily_data`
WHERE 
  Total_Distance != Tracker_Distance
GROUP BY
  ROLLUP(User_Id);
````
> Average tracker and total distance calculation
#####Average tracker & total distance for each users
````
SELECT
  User_Id,
  ROUND(AVG(Total_Distance), 1) AS avg_total_distance,
  ROUND(AVG(Tracker_Distance), 1) AS avg_tracker_distance
FROM
`case-study-capsone.smart_device_usage.smart_usage_daily_data`
GROUP BY
  User_Id
> Percentage of each sensors was calculated for all non-Bellabeat products
````
> fitness_tracker_calculation
````
SELECT
  (COUNTIF(Accelerometer) / COUNT(Accelerometer)) * 100 AS true_accelerometer_percentage,
  (COUNTIF(Gyroscope) / COUNT(Gyroscope)) * 100 AS true_gyroscoper_percentage,
  (COUNTIF(Magnetometer) / COUNT(Magnetometer)) * 100 AS true_magnetometer_percentage,
  (COUNTIF(Barometer) / COUNT(Barometer)) * 100 AS true_barometer_percentage,
  (COUNTIF(GPS) / COUNT(GPS)) * 100 AS true_GPS_percentage,
  (COUNTIF(PPG) / COUNT(PPG)) * 100 AS true_PPG_percentage
FROM
  `case-study-capsone.smart_device_usage.fitness_tracker_info`
````
> BMI Calculation
##### Average_bmi for each users
````
SELECT
  DISTINCT(User_Id) AS User_id,
  AVG(BMI) AS avg_bmi 
FROM 
  `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
WHERE 
  BMI IS NOT NULL
GROUP BY
  User_Id
ORDER BY 
  CAST(SUBSTRING(User_id, 6) AS INT64)  
 ````   
> Other findings 
````
SELECT
  MAX(BMI) AS max_bmi, 
  MIN(BMI) AS min_bmi, 
  AVG(BMI) AS avg_bmi, 
  stddev(BMI) AS stddev_bmi 
FROM 
  `case-study-capsone.smart_device_usage.smart_usage_daily_data` 
WHERE 
  BMI IS NOT NULL
````
Kindly find the data analysis report in [README](https://medium.com/@abodesodiq195/bellabeat-project-google-data-analytics-case-study-1d793bde261e)

## THANKS
