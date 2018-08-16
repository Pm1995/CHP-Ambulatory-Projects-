# CHP-Ambulatory-Projects-

## Introduction- CHP

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture1.jpg)

Children’s Hospital of Pittsburgh
Tertiary care facility
315 beds
41 Bed ED
103 critical care beds
13 OR suites
40+ specialties

## CHP Region 

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture2.png)

Main campus – Lawrenceville
Four Ambulatory Care Centers
Seven Children’s Express Care locations
Five Specialty Care Centers

Children’s Hospitals are generally considered as not competing with ‘adult’ hospitals in their region

## Problem Description 

Patients experience a long wait time to make appointments.
The services state that they cannot increase capacity because of lack of space provided by CHP for appointments. Space is currently allocated based on doctor monthly schedules. 
CHP observes that rooms are not fully utilized during the day.
Can CHP predict room availability or additional needs to reallocate rooms between services?

## Distribution of difference between rented and actual used rooms

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture3.png)

For each session, compare rented grid and the staffed rooms as determined from the patient time in room.
Some sessions require more room than rent grid, but generally rent grid is greater than staffed rooms.

## Data Fields for patient appointment

Demographics of patient
Gender, age, zip code, insurance status, race/ethnicity
New/return
Schedule
Scheduled provider time
Actual appointment
Status: Completed, Cancelled, No-show
Patient in room time, Discharge time

## Data Fields For Room 

“Rented” rooms – For each session (AM/PM), rooms allocated to service for use in clinic
Actual room use
Not currently recorded
Derive this from the patient time in room
Determine the maximum number of patients in rooms simultaneously during a session
Verified method through one month of observation

## Room Utilization Seems Low 

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture4.png)

Actual room utilization based on patient time in room is low.
Suggests that rooms can be more effectively assigned.
Rented rooms do not account for variations in doctor schedules.

## Predictive Model 

Goal: develop a predictive model that predicts actual room use given the current state of the schedule.
2 days ahead, 1 week ahead, 2 weeks ahead
CHP can identify services that are not expected to use all of their rented rooms, and identify rooms for reallocation to services that have additional patients.

## Missing Patient Time Data 

Not all patients have rooming or discharge times recorded.
Impute missing data by estimating patient time in room conditioned on type of patient (new/return) and the scheduled appointment time.
If both rooming time and depart summary are unavailable, impute the rooming time based on the scheduled appointment time, patient type and scheduled provider time.

## Inputs for Predictive Model Room Use

Scheduled room use - Estimate patient time in room based on patient time, scheduled appointment length, and schedule appointment time.  Find maximum scheduled patients in room simultaneously.
Demographics of scheduled patients
Schedule status at time horizon
EHR data includes when appointments are made or cancelled.

## Model Evaluation 

For each model family, use 10 fold cross validation and show RMSE for 1 week look ahead.
RMSE vs complexity parameter graph for the one week model

## Model Evaluation Summary 

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture5.png)

Table with six models and RMSE for 1 Week look ahead.

## Predicting Staffed Rooms 

![alt-text](https://github.com/Pm1995/CHP-Ambulatory-Projects-/blob/master/Picture6.png)

Models will predict staffed rooms at two weeks, one week, and two working days ahead.

## Future Work 

Develop another set of models for 2 day ahead prediction
Repeat analysis for all services
Determine how to handle larger proportion of missing data cases
Develop policy for reallocating rooms based on the predictive model
Allow for a safety room




