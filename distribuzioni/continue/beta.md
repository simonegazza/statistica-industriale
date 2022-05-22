---
title: "Beta"
---
# Beta
La beta è una [[distribuzione]] di [[probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \mathrm{beta}(\alpha, \beta)$ con $\alpha, \beta \in \mathbb{R}$ anche se generalmente sono interi.

La [[variabili-aleatorie#Continue|funzione di densità di probabilità]] è:
$$
P(X \le t) = c_{\alpha,\beta} \cdot t^{\alpha -1} \cdot (1 - t)^{\beta - 1}
$$
con $0 < t < 1$.

Generalizza l'[[uniforme]] quando $a = b = 1$, infatti $\mathrm{beta}(1, 1) \sim \mathrm{unif}(0, 1)$.

Ha anche una definizione operativa: si prenda una lista $X_1, X_2, \ldots, X_{n+m}$ [[variabili-aleatorie#Continue|v.a.]] $\mathrm{unif}(0, 1)$ [[indipendenti|i.i.d]] e le si ordinino per valore, ottenendo le [[variabili-aleatorie#Continue|v.a.]] $U_1, U_2, \ldots, U_{n+m}$. La beta indica la [[distribuzione]] della (m+1)-esima più piccola o (n+1)-esima più grande tra le $m + n + 1$ [[variabili-aleatorie#Continue|v.a.]] $U_i$. Si noti però che questa definizione operativa prevede $m$ ed $n$ interi (cosa che è molto restrittiva).

Ha [[media]] $E(X) = \frac{a + b}{2}$ e [[varianza]] $Var(X) = \frac{(b - a)^2}{12}$.

<img src="https://upload.wikimedia.org/wikipedia/commons/f/f3/Beta_distribution_pdf.svg" alt="grafico della distribuzione" width=700 style="background: white">
