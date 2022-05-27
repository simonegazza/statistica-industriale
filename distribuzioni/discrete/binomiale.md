---
title: "Binomiale"
---
# Binomiale
La Binomiale è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Discrete|discreta]].

Si indica con $X \sim \mathrm{bin}(n, p)$ in cui $n \in \mathbb{N}^+$ e $p \in [0,1]$, dove il parametro $n$ indica il numero di prove ripetute di un esperimento che ha [[probabilita|probabilità]] $p$ di avere successo (o meno).

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$
per una binomiale di parametri $n$ e $p$ con $k = 1, \ldots, n$ risultati favorevoli.

È [[riproducibile]]: ovvero se $X_1, X_2, \ldots, X_m$ [[indipendenza|indipendenti]] e $X_i \sim \mathrm{bin}(n_i, p)$ allora $X_1 + X_2 + \ldots + X_m \sim \mathrm{bin}(n_1 + n_2 + \ldots + n_m, p)$.

Ha [[media]] $E(X) = np$ e [[varianza]] $Var(X) = np(1-p)$.

<img src="https://upload.wikimedia.org/wikipedia/commons/7/75/Binomial_distribution_pmf.svg" alt="grafico della distribuzione" width=700>
