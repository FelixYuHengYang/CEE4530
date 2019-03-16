#**Lab Fire Reactors Prelab**
###Eirini Sarri & Felix Yang
March 6, 2019

1. Calculate the change in hydraulic grade line between baffled sections of a reactor with a flow rate of 380 mL/min. The reactor baffles are perforated with 6 holes 1 mm in diameter. Is the flow through these orifices in series or in parallel? Do you multiply the head loss for one orifice by the number of orifices to get the total head loss? Are the orifices in parallel or in series? Use the pc.head_orifice function to calculate the head loss through an orifice. The vena contracta for the orifice can be found at aguaclara.core.constants.VC_ORIFICE_RATIO. Why would 6 holes 1 mm in diameter not be a good design for this reactor?

The change in hydraulic grade line with these parameters will be $.23 m$. To get the total head loss you find the headloss for a single orifice that takes a fraction of the full flow rate of 380 mL/min. The flow through the orifices is in parallel as the orifices of the baffles are collectively hitting the water at more or less the same time. If it were in series it would be passing through at different times, dissipating energy one after another. 6 holes, 1 mm in diameter would not be a good design for this reactor because the headloss through the system is very substantial to the point where water may backed up and overflow the reactor.

2. On a single graph plot the exit age distribution (E(t⋆)) for a reactor that operates as a 1-dimensional advection-dispersion reactor with Peclet numbers of 1, 10, and 100 (there will be three plots on the graph and thus a legend is required). The x-axis should be t⋆ from 0.0 to 3.0. Comment on the shapes of the curves as a function of the Peclet number. Note that the advective dispersion equation is undefined for t⋆=0. Use the epa.E_Advective_Dispersion(t,Pe) function.

Graph can be found by running the code below. As Peclet number increases, the curve becomes less skewed. With increasing Peclet number, we get a decrease in dispersion and the behavior of the system matches more that of a Plug Flow Reactor.

<p align="center">
  <img src="https://raw.githubusercontent.com/FelixYuHengYang/CEE4530/master/prelabs/Reactors_Question_2.png" alt="Exit age Distrubtion"/>
</p>



```python
from aguaclara.core.units import unit_registry as u
import aguaclara.core.materials as mat
import aguaclara.core.constants as con
import aguaclara.core.utility as ut
import aguaclara.core.physchem as pc
import aguaclara.research.environmental_processes_analysis as epa
import matplotlib.pyplot as plt
import numpy as np
from scipy import interpolate, integrate

Aorifice = pc.area_circle(0.001*u.m)
Korifice = con.VC_ORIFICE_RATIO
Q_flow=(380*u.mL/u.min).to(u.m**3/u.s)
numorifice=6
Q_flow_orifice=Q_flow/numorifice
g = 9.81*u.m/u.sec**2
Deltah = pc.head_orifice(0.001,Korifice,Q_flow_orifice)
Deltah

#Pe = 1
t_dim_= np.arange(0.01,3,0.01)
Pe_1 = 1
E_1=epa.E_Advective_Dispersion(np.arange(0.01,3,0.01), Pe_1)

#Pe = 10
Pe_10 = 10
E_2=epa.E_Advective_Dispersion(np.arange(0.01,3,0.01), Pe_10)

#Pe = 100
Pe_100 = 100
E_3=epa.E_Advective_Dispersion(np.arange(0.01,3,0.01), Pe_100)

fig, ax = plt.subplots()
plt.xlabel('t*')
plt.ylabel('E(t*)')
ax.plot(np.arange(0.01,3,0.01),E_1,'r', label='Pe = 1')
ax.plot(np.arange(0.01,3,0.01),E_2,'y', label='Pe = 10')
ax.plot(np.arange(0.01,3,0.01),E_3,'c', label='Pe = 100')
ax.legend()
plt.savefig('C:/Users/Felix/Documents/Github/CEE4530/prelabs/Question_2')
plt.show()
