ReadMe File for 895_Project GitHub Repository
Author: Austin Abbott, aabbo005@odu.edu
Date Last Modified: 4/19/2020

DESCRIPTION OF FILES:

1) Project_Plan.pdf
This document contains my original machine learning goals for this project
	Changes:
	a. All data at 2.5m (Temp, Salinity, PAR) was unavailable from the SHEBA data repo, and is thus omitted from the final product (data was there, but was all NaN's).
	b. I completely ran out time to address wind speed as a potential predictor variable.  This may be explored further in the future.

2) Data_Exploration.ipynb
This script focused on processing the raw data, mostly by resampling.  All raw data was recorded at hourly intervals, but I needed cumulative measurements as machine learning inputs.
Some hourly and daily data visualization is included, but ultimately does not reflect the final predictor variables used in the models.  Raw data files available upon request.

3) model_input.csv
This data file contains 22 discrete time points and associated data values between Buoy data (2018) and SHEBA data (1998).  Variables presented in this file are those used in the 
machine learning scripts.
	Description of Variables:
	a. Date: Date string presented as d-month.  Ignore any year values.  This column should only be used for user reference, never for plotting or data analysis.
	b. Date_Julian: 3 digit Julian date (1-365) independent of year
	c. DMP_NoWater: Melt Pond Fraction.  The "NoWater" portion indicates that these data reflect pond fraction of a 2D ice flow, NOT pond fraction of an entire 2D scene to include
	   open water.  For example, a DMP_NoWater value of 0.2 means that 20% of the ice was ponded.
	d. Lat: Average latitude for the associated date (since station/buoys drift slowly throughout the day)
	e. Lon: Average longitude for the associated date (since station/buoys drift slowly throughout the day)
	f. Hrs_Above_Frz_Ice_Since_Jun1: CUMULATIVE hours above freezing (since June 1st) as measured at the ice surface
	g. Cum_Surface_Irradiance_SinceJun1: CUMULATIVE downwelling irradiance (PAR: 400-700nm) since June 1st measured at the surface of the ice (umol photon / m^2)
	h. Cum_SubSurface_Irradiance_SinceJun1: CUMULATIVE downwelling irradiance (PAR: 400-700nm) since June 1st measured on the underside of the ice (umol photon / m^2)
	   The ice was around 1m thick for the buoy data, and 2-3m thick for the SHEBA data.  Not used as a predictor variable as it reduced model score, but still available to use.
	i. Source: Source of data.  Buoy7 and Buoy8 are collectively referred to as just "Buoy" data in the machine learning scripts.
	j. Split: Used when I manually assign train/test split data points in the machine learning scripts.  Further explained in comments in the scripts.

4) Project_Script_Final.ipynb
Machine learning script that predicts melt pond fraction ("DMP_NoWater") from predictor variables outlined above. Explores the effectiveness of using a Random Forest Regressor from
Python's sklearn package.  Looks at the use of the LeaveOneOut approach, as well as manually selecting training and testing data.

5) MLP_Final.ipynb
Extension of Project_Script_Final.  Looks at using the MLP Regressor opposed to the Random Forest.



