

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
```
Full lab reports (+)
Write the laboratory report as if the experiment were your idea. Imagine that you are working for a consulting firm or in a research laboratory and that you needed to do laboratory research to investigate options for areal world project. You can use the Lab Manual as an example of a well formatted WORD document. The Atom reports should have similar formatting with the required python code. Full laboratory reports should include the following sections:

#Introduction and Objectives
In the past, the United States had serious air quality issues, especially with acid rain caused by the combustion of fossil fuels that produce sulfric and nitric acid in the atmosphere. The biggest consequence of acid rain is the acidification of lakes that do not have acid neutralizing capacity (ANC) in their soils to mitigate acid rains. Today, there is a huge problem with acid rain in Asian cities such as Beijing and New Delhi due to their rapid industrial growth. The team decided to do this experiment with the goal of learning a practical method of remediating the effects of acid rain on lakes by using the addition of ANC. This also provides the first opportunity to code pH, ANC equations, and reactors equations as shown below.  

Acidity is principally measured using pH which measures the negative log of concentration of hydrogen ions as described in equation 1. Healthy lakes are typically in the pH range of 6.5 to 8.5, controlling the pH via the carbonate system. This system has the following components: dissolved carbon dioxide, carbonic acid, bicarbonate, and carbonate. Equation 2 describes the molar concentration of the carbonate system but omits dissolved carbon dioxide because it exists at very low levels in aqueous systems.  

$pH=-log{H^+}$ (1)

$C_T=[H_2CO_3]+[HCO_3^-]+[CO_3^{-2}]$ (2)

The carbonate system can be modeled as a "volatile" or "non-volatile" system. This depends on whether or not aqueous carbon dioxide is at equilibrium with atmospheric carbon dioxide. The equations for ANC are given for the volatile and non-volatile systems in (3) and (4) respectively.


$ANC=\frac{P_{CO_{2} } K_{H} }{a_{0} } (\alpha _{1}+2\alpha _{2})+\frac{K_{w} }{\left[{H}^{+} \right]} \; -\left[{H}^{+} \right]+\left[{A}_{{org}}^{{-}} \right]$  (3)

Where $C_T = \frac{P_{CO_2} K_H}{\alpha_0}$

$ANC=C_T(\alpha_1+2\alpha_2)+\frac{K_w}{H+}-[H+]+\left[{A}_{{org}}^{{-}} \right]$                     (4)

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
Present results in a clearly labeled format. Data analysis methods, equations, graphs, and tables should be presented in this section. The report text should refer to each equation, figure, and table. Include a table of relevant experimental parameters (e.g., measured flow rates, sample sizes, concentrations of reagents, etc.).

Compare theoretical expectations with your results and discuss reasons for any observed deviations. If the results weren't as expected, suggest reasons why the laboratory results may have differed from theory and suggest improved techniques to obtain more accurate results or modifications to the theory to better describe the experimental conditions.

Make sure that responses to specific questions and data analysis requested in the lab manual are included in this section. But don't answer the questions in a list format. Instead, include your answers as part of the narrative that is designed to meet your objectives.


#Conclusions
The conclusions section should not include any new observation. It is the place to summarize the results in a few sentences. Make sure you connect your conclusions to your objectives for doing the research.
