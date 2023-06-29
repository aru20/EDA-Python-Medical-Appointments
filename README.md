# Explorarory Data Analysis of Medical Appointments No-Show Data
EDA-Python-Medical Appointments No-show data
## Table of Contents
* Introduction
* Data Wrangling
* Exploratory Data Analysis
* Conclusions
## Introduction
This dataset collects information from 100k medical appointments in Brazil and is focused on whether patients show up for their appointment. 
This analysis aims to answer why 30% of patients miss their scheduled appointments. who receive treatment instructions do not show up at the next appointment time. In other words, what are the contributing factors for missing appointments?
<!---We are trying to predict the most important factors that affect the patient's attendance.-->

Some questions we can ask to help us explore the data are:

* What is the ratio of people who miss appointments to those who don’t?
* Does the patient's gender has a relation with the attendance?
* What is the most popular month/day/hour for not showing up?
* What is the age distribution of patients?
* Does the neighborhood play a role in making patients don't show up? "Location of the hospital"
* Which patients show up more? Does old age take better care of their health than youth?
* Does the disease type affect the patient's show-up?
## Dataset Description: 
The data set is a Medical Appointment No Shows dataset that contains information about the patient’s appointments.

Each patient’s record is characterized by the following features:
### Data Dictionary

* PatientID — a unique identifier of a patient
* AppointmentID — a unique identifier of an appointment
* Gender
* ScheduledDay — a day when an appointment is planned to occur.
* AppointmentDay — a real date of an appointment
* Age — a patient’s age.
* Neighborhood — a neighborhood of each patient
* Scholarship — Does the patient receive a scholarship?
* Hypertension — Does the patient have hypertension?
* Diabetes
* Alcoholism
* Handicap
* SMS_received — Has the patient received an SMS reminder?
* No_show — Has the patient decided not to show up?


### Data Information
This section will provide basic information about the data.

<img width="749" alt="image" src="https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/83191e49-6ca0-4345-999a-c73bb9ebbb47">


In the table above, the first number, the count, shows how many rows have non-missing values. In this instance, we have no missing values.

The second value is the mean, which is the average. Patients in the data frame are, on average, 37 years old. Under that, std is the standard deviation, which measures how numerically spread out the values are, in another word, it tells how close to the mean the data points are.

The column Age has a minimum age of -1 which is erroneous data, likewise, the maximum age is 115 years old which seems very high as Brazil's life expectancy for 2020 is 77 years old (please see here). We will deal with these errors in the next section.

The column Handcap should be binary (True or False) but it has a max value of 4. This will need to be investigated,# 4. Data Cleaning and Processing

# 4. Data Cleaning and Processing
In this section, we will identify missing values and duplicate values. We will also check for inconsistent values. We will also check for misspelled and outlier data.

ScheduledDay and AppointmentDay are currently objects, it will be converted to DateTime
AppointmentDay's time will be dropped (as it is set as 00:00:00)
Misspelled columns are going to be renamed.
* This data set has no missing values.
* This data set does not have duplicate appointments but has 48,228 patients that can be considered returning patients.
* For better analysis and modeling, Convert columns to their correct data types (e.g., converting dates to datetime objects).
* Renamed misspelled columns: Hipertension -> Hypertension ,Handcap ->Handicap, SMS_received-> SMSReceived
* ![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/1a4bae39-35b3-40e4-9a94-ef21e45cb2a2)
  Most of the patients are between 18 and 55 years old. It is clearly shown that the values 115 and -1 in columns are outliers. So we will eliminate the patient's records who are aged      115 years and -1years.
## 4.6 Feature engineering
We can add a new feature to the dataset — ‘Waiting Time Days’ to check how long the patient needs to wait for the appointment day. Another new feature may be ‘WeekDay’ — a weekday of an appointment. With this feature, we can analyze on which days people don’t show up more often. Similarly, add ‘Month’, and ‘Hour’ features.
## 5. Exploratory Data Analysis¶
###   5.1 Overview of No-Show
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/4f62e70d-f1ac-403e-b528-3e0f1cc61448)
It’s clear that only 20.2% of patients didn’t show up while 79.8% were present on the appointment day.
### 5.2 Age group
We created the below age group. 
AgeGroup
Less than 10    17475
10-18           11391
19-25            9733
26-35           14404
36-45           14582
46-55           15437
56-65           14203
More than 65    13294
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/e53be289-7ae8-41eb-ba30-7e05290d8b46)
The patients that seem most likely to not show up for their appointments are between 10 and 35 years old.
### 5.3 Gender
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/588dc675-f47c-43e1-97aa-ebd5ba8f0b05)

From the table above, we can clearly see that 'Female' patients usually have more appointments that 'Male' patients, they also have about the double number of missed appointments. However, looking at the percentage of missed appointments by gender shows that it is almost the same rate (about 20%). Therefore, gender does not seem to be an important feature.

### 5.4 Appointment Day
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/33ade37b-7949-4685-b143-bb8cce0ad638)
The percentage of present and absent is roughly the same across the week.
### 5.5 Waiting Time Between Booking and Medical Appointment
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/71828ccf-22ed-4651-94c3-7c3d26a6243a)
Most of the appointments are taken on the same day or within a month. There are a few appointments that are scheduled six months in advance. We created pre-appointment period groups using the distribution above.
Same day             38560
Less than a week     27276
A week               14018
Two weeks             9925
Three weeks           6859
A month               6229
More than a month     7647
unknown                  5
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/b890b369-4b8e-4e72-8fd8-0bcff616c2c5)
We can clearly identify that people missed their appointment because of the long waiting time between appointment booking and appointment day.
### 5.6 Neighborhood
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/a9df7e1a-259d-4041-972e-7918175ed44d)
Most of the neighborhoods have the same percentage of no-shows. So this analysis will not help us derive any significant predictions.
### 5.7 SMS Received
![image](https://github.com/aru20/EDA-Python-Medical-Appointments/assets/73730336/59f1a3ce-dff2-4fcf-8e91-8cdb1aeecee4)
The above chart shows that the patients who received SMS notifications missed their appointments more than those patients who did not receive SMS.
## Conclusions

* It is observed that only 20.2% of patients didn't show up for their appointments, while 79.8% were present on the appointment day.

* The analysis suggests that the gender of a patient does not have a significant influence on whether the patient shows up or not. In other words, the attendance rate does not vary significantly between genders.

* The age group of patients seems to have an impact on their attendance. Specifically, patients between the ages of 10 and 35 are more likely to not show up for their appointments. It implies that this age group may have factors or circumstances that make them more prone to missing their scheduled appointments.

* The analysis indicates that the time between the patient scheduling their appointment and the actual appointment date affects whether the patient shows up or not. Patients are more likely to show up if there is a shorter time gap between the scheduling and appointment date. Conversely, patients may miss their appointments if there is a long waiting time between booking and the appointment day. This suggests that reducing the waiting time may lead to improved attendance rates.

* The analysis reveals that the percentage of patients who received a text message is slightly more likely to not show up compared to patients who did not receive a text message. However, the difference in attendance rates between the two groups is small.

