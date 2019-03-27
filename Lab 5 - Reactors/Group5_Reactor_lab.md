Felix Yang Eirini Sarri

Lab Fire Group 5

Felix Yang:  hours

Eirini Sarri: 4 hours
# Introduction and Objectives
A reactor is a system with a defined boundary that can experience flow in and out. There are various types of reactors such as Continuously Mixed Flow Reactors (CMFR) and Plug Flow Reactors (PFR) and many natural and engineered systems can be modeled using reactor equations. The purpose of reactors is to maximize the time of contact between a solute (tracer, contaminant, etc) with a solvent (water).  The objective of this experiment was to investigate the effect of different configuration of a rector on the effective contact time of a red dye tracer and water.


# Procedures
This experiment was divided into four parts, each part corresponding to a different reactor design. In general, for all reactor designs, a setup which supplied the reactor with a continuous inflow of DI water was used, with a weir at the effluent for a continuous outflow, keeping the volume of the reactor constant. The tracer was always added near the input of the reactor and a photometer was placed near the effluent, where it logged the concentration of tracer it came into contact with, therefore producing a graph of concentration of red dye versus time. The smaller the concentrations of red dye at a specific moment in time, the better the mixing, as more dye was incorporated into the water instead of moving unmixed towards the effluent. The four reactor designs are as follows:

## Continuously Mixed Flow Reactor (CMFR)
The first experiment that was conducted was turning our reactor into a CMFR. To do that, the team used a plastic tank as a reactor with a volume of 2.7 L and a stirring rod to achieve continuous mixing. There was a constant inflow and outflow of water at 100 rpm. $810 uL$ of $10 \frac{g}{L}$ of red dye tracer, which corresponded to a concentration of $30 \frac{mg}{L}$, was added near the inflow of the reactor and was let to mix with the water. The photometer was taking continuous measurements of the concentration of red dye near the effluent. The experiment was terminated when the concentration of red dye reached approximately $0.5 \frac{mg}{L}$. Then the weight of the water was measured and therefore the final volume was calculated assuming the density of the solution to be equal to the density of water.

## Baffle Design 1
The second experiment conducted used a reactor design which included two baffles with four $1 cm$ holes each. The baffles were placed with the holes on opposite sides of the reactor so that water would be forced to take longer route to reach the effluent. As in the reactor above, a stirring rod was added in the middle of the eractor to achieve continuous mixing. There was a constant inflow and outflow of water at 100 rpm. $7 mL$ of $10 \frac{g}{L}$ of red dye tracer was added near the inflow of the reactor and was let to mix with the water. The photometer was taking continuous measurements of the concentration of red dye near the effluent. The experiment was terminated when the concentration of red dye reached approximately $0.5 \frac{mg}{L}$. Then the weight of the water was measured and therefore the final volume was calculated assuming the density of the solution to be equal to the density of water. In addition, the concentration of red dye of the whole reactor was measured using a photometer.

## Baffle Design 2
The third experiment conducted used a reactor design which included four baffles with four $1 cm$ holes each. The baffles were placed with the holes on opposite sides of the reactor so that water would be forced to take longer route to reach the effluent. As in the reactor above, a stirring rod was added in the middle of the eractor to achieve continuous mixing. There was a constant inflow and outflow of water at 100 rpm. $5 mL$ of $10 \frac{g}{L}$ of red dye tracer was added near the inflow of the reactor and was let to mix with the water. The photometer was taking continuous measurements of the concentration of red dye near the effluent. The experiment was terminated when the concentration of red dye reached approximately $0.5 \frac{mg}{L}$. Then the weight of the water was measured and therefore the final volume was calculated assuming the density of the solution to be equal to the density of water. In addition, the concentration of red dye of the whole reactor was measured using a photometer.

## Baffle Design 3
The fourth experiment conducted used a reactor design which included two baffles with four $0.4 cm$ holes each. The baffles were placed with the holes on opposite sides of the reactor so that water would be forced to take longer route to reach the effluent. As in the reactor above, a stirring rod was added in the middle of the eractor to achieve continuous mixing. There was a constant inflow and outflow of water at 100 rpm. $7 mL$ of $10 \frac{g}{L}$ of red dye tracer was added near the inflow of the reactor and was let to mix with the water. The photometer was taking continuous measurements of the concentration of red dye near the effluent. The experiment was terminated when the concentration of red dye reached approximately $0.5 \frac{mg}{L}$. Then the weight of the water was measured and therefore the final volume was calculated assuming the density of the solution to be equal to the density of water. In addition, the concentration of red dye of the whole reactor was measured using a photometer.

