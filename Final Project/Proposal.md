#Group 5 - Lab Fire Final Project Proposal

##Intro/context – What is the problem? Why is it important?
Current AguaClara technology utilizes enclosed stacked rapid sand filters (ESTaRS) which itself an innovation upon traditional rapid sand filters that saves floor space. It does so by placing several beds of sand on top of one another between inlet and outlet pipes. However, it is possible that even more space could be conserved by reducing the height of each bed of sand. It is important because a part of AguaClara's mission is to create the most affordable technology possible without compromising on the quality of the water that is produced. This research project seeks to discover if sand bed depths as low as 2 cm or lower are feasible options. Conclusions from these experiments would also have implications for the size of the mass transfer zone in the sand filtration process.

##Objectives – What is the hypothesis? What will you do to test the hypothesis?
ESTaRS currently uses 20 cm of sand for each bed, which is lower than the current industry standard of 50 cm to 75 cm. That reduced depth was arbitrarily chosen. Since there was no significant adverse effect of the function of the sand filters, it is likely that it could be reduced even further.

The hypothesis for this experiment is that lowering the sand filter depth will decrease the failure time of the system, until the depth matches that of the mass transfer zone, when the failure time will equal three minutes.

Group 5 (Lab Fire) will test this hypothesis by running experiments, varying the depth of the sand filter bed and coagulant dose, and controlling for flow rate, and influent turbidity. Failure time is determined as the time at which the filter no longer produces water that is below 1 NTU.

##Experimental plan including – How will you measure it?
To measure time to failure, the team will be continuously measuring turbidity at the effluent. Failure is defined as when 1 NTU effluent is reached. To compare the efficiency of each bed using different influent coagulant concentrations, the team members will compare the time it takes for each system to fail.

##Key design parameters
1. Filter Heights: start from 20 cm and keep decreasing until we reach the mass transfer zone
2. Coagulant Concentrations: $2 \frac{mg}{L}$, $1 \frac{mg}{L}$, $0 \frac{mg}{L}$
3. Influent flow Rate: 50 RPM
4. Clay Concentration: 5 NTU
5. Humic Acid Concentration:


##Timeline of tasks/experiments

Table 1: Experiment Schedule

| Date | Procedure |
|:--------:|:-----:|
| Friday, April 12 | Coagulant concentration: $2 \frac{mg}{L}$, Filter Height: 20 cm |
| Monday, April 15 |Coagulant concentration: $2 \frac{mg}{L}$, Filter Height: 2 cm |
| Wednesday, April 17 | Coagulant concentration: $2 \frac{mg}{L}$, Filter Height: depending on previous experiments |
| Friday, April 19 | Coagulant concentration: $1 \frac{mg}{L}$, Filter Height: 20 cm |
| Monday, April 22 | Coagulant concentration: $1 \frac{mg}{L}$, Filter Height: 2 cm |
| Wednesday, April 24 | Coagulant concentration: $1 \frac{mg}{L}$, Filter Height: depending on previous experiments |
| Friday, April 26 | Coagulant concentration: $0 \frac{mg}{L}$, Filter Height: 20 cm |
| Monday, April 29 | Coagulant concentration: $0 \frac{mg}{L}$, Filter Height: 2 cm |
| Wednesday, May 1 | Coagulant concentration: $0 \frac{mg}{L}$, Filter Height: depending on previous experiments |
| Friday, May 3 | Final experiments, repeats, etc |
| Monday, May 6 | Prepare report, ask questions |


##Possible hurdles/challenges
Automating the experiment using ProCoda is preferable so that the members of Group 5 do not have to be present at all times. However this may prove to be a challenge because neither members are familiar enough with the program to program such code that would automate. Another challenge is estimating failure time for each system so that the volume of influent needed can be determined. To solve this issue, the team will run an initial experiment where both members will be present for the whole duration, to get a better idea of the length of the experiment.


##Resources needed to conduct experiments – What tools will you use?
Tubing: #18 tubing for water influent, #14 tubing for stock solution influent
Filter Column: 1 inch Diameter Schedule 80 Clear PVC Pipe 12"
Pump: 1
Valves: 4   
Sand: To be determined as experiments are conducted
Turbidimeters: 2
Clay: To be determined as experiments are conducted

##Expectations/Anticipated results
The expected results are that the sand filters, despite having reduced sand bed depths, function reasonably well by not reaching failure mode within a certain period of time. The team is expecting that the mass transfer zone length for each coagulant concentration can be estimated with this method.

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


```
