Felix Yang Eirini Sarri

Lab Fire Group 5

Felix Yang: 5 hours

Eirini Sarri: 7 hours
# Introduction and Objectives
In the past, some regions of the United States had serious air and water quality issues, especially with acid rain caused by the combustion of fossil fuels that produce sulfuric and nitric acid in the atmosphere. The biggest consequence of acid rain on water quality is the acidification of lakes that do not have enough acid neutralizing capacity (ANC) in their soils to mitigate sudden additions of acidic solutions. Today, the problem with acid rain is concentrated in Asian cities such as Beijing and New Delhi due to their rapid industrial growth. The team decided to do this experiment with the goal of learning a practical method of remediating the effects of acid rain on lakes by adding substances in the water which increase the levels of ANC. The acid rain lab provides the first opportunity to code pH, ANC equations, and reactor equations (CMFR) as shown below. In the next lab (ANC lab), titration techniques and Gran plot analysis were used to back calculate the ANC levels of the lake at different time points, which were used to compare to measured and predicted ANC values found in the previous lab.

Acidity is principally measured using pH which measures the negative log of concentration of hydrogen ions as described in Equation 1. Healthy lakes are typically in the pH range of 6.5 to 8.5, controlling the pH via the carbonate system. This system has the following components: dissolved carbon dioxide, carbonic acid, bicarbonate, and carbonate. Equation 2 describes the molar concentration of the carbonate system but omits dissolved carbon dioxide because it exists at very low levels in aqueous systems.  

$pH=-log{[H^+]}$ (1)

$C_T=[H_2CO_3]+[HCO_3^-]+[CO_3^{-2}]$ (2)

The carbonate system can be modeled as a "volatile" or "non-volatile" system. This depends on whether or not aqueous carbon dioxide is at equilibrium with atmospheric carbon dioxide. The equations for ANC are given for the volatile and non-volatile systems in (3) and (4) respectively.


$ANC=\frac{P_{CO_{2} } K_{H} }{a_{0} } (\alpha_{1}+2\alpha_{2})+\frac{K_{w} }{\left[{H}^{+} \right]} \; -\left[{H}^{+} \right]$  (3)

Where $C_T = \frac{P_{CO_2} K_H}{\alpha_0}$

$ANC=C_T(\alpha_1+2\alpha_2)+\frac{K_w}{H+}-[H+]$                     (4)

Where $\alpha_1$ is equal to $\frac{1}{\frac{[H^+]}{K_1} + 1 + \frac{K_2}{[H^+]}}$ and $\alpha_2$ is equal to $\frac{1}{\frac{[H^+]^2 }{K_1 K_2} +\frac{[H^+]}{K_2} + 1}$ and $K_1$  and $K_2$ are the first and second dissociation constants for carbonic acid. $K_w$ is the described in equation (5).

${K_w} ={\left[H^+\right]} \left[{OH}^{{-}} \right]$ (5)

Determination of ANC or alkalinity in an unknown solution can be achieved using titration. For the titration experiment, one first has to find the equivalence point, or the point in the titration one adds exactly an equivalent or stoichiometric amount of titrant. This volume is known as the "equivalent" volume or $V_e$ as shown in the equation below.

$V_e=\frac{V_s*N_s}{N_t}$ (6)

The other way to determine ANC is to use a Gran plot technique, that is used after the equivalence point has been attained, where initial ANC is 0. This works because further titration past the equivalence point will result in an increase in the amount of [H+] equivalent to the amount of [H+] added. In other words, the number of moles of [H+] added equals the number of moles [H+] in solution as described in the mass balance equation below.

$\left[H^{+} \right]=\frac{N_{t} \left(V_{t} -V_{e} \right)}{\left(V_{s} +V_{t} \right)}$ (7)

The first Gram function is thus defined as equation 8 found below where $V_s$ and $V_t$ are volume of sample and volume of titrant, respectively. $F_1 = \frac{V_s +V_t }{V_s } {[H}^+ {]}$ (8)

The above eight are the principal equations that the team is going to use to determine ANC with increasing amounts of acid rain entering the system.


# Procedures

The goal of this experiment was to record the ANC change versus time by simulating the effects of acid rain on a lake. This was done by considering the lake as a Continuously Mixed Flow Reactor (CMFR), and measuring pH, which was then used to determine ANC using the equations described in the introduction. The methods for this experiment are divided into six parts: lake, addition of acid rain, pH measurement, titration, second experiment, and general measurements.

