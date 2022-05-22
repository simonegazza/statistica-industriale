---
title: "Deviazione standard"
---
# Deviazione standard
Non è un vero e proprio [[momenti-distribuzioni|momento di una distribuzione]], ma è la radice della [[varianza]], spesso si indica con $\sigma$ ed è definita come:
$$
\sigma = \sqrt{Var(X)}
$$
con $X$ [[variabili-aleatorie|variabile aleatoria]].

Risulta veramente molto comoda per verifare quanto un valore si discosta dalla vedia, e spesso viene usata nella [[gaussiana]] come misura qualitativa per vedere quanto è probabile un dato. Infatti si ha che:
- $P(|X - E(X)| \le \sigma) \approx 68\%$
- $P(|X - E(X)| \le 2*\sigma) \approx 95\%$
- $P(|X - E(X)| \le a*\sigma) \approx 1 - \frac{1}{a^2}$ con $a \in \mathbb{R}$

## Disuaglianza di Markov
Se $X \ge 0$ e $P(X \ge 0) = 1$ allora $P(X \le t) \le \frac{1}{t} E(X)$ per ogni $t > 0$

## Disuaglianza di Chebyshev
Se $X$ ha [[media]] e [[varianza]] finite, allora $P(|X - E(X)| > t) \le \frac{1}{t^2} Var(X)$ per ogni $t > 0$
