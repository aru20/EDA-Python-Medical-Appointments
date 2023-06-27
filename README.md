# Explorarory Data Analysis of Medical Appointments No-Show Data
EDA-Python-Medical Appointments No-show data
## Table of Contents
* Introduction
* Data Wrangling
* Exploratory Data Analysis
* Conclusions
## Introduction
This dataset collects information from 100k medical appointments in Brazil and is focused on the question of whether or not patients show up for their appointment. 
Our goal in this analysis is to answer why 30% of patients miss their scheduled appointments. who receive treatment instructions do not show up at the next appointment time. In other words, what are the contributing factors for missing appointments?
<!---We are trying to predict the most important factors that affect the patient's attendance.-->

Some questions we can ask to help us explore the data:

* What is the ratio of people who miss appointments to those who don’t?
* Does the patient gender has a realation with the atendance?
* What is the most popular month/day/hour for not showing up?
* What is the age distribution of patients?
* Does the neighborhood play a role in making patients don't show up? "Location of the hospital"
* Which patients show up more? Does old age take better care of their health more than youth?
* Does the disease type affect the patient's show up?
## Dataset Description: 
The data set is a Medical Appointment No Shows dataset that contains information about the patients’ appointments.

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

The second value is the mean, which is the average. Patients in the data frame are, on average, 37 years old. Under that, std is the standard deviation, which measures how numerically spread out the values are, in other word, it tells how close to the mean the data points are.

The column Age has a minimum age of -1 which is erronous data, likewise,the maximum age is 115 years old which seems very high as Brazil's life expectancy for 2020 is 77 years old (please see here). We will deal with these errors in next section.

The column Handcap should be binary (True or False) but it has a max value of 4. This will need to be investigated,
