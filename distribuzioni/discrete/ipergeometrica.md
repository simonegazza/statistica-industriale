---
title: "Ipergeometrica"
---
# Ipergeometrica
L'ipergeometrica è una [[distribuzione]] di probabilità [[variabili-aleatorie#Discrete|discreta]].

Si indica con $X \sim \mathrm{hypg}(n, a, m)$ dove $X$ indica il numero di palline **colorate** estratte dall'urna; generalmente simula il processo di estrazione di palline colorate da un'urna, per cui $m$ è il totale di palline, $a$  il numero di palline colorate e $n$ quante ne sono già state estratte **senza rimessa**. Si noti che $m \ge 1$, $0 \le a \le m$ e $1 \le n \le m$.

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
P(X = k) = \frac{\binom{a}{k}\binom{m - a}{n - k}}{\binom{m}{n}}
$$
con $k \le \max(0, n - (m - a))$ e $X \le \min(a, n)$.

Si noti che se modellassimo lo stesso processo **ma con rimessa** allora sarebbe una [[binomiale]] della forma $\mathrm{bin}(n, \frac{a}{m})$. Otteniamo sempre una [[binomiale]] anche nel caso in cui $m >> n$, infatti $\mathrm{hypg}(n, a, m) \dot \sim \mathrm{bin}(n, \frac{a}{m})$.

Ha [[momenti/media]] $E(X) = \frac{na}{m}$ e una [[momenti/varianza]] $Var(X)$ che è poco meno di quella della [[binomiale]].

<img src="https://upload.wikimedia.org/wikipedia/commons/c/c1/HypergeometricPDF.png" alt="grafico della distribuzione" width=700>
