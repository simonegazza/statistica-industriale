---
title: "Poisson-gamma"
---
La Poisson-gamma è una distribuzione di probabilità discreta. In particolare è ottenuta da una variabile aleatoria di distribuzione [[gamma]] $T \sim \mathrm{gamma}(\alpha, \lambda)$ (con $\alpha \ge 0$ e $\lambda \ge 0$) e poi da una variabile aleatoria $X \sim \mathrm{Pois}(T)$ di distribuzione [[poissoniana|Poisson]].

Una possibile formalizzazione la indica con $X \sim \mathrm{PG}(\alpha, p)$.

Per realizzarsi, si noti che deve verificarsi che $E(X) \le Var(X)$.

La funzione di densità di probabilità è:
$$
P(X = k) = \frac{\Gamma(\alpha + k)}{\Gamma(\alpha) k!} \bigg(\frac{\lambda}{\lambda + 1}\bigg)^\alpha \bigg(\frac{1}{\lambda + 1}\bigg)^k
$$
per $k = 0, 1, 2, \ldots$.

Ha media $E(X) = \alpha \frac{1-p}{p} = \frac{\alpha}{\lambda}$ e varianza $Var(X) = \alpha \frac{1-p}{p^2} = \frac{\alpha}{\lambda} + \frac{\alpha}{\lambda^2}$.

Generalizza la [[binomiale-negativa|binomiale negativa]] se $\alpha = n$ intero, allora $X + n \sim \mathrm{negbin}(n, p)$.

Generalizza la [[poissoniana]] se $\alpha \to \infty, \lambda \to \infty$ e $\frac{\alpha}{\lambda} \to \nu$, allora $\mathrm{gamma}(\alpha, \lambda) \to \delta_\nu$ e quindi $\mathrm{Pois}(\nu)$. Si tratta di una legge in due parametri sugli interi non negativi, ed è quindi molto più flessibile della [[poissoniana]].

È l'analogo discreto della [[gamma]].
