## BELLABEAT SMART DEVICE ANALYSIS PROJECT
**By** Abode Sodiq

**Company:** Bellabeat				

**Industry:** Healthcare		

**Position:** Junior Data Analyst

**Date:** FEBRUARY 2024

_In this case study I  analyzed smart device usage data to gain insight into how consumers use non-Bellabeat smart devices, determine trends, and give high-level recommendations for how these trends can inform Bellabeat's marketing strategy based on those findings._

### Table of Content
### 1.0 Summary 
### 2.0 Introduction
### 2.1 About the company 
### 2.2 Founders
### 2.3 Smart Device
### 2.3.1 Bellabeat Smart Device
### 2.4 Purpose of analysis
### 2.5 Significance of analysis 
### 3.0 Business task 
### 3.1 Key task
### 3.2 Stakeholder
### 4.0 Data source
### 4.1 Integration step taken 
### 4.2 Data cleaning tools
### 4.3 Data cleaning and manipulation
### 4.4 Conclusion 
### 5.0 Analysis summary and key findings
### 5.1 Tracker distance 
### 5.2 BMI (Body mass index) 
### 5.2.1 BMI Calculation 
### 5.3 Fitness tracker
### 5.3.1 Percentage of sensors in 187 trackers
### 5.4 Daily steps and calories 
### 5.5 Age range
### 6.0 Recommendation 
### Reference


### 1.0 SUMMARY 
My name is Abode Sodiq, and I work as a junior data analyst at Bellabeat. We're known for creating some of the first wearable devices made just for women, and we've expanded to develop a range of digital products aimed at helping women track and enhance their health. The business task for this project is to analyze smart device usage data, identify trends in consumer behavior, and apply these insights to Bellabeat customers. 

The goal is to understand how consumers use non-Bellabeat smart devices, extrapolate relevant trends, and use this information to influence Bellabeat's marketing strategy for a selected product. The deliverables include a clear summary of the task, a description of data sources, documentation of data cleaning or manipulation, a summary of the analysis with supporting visualizations and key findings, and high-level content recommendations based on the insights gained. 

### 2.1 ABOUT THE COMPANY 
A pioneer in the fem-tech realm, Bellabeat is a women’s wellness company that has helped millions of women track their cycles and pregnancies, and live more in sync with their cycles. Founded in 2014, Bellabeat is the company that developed one of the first wearables specifically designed for women and has since gone on to create a portfolio of digital products for tracking and improving the health of women.

Focusing on creating innovative health and wellness products for women, our mission is to empower women to take control of their health by providing them with technology-driven solutions that blend design and function. Bellabeat stands as a beacon in the tech-driven wellness landscape, particularly for women. Originating from Sršen's artistic background, Bellabeat crafts beautifully designed technology that provides insights into various aspects of women's health. Founded in 2014 by Urška Sršen and Sando Mur.

### 2.2 FOUNDERS
##### 2.2.1 Urška Sršen(Co-founder & CPO) 
Urska's educational background includes studying fine arts sculpture at ALUO Ljubljana and Kuvataideakatemia in Helsinki. She brings her attention to detail and passion for design to her role at Bellabeat, where she is instrumental in the development and execution of their innovative products in the digital health market.

##### 2.2.2 Sando Mur (Co-founder & CEO)
Sandro Mur is a seasoned entrepreneur with a background in engineering. He draws inspiration from his mother and grandmother, both of whom were forward-thinking businesswomen. At Bellabeat, Sandro oversees strategy, finance, and growth. With a keen interest in startups, he established Bellabeat's investment program to support promising local talent and technology.

### 2.3 SMART DEVICE
Smart devices have revolutionized the way individuals engage with their health and wellness journeys. Specifically designed for fitness enthusiasts, these cutting-edge devices seamlessly integrate into active lifestyles, providing real-time tracking, personalized insights, and a holistic approach to well-being. 

From advanced fitness metrics to GPS-enabled workout monitoring, these smart devices empower users to optimize their workouts, set and achieve fitness goals, and enjoy a more connected and data-driven fitness experience. 

#### 2.3.1 BELLABEAT SMART DEVICE 
##### Ivy Health Tracker
Ivy is the only tracker designed and engineered for women, which correlates menstrual cycle data, lifestyle habits, and biometric readings. It Identifies self-care gaps and suggests improvements, calculates Wellness and Readiness Scores, monitors heart rate, cardiac coherence, respiratory rate, activity, and sleep. It reveals a comprehensive and accurate state of body and mind.
##### Leaf Urban & Leaf Chakra
It tracks activity, sleep, stress, meditation, and reproductive health

