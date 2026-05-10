# Flux Qubit

A flux qubit is a type of superconducting qubit based on a micrometer-sized loop of superconducting material interrupted by Josephson junctions. It uses magnetic flux as the basis for quantum information, with states represented by clockwise or counter-clockwise persistent currents. It enables quantum superposition, existing in both current states simultaneously.

The system is characterized by a potential with two minima, corresponding to the two current directions. Quantum tunneling between these wells allows superposition states. 
Flux qubits have high anharmonicity, meaning the energy levels are not evenly spaced. This makes it easier to target the specific transition needed for operations without accidentally exciting the qubit to higher states.

To control the qubit, an external magnetic field is typically applied to bias the loop at approximately half of a magnetic flux quantum. This creates a double-well potential where the two current states are nearly degenerate, allowing for quantum tunneling between them.

A related type, the fluxonium qubit, adds a large inductor to protect the qubit from environmental noise, enhancing coherence.

As you increase the number of Josephson junctions (JJs) in a flux qubit, the circuit moves from a simple sensor-like structure to a highly engineered quantum bit with better protection against noise.

### 1-JJ Flux Qubit (rf-SQUID)
The simplest design, consisting of a single junction in a superconducting loop. 
Mechanism: Relies on the loop's geometric inductance to create a double-well potential.
Pros: Simple and robust; excellent for magnetic field sensing.
Cons: Requires a very large loop to achieve enough inductance for a qubit state. This makes it highly sensitive to external magnetic flux noise, which causes decoherence. 

### 2-JJ Flux Qubit (dc-SQUID)
Uses two junctions, effectively acting like a dc-SQUID loop. 
Mechanism: The two junctions provide a more complex potential energy surface. It is often used to study regimes with large tunneling amplitudes.
- Pros: Allows for higher tunneling between states compared to the 1-JJ version.
- Cons: Still limited in flexibility for modern large-scale quantum processors because the potential landscape is harder to "tune" perfectly without affecting other parameters. 

### 3-JJ Flux Qubit (Standard Modern Flux Qubit)
The current industry standard (pioneered by Delft/Mooij). It uses two identical junctions and one smaller "alpha-junction" (typically 60-80% the size of the others). The two larger junctions act as a replacement for loop inductance, allowing the qubit loop to be much smaller.

- Pros:
    - High Anharmonicity: Makes it easier to distinguish the 0 and 1 states from higher energy levels.
    - Compact Design: Smaller loops are less sensitive to environmental flux noise.
    - Tunability: By replacing the small alpha-junction with a dc-SQUID (creating a 4-JJ qubit), the qubit's energy gap can be tuned mid-experiment.
- Cons: More complex fabrication; requiring three (or more) junctions to be precisely matched or scaled. 

Summary Comparison Table:

| Feature | 1-JJ | 2-JJ | 3-JJ |
|---|---|---|---|
| Loop Size |	Large (needs high L) | Medium | Smallest (compact) |
| Noise Sensitivity	| Very High | High | Low |
| Primary Advantage | Simplicity | High Tunneling | Anharmonicity & Scalability |
| Typical Use | Basic Sensors | Physics Research | Quantum Computing |

Key Technical Differences between the transmon and a flux qubit:

| Feature | Transmon Qubit | Flux / Fluxonium Qubit |
|---|---|---|
| Circuit Design | A Josephson junction in parallel with a large capacitor. | A superconducting loop containing one or more Josephson junctions and a superinductor. |
| Operating Frequency | Typically higher, around 4–5 GHz. |	Typically lower, often between 0.1–1 GHz. |
| Anharmonicity | Low (~200–300 MHz); energy levels are closely spaced, which can lead to "leakage" into higher states. | High; energy levels are widely separated, allowing for faster control pulses without accidental transitions. |
| Coherence Times | Generally in the range of tens to hundreds of microseconds. | Can exceed 1 millisecond, roughly 10x longer than typical transmons. |
| Sensitivity | Highly resistant to charge noise but can be sensitive to dielectric loss. | Highly resistant to dielectric loss due to lower frequencies. |