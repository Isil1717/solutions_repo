# 🌌 Kepler’s Third Law: Orbital Period and Radius Simulation with Python

---

## 📘 Introduction

Johannes Kepler’s Third Law is a fundamental principle in celestial mechanics. It describes the relationship between the orbital period and the radius of a body orbiting a central mass in a circular orbit.

**Kepler’s Third Law (for circular orbits):**

$$
T^2 = \frac{4 \pi^2 r^3}{G M}
$$

Where:

- \( T \): Orbital period (seconds)  
- \( r \): Orbital radius (meters)  
- \( G \): Universal gravitational constant \( (6.67430 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}) \)  
- \( M \): Mass of the central body (e.g., Earth) in kilograms

This equation shows:

$$
T^2 \propto r^3
$$

This elegant yet powerful relationship allows us to analyze planetary systems, satellites, star systems, and even galaxies.

---

## 🎯 Objective

- Numerically verify Kepler’s Third Law  
- Calculate orbital periods for various radii using Python  
- Visualize the linear relationship between \( T^2 \) and \( r^3 \)  
- Discuss real-world examples (e.g., Earth-Moon system)

---

## 🧠 Theoretical Background

The gravitational force equals the centripetal force for circular motion:

$$
\frac{G M m}{r^2} = \frac{m v^2}{r}
$$

Solving for orbital speed \( v \):

$$
v = \sqrt{\frac{G M}{r}}
$$

Orbital period:

$$
T = \frac{2\pi r}{v}
$$

Substitute \( v \):

$$
T = 2\pi \sqrt{\frac{r^3}{G M}} \Rightarrow T^2 = \frac{4\pi^2 r^3}{G M}
$$

---

## 💻 Python Implementation

Let’s verify this relationship numerically.

### 📦 Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
🌍 Physical Constants
G = 6.67430e-11        # Gravitational constant (m^3 kg^-1 s^-2)
M = 5.972e24           # Mass of Earth (kg)

📐 Radius and Period Calculations
radii = np.linspace(1e7, 5e8, 200)  # From 10,000 km to 500,000 km
periods = 2 * np.pi * np.sqrt(radii**3 / (G * M))

📈 Plot: 
𝑇
2
T 
2
  vs 
𝑟
3
r 
3
 
python

plt.figure(figsize=(10, 6))
plt.plot(radii**3, periods**2, label=r"$T^2$ vs $r^3$", color="blue")
plt.xlabel("Orbital Radius Cubed $r^3$ (m³)")
plt.ylabel("Orbital Period Squared $T^2$ (s²)")
plt.title("Kepler's Third Law Verification")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

🌍 Real-World Example: The Moon’s Orbit
Distance from Earth:
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

Orbital period:
𝑇
≈
27.3
 
days
=
2.36
×
10
6
 
seconds
T≈27.3days=2.36×10 
6
 seconds

This can be used to reverse-calculate the mass of Earth using Kepler’s Law.

📌 Extension to Elliptical Orbits
Circular orbits are a special case. For elliptical orbits, Kepler’s Third Law generalizes to:

𝑇
2
=
4
𝜋
2
𝑎
3
𝐺
(
𝑀
+
𝑚
)
T 
2
 = 
G(M+m)
4π 
2
 a 
3
 
​
 
Here, 
𝑎
a is the semi-major axis. If the orbiting body is much smaller than the central body, 
𝑀
+
𝑚
≈
𝑀
M+m≈M.

✅ Conclusion
The relationship 
𝑇
2
∝
𝑟
3
T 
2
 ∝r 
3
  has been confirmed numerically

The graph shows a clear linear trend between 
𝑇
2
T 
2
  and 
𝑟
3
r 
3
 

Kepler’s Law is critical in mass and distance calculations in astronomy

This principle enables accurate modeling of satellites, planetary systems, and galaxies

https://colab.research.google.com/drive/1vRSkWuLrWI9SwNMovPSkJw4wr2AKpbz4?authuser=0#scrollTo=hj0QrGlqrL3B
