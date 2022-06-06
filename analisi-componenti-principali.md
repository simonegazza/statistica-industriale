---
title: "Analisi delle componenti principilali"
---
# Analisi delle componenti principilali (PCA)
Sia $\bold{X}$ un [[vettori-aleatori|vettore aleatorio]] di dimensione $n$ con [[covarianza|matrice di covarianza]] $M = C(X)$. Allora $M$ ha $n$ autovalori non negativi $\lambda_1, \lambda_2, \ldots, \lambda_n \in \mathbb{R}^+$ e $n$ autovettori ortogonali $v_1, v_2, \ldots, v_n \in \mathbb{R}^n$ di lunghezza unitaria, per cui avremo che $Mv_k = \lambda_k v_k$ per $k = 1, \ldots, n$. E quindi avremo che:
$$
MV = V \Lambda \iff V^T M V =V^T V \Lambda = \Lambda
$$

Guardiamo ora la composizione delle varie matrici:
$$
V = \begin{pmatrix}
|   & |     &        & |    \\
v_1 & v_2   & \ldots & v_n  \\
|   & |     &        & |
\end{pmatrix} \in M_{n \times n},

\\

MV = \begin{pmatrix}
        |     &         |       &        & |    \\
\lambda_1 v_1 & \lambda_2 v_2   & \ldots & \lambda_n v_n  \\
        |     &         |       &        & |
\end{pmatrix} \in M_{n \times n},
=
V \cdot \begin{pmatrix}
\lambda_1   &           & \\
            & \ddots    & \\
            &           &  \lambda_n
\end{pmatrix},
$$

Questo permette di definire una trasformazione molto utile: $Y = V^TX$ con $C(Y) = diag(\lambda)$, infatti $C(Y) = V^TC(X)V = V^TMV=\Lambda$.

Si noti che le componenti di $Y$ si chiamano **componenti principali** di $X$.

Per i motivi sopra elencati, dato un qualunque [[vettori-aleatori|vettore aleatorio]] $X$ esiste una rotazione di $\mathbb{R}^n$ detta $N \in M_{n \times n}$ tale che il vettore ruotato $Y = NX$ ha $C(Y)$ diagonale. Nel riferimento ruotato quindi,il vettore originario ha le varie componenti scorrelate fra di loro (ovvero [[covarianza]] zero).

<img src="https://i2.wp.com/dataaspirant.com/wp-content/uploads/2021/01/9-Principal-Component-Analysis-With-Dimensions.png?ssl=1" alt="grafico della distribuzione" width=700>
