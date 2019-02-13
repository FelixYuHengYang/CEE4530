# Acid Neutralizing Capacity Prelab
##Labfire - Felix Yang and Eirini Sarri

1. Compare the ability of Cayuga lake and Wolf pond (an Adirondack lake) to withstand an acid rain runoff event (from snow melt) that results in 20% of the original lake water being replaced by acid rain. The acid rain has a pH of 3.5 and is in equilibrium with the atmosphere. The ANC of Cayuga lake is 1.6 meq/L and the ANC of Wolf Pond is 70 μeq/L. Assume that carbonate species are the primary component of ANC in both lakes, and that they are in equilibrium with the atmosphere. What is the pH of both bodies of water after the acid rain input? Remember that ANC is the conservative parameter (not pH!). Hint: You can use the scipy optimize root finding function called brentq. Scipy can’t handle units so the units must be removed using .magnitude.}

The pH of Cayuga lake and Wolf Lake after acid rain input is 8.44 and 5.11 respectively. See python code below for calculations.

2. What is the ANC of a water sample containing only carbonates and a strong acid that is at pH 3.2? This requires that you inspect all of the species in the ANC equation (Equation (33)) and determine which species are important.

Since pH=3.2 where pH is significantly smaller than $pK_1$, then the ANC formula simplifies so that the [H+] variable dominates the value of ANC. So $ANC=-[H+]=-10^{-3.2}=-0.00063 \frac{equivalents}{L}$

3. Why is [H+] not a conserved species?

[H+] is not a conserved species because when it is added to a solution it has two possible fates, one being a free cation in solution which lowers the pH, in which it is a conserved species, and the other binding to existing anions in solution such as $CO_3^{2-}$ and $HCO_3^-$. The pH does not change when H+ binds to anions. In most real life cases there are often anions for H+ to bind to, therefore H+ is not a conserved species. 

```python
from aguaclara.core.units import unit_registry as u
u.define('equivalent = mole = eq')
import aguaclara.research.environmental_processes_analysis as epa
from scipy import optimize

def ANC_zeroed(pHguess, ANC):
  return ((epa.ANC_open(pHguess) - ANC).to(u.mol/u.L)).magnitude
# Now we use root finding to find the pH that results in the known ANC.
# Our function will call the ANC_zeroed function. The pHguess is the first
# input of the ANC_zeroed function and the range on that is set by the next
# two inputs in the optimize.brentq function. The ANC is passed as an
# additional argument.

def pH_open(ANC):
  return optimize.brentq(ANC_zeroed, 0, 14,args=(ANC))

# We can test this function to find the pH of pure water in equilibrium
# with the atmosphere
print('The pH of pure water equilibrium with the atmosphere is',pH_open(0))

pH=3.5 #Initial acid rain pH assumption
ANC_Cayuga=1.6*10**-3*u.equivalent/u.L #Given
ANC_Wolf=70*10**-6*u.equivalent/u.L #Given
ANC_in=-10**-pH*u.equivalent/u.L
ANC_out_Cayuga=.2*ANC_in+.8*ANC_Cayuga
ANC_out_Wolf=.2*ANC_in+.8*ANC_Wolf
ANC_out_Cayuga
ANC_Wolf

pH_open(ANC_out_Cayuga)
pH_open(ANC_Cayuga)

pH_open(ANC_out_Wolf)
pH_open(ANC_Wolf)

ANC_onlycarbonates=-10**-3.2*u.equivalents/u.L
ANC_onlycarbonates
```