## Lake
To recreate the lake system (CMFR), a plastic tank of approximately 6 L capacity was filled with approximately 4L of deionized water. 623 mg of $NaHCO_3$ were added to bring the ANC of the lake to the value of 50 $\mu eq/L$ given in the lab manual. A magnetic stir bar was added to the lake and the tank was placed on a magnetic stirrer. Finally, 1 mL of bromocresol green indicator solution was added to the lake which changed the color of the lake from transparent to blue and then eventually to yellow as pH levels dropped. The metal weir of the tank was set in an angle just above the water level so that addition of acid rain would cause immediate overflow and thus satisfy the requirement for constant volume in a CMFR. The outflow of the lake was located in the bottom and connected via tubing to a drain on the workbench.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/lab_setup_labels.jpg" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Picture 1: Lab apparatus set-up</p>

## Addition of Acid Rain
The acid rain solution was provided in an F-style jug. #18 tubing was used to move the acid from the jug to the peristaltic pump, which was set to 70.3 RPM, and then to the lake. Once the peristaltic pump was turned on, the acid entered the lake with a rate of 267 mL/min.

## pH Measurement
A pH probe was first calibrated using the ProCoDA software and then inserted into the lake to measure pH. The settings were adjusted so that the probe would log pH measurements every second (again manipulated using ProCoDA). The probe was placed away from the effluent and close to the center of the lake to avoid the turbulence caused by the spinning stir bar. ProCoDA then creates a file that measures pH values across time.

## Titration
Samples were taken from the lake at time 0, 5, 10, 15, and 20 minutes. For this step, labeled plastic beakers were dipped into the lake and approximately 100 mL of sample were removed each time. Titration was performed for the 0, 5, and 10 minute samples because the 15 and 20 minute samples were already at pH lower that 4, meaning that the ANC could simply be calculated by the concentration of protons in the aqueous solution. 50mL of each sample were measured using a graduated cylinder and 0.05 N HCl was added in increments, with ProCoDA generating a Gran plot by measuring the change in pH with each successive HCl addition. By analyzing the data it was determined when the buffer capacity of the solution was depleted; finally the ANC was calculated.

## Second Experiment
For the second experiment, the substance contributing to the positive ANC of the lake was changed from $NaHCO_3$ to $CaCO_3$. 742 mg of $CaCO_3$ was added (again to get the target 50 μeq/L initial ANC.) Steps 1-3 were repeated, but samples were not obtained for this experiment (step 4.)

## General Measurements
The effluent rate was determined by measuring the volume of effluent that comes out in 15 seconds. The volume of water was calculated by measuring the mass of the tank with and without the lake water, thus calculating the mass of water, and dividing by the theoretical density of water at room temperature.

For detailed methods on procedures such as pH probe calibration, please refer to the Laboratory Manual.

# Results and Discussion
## Data Analysis

The analysis of the data required certain parameters which are summarized in Table 1 below.

Table 1: Relevant Experimental Parameters

| Experimental Parameter | Value | Units |
|:----------------------:|:-----:|:-----:|
|Mass of Tub and Water|4645|g|
|Mass of Tub|496|g|
|Density of Water|997|g/L|
|Volume of Lake|4.161|L|
|Flow Rate|0.005|L/s|
|Residence Time|832.3|s|
|$ANC_{in}$|-0.001|eq/L|
|$NaHCO_3$ Molecular Weight|84|g/mol|
|$NaHCO_3$ Mass|0.623|g|
|$ANC_0$ for $NaHCO_3$|0.00178|eq/L|
|ANC for $15$ minute sample|-0.000162|eq/L|
|ANC for $20$ minute sample|-0.000442|eq/L|
|$CaCO_3$ Molecular Weight|100|g/mol|
|$CaCO_3$ Mass|0.742|g|
|$ANC_0$ for $CaCO_3$|0.00178|eq/L|
|$K_1$|$10^{-6.3}$|-|
|$K_2$|$10^{-10.3}$|-|
|$K_H$|$10^{-1.5}$|mol/(L*atm)|
|$P_{CO_2}$|$10^{-3.5}$|atm|
|$K_w$|$10^{-14}$|-|

The set of graphs below for the closed and open systems of ANC (Figure 3,4 and 5) were smoothed out, but the graphs are still available in the code above the report. The function linspace creates new x dimensionless time intervals, typically between 30 and 50 points using the range of the original x values. Then it uses linear interpolation to create lines between the new points.

