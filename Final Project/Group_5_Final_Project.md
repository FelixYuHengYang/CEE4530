consistent#Group 5 - Lab Fire Final Project
##A Study of Sand Filtration

##Introduction
Current AguaClara technology utilizes enclosed stacked rapid sand filters (ESTaRS), which is itself an innovation upon traditional rapid sand filters that saves floor space. It does so by placing several beds of sand on top of one another between inlet and outlet pipes. However, it is possible that even more space could be conserved by reducing the height of each bed of sand. Conserving space and thus money is important because a part of AguaClara's mission is to create the most affordable technology possible without compromising on the quality of the water that is produced. This research project seeks to discover the effect of different sand media as well as coagulant dosage on wastewater filtration.

There are many relevant equations to our research, but because of the scope of the project, equations such as those that predict head-loss in the experimental apparatus, backwash velocity required to fluidize the sand bed, and others were not included. Instead, standard upflow velocities of AguaClara plants were used, to mimic plant conditions as closely as possible.

##Objectives
ESTaRS currently uses 20 cm of sand for each bed, which is lower than the current industry standard of 50 cm to 75 cm. That reduced depth was arbitrarily chosen. Since there was no significant adverse effect of the function of the sand filters except for a reduction in time until backwash is needed, it is likely that other combinations of sand types and depths could provide more effective filtration in the system.

The hypothesis for this experiment is that lowering the sand filter depth will decrease the failure time of the system, until the depth matches that of the mass transfer zone, when the failure time will equal three minutes.  

Group 5 (Lab Fire) will test this hypothesis by running experiments, varying the depth of the sand filter bed and coagulant dose, and controlling for flow rate, humic acid, and influent turbidity. Failure time is determined as the time at which the filter no longer produces water that is below 1 NTU. Another set of experiments will be ran with different sand grain sizes, while keeping the sand depth constant. It is unsure what the effect of the having heterogenous mixture of sand will be on filtration performance.

##Methods
The methods will be divided into experimental apparatus, pump, stock solution, sand column, and ProCoDA.

###Experimental apparatus
The primary goal of the experiment was to measure breakthrough time while changing parameters of the experiment. This meant that ProCoDA had to have two turbidimeters as inputs, one at the influent and one at the effluent. Before entering the influent turbidimeter, the stock tank, containing coagulant, humic acid, and clay, and a tap water source, was pumped in the flocculator where it mixed. Then, it entered through the top of the sand column, exiting out the bottom, and into the effluent turbidimeter, and finally into the drain.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/Diagram_of_setup.png" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 1: Lab apparatus diagram</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/setup.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 2: Lab apparatus set-up</p>

####Pump
Pump speed had to be determined before calculating stock solution concentrations because that would determine how much solution we would need. Pump speed also determines upflow and backwash velocity, so it was essential to calculate this first. Because Group 5 wanted to simulate plant conditions, standard upflow velocity (1.8 mm/s) for the sand column was utilized. This came out to 3.34 $mL/s$ for the variable that represented plant flow rate, $Q_{Filter}$, which corresponds to 50 rpm on the pump.

During backwash, a different pump rate than regular filtration had to be utilized. 80 rpm fluidized the bed for the homogenous sand mixture, while 50 rpm fluidized the bed for the heterogenous mixture. This lower speed for the latter was because the experiment required that the two layers of sand not mix, and a lower speed would decrease the chance that there would be mixing. Below is a picture of our pump, which combines the flow of water and liquid from our reactor before entering the flocculator. Calculations for determining pump seed can be found in the python appendix after the report.


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/pump.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 3: Microflex pump </p>

####Stock solution
The stock tank contained a 4L solution of polyaluminum chloride, humic acid, clay, and water for dilution. All stock solutions had the same amount of clay and humic acid, as to try to keep influent turbidity consistent at 5 NTU, while varying the coagulant dose from 1 mg/L to 8 mg/L of PACl. Below is a sample calculation for a 8 mg/L coagulant stock solution. See appendix for the rest of the calculations.

