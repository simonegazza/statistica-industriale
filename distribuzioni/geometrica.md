---
title: "Geometrica"
---
La Geometrica è una distribuzione di probabilità discreta.

Si indica con $X \sim \mathrm{geom}(p)$ in cui $p \in (0,1]$ (se $p = 0$ allora sarebbe $X = \infty$), $p$ indica la probabilità della prima verifica di un evento.

La funzione di densità di probabilità è:
$$P(X = k) = p (1-p)^{k-1}$$

Si trova tutte le volte che si c'è un processo di Bernoulli alla base, in questo caso si conta il numero di tentativi prima che il k-esimo successo avvenga.

È la versione discreta dell'[[esponenziale]].

Ha media $E(X) = \frac{1}{p}$ e varianza $Var(X) = \frac{1-p}{p^2}$.

<img src="https://valelab4.ucsf.edu/svn/3rdpartypublic/boost/libs/math/doc/sf_and_dist/graphs/geometric_pdf_2.png" alt="grafico della distribuzione" width=700>
