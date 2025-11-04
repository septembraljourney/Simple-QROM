# Quantum ROM
We implement here a Qiskit function that takes an input, a classical Boolean function $f:\mathbb F_2^n \to \mathbb F_2^d$, and outputs the oracle

$$U_f : \ket{x} \ket{y} \mapsto \ket{x}\ket{y \oplus f(x)}$$

and verify its correctness for small $n$ and $d$.

## Method
For each $j$-th output bit $f_j$:
- Collect $S_j=\{x\in\mathbb F_2^n \mid f_j(x)=1\}$.
- For each $x\in S_j$ : temporarily flip 0-controls on the input, apply one $n$-controlled $X$ to target $y_j$, then unflip.
Repeat for all $j$. This realizes $y \mapsto y\oplus f(x)$ and thus $U_f$.
