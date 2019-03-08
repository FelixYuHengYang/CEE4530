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


# Plot the raw data
for i in range(airflows.size):
  plt.plot(time_data[i], DO_data[i],'-')

for i in range(5):
  plt.plot(time_data[i], DO_data[i],'-')
plt.xlabel(r'$time (s)$')
plt.ylabel(r'Oxygen concentration $\left ( \frac{mg}{L} \right )$')
plt.legend(airflows.magnitude)
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab 4 - Gas Transfer/Images/Question_2')
plt.show()

#delete data that is less than 2 or greater than 6 mg/L
DO_min = 2 * u.mg/u.L
DO_max = 6 * u.mg/u.L
for i in range(airflows.size):
  idx_start = (np.abs(DO_data[i]-DO_min)).argmin()
  idx_end = (np.abs(DO_data[i]-DO_max)).argmin()
  time_data[i] = time_data[i][idx_start:idx_end] - time_data[i][idx_start]
  DO_data[i] = DO_data[i][idx_start:idx_end]
  Accumulator_P[i] = Accumulator_P[i][idx_start:idx_end]


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


# Conclusions
