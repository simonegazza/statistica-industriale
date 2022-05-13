---
title: "Uniforme discreta"
---
# Uniforme discreta
L'uniforme discreta è una distribuzione di probabilità discreta.
Spesso modella bene dadi o monete.

Non ha un vero e proprio simbolo con cui si indica (anche se talvolta si indica con $\mathcal{U}\{a, b\}$, da non confondersi con la [[uniforme]] che è continua e si indica con $\mathcal{U}(a, b)$).

La funzione di densità di probabilità è:
$$P(X = i) = \frac{1}{n}$$
con $i = 1, 2, \ldots, n$.

Non è [[riproducibile]]: infatti se avessi delle $X_i$ tutte uniformi discrete sullo stesso intervallo allora $\sum_i X_i \sim \mathcal{N}(\mu, \sigma)$.

Ha media $E(X) = \frac{n}{p}$ e varianza $Var(X) = n\frac{1-p}{p^2}$.

<img src="https://www.statisticshowto.com/wp-content/uploads/2015/04/negative-bimonial.png" alt="grafico della distribuzione" width=700>
