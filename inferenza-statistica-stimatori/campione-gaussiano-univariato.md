---
title: "Un campione gaussiano univariato"
---
# Un campione gaussiano univariato
Supponiamo di avere $X_1, \ldots, X_n$ con $X_i \sim \mathcal{N}(\mu, \sigma^2)$

## Media
$\mathcal{N}(\mu, \frac{\sigma^2}{n}) \sim \bar X \approx \mu$. Si noti che $\bar X$ ha la [[varianza]] ridotta rispetto alle $X_i$. Tipicamente poi si [[gaussiana|standardizza]] come
$$
\frac{\bar X - \mu}{\sigma} \sqrt{n} \sim \mathcal{N}(0, 1)
$$

Si noti che abbiamo diviso per $\frac{\sigma}{\sqrt{n}}$, perchè questa è la varianza di $\bar X$. Ricordiamo che $\bar X$ è lo stimatore della [[media]] perchè [[gaussiana|combinazione lineare di gaussiane]], e questo preserva la gaussianità.

Questa può essere usata anche come [[funzione-ancillare|funzione ancillare]].

## Varianza o deviazione standard
$S_X^2 \approx \sigma^2$ e sappiamo che $\frac{S_x^2}{\sigma}(n-1) \sim \chi^2(n-1)$ dal [[teorema-cochran|teorema di Cochram]] e [[indipendenza|indipendente]] da $\bar X$ visto sopra.
Anche questa può essere usata come [[funzione-ancillare|funzione ancillare]] per $\sigma$ o $\sigma^2$.

Possiamo usare un'altra [[funzione-ancillare|funzione ancillare]] per $\sigma$ (è un caso raro ma può capitare): bisogna prima definire la deviazione standard [[componenti-fondamentali-statistica#Stimatore corretto|distorta]] $\tilde S_X = \sqrt{\frac{1}{n}\sum(X_i - \mu)^2}$ e otteniamo
$$
\frac{\tilde S_X}{\sigma^2} n \sim \chi^2(n)
$$

## t di Student
Possiamo sostituire a $\sigma$ il $S_X$ all'interno di $\frac{\bar X - \mu}{\sigma} \sqrt{n}$ e ottenere una [[t-student|t di Student]]
$$
\frac{\bar X - \mu}{S_X} \sqrt{n} \sim t(n-1)
$$

Questa in particolare è una [[funzione-ancillare|funzione ancillare]] per $\mu$.

Questo perchè al crescere di $n$ avremo che $S_X$ approssima sempre meglio $\sigma$. Infatti si noti che $\mathcal{N}(0, 1) \dot \sim t(\nu-1)$.

La dimostrazione formale avviene perchè
$$
\frac{\bar X - \mu}{\sigma} \sqrt{n} \cdot \frac{\sigma}{S_X} = \frac{\bar X - \mu}{\sigma} \sqrt{n} \cdot \sqrt{\frac{n - 1}{\frac{S_X^2}{\sigma^2} (n-1)}} \stackrel{def.}{\sim} t(n-1)
$$
