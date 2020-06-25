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

## 1.2 Basic Theorems

### Part A: Normal form SIS

1. Show that for random $\mathbf{B} \in \mathbb{Z}_q^{n\times n}, A' \in \mathbb{Z}_q^{n \times (m - n)}$,  $\mathbf{B}[\mathbf{A}'\Vert I]$ is uniformly random.
2. Show polynomial-time reductions of ssLWE($n,m,q,\chi$) and LWE($n,m,q,\chi)$ in both directions, where ssLWE is LWE except that the secret is also short (drawn from the error distribution).

## 1.3 Basic Crypto Application

1. Show that the PKE demonstrated is correct if $\mathsf{Supp}(\chi) \subseteq (-q/4,q/4)$ aand CPA-secure under the LWE assumption $\mathsf{LWE}$$(n,m = \mathsf{poly}(n),q,\chi)$.

2. > Open Problem 1.1: Construct a *nice* private-key encryption from the hardness of SIS.

3. Prove that the Regev Scheme for public-key encryption is correct and CPA-secure.

4. (Not stated as an exercise in note, but) Analyze the dual Regev Scheme.

5. > Open Problem 1.2: construct a public-key encryption scheme from the hardness of LWE where the suuport of error $\chi$ is large, namely $[-cq,cq]$ for some constant $c$.

