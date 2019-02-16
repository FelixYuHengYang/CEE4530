

```python
from aguaclara.core.units  import unit_registry as u
u.define('equivalent = mole = eq')
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize
from aide_design.play import*
from aide_design.physchem import*
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
from math import*

#Variable Names
mass_combined = 4645*u.g
mass_tub = 496*u.g
density = 997*u.g/u.L
volume = (mass_combined-mass_tub)/density
flow_rate = (75*10**-3*u.L)/(15*u.s)
residence_time = (volume/flow_rate).magnitude
residence_time
ANC_in = -0.001*u.equivalent/u.L
MW_sodium_bicarb = 84*u.g/u.mole
mass_sodium_bicarb = 0.623*u.g
ANC_0_sodium_bicarb = mass_sodium_bicarb/(MW_sodium_bicarb*volume)
MW_calcium_carb = 100*u.g/u.mole
mass_calcium_carb = 0.742*u.g
ANC_0_calcium_carb = mass_calcium_carb/(MW_calcium_carb*volume)
K_1 = 10**(-6.3)
K_2 = 10**(-10.3)
K_H = 10**(-1.5)*u.mol/(u.L*u.atm)
P_CO2 = 10**(-3.5)*u.atm
K_w = 10**(-14)


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

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_1')
plt.show()


#Question 2
ANC_out_sodium_bicarb = ANC_in*(1-e**(-dimensionless_residence_time_1))+ANC_0_sodium_bicarb*e**(-dimensionless_residence_time_1)


#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('Conservative ANC (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb,'r')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_2')
plt.show()

#Question 3

alpha_1_sodium_bicarb = 1/((10**(-lakepH_1)/K_1)+1+(K_2/10**(-lakepH_1)))
alpha_2_sodium_bicarb = 1/((10**(-2*lakepH_1)/(K_1*K_2))+(10**(-lakepH_1)/K_2)+1)
C_t_closed_sodium_bicarb = ANC_0_sodium_bicarb * e**(-dimensionless_residence_time_1)

ANC_out_sodium_bicarb_closed = C_t_closed_sodium_bicarb * (alpha_1_sodium_bicarb + 2*alpha_2_sodium_bicarb) + K_w/(10**(-lakepH_1))*u.mole/u.L - 10**(-lakepH_1)*u.mole/u.L

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_closed,'c')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_3')
plt.show()



#Question 4

alpha_0_sodium_bicarb = 1/(1+(K_1/10**(-lakepH_1))+((K_1*K_2)/10**(-2*lakepH_1)))
C_t_open_sodium_bicarb = (P_CO2*K_H)/alpha_0_sodium_bicarb
ANC_out_sodium_bicarb_open = C_t_open_sodium_bicarb * (alpha_1_sodium_bicarb + 2*alpha_2_sodium_bicarb) + K_w/(10**(-lakepH_1))*u.mole/u.L - 10**(-lakepH_1)*u.mole/u.L

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_open,'y')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_4')
plt.show()

#Now plot the graph
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_open,'y')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb_closed,'c')
plt.plot(dimensionless_residence_time_1,ANC_out_sodium_bicarb,'r')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC (eq/L)')

plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/ANC_Compare')
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
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5a')
plt.show()


#Question 5b

ANC_out_calcium_carb = ANC_in*(1-e**(-dimensionless_residence_time_2))+ANC_0_calcium_carb*e**(-dimensionless_residence_time_2)

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('Conservative ANC (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb,'r')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5b')
plt.show()


#Question 5c

alpha_1_calcium_carb = 1/((10**(-lakepH_2)/K_1)+1+(K_2/10**(-lakepH_2)))
alpha_2_calcium_carb = 1/((10**(-2*lakepH_2)/(K_1*K_2))+(10**(-lakepH_2)/K_2)+1)
C_t_closed_calcium_carb = ANC_0_calcium_carb * e**(-dimensionless_residence_time_2)

ANC_out_calcium_carb_closed = C_t_closed_calcium_carb * (alpha_1_calcium_carb + 2*alpha_2_calcium_carb) + K_w/(10**(-lakepH_2))*u.mole/u.L - 10**(-lakepH_2)*u.mole/u.L

#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Closed System (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_closed,'c')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5c')
plt.show()


#Question 5d

alpha_0_calcium_carb = 1/(1+(K_1/10**(-lakepH_2))+((K_1*K_2)/10**(-2*lakepH_2)))
C_t_open_calcium_carb = (P_CO2*K_H)/alpha_0_calcium_carb
ANC_out_calcium_carb_open = C_t_open_calcium_carb * (alpha_1_calcium_carb + 2*alpha_2_calcium_carb) + K_w/(10**(-lakepH_2))*u.mole/u.L - 10**(-lakepH_2)*u.mole/u.L


#Now plot the graph
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC Open System (eq/L)')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_open,'y')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/Question_5d')
plt.show()

#Now plot the graph
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb,'r')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_closed,'c')
plt.plot(dimensionless_residence_time_2,ANC_out_calcium_carb_open,'y')
plt.xlabel('Dimensionless Hydraulic Residence Time')
plt.ylabel('ANC (eq/L)')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 2 - Acid Rain/images/ANC_calcium_carb_Compare')
plt.show()



```