Figure 1 matches the theoretical expectations for the relationship between pH and hydraulic residence time, since the significant drop in pH (from approximately 5.5 to 4) occurs after a unit of the residence time of the system. This means that the lake had just enough acid neutralizing capacity for one residence time, after which the ANC of the lake started depleting and the ANC of the incoming acid lowered the pH of the system. Figure 2 also confirms the expected relationship between ANC and residence time. After one unit of hydraulic residence time, the ANC of the lake is almost zero, becoming negative as more acid rain enters the system. The closed system approximation (Figure 3) corresponds with the experimental results shown in Figure 2. This means that assuming that the amount of total carbon is equal to the carbon that we added to the system by the addition of $NaHCO_3$ is a good model for approximating the ANC level at various time points. Theoretically, this is due to the fact that the lake likely did not have time to equilibrate with the atmosphere, since the experiment was run the moment the carbon was added and reaching equilibrium with atmospheric $CO_2$ would take much longer than that given amount of time. The volatile system modeled in Figure 4 is evidently underestimating the lake ANC levels in the beginning of the experiment although it matches the experimental ANC values after approximately 1 residence time. This is because after 1 residence time, both the volatile and the non-volatile systems assume a complete depletion of total carbon in the system. Finally, Figure 5 shows the experimental ANC levels as well as the two models in the same graph, which emphasizes the strong relationship between the closed system to the experimental values and the large deviation of the volatile system from the actual ANC levels in the lake.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_1.png" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 1: pH vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_2.png" alt="Conservative ANC vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 2: Conservative ANC vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_3_smoothed.png" alt="ANC Closed System vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 3: ANC Closed System vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_4_smoothed.png" alt=" ANC Open System vs dimensionless hydraulic residence time"/>
</p>
<p align= "center"> Figure 4: ANC Open System vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/ANC_Compare_smooth.png" alt="ANC for open, closed, and predicted ANC"/>
</p>

<p align= "center"> Figure 5: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time. The red line demonstrates the experimental ANC values, the blue the closed system model and the yellow the open system model.


Moving on to $CaCO_3$, the outcome of the experiment was different than expected. Like in the previous set of graphs the graphs for the closed and open systems of ANC were smoothed out, but the original graphs are still available in the code above the report. As demonstrated in Figure 6, the pH drop occurred immediately after the addition the acid rain to the system. This means that the lake had minimal acid neutralizing capacity at the beginning of the experiment, even though the correct amount of $CaCO_3$ was intended to maintain at least $50μeq/L$ ANC after 1 residence time. This result is also apparent in Figure 8 which models the closed system based on pH values, where the ANC levels drop as soon as the experiment starts. Upon observation of the model lake, it was determined that $CaCO_3$ did not dissolve as soon as it was added to water and stirred, but instead was deposited as a solid at the bottom and edges of the tank. This resulted in the wrong initial ANC concentration which is why the system had limited buffering capacity and its pH dropped as soon as the acid entered the tank. Therefore, since the experimental values of pH were not indicative of a real-world system, neither the closed system (Figure 8) nor the open system (Figure 9) matches the observed ANC levels (Figure 7). This can also be seen in Figure 10.


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5a.png" alt=">pH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 6: pH vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5b.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 7: Conservative ANC vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5c_smoothed.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 8: ANC Closed System vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5d_smoothed.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 9: ANC Open System vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/ANC_calcium_carb_Compare_smooth.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 10: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time

Labfire learned that the $CaCO_3$ does not dissolve as readily as sodium bicarbonate so by the time the team started adding added the lake did not have a sufficient level of ANC. Therefore the buffer capacity using compared  $CaCO_3$  to the buffer capacity sodium bicarbonate was reduced, causing a reduction of pH when even small amounts of acid were added. Therefore, the team cannot be certain which model fits the measured ANC values better. As a next step, one could repeat the experiment but make sure that the $CaCO_3$ is not present as a solid at the edges of the tank.

