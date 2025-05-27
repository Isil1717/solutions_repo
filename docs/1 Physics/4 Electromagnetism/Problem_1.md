# Problem 1
# Electromagnetism: Lorentz Force — Theory and Simulation
##  Motivation

The **Lorentz force** governs how charged particles move under electric and magnetic fields. This concept is foundational in:

* **Plasma physics** (e.g., fusion reactors)
* **Particle accelerators** (e.g., cyclotrons)
* **Astrophysics** (e.g., solar winds, cosmic rays)
* **Mass spectrometry**

Simulating this force allows us to understand real-world applications and visualize intricate particle trajectories. This document explores applications, mathematical modeling, and numerical simulation of the Lorentz force using Python.

---

##  Fundamental Formula

The Lorentz force is the total electromagnetic force acting on a charged particle:

$$
\vec{F} = q\vec{E} + q\vec{v} \times \vec{B}
$$

Where:

* $\vec{F}$: Force (N)
* $q$: Charge (C)
* $\vec{E}$: Electric field (V/m)
* $\vec{v}$: Velocity (m/s)
* $\vec{B}$: Magnetic field (T)

The first term represents the electric force, and the second term is the magnetic force. If $\vec{E} = 0$, the motion is purely influenced by the magnetic field.

---

##  Applications of Lorentz Force

| System                         | Role of Lorentz Force                                      |
| ------------------------------ | ---------------------------------------------------------- |
| Particle Accelerators          | Provides centripetal force for circular particle motion    |
| Mass Spectrometers             | Differentiates ions by mass-to-charge ratio $\frac{m}{q}$  |
| Magnetic Traps (Penning Traps) | Confinement of charged particles in small regions          |
| Astrophysics                   | Affects charged particles in cosmic and solar environments |

These systems rely on our ability to control particle paths using electric and magnetic fields.

---

## Useful Derived Quantities

* **Larmor Radius**:

  $$
  r_L = \frac{mv_\perp}{qB}
  $$

  Describes the radius of circular motion perpendicular to a magnetic field.

* **Cyclotron Frequency**:

  $$
  \omega_c = \frac{qB}{m}
  $$

  The angular frequency of a particle's circular motion in a uniform magnetic field.

* **Drift Velocity in Crossed Fields**:

  $$
  \vec{v}_d = \frac{\vec{E} \times \vec{B}}{B^2}
  $$

  Indicates how particles drift when electric and magnetic fields are perpendicular.

---

##  Example 1: Circular Motion in a Magnetic Field

Let a particle have:

* $q = 1.6 \times 10^{-19} \ \mathrm{C}$
* $m = 9.1 \times 10^{-31} \ \mathrm{kg}$
* $\vec{v} = (1 \times 10^6, 0, 0) \ \mathrm{m/s}$
* $\vec{B} = (0, 0, 1) \ \mathrm{T}$

Then:

* Larmor radius:

  $$
  r_L = \frac{(9.1 \times 10^{-31}) (1 \times 10^6)}{(1.6 \times 10^{-19})(1)} \approx 5.7 \times 10^{-3} \ \mathrm{m}
  $$

* Cyclotron frequency:

  $$
  \omega_c = \frac{1.6 \times 10^{-19} \times 1}{9.1 \times 10^{-31}} \approx 1.76 \times 10^{11} \ \mathrm{rad/s}
  $$

The motion is circular in the plane perpendicular to the magnetic field, with radius $r_L$ and angular speed $\omega_c$.

---



---

##  Task 2: Crossed Electric and Magnetic Fields

For $\vec{E} \perp \vec{B}$, the charged particle experiences a steady drift:

$$
\vec{v}_d = \frac{\vec{E} \times \vec{B}}{B^2}
$$

The motion includes:

* **Cyclotron motion** about the field line
* **Superimposed drift** in the $\vec{E} \times \vec{B}$ direction

This phenomenon is exploited in devices like velocity selectors and magnetrons.

---

##  Task 3: Parameter Exploration (with Slider)

```python
import ipywidgets as widgets
from IPython.display import display

@widgets.interact(B_strength=(0.1, 5.0, 0.1))
def simulate(B_strength=1.0):
    q = 1.6e-19
    m = 9.1e-31
    E = np.array([0, 0, 0])
    B = np.array([0, 0, B_strength])
    v = np.array([1e6, 0, 1e6])
    r = np.array([0.0, 0.0, 0.0])

    dt = 1e-11
    steps = 1000
    traj = []

    for _ in range(steps):
        F = q * (E + np.cross(v, B))
        a = F / m
        v += a * dt
        r += v * dt
        traj.append(r.copy())

    traj = np.array(traj)
    plt.figure(figsize=(6,6))
    plt.plot(traj[:,0], traj[:,1])
    plt.title(f"Trajectory for B = {B_strength} T")
    plt.xlabel("x (m)")
    plt.ylabel("y (m)")
    plt.axis('equal')
    plt.grid()
    plt.show()
```

---

##  Task 4: 3D Helical Motion Visualization

```python
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

ax.plot(positions[:,0], positions[:,1], positions[:,2])
ax.set_title("3D Helical Motion in Magnetic Field")
ax.set_xlabel("x (m)")
ax.set_ylabel("y (m)")
ax.set_zlabel("z (m)")
plt.show()
```

---

##  Practical Implications

* **Cyclotrons** use uniform $\vec{B}$ to accelerate particles in circular orbits.
* **Plasma confinement** in tokamaks relies on helical paths and drift velocities.
* **Velocity selectors** use crossed $\vec{E}$ and $\vec{B}$ fields to isolate particles with specific speeds.

---

##  Conclusion

The Lorentz force provides a unified framework for understanding how electric and magnetic fields influence the motion of charged particles. Through analytical formulas, numerical simulations, and visualizations, we explored fundamental behaviors such as circular and helical trajectories, as well as drift in crossed fields. These concepts are not only critical in academic studies but are directly applied in advanced technologies like particle accelerators, plasma confinement devices, and astrophysical models.

By adjusting parameters and simulating trajectories in Colab, students gain an intuitive and visual understanding of electromagnetic forces. The concepts covered here form a solid foundation for more advanced topics like non-uniform fields, relativistic dynamics, and electromagnetic wave-particle interactions.

---
