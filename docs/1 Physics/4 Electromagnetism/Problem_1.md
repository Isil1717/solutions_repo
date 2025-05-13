# Problem 1

#  Lorentz Force Simulation in Electromagnetic Fields

##  Introduction

This project simulates the **motion of charged particles** under electric and magnetic fields, governed by the **Lorentz force**:

$$
\vec{F} = q\vec{E} + q(\vec{v} \times \vec{B})
$$

---

##  Objectives

- Simulate particle motion in uniform and crossed fields.
- Vary parameters like velocity, charge, mass, and field strengths.
- Visualize 2D/3D trajectories using Python.
- Analyze physical phenomena like the Larmor radius and drift velocity.

---

##  Simulation Code (Python)

Below is a simple Euler method simulation using NumPy and Matplotlib:

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1.6e-19       # Charge (Coulombs)
m = 9.11e-31      # Mass (kg)
E = np.array([0, 0, 0])           # Electric field (V/m)
B = np.array([0, 0, 1])           # Magnetic field (T)
v0 = np.array([1e6, 0, 1e6])      # Initial velocity (m/s)
x0 = np.array([0.0, 0.0, 0.0])    # Initial position (m)

# Time parameters
dt = 1e-11        # Time step (s)
t_max = 1e-7
steps = int(t_max / dt)

# Initialize arrays
x = np.zeros((steps, 3))
v = np.zeros((steps, 3))
x[0] = x0
v[0] = v0

# Euler method loop
for i in range(steps - 1):
    F = q * (E + np.cross(v[i], B))
    a = F / m
    v[i + 1] = v[i] + a * dt
    x[i + 1] = x[i] + v[i] * dt

# Plot 3D trajectory
fig = plt.figure(figsize=(10, 6))
ax = fig.add_subplot(111, projection='3d')
ax.plot(x[:, 0], x[:, 1], x[:, 2])
ax.set_xlabel('x (m)')
ax.set_ylabel('y (m)')
ax.set_zlabel('z (m)')
ax.set_title('Charged Particle Trajectory in Magnetic Field')
plt.tight_layout()
plt.show()
```

---

##  Observations

- If \( \vec{B} \) is present and \( \vec{E} = 0 \), particle moves in a **helix**.
- If both \( \vec{E} \) and \( \vec{B} \) are present and perpendicular, the particle **drifts**.
- Larmor radius:  
  $$
  r_L = \frac{mv_\perp}{qB}
  $$

---

##  Applications

| Application         | Description                                       |
|---------------------|---------------------------------------------------|
| Cyclotron           | Circular motion of particles under \( \vec{B} \) |
| Mass spectrometer   | Deflection by \( \vec{B} \) depends on \( m/q \) |
| Tokamak             | Plasma confinement using \( \vec{E} \times \vec{B} \) drift |
| Solar wind          | Deflected by Earth's magnetic field              |

---

##  Parameter Exploration

You can change:
- `q`, `m`: particle properties
- `E`, `B`: field vectors
- `v0`: initial velocity
- `dt`, `t_max`: simulation time resolution

---

##  Conclusion

This simulation demonstrates how charged particles behave in electric and magnetic fields, illustrating the effects of the Lorentz force through numerical methods. It shows:

- **Circular/Helical paths** under uniform magnetic fields
- **Linear acceleration** under electric fields
- **Drift motion** in crossed \( \vec{E} \) and \( \vec{B} \)

The approach is extensible to complex setups like:
- Non-uniform or time-varying fields
- Multi-particle systems
- Relativistic dynamics

Such simulations underpin real-world devices like **cyclotrons, magnetic mirrors, fusion reactors**, and **space plasma studies**.

---



