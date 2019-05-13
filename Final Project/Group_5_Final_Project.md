#Group 5 - Lab Fire Final Project
##A Study of Sand Filtration

##Introduction
Current AguaClara technology utilizes enclosed stacked rapid sand filters (ESTaRS), which is itself an innovation upon traditional rapid sand filters that was developed to save floor space. It does so by placing several beds of sand on top of one another between inlet and outlet pipes. However, it is possible that space could be further conserved by reducing the height of each bed of sand. Conserving space and thus money is important to AguaClara's because it's philosophy is to create the most affordable technology possible without compromising on the quality of the water that is treated. This research project seeks to discover the effect of different sand media, filter bed depth, and coagulant dosage on wastewater filtration.

There are many relevant equations to our research, but because of the scope of the project, equations such as those that predict head-loss in the experimental apparatus, backwash velocity required to fluidize the sand bed, and others were not utilized and thus not  included. Instead, standard upflow velocities of AguaClara plants were used, to mimic plant conditions as closely as possible.

##Objectives
ESTaRS currently uses 20 cm of sand for each bed, which is lower than the current industry standard of 50 cm to 75 cm. That reduced depth was arbitrarily chosen. Since there was no significant adverse effect of the function of the sand filters except for a reduction in time until backwash is needed, it is likely that other combinations of sand types and depths could provide more effective filtration in the system.

The hypothesis for this experiment is that lowering the sand filter depth will decrease breakthrough time of the system. The second hypothesis is that higher coagulant doses will correlate with decreased breakthrough times.

The reasoning behind the first hypothesis is that the decreased bed depth would decrease the amount of space flocs have to collect in the sand bed. This decreased space means that the filter bed would fail faster (decreasing the breakthrough time) as it receives the same amount of flow with a reduced capacity to filter the flow. For the second hypothesis, it is believed that the higher coagulant doses would create larger flocs than would have been possible lower coagulant doses.

Group 5 will test this hypothesis by running experiments to measure breakthrough time, varying the depth of the sand filter bed and coagulant dose while controlling for flow rate, clay humic acid, and influent turbidity. Breakthrough time is defined as the time at which the effluent turbidity is no longer lower than 30% of the influent turbidity. Another set of experiments was run with different sand grain sizes, while keeping the sand depth constant.

##Methods
The methods will be divided into experimental apparatus, pump, stock solution, sand column, and ProCoDA.

###Experimental apparatus
The primary goal of the experiment was to measure breakthrough time while changing parameters of the experiment. This meant that ProCoDA had to have two turbidimeters as inputs, one at the influent and one at the effluent. Before entering the influent turbidimeter, the stock tank, containing coagulant, humic acid, and clay, and a tap water source, was pumped in the flocculator where it mixed. Then, after going through the input turbidimeter, it entered through the top of the sand column, exiting out the bottom, and into the effluent turbidimeter, and finally into the drain. This can be better visualized in the two figures below.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/Diagram_of_setup.png" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 1: Lab apparatus diagram</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/setup.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 2: Lab apparatus set-up</p>

####Pump
Pump speed had to be determined before calculating stock solution concentrations because that would determine how much solution would be need. Pump speed also determines upflow and backwash velocity, so it was essential to calculate this first. Because Group 5 wanted to simulate plant conditions, standard upflow velocity (1.8 mm/s) for the sand column was utilized. This came out to 3.34 $mL/s$ for the variable that represented plant flow rate, $Q_{Filter}$, which corresponds to 50 RPM on the pump.

During backwash, a different pump rate than regular filtration had to be utilized. 80 RPM fluidized the bed for the homogenous sand mixture, while 50 RPM fluidized the bed for the heterogenous mixture. This lower speed for the latter was used because the experiment required that the two layers of sand not mix, and a lower speed would decrease the chance that there would be mixing. Below is a picture of the pump setup, which combines the flow of water and liquid from our reactor before entering the flocculator. Calculations for determining pump speed can be found in the python appendix after the report.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/pump.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 3: Microflex pump in the off state</p>

####Stock solution
The stock tank contained a 4L solution of polyaluminum chloride, humic acid, clay, and water for dilution. All stock solutions had the same amount of clay and humic acid, as to keep influent turbidity consistent at 5 NTU, but varied in the coagulant dose from 1 mg/L to 8 mg/L of PACl. Below is a sample calculation for a 8 mg/L coagulant stock solution. See appendix for the rest of the calculations.

