---
title: "Varianza"
---
# Varianza
È il [[momenti-distribuzioni|momento centrato secondo]], e quindi abbiamo che:
$$
    Var(X) \coloneqq E(X - E(X)^2) = E(X^2) - E(X)^2
$$

Si tratta di una misura che indica di quanto $X$ si discosta dalla [[media]]. Quindi è un numero non-negativo, infatti $Var(X) \ge 0$.

Properità della varianza:
- Quadraticità: $Var(aX + b) = a^2 Var(X)$
- $Var(X - Y) = Var(X) + Var(Y)$
- Se $X$ e $Y$ indipendenti, allora $Var(X + Y) = Var(X) + Var(Y)$, altrimenti $Var(X + Y) = Var(X) + Var(Y) + 2Cov(X, Y)$
- Se $Var(X) = 0$ allora $\exists a : P(X = a) = 1$, ma anche che se $f_X(x) = \delta(x - a)$ allora $Var(X) = 0$, con $a \in \mathbb{R}$ e la funzione $\delta$ è la distribuzione [[delta-dirac|delta di Dirac]].