# Results and Discussion

1. Use multivariable nonlinear regression to obtain the best fit between the experimental data and the two models by minimizing the sum of the squared errors. Use epa.Solver_AD_Pe and epa.Solver_CMFR_N. These functions will minimize the error by varying the values of average residence time, (mass of tracer/reactor volume), and either the number of CMFR in series or the Peclet number.

Found in code below.

2. Generate a plot showing the experimental data as points and the model results as thin lines for each of your experiments. Explain which model fits best and discuss those results based on your expectations.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/images/Question_2%20Exp_1.png" alt="550_flow_b"/>
</p>
<p align="center">Figure 1: Observed data for experiment 1 and models </p>

<p align="center">
<img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/images/Question%202%20Exp2.png" alt="550_flow_b"/>
</p>
<p align="center">Figure 2: Observed data for experiment 2 and models</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/images/Question%202%20Exp3.png" alt="550_flow_b"/>
</p>
<p align="center">Figure 3: Observed data for experiment 3 and models </p>

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/images/Question%202%20Exp4.png" alt="Figure 4: Observed data for experiment 4 and models"/>
</p>

<p align="center">Figure 4: Observed data for experiment 4 and models </p>

Generally speaking, the CMFR model consistently fit the observed data better. This is because as we increase the number of CMFR in series we get closer to simulating a PFR, meaning that no matter what the reactor design, we can approximate the concentration of red dye assuming the system is composed of many CMFRs in series. Also, the Peclet numbers from the model equations were very small, leading to a large predicted variability that was not found in the experimental data.

3. Compare the trends in the estimated values of N and Pe across your set of experiments. How did your chosen reactor modifications affect dispersion?

As the number of baffles increased from 0 (Experiment 1 - CMFR) to 2 (Experiments 2 and 4) to 4 (Experiment 3), both N and Pe increased in value. This is the expected result, as a higher N and Pe value corresponds to a system more closely simulating a PFR, which can be achieved by adding multiple CMFRs in series. In addition to this observation, it was noted that the same number of baffles but different sized-holes had an effect on the N and Pe numbers. The smaller the holes on the baffle, the higher the Pe number, which is a reasonable result since putting "more obstacles" for the water to go through increases the contact time of the red dye with water, matching a PFR more closely. On the other hand, using the same rationale, we would expect a higher N value for experiment 4; however, the model guesses an N value of 1 which is not supported by this hypothesis.

4. Report the values of t⋆ at F = 0.1 for each of your experiments. Do they meet your expectations?

t⋆ values were .16, .31,.3 and .345 at F=0.1 for experiments 1-4, respectively. The difference between the first experiment and last 3 line up with initial expectations, but the negligible difference between the 2nd and 3rd t⋆ values was not expected.

5. Evaluate whether there is any evidence of “dead volumes” or “short circuiting” in your reactor.

There was evidence that there were dead volumes and short circuiting in the experimental reactor. In the picture below there is dye that is still highly concentrated in the corner of the reactor. Short circuiting was also present as the baffles were only taped to hold it in place, which left a gap on the sides, allowing water to move directly down the sides of the baffles. A seal would have prevented this, but there were time and resource constraints.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/images/deadvolume.jpg" alt="550_flow_b"/>
</p>
<p align="center">Dead volume in reactor</p>

6. Make a recommendation for the design of a full scale chlorine contact tank. As part of your recommendation discuss the parameter you chose to vary as part of your experimentation and what the optimal value was determined to be.

Group 5 would recommend that in a full scale chlorine contact tank one should have conditions as close to an ideal PFR as possible. This can be achieved by having high length to width ratio of baffles, that resemble a maze. This would maximize the contact time that the chlorine has with the pathogen before the water is sent to the distribution system, and eventually in people's bodies. Based on our the four experiments that were conducted, Group 5 would suggest a design more similar to Experiment 4, as Experiment 4 was the one with the highest t⋆ and therefore the highest contact time.

# Conclusions

In conclusion, the more complicated the reactor system, the more the behavior of the reactor matches that of a PFR. Comparing between increasing the number of baffles versus decreasing the size of holes, it was determined that a decrease in the size of holes was actually more effective in increasing contact time. However, larger differences were expected overall but were not observed. Between the Advective Dispersion and CMFR models, the CMFR model was the one that matched the experimental data more closely.


