#**Lab Fire Gas Transfer Prelab**
###Eirini Sarri & Felix Yang
Feburary 19th, 2018
1. Calculate the mass of sodium sulfite needed to reduce all the dissolved oxygen in 750 mL of pure water in equilibrium with the atmosphere and at 22∘C.

Volume = 0.75 L

Density (at 22∘C) = 8.894 mg/L

Mass = 6.67 mg

From the textbook:

$\frac{{mole\; O}_{{2}} }{{32000\; mg\; O}_{{2}} } \cdot \frac{{2\; mole\; Na}_{{2}} {SO}_{{3}} }{{mole\; O}_{{2}} } \cdot \frac{{126,000\; mg\; Na}_{{2}} {SO}_{{3}} }{{mole\; Na}_{{2}} {SO}_{{3}} } =\frac{{\; 7.875\; mg\; Na}_{{2}} {SO}_{{3}} }{{mg\; O}_{{2}} }$ (1)

Therefore, for 6.67 mg of $O_{2}$, we would need $\frac{{6.67 \;mg \;O_2*\; 7.875\; mg\; Na}_{{2}} {SO}_{{3}} }{{mg\; O}_{{2}} }=52.53\;mg\; Na_{2}SO_{3{}}$ (2)

The math done above was also calculated in the python code below the questions.

2. Describe your expectations for dissolved oxygen concentration as a function of time during a reaeration experiment. Assume you have added enough sodium sulfite to consume all of the oxygen at the start of the experiment. What would the shape of the curve look like?

If Labfire had added enough sodium sulfite to consume all of the oxygen at the start of the experiment, the shape of the dissolved oxygen concentration as a function of time during the reaeration experiment would be a curve that initially appears linear and then approaches the asymptote at the saturated dissolved oxygen concentration. The saturated dissolved oxygen concentration is dependent on partial pressure and temperature of the water.

3. Why is k^v,l not zero when the gas flow rate is zero? How can oxygen transfer into the reactor even when no air is pumped into the diffuser?

$K_{v,l}$ is not 0 even when the gas flow rate is 0 because the system is open to the atmosphere, allowing oxygen exchange with its surroundings. In other words, it can be in chemical equilibrium with the atmosphere where there is a net transfer of 0 but there is still exchange of oxygen molecules.

4. Describe your expectations for k^v,l as a function of gas flow rate. Do you expect a straight line? Why?

Assuming that the OTE is constant as gas flow rate increases, in order to counterbalance the increase in $Q_{air}$ the $k_{v,l}$ increases linearly with it. It is expected to be a straight line because both variables are raised to the first power.

5. A dissolved oxygen probe was placed in a small vial in such a way that the vial was sealed. The water in the vial was sterile. Over a period of several hours the dissolved oxygen concentration gradually decreased to zero. Why? (You need to know how dissolved oxygen probes work!)

The dissolved oxygen probe measures the current that is proportional to the rate at which oxygen molecules are reacting with the electrons provided by the cathode to reduce oxygen to $H_2O$. If we let the probe operate for long periods of time, the voltage difference will drop to zero, preventing the conversion of $O_2$ to $H_2O$ and thus increasing the concentration of $O_2$ within the probe. This will lead to the generation of an equilibrium between the probe and the cell, thus preventing the transfer of oxygen into the probe and leading to a displayed oxygen concentration of zero.


```python
""" importing """
import aguaclara.research.environmental_processes_analysis as epa
from aguaclara.core.units import unit_registry as u
import matplotlib.pyplot as plt
import numpy as np
# the code below will eventually be in the AguaClara core and should be called directly
def O2_sat(P_air, temp):
  """This equation returns saturated oxygen concentration in mg/L. It is valid
  for 278 K < T < 318 K
  Parameters
  ----------
  Pressure_air : float
      air pressure with appropriate units.
  Temperature :
      water temperature with appropriate units
  Returns
  -------
  Saturated oxygen concentration in mg/L
  Examples
  --------
  >>> O2_sat(1*u.atm , 300*u.kelvin)
  8.093157231428425 milligram/liter
  """
  fraction_O2 = 0.21
  P_O2 = P_air * fraction_O2
  return ((P_O2.to(u.atm).magnitude) *
          u.mg/u.L*np.exp(1727 / temp.to(u.K).magnitude - 2.105))

P_air = 101.3*u.kPa
temp = np.linspace(0,40)*u.degC
C_Oxygen = epa.O2_sat(P_air,temp)

fig, ax = plt.subplots()
ax.plot(temp,C_Oxygen)
ax.set(xlabel='Temperature (degrees Celsius)', ylabel='Oxygen concentration (mg/L)')
fig.savefig('Gas_Transfer/Images/Oxygen_vs_T')
plt.show()
