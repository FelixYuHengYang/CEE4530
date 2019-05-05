#Group 5 - Lab Fire Final Project
##A Study of Sand Filtration

##Introduction
Current AguaClara technology utilizes enclosed stacked rapid sand filters (ESTaRS), which is itself an innovation upon traditional rapid sand filters that saves floor space. It does so by placing several beds of sand on top of one another between inlet and outlet pipes. However, it is possible that even more space could be conserved by reducing the height of each bed of sand. Conserving space and thus money is important because a part of AguaClara's mission is to create the most affordable technology possible without compromising on the quality of the water that is produced. This research project seeks to discover the effect of different sand media as well as coagulant dosage on wastewater filtration.

##Objectives
ESTaRS currently uses 20 cm of sand for each bed, which is lower than the current industry standard of 50 cm to 75 cm. That reduced depth was arbitrarily chosen. Since there was no significant adverse effect of the function of the sand filters except for a reduction in time until backwash is needed, it is likely that other combinations of sand types could provide more effective filtration in the system.

The hypothesis for this experiment is that lowering the sand filter depth will decrease the failure time of the system, until the depth matches that of the mass transfer zone, when the failure time will equal three minutes.

Group 5 (Lab Fire) will test this hypothesis by running experiments, varying the depth of the sand filter bed and coagulant dose, and controlling for flow rate, humic acid, and influent turbidity. Failure time is determined as the time at which the filter no longer produces water that is below 1 NTU.


##Resources needed to conduct experiments – What tools will you use?
Tubing: #18 tubing for water influent, #14 tubing for stock solution influent
Filter Column: 1 inch Diameter Schedule 80 Clear PVC Pipe 12"
Pump: 1
Valves: 4   
Sand: To be determined as experiments are conducted
Turbidimeters: 2
Clay: To be determined as experiments are conducted


##References/Bibliography

Adelman Michael J., Weber-Shirk Monroe L., Cordero Anderson N., Coffey Sara L., Maher William J., Guelig Dylan, Will Jeffrey C., Stodter Sarah C., Hurst Matthew W., and Lion Leonard W. “Stacked Filters: Novel Approach to Rapid Sand Filtration.” Journal of Environmental Engineering 138, no. 10 (October 1, 2012): 999–1008. https://doi.org/10.1061/(ASCE)EE.1943-7870.0000562.

Adelman Michael J., Weber-Shirk Monroe L., Will Jeffrey C., Cordero Anderson N., Maher William J., and Lion Leonard W. “Novel Fluidic Control System for Stacked Rapid Sand Filters.” Journal of Environmental Engineering 139, no. 7 (July 1, 2013): 939–46. https://doi.org/10.1061/(ASCE)EE.1943-7870.0000700.

Reynolds, T. D., and P. A. Richards. Unit Operations and Processes in Environmental Engineering. Boston, MA: PWS Publishing Company, 1996.

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import aguaclara.core.physchem as pc
import aguaclara.core.utility as ut
import numpy as np
import matplotlib.pyplot as plt
from scipy.interpolate import make_interp_spline, BSpline
import collections
import os
from pathlib import Path
import pandas as pd

Diameter_Column=.957*u.inch
Area_Column=Diameter_Column**2*u.pi
Filtration_Velocity=1.8*u.mm/u.s
Q_Filter=(Area_Column*Filtration_Velocity).to(u.mL/u.s)
Q_Filter_hour=(Q_Filter*3600*u.s).to(u.L)
Q_Filter_hour
Fourteen_tubing = 0.21 *u.mL/u.revolution
Eighteen_tubing = 3.8 *u.mL/u.revolution
RPM = (Q_Filter/(Fourteen_tubing+Eighteen_tubing)).to(u.turn/u.min)
RPM
Q_stock_minute = RPM*Fourteen_tubing
Q_water = RPM*Eighteen_tubing
Q_water*60*3*u.min

C_Clay_Filter=(5*u.NTU).to(u.mg/u.L)
C_Clay_Filter
C_Clay_Stock = (Q_Filter*C_Clay_Filter/Q_stock_minute).to(u.mg/u.L)
C_Clay_Stock
Volume_Stock_6hrs=(Q_stock_minute*60*u.min*6).to(u.L)
Volume_Stock = 4*u.L
Mass_Clay_Stock=C_Clay_Stock*Volume_Stock
Mass_Clay_Stock

Mass_HA_Stock = 0.1*Mass_Clay_Stock
C_HA_Stock = Mass_HA_Stock/Volume_Stock

#For PACl = 2mg/L
C_PACl_Filter=2*u.mg/u.L ##This is variable
C_PACl_Stock = (Q_Filter*C_PACl_Filter/Q_stock_minute).to(u.mg/u.L)
C_PACl_Stock
C_PACl_La =70.28*u.mg/u.mL

