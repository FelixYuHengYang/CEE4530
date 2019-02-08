Used for the Fundamentals lab.
Submit both the data sheet and the atom analysis file
Use units on all numbers to help improve self documentation.
Do all calculations with units in Atom.
Designate an area in the atom markdown sheet where all the constants are entered. Name the constants.
Use equations to logically show dependency. Don't type in numbers that should be calculated values..
All laboratory reports (all 3 flavors!) must include conclusions, suggestions/comments and well done graphs!

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!


See attached spreadsheet.

2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.

See below in code.

3. What is the value of the extinction coefficient, ε?

5.21e+04 $\frac{L}{cm*mole}$ See calculations in atom code.

4. Did you use interpolation or extrapolation to get the concentration of the unknown?

We used interpolation because the absorbance value of the unknown was calculated to be within the range of already measured absorbance values. Therefore we needed to interpolate to estimate the unknown concentration.

5. What measurement controls the accuracy of the density measurement for the NaCl solution?

The measurement of the volume of the solution using the volumentric flask controls the accuracy of the density because the scales in the lab are more accurate than the flasks. In other words the least accurate measurement tool we used was the volumetric flasks.

6. What density did you expect (see prelab 2)?


We expected a density of 1038.82 $\frac{kg}{m^3}$.

7. Approximately what should the accuracy be for the density 8. measurement?
Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.

In conclusion, this experiment explored the concept of absorbance of light in relation to increasing concentration of a solute. The results showed that absorbance increases linearly with concentration up
to a maximum after which the equipment cannot accurately detect absorbance values (approximately above 3 absorbance units which corresponds with concentration with 100 and 200 mg/L). However, the values that were accurately measured by the sensor showed the linear trend and allowed us to determine an extinction coefficient of approximately $5*10^4 \frac{L}{cm*mole}$ .
A suggestion that might make this experiment more accurate would be to use a more opaque type of tubing so that light from other sources (lights in classroom, the sun, etc.) doesn’t enter the sensor system. The experiment that was conducted to measure the density of NaCl could be improved by using a scale which is closed all around so that movement around the scale does not influence the value
shown, as with the current setup the value kept fluctuating for a long time. Lastly, there was an issue where air bubbles would enter the tubing, which influenced the measured absorbance values.

9. Verify that your report and graphs meet the requirements as outlined on the course website.



```python

from aguaclara.core.units import unit_registry as u
from aide_design.play import*
from aide_design.physchem import*
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
from math import*


data_file_path= "https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/Lab1_Fundamentals/Lab%201%20data%202_7_2018.txt"
#Constants
V_dark=-1.307*u.V
b=0.6*u.cm #length that the light travels through solution ie the diameter of the tubing
Water_Temp=21.2*u.degC
Density_Water=density_water(21.2*u.degC) #997.95
  #2 Create a graph. First import the dataset.
df = pd.read_csv(data_file_path,delimiter='\t')
list(df)
columns = df.columns
x = df.iloc[:,4].values * u.mg/u.L #Concentration
y = (df.iloc[:,3].values)  #Absorbance has no units
slope, intercept, r_value, p_value, std_err = stats.linregress(x,y)
intercept
slope = slope * 1/x.units
slope
fig, ax = plt.subplots()
# plot the data as red circles
ax.plot(x, y, 'ro', )

  #plot the linear regression as a black line
ax.plot(x, slope * x + intercept, 'k-', )

  # Add axis labels using the column labels from the dataframe
ax.set(xlabel='Concentration (mg/L)')
ax.set(ylabel='Absorbance')
ax.legend(['Measured', 'Linear regression'])
ax.grid(True)
  # Here I save the file to my local harddrive. You will need to change this to work on your computer.
  # We don't need the file type (png) here.
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/Lab1_Fundamentals/images/')
plt.show()
#3 Calculate Extinction values for concentrations 0.01 to 0.5 mg/L
x_unitless = df.iloc[1:7,4].values

b_unitless=.6
x_convert=x_unitless*(1)/(496.416)*(1)/(1000)
x_convert
y_convert=df.iloc[1:7,3].values
y_convert
Extinction=y_convert/(b_unitless*x_convert)
Extinction_units=Extinction*u.L/(u.mole*u.cm)
Extinction_units
E=np.mean(Extinction_units) #Our number that we calculated for question 3


#def extinction(Absorbance,b,concentration): this function failed but will keep it here
  #ex=[]
  #i=0
  #for i in range(0,len(concentration)-1):
  #  ex[i]=Absorbance[i]/(b*concentration[i])

  #return[ex]
#extinction(y,b,x_convert)
```
