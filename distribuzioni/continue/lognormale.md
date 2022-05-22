---
title: "Lognormale"
---
# Lognormale
La lognormale è una [[distribuzione]] di [[probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \mathrm{lognormale}(\mu, \sigma^2)$ in cui $\mu \in \mathbb{R}$ è la [[momenti/media]] e $\sigma > 0$ la [[deviazione-standard|deviazione standard]].

La classe delle gaussiane è chiusa per trasformazioni lineari, che vuol dire che se $X \sim \mathcal{N}(\mu, \sigma^2)$ allora $a + bX \sim \mathcal{N}(a + b\mu, b^2\sigma^2)$.

Si tratta dell'esponenziale della gaussiana ed è *sempre positiva*. Il suo logaritmo è una variabile normale, infatti $\log X \sim \mathcal{N}(\mu, \sigma)$.

Si noti che cambiare la base del logaritmo è equivalente a fare una trasformazione lineare, infatti $\log_a X \iff \frac{\log_b X}{\log_b a} \sim \mathcal{N}\bigg(\frac{\mu}{\log_b a}, \big(\frac{\sigma}{\log_b a}\big)^2\bigg)$.

Il [[teorema-limite-centrale|teorema del limite centrale]] pone il **prodotto** di contributi [[indipendenti]] simile ad una lognormale. Si noti che se fosse il la somma di contributi [[indipendenti]], tratteremmo una [[gaussiana]]. Esempi famosi sono redditi, patrimoni, ecc.

È asimmetrica con coda a destra e assume spesso valori con diversi ordini di grandezza.

Durante l'analisi dei dati, si fa il logaritmo della variabile e poi si tratta come dati [[gaussiana|normali]].

Ha [[momenti/media]] $E(X) = e^{\mu + \frac{\sigma^2}{2}}$.
La [[mediana]] è $e^\mu$.

<img src="https://upload.wikimedia.org/wikipedia/commons/4/46/Lognormal_distribution_PDF.png" alt="grafico della distribuzione" width=700 style="background: white">