#Introduction and Objectives
In the past, the United States had serious air quality issues, especially with acid rain caused by the combustion of fossil fuels that produce sulfuric and nitric acid in the atmosphere. The biggest consequence of acid rain is the acidification of lakes that do not have acid neutralizing capacity (ANC) in their soils to mitigate this sudden addition of acidic solutions. Today, there is a huge problem with acid rain in Asian cities such as Beijing and New Delhi due to their rapid industrial growth. The team decided to do this experiment with the goal of learning a practical method of remediating the effects of acid rain on lakes by adding substances in the water which increase the levels of ANC. This also provides the first opportunity to code pH, ANC equations, and reactor equations (CMFR) as shown below.  

Acidity is principally measured using pH which measures the negative log of concentration of hydrogen ions as described in Equation 1. Healthy lakes are typically in the pH range of 6.5 to 8.5, controlling the pH via the carbonate system. This system has the following components: dissolved carbon dioxide, carbonic acid, bicarbonate, and carbonate. Equation 2 describes the molar concentration of the carbonate system but omits dissolved carbon dioxide because it exists at very low levels in aqueous systems.  

$pH=-log{[H^+]}$ (1)

$C_T=[H_2CO_3]+[HCO_3^-]+[CO_3^{-2}]$ (2)

The carbonate system can be modeled as a "volatile" or "non-volatile" system. This depends on whether or not aqueous carbon dioxide is at equilibrium with atmospheric carbon dioxide. The equations for ANC are given for the volatile and non-volatile systems in (3) and (4) respectively.


$ANC=\frac{P_{CO_{2} } K_{H} }{a_{0} } (\alpha _{1}+2\alpha _{2})+\frac{K_{w} }{\left[{H}^{+} \right]} \; -\left[{H}^{+} \right]$  (3)

Where $C_T = \frac{P_{CO_2} K_H}{\alpha_0}$

$ANC=C_T(\alpha_1+2\alpha_2)+\frac{K_w}{H+}-[H+]$                     (4)

Where $\alpha_1$ is equal to $\frac{1}{\frac{[H^+]}{K_1} + 1 + \frac{K_2}{[H^+]}}$ and $\alpha_2$ is equal to $\frac{1}{\frac{[H^+]^2 }{K_1 K_2} +\frac{[H^+]}{K_2} + 1}$ and $K_1$  and $K_2$ are the first and second dissociation constants for carbonic acid. $K_w$ is the described in equation (5).

${K_w} ={\left[H^+\right]} \left[{OH}^{{-}} \right]$ (5)

The above five are the principal equations that the team is going to use to determine ANC with increasing amounts of acid rain entering the system.


#Procedures

The goal of this experiment was to determine the ANC change versus time while adding increasing amounts of acid rain in a lake which acted as a Continuously Mixed Flow Reactor (CMFR). The methods for this experiment could be divided into six parts: lake, addition of acid rain, pH measurement, sample taking, second experiment, and general measurements.

##Lake
To recreate the lake system (CMFR), a plastic tank of approximately 6 L capacity was filled with deionized water up to 4 L. 623 mg of $NaHCO_3$ were added to bring the ANC of the lake to the value of 50 $\mu eq/L$ given in the lab manual. A magnetic stir bar was added to the lake and the tank was placed on a magnetic stirrer. Finally, 1 mL of bromocresol green indicator solution was added to the lake which theoretically should turn the color of the lake from transparent to blue and then eventually to yellow. The metal weir of the tank was set in an angle just above the water level so that the addition of acid rain would cause immediate overflow and thus satisfy the requirement for constant volume in a CMFR. The outflow of the lake was located in the bottom and connected via tubing to a drain on the workbench.

