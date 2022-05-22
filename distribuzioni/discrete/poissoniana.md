---
title: "Poissoniana"
---
# Poissoniana
La Poissoniana è una [[distribuzione]] di [[probabilità]] [[variabili-aleatorie#Discrete|discreta]].

Si indica con $X \sim \mathrm{Pois}(\nu)$ in cui il parametro $\nu > 0$ indica la **frequenza [[media]]** del verificarsi di un certo evento. Si noti che $\nu$ può assumere un **qualsiasi valore sopra $0$**.

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
P(X = k) = \frac{\nu^k}{k!} e^{-\nu}
$$
con $k \in \mathbb{N}$ il numero di volte che tale evento si verifica.

Questa distribuzione è il limite di una [[binomiale]] $\mathrm{bin}(n, p)$ con $p << 1$ (molto piccolo) e $n >> 1$ (molto grande), infatti verifichiamo sostituendo alla [[binomiale]] $p = \frac{\nu}{n}$ e otteniamo che:
$$
\lim_{n \to +\infty} \mathrm{bin}\bigg(n, \frac{\nu}{n} \bigg) =
\lim_{n \to +\infty} \binom{n}{k} \bigg(\frac{\nu}{n}\bigg)^k \bigg(1-\frac{\nu}{n}\bigg)^{n-k} = \\
\lim_{n \to +\infty} \frac{n!}{k!(n-k)!} \bigg(\frac{\nu}{n}\bigg)^k \bigg(1-\frac{\nu}{n}\bigg)^{n-k} = \\
\lim_{n \to +\infty} \frac{n (n-1) (n-2) \ldots (n-k+1) (n-k)}{k!} \frac{\nu^k}{n^k} \bigg(1-\frac{\nu}{n}\bigg)^n \bigg(1-\frac{\nu}{n}\bigg)^{-k} = \\
\frac{\nu^k}{k!} \lim_{n \to +\infty} \frac{n (n-1) (n-2) \ldots (n-k+1) (n-k)}{n^k} \bigg(1-\frac{\nu}{n}\bigg)^n \bigg(1-\frac{\nu}{n}\bigg)^{-k} = \\
\frac{\nu^k}{k!} \lim_{n \to +\infty} \bigg(1-\frac{\nu}{n}\bigg)^n =
\frac{\nu^k}{k!} e^{-\nu}
$$

In termini più pratici, se $p << 1$ e $n >> 1$ allora $\mathrm{bin}(n, p) \dot\sim \mathrm{Pois}(np)$. Talvolta però se $p$ è sufficientemente piccolo, allora $n$ non serve tanto grande.

È [[riproducibile]]: ovvero se $X_1, X_2, \ldots, X_m$ [[indipendenti]] e $X_i \sim \mathrm{Pois}(\nu_i)$ allora $X_1 + X_2 + \ldots + X_m \sim \mathrm{Pois}(\nu_1 + \nu_2 + \ldots + \nu_m)$.

Ha [[media]] $E(X) = \nu$ e [[varianza]] $Var(X) = \nu$.

Si noti che conta il numero di successi in casi in cui la [[binomiale]], soprattutto quando $n$ e $p$ sono più "vaghi" della loro [[media]] $np$.

Si noti che con $\nu$ piccolo è molto asimmetrica.
<img src="https://www.boost.org/doc/libs/1_47_0/libs/math/doc/sf_and_dist/graphs/poisson_pdf_1.png" alt="grafico della distribuzione" width=700>