The conversion from clay to turbid water was used to determine the mass of clay needed. This conversion factor is 1.47 mg/L of clay for every NTU of turbidity.

$5 NTU=7.35 \frac{mg}{L} of clay$

$C_{Clay_{Stock}} = \frac{Q_{Filter}C_{Clay_{Filter}}}{{Q_{Stock_{Minute}}}}$

$Volume_{Reactor} = 4L$

$Mass_{Clay_{Stock}}$ = $C_{Clay_{Stock}} * Volume_{Reactor}$

$Mass_{Clay_{Stock}}$=$561.4mg$

$Mass_{HA_{Stock}} = 0.1*Mass_{Clay_{Stock}}$
$Mass_{HA_{Stock}} = 56.1mg$

The mass of clay and humic acid stayed constant for all experiments. Only the coagulant dosage was changed. For example in case that PACl = 2 mg/L.

$C_{PACl_{Filter}}=2*u.mg/u.L$

$C_{PACl_{Reactor}} = \frac{Q_Filter*C_{PACl_{Filter}}}{Q_{Stock_{Minute}}}$

$C_{PACl_{Reactor}} = 38.19 mg/L$

$C_{PACl_{Stock}} =70.28mg/mL$

$DilutionFactor=\frac{C_{PACl_{Stock}}}{C_{PACl_{Reactor}}}$

$DilutionFactor = 1840.25$

$V_{Conc}=\frac{C_{PACl_{Reactor}}* Volume_{Reactor}}{C_{PACl_{Reactor}}}$

$V_{Conc} = 1086 mL$

####Flocculator
Between the pump and the influent turbidimeter was a flocculator to encourage collisions to form flocs. This was formed by wrapping flexible tubing around a graduated cylinder 12 times. The exact hydraulic residence time of the flocculator is unknown because the flexible tubing inner diameter could not be precisely determined. However, it is estimated to be around 100 seconds.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/flocculator.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 4: Flocculator with tee that combines the flow on the left side </p>

####Sand Column
Three sets of experiments were ran, two with homogenous sand grain size, and one with two sand grain sizes. The first two had sand bed depths of 20 cm and 15 cm. The heterogenous mixture had 15 cm of fine grain sand, and 5 cm of coarse grain sand.

The sand bed depths were measured from the bottom of the PVC tube, which was fabricated from two 15cm clear PVC pipe that were PVC glued together. This glue obscured visibility of the middle portion of the column, but otherwise stayed water tight during experiments.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/column.jpg" alt=""/>
</p>
<p align="center">Figure 5: 20 cm sand filter column </p>

####ProCoDA
ProCoDA software was used to automate experiments, and monitor the turbidity of the influent and effluent solutions. The methods file can be found in the Github repository. Below is a screenshot of the software in the rules and outputs tab.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/procoda%20screenshot%201.PNG" alt=""/>
</p>
<p align="center">Figure 6: ProCoDA Rules and Outputs Tab </p>

##Procedure

1. Prepare the reactor solution by mixing 561.4 mg of clay, 56.1 mg of humic acid, and specified amount of coagulant in a 6L tank. This should be then diluted by tap water to create a 4L solution. Make sure the stir bar is in the center of the tank as to prevent particles from settling. To prevent evaporation, a second 6L container was placed on top of the reactor as seen in Figure 2.

2. Backwash the system to clean sand bed and to make sure there are no leaks in the system. Before starting backwash make sure the reactor is not connected to the rest of the system or else the pump will begin pumping water into the reactor, diluting the solution. Do this by unlocking the pump that holds the tube from the reactor to the flocculator, and kinking the tube manually or with a tool like a wrench.

3. After the backwash procedure is completed, clean turbidimeter glasses because sand may enter during backwash. Use deionized water to rinse, and handle with kimwipes (or other delicate task wipers) to avoid getting oils on the glass that may interfere with the turbidimeter function. Before placing back into turbidimeter, dry completely.

4. Run forward filtration. Keep in mind that tubing size for the water line is bigger, so the rate at which water is depleted is much faster than the rate at which the solution in the reactor is depleted. For example, the back tube in Figure 2 is connected to a 20L jerrycan below the lab apparatus, which had to be filled approximately ever hour.


##Results and Discussion

