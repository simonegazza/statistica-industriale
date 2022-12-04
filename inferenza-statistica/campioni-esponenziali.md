---
title: "Campioni esponenziali"
---
# Un campione [[esponenziale]]
Supponiamo di avere $T_1, \ldots, T_n \sim \mathrm{expo}(\lambda)$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d.]] con $\lambda > 0$.
Lo [[componenti-fondamentali-statistica|stimatore]] per $\lambda \approx \frac{1}{\bar T}$ (oppure $\nu = E(T_i) \coloneqq \frac{1}{\lambda} = \bar T$)

La distribuzione dello [[componenti-fondamentali-statistica|stimatore]] $\bar T$ della [[media]] è
$$
\bar T \sim \mathrm{gamma}(\alpha = n, \beta = \frac{\nu}{n})
$$
Questa **NON** è una [[funzione-ancillare|funzione ancillare]] (perchè abbiamo due parametri incogniti), per ricavarla dobbiamo moltiplicare per $2\frac{n}{\nu}$ (basterebbe dividere per $\nu$ in realtà, ma moltiplicando anche per $2n$ ottengo una [[gamma]] un po' più speciale, ovvero una [[chi-quadro|chi quadro]]), quindi:
$$
2 \frac{n}{\nu} \bar T = 2 n \lambda \bar T \sim \mathrm{gamma}(\alpha = \frac{2n}{2}, \beta = 2) \sim \chi^2(2n)
$$

# Due campioni [[esponenziale|esponenziali]]
Supponiamo di avere $T_1, \ldots, T_m \sim \mathrm{expo}(\lambda_T)$ e $R_1, \ldots, R_n \sim \mathrm{expo}(\lambda_R)$

Useremo i rapporti fra le medie perchè queste hanno distribuzione [[chi-quadro|chi quadro]], in modo tale che ci vengano delle [[f-fisher|F di Fisher]], infatti dato che $\lambda_T \approx \frac{1}{\bar T}$ e $\lambda_R \approx \frac{1}{\bar R}$ allora abbiamo che $\frac{\lambda_T}{\lambda_R} \approx \frac{\bar R}{\bar T}$ e quindi
$$
\frac{\bar R}{\bar T} \cdot \frac{\lambda_R}{\lambda_T} \sim F(2n; 2m)
$$

Questa è anche una [[funzione-ancillare|funzione ancillare]].
