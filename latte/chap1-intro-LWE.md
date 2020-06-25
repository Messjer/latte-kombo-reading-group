# Chapter 1 -- The LWE Problem

## 1.1 LWE and SIS: definitions

### Part A: SIS-related

1. Show that for the SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$
    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very likely to exist if $(2B+1)^m \gg q^n$, or $m = \Omega(\frac{n\log q}{\log B})$ . This regime is called the total regime or the SIS regime.

2. Show that for the hSIS (homogenous SIS) problem
    $$
    \mathbf{A}\mathbf{e} = 0 \mod q.
    $$
    This problem is total as long as $(B+1)^m > q^n$, i.e. in that case, for every $\mathbf{A}$ a short solution is guaranteed to exist.

3. Show that the average cases of hSIS and SIS are equivalent in that a p.p.t. algorithm for one gives a p.p.t. algorithm to the other.

### Part B: LWE-related

1. Show that for the following SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$

    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very **unlikely** to exist if $(2B+1)^m \ll q^n$. Also, show that if $\mathbf{A}$ and $\mathbf{e}$ are random and $\mathbf{b}$ is computed accordingly, the solution $\mathbf{e}$ is very likely to be unique.

2. Show that for the LWE problem with $(\mathbf{A,y})$ as input, the error vector $\mathbf{e}$ is unique.

3. It was shown that you can reduce LWE to SIS in the *LWE-regime*. Running the reduction in reverse transforms SIS to LWE. Therefore SIS in the LWE-regime is LWE in disguise. Show explicitly such a reduction.

