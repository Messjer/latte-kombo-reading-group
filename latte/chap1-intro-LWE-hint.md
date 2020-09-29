# Chapter 1 -- The LWE Problem

## 1.1 LWE and SIS: definitions

### Part A: SIS-related

1. Show that for the SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$
    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very likely to exist if $(2B+1)^m \gg q^n$, or $m = \Omega(\frac{n\log q}{\log B})$ . This regime is called the total regime or the SIS regime.

    ~~*Hint.* For distinct $\boldsymbol{e}, \boldsymbol{f} \in \mathbb{F}_q^m$, the events $\boldsymbol{Ae=b}$ and  $\boldsymbol{Af=b}$ (where $\boldsymbol{A}$ and $\boldsymbol{b}$ uniformly random) are indep because the event $\boldsymbol{A}(\boldsymbol{f}-\boldsymbol{e})=\boldsymbol{0}$ has prob $\frac{1}{q^n}$ by independence of rows, and for any fixed $\boldsymbol{A}$,  $\boldsymbol{Ae}  = \boldsymbol{b}$ has prob $\frac{1}{q^n}$. Let $X = |\{\boldsymbol{e} \in [-B, B]^m: \boldsymbol{Ae}=\boldsymbol{b}\}|$, which is a sum of pairwise indep indicators (n.b. not necessarily all indep). Now show that $X\neq 0$ w.h.p.~~

    `Solution:` For a fixed $\mathbf{e} \in \{-B, \ldots,+B\}^n$ and some $\mathbf{A} \gets \mathbb{Z}_q^{n \times m}$, there is exactly one $\mathbf{b} \in \mathbb{Z}_q^n$ that satisfies the equation. Thereore
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
    This problem is total as long as $(B+1)^m > q^n$, i.e. in that case, for every $\mathbf{A}$ a short solution is guaranteed to exist.
    
    ~~Hint: Pigeonhole principle.~~
    
    `Solution:` Consider the set $\{e_1\mathbf{a}_1 + \ldots e_m \mathbf{a}_m \vert e_1,\ldots, e_m \in \{0,1,2\ldots,B\}\}$. Since $(B + 1)^m > q^n$, there exist  $\mathbf{e}, \mathbf{f}$ such that $\mathbf{Ae = Af}$ so $\mathbf{A}(\mathbf{e - f}) = 0$. Note that $\mathbf{e - f} \in \{-B,\ldots,B\}^m$ is such a short vector solution. 
    
3. Show that the average cases of hSIS and SIS are equivalent in that a p.p.t. algorithm for one gives a p.p.t. algorithm to the other.
    `Solution:` 
    `First direction` From $\mathsf{SIS}(n,m,q,B)$ to $\mathsf{hSIS}(n,m + 1,q,\frac{B}{2})$: Given a random $(\mathbf{A,b})$ for SIS, let 
    $$
    A' = 
    \begin{bmatrix}
    \mathbf{A} & \mathbf{A}\mathbf{r} + t\mathbf{b}
    \end{bmatrix},
    $$
    where $r \gets \{-1,1\}^B, t \gets \{-(B/2)^{-1},\ldots,-1,1\ldots,(B/2)^{-1}\}$ are randomly chosen. By the leftover hash lemma, $(\mathbf{A}, \mathbf{Ar})$ is statistically close to $(\mathbf{A}, \mathbf{y})$ where $\mathbf{y}$ is uniformly random. So $A'$ is uniformly random and independent from $t$. We call hSIS on $A'$ to obtain a solution $e' = [\mathbf{e}\quad k]$ where $k$ corresponds to the extra column. Now we have
    $$
    \mathbf{Ae} + k\mathbf{Ar} + kt\mathbf{b} = 0.
    $$
    Since $A'$ is independent from $t$, $k$ and $t$ are independent. Therefore $\Pr[kt = -1]$ is roughly $\frac{1}{B}$, in which case $\mathbf{e} + k\mathbf{r}$ is a solution to the SIS.
    
    `Other direction` From $\mathsf{hSIS}(n,m,q,B)$ to $\mathsf{SIS}(n,m - 1,q,B)$: Given a random input $\mathbf{A} = [A' \Vert b]$ for hSIS, we can solve for a short $\mathbf{e}$ to the equation $\mathbf{Ae} = 0$ by querying the SIS oracle with $(A', b)$, which gives us a short $\mathbf{e}'$ satisfying $A'\mathbf{e}' = b$. Then
    $$
    e = \begin{bmatrix} \mathbf{e}'\\ -1 \end{bmatrix}
    $$
    
    is a solution to the original hSIS problem.
    
    `Another reduction for the other direction` From $\mathsf{hSIS}(n,m,q,B)$ to $\mathsf{SIS}(n,m,q,\frac{B}{2})$: Given a random input $\mathbf{A}$, generate a random $\mathbf{f}$ and query the SIS oracle with $(A, A\mathbf{f})$. Within several trials we would obtain a solution that is not $\mathbf{f}$. Their difference is a solution to the hSIS problem.

### Part B: LWE-related