The conversion from clay to turbid water was used to determine the mass of clay needed. This conversion factor is 1.47 mg/L of clay for every NTU of turbidity.
$5 NTU=7.35 \frac{mg}{L} of clay$
$C_{Clay Stock} = \frac{Q_{Filter}C_{Clay Filter}}{{Q_{StockMinute}}}$
$Volume_{Reactor} = 4L$
Mass_Clay_Stock=C_Clay_Stock*Volume_Reactor
$Mass_{ClayStock}$=$561.4mg$

$Mass_{HAStock} = 0.1*Mass_{ClayStock}$
$Mass_{HAStock} = 56.1mg$

The mass of clay and humic acid stayed constant for all experiments. Only the coagulant dosage was changed. For example in case that PACl = 2 mg/L.

$C_{PACl Filter}=2*u.mg/u.L$
$C_PACl_Reactor = \frac{Q_Filter*C_{PACl Filter}}{Q_StockMinute}$
$C_{PAClReactor} = 38.19 mg/L$
$C_{PAClStock} =70.28mg/mL$
$DilutionFactor=\frac{C_{PAClStock}}{C_{PAClReactor}}$
$DilutionFactor = 1840.25$

$V_{Conc}=(C_{PAClReactor}Volume_{Reactor}/C_{PACLReactor})$
$V_{Conc} = 1086 mL$

####Flocculator
Between the pump and the influent turbidimeter was a flocculator to encourage collisions to form flocs. This was formed by wrapping flexible tubing around a graduated cylinder 12 times. The exact hydraulic residence time of the flocculator is unknown because the flexible tubing inner diameter could not be precisely determined. However, it is estimated to be around 100 seconds.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/flocculator.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 4: Flocculator with tee that combines flow on the left side </p>

####Sand Column
There were three sets of experiments ran, two with homogenous sand grain size, and one with two sand grain sizes. The first two had sand bed depths of 20 cm and 15 cm. The heterogenous mixture had 15 cm of fine grain sand, and 5 cm of coarse grain sand.

The sand bed depths were measured from the bottom of the PVC tube, which was fabricated from two 15cm clear PVC pipe that was PVC glued together. This glue obscured visibility of the middle portion of the column, but otherwise stayed water tight during experiments.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/column.jpg" alt=""/>
</p>
<p align="center">Figure 5: Flocculator with tee that combines flow on the left side </p>

####ProCoDa
ProCoDa software was used to automate experiments, and the monitor turbidity of influents and effluents. The methods file can be found in the github repository. Below is a screenshot of the software in the rules and outputs tab.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/procoda%20screenshot%201.PNG" alt=""/>
</p>
<p align="center">Figure 6: Flocculator with tee that combines flow on the left side </p>

##Procedure
This is the procedure for conducting experiments.
1. Prepare the reactor solution by mixing 561.4 mg of clay, 56.1 mg of humic acid, and specified amount of coagulant. This should be then diluted by water to create a 4L solution. Make sure stir bar is in the center mixing as to prevent particle from settling. Evaporation was an issue, so a second 4L container was placed on top of the reactor as seen in Figure 2.

2. Backwash the system to clean sand bed and to make sure there are no leaks in the system. Before starting backwash make sure the reactor is not connected to the rest of the system or else the pump will begin pumping water into the reactor, diluting the solution. Do this by unlocking the pump that holds the tube from the reactor to the flocculator, and kinking the tube manually or with a tool like a wrench.

3. Clean turbidimeter glasses because sand may enter via backwash. Use deionized water to rinse, and handle with kimwipes (or other dleicate task wipers) to avoid getting oils on the glass that may interfere with the turbidimeter function. Before placing back into turbidimeter, dry completely.

4. Run forward filtration. Keep in mind that tubing size for the water line is bigger, so the rate at which water is depleted is much faster than the rate at which the solution in the reactor is depleted. For example, the back tube in Figure 2 is connected to a (CAPACITY) gerrycan below the lab apparatus had to be filled approximately ever hour.
##Results and Discussion
##Conclusions
##Suggestions/Comments
The experiment ran into a lot of issues at every step of the way. Initially, experiments could not be ran because of problems with connecting two turbidimeters to one computer. This was not resolved for 2 weeks, delaying progress for a substantial period of time. Once this was resolved, many other issues came up that are detailed below.

