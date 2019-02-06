Used for the Fundamentals lab.
Submit both the data sheet and the atom analysis file
Use units on all numbers to help improve self documentation.
Do all calculations with units in Atom.
Designate an area in the atom markdown sheet where all the constants are entered. Name the constants.
Use equations to logically show dependency. Don't type in numbers that should be calculated values..
All laboratory reports (all 3 flavors!) must include conclusions, suggestions/comments and well done graphs!

1. Fill out the attached spreadsheet. Make sure that all calculated values are entered in the spreadsheet as equations. All remaining analysis for the course will be done in Atom using Python!
2. Create a graph of absorbance vs. concentration of red dye \#40 in Atom/Markdown using the exported data file. Does absorbance increase linearly with concentration of the red dye? Remove data points from the graph that are outside of the linear region.
3. What is the value of the extinction coefficient, ε?
4. Did you use interpolation or extrapolation to get the concentration of the unknown?
5. What measurement controls the accuracy of the density measurement for the NaCl solution?
6. What density did you expect (see prelab 2)?
7. Approximately what should the accuracy be for the density 8. measurement?
Don’t forget to write a brief paragraph on conclusions and on suggestions using Markdown.
9. Verify that your report and graphs meet the requirements as outlined on the course website.



```python

from aguaclara.core.units import unit_registry as u
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from scipy import stats
from math import*

  data_file_path= "https://github.com/FelixYuHengYang/CEE4530/blob/master/Lab1_Fundamentals/Lab%201%20-%20es859_fyy2.csv"
