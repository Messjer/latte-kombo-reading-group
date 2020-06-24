# Chapter 1 -- The LWE Problem

## 1.1 LWE and SIS: definitions

1. Show that for the SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$
    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very likely to exist if $(2B+1)^m \gg q^n$, or $m = \Omega(\frac{n\log q}{\log B})$ . This regime is called the total regime or the SIS regime.

    ~~*Hint.* For distinct $\boldsymbol{e}, \boldsymbol{f} \in \mathbb{F}_q^m$, the events $\boldsymbol{Ae=b}$ and  $\boldsymbol{Af=b}$ (where $\boldsymbol{A}$ and $\boldsymbol{b}$ uniformly random) are indep because the event $\boldsymbol{A}(\boldsymbol{f}-\boldsymbol{e})=\boldsymbol{0}$ has prob $\frac{1}{q^n}$ by independence of rows, and for any fixed $\boldsymbol{A}$,  $\boldsymbol{Ae}  = \boldsymbol{b}$ has prob $\frac{1}{q^n}$. Let $X = |\{\boldsymbol{e} \in [-B, B]^m: \boldsymbol{Ae}=\boldsymbol{b}\}|$, which is a sum of pairwise indep indicators (n.b. not necessarily all indep). Now show that $X\neq 0$ w.h.p.~~

    *Solution*: For a fixed $\mathbf{e} \in \{-B, \ldots,+B\}^n$ and some $\mathbf{A} \gets \mathbb{Z}_q^{n \times m}$, there is exactly one $\mathbf{b} \in \mathbb{Z}_q^n$ that satisfies the equation. Thereore
    $$
    \Pr_{A \gets \mathbb{Z}_q^{n \times m}, \mathbf{b} \gets \mathbb{Z}_q^n}[\mathbf{Ae} = \mathbf{b}] = \frac{1}{q^n}.
    $$
    Let $I_{\mathbf{e}}$ be the indicator of the above event. There exists a solution to $\mathbf{Ae} = \mathbf{b}$ iff 
    $$
    \sum_e I_e \ge 1.
    $$
    So for random $\mathbf{A}$ and $\mathbf{b}$, we have $E := \mathbb{E}[\sum_e I_e] = \frac{(2B + 1)^m}{q^n} \gg 1$. For two such solutions, $\mathbf{e \neq f}$, the r.v's $I_e$ and $I_f$ and independent because for the concurrence of the events $\mathbf{Ae = b}$ and $\mathbf{Af = b}$ is equivalent to
    $$
    \begin{align}
    \mathbf{A(e - f)} &= 0\\
    \mathbf{Af} &= b.
    \end{align}
    $$
    The first event happens with probability $\frac{1}{q^n}$ because after fixing all but one column of $\mathbf{A}$ that corresponds to non-zeros in $\mathbf{e - f}$, there is only 1 way to fill in the last column to make $\mathbf{A(e - f)} = 0$. The second event apparently happens with probability $\frac{1}{q^n}$. Therefore $I_e$ and $I_f$ are independent.
    Therefore all the $I_e$'s are pairwise independent. We select Chebyshev's inequality as our bound to use here. First $\mathbf{Var}[I_e] = \mathbb{E}[I_e^2] - \mathbb{E}[I_e]^2 = \frac{1}{q^n} - \frac{1}{q^{2n}}$. Define $I = \sum_e I_e$ then $\mathbf{Var}[I] = (2B + 1)^m\mathbf{Var}[I_e]$. By Chebyshev's inequality,
    $$
    \begin{align}
    	\Pr[X = 0] \le \Pr[\lvert X - E\rvert \ge E] &\le \frac{(2B + 1)^m\mathbf{Var}[I_e]}{E^2}\\
    	&= \frac{q^n - 1}{(2B + 1)^m} \approx 0.
    \end{align}
    $$
    So there exists a solution w.h.p.
    
2. Show that for the hSIS (homogenous SIS) problem
    $$
    \mathbf{A}\mathbf{e} = 0 \mod q.
    $$
    This problem is total as long as $(B+1)^m > q^n$, i.e. for every $\mathbf{A}$ a short solution is guaranteed to exist. Also prove that SIS and hSIS are equivalent on the avereage-case.
    
3. Show that hSIS and SIS are equivalent in that a p.p.t. algorithm for one gives a p.p.t. algorithm to the other.

    