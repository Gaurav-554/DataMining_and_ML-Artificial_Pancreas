Data Mining and Machine Learning: Artificial Pancreas Medical Control System

Background:

In this project we are considering the Artificial Pancreas medical control system, specifically the Medtronic 670G system. The Medtronic system consists of a continuous glucose monitor (CGM) and the Guardian Sensor, which is used to collect blood glucose measurements every 5 minutes. The sensor is single use and can be used continuously for 7 days after which it has to be replaced. The replacement procedures include a recalibration process that requires the user to obtain blood glucose measurements using a Contour NextLink 2.4 glucosemeter.

Note that this process also requires manual intervention. The Guardian Link Transmitter, powers the CGM sensor and sends the data to the MiniMed 670G insulin pump. The insulin pump utilizes the Smart Guard Technology that modulates the insulin delivery based on the CGM data. The SmartGuard Technology uses a Proportional, Integrative, and Derivative controller to derive small bursts of insulin also called Micro bolus to be delivered to the user. During meals, the user uses a BolusWizard to compute the amount of food bolus required to maintain blood glucose levels. The user manually estimates the amount of carbohydrate intake and enters it to the Bolus Wizard.

The Bolus Wizard is pre-configured with the correction factor, body weight, and average insulin sensitivity of the subject, and it calculates the bolus insulin to be delivered. The user can then program the MiniMed 670G infusion pump to deliver that amount. In addition to the bolus, the MiniMed 670G insulin pump can also provide a correction bolus. The correction bolus amount is provided only if the CGM reading is above a threshold (typically 120 mg/dL) and is a proportional amount with respect to the difference of the CGM reading and the threshold.

The SmartGuard technology has two methods of suspending insulin delivery: a) Suspend on low, where the insulin delivery is stopped when the CGM reading is less than a certain threshold, or b) suspend on predicted low, where the insulin delivery is stopped when the CGM reading is predicted to be less than a certain threshold. Apart from these options, insulin delivery can also be suspended manually by the user or can be suspended when the insulin reservoir is running low.

Data Description:

Two datasets have been used:
1.	Continuous Glucose Sensor Data (CGMData_Patient#.csv)
2.	Insulin Pump Data (InsulinData_Patient#.csv)

The output of the CGM sensor consists of following columns:
a.	Data-Time stamp (Columns B and C combined)
b.	5 minute filtered CGM reading in mg/dL (Column AE)
c.	ISIG value, which is the raw sensor output every 5 minutes

The output of the pump has the following information:
a.	Data-Time stamp
b.	Basal setting
c.	Micro bolus every 5 minutes
d.	Meal intake amount in terms of grams of carbohydrate
e.	Meal bolus
f.	Correction bolus
g.	Correction factor
h.	CGM calibration or insulin reservoir related alarms
i.	AUTO mode exit events and unique codes representing reasons (Column Q)

Objective:
Overall objective has been divided into 3 successive parts as explained below.

Part 1
Extract below mentioned performance metrics of an Artificial Pancreas System from sensor data.
1.	Percentage time in hyperglycemia (CGM > 180 mg/dL)
2.	Percentage of time in hyperglycemia critical (CGM > 250 mg/dL)
3.	Percentage time in range (CGM >= 70 mg/dL and CGM <= 180 mg/dL)
4.	Percentage time in range secondary (CGM >= 70 mg/dL and CGM <= 150 mg/dL)
5.	Percentage time in hypoglycemia level 1 (CGM < 70 mg/dL)
6.	Percentage time in hypoglycemia level 2 (CGM < 54 mg/dL)
Each metric has to be extracted in three different time intervals and two different modes as given below: 
•	Daytime (6 AM to midnight) with Manual Mode
•	Overnight (midnight to 6 AM) with Manual Mode
•	Whole Day (12 AM to 12 AM) with Manual Mode
•	Daytime (6 AM to midnight) with Auto Mode
•	Overnight (midnight to 6 AM) with Auto Mode
•	Whole Day (12 AM to 12 AM) with Auto Mode

Part 2:
Train and Test a machine model to distinguish between mean and no-meal time series data, and access accuracy of the trained model.

Part 3: 
Apply clustering techniques based upon carbohydrate intake data and validate them.