### 2.4 PURPOSE OF ANALYSIS 
The purpose of this analysis is to gain comprehensive insights into the usage patterns of non-Bellabeat smart devices, providing a foundation for strategic decision-making. By understanding broader market trends in smart device usage, Bellabeat can refine its products and marketing strategies to better cater to the evolving needs and preferences of its customer base.

### 2.5 SIGNIFICANCE OF ANALYSIS
Smart devices have become integral in consumers' lives, influencing lifestyle choices and well-being. Analyzing usage data helps Bellabeat align its products with consumer habits, enhancing user satisfaction. Staying abreast of trends in smart device usage provides Bellabeat with a competitive advantage. The insights derived will empower the company to innovate and differentiate its offerings in the market. 

Understanding how consumers engage with non-Bellabeat smart devices enables the tailoring of marketing strategies. Bellabeat can identify key touchpoints and market directly to potential customers with a higher likelihood of conversion. The analysis serves as a foundation for product enhancement. By recognizing successful features and usage patterns, Bellabeat can refine existing products or develop new ones that align with consumer expectations. 

The insights derived from this analysis will guide high-level decisions, from product development to marketing campaigns. Bellabeat can ensure that its strategies align with the current landscape of smart device usage.

### 3.0 BUSINESS TASK 
Leveraging Insights into Non-Bellabeat Smart Device Usage for Strategic Product Enhancement In the pursuit of sustained innovation and market relevance, Bellabeat recognizes the critical importance of understanding broader trends in smart device usage. The primary business task is to conduct a thorough analysis of non-Bellabeat smart device usage data, seeking valuable insights that can be strategically applied to enhance a selected Bellabeat product. 

This task is not only an exercise in understanding market dynamics but a strategic initiative to position Bellabeat's products in alignment with evolving consumer preferences and industry trends. By undertaking this business task, Bellabeat aims to not only stay ahead of market trends but actively shape them. It underscores a commitment to continuous improvement, innovation, and ensuring that Bellabeat products remain at the forefront of technological advancements in the smart wellness landscape.

##### 3.1 Key Task:
- Undertake a comprehensive examination of usage patterns, user behaviors, and emerging trends in the broader market of non-Bellabeat smart devices.
- Apply the derived insights judiciously to refine and elevate the features and functionalities of a chosen Bellabeat product. This involves identifying opportunities for improvement and - -aligning with consumer expectations.
- The goal is not just to keep pace with the industry but to surpass it. By leveraging insights into smart device usage, Bellabeat aims to gain a competitive edge, positioning itself as an innovative leader in the smart wellness technology sector.
- With a focus on understanding user behaviors, the business task emphasizes the importance of adopting a customer-centric approach. The end goal is to create products that seamlessly integrate into users' lives and cater to their evolving needs.
- The insights derived from this analysis will serve as a cornerstone for strategic decision-making, influencing product development, marketing strategies, and overall business planning.

### 3.2 Stakeholders
- Urska Srsen
- Sando Mur
- Bellabeat marketing analytics team

### 4.0 DATA SOURCE
##### 1. Fitbit Fitness Tracker Data (Primary Data Source suggested by Sršen):
- Nature of Data: Fitbit fitness tracker data was obtained from a public Kaggle dataset through Mobius.
- Time Range: From 12-4-2016 to 12-5-2016.
- Users: Discrepancy was found as 33 users were identified instead of the reported 30.
- Biases: Potential biases acknowledged, especially regarding missing weight and BMI data.
- Useful Information: Key metrics include total distance, tracker distance, calories burned, heart rate, and total steps.
##### 2. Ownership of Smart Wristband by Age
- Source: GWI (Q3 2022).
- Content: Percentage of male and female internet users using smart wristbands like Fitbit categorized by age group (16-64 years old).
- Purpose: Aids in determining the age range with the highest smart device usage, guiding Bellabeat's marketing strategy.
##### 3. Fitness Tracker and Smart Watches Data:
- Source: BMC Research Note
- Attributes: Includes wearable name, brand, release year, country of origin, crowdfunding status, form factor, and supported sensors.
- Collection Period: Between May 15th and July 1st, 2017.
- Purpose: Provide an overview of wearables in the market before July 2017, helping identify trends among other products.
- Sensor Mapping: Indicates specifications like accelerometer, magnetometer, gyroscope, altimeter, GPS, and optical pulse sensor.