From the titration experiments, the team was able to determine the ANC of the lake at different time points, using the samples that were collected at time = 0, 5, 10, 15, and 20 minutes. Since the pH of the solution at time = 15 and time = 20 minutes was already less than 4 (pH at 15 = 3.79 and pH at 20 = 3.355), an approximation was used which states that $ANC = - [H+]$, which is derived from Equation 33 in the Acid Neutralizing chapter of the textbook. The pH change over the volume of titrant added to solution was graphed in Figure 11. This graph shows that there are two areas where the solution has a strong enough buffer capacity: a region around a pH of 6.3 and a region around a pH of 3. The first region corresponds to the acid neutralizing capacity of the $HCO_{3}$ which uses up $H+$ by converting into $H_{2}CO_{3}$. The second yellow region of small pH change is due to the pH of the lake approaching the pH of the input. The governing equation for this is $ANC = - [H+]$ as stated above. From the Gran plot shown in Figure 12, the equivalent volume of titrant needed to overcome the ANC of the solution was calculated and then compared to the calculation made by ProCoDA. The answers were very similar, as ProCoDA calculated the equivalent volume to be 1.735 $\frac{meq}{L}$ whereas the calculation using linear extrapolation produced an equivalent volume of 1.766 $\frac{meq}{L}$. Finally, using the same method to determine the ANC of the lake at all the other time points, it was determined that the Gran plot method data corresponded with the conservative ANC data, as shown in the red line on Figure 13.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/images/Question_1.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 11: pH vs titrant volume

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/images/Question_2_Figure12.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 12: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/images/Question_3.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 13: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time


# Questions
1. What do you think would happen if enough $NaHCO_3$ were added to the lake to maintain an ANC greater than 50μeq/L for 3 residence times with the stirrer turned off? How much $NaHCO_3$ would need to be added?

Based on our prelab, we calculated that we would need 6.73 g of  $NaHCO_3$ to be added to the lake to maintain ANC greater than $50μeq/L$ for 3 residence times. If the stirrer was turned off, then we would have to wait for diffusion to occur so that the $NaHCO_3$ is fully mixed which could take a very long time. Therefore, instead of a solution with a high $NaHCO_3$ concentration, we would have a solution with a large mass of $NaHCO_3$ that is not fully aqueous and settles as a solid on the bottom of the tank. This means that even though we would have added the correct amount of $NaHCO_3$ to keep the ANC levels at 50μeq/L for 3 residence times, in reality the ANC levels would drop because the system wouldn't have the required amount of dissolved carbon.   


2. What are some of the complicating factors you might find in attempting to remediate a lake using $CaCO_3$? Below is a list of issues to consider.
extent of mixing
solubility of $CaCO_3$ (find the solubility and compare with NaHCO3)
density of $CaCO_3$ slurry (find the density of CaCO3)

Some problems that may arise when using $CaCO_3$ might be due to limited time as the experiment has shown. If one needs to immediately raise ANC in a body of water, the solubility of $CaC0_3$ may be antithetical to such efforts as shown in Figure 6 where the pH immediately dropped below 4 even .2 units of dimensionless hydraulic residence time in, and did not resemble Figure 1 where the pH slowly approached 3. Solubility of $CaC0_3$ is 15 mg/L while solubility of $NaHCO_3$ is 9600mg/L, which is more than a 100 fold times larger.


# Conclusions

In this experiment the team discovered that not all chemicals are equal in their effectiveness in remediating acid rain in water bodies. Although theoretically the effectiveness of $CaCO_3$ and $NaHCO_3$ should have been the same after one residence time, due to their difference in solubility the ANC level in the $CaCO_3$ case was not sufficient to mitigate the acidity of the solution coming into the lake. Practically speaking, if there were a case when a lake had to be immediately protected from incoming acid rain, it would be wise to use $NaHCO_3$ as opposed to $CaCO_3$, since it would dissolve more readily. In addition, based on the experiment with $NaHCO_3$ as the carbon source, it was determined that the model that better estimates the ANC levels at any point in the lake would be the closed system model.

# Suggestions
The team would suggest not to use $CaCO_{3}$ as an alternative source of ANC in the lake because of the large difference in solubility between this compound and $NaHCO_{3}$. For $CaCO_{3}$ to behave as a good source of ANC, the system needs to be better stirred so that $CaCO_{3}$ dissolves completely. In addition, a second suggestion would be to include a few more points during the titration experiment after the equivalent volume is added, so as to obtain a more accurate equation for the linear relationship between $F1$ and volume of titrant added.


# Python Code Appendix

