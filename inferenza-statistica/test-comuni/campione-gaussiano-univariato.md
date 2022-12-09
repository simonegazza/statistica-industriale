---
title: "Un campione gaussiano univariato"
---
# Un [[inferenza-statistica|campione]] gaussiano univariato
Supponiamo di avere $X_1, \ldots, X_n$ con $X_i \sim \mathcal{N}(\mu, \sigma^2)$

## Inferenza sulla media
$\mathcal{N}(\mu, \frac{\sigma^2}{n}) \sim \bar X \approx \mu$. Si noti che $\bar X$ ha la [[varianza]] ridotta rispetto alle $X_i$. Tipicamente poi si [[gaussiana|standardizza]] come
$$
\frac{\bar X - \mu}{\sigma} \sqrt{n} \sim \mathcal{N}(0, 1)
$$

Si noti che abbiamo diviso per $\frac{\sigma}{\sqrt{n}}$, perchè questa è la varianza di $\bar X$. Ricordiamo che $\bar X$ è lo [[inferenza-statistica|stimatore]] della [[media]] perchè [[gaussiana|combinazione lineare di gaussiane]], e questo preserva la gaussianità.

Questa può essere usata anche come [[funzione-ancillare|funzione ancillare]] se $\sigma$ è nota a priori.

Tipicamente tuttavia la varianza non è nota a priori. Per questo si usa
$$
\frac{\bar X - \mu}{S_X} \sqrt{n} \sim t(n - 1)
$$
con $S_X$ la varianza campionaria.

Si noti che in questo ultimo caso, se $n>>1$ allora vi è poca differenza fra $\sigma$ e $S_X$ e quindi $\sigma \approx S_X \implies \mathcal{N}(0, 1) \sim t(n - 1)$.

La dimostrazione formale si ottiene da $Z \coloneqq \frac{\bar X - \mu}{\sigma} \sqrt{n}, T \coloneqq \frac{\bar X - \mu}{S_X} \sqrt{n}$ e $W \coloneqq \frac{S_X^2}{\sigma^2}(n - 1)$ allora
$$
T = Z \cdot \frac{\sigma}{S_X} = Z \cdot \sqrt{\frac{n-1}{W}}
$$
che è la definizione di un $t(n - 1)$ [[t-student|t di Student]] con $(n - 1)$ gradi di libertà


## Inferenza sulla varianza o deviazione standard
Possiamo usare un'altra [[funzione-ancillare|funzione ancillare]] per $\sigma$ (è un caso raro ma può capitare): bisogna prima definire la deviazione standard [[inferenza-statistica#Stimatore corretto|distorta]] $\tilde S_X = \sqrt{\frac{1}{n}\sum_{i = 1}^n(X_i - \mu)^2}$ e otteniamo
$$
\frac{\tilde S_X^2}{\sigma^2} n \sim \chi^2(n)
$$
