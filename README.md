
# Eigenvector Preparation with QPE and Grover

This project implements a quantum circuit in Qiskit that **prepares an eigenvector** $|x\rangle$ of a given diagonal unitary matrix $U$, such that:

$$
U|x\rangle = e^{2\pi i \theta(x)} |x\rangle,
\quad \text{where } \theta(x) = t
$$

It combines **Quantum Phase Estimation (QPE)** with **Grover's algorithm** to amplify the correct eigenvector.


## Inputs

* `U`: An $n$-qubit **diagonal unitary**, defined by eigenvalues $e^{2\pi i \theta(x)}$
* `d`: Number of ancilla qubits for **phase estimation**
* `t`: Target phase in $[0, 1)$, matching exactly one eigenvalue



## How It Works

1. **QPE** estimates the phase $\theta(x)$ in the ancilla register
2. **Grover oracle** marks the ancilla state closest to $t$
3. **Amplitude amplification** boosts the corresponding eigenvector $|x\rangle$
4. The system qubits are left in the state $|x\rangle$

No measurements are used — the final state is extracted using the `Statevector` simulator.


## Example

If $\theta(001) = 0.125$ and $t = 0.125$, the output will be:

```
Top outcomes for system register:
|001⟩ → ~1.0
```