### 4.1 INTEGRATION STEPS TAKEN 
**Data Timeframes:** Ensured alignment of timeframes across datasets for consistent analysis.

**User Identification:** Addressed the user discrepancy by cross-referencing and validating user IDs.

**Data Gaps:** Acknowledged potential biases and gaps in weight and BMI data, considering their impact on the analysis.

**Geographical Alignment:** Aligned geographical categories across datasets for a coherent understanding of regional usage patterns.

**Sensor Standardization:** Standardized sensor specifications to facilitate cross-comparison among different wearables.

This integrative approach provides a comprehensive view of smart device usage trends, ensuring the analysis is both robust and coherent across various dimensions.

### 4.2 DATA CLEANING TOOLS
A combination of **Google Sheets** and **SQL** was employed for data cleaning. Google Sheet was particularly used for tasks like date format, renaming columns, checking for duplicates, and addressing specific display issues. Bigquery Studio was used for broader data manipulation and consistency checks. Used to join tables together perfectly and create a unique ID for each username. Final data cleaning was done with Bigquery and exported for visualization. 

### 4.3 DATA CLEANING AND MANIPULATION
In the process of preparing the data for analysis, several steps were taken to ensure accuracy and consistency. Here's a breakdown of the key actions taken during data cleaning and manipulation:
##### 1. Fitbit Daily Activity Data:
Unnecessary columns like logged activities, distances, and specific minute breakdowns were removed, focusing on essential data.
Validation checks were conducted to reconcile total daily steps with calculated values in minutes and hourly steps to rectify any inconsistencies.
Total distance metrics were rounded to one decimal place for clarity and labeled accordingly.
#### 2. Calories Data:
Data sets related to daily, hourly, and minute-wise calories were organized, with particular attention to ensuring accuracy in daily calorie figures.
Ordering the data by ID and date facilitated a better understanding and correlation with other datasets.
##### 3. Steps Data:
Checks and corrections were made to daily steps data, aligning it with minute and hourly steps data for accuracy.
Date and time were separated, focusing on ascending order by date and ID for coherence.
##### 4. Sleep Data:
Sleep data, available for 24 users, was organized by separating time and date and ordering by date for subsequent correlation.
##### 5. Weight Log Information:
Data for weight log information was streamlined, emphasizing essential metrics like weight in kilograms and BMI.
Unnecessary columns such as weight in pounds, fat percentage, and manual reporting indicators were removed.
##### 6. Fitness Tracker Data:
Non-essential columns like device name and crowdfunding status were removed for clarity.
##### 7. Data Consistency and User Identification:
Ensured consistent user identification by assigning user IDs (User_1 to User_33) for each record.
Duplicate checks were performed to maintain data integrity.
##### 8. Smart Wristband and Fitness Tracker Data:
Checked and cleaned data related to smart wristbands and fitness trackers, ensuring no duplicates.

#### 4.4 CONCLUSION:
The entire process is aimed at creating a clean, consistent, and well-organized dataset ready for subsequent analysis. All steps and code used were documented for transparency and replicability. 
	

### 5.0 ANALYSIS SUMMARY AND KEY FINDINGS
##### 5.1 Tracker Distance
The analysis of total distance, representing the kilometers covered in a day, and tracker distance provides valuable insights into the usage patterns of fitness trackers among users. The combined total distance covered by all users is 5189.2 kilometers, with the tracker specifically registering a distance of 5175.8 kilometers. On average, each user travels approximately 5.5 kilometers per day. Notably, only two users (User_25 and User_26) collectively cover a distance of 13.4 kilometers without the tracker functionality activated. 

The data shows a consistent trend across all users, indicating that individuals carry their trackers with them consistently throughout the day. This observation highlights the portability and durability of fitness trackers, as well as their integration into users' daily routines. The frequent utilization of trackers during day-to-day activities suggests their practicality and reliability in supporting individuals' fitness and wellness goals.

##### 5.2 BMI (Body Mass Index)
The analysis conducted on the body mass index (BMI) data provides valuable insights into the characteristics of individuals who predominantly use fitness trackers, thereby aiding in the identification of Bellabeat's target audience. By calculating the maximum, minimum, average, and standard deviation of BMI values, we gain a comprehensive understanding of the BMI distribution among users. The BMI measurements were collected over various days within a month, revealing consistent readings with no significant fluctuations. 

