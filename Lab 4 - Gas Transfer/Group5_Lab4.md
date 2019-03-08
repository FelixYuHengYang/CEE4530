Felix Yang Eirini Sarri

Lab Fire Group 5

Felix Yang:  4 hours

Eirini Sarri:  4 hours

# Question 1
Eliminate the data from each data set when the dissolved oxygen concentration was less than 2 mg/L. This will ensure that all of the sulfite has reacted. Also remove the data when the dissolved oxygen concentration was greater than 6 mg/L to reduce the effect of measurement errors when the oxygen deficit is small.

Found in code below.

# Question 2
Plot a representative subset of the data showing dissolved oxygen vs. time. Perhaps show 5 plots on one graph.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_2_b.png" alt="Oxygen Concentration vs Time"/>
</p>
<p align="center">Figure 1: Oxygen Concentration vs Time for Flow Rates of $100$, $125$, $175$, $200$, and $225 \frac{\mumol}{s}$</p>

# Question 3
Calculate C⋆ based on the average water temperature, barometric pressure, and the equation from environmental processes analysis called O2_sat. C⋆=PO2e(1727T−2.105) where T is in Kelvin, PO2 is the partial pressure of oxygen in atmospheres, and C⋆ is in mg/L.

Using the following variables, we get a C* value of $8.92 \frac{mg}{L}$.

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
| 100 | 0.000393 |
| 125 | 0.000522 |
| 175 | 0.000496 |
| 200 | 0.000460 |
| 225 | 0.000605 |
| 250 | 0.000976 |
| 350 | 0.000934 |
| 400 | 0.001244 |
| 450 | 0.001265 |
| 475 | 0.001300 |
| 500 | 0.001017 |
| 525 | 0.001044 |
| 550 | [insufficient data in subset] |
| 575 | 0.000916 |
| 650 | 0.001426 |
| 700 | 0.001655 |
| 725 | 0.001327 |
| 750 | 0.001556 |
| 775 | 0.001554 |
| 800 | 0.001008 |
| 825 | 0.000987 |
| 850 | 0.001627 |
| 925 | 0.000709 |
| 950 | 0.001629 |

For the flow rate of $550 \frac{\mu mol}{s}$ there was insufficient data because the trend of dissolved oxygen over time was first decreasing and then increasing as shown in the Figure 2 below.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/550_flow_b.png" alt="550_flow_b"/>
</p>
<p align="center">Figure 2: Dissolved Oxygen Concentration vs Time for Flow Rate of $550\frac{\mu mol}{s}$ </p>

This shows that after the DO values less than $2 \frac{mg}{L}$ are removed, the rest of the data points cannot be linearly related, and therefore linear regression cannot be achieved and a slope (which is the value of $k_{v,l}$) cannot be determined.

# Question 5
Create a graph with a representative plot showing the model curve (as a smooth curve) and the data from one experiment. You will need to derive the equation for the concentration of oxygen as a function of time based on equation (103).

The equation derived for the concentration of oxygen as a function of time is the following:

$C = C_{sat} - (C_{sat} - C_{0})e^{-k_{v,l}\cdot t}$

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_5_500.png" alt="500_flow"/>
</p>
<p align="center">Figure 3: Model and Experimental Data vs Time for Flow Rate of $500\frac{\mu mol}{s}$ </p>

# Question 6
Plot $k_{v,l}$ as a function of airflow rate ($\frac{\mu mol}{s}$).

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_6.png" alt="kvl vs flow rate"/>
</p>
<p align="center">Figure 4: $k_{v,l}$ vs Air Flow Rate </p>

# Question 7
Plot OTE as a function of airflow rate ($\frac{\mu mol}{s}$) with the oxygen deficit (C⋆−C) set at 6 $\frac{mg}{L}$.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Images/Question_7.png" alt="OTE vs flow rate"/>
</p>
<p align="center">Figure 5: OTE vs Air Flow Rate </p>

