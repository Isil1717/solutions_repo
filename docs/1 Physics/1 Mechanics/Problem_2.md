# Problem 2
# Investigating the Dynamics of a Forced Damped Pendulum

## Introduction

The forced damped pendulum is a classic example of a non-linear oscillatory system. The system demonstrates a rich variety of behaviors, including resonance, chaos, and quasiperiodic motion, depending on the interplay between damping, restoring forces, and external driving forces. The dynamics of this system are governed by the second-order differential equation:

$$
\frac{d^2 \theta}{dt^2} + b \frac{d\theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
$$

Where:
- \( \theta(t) \) is the angular displacement,
- \( b \) is the damping coefficient,
- \( g \) is the gravitational acceleration,
- \( L \) is the length of the pendulum,
- \( A \) is the amplitude of the external driving force,
- \( \omega \) is the angular frequency of the external force.

---

## Small-Angle Approximation

For small oscillations, we use the approximation \( \sin(\theta) \approx \theta \), leading to a linearized form of the equation:

$$
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

This approximation simplifies the analysis, and the system behaves similarly to a driven damped harmonic oscillator. The natural frequency of the undamped system is:

$$
\omega_0 = \sqrt{\frac{g}{L}}
$$

At resonance, when the driving frequency \( \omega \) matches the natural frequency \( \omega_0 \), the amplitude of oscillations can increase dramatically. This condition is given by:

$$
\omega_{\text{res}} = \sqrt{\frac{g}{L}}
$$

---

## Numerical Simulation

To simulate the dynamics of the forced damped pendulum, we rewrite the second-order differential equation as a system of first-order equations:

Let:
- \( \theta_1 = \theta \),
- \( \theta_2 = \frac{d \theta}{dt} \).

The system becomes:

$$
\frac{d \theta_1}{dt} = \theta_2
$$

$$
\frac{d \theta_2}{dt} = -b \theta_2 - \frac{g}{L} \sin(\theta_1) + A \cos(\omega t)
$$

This system can be solved numerically using methods like the **Runge-Kutta** algorithm to obtain the time evolution of \( \theta_1(t) \) and \( \theta_2(t) \).

---

## Effects of Damping and Driving Forces

### Damping Coefficient \( b \)

The damping coefficient \( b \) controls the rate at which the oscillations decay. As \( b \) increases, the system loses energy more rapidly, causing the amplitude of oscillations to decrease. When \( b \) is large enough, the system eventually reaches a steady state with no oscillations.

For small damping \( b \), resonance phenomena occur, and the system can exhibit large oscillations if the driving frequency \( \omega \) is close to the natural frequency of the system.

The modified equation for damping is:

$$
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

### Driving Force Amplitude \( A \)

The amplitude of the driving force \( A \) determines how much energy is supplied to the system. As \( A \) increases, the amplitude of oscillations increases. If \( A \) is large enough and \( \omega \) is close to \( \omega_{\text{res}} \), the system enters a state of large amplitude oscillations, potentially leading to resonance.

### Driving Frequency \( \omega \)

The driving frequency \( \omega \) plays a crucial role in determining the behavior of the system. At resonance, when \( \omega = \omega_{\text{res}} \), the system's response is maximal, and the oscillations grow significantly. The system exhibits a peak in amplitude at this frequency.

For frequencies far from resonance, the oscillations have much smaller amplitudes.

---

## Chaos and Bifurcations

As the parameters \( A \) (driving amplitude) and \( \omega \) (driving frequency) are varied, the system can undergo bifurcations, where small changes in parameters lead to large changes in the system’s behavior. The bifurcation diagram can reveal transitions from periodic to chaotic motion.

In a bifurcation diagram, as \( A \) or \( \omega \) increases, the system may exhibit a sudden transition to chaotic behavior. This is due to sensitive dependence on initial conditions, a hallmark of chaos.

---

## Lyapunov Exponent

The **Lyapunov exponent** measures the rate at which nearby trajectories in phase space diverge, and is a key indicator of chaos. A positive Lyapunov exponent indicates chaotic behavior, while a negative value suggests stable periodic motion. It is defined as:

$$
\lambda = \lim_{t \to \infty} \frac{1}{t} \ln \left( \frac{|\delta(t)|}{|\delta(0)|} \right)
$$

Where:
- \( \delta(t) \) is the separation between two nearby trajectories at time \( t \),
- \( \delta(0) \) is the initial separation.

A positive Lyapunov exponent means that the system is chaotic and exhibits exponential divergence of nearby trajectories.

---

## Conclusion

The dynamics of the forced damped pendulum provide a rich example of nonlinear behavior, including resonance, chaos, and periodic motion. By varying the damping coefficient, driving amplitude, and driving frequency, we observe a variety of dynamic responses, from stable oscillations to chaotic motion.

Numerical simulations and analytical techniques such as the Lyapunov exponent and bifurcation diagrams allow for a deeper understanding of these behaviors, with applications in engineering, biomechanics, and electronics.





 