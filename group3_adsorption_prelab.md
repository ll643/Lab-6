### Lynn Li (ll643) and Allison Tran (ant42)
### Group 3
### Due 03/22/2019
# Adsorption Prelab

# Question 1: A carbon column is packed with 15 cm of activated carbon and then used to remove 50 mg/L of red dye #40. The approach velocity is 1 mm/s, the porosity is 0.4, and the bulk density of the activated carbon is 0.5 g/cm3. How long will it take for the mass transfer zone to travel to the bottom of the carbon column?

```python
import aguaclara
import os
from pathlib import Path
from aguaclara.core.units import unit_registry as u
import aguaclara.core.physchem as pc
u.define('equivalent = mole = eq')
import aguaclara.research.environmental_processes_analysis as epa
from aguaclara.core import utility as ut

velocity = 1*(u.mm/u.s)
porosity = 0.4
carbon_column = 15 * u.cm
C_0 = (50 * u.mg/u.L).to(u.g/u.L)
q_0 = 0.08
t_water = (carbon_column*porosity/velocity).to(u.s)
Density_bulk = (0.5*(u.g/u.cm**3)).to(u.g/u.L)
R_adsorption = (Density_bulk*q_0)/(porosity*C_0)
t_mtz = (R_adsorption*t_water).to(u.hour)

print('The time it take for the mass transfer zone to travel to the bottom of the carbon column is',ut.round_sf(t_mtz,3),'.')
```