From each experiment, a graph which displayed inlet and outlet turbidity versus time was generated. Since the influent turbidity was not consistently at 5 NTU, often times increasing or decreasing throughout the course of an experiment, the results were normalized so that breakthrough time was relative to the influent concentration of the experiment. Therefore the breakthrough time is the range of time when effluent concentration was below 30% of the influent concentration. The normalized graphs are shown below, except for Figure 5 as an example. See python code and GitHub for graphs that are not normalized.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_1_PAC.png" alt=""/>
</p>
<p align="center">Figure 5: Results for 20 cm sand filter column experiments </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/20_sand_8_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 6: Normalized results for 20 cm sand filter column with 8 mg/L of coagulant</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/20_sand_4_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 7: Normalized results for 20 cm sand filter column with 4 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/20_sand_2_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 8: Normalized results for 20 cm sand filter column with 2 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/20_sand_1_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 9: Normalized results for 20 cm sand filter column with 1 mg/L of coagulant </p>

The graphs above show the results for the experiments ran for 20 cm homogenous sand bed. The breakthrough times in seconds are as follows: 170, 380, 25, 1280.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_5_coarse_8_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 10: Normalized results for 15 cm fine sand and 5 cm coarse sand with 8 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_5_coarse_4_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 11: Normalized results for 15 cm fine sand and 5 cm coarse sand with 4 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_5_coarse_2_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 12: Normalized results for 15 cm fine sand and 5 cm coarse sand with 2 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_5_coarse_1_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 13: Normalized results for 15 cm fine sand and 5 cm coarse sand with 8 mg/L of coagulant </p>

The graphs above  show the results for the experiments ran for 15 and 5 cm hetereogenous sand bed. The breakthrough times in seconds are as follows: 165, 335, 295, 65.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_8_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 13: Normalized results for 15 cm fine sand with 8 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_4_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 14: Normalized results for 15 cm fine sand with 4 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_2_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 15: Normalized results for 15 cm fine sand with 2 mg/L of coagulant </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/15_sand_1_PAC_percent.png"" alt=""/>
</p>
<p align="center">Figure 16: Normalized results for 15 cm fine sand with 1 mg/L of coagulant </p>

The graphs above  show the results for the experiments ran for 15 cm homogenous sand bed. The breakthrough times in seconds are as follows: 75, 360, 80, 350.

The experiments showed that there is still a lot of knowledge about sand filtration that is lacking. It was expected that increasing the coagulant dosage and decreasing bed depth would result in a decreased breakthrough time. In addition, adding a layer of coarser sand should have increased the breakthrough time according to our hypothesis. However, this experiment did not verify the hypotheses mentioned above as there were no discernible trends (Figures 17 and 18). For both experiments, the 2 mg/L coagulant dose yielded the shortest breakthrough time in the 20 cm sand bed depth experiment (25 seconds), and the second shortest breakthrough time in the 15 cm sand bed depth experiment (80 seconds) which is inconsistent with the initial hypothesis. We believe that this is due to experimental errors and inconsistencies in the experimental procedure, which are outlined below.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/Breakthrough%20vs%20Sand%20Size.png"" alt=""/>
</p>
<p align="center">Figure 17: Breakthrough time as a function of sand bed depths </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Images/Breakthrough%20vs%20Coagulant%20Dosage.png"" alt=""/>
</p>
<p align="center">Figure 18: Breakthrough time as a function of coagulant dose</p>

##Conclusions

This experiment was conducted to investigate the effect of sand bed media, depths, and coagulant dosage on sand filtration. The purpose of the experiment was to determine which experimental setup would filter water contaminated with clay and humic acid more effectively. To quantify this objective, effective filtration was characterized as an effluent concentration that is below 30% of the influent concentration. This limit was arbitrarily set and could have been 20% or 40% of the influent NTU, but at 20% breakthrough times for some coagulant doses were zero seconds which would not have yielded any meaningful results. As stated in the objectives, breakthrough time is defined as the time at which the effluent turbidity is no longer lower than 30% of the influent turbidity. The hypotheses we had formed were that increasing the coagulant dosage and decreasing bed depth would result in a decreased breakthrough time, whereas adding a layer of coarser sand should have increased the breakthrough time. Even though we conducted various combinations of sand bed depths, media, and coagulant dosages, as well as multiple runs of each combination, clear trends were not discernable. We hypothesize that this is due to experimental errors and inconsistencies in procedure that are discussed below. Overall, it was a very interesting experiment and if there were more time in the semester we would conduct additional experiments as well as repeat the ones already conducted with a more standard procedure.

