#**Lab Fire Adsorption Prelab**
###Eirini Sarri & Felix Yang
March 20, 2019

1. A carbon column is packed with $15$ cm of activated carbon and then used to remove $50 \frac{mg}{L}$ of red dye #40. The approach velocity is $1 \frac{mm}{s}$, the porosity is $0.4$, and the bulk density of the activated carbon is $0.5 \frac{g}{cm^{3}}$. How long will it take for the mass transfer zone to travel to the bottom of the carbon column?



```python
from aguaclara.core.units import unit_registry as u
from aide_design.play import *

v_a = 1 * u.mm/u.s
porosity = 0.4
L_column = 15 * u.cm
C_0 = 50 * u.mg/u.L
Density_bulk = 0.5 * u.g/(u.cm**3)
R_adsorption = 1

t_water = (L_column*porosity/v_a).to(u.s)
t_mtz = R_adsorption * t_water

t_mtz
