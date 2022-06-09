---
title: "Vettori aleatori"
---
# Vettori aleatori
Sia $\bold{X} = (X_1, X_2, \ldots, X_n)$ è un vettore di [[variabili-aleatorie|vv.aa.]] di componenti $X_1, X_2, \ldots, X_n$.

La [[media]] del vettore è $\bold{\mu} = E(\bold{X}) = (E(X_1), E(X_2), \ldots, E(X_n)) = (\mu_1, \mu_2, \ldots, \mu_n) \in \mathbb{R}^n$.

La [[covarianza]] del vettore è una matrice $\Sigma \in \mathrm{M}_{n \times n}$ tale che
$$
\Sigma \coloneqq C(X) \coloneqq\begin{bmatrix}
    \Sigma_{1, 1} & \Sigma_{1, 2} & \dots  & \Sigma_{1, n} \\
    \Sigma_{2, 1} & \Sigma_{2, 2} & \dots  & \Sigma_{2, n} \\
    \vdots        &               & \ddots & \vdots       \\
    a_{K1}        &               & \ldots & a_{KK}
\end{bmatrix}
$$
dove $\Sigma_{i, j} \coloneqq Cov(X_i, X_j)$.

Dato che la covarianza è simmetrica, sulle diagonali ci sono le $Cov(X_i, X_i) = Var(X_i)$ e la parte sotto la diagonale principale della matrice è equivalente alla parte superiore alla diagonale principale.

Si noti che se le $X_1,X_2, \ldots, X_n$ sono tutte [[indipendenza|indipendenti]], allora $\Sigma$ è diagonale.

Si noti che $\Sigma$ è *semidefinita positiva*, ovvero $\forall v \in \mathbb{R}^n$ ho $v^T C(X) v \ge 0$. La conseguenza di questo fatto è che esiste una rotazione di $\mathbb{R}^n$ detta $N \in M_{n \times n}$ tale che il vettore ruotato di $X$ detto $Y \coloneqq NX$ ha una $C(Y)$ diagonale. Questo è molto utile nella [[analisi-componenti-principali|PCA]].

![Prova prova](https://miro.medium.com/max/1400/1*T7CqlFV5aRm6MxO5nJt7Qw.gif)
*PCA - principal component analysis*

# Trasformazioni lineari
Sia $\bold{X}$ un vettore aleatorio di dimensione $n$, [[media]] $E(\bold{X}) \in \mathbb{R}^n$ e [[covarianza|matrice di covarianza]] $\Sigma = C(\bold{X}) \in M_{n \times n}$ e sia $N : \mathbb{R}^n \to \mathbb{R}^m$, con $N \in M_{m \times n}$ e vettore $a \in \mathbb{R}^m$. Allora avremo una trasformazione affine generica $Y = NX + a$. In tal caso avremo che $E(Y) = N\mu + a$ e $C(Y) = N \Sigma N^T$.

Si noti inoltre che se:
- $m = n$ e
- $N$ è invertibile e
- $X$ ha pdf $f_X : \mathbb{R}^n \to \mathbb{R}^+$,

allora $Y$ ha una pdf $f_Y : \mathbb{R}^m \to \mathbb{R}$ con $f_Y = |det(N)|^{-1} f_X(N^{-1}y)$.