##Suggestions/Comments
The experiment ran into a lot of issues at every step of the way. Initially, experiments could not be ran because of problems with connecting two turbidimeters to one computer. This was not resolved for 2 weeks, delaying progress for a substantial period of time. Once this was resolved, many other issues came up that are detailed below.

* Influent NTU
  * Often was not consistently at 5 NTU despite all reactor solutions containing the same amount of clay and humic acid.
  * Often consistently decreased in NTU or increased in NTU as the experiment went on.
  * This could be because of inefficient mixing in the reactor, in which case a solution would be to monitor the mixing process until the solution looks very well mixed.
* Backwash procedure was not standardized
  * Backwash operation was ran until effluent was less than 1 NTU, but this was not always followed, which may have caused some consistency issues in experiments.
  * Turbidimeter glass was found to have sand grains in them after backwashing, but this was discovered late in the semester. This likely caused inaccurate turbidity measurements.
* Inner diameter of sand column
  * Inner diameter was measured in-house (0.957"), but appears to be different in manufacturer models(1.049"). This likely means that the RPM calculated for the experiments was not right.
* Sand mixing
  * Even though a slower rate (50 PRM) for backwash was used to clean the heterogenous sand mixture, the different sand layers were not easily distinguishable after backwash

##Resources needed to conduct experiments
Tubing: #18 tubing for water influent, #14 tubing for stock solution influent
Filter Column: 30 cm length 1 inch Diameter Schedule 80 Clear PVC Pipe
Pump: 1
Valves: 5   
Turbidimeters: 2
Sand: depending on the condition tested in each experiment
Clay: 561.4 mg of clay per experiment run
Humic Acid: 56 mg of humic acid per experiment run
PACl: 16303 microliters of 70.28 mg/L of PACl


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
from textwrap import wrap

##Flow calculations
Diameter_Column=.957*u.inch
Area_Column=Diameter_Column**2*u.pi
Filtration_Velocity=1.8*u.mm/u.s
Q_Filter=(Area_Column*Filtration_Velocity).to(u.mL/u.s)
Q_Filter_hour=(Q_Filter*3600*u.s).to(u.L)
Fourteen_tubing = 0.21 *u.mL/u.revolution
Eighteen_tubing = 3.8 *u.mL/u.revolution
RPM = (Q_Filter/(Fourteen_tubing+Eighteen_tubing)).to(u.turn/u.min)
Q_stock_minute = RPM*Fourteen_tubing
Q_water = RPM*Eighteen_tubing

##Flocculator information
ID_Flocculator=4*u.mm
Area_Flocculator_Tube=ID_Flocculator**2*u.pi
Grad_Cylinder_Diam=4*u.inch
Wraps=12
V_Flocculator=Area_Flocculator_Tube*Wraps*2*u.pi*Grad_Cylinder_Diam
HRT_Flocculator=(V_Flocculator/Q_Filter).to(u.s)

##Stock calculations
C_Clay_Filter=(5*u.NTU).to(u.mg/u.L)
C_Clay_Stock = (Q_Filter*C_Clay_Filter/Q_stock_minute).to(u.mg/u.L)
Volume_Stock_6hrs=(Q_stock_minute*60*u.min*6).to(u.L)
Volume_Stock = 4*u.L
Mass_Clay_Stock=C_Clay_Stock*Volume_Stock
Mass_HA_Stock = 0.1*Mass_Clay_Stock
C_HA_Stock = Mass_HA_Stock/Volume_Stock

#For the different PACl concentrations
C_PACl_Filter=8*u.mg/u.L ##This is variable
C_PACl_Stock = (Q_Filter*C_PACl_Filter/Q_stock_minute).to(u.mg/u.L)
C_PACl_Lab =70.28*u.mg/u.mL

Dilution_Factor=(C_PACl_Lab)/(C_PACl_Stock).to(u.mg/u.mL)

##this is in a 4 L bucket
V_Conc=(C_PACl_Stock*Volume_Stock/C_PACl_Lab)

V_Conc_8mL_Coag=u.uL*8695
V_Conc_4mL_Coag=u.uL*4347
V_Conc_2mL_Coag=u.uL*2174
V_Conc_1mL_Coag=u.uL*1087
V_Per_Sand_Depth=(8695+4347+2174+1087)*u.uL
V_Per_Sand_Depth