```python
  from aguaclara.core.units  import unit_registry as u
  u.define('equivalent = mole = eq')
  import aguaclara.research.environmental_processes_analysis as epa
  import aguaclara.core.utility as ut
  from scipy import optimize
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats
  from scipy.interpolate import make_interp_spline, BSpline
  from math import*

#Acid Rain Lab
#Variable Names
mass_combined = 4645*u.g  
mass_tub = 496*u.g
density = 997*u.g/u.L
volume = (mass_combined-mass_tub)/density
flow_rate = (75*10**-3*u.L)/(15*u.s)
residence_time = (volume/flow_rate).magnitude
ANC_in = -0.001*u.equivalent/u.L
MW_sodium_bicarb = 84*u.g/u.mole
mass_sodium_bicarb = 0.623*u.g
ANC_0_sodium_bicarb = mass_sodium_bicarb/(MW_sodium_bicarb*volume)
MW_calcium_carb = 100*u.g/u.mole
mass_calcium_carb = 0.742*u.g
ANC_0_calcium_carb = mass_calcium_carb/(MW_calcium_carb*volume)
ANC_sample_15 = -10**(-3.79)*u.equivalent/u.L
ANC_sample_20 = -10**(-3.355)*u.equivalent/u.L

#Sodium Bicarbonate

#File path for the excel file containing the experimental measurements
data_file_path = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/Acid_Rain_Sodium_Bicarbonate_v3.txt"


#Pandas dataframe with the data in the file
df_sodium_bicarb = pd.read_csv(data_file_path,delimiter='\t')

#Column headers
list(df_sodium_bicarb)


#Comments in the data file.
lakepHnotes = epa.notes(data_file_path)
lakepHnotes

# set the start index of the data file to one past the note indicating the start.
start=8

#The pH data is in column 1
column=1

#Question 1

lakepH_1=epa.column_of_data(data_file_path,start,column)

#extract the corresponding time data and convert to seconds
time_1 = epa.column_of_time(data_file_path,start).to(u.s).magnitude
dimensionless_residence_time_1 = time_1 / residence_time

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(dimensionless_residence_time_1,lakepH_1,'r')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('pH')

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_1')
plt.show()

#Question 2

ANC_out_sodium_bicarb = epa.CMFR(dimensionless_residence_time_1,ANC_0_sodium_bicarb,ANC_in)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('Conservative ANC (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb,'r')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_2')
plt.show()

#Question 3

alpha_1_sodium_bicarb = epa.alpha1_carbonate(lakepH_1)
alpha_2_sodium_bicarb = epa.alpha2_carbonate(lakepH_1)
C_t_closed_sodium_bicarb = ANC_0_sodium_bicarb * e**(-dimensionless_residence_time_1)
ANC_out_sodium_bicarb_closed=epa.ANC_closed(lakepH_1,C_t_closed_sodium_bicarb)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_closed,'c')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_3')
plt.show()

#Smooth the model by using spline function
xnew_figure3 = np.linspace(dimensionless_residence_time_1.min(),dimensionless_residence_time_1.max(),28) #28 is number of points between first and dim-less hydraulic residence time
spl = make_interp_spline(dimensionless_residence_time_1, ANC_out_sodium_bicarb_closed, k=3)
ANC_out_sodium_bicarb_closed_smooth = spl(xnew_figure3)
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(xnew_figure3,ANC_out_sodium_bicarb_closed_smooth,'c')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_3_smoothed')
plt.show()


#Question 4
ANC_out_sodium_bicarb_open=epa.ANC_open(lakepH_1)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_open,'y')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_4')
plt.show()

#Smooth the model by using spline function
xnew_figure4 = np.linspace(dimensionless_residence_time_1.min(),dimensionless_residence_time_1.max(),40) #40 is number of points between first and dim-less hydraulic residence time

spl = make_interp_spline(dimensionless_residence_time_1, ANC_out_sodium_bicarb_open, k=3)
ANC_out_sodium_bicarb_open_smooth = spl(xnew_figure4)
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')
plt.plot(xnew_figure4,ANC_out_sodium_bicarb_open_smooth,'y')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_4_smoothed')
plt.show()

#Now plot the graph with all three on same graph
plt.plot(xnew_figure3,ANC_out_sodium_bicarb_closed_smooth,'c')
plt.plot(xnew_figure4,ANC_out_sodium_bicarb_open_smooth,'y')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb,'r')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC (eq/L)')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/ANC_Compare_smooth')
plt.show()

#Calcium Carbonate

#File paths for the excel file containing the experimental measurements
data_file_path_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/Acid%20Rain%20Calcium%20Carbonate_v2.txt"

#Pandas dataframe with the data in the file
df_calcium_carb= pd.read_csv(data_file_path_2,delimiter='\t')

#Column headers
list(df_calcium_carb)

#Question 5a

#Comments in the data file.
lakepHnotes = epa.notes(data_file_path_2)
lakepHnotes

# set the start index of the data file to one past the note indicating the start.
start=8

#The pH data is in column 1
column=1

lakepH_2=epa.column_of_data(data_file_path_2,start,column)

#extract the corresponding time data and convert to seconds
time_2 = epa.column_of_time(data_file_path_2,start).to(u.s).magnitude
dimensionless_residence_time_2 = time_2 / residence_time

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('pH')
plt.plot(dimensionless_residence_time_2,lakepH_2,'r')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5a')
plt.show()

#Question 5b
ANC_out_calcium_carb = epa.CMFR(dimensionless_residence_time_2,ANC_0_calcium_carb,ANC_in)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('Conservative ANC (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb,'r')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5b')
plt.show()

#Question 5c
alpha_1_calcium_carb = epa.alpha1_carbonate(lakepH_2)
alpha_2_calcium_carb = epa.alpha2_carbonate(lakepH_2)
C_t_closed_calcium_carb = ANC_0_calcium_carb * e**(-dimensionless_residence_time_2)
ANC_out_calcium_carb_closed = epa.ANC_closed(lakepH_2,C_t_closed_calcium_carb)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_closed,'c')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5c')
plt.show()

#Smooth the model by using spline function
xnew_figure8 = np.linspace(dimensionless_residence_time_2.min(),dimensionless_residence_time_2.max(),50) #50 is number of points between first and dim-less hydraulic residence time
spl = make_interp_spline(dimensionless_residence_time_2, ANC_out_calcium_carb_closed, k=3)
ANC_out_calcium_carb_closed_smooth = spl(xnew_figure8)
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(xnew_figure8,ANC_out_calcium_carb_closed_smooth,'c')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5c_smoothed')
plt.show()

#Question 5d
ANC_out_calcium_carb_open = epa.ANC_open(lakepH_2)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_open,'y')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5d')
plt.show()

#Smooth the model by using spline function
xnew_figure9=np.linspace(dimensionless_residence_time_2.min(),dimensionless_residence_time_2.max(),50) #50 is number of points between first and dim-less hydraulic residence time

spl = make_interp_spline(dimensionless_residence_time_2, ANC_out_calcium_carb_open, k=3)
ANC_out_calcium_carb_open_smooth = spl(xnew_figure9)
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')

plt.plot(xnew_figure8,ANC_out_calcium_carb_open_smooth,'y')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5d_smoothed')
plt.show()

#Now plot the graph
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb,'r')
plt.plot(xnew_figure8,ANC_out_calcium_carb_closed_smooth,'c')
plt.plot(xnew_figure9,ANC_out_calcium_carb_open_smooth,'y')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC (eq/L)')
#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/ANC_calcium_carb_Compare_smooth')
plt.show()


#ANC Lab

#File paths for the excel file containing the experimental measurements
data_file_path_3 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/0_minute_sample.xls"

# The epa.Gran function imports data from your Gran data file as saved by ProCoDA.
# The epa.Gran function assigns all of the outputs in one statement

V_titrant_0, pH_0, V_Sample_0, Normality_Titrant_0, V_equivalent_0, ANC_0 = epa.Gran(data_file_path_3)



#Question 1

#pH Ranges
Range_1=V_titrant_0[0:7]
pH_range_1=pH_0[0:7]
Range_2=V_titrant_0[6:9]
pH_range_2=pH_0[6:9]
Range_3=V_titrant_0[8:]
pH_range_3=pH_0[8:]

#Now plot the graph
fig, ax = plt.subplots()
plt.annotate('Equivalent Volume: 1.73mL',xy=(1.73,2.8),xytext=(0.3,4),           arrowprops=dict(facecolor='black', shrink=0.001))
ax.plot(Range_1,pH_range_1,'c', label='HCO3- + H+ --> H2CO3')
ax.plot(Range_2,pH_range_2,'r')
ax.plot(Range_3,pH_range_3,'y', label='Approaching pH of acid rain input')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('pH')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 3 - ANC/images/Question_1')
plt.show()


#Question 2

#Define the gran function.
def F1(V_sample,V_titrant,pH):
  return (V_sample + V_titrant)/V_sample * epa.invpH(pH)

#Create an array of the F1 values.
F1_data_0 = F1(V_Sample_0,V_titrant_0,pH_0)

#By inspection I guess that there are 5 good data points in the linear region.
N_good_points_0 = 4

#use scipy linear regression. Note that the we can extract the last n points from an array using the notation [-N:]
slope_0, intercept_0, r_value_0, p_value_0, std_err_0 = stats.linregress(V_titrant_0[-N_good_points_0:],F1_data_0[-N_good_points_0:])


#reattach the correct units to the slope and intercept.
intercept_0 = intercept_0*u.mole/u.L
slope_0 = slope_0*(u.mole/u.L)/u.mL
V_eq_0 = -intercept_0/slope_0
ANC_sample_0 = V_eq_0*Normality_Titrant_0/V_Sample_0

print('The r value for this curve fit is', ut.round_sf(r_value_0,5))
print('The equivalent volume was', ut.round_sf(V_eq_0,2))
print('The acid neutralizing capacity was',ut.round_sf(ANC_sample_0.to(u.meq/u.L),2))

#The equivalent volume agrees well with the value calculated by ProCoDA.
#create an array of points to draw the linear regression line
x=[V_eq_0.magnitude,V_titrant_0[-1].magnitude ]
y=[0,(V_titrant_0[-1]*slope_0+intercept_0).magnitude]

#Now plot the data and the linear regression
plt.plot(V_titrant_0, F1_data_0,'o')
plt.plot(x, y,'r')
plt.xlabel('Titrant Volume (mL)')
plt.ylabel('Gran function (mole/L)')
plt.legend(['data'])

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 3 - ANC/images/Question_2_Figure12')
plt.show()

V_equivalent_0 #ProCoDA Calculation
V_eq_0 #Python Calculation

#Question 3

#File Paths
data_file_path_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/5_minute_sample.xls"

data_file_path_5 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%203%20-%20ANC/10_minute_sample.xls"

#Gran Functions
V_titrant_5, pH_5, V_Sample_5, Normality_Titrant_5, V_equivalent_5, ANC_5 = epa.Gran(data_file_path_4)

V_titrant_10, pH_10, V_Sample_10, Normality_Titrant_10, V_equivalent_10, ANC_10 = epa.Gran(data_file_path_5)

#Create an array of the F1 values.
F1_data_5 = F1(V_Sample_5,V_titrant_5,pH_5)

F1_data_10 = F1(V_Sample_10,V_titrant_10,pH_10)

#By inspection I guess that there are 4 good data points in the linear region.
N_good_points_5 = 3

N_good_points_10 = 3

#use scipy linear regression. Note that the we can extract the last n points from an array using the notation [-N:]
slope_5, intercept_5, r_value_5, p_value_5, std_err_5 = stats.linregress(V_titrant_5[-N_good_points_5:],F1_data_5[-N_good_points_5:])

slope_10, intercept_10, r_value_10, p_value_10, std_err_10 = stats.linregress(V_titrant_10[-N_good_points_10:],F1_data_10[-N_good_points_10:])

#reattach the correct units to the slope and intercept.
intercept_5 = intercept_5*u.mole/u.L
slope_5 = slope_5*(u.mole/u.L)/u.mL
V_eq_5 = -intercept_5/slope_5
ANC_sample_5 = V_eq_5*Normality_Titrant_5/V_Sample_5


intercept_10 = intercept_10*u.mole/u.L
slope_10 = slope_10*(u.mole/u.L)/u.mL
V_eq_10 = -intercept_10/slope_10
ANC_sample_10 = V_eq_10*Normality_Titrant_10/V_Sample_10

#Graph with all ANCs
plt.plot(xnew_figure3,ANC_out_sodium_bicarb_closed_smooth,'c')
plt.plot(xnew_figure4,ANC_out_sodium_bicarb_open_smooth,'y')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb,'r')
plt.plot(0,ANC_sample_0,'ko')
plt.plot(5*60/residence_time,ANC_sample_5,'ko')
plt.plot(10*60/residence_time,ANC_sample_10,'ko')
plt.plot(15*60/residence_time,ANC_sample_15,'ko')
plt.plot(20*60/residence_time,ANC_sample_20,'ko')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC (eq/L)')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 3 - ANC/images/ANC_Compare_smooth_Question 3')
plt.show()

 ```
