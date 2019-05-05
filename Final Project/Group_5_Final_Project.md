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

#20cm sand and 8 mg/L PAC as Al

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


#20cm sand and 4 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_8mgperL_PAC_final.txt"

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

```
