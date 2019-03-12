Felix Yang Eirini Sarri

Lab Fire Group 5

Felix Yang:  4 hours

Eirini Sarri:  4 hours

# Question 1
Eliminate the data from each data set when the dissolved oxygen concentration was less than 2 mg/L. This will ensure that all of the sulfite has reacted. Also remove the data when the dissolved oxygen concentration was greater than 6 mg/L to reduce the effect of measurement errors when the oxygen deficit is small.

This step is found in code below.

# Question 2
Plot a representative subset of the data showing dissolved oxygen vs. time. Perhaps show 5 plots on one graph.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_2_b.png" alt="Oxygen Concentration vs Time"/>
</p>
<p align="center">Figure 1: Oxygen Concentration vs Time for Flow Rates of 100, 125, 175, 200, and 225 umol/s</p>

# Question 3
Calculate $C_{sat}$ based on the average water temperature, barometric pressure, and the equation from environmental processes analysis called O2_sat. $C_{sat}=P_{O2}e^{\frac{1727}{T}−2.105}$ where T is in Kelvin, $P_{O2}$ is the partial pressure of oxygen in atmospheres, and $C_{sat}$ is in mg/L.

Using the following variables, we get a C_sat value of $8.92 \frac{mg}{L}$.

Table 1: Variables Used to Determine The Saturated Oxygen Concentration

| Variable | Value | Units |
|:--------:|:-----:|:-----:|
| $P_{O2}$ | 0.21  |  atm  |
|    T     |  295  |   K   |

# Question 4
Estimate $k_{v,l}$ using linear regression and equation (103) for each data set.

Using the code found below, the team determined the $k_{v,l}$ for all the flow rates. The results are summarized in the table below.

Table 2: $k_{v,l}$ For Each Flow Rate

| Flow Rate [$\frac{\mu mol}{s}$] | $k_{v,l}$ [$\frac{1}{s}$] |
|:--------:|:-----:|
| 100 | 0.00271 |
| 125 | 0.00363 |
| 175 | 0.00345 |
| 200 | 0.00318 |
| 225 | 0.00418 |
| 250 | 0.00667 |
| 350 | 0.00642 |
| 400 | 0.00847 |
| 450 | 0.00899 |
| 475 | 0.00899 |
| 500 | 0.00711 |
| 525 | 0.00735 |
| 550 | 0.00557 |
| 575 | 0.00643 |
| 650 | 0.00972 |
| 700 | 0.01136 |
| 725 | 0.00902 |
| 750 | 0.01078 |
| 775 | 0.01074 |
| 800 | 0.00704 |
| 825 | 0.00691 |
| 850 | 0.00993 |
| 925 | 0.00492 |
| 950 | 0.01136 |

Initially, the flow rate of $550 \frac{\mu mol}{s}$ had no $k_{vl}$ value because the trend of dissolved oxygen over time was first decreasing and then increasing as shown in the Figure 2 below.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/550_flow_b.png" alt="550_flow_b"/>
</p>
<p align="center">Figure 2: Dissolved Oxygen Concentration vs Time for Flow Rate of 550 umol/s$ </p>

This shows that after the DO values less than $2 \frac{mg}{L}$ are removed, the rest of the data points cannot be linearly related, and therefore linear regression cannot be achieved and a slope (which is the value of $k_{v,l}$) cannot be determined. Thus, the first three values were removed so that the function that finds $k_{v,l}$ could function properly.

# Question 5
Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).

The model as represented in the red line in the figure below is the concentration of oxygen as a function of time derived to be the following equation:

$C(t) = C_{sat} - (C_{sat} - C_{0})e^{-k_{v,l}\cdot t}$

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_5_500_fixed.png" alt="500_flow"/>
</p>
<p align="center">Figure 3: Model and Experimental Data vs Time for Flow Rate of 500 umol/s</p>


# Question 6
Plot $k_{v,l}$ as a function of airflow rate ($\frac{\mu mol}{s}$).

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_6_fixed.png" alt="kvl vs flow rate"/>
</p>
<p align="center">Figure 4: $kv,l vs Air Flow Rate </p>

