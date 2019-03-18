#**Lab Fire Adsorption Prelab**
###Eirini Sarri & Felix Yang
March 20, 2019

1. A carbon column is packed with $15$ cm of activated carbon and then used to remove $50 \frac{mg}{L}$ of red dye #40. The approach velocity is $1 \frac{mm}{s}$, the porosity is $0.4$, and the bulk density of the activated carbon is $0.5 \frac{g}{cm^{3}}$. How long will it take for the mass transfer zone to travel to the bottom of the carbon column?

The time required for the mass transfer zone to travel to the bottom of the carbon column is calculated below. First the retardation factor is found. Then, the relationship between $R_{adsorption}$, $t_{mtz}$, and $t_{water}$ was used to find $t_{mtz}$, which was determined to be 2000 minutes or 33.3 hours. 

$R_{adsorption}\cong  \frac{v_a q_0 \rho_{bulk \; adsorbent}}{\phi v_a C_0} =\frac{q_0 \rho_{bulk \; adsorbent}}{\phi C_0}$

$R_{adsorption} = \frac{t_{mtz}}{t_{water}} = \frac{v_{water}}{v_{mtz}}$

$t_{mtz}=R_{adsorption}t_{water}=2000$ minutes


```python
from aguaclara.core.units import unit_registry as u
from aide_design.play import *

v_a = 1 * u.mm/u.s
porosity = 0.4
L_column = 15 * u.cm
C_0 = 50 * u.mg/u.L
Density_bulk = 0.5 * u.g/(u.cm**3)
q = 0.08

R_adsorption = q * Density_bulk / (porosity*C_0)
R_adsorption
t_water = (L_column*porosity/v_a).to(u.s)
t_mtz = R_adsorption * t_water

t_mtz_hours=t_mtz.to(u.hours)
t_mtz_minutes=t_mtz.to(u.minutes)
t_mtz_hours
t_mtz_minutes
