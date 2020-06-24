# Chapter 1 -- The LWE Problem

## 1.1 LWE and SIS: definitions

1. Show that for the SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$
    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very likely to exist if $(2B+1)^m \gg q^n$, or $m = \Omega(\frac{n\log q}{\log B})$ . This regime is called the total regime or the SIS regime.

2. Show that for the hSIS (homogenous SIS) problem
    $$
    \mathbf{A}\mathbf{e} = 0 \mod q.
    $$
    This problem is total as long as $(B+1)^m > q^n$, i.e. for every $\mathbf{A}$ a short solution is guaranteed to exist. Also prove that SIS and hSIS are equivalent on the avereage-case.
    
3. Show that hSIS and SIS are equivalent in that a p.p.t. algorithm for one gives a p.p.t. algorithm to the other.

