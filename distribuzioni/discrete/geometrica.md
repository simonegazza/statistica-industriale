---
title: "Geometrica"
---
# Geometrica
La Geometrica è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Discrete|discreta]].

Si indica con $X \sim \mathrm{geom}(p)$ in cui $p \in (0,1]$ (se $p = 0$ allora sarebbe $X = \infty$), $p$ indica la [[probabilita|probabilità]] della prima verifica di un evento.

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
P(X = k) = p (1-p)^{k-1}
$$

Si trova tutte le volte che c'è un [[processo-bernoulli|processo di Bernoulli]] alla base, in questo caso si conta il numero di tentativi prima che il primo successo avvenga.

È la versione discreta dell'[[esponenziale]].

Ha [[media]] $E(X) = \frac{1}{p}$ e [[varianza]] $Var(X) = \frac{1-p}{p^2}$.

<img src="https://dr282zn36sxxg.cloudfront.net/datastreams/f-d%3A5a37978358a26231532cb533a12b4a31b472eb3d5b77ab1669a227db%2BIMAGE_TINY%2BIMAGE_TINY.1" alt="grafico della distribuzione" width=700>