##Addition of Acid Rain
The acid rain solution was provided in an F-style jug. #18 tubing was used to move the acid from the jug to the peristaltic pump, which was set to 70.3 RPM, and then to the lake. Once the peristaltic pump was turned on, the acid entered the lake with a rate of 267 mL/min.

##pH Measurement
A pH probe was first calibrated using the ProCoda software and then inserted into the lake to measure pH. The settings were adjusted so that the probe would log pH measurements every second (again manipulated using ProCoda.) The probe was placed away from the effluent and close to the center of the lake, keeping in mind to avoid the turbulence caused by the spinning stir bar. ProCoda thus creates a file with time points and respective pH values.

##Sample Taking
Samples from the lake were taken at time 0, 5, 10, 15, and 20 minutes. For this step, labeled plastic beakers were dipped into the lake and approximately 100 mL of sample were removed each time.

##Second Experiment
For the second experiment, the substance contributing to the positive ANC of the lake was switched from $NaHCO_3$ to $CaCO_3$. The amount of $CaCO_3$ added was 742 mg (again to get the target 50 μeq/L initial ANC.) Steps 1-3 were repeated, but samples were not obtained for this experiment (step 4.)

##General Measurements
The effluent rate was measured by measuring the volume of effluent per 15 seconds. The volume of water was calculated by measuring the mass of the tank with and without the lake water, thus calculating the mass of water, and dividing by the theoretical density of water.

For detailed methods on procedures such as pH probe calibration, please refer to the Laboratory Manual.

#Results and Discussion
##Data Analysis

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
|$CaCO_3$ Molecular Weight|100|g/mol|
|$CaCO_3$ Mass|0.742|g|
|$ANC_0$ for $CaCO_3$|0.00178|g/mol|
|$K_1$|$10^{-6.3}$|-|
|$K_2$|$10^{-10.3}$|-|
|$K_H$|$10^{-1.5}$|mol/(L*atm)|
|$P_{CO_2}$|$10^{-3.5}$|atm|
|$K_w$|$10^{-14}$|-|


Figure 1 matches the theoretical expectations for the relationship between pH and hydraulic residence time, since the significant drop in pH (from approximately 5.5 to 4) occurs around the residence time of the system. This means that the lake had enough acid neutralizing capacity for one residence time, after which the ANC of the lake started depleting and the ANC of the incoming acid shifted the pH of the system down. Figure 2 also agrees with the expected relationship between ANC and residence time. At a ratio of time over residence time of 1, the ANC of the lake is almost zero, after which point it becomes negative as the acid rain keeps entering the system. The closed system approximation (Figure 3) matches the experimental results shown in Figure 2. This means that assuming that the amount of total carbon is equal to the carbon that we added to the system by the addition of $NaHCO_3$ is a good model for approximating the ANC level at various time points. Theoretically, this is explained by the fact that the lake did not have time to equilibrate with the atmosphere, since the experiment was run the moment the carbon was added and reaching equilibrium with atmospheric $CO_2$ would take very long. The volatile system modeled in Figure 4 is evidently underestimating the lake ANC levels in the beginning of the experiment although it matches the experimental ANC values after approximately 1 residence time. This is because after 1 residence time, both the volatile and the non-volatile systems assume a complete depletion of total carbon in the system. Finally, Figure 5 shows the experimental ANC levels as well as the two models in the same graph, which emphasizes the strong agreement of the closed system to the experimental values and the large deviation of the volatile system from the actual ANC levels in the lake.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_1.png" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 1: pH vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_2.png" alt="Conservative ANC vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 2: Conservative ANC vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_3.png" alt="ANC Closed System vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 3: ANC Closed System vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_4.png" alt=" ANC Open Systemvs dimensionless hydraulic residence time"/>
</p>
<p align= "center"> Figure 4: ANC Open System vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/ANC_Compare.png" alt="ANC for open, closed, and predicted ANC"/>
</p>

<p align= "center"> Figure 5: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time. The red line demonstrates the experimental ANC values, the blue the closed system model and the yellow the open system model.