# Question 7
Plot OTE as a function of airflow rate ($\frac{\mu mol}{s}$) with the oxygen deficit $(C_{sat}−C)$ set at 6 $\frac{mg}{L}$.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_7_fixed.png" alt="OTE vs flow rate"/>
</p>
<p align="center">Figure 5: OTE vs Air Flow Rate </p>

# Question 8
Comment on the oxygen transfer efficiency and the trend or trends that you observe.

Oxygen Transfer Efficiency seems to be between 0.05% and 0.27%. The general trend shows that as airflow rate increases, OTE goes down in a linear fashion. However, it is significant to mention that the efficiencies that were calculated were very small, which is reasonable since, according to the textbook "the most efficient systems use membrane diffusers and achieve an OTE of approximately 10%" meaning that even a system that has been designed and implemented in real life for the purpose of reaeration also has a relatively small efficiency. OTE gets smaller with increasing flow rate because it is inversely proportional to Qair (Qair in the denominator of the OTE fraction equation).

# Question 9
Propose a change to the experimental apparatus that would increase the efficiency.

A change that might increase efficiency is a tank with larger depth, so that oxygen could have more time to travel to the surface, and therefore higher probability to reaereate the water before it is released into the atmosphere.

#Conclusions

From Figure 1, it can be seen that for the first 5 flow rates oxygen concentration tends to go up as a function of time. This is because experiments were ran after the DO was depleted using cobalt with the exception of the red line representing the 200 $\mu mol/s$ flow rate, which was likely due to an error in the ProCoDA experiment start time.

Figure 3 shows a sample graph of model and experimental data vs time for the flow rate of 500 $\mu mol/s$. The blue line representing the observed data is very close to the red line representing the theoretical model. This is despite factors such as the low depth of reactor, and low efficiency of the system delivering oxygen, which would have not been accounted for in the model equation.

Figure 4 shows an increase of $k_{v,l}$ with increasing airflow rate, even though large deviations can be observed (large variability of data.) This increase however is not significant enough to increase the OTE with increasing flow rates as seen in Figure 5, where OTE decreasing with increasing flow rate. This means that the effect of increasing $k_{v,l}$ (in the numerator of the OTE equation) is not as significant as the effect of increasing flow rate (in the denominator of the OTE equation) and therefore OTE decreases as flow rate increases. In other words, there is an inverse relationship between OTE and air flow rate.

#Suggestions
One suggestion that lab fire has for future experiments is to use a dissolved oxygen probe that isn't as sensitive to air bubbles. Because the reactor was relatively small, the metal stirrer constantly created turbulence that sometimes sent air bubbles onto the membrane of the DO probe, which made the readings inaccurate. This could also be addressed by using bigger reactors, so that one can clamp the DO probe farther from the oxygen influent and the stirrer.

Again touching on the size, the group believes that the height of the reactor could also be increased so that the oxygen coming into the reactor can have time to oxygenate the water. However, the low depth did not seem to affect how accurate the models were in predicting DO concentration across time.

The last suggestion is possibly to use membrane diffusers to obtain higher OTE values. However, this is likely not feasible in the lab as it is used in the industry, meaning it is likely too expensive for laboratory experiments like this one.

# Appendix

