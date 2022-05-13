---
title: "Binomiale negativa"
---
# Binomiale negativa
La Binomiale negativa è una distribuzione di probabilità discreta.
È chiamata anche distribuzione di Pascal.

Si indica con $X \sim \mathrm{negbin}(n, p)$ in cui $n \in \mathbb{N}^+$ e $p \in [0,1]$, dove il parametro $n$ indica il numero di prove ripetute di un esperimento che ha probabilità $p$ di avere successo (o meno).

La funzione di densità di probabilità è:
$$P(X = k) = \binom{k-1}{n-1} p^n (1-p)^{k-n}$$
per una binomiale negativa di parametri $n$ e $p$ con $k \ge n$ risultati favorevoli. Si noti che ha $k$ e $n$ nelle posizioni opposte rispetto alla [[binomiale]].

È [[riproducibile]]: ovvero se $X_1, X_2, \ldots, X_m$ indipendenti e $X_i \sim \mathrm{negbin}(n_i, p)$ allora $X_1 + X_2 + \ldots + X_m \sim \mathrm{negbin}(n_1 + n_2 + \ldots + n_m, p)$.

Ha media $E(X) = \frac{n}{p}$ e varianza $Var(X) = n\frac{1-p}{p^2}$.

<img src="https://www.statisticshowto.com/wp-content/uploads/2015/04/negative-bimonial.png" alt="grafico della distribuzione" width=700>