* Influent NTU
  * Often was not consistently at 5 NTU despite all reactor solutions containing the same amount of clay and humic acid.
  * Often consistently decreased in NTU or increased in NTU as the experiment went on.
* Backwash procedure was not standardized
  * Backwash operation was ran until effluent was less than 1 NTU, but this was not always followed, which may have caused some consistency issues in experiments.
  * Turbidimeter glass was found to have sand grains in them after backwashing, but this was discovered late in the semester. This likely caused inaccurate turbidity measurements.
* Inner diameter of sand column
  * Inner diameter was measured in-house (0.957"), but appears to be different in manufacturer models(1.049"). This likely means that the rpm calculated for the experiments was not right.
* Choppy data
  * Data smoothing had to be employed because some experiments had very choppy data.
* Sand mixing
  * During backwash for heterogenous sand layers, the layers often mixed which was not ideal as they were supposed to be separate.
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

##Appendix
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
##Flow calculations
  Diameter_Column=.957*u.inch
Area_Column=Diameter_Column**2*u.pi
Filtration_Velocity=1.8*u.mm/u.s
Q_Filter=(Area_Column*Filtration_Velocity).to(u.mL/u.s)
Q_Filter_hour=(Q_Filter*3600*u.s).to(u.L)
Q_Filter
Fourteen_tubing = 0.21 *u.mL/u.revolution
Eighteen_tubing = 3.8 *u.mL/u.revolution
RPM = (Q_Filter/(Fourteen_tubing+Eighteen_tubing)).to(u.turn/u.min)
RPM
Q_stock_minute = RPM*Fourteen_tubing
Q_water = RPM*Eighteen_tubing
Q_water*60*3*u.min

##Flocculator information
ID_Flocculator=4*u.mm
Area_Flocculator_Tube=ID_Flocculator**2*u.pi
Grad_Cylinder_Diam=4*u.inch
Wraps=12
V_Flocculator=Area_Flocculator_Tube*Wraps*2*u.pi*Grad_Cylinder_Diam
V_Flocculator.to(u.L)
HRT_Flocculator=(V_Flocculator/Q_Filter).to(u.s)
HRT_Flocculator
##Stock calculations
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
V_Conc.to(u.uL)

#Duplicate the code above to get the 1 mg/L and 0 mg/L masses and volumes for the stock solutions

C_PACl_Filter=1*u.mg/u.L ##This is variable
C_PACl_Stock = (Q_Filter*C_PACl_Filter/Q_stock_minute).to(u.mg/u.L)
C_PACl_Stock
C_PACl_La =70.28*u.mg/u.mL

V_Conc=(C_PACl_Stock*Volume_Stock/C_PACl_La)
V_Conc

V_Conc_8mL_Coag=u.uL*8695
V_Conc_4mL_Coag=u.uL*4347
V_Conc_2mL_Coag=u.uL*2174
V_Conc_1mL_Coag=u.uL*1087
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

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_8_PAC')
plt.show()