Dilution_Factor=(C_PACl_La)/(C_PACl_Stock).to(u.mg/u.mL)
Dilution_Factor
##this is in a 4 L ucket
V_Conc=(C_PACl_Stock*Volume_Stock/C_PACl_La)
V_Conc

#Duplicate the code above to get the 1 mg/L and 0 mg/L masses and volumes for the stock solutions

C_PACl_Filter=1*u.mg/u.L ##This is variable
C_PACl_Stock = (Q_Filter*C_PACl_Filter/Q_stock_minute).to(u.mg/u.L)
C_PACl_Stock
C_PACl_La =70.28*u.mg/u.mL

V_Conc=(C_PACl_Stock*Volume_Stock/C_PACl_La)
V_Conc


#Analyzing data

#20cm fine sand and 8 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_8 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_8mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_8 = pd.read_csv(dfp_20_8,delimiter='\t')

#Column headers
list(df_20_8)

#Set the start index of the data file
start_20_8=1

#The inlet turbidity data is in column 1
column_inlet_20_8=5

#The outlet turbidity data is in column 1
column_outlet_20_8=4

#Extracting the inlet data
Inlet_20_8=epa.column_of_data(dfp_20_8,start_20_8,column_inlet_20_8)

#Extracting the outlet data
Outlet_20_8=epa.column_of_data(dfp_20_8,start_20_8,column_outlet_20_8)

