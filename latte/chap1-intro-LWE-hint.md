# Chapter 1 -- The LWE Problem

## 1.1 LWE and SIS: definitions

1. Show that for the SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$
    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very likely to exist if $(2B+1)^m \gg q^n$, or $m = \Omega(\frac{n\log q}{\log B})$ . This regime is called the total regime or the SIS regime.

    *Hint.* For distinct $\boldsymbol{e}, \boldsymbol{f} \in \mathbb{F}_q^m$, the events $\boldsymbol{Ae=b}$ and  $\boldsymbol{Af=b}$ (where $\boldsymbol{A}$ and $\boldsymbol{b}$ uniformly random) are indep because the event $\boldsymbol{A}(\boldsymbol{f}-\boldsymbol{e})=\boldsymbol{0}$ has prob $\frac{1}{q^n}$ by independence of rows, and for any fixed $\boldsymbol{A}$,  $\boldsymbol{Ae}  = \boldsymbol{b}$ has prob $\frac{1}{q^n}$. Let $X = |\{\boldsymbol{e} \in [-B, B]^m: \boldsymbol{Ae}=\boldsymbol{b}\}|$, which is a sum of pairwise indep indicators (n.b. not necessarily all indep). Now show that $X\neq 0$ w.h.p. 

2. Show that for the hSIS (homogenous SIS) problem
    $$
    \mathbf{A}\mathbf{e} = 0 \mod q.
    $$
    This problem is total as long as $(B+1)^m > q^n$, i.e. for every $\mathbf{A}$ a short solution is guaranteed to exist. Also prove that SIS and hSIS are equivalent on the avereage-case.s