This consistency underscores the reliability of the BMI data in accurately representing individuals' body compositions over time, making it a robust metric for analysis. Upon evaluating the standard BMI readings (below the table), a notable observation emerges. A proportion of individuals who utilize fitness trackers fall within the overweight and obese categories. This finding sheds light on the prevalent health trends among fitness tracker users, indicating a potential target audience for Bellabeat's wellness products and services.


Below 18.5 – you're in the underweight range. between 18.5 and 24.9 – you're in the healthy weight range. between 25 and 29.9 – you're in the overweight range. 30 or over – you're in the obese range.

##### 5.3 FITNESS TRACKER 
Upon analyzing 187 fitness trackers from different manufacturers, it became evident that certain patterns emerged in their specifications. Specifically, it was found that every fitness tracker, except for those from BellaBeat, includes accelerometers. Additionally, a significant portion of these devices also incorporate PPG sensors, while a smaller percentage feature GPS and gyroscopes. This insightful observation provides us with valuable information to tailor our product to meet customer preferences and surpass competitors in the market.
##### 5.4 Daily step and calories burn
In my analysis utilizing scatter plot charts to examine the correlation between daily step count and calorie expenditure per user, a notable trend emerged. An increase in daily steps was consistently associated with a corresponding rise in calories burned. This finding highlight the potential health benefits of regular physical activity, suggesting that higher step counts may contribute to weight management and overall well-being.
##### 5.5 Age Range
Analysis of the percentage of internet users that own wristband trackers are categorized according to their age. It was observed that from 25 to 54 years of age, the percentage of females is high when compared to males. This helps to determine the target audience for Bellabeat products which are meant for females. 

### 6.0 RECOMMENDATION
- **Product Development:** Incorporate features that align with common patterns observed in fitness tracker specifications, such as accelerometers and PPG sensors, while also considering the integration of GPS and gyroscopes to enhance the functionality and appeal of Bellabeat products such as Ivy.
- **Targeted Marketing:** Utilize the identified target audience segments, particularly females within the 25 to 54 age range, to tailor marketing strategies and messaging effectively. Highlight the health benefits of regular physical activity and the potential role of Bellabeat products in supporting weight management and overall well-being.
- **User Engagement:** Leverage the correlation between daily step count and calorie expenditure to encourage user engagement and motivation. Develop features or initiatives that promote and incentivize increased physical activity, such as challenges, rewards, or personalized insights based on individual activity levels.
- **Brand Positioning:** Emphasize Bellabeat's commitment to innovation and user-centric design, leveraging insights from the analysis to differentiate the brand in the competitive wearable technology market such as menstrual cycle calculation, state of health feelings, and pregnancy care features in ivy. Highlight the reliability, accuracy, and practicality of Bellabeat products in empowering users to achieve their fitness and wellness goals.
- **Continuous Improvement:** Invest in ongoing data collection and analysis efforts to monitor user trends, preferences, and behaviors continuously. Use iterative feedback loops to refine product offerings, marketing strategies, and user experiences, ensuring alignment with evolving customer needs and market dynamics.
- **Research and Development:** Explore avenues such as user surveys, focus groups, and usability studies to gather qualitative feedback and understand user experiences comprehensively.

Additionally, consider partnering with healthcare professionals, researchers, and industry experts to explore emerging trends, technologies, and best practices in wearable health technology. 

This proactive approach to research and development will provide valuable insights to inform product innovation, feature enhancements, and strategic decision-making, ultimately positioning Bellabeat as a leader in the wearable technology market and driving sustained growth and success for women.

## REFERENCE
- Bellabeat. (2023). Make informed decisions about your health. Every day. Retrieved February 6, 2024, from https://www.bellabeat.com
- Datareportal.(2023). Digital 2023 deep-dive: the rise of wearables. Retrieved February 6, 2024, from https://datareportal.com/reports/digital-2023-deep-dive-the-rise-of-wearables?rq=smart
- Furberg, R., Brinton, J., Keating, M., & Ortiz, A. (2016). Crowd-sourced Fitbit datasets 03.12.2016-05.12.2016 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.53894
- Henriksen, A., Woldaregay, A.Z., Muzny, M. et al. Dataset of fitness trackers and smartwatches to measuring physical activity in research. BMC Res Notes 15, 258 (2022). https://doi.org/10.1186/s13104-022-06146-5


## For inquiry,
- Email: abodesodiq195@gmail.com
- Tel: 08145313364
- LinkedIn: [Click here](https://www.linkedin.com/in/abode-sodiq-19b80418a/)


# THANK YOU

