# Problem 2
# 🌀 Investigating the Dynamics of a Forced Damped Pendulum

## 🔍 Motivation

The **forced damped pendulum** is a nonlinear system that shows a range of behaviors—resonance, quasiperiodicity, and even chaos. Studying its dynamics reveals how simple equations can lead to complex motion and provides insight into a variety of real-world systems:

- Driven mechanical structures
- Energy harvesters
- Oscillating circuits
- Climate models and biomechanical rhythms

---

## ⚙️ Governing Equation

The equation describing the pendulum's motion is:

$$
\frac{d^2\theta}{dt^2} + b \frac{d\theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
$$

Where:

- $ \theta(t) $ — angular displacement  
- $ b $ — damping coefficient  
- $ g $ — gravitational acceleration  
- $ L $ — pendulum length  
- $ A $ — driving force amplitude  
- $ \omega $ — driving frequency

---

## 🧠 Theoretical Foundation

### 🔹 Linear Approximation for Small Angles

For small angles, we can use the approximation:

$$
\sin(\theta) \approx \theta
$$

This simplifies the equation to:

$$
\frac{d^2\theta}{dt^2} + b \frac{d\theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

This is the **driven damped harmonic oscillator**, which has the general solution:

$$
\theta(t) = \theta_{\text{hom}}(t) + \theta_{\text{part}}(t)
$$

Where:

- $ \theta_{\text{hom}}(t) $ — transient (decaying) solution  
- $ \theta_{\text{part}}(t) $ — steady-state oscillation due to the external force

---

## 💻 Numerical Simulation (Nonlinear Case)

We now solve the full nonlinear system numerically.

```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt

def pendulum(t, y, b, g, L, A, omega):
    theta, omega_ = y
    dtheta_dt = omega_
    domega_dt = -b * omega_ - (g / L) * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Parameters
params = dict(b=0.5, g=9.81, L=1.0, A=1.2, omega=2.0)
y0 = [0.1, 0.0]
t_eval = np.linspace(0, 50, 1000)

sol = solve_ivp(pendulum, [0, 50], y0, t_eval=t_eval, args=tuple(params.values()))

plt.plot(sol.t, sol.y[0])
plt.title("Forced Damped Pendulum: θ(t)")
plt.xlabel("Time (s)")
plt.ylabel("θ (rad)")
plt.grid()
plt.show()
