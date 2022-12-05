---
title: "Multinomiale"
---
# Multinomiale
La Multinomiale è un [[vettori-aleatori|vettore aleatorio]] di [[probabilita|probabilità]] [[variabili-aleatorie#Discrete|discreta]].

Si indica con $\bold{X} \sim \mathrm{multin}(n, \bold{p})$ in cui $n \in \mathbb{N}^+$ e $\bold{p} = (p_1, p_2, \ldots, p_k) \land p_i \in [0,1] \land \sum_{i=1}^k p_i = 1$, dove il parametro $n$ indica il numero di prove ripetute di $k$ esperimenti che hanno [[probabilita|probabilità]] $\bold{p}$ di avere successo *in maniera non indipendente*.

Si noti che le [[binomiale|binomiali]] interne **non sono indipendenti**, infatti abbiamo $\sum_{i=1}^k p_i = 1$. Si noti inoltre che $\bold{X} = (X_1, X_2, \ldots, X_k)$ e che $n = \sum_{i=1}^k X_i$

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
P(\bold{X} = \bold{a}) = \binom{n}{a_1 a_2 \ldots a_n} p^{a_1} p^{a_2} \ldots p^{a_k} =\frac{n!}{\prod_{i = 1}^k a_i!}\prod_{i = 1}^k p_i^{a_i}
$$

Si noti che i vari componenti del vettore formano una base canonica, infatti richiedendo che $P(X_j = e_i) = p_i$ con $e_1 = (1, 0, \ldots, 0)$ e $e_n = (0, 0, \ldots, 1)$ allora si descrive una variabile aleatoria $\bold{S} = X_1 + X_2 + \ldots + X_n$.

Ha [[media]] $E(\bold{X}) = (E(X_1), E(X_2), \ldots, E(X_k)) = n(p_1, p_2, \ldots, p_k) = (np_1, np_2, \ldots, np_k)$.
Ha [[varianza]] $Var(\bold{X}) = (Var(X_1), Var(X_2), \ldots, Var(X_k)) = (n p_1(1 - p_1), n p_2(1 - p_2), \ldots, n p_k(1 - p_k))$
Ha [[covarianza]] $Cov(X_i, X_j) = (-np_i p_j) \quad \forall i \not = j$

## Generazione di una Multinomiale
È possibile generare la multinomiale in 2 modi differenti:
- genero $n$ prove indipendenti chiamate $Y_i$ in cui $P(Y_i = j) = p_j$. Imposto che $Y_i = F_{Y_i}^{-1}(\mathrm{unif}(0,1))$, con $\mathrm{unif}$ una [[uniforme]]. Si noti che in questo caso la CdF è a gradini poichè ogni contributo di ogni [[variabili-aleatorie|vv.aa.]] alza la probabilità del rispettivo $p_i$. A questo punto le nostre $X_j = \#\{i : Y_i = j\}$.
- genero $\bold{X}$ componente per componente direttamente: infatti $X_1 = \mathrm{bin}(n, p_1)$, $X_2 = \mathrm{bin}(n - X_1, \frac{p_2}{p_2 + \ldots + p_k})$, $X_2 = \mathrm{bin}(n - X_1 - X_2, \frac{p_3}{p_3 + \ldots + p_k})$, ecc.... Quindi
$$
X_i = \mathrm{bin} \Bigg(n - \sum_{j = 1}^{i-1} X_j, \frac{p_i}{\sum_{q = i}^k p_q} \Bigg)
$$
