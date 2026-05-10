# QFP Quantum Flux Parametron

A Quantum Flux Parametron (QFP) is a type of ultra-fast, energy-efficient digital logic device that relies on Josephson junctions (JJ). Despite the name, it is a classical computing technology that uses quantum mechanical effects to function. It is Deterministic: A QFP processes bits ($0$ or $1$) in a standard, deterministic way similar to conventional computer chips. It does not use qubits, superposition, or entanglement.

The device stores information (a 0 or a 1) as a single quantum of magnetic flux trapped within a superconducting loop. The "Parametron" name comes from an older invention called the "parametron," which used parametric oscillation to maintain a stable state. The QFP adapts this principle, using superconducting loops to provide much higher speeds and lower energy usage than traditional semiconductor-based transistors.

The QFP is functionally and structurally an rf SQUID.

* DC SQUIDs utilize two Josephson junctions in a parallel configuration and are typically biased with a constant DC current to produce a voltage output that oscillates with changes in magnetic flux.

* RF SQUIDs utilize a single Josephson junction (or in the case of a QFP, a specific arrangement of junctions) in a loop and are typically driven by an AC (radio-frequency) flux bias. The QFP operates in this "rf" mode, where an AC activation signal periodically "tips" the potential energy landscape of the loop to force it into one of two stable, binary states.

While a classic, textbook rf SQUID contains exactly one Josephson junction, the standard QFP circuit typically contains two Josephson junctions.

This two-junction architecture is used to create a more robust and controllable "double-well" potential, which allows the device to act as a stable logic gate (like a buffer or a majority gate) rather than just a sensitive flux sensor.

the alpha ($\alpha$) and delta ($\delta$) biases are the "control knobs" that dictate the state of the circuit. By manipulating these, you transform a passive superconducting loop into an active logic gate.To understand this, we look at the potential energy landscape of the device. As mentioned, this is a "double-well" potential where the two wells represent the binary states ($0$ and $1$).

```python
import numpy as np
import matplotlib.pyplot as plt

# Define the potential function
# The potential U(phi) = (1/4) * phi^4 - (delta/2) * phi^2 - alpha * phi
# delta affects the "depth" of the barrier (bifurcation parameter)
# alpha affects the tilt
def potential(phi, delta, alpha):
    return 0.25 * phi**4 - (delta / 2.0) * phi**2 - alpha * phi

# Generate phi values
phi = np.linspace(-2.5, 2.5, 400)

# Define scenarios
# 1. Delta < 0 (below threshold) -> single well (Reset/Inactive)
delta_low = -1.0
alpha_0 = 0.0
u_low = potential(phi, delta_low, alpha_0)

# 2. Delta > 0 (above threshold) -> symmetric double well (Evaluating)
delta_high = 2.0
alpha_0 = 0.0
u_sym = potential(phi, delta_high, alpha_0)

# 3. Delta > 0, Alpha > 0 -> tilted double well (Biased/Logic Decision)
delta_high = 2.0
alpha_pos = 0.5
u_asym = potential(phi, delta_high, alpha_pos)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(phi, u_low, label=r'$\delta < 0, \alpha = 0$ (Reset/Inactive)', linestyle='--')
plt.plot(phi, u_sym, label=r'$\delta > 0, \alpha = 0$ (Evaluating/Symmetric)', linewidth=2)
plt.plot(phi, u_asym, label=r'$\delta > 0, \alpha > 0$ (Biased/Tilted)', linewidth=2)

plt.title('Potential Energy Landscape of a QFP')
plt.xlabel(r'Magnetic Flux ($\phi$)')
plt.ylabel(r'Potential Energy ($U$)')
plt.axhline(0, color='black', linewidth=0.5)
plt.axvline(0, color='black', linewidth=0.5)
plt.ylim(-2, 2)
plt.legend()
plt.grid(True, linestyle=':', alpha=0.6)
plt.show()
```

![alt text](image.png)

