# Problem set 1

## A.Introduction

1. Ramsey's theorem.
    `Solution:` 
    (a) We have already shown by induction that $n = n(s, 2)$ exists for any $s \in \mathbb{N}$. Now we induct on $r$ to show that the claim holds for any $s, r \in \mathbb{N}$. (*Note the bound we give here is very loose.*) 
    Suppose for any $s \in \mathbb{N}$ and any $r \le R \in \mathbb{N} $ the claim is valid. To show that there exists $n = n(s, R + 1)$ such that the claim is true, we consider a graph $G$ with $n(n(s, 2), R)$ vertices. We color $G$ with $R + 1$ colors, but we treat the last two colors as the same for the moment. Therefore by inductive hypothesis, there exists a monochromatic clique $K$ with $n(s,2)$ vertices. If $K$ is really monochromatic when we treat the last 2 colors as different, we are done because it contains $K_s$. Otherwise, there are only 2 colors in $K$, which has $n(s,2)$ nodes. Therefore there exists a monochromatic $K_s$ in $K$ and we are done.
    (b)