# Question 8
Comment on the oxygen transfer efficiency and the trend or trends that you observe.

# Question 9
Propose a change to the experimental apparatus that would increase the efficiency.

Oxygen transfer is a remarkably inefficient process; only a small fraction of the oxygen carried by the rising bubbles diffuses into the activated sludge. The most efficient systems use membrane diffusers and achieve an OTE of approximately 10%.

#Conclusions
Go through all the graphs and talk about them. Want relationship between Oxygen concentration and time for different air flows, model vs observed conclusion, kvl vs airflow, and OTE vs airflow.
#Suggestions
-Possibly use a different DO sensor that isn't as sensitive to air bubbles
-Make height of reactor higher so that the oxygen can have time to oxygenate the water. (possibly why the model overestimates)
-membrane diffusers

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
plt.legend(airflows.magnitude)
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
for i in range(0,12):
  slope, intercept, r_value, p_value, std_err = stats.linregress(time_data[i],np.log((C_sat-DO_data[i])/(C_sat-DO_data[i][0]))/(C_sat-DO_data[i][0]))
  print(-slope)
for i in range(13,24):
  slope, intercept, r_value, p_value, std_err = stats.linregress(time_data[i],np.log((C_sat-DO_data[i])/(C_sat-DO_data[i][0]))/(C_sat-DO_data[i][0]))
  print(-slope)

P= 1*u.atm
T_avg=295*u.degK
C_sat=epa.O2_sat(P,T_avg)
C_init_500=DO_data[10][0]

#5 Plot C for flow rate 500 experiments
C_model_500=C_sat-(C_sat-C_init)*(np.exp(-.001017/u.s*time_data[10]))
C_model

fig, ax = plt.subplots()
ax.plot(time_data[10],C_model_500,'r',label='Model')
ax.plot(time_data[10],DO_data[10],'b',label='Observed')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_5_500')
plt.show()


C_init_225=DO_data[4][0]
C_init_225
C_model_225=C_sat-(C_sat-C_init_225)*(np.exp(-0.0173/u.s*time_data[4]))
C_model_225

fig, ax = plt.subplots()
ax.plot(time_data[4],C_model_225,'r',label='Model')
ax.plot(time_data[4],DO_data[4],'b',label='Observed')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_5_225')
plt.show()

#Q6
Airflow_array = [100,125,175,200,225,250,350,400,450,475,500,525,575,650,700,725,750,775,800,825,850,925,950]
Kvl_array=[.000393,.000522,.000496,.000460,.000605,.000976,.000934,.001244,.001265,.001300,.001017,.001044,.000916,.001426,.001655,.001327,.001556,.001554,.001008,.000987,.001627,.000709,.001629]

plt.plot(Airflow_array,Kvl_array,'r')
plt.xlabel(r'$\mu mol/s $')
plt.ylabel(r' $k_v,l\left ( \frac{1}{s} \right )$')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_6')
plt.show()


#Q7
Oxygen_Deficit = 6*u.mg/u.L
MW_O2 = 31998*u.mg/u.mole
f_O2 = 0.21
V = 0.75*u.L
R = 0.082057*(u.L*u.atm)/(u.degK*u.mole)

nair = Airflow_array*u.mol*10**-6/u.s*f_O2
naq = V*Kvl_array*u.s**-1*Oxygen_Deficit/MW_O2

OTE = naq / nair
OTE

plt.plot(Airflow_array,OTE,'r')
plt.xlabel(r'$\mu mol/s $')
plt.ylabel(r' $Oxygen Transfer Efficiency$')
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_7')
plt.show()


```
  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/100.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/125.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/175.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/200.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/225.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/250.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/350.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/400.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/450.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/475.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/500.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/525.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/550.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/575.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/650.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/700.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/725.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/750.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/775.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/800.xls


  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/825.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/850.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/925.xls

  https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab%204%20-%20Gas%20Transfer/Aeration/950.xls
