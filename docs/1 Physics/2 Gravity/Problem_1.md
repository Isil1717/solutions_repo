# Problem 1
# 🌌 Gravity – Problem 1: Orbital Period and Orbital Radius

## 🧠 Motivation

The relationship between the **square of the orbital period** and the **cube of the orbital radius**—known as **Kepler's Third Law**—is foundational in celestial mechanics:

> $$ T^2 \propto r^3 $$

This principle is used to compute satellite orbits, planetary distances, and star systems.

---

## 🧪 1. Theoretical Foundation

In a circular orbit, the gravitational force provides the centripetal force:

$$
\frac{G M m}{r^2} = \frac{m v^2}{r}
$$

Solving for orbital speed \( v \):

$$
v = \sqrt{\frac{G M}{r}}
$$

Since orbital period is \( T = \frac{2\pi r}{v} \):

$$
T = 2\pi \sqrt{\frac{r^3}{G M}} \Rightarrow T^2 = \left( \frac{4\pi^2}{G M} \right) r^3
$$

---

## 🧮 2. Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant (m^3/kg/s^2)
M = 5.972e24     # Mass of the Earth (kg)

# Orbital radii (meters)
radii = np.linspace(7e6, 4.2e7, 100)  # from LEO to GEO
T = 2 * np.pi * np.sqrt(radii**3 / (G * M))  # Orbital periods (seconds)

# Kepler's Law: Plot T^2 vs r^3
T_squared = T**2
r_cubed = radii**3

plt.figure(figsize=(8,6))
plt.plot(r_cubed, T_squared, color='royalblue')
plt.title("Verification of Kepler's Third Law")
plt.xlabel("Orbital Radius³ (m³)")
plt.ylabel("Orbital Period² (s²)")
plt.grid(True)
plt.tight_layout()
plt.show()
📊 3. Graphical Output
The graph should show a perfectly linear relationship between 
𝑟
3
r 
3
  and 
𝑇
2
T 
2
 , confirming Kepler’s Law for circular orbits.

🌍 4. Real-World Examples
🌕 Moon around Earth:
𝑟
≈
3.84
×
10
8
 
m
r≈3.84×10 
8
 m

𝑇
≈
27.3
 
days
T≈27.3days

🛰️ Geostationary Satellite:
𝑟
≈
4.2
×
10
7
 
m
r≈4.2×10 
7
 m

𝑇
≈
24
 
hours
T≈24hours

🌠 5. Extension to Elliptical Orbits
Kepler's Third Law also applies to elliptical orbits by replacing 
𝑟
r with the semi-major axis 
𝑎
a:

𝑇
2
∝
𝑎
3
T 
2
 ∝a 
3
 
This law is universally valid—from planets and moons to exoplanets and binary star systems—offering deep insights into the structure of the universe.
