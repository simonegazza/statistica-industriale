---
title: "Gaussiana"
---
# Gaussiana
La gaussiana è una distribuzione di probabilità continua. È chiamata anche normale.

Si indica con $X \sim \mathcal{N}(\mu, \sigma^2)$ in cui $\mu \in \mathbb{R}$ è la media e $\sigma > 0$ la [[momenti-distribuzioni|deviazione standard]].

La funzione di densità di probabilità è:
$$
P(X \le k) = \frac{1}{\sigma\sqrt{2 \pi}} e^{-\frac{x - \mu}{2\sigma^2}}
$$

La classe delle gaussiane è chiusa per trasformazioni lineari, che vuol dire che se $X \sim \mathcal{N}(\mu, \sigma^2)$ allora $a + bX \sim \mathcal{N}(a + b\mu, b^2\sigma^2)$.

Si dice *standard* una gaussiana con $\mu = 0$ e $\sigma^2 = 1$, ovvero $X$ è gaussiana standard se $X \sim \mathcal{N}(0, 1)$.

È la regina delle distribuzioni, infatti il [[teorema-limite-centrale|teorema del limite centrale]] pone proprio la **somma** di contributi indipendenti simile ad una gaussiana. Si noti che se fosse il prodotto di contributi indipendenti, tratteremmo una [[lognormale]].

È [[riproducibile]], ma non solo, non necessita che le variabili siano indipendenti. Infatti la somma di gaussiane genera una gaussiana la cui media è la somma delle medie (mentre la varianza è più complicata).

Ha media $E(X) = \mu$ e varianza $Var(X) = \sigma^2$.

La [[variabili-aleatorie#Continue|CdF]] è $\Phi(t) = P(\mathcal{N}(0, 1) \le t)$ e quindi $\Phi(\frac{t - \mu}{\sigma}) = P(\mathcal{N}(\mu, \sigma^2) \le t)$.

Si noti che se $\sigma = 0$ allora la gaussiana degenera in una [[delta-dirac|delta di Dirac]].
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/25/The_Normal_Distribution.svg/800px-The_Normal_Distribution.svg.png" alt="grafico della distribuzione" width=700 style="background: white">
