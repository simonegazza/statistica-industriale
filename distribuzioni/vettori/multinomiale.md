---
title: "Multinomiale"
---
# Multinomiale
La Multinomiale è un [[vettori-aleatori|vettore aleatorio]] di [[probabilita|probabilità]] [[variabili-aleatorie#Discrete|discreta]].

Si indica con $X \sim \mathrm{multin}(n, p)$ in cui $n \in \mathbb{N}^+$ e $p = (p_1, p_2, \ldots, p_n) \land p_i \in [0,1] \land \sum_{i=1}^n p_i = 1$, dove il parametro $n$ indica il numero di prove ripetute di un esperimento che ha [[probabilita|probabilità]] $p$ di avere successo (o meno). Si noti che le [[binomiale|binomiali]] interne non sono indipendenti, infatti abbiamo $\sum_{i=1}^n p_i = 1$.

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
P(X = k) = \binom{n}{x_1 x_2 \ldots x_n} p^{x_1} p^{x_2} \ldots p^{x_n} =\frac{n!}{\prod_{i = 1}^k x_i!}\prod_{i = 1}^k p_i^{x_i}
$$

Si noti che i vari componenti del vettore formano una base canonica, infatti richiedendo che $P(X_j = e_i) = p_i$ con $e_1 = (1, 0, \ldots, 0)$ e $e_n = (0, 0, \ldots, 1)$ allora si descrive una variabile aleatoria $S = X_1 + X_2 + X_n$.

Si noti che si ottiene una [[binomiale]] da una multinomiale di parametri $(p, 1-p)$ e $n$, quindi se $X \sim \mathrm{multin}(n, (p, 1-p)) = \mathrm{binom}(n, p)$

Ha [[media]] $E(\bold{X}) = (E(X_1), E(X_2), \ldots, E(X_n)) = n(p_1, p_2, \ldots, p_n) = (np_1, np_2, \ldots, np_n)$.

È possibile generare la multinomiale in 2 modi differenti:
- posso generare le $k$ prove indipendenti chiamate $Y_i$ e quindi $P(Y_i = j) = p_j$. A questo punto faccio che $Y_i = F_{Y_i}^{-1}(\mathrm{unif}(0,1))$, con $\mathrm{unif}$ una [[uniforme]]. Si noti che in questo caso la CdF è a gradini poichè ogni contributo di ogni [[variabili-aleatorie|vv.aa.]] alza la probabilità del rispettivo $p_i$. A questo punto le nostre $X_j = \#\{i : Y_i = j\}$.
- genero $\bold{X}$ componente per componente direttamente: infatti $X_1 = \mathrm{bin}(n, p_1)$, $X_2 = \mathrm{bin}(n - X_1, \frac{p_2}{p_2 + \ldots + p_k})$, $X_2 = \mathrm{bin}(n - X_1 - X_2, \frac{p_3}{p_3 + \ldots + p_k})$, $\ldots$