#Failure plot
fig, ax = plt.subplots()
ax.plot(Time_20_8,Inlet_20_8,'r',label='Inlet Turbidity')
ax.plot(Time_20_8,Outlet_20_8,'k', label='Outlet Turbidity')
plt.axvline(x=260, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_8_PAC_failure')
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

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_4_PAC')
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
plt.axvline(x=860, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_4_PAC_failure')
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

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_2_PAC')
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
plt.axvline(x=350, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_2_PAC_failure')
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

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_1_PAC')
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
plt.axvline(x=350, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/20_sand_1_PAC_failure')
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
Smoothing_15_5_4 = np.linspace(Time_15_5_4.min(),Time_15_5_4.max(),300)
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
plt.axvline(x=1100, label='Breakthrough Point')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=11);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_5_coarse_1_PAC_failure')
plt.show()

#15cm fine sand and 8 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_8 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_8mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_8 = pd.read_csv(dfp_15_8,delimiter='\t')

#Column headers
list(df_15_8)

#Set the start index of the data file
start_15_8=1

#The inlet turbidity data is in column 5
column_inlet_15_8=5

#The outlet turbidity data is in column 4
column_outlet_15_8=4

#Extracting the inlet data
Inlet_15_8=epa.column_of_data(dfp_15_8,start_15_8,column_inlet_15_8)

#Extracting the outlet data
Outlet_15_8=epa.column_of_data(dfp_15_8,start_15_8,column_outlet_15_8)

#Extracting the corresponding time data and convert to seconds
Time_15_8 = epa.column_of_time(dfp_15_8,start_15_8).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_8,Inlet_15_8,'r',label='Inlet Turbidity')
ax.plot(Time_15_8,Outlet_15_8,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
plt.axvline(x=30, label='Filtration Start').set_color("green")
plt.axvline(x=110, label='Breakthrough Point')
ax.legend()
#plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_8_PAC')
plt.show()

#15cm fine sand and 4 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_4mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_4 = pd.read_csv(dfp_15_4,delimiter='\t')

#Column headers
list(df_15_4)

#Set the start index of the data file
start_15_4=1

#The inlet turbidity data is in column 5
column_inlet_15_4=5

#The outlet turbidity data is in column 4
column_outlet_15_4=4

#Extracting the inlet data
Inlet_15_4=epa.column_of_data(dfp_15_4,start_15_4,column_inlet_15_4)

#Extracting the outlet data
Outlet_15_4=epa.column_of_data(dfp_15_4,start_15_4,column_outlet_15_4)

#Extracting the corresponding time data and convert to seconds
Time_15_4 = epa.column_of_time(dfp_15_4,start_15_4).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_4,Inlet_15_4,'r',label='Inlet Turbidity')
ax.plot(Time_15_4,Outlet_15_4,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
plt.axvline(x=50, label='Filtration Start').set_color("green")
plt.axvline(x=160, label='Breakthrough Point')
ax.legend()
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_4_PAC')
plt.show()

#15cm fine sand and 2 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_2mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_2 = pd.read_csv(dfp_15_2,delimiter='\t')

#Column headers
list(df_15_2)

#Set the start index of the data file
start_15_2=1

#The inlet turbidity data is in column 5
column_inlet_15_2=5

#The outlet turbidity data is in column 4
column_outlet_15_2=4

#Extracting the inlet data
Inlet_15_2=epa.column_of_data(dfp_15_2,start_15_2,column_inlet_15_2)

#Extracting the outlet data
Outlet_15_2=epa.column_of_data(dfp_15_2,start_15_2,column_outlet_15_2)

#Extracting the corresponding time data and convert to seconds
Time_15_2 = epa.column_of_time(dfp_15_2,start_15_2).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_2,Inlet_15_2,'r',label='Inlet Turbidity')
ax.plot(Time_15_2,Outlet_15_2,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
plt.axvline(x=60, label='Filtration Start').set_color("green")
plt.axvline(x=100, label='Breakthrough Point')
ax.legend()
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_2_PAC')
plt.show()

#15cm fine sand and 1 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_1mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_1 = pd.read_csv(dfp_15_1,delimiter='\t')

#Column headers
list(df_15_1)

#Set the start index of the data file
start_15_1=4

#The inlet turbidity data is in column 5
column_inlet_15_1=5

#The outlet turbidity data is in column 4
column_outlet_15_1=4

#Extracting the inlet data
Inlet_15_1=epa.column_of_data(dfp_15_1,start_15_1,column_inlet_15_1)

#Extracting the outlet data
Outlet_15_1=epa.column_of_data(dfp_15_1,start_15_1,column_outlet_15_1)

#Extracting the corresponding time data and convert to seconds
Time_15_1 = epa.column_of_time(dfp_15_1,start_15_1).to(u.s).magnitude

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_1,Inlet_15_1,'r',label='Inlet Turbidity')
ax.plot(Time_15_1,Outlet_15_1,'k', label='Outlet Turbidity')
plt.xlabel('Time (s)')
plt.ylabel('Turbidity (NTU)')
plt.axvline(x=20, label='Filtration Start').set_color("green")
plt.axvline(x=150, label='Breakthrough Point')
ax.legend()
plt.xlim(left=0,right=1000);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Final Project/Images/15_sand_1_PAC')
plt.show()
```