1. Show that for the following SIS problem
    $$
    \mathbf{A}\mathbf{e} = \mathbf{b} \mod q,
    $$

    parameterized by $(n,m,q,B)$, ($B$-bounded) solutions are very **unlikely** to exist if $(2B+1)^m \ll q^n$. Also, show that if $\mathbf{A}$ and $\mathbf{e}$ are random and $\mathbf{b}$ is computed accordingly, the solution $\mathbf{e}$ is very likely to be unique.
    
    `Solution:` There are a total of $(2B + 1)^m$ choices of $\mathbf{e}$, so for a fixed $\mathbf{A} \in \mathbb{R}^{m \times n}$ there are at most $(2B + 1)^m$ points in $\mathbb{Z}_q^n$ that has short preimages, so there is no solution with high probability when $\mathbf{b}$ is chosen at random. 
    
    For the second problem, for fixed $e \neq e'$ the distribution $A(e-e')$ is uniformly random when $A$ is uniform. Therefore
    $$
    \Pr[Ae = Ae'] = q^{-n},
    $$
    so by union bound
    $$
    \Pr[\exists e' \neq e, Ae = Ae'] \le (2B+1)^mq^{-n}\ll 1.
    $$
    Therefore with high probability the solution is unique. 
    
2. Show that the following happens whp: for the LWE problem with $(\mathbf{A,y})$ as input, the error vector $\mathbf{e}$ is unique.
    `Solution:` Suppose there are another error vector $e'$ and another secret $s'$ that correponds to $(A,y)$ then
    $$
    y^T = s^T A + e^T\\
    y^T = s'^TA + e'^T.
    $$
    Thus $0 = (s^T - s'^T)A + (e^T-e'^T)$. As $e \neq e'$ we have $s \neq s'$.

    Therefore in order to have such a "collision", the secrets have to be different. We claim that having two secrets solving $(A, y)$ is unlikely.

    Consider any pair of vectors $s, s' \in \mathbb{Z}_q^n$, the inner product $(s^T - s'^T)A$ distributes uniformly in $\mathbb{Z}_q^m$. For the collision to happen there exist short vectors $e^T - e'^T$  in $\{-2B, -2B +1, \ldots, 2B - 1, 2B\}^n$. Therefore for a random choice of $A$,
    $$
    \Pr[(s' - s)^TA \text{ is short}] \le ((4B+1)/q)^{-m}.
    $$
    When $(A, y)$ is generated by sampling $A$ and some $s$, by union bound over $s'$ we have
    $$
    \Pr[\exists s' (s' - s)^TA \text{ is short}]\le q^n \left(\frac{4B+1}{q}\right)^{-m},
    $$
    where the right hand side is small for $m = \Omega(n)$.

3. It was shown that you can reduce LWE to SIS in the *LWE-regime*. Running the reduction in reverse transforms SIS to LWE. Therefore SIS in the LWE-regime is LWE in disguise. Show explicitly such a reduction.
    `Solution:` Let $(\mathbf{A,b})$ be an input to SIS. Our goal is to find short $\mathbf{e}$ that satisfies $\mathbf{Ae} =\mathbf{b}$. We can find a (not-necessarily short) vector $\mathbf{y} \in \mathbb{Z}_q^m$ by performing Gaussian elimination on $\mathbf{Ay} = \mathbf{b}$. Then $\mathbf{A}(\mathbf{y} - \mathbf{e}) = 0$ so $\mathbf{y} - \mathbf{e}$ is in the null space of $A$. Let $B \in \mathbb{Z}_q^{m\times (m - n)}$ be a matrix whose columns form a basis of the null space. Then there exists some $\mathbf{s} \in \mathbb{Z}_q^{m - n}$ such that $B\mathbf{s} = \mathbf{y} - \mathbf{e}$. Therefore $(B, \mathbf{y})$ is the LWE instance we need, since if we can solve for $\mathbf{s}$ we obtain $\mathbf{e} = \mathbf{y} - B\mathbf{s}$.

## 1.2 Basic Theorems

### Normal form SIS and short secret LWE

1. Show that for random $\mathbf{B} \in \mathbb{Z}_q^{n\times n}, A' \in \mathbb{Z}_q^{n \times (m - n)}$,  $\mathbf{B}[\mathbf{A}'\Vert I]$ is uniformly random.
2. Show polynomial-time reductions of ssLWE($n,m,q,\chi$) and LWE($n,m,q,\chi)$ in both directions, where ssLWE is LWE except that the secret is also short (drawn from the error distribution). *Maybe this can be shown by noting that ssLWE is nfSIS in disguise.*

## 1.3 Basic Crypto Application

1. Show that the PKE demonstrated is correct if $\mathsf{Supp}(\chi) \subseteq (-q/4,q/4)$ aand CPA-secure under the LWE assumption $\mathsf{LWE}$$(n,m = \mathsf{poly}(n),q,\chi)$.
    `Solution:` Correctness is immediate. For security:

2. > Open Problem 1.1: Construct a *nice* private-key encryption from the hardness of SIS.

3. Prove that the Regev Scheme for public-key encryption is correct and CPA-secure.
    ~~Hint: maybe need leftover hash lemma.~~

4. (Not stated as an exercise in note, but) Analyze the dual Regev Scheme.

5. > Open Problem 1.2: construct a public-key encryption scheme from the hardness of LWE where the suuport of error $\chi$ is large, namely $[-cq,cq]$ for some constant $c$.