#Analyzing data

#20cm fine sand and 8 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_8 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_8mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_8 = pd.read_csv(dfp_20_8,delimiter='\t')

#Column headers
list(df_20_8)

#Set the start index of the data file
start_20_8=7

#The inlet turbidity data is in column 5
column_inlet_20_8=5

#The outlet turbidity data is in column 4
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
plt.xlim(right=2000,left=0);
plt.ylim(bottom=0,top=15);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_8_PAC')
plt.show()


Outlet_Percent_20_8 = np.divide(Outlet_20_8,Inlet_20_8)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_8,Outlet_Percent_20_8,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=2000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_8_PAC_percent')
plt.show()


Outlet_Percent_20_8_New = [x for x in Outlet_Percent_20_8 if x <= 30 and x+1<=30]
Outlet_Percent_20_8_New_Size = len(Outlet_Percent_20_8_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_20_8 = ((Outlet_Percent_20_8_New_Size)*5)
Breakthrough_Time_20_8

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
plt.xlim(right=2000,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_4_PAC')
plt.show()

Outlet_Percent_20_4 = np.divide(Outlet_20_4,Inlet_20_4)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_4,Outlet_Percent_20_4,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=2000,left=0);
plt.ylim(bottom=0,top=100);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_4_PAC_percent')
plt.show()


Outlet_Percent_20_4_New = [x for x in Outlet_Percent_20_4 if x <= 30 and x+1<=30]
Outlet_Percent_20_4_New_Size = len(Outlet_Percent_20_4_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_20_4 = ((Outlet_Percent_20_4_New_Size)*5)
Breakthrough_Time_20_4

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
plt.xlim(right=2500,left=0);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_2_PAC')
plt.show()

Outlet_Percent_20_2 = np.divide(Outlet_20_2,Inlet_20_2)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_2,Outlet_Percent_20_2,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=2500,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_2_PAC_percent')
plt.show()


Outlet_Percent_20_2_New = [x for x in Outlet_Percent_20_2 if x <= 30 and x+1<=30]
Outlet_Percent_20_2_New_Size = len(Outlet_Percent_20_2_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_20_2 = ((Outlet_Percent_20_2_New_Size)*5)
Breakthrough_Time_20_2

#20cm fine sand and 1 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_20_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/20cm_sand_1mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_20_1 = pd.read_csv(dfp_20_1,delimiter='\t')

#Column headers
list(df_20_1)

#Set the start index of the data file
start_20_1=9

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

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_1_PAC')
plt.show()

Outlet_Percent_20_1 = np.divide(Outlet_20_1,Inlet_20_1)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_20_1,Outlet_Percent_20_1,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=8000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/20_sand_1_PAC_percent')
plt.show()


Outlet_Percent_20_1_New = [x for x in Outlet_Percent_20_1 if x <= 30 and x+1<=30]
Outlet_Percent_20_1_New_Size = len(Outlet_Percent_20_1_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_20_1 = ((Outlet_Percent_20_1_New_Size)*5)
Breakthrough_Time_20_1

#15cm fine sand, 5 cm coarse sand and 8 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_8 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_8mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_8 = pd.read_csv(dfp_15_5_8,delimiter='\t')

#Column headers
list(df_15_5_8)

#Set the start index of the data file
start_15_5_8=19

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
plt.xlim(right=5000,left=0);
plt.ylim(bottom=0,top=25);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_8_PAC')
plt.show()

Outlet_Percent_15_5_8 = np.divide(Outlet_15_5_8,Inlet_15_5_8)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_8,Outlet_Percent_15_5_8,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=5000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_8_PAC_percent')
plt.show()


Outlet_Percent_15_5_8_New = [x for x in Outlet_Percent_15_5_8 if x <= 30 and x+1<=30]
Outlet_Percent_15_5_8_New_Size = len(Outlet_Percent_15_5_8_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_5_8 = ((Outlet_Percent_15_5_8_New_Size)*5)
Breakthrough_Time_15_5_8

#15cm fine sand, 5 cm coarse sand and 4 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_4mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_4 = pd.read_csv(dfp_15_5_4,delimiter='\t')

#Column headers
list(df_15_5_4)

#Set the start index of the data file
start_15_5_4=15

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

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_4_PAC')
plt.show()

Outlet_Percent_15_5_4 = np.divide(Outlet_15_5_4,Inlet_15_5_4)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_4,Outlet_Percent_15_5_4,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=3000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_4_PAC_percent')
plt.show()


Outlet_Percent_15_5_4_New = [x for x in Outlet_Percent_15_5_4 if x <= 30 and x+1<=30]
Outlet_Percent_15_5_4_New_Size = len(Outlet_Percent_15_5_4_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_5_4 = ((Outlet_Percent_15_5_4_New_Size)*5)
Breakthrough_Time_15_5_4

#15cm fine sand, 5 cm coarse sand and 2 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_2mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_2 = pd.read_csv(dfp_15_5_2,delimiter='\t')

#Column headers
list(df_15_5_2)

#Set the start index of the data file
start_15_5_2=7

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
plt.xlim(right=2500,left=0);
plt.ylim(bottom=0,top=20);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_2_PAC')
plt.show()

Outlet_Percent_15_5_2 = np.divide(Outlet_15_5_2,Inlet_15_5_2)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_2,Outlet_Percent_15_5_2,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=2500,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_2_PAC_percent')
plt.show()


Outlet_Percent_15_5_2_New = [x for x in Outlet_Percent_15_5_2 if x <= 30 and x+1<=30]
Outlet_Percent_15_5_2_New_Size = len(Outlet_Percent_15_5_2_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_5_2 = ((Outlet_Percent_15_5_2_New_Size)*5)
Breakthrough_Time_15_5_2

#15cm fine sand, 5 cm coarse sand and 1 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_5_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_5cm_coarse_1mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_5_1 = pd.read_csv(dfp_15_5_1,delimiter='\t')

#Column headers
list(df_15_5_1)

#Set the start index of the data file
start_15_5_1=12

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

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_1_PAC')
plt.show()

Outlet_Percent_15_5_1 = np.divide(Outlet_15_5_1,Inlet_15_5_1)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_5_1,Outlet_Percent_15_5_1,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=4000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_5_coarse_1_PAC_percent')
plt.show()


Outlet_Percent_15_5_1_New = [x for x in Outlet_Percent_15_5_1 if x <= 30 and x+1<=30]
Outlet_Percent_15_5_1_New_Size = len(Outlet_Percent_15_5_1_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_5_1 = ((Outlet_Percent_15_5_1_New_Size)*5)
Breakthrough_Time_15_5_1

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
ax.legend()
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_8_PAC')
plt.show()


Outlet_Percent_15_8 = np.divide(Outlet_15_8,Inlet_15_8)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_8,Outlet_Percent_15_8,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=1000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_8_PAC_percent')
plt.show()


Outlet_Percent_15_8_New = [x for x in Outlet_Percent_15_8 if x <= 30 and x+1<=30]
Outlet_Percent_15_8_New_Size = len(Outlet_Percent_15_8_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_8 = ((Outlet_Percent_15_8_New_Size)*5)
Breakthrough_Time_15_8

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
ax.legend()
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_4_PAC')
plt.show()

Outlet_Percent_15_4 = np.divide(Outlet_15_4,Inlet_15_4)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_4,Outlet_Percent_15_4,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=1000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_4_PAC_percent')
plt.show()


Outlet_Percent_15_4_New = [x for x in Outlet_Percent_15_4 if x <=30 and x+1<=30]
Outlet_Percent_15_4_New_Size = len(Outlet_Percent_15_4_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_4 = ((Outlet_Percent_15_4_New_Size)*5)
Breakthrough_Time_15_4

#15cm fine sand and 2 mg/L PAC as Al

#File path for the tab delimited file containing the experimental measurements
dfp_15_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Final%20Project/Data%20Files/15cm_sand_2mgperL_PAC_final.txt"

#Pandas dataframe with the data in the file
df_15_2 = pd.read_csv(dfp_15_2,delimiter='\t')

#Column headers
list(df_15_2)

#Set the start index of the data file
start_15_2=6

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
ax.legend()
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_2_PAC')
plt.show()

Outlet_Percent_15_2 = np.divide(Outlet_15_2,Inlet_15_2)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_2,Outlet_Percent_15_2,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=300,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_2_PAC_percent')
plt.show()


Outlet_Percent_15_2_New = [x for x in Outlet_Percent_15_2 if x <= 30 and x+1<=30]
Outlet_Percent_15_2_New_Size = len(Outlet_Percent_15_2_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_2 = ((Outlet_Percent_15_2_New_Size)*5)
Breakthrough_Time_15_2

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
ax.legend()
plt.xlim(left=0,right=7000);
plt.ylim(bottom=0,top=10);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_1_PAC')
plt.show()

Outlet_Percent_15_1 = np.divide(Outlet_15_1,Inlet_15_1)*100

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(Time_15_1,Outlet_Percent_15_1,'r', label='Percent of Inlet Turbidity in Effluent')
plt.axhline(y=30, label='Breakthrough Threshold')
plt.xlabel('Time (s)')
plt.ylabel('Percent Turbidity (%)')
ax.legend()
plt.xlim(right=5000,left=0);
plt.ylim(bottom=0,top=200);

#plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/15_sand_1_PAC_percent')
plt.show()


Outlet_Percent_15_1_New = [x for x in Outlet_Percent_15_1 if x <= 30 and x+1<=30]
Outlet_Percent_15_1_New_Size = len(Outlet_Percent_15_1_New)

#Since measurements were taken every 5 seconds:

Breakthrough_Time_15_1 = ((Outlet_Percent_15_1_New_Size)*5)
Breakthrough_Time_15_1

#Now plot the graph of breakthrough times vs sand size

Breakthrough_Times_8 = [Breakthrough_Time_20_8, Breakthrough_Time_15_5_8, Breakthrough_Time_15_8]

Breakthrough_Times_4 = [Breakthrough_Time_20_4, Breakthrough_Time_15_5_4, Breakthrough_Time_15_4]

Breakthrough_Times_2 = [Breakthrough_Time_20_2, Breakthrough_Time_15_5_2, Breakthrough_Time_15_2]

Breakthrough_Times_1 = [Breakthrough_Time_20_1, Breakthrough_Time_15_5_1, Breakthrough_Time_15_1]

Sand_Sizes = [20, 17.5, 15]


fig, ax = plt.subplots()
ax.plot(Sand_Sizes,Breakthrough_Times_8,'ro', label='PAC = 8mg/L')
ax.plot(Sand_Sizes,Breakthrough_Times_4,'co', label='PAC = 4mg/L')
ax.plot(Sand_Sizes,Breakthrough_Times_2,'ko', label='PAC = 2mg/L')
ax.plot(Sand_Sizes,Breakthrough_Times_1,'mo', label='PAC = 1mg/L')
plt.ylabel('Breakthrough Time (s)')
ax.legend()
plt.xlim(right=10,left=25);
plt.ylim(bottom=0,top=1500);

x_ticks_labels = ['20cm fine','15cm fine  5cm coarse','15cm fine']
x_ticks_labels = [ '\n'.join(wrap(l, 10)) for l in x_ticks_labels ]

# Set number of ticks for x-axis
ax.set_xticks(Sand_Sizes)
# Set ticks labels for x-axis
ax.set_xticklabels(x_ticks_labels, rotation='horizontal', fontsize=10)


plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/Breakthrough vs Sand Size')
plt.show()

Breakthrough_Times_20 = [Breakthrough_Time_20_8, Breakthrough_Time_20_4, Breakthrough_Time_20_2, Breakthrough_Time_20_1]

Breakthrough_Times_15_5 = [Breakthrough_Time_15_5_8, Breakthrough_Time_15_5_4, Breakthrough_Time_15_5_2, Breakthrough_Time_15_5_1]

Breakthrough_Times_15 = [Breakthrough_Time_15_8, Breakthrough_Time_15_4, Breakthrough_Time_15_2, Breakthrough_Time_15_1]

Coagulant = [8, 4, 2, 1]

fig, ax = plt.subplots()
ax.plot(Coagulant,Breakthrough_Times_20,'ro', label='Sand: 20cm fine')
ax.plot(Coagulant,Breakthrough_Times_15_5,'co', label='Sand: 15cm fine, 5cm coarse')
ax.plot(Coagulant,Breakthrough_Times_15,'ko', label='Sand: 15cm fine')
plt.xlabel('Coagulant (mg/L)')
plt.ylabel('Breakthrough Time (s)')
ax.legend()
plt.xlim(right=0,left=10);
plt.ylim(bottom=0,top=500);

plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Final Project/Images/Breakthrough vs Coagulant Dosage')
plt.show()
```
