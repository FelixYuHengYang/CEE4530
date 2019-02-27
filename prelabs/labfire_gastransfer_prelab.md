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