```python
from aguaclara.core.units import unit_registry as u
import aguaclara.research.environmental_processes_analysis as epa
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats
import collections
import os
from pathlib import Path

# This code is included because there is a bug in the version of this code that is in epa.

def aeration_data(DO_column, dirpath):
    """This function extracts the data from folder containing tab delimited files of aeration data. The file must be the original tab delimited file.
    All text strings below the header must be removed from these files.
    The file names must be the air flow rates with units of micromoles/s.
    An example file name would be "300.xls" where 300 is the flow rate in
    micromoles/s. The function opens a file dialog for the user to select
    the directory containing the data.

    Parameters
    ----------
    DO_column : int
        index of the column that contains the dissolved oxygen concentration
        data.

    dirpath : string
        path to the directory containing aeration data you want to analyze

    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate

    airflows : numpy array
        sorted array of air flow rates with units of micromole/s attached

    DO_data : numpy array list
        sorted list of numpy arrays. Thus each of the numpy data arrays can
        have different lengths to accommodate short and long experiments

    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds

    Examples
    --------

    """
    #return the list of files in the directory
    filenames = os.listdir(dirpath)
    #extract the flowrates from the filenames and apply units
    airflows = ((np.array([i.split('.', 1)[0] for i in filenames])).astype(np.float32))
    #sort airflows and filenames so that they are in ascending order of flow rates
    idx = np.argsort(airflows)
    airflows = (np.array(airflows)[idx])*u.umole/u.s
    filenames = np.array(filenames)[idx]

    filepaths = [os.path.join(dirpath, i) for i in filenames]
    #DO_data is a list of numpy arrays. Thus each of the numpy data arrays can have different lengths to accommodate short and long experiments
    # cycle through all of the files and extract the column of data with oxygen concentrations and the times
    DO_data=[epa.column_of_data(i,0,DO_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,0,-1)).to(u.s) for i in filepaths]
    aeration_collection = collections.namedtuple('aeration_results','filepaths airflows DO_data time_data')
    aeration_results = aeration_collection(filepaths, airflows, DO_data, time_data)
    return aeration_results

# The column of data containing the dissolved oxygen concentrations
DO_column = 2
dirpath = "C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Aeration"
filepaths, airflows, DO_data, time_data = aeration_data(DO_column,dirpath)
DO_data

# Plot the raw data
for i in range(airflows.size):
  plt.plot(time_data[i], DO_data[i],'-')

for i in range(5):
  plt.plot(time_data[i], DO_data[i],'-')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(airflows)
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_2_b')
plt.show()

plt.plot(time_data[12],DO_data[12],'r')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/550_flow_b')
plt.show()

#delete data that is less than 2 or greater than 6 mg/L
DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(airflows.size):
  idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
  idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
  time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
  DO_data[i] = DO_data[i][idx_start:idx_end]


range(airflows.size)
K_vl_array=(np.zeros(24))/u.s
K_vl_array[1]
for i in range(0,24):
  slope, intercept, r_value, p_value, std_err = stats.linregress(time_data[i],np.log((C_sat-DO_data[i])/(C_sat-DO_data[i][0])))
  K_vl_array[i]=-slope/u.s
  print(-slope)
K_vl_array
P= 1*u.atm
T_avg=295*u.degK
C_sat=epa.O2_sat(P,T_avg)
C_init_500=DO_data[10][0]
airflows[10]
#C_init_125=DO_data[1][0]

#5 Plot C for flow rate 500 experiments
C_model_500=C_sat-(C_sat-C_init_500)*(np.exp(-K_vl_array[10]*(time_data[10]-time_data[10][0])))
#C_model_125=C_sat-(C_sat-C_init_125)*(np.exp(-.000522/u.s*time_data[1]))
C_model_500
#C_model_125

fig, ax = plt.subplots()
ax.plot(time_data[10],C_model_500,'r',label='Model')
ax.plot(time_data[10],DO_data[10],'bo',label='Observed')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_5_500_fixed')
plt.show()


#Q6
plt.plot(airflows,K_vl_array,'r')
plt.xlabel(r'$\mu mol/s $')
plt.ylabel(r' $k_v,l\left ( \frac{1}{s} \right )$')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_6_fixed')
plt.show()


#Q7
Oxygen_Deficit = 6*u.mg/u.L
MW_O2 = 31998*u.mg/u.mole
f_O2 = 0.21
V = 0.75*u.L
R = 0.082057*(u.L*u.atm)/(u.degK*u.mole)

nair = airflows*u.mol*10**-6/u.s*f_O2
naq = V*K_vl_array*u.s**-1*Oxygen_Deficit/MW_O2

OTE = naq / nair
OTE

plt.plot(airflows,OTE,'r')
plt.xlabel(r'$\mu mol/s $')
plt.ylabel(r' $Oxygen Transfer Efficiency$')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_7_fixed')
plt.show()


`