#Extracting the corresponding time data and convert to seconds
Time_20_8 = epa.column_of_time(dfp_20_8,start_20_8).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_8,Inlet_20_8,'r',label='Inlet Turbidity')
ax.plot(Time_20_8,Outlet_20_8,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_8_PAC')
plt.show()

#Failure plot
fig, ax = plt.subplots()
ax.plot(Time_20_8,Inlet_20_8,'r',label='Inlet Turbidity')
ax.plot(Time_20_8,Outlet_20_8,'k', label='Outlet Turbidity')
plt.axvline(x=60, label='Filtration Start').set_color("green")
plt.axvline(x=260, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_8_PAC_failure')
plt.show()


#20cm fine sand and 4 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_4mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_4 = pd.read_csv(dfp_20_4,delimiter='\t')

#Column headers
list(df_20_4)

#Set the start index of the data file
start_20_4=9

#The inlet turbidity data is in column 1
column_inlet_20_4=5

#The outlet turbidity data is in column 1
column_outlet_20_4=4

#Extracting the inlet data
Inlet_20_4=epa.column_of_data(dfp_20_4,start_20_4,column_inlet_20_4)

#Extracting the outlet data
Outlet_20_4=epa.column_of_data(dfp_20_4,start_20_4,column_outlet_20_4)

#Extracting the corresponding time data and convert to seconds
Time_20_4 = epa.column_of_time(dfp_20_4,start_20_4).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_4,Inlet_20_4,'r',label='Inlet Turbidity')
ax.plot(Time_20_4,Outlet_20_4,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_4_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_20_4 = np.linspace(Time_20_4.min(),Time_20_4.max(),300)
spl_inlet_20_4 = make_interp_spline(Time_20_4, Inlet_20_4, k=3)
Inlet_20_4_smooth = spl_inlet_20_4(Smoothing_20_4)

spl_outlet_20_4 = make_interp_spline(Time_20_4, Outlet_20_4, k=3)
Outlet_20_4_smooth = spl_outlet_20_4(Smoothing_20_4)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_20_4,Inlet_20_4_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_20_4,Outlet_20_4_smooth,'k', label='Outlet Turbidity')
plt.axvline(x=60, label='Filtration Start').set_color("green")
plt.axvline(x=860, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_4_PAC_failure')
plt.show()

#20cm fine sand and 2 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_2mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_2 = pd.read_csv(dfp_20_2,delimiter='\t')

#Column headers
list(df_20_2)

#Set the start index of the data file
start_20_2=20

#The inlet turbidity data is in column 1
column_inlet_20_2=5

#The outlet turbidity data is in column 1
column_outlet_20_2=4

#Extracting the inlet data
Inlet_20_2=epa.column_of_data(dfp_20_2,start_20_2,column_inlet_20_2)

#Extracting the outlet data
Outlet_20_2=epa.column_of_data(dfp_20_2,start_20_2,column_outlet_20_2)

#Extracting the corresponding time data and convert to seconds
Time_20_2 = epa.column_of_time(dfp_20_2,start_20_2).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_2,Inlet_20_2,'r',label='Inlet Turbidity')
ax.plot(Time_20_2,Outlet_20_2,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_2_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_20_2 = np.linspace(Time_20_2.min(),Time_20_2.max(),300)
spl_inlet_20_2 = make_interp_spline(Time_20_2, Inlet_20_2, k=3)
Inlet_20_2_smooth = spl_inlet_20_2(Smoothing_20_2)

spl_outlet_20_2 = make_interp_spline(Time_20_2, Outlet_20_2, k=3)
Outlet_20_2_smooth = spl_outlet_20_2(Smoothing_20_2)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_20_2,Inlet_20_2_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_20_2,Outlet_20_2_smooth,'k', label='Outlet Turbidity')
plt.axvline(x=150, label='Filtration Start').set_color("green")
plt.axvline(x=350, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_2_PAC_failure')
plt.show()

#20cm fine sand and 1 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_1mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_1 = pd.read_csv(dfp_20_1,delimiter='\t')

#Column headers
list(df_20_1)

#Set the start index of the data file
start_20_1=1

#The inlet turbidity data is in column 1
column_inlet_20_1=5

#The outlet turbidity data is in column 1
column_outlet_20_1=4

#Extracting the inlet data
Inlet_20_1=epa.column_of_data(dfp_20_1,start_20_1,column_inlet_20_1)

#Extracting the outlet data
Outlet_20_1=epa.column_of_data(dfp_20_1,start_20_1,column_outlet_20_1)

#Extracting the corresponding time data and convert to seconds
Time_20_1 = epa.column_of_time(dfp_20_1,start_20_1).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_1,Inlet_20_1,'r',label='Inlet Turbidity')
ax.plot(Time_20_1,Outlet_20_1,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=8000,left=0);
plt.ylim(bottom=0,top=8);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_1_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_20_1 = np.linspace(Time_20_1.min(),Time_20_1.max(),300)
spl_inlet_20_1 = make_interp_spline(Time_20_1, Inlet_20_1, k=3)
Inlet_20_1_smooth = spl_inlet_20_1(Smoothing_20_1)

spl_outlet_20_1 = make_interp_spline(Time_20_1, Outlet_20_1, k=3)
Outlet_20_1_smooth = spl_outlet_20_2(Smoothing_20_1)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_20_1,Inlet_20_1_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_20_1,Outlet_20_1_smooth,'k', label='Outlet Turbidity')
plt.axvline(x=150, label='Filtration Start').set_color("green")
plt.axvline(x=350, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_1_PAC_failure')
plt.show()

#15cm fine sand, 5 cm coarse sand and 8 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_8 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_8mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_8 = pd.read_csv(dfp_15_5_8,delimiter='\t')

#Column headers
list(df_15_5_8)

#Set the start index of the data file
start_15_5_8=15

#The inlet turbidity data is in column 1
column_inlet_15_5_8=5

#The outlet turbidity data is in column 1
column_outlet_15_5_8=4

#Extracting the inlet data
Inlet_15_5_8=epa.column_of_data(dfp_15_5_8,start_15_5_8,column_inlet_15_5_8)

#Extracting the outlet data
Outlet_15_5_8=epa.column_of_data(dfp_15_5_8,start_15_5_8,column_outlet_15_5_8)

#Extracting the corresponding time data and convert to seconds
Time_15_5_8 = epa.column_of_time(dfp_15_5_8,start_15_5_8).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_8,Inlet_15_5_8,'r',label='Inlet Turbidity')
ax.plot(Time_15_5_8,Outlet_15_5_8,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
#plt.xlim(right=8000,left=0);
#plt.ylim(bottom=0,top=8);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_8_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_15_5_8 = np.linspace(Time_15_5_8.min(),Time_15_5_8.max(),300)
spl_inlet_15_5_8 = make_interp_spline(Time_15_5_8, Inlet_15_5_8, k=3)
Inlet_15_5_8_smooth = spl_inlet_15_5_8(Smoothing_15_5_8)

spl_outlet_15_5_8 = make_interp_spline(Time_15_5_8, Outlet_15_5_8, k=3)
Outlet_15_5_8_smooth = spl_outlet_15_5_8(Smoothing_15_5_8)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_15_5_8,Inlet_15_5_8_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_15_5_8,Outlet_15_5_8_smooth,'k', label='Outlet Turbidity')
plt.axvline(x=130, label='Filtration Start').set_color("green")
plt.axvline(x=250, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_8_PAC_failure')
plt.show()

#15cm fine sand, 5 cm coarse sand and 4 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_4mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_4 = pd.read_csv(dfp_15_5_4,delimiter='\t')

#Column headers
list(df_15_5_4)

#Set the start index of the data file
start_15_5_4=1

#The inlet turbidity data is in column 1
column_inlet_15_5_4=5

#The outlet turbidity data is in column 1
column_outlet_15_5_4=4

#Extracting the inlet data
Inlet_15_5_4=epa.column_of_data(dfp_15_5_4,start_15_5_4,column_inlet_15_5_4)

#Extracting the outlet data
Outlet_15_5_4=epa.column_of_data(dfp_15_5_4,start_15_5_4,column_outlet_15_5_4)

#Extracting the corresponding time data and convert to seconds
Time_15_5_4 = epa.column_of_time(dfp_15_5_4,start_15_5_4).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_4,Inlet_15_5_4,'r',label='Inlet Turbidity')
ax.plot(Time_15_5_4,Outlet_15_5_4,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_4_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_15_5_4 = np.linspace(Time_15_5_4.min(),Time_15_5_4.max(),100)
spl_inlet_15_5_4 = make_interp_spline(Time_15_5_4, Inlet_15_5_4, k=3)
Inlet_15_5_4_smooth = spl_inlet_15_5_4(Smoothing_15_5_4)

spl_outlet_15_5_4 = make_interp_spline(Time_15_5_4, Outlet_15_5_4, k=3)
Outlet_15_5_4_smooth = spl_outlet_15_5_4(Smoothing_15_5_4)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_15_5_4,Inlet_15_5_4_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_15_5_4,Outlet_15_5_4_smooth,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_4_PAC_failure')
plt.show()

#15cm fine sand, 5 cm coarse sand and 2 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_2mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_2 = pd.read_csv(dfp_15_5_2,delimiter='\t')

#Column headers
list(df_15_5_2)

#Set the start index of the data file
start_15_5_2=1

#The inlet turbidity data is in column 1
column_inlet_15_5_2=5

#The outlet turbidity data is in column 1
column_outlet_15_5_2=4

#Extracting the inlet data
Inlet_15_5_2=epa.column_of_data(dfp_15_5_2,start_15_5_2,column_inlet_15_5_2)

#Extracting the outlet data
Outlet_15_5_2=epa.column_of_data(dfp_15_5_2,start_15_5_2,column_outlet_15_5_2)

#Extracting the corresponding time data and convert to seconds
Time_15_5_2 = epa.column_of_time(dfp_15_5_2,start_15_5_2).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_2,Inlet_15_5_2,'r',label='Inlet Turbidity')
ax.plot(Time_15_5_2,Outlet_15_5_2,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=3000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_2_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_15_5_2 = np.linspace(Time_15_5_2.min(),Time_15_5_2.max(),500)
spl_inlet_15_5_2 = make_interp_spline(Time_15_5_2, Inlet_15_5_2, k=3)
Inlet_15_5_2_smooth = spl_inlet_15_5_2(Smoothing_15_5_2)

spl_outlet_15_5_2 = make_interp_spline(Time_15_5_2, Outlet_15_5_2, k=3)
Outlet_15_5_2_smooth = spl_outlet_15_5_2(Smoothing_15_5_2)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_15_5_2,Inlet_15_5_2_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_15_5_2,Outlet_15_5_2_smooth,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=3000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_2_PAC_failure')
plt.show()

#15cm fine sand, 5 cm coarse sand and 1 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_1mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_1 = pd.read_csv(dfp_15_5_1,delimiter='\t')

#Column headers
list(df_15_5_1)

#Set the start index of the data file
start_15_5_1=1

#The inlet turbidity data is in column 1
column_inlet_15_5_1=5

#The outlet turbidity data is in column 1
column_outlet_15_5_1=4

#Extracting the inlet data
Inlet_15_5_1=epa.column_of_data(dfp_15_5_1,start_15_5_1,column_inlet_15_5_1)

#Extracting the outlet data
Outlet_15_5_1=epa.column_of_data(dfp_15_5_1,start_15_5_1,column_outlet_15_5_1)

#Extracting the corresponding time data and convert to seconds
Time_15_5_1 = epa.column_of_time(dfp_15_5_1,start_15_5_1).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_1,Inlet_15_5_1,'r',label='Inlet Turbidity')
ax.plot(Time_15_5_1,Outlet_15_5_1,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=11);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_1_PAC')
plt.show()

#Smooth the model by using spline function
Smoothing_15_5_1 = np.linspace(Time_15_5_1.min(),Time_15_5_1.max(),300)
spl_inlet_15_5_1 = make_interp_spline(Time_15_5_1, Inlet_15_5_1, k=3)
Inlet_15_5_1_smooth = spl_inlet_15_5_1(Smoothing_15_5_1)

spl_outlet_15_5_1 = make_interp_spline(Time_15_5_1, Outlet_15_5_1, k=3)
Outlet_15_5_1_smooth = spl_outlet_15_5_1(Smoothing_15_5_1)

#Failure plot
fig, ax = plt.subplots()
ax.plot(Smoothing_15_5_1,Inlet_15_5_1_smooth,'r',label='Inlet Turbidity')
ax.plot(Smoothing_15_5_1,Outlet_15_5_1_smooth,'k', label='Outlet Turbidity')
plt.axvline(x=120, label='Filtration Start').set_color("green")
plt.axvline(x=1100, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=11);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_1_PAC_failure')
plt.show()

```
