Group 5
Felix Yang
Irene Sarri

#Data Analysis
1. Plot the breakthrough curves showing $\frac{C}{C_0}$ versus time.

<p align="center">
  <img src="link to graph here" alt="C/C_o versus time/>
</p>
<p align="center">Figure 1. Tracer curves for sand columns at two different flow rates. It is likely that different setups had different amounts of tubing volume that influenced how long it took for the tracer to reach the detector.  </p>

<p align="center">
  <img src="link to graph here" alt="C/C_o versus time/>
</p>
<p align="center"> Figure 2. Tracer curves for columns with different masses of activated carbon. </p>

2. Find the time when the effluent concentration was 50% of the influent concentration and plot that as a function of the mass of activated carbon used.

<p align="center">
  <img src="link to graph here" alt="PH vs Dimensionless Hydraulic Residence Time"/>
</p>
<p align="center">Figure 3: C/C_o versus time </p>

3. Calculate the retardation coefficient (Radsorption) based on the time to breakthrough for the columns with and without activated carbon.
4. Calculate the q0 for each of the columns based on equation (97). Plot this as a function of the mass of activated carbon used.
5. What did you learn from this analysis? How can you explain the results that you have obtained? What changes to the experimental method do you recommend for next year (or for a project)?
#Conclusions

#Suggestions


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



def adsorption_data(C_column, dirpath):
    """This function extracts the data from folder containing tab delimited
    files of adsorption data. The file must be the original tab delimited file.

    Parameters
    ----------
    C_column : int
        index of the column that contains the dissolved oxygen concentration
        data.
    dirpath : string
        path to the directory containing aeration data you want to analyze
    Returns
    -------
    filepaths : string list
        all file paths in the directory sorted by flow rate
    time_data : numpy array list
        sorted list of numpy arrays containing the times with units of seconds
    Examples
    --------
    """
    #return the list of files in the directory
    metadata = pd.read_csv(dirpath + '/metadata.txt', delimiter='\t')
    filenames = metadata['file name']
    #extract the flowrates from the filenames and apply units
    #sort airflows and filenames so that they are in ascending order of flow rates


    filepaths = [dirpath + '/' + i for i in filenames]
    #C_data is a list of numpy arrays. Thus each of the numpy data arrays can have different lengths to accommodate short and long experiments
    # cycle through all of the files and extract the column of data with oxygen concentrations and the times
    C_data=[epa.column_of_data(i,epa.notes(i).last_valid_index() + 1,C_column,-1,'mg/L') for i in filepaths]
    time_data=[(epa.column_of_time(i,epa.notes(i).last_valid_index() + 1,-1)).to(u.s) for i in filepaths]

    adsorption_collection = collections.namedtuple('adsorption_results','metadata filenames C_data time_data')
    adsorption_results = adsorption_collection(metadata, filenames, C_data, time_data)
    return adsorption_results


C_column = 1
dirpath = "https://raw.githubusercontent.com/monroews/CEE4530/master/Examples/data/Adsorption"



metadata, filenames, C_data, time_data = adsorption_data(C_column,dirpath)
metadata

Column_D = 1 * u.inch
Column_A = pc.area_circle(Column_D)
Column_L = 15.2 * u.cm
Column_V = Column_A * Column_L
#I'm guessing at the volume of water in the tubing, in the photometer, and in the space above and below the column. This parameter could be adjusted!
Tubing_V = 60 * u.mL
Flow_rate = ([metadata['flow (mL/s)'][i] for i in metadata.index])* u.mL/u.s
Mass_carbon= ([metadata['carbon (g)'][i] for i in metadata.index])* u.g
Tubing_HRT = Tubing_V/Flow_rate
#to make things simple we are assuming that the porosity is the same for sand and for activated carbon. That is likely not true!
porosity = 0.4
v_a = 1 * u.mm/u.s
C_0 = 50 * u.mg/u.L
t_water = (Column_L*porosity/v_a).to(u.s)
#estimate the HRT for all of the columns
HRT = (porosity * Column_V/Flow_rate).to(u.s)

#zero the concentration data by subtracting the value of the first data point from all data points. Do this in each data set.
for i in range(np.size(filenames)):
  C_data[i]=C_data[i]-C_data[i][0]


#Create a graph of the columns that didn't have any activated carbon
mylegend = []
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] == 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(metadata['flow (mL/s)'][i]) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=3,left=0);
plt.ylabel(r'Normalized red dye concentration $\left ( \frac{mg}{L} \right )$');
plt.legend(mylegend);
plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Lab 6 - Adsorption/Images/Question 1a')
plt.show()

# create a graph of the columns that had different masses of activated carbon. Note that this includes systems with different flow rates!
mylegend =[]
for i in range(np.size(filenames)):
  if (metadata['carbon (g)'][i] != 0):
    plt.plot(time_data[i]/HRT[i] - Tubing_HRT[i]/HRT[i], C_data[i]/C_0,'-');
    mylegend.append(str(ut.round_sf(metadata['carbon (g)'][i],3)) + ' g, ' + str(ut.round_sf(metadata['flow (mL/s)'][i],2)) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=100,left=0);
plt.ylabel(r'Normalized red dye concentration $\left ( \frac{mg}{L} \right )$');
plt.legend(mylegend);
plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Lab 6 - Adsorption/Images/Question 1b')
plt.show()

idx=np.zeros(np.size(C_data),int)
time=np.zeros(np.size(C_data),int)*u.s

for i in range(np.size(C_data)):
  idx[i] = (np.abs(C_data[i]-0.5*C_0)).argmin()
  time[i] = time_data[i][idx[i]]

t_mtz=time
t_mtz_dimless=time/HRT

mylegend = []
for i in range(np.size(filenames)):
    plt.plot(Dimless_time[i],Mass_carbon[i],'o');
    mylegend.append(str(metadata['flow (mL/s)'][i]) + ' mL/s')

plt.xlabel(r'$\frac{t}{\theta}$');
plt.xlim(right=500,left=0);
plt.ylabel(r'Mass of Carbon $\left (g) \right )$');
plt.legend(mylegend);
plt.savefig('C:/Users/Eirini Sarri/github/CEE4530/Lab 6 - Adsorption/Images/Question 2')
plt.show()

#Question 3

R_adsorption = t_mtz/t_water
R_adsorption
#Question 4
#We measured the bulk density in the lab
Density_bulk_AC = 386 * u.kg/u.m**3
V_carbon = (Mass_carbon/Density_bulk_AC).to(u.mL)


density_sand = 2650 * u.kg/u.m**3
M_sand = ((Column_V-V_carbon)*density_sand*(1-porosity)).to(u.g)

q_0 = ((R_adsorption-1)*(C_0*porosity*Column_V)/(Mass_carbon+M_sand)).to(u.dimensionless)
q_0

#Negative q explained by uncertainty in tubing material
```