Moving on to $CaCO_3$, the outcome of the experiment was different that expected. As demonstrated in Figure 6, the pH drop occurred immediately after the addition the acid rain to the system. This means that the lake had minimal acid neutralizing capacity at the beginning of the experiment, even though the correct amount of $CaCO_3$ was added for the lake to have $50μeq/L$ ANC after 1 residence time. This result is also apparent in Figure 8 which is modeling the closed system based on pH values, where the ANC levels drop as soon as the experiment starts. After observing the tank, it was determined that $CaCO_3$ did not dissolve as soon as it was added to water and stirred, but instead was deposited as a solid at the bottom and edges of the tank. This result in the wrong initial ANC concentration which is why the system had limited buffering capacity and its pH dropped as soon as the acid entered the tank. Therefore, since the experimental values of pH were not indicative of a real-world system, neither the closed system (Figure 8) nor the open system (Figure 9) matches the observed ANC levels (Figure 7). This can also be seen in Figure 10.


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5a.png" alt=">pH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align= "center"> Figure 6: pH vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5b.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 7: Conservative ANC vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5c.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 8: ANC Closed System vs Dimensionless Hydraulic Residence Time

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/Question_5d.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 9: ANC Open System vs Dimensionless Hydraulic Residence Time


<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%202%20-%20Acid%20Rain/images/ANC_calcium_carb_Compare.png" alt="ANC for open, closed, and predicted ANC"/>
</p>
<p align= "center"> Figure 10: ANC for Open and Closed System, and conservative ANC vs Dimensionless Hydraulic Residence Time

Labfire learned that the $CaCO_3$ does not dissolve as readily as sodium bicarbonate so by the time the team started adding added the lake did not have a sufficient level of ANC. Therefore the buffer capacity using compared  $CaCO_3$  to the buffer capacity sodium bicarbonate was reduced, causing a reduction of pH when even small amounts of acid were added. Therefore, the team cannot be certain which model fits the measured ANC values better. As a next step, one could repeat the experiment but make sure that the $CaCO_3$ is not present as a solid at the edges of the tank.


#Questions
1. What do you think would happen if enough $NaHCO_3$ were added to the lake to maintain an ANC greater than 50μeq/L for 3 residence times with the stirrer turned off? How much $NaHCO_3$ would need to be added?

Based on our prelab, we calculated that we would need 6.73 g of  $NaHCO_3$ to be added to the lake to maintain ANC greater than $50μeq/L$ for 3 residence times. If the stirrer was turned off, then we would have to wait for diffusion to occur so that the $NaHCO_3$ is fully mixed which could take a very long time. Therefore, instead of a solution with a high $NaHCO_3$ concentration, we would have a solution with a large mass of $NaHCO_3$ that is not fully aqueous and settles as a solid on the bottom of the tank. This means that even though we would have added the correct amount of $NaHCO_3$ to keep the ANC levels at 50μeq/L for 3 residence times, in reality the ANC levels would drop because the system wouldn't have the required amount of dissolved carbon.   


2. What are some of the complicating factors you might find in attempting to remediate a lake using $CaCO_3$? Below is a list of issues to consider.
extent of mixing
solubility of $CaCO_3$ (find the solubility and compare with NaHCO3)
density of $CaCO_3$ slurry (find the density of CaCO3)

Some problems that may arise when using $CaC0_3$ might be due to limited time as the experiment has shown. If one needs to immediately raise ANC in a body of water, the solubility of $CaC0_3$ may be antithetical to such efforts as shown in Figure 6 where the pH immediately dropped below 4 even .2 units of dimensionless hydraulic residence time in, and did not resemble Figure 1 where the pH slowly approached 3. Solubility of $CaC0_3$ is 15 mg/L while solubility of $NaHCO_3$ is 9600mg/L, which is more than a 100 fold times larger.  


#Conclusions

In this experiment the team discovered that not all chemicals are equal in their effectiveness in remediating acid rain in water bodies. Although theoretically the effectiveness of $CaCO_3$ and $NaHCO_3$ should have been the same after one residence time, due to their difference in solubility the ANC level in the $CaCO_3$ case was not sufficient to mitigate the acidity of the solution coming into the lake. Practically speaking, if there were a case when a lake had to be immediately protected from incoming acid rain, it would be wise to use $NaHCO_3$ as opposed to $CaCO_3$, since it would dissolve more readily. In addition, based on the experiment with $NaHCO_3$ as the carbon source, it was determined that the model that better estimates the ANC levels at any point in the lake would be the closed system model.
```