# Suggestions

As future steps or changes, the team would recommend conducting experiments with larger deviations, i.e. 3 CMFRs in series vs 9 CMFRs in series, so that differences become more noticeable. In addition, experimenting with water flow rate would be an interesting variation, to determine what factor affects contact time the most.


# Python Code Appendix

```python
  from aguaclara.core.units  import unit_registry as u
  import aguaclara.research.environmental_processes_analysis as epa
  import aguaclara.core.utility as ut
  from scipy import optimize
  import numpy as np
  import matplotlib.pyplot as plt
  import pandas as pd
  from scipy import stats
  from scipy.interpolate import make_interp_spline, BSpline
  from math import*

#Reactor Characteristics Lab
#Variable Names
Volume_Tot=30*u.cm*15*u.cm*6*u.cm
V_Dye_Exp_1=8100*u.uL
V_Dye_Exp_2=7000*u.uL
V_Dye_Exp_3=5000*u.uL
V_Dye_Exp_4=7000*u.uL
C_Dye=10*u.g/u.L
M_Dye_Exp_1 = (V_Dye_Exp_1 * C_Dye).to(u.mg)
M_Dye_Exp_2 = (V_Dye_Exp_2 * C_Dye).to(u.mg)
M_Dye_Exp_3 = (V_Dye_Exp_3 * C_Dye).to(u.mg)
M_Dye_Exp_4 = (V_Dye_Exp_4 * C_Dye).to(u.mg)
M_Tank_1=490*u.g
M_Tank_2=592*u.g
M_Tank_3=590*u.g
M_Tank_4=593*u.g
M_Tank_Exp_1=3213*u.g
M_Tank_Exp_2=3154*u.g
M_Tank_Exp_3=3154*u.g
M_Tank_Exp_4=3210*u.g
V_1=(M_Tank_Exp_1-M_Tank_1)/(1*u.g/u.mL)
V_2=(M_Tank_Exp_2-M_Tank_2)/(1*u.g/u.mL)
V_3=(M_Tank_Exp_3-M_Tank_3)/(1*u.g/u.mL)
V_4=(M_Tank_Exp_4-M_Tank_4)/(1*u.g/u.mL)
Q=380*u.mL/u.minute
theta_guess_1=V_1/Q
theta_guess_2=V_2/Q
theta_guess_3=V_3/Q
theta_guess_4=V_4/Q
C_bar_guess_1 = M_Dye_Exp_1/V_1
C_bar_guess_2 = M_Dye_Exp_2/V_2/2
C_bar_guess_3 = M_Dye_Exp_3/V_3/4
C_bar_guess_4 = M_Dye_Exp_4/V_4/2

#File path for the excel file containing the experimental measurements

link_exp_1 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/Files/30mgperL.txt"
link_exp_2 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/Files/Exp2.txt"
link_exp_3 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/Files/Exp3.txt"
link_exp_4 = "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%205%20-%20Reactors/Files/Exp4.txt"


#Pandas dataframe with the data in the file
Experiment_1 = pd.read_csv(link_exp_1,delimiter='\t')
Experiment_2 = pd.read_csv(link_exp_2,delimiter='\t')
Experiment_3 = pd.read_csv(link_exp_3,delimiter='\t')
Experiment_4 = pd.read_csv(link_exp_4,delimiter='\t')

# set the start index of the data file to one past the note indicating the start.
start_exp_1=8
start_exp_2=218
start_exp_3=11
start_exp_4=22
time_1 = epa.column_of_time(link_exp_1,start_exp_1)
dimless_time_1 = time_1/theta_guess_1.to(u.days)
conc_1=epa.column_of_data(link_exp_1,start_exp_1,1)*u.mg/u.L
time_2 = epa.column_of_time(link_exp_2,start_exp_2)
dimless_time_2=time_2/theta_guess_2.to(u.days)
conc_2 = epa.column_of_data(link_exp_2,start_exp_2,1)*u.mg/u.L
time_3 =epa.column_of_time(link_exp_3,start_exp_3)
dimless_time_3=time_3/theta_guess_3.to(u.days)
conc_3 = epa.column_of_data(link_exp_3,start_exp_3,1)*u.mg/u.L
time_4 =epa.column_of_time(link_exp_4,start_exp_4)
dimless_time_4=time_4/theta_guess_4.to(u.days)
conc_4 = epa.column_of_data(link_exp_4,start_exp_4,1)*u.mg/u.L

#Now plot the graph
fig, ax = plt.subplots()
ax.plot(time_1,conc_1,'r')
plt.xlabel('Time')
plt.ylabel('Concentration (mg/L)')

#plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_1')
plt.show()  

#AD Model Experiment 1
theta_1_AD, C_bar_1_AD, Pe_1_AD = epa.Solver_AD_Pe(time_1,conc_1,theta_guess_1,C_bar_guess_1)
E_1_AD=epa.E_Advective_Dispersion((time_1/theta_guess_1).to_base_units(), Pe_1_AD)
Model_AD_Exp1=C_bar_1_AD*E_1_AD

Pe_1_AD

#CMFR Model Experiment 1
theta_1_CMFR, C_bar_1_CMFR, N_1_CMFR = epa.Solver_CMFR_N(time_1,conc_1,theta_guess_1,C_bar_guess_1)
E_1_CMFR=epa.E_CMFR_N((time_1/theta_guess_1).to_base_units(), N_1_CMFR)
Model_CMFR_Exp1=C_bar_1_CMFR*E_1_CMFR

N_1_CMFR

#AD Model Experiment 2
theta_2_AD, C_bar_2_AD, Pe_2_AD = epa.Solver_AD_Pe(time_2,conc_2,theta_guess_2,C_bar_guess_2)
E_2_AD=epa.E_Advective_Dispersion((time_2/theta_guess_2).to_base_units(), Pe_2_AD)
Model_AD_Exp2=C_bar_2_AD*E_2_AD

Pe_2_AD

#CMFR Model Experiment 2
theta_2_CMFR, C_bar_2_CMFR, N_2_CMFR = epa.Solver_CMFR_N(time_2,conc_2,theta_guess_2,C_bar_guess_2)
E_2_CMFR=epa.E_CMFR_N((time_2/theta_guess_2).to_base_units(), N_2_CMFR)
Model_CMFR_Exp2=C_bar_2_CMFR*E_2_CMFR

N_2_CMFR

#AD Model Experiment 3
theta_3_AD, C_bar_3_AD, Pe_3_AD = epa.Solver_AD_Pe(time_3,conc_3,theta_guess_3,C_bar_guess_3)
E_3_AD=epa.E_Advective_Dispersion((time_3/theta_guess_3).to_base_units(), Pe_3_AD)
Model_AD_Exp3=C_bar_3_AD*E_3_AD

Pe_3_AD

#CMFR Model Experiment 3
theta_3_CMFR, C_bar_3_CMFR, N_3_CMFR = epa.Solver_CMFR_N(time_3,conc_3,theta_guess_3,C_bar_guess_3)
E_3_CMFR=epa.E_CMFR_N((time_3/theta_guess_3).to_base_units(), N_3_CMFR)
Model_CMFR_Exp3=C_bar_3_CMFR*E_3_CMFR

N_3_CMFR

#AD Model Experiment 4
theta_4_AD, C_bar_4_AD, Pe_4_AD = epa.Solver_AD_Pe(time_4,conc_4,theta_guess_4,C_bar_guess_4)
E_4_AD=epa.E_Advective_Dispersion((time_4/theta_guess_4).to_base_units(), Pe_4_AD)
Model_AD_Exp4=C_bar_4_AD*E_4_AD

Pe_4_AD

#CMFR Model Experiment 4
theta_4_CMFR, C_bar_4_CMFR, N_4_CMFR = epa.Solver_CMFR_N(time_4,conc_4,theta_guess_4,C_bar_guess_4)
E_4_CMFR=epa.E_CMFR_N((time_4/theta_guess_4).to_base_units(), N_4_CMFR)
Model_CMFR_Exp4=C_bar_4_CMFR*E_4_CMFR

N_4_CMFR

#Question 2

#Plot data, AD,and CMFR models
fig, ax = plt.subplots()
ax.plot(dimless_time_1,Model_AD_Exp1,'c',label='AD model')
ax.plot(dimless_time_1,Model_CMFR_Exp1,'y',label='CMFR model')
ax.plot(dimless_time_1,conc_1,'ro',label='Observed')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('Concentration (mg/L)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Question_2 Exp_1')
plt.show()

##Exp2
fig, ax = plt.subplots()
ax.plot(dimless_time_2,Model_AD_Exp2,'c',label='AD model')
ax.plot(dimless_time_2,Model_CMFR_Exp2,'y',label='CMFR model')
ax.plot(dimless_time_2,conc_2,'ro',label='Observed')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('Concentration (mg/L)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Question 2 Exp2')
plt.show()

##Exp3
fig, ax = plt.subplots()
ax.plot(dimless_time_3,Model_AD_Exp3,'c',label='AD model')
ax.plot(dimless_time_3,Model_CMFR_Exp3,'y',label='CMFR model')
ax.plot(dimless_time_3,conc_3,'ro',label='Observed')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('Concentration (mg/L)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Question 2 Exp3')
plt.show()


##Exp4
fig, ax = plt.subplots()
ax.plot(dimless_time_4,Model_AD_Exp4,'c',label='AD model')
ax.plot(dimless_time_4,Model_CMFR_Exp4,'y',label='CMFR model')
ax.plot(dimless_time_4,conc_4,'ro',label='Observed')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('Concentration (mg/L)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Question 2 Exp4')
plt.show()


#Question 3
#Exp1
E_EXP_1=(conc_1*V_1/M_Dye_Exp_1).to(u.dimensionless)
E_EXP_1
fig, ax = plt.subplots()
ax.plot(dimless_time_1,E_EXP_1,'c',label='E(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('E(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_1_E')
plt.show()


#trapezoidal integration
F_1=np.zeros(E_EXP_1.size)
for i in range(E_EXP_1.size):
  F_1[i]=np.trapz(E_EXP_1[0:i],dimless_time_1[0:i])
  if F_1[i]<.1:
    print('F is not over .1 at '+str(dimless_time_1[i]))
  else:
    print('F is over .1 at '+ str(dimless_time_1[i]))

t_star_1=.16    
fig, ax = plt.subplots()
ax.plot(dimless_time_1,F_1,'c',label='F(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('F(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_1_F')
plt.show()

##Exp 2
E_EXP_2=(conc_2*V_2/M_Dye_Exp_2).to(u.dimensionless)
fig, ax = plt.subplots()
ax.plot(dimless_time_2,E_EXP_2,'c',label='E_2(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('E(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_2_E')
plt.show()

dimless_time_2
F_2=np.zeros(E_EXP_2.size)
for i in range(E_EXP_2.size):
  F_2[i]=np.trapz(E_EXP_2[0:i],dimless_time_2[0:i])
  if F_2[i]<.1:
    print('F is not over .1 at '+str(dimless_time_2[i]))
  else:
    print('F is over .1 at '+ str(dimless_time_2[i]))
t_star_2=.31

fig, ax = plt.subplots()
ax.plot(dimless_time_2,F_2,'c',label='F_2(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('F(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_2_F')
plt.show()

##Exp 3

E_EXP_3=(conc_3*V_3/M_Dye_Exp_3).to(u.dimensionless)
fig, ax = plt.subplots()
ax.plot(dimless_time_3,E_EXP_3,'c',label='E_3(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('E_3(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_3_E')
plt.show()

dimless_time_3
F_3=np.zeros(E_EXP_3.size)
for i in range(E_EXP_3.size):
  F_3[i]=np.trapz(E_EXP_3[0:i],dimless_time_3[0:i])
  if F_3[i]<.1:
    print('F is not over .1 at '+str(dimless_time_3[i]))
  else:
    print('F is over .1 at '+ str(dimless_time_3[i]))
t_star_3=.3

fig, ax = plt.subplots()
ax.plot(dimless_time_3,F_3,'c',label='F_3(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('F(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_3_F')
plt.show()


##Exp 4
E_EXP_4=(conc_4*V_4/M_Dye_Exp_4).to(u.dimensionless)
fig, ax = plt.subplots()
ax.plot(dimless_time_4,E_EXP_4,'c',label='E_4(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('E_4(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_4_E')
plt.show()

dimless_time_4
F_4=np.zeros(E_EXP_4.size)
for i in range(E_EXP_4.size):
  F_4[i]=np.trapz(E_EXP_4[0:i],dimless_time_4[0:i])
  if F_4[i]<.1:
    print('F is not over .1 at '+str(dimless_time_4[i]))
  else:
    print('F is over .1 at '+ str(dimless_time_4[i]))
t_star_4=.345

fig, ax = plt.subplots()
ax.plot(dimless_time_4,F_4,'c',label='F_4(t)')
plt.xlabel('Dimensionless Residence Time')
plt.ylabel('F_4(t)')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 5 - Reactors/images/Exp_4_F')
plt.show()





 ```
