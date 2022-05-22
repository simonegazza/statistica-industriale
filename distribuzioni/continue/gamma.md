---
title: "Gamma"
---
# Gamma
La gamma è una [[distribuzione]] di [[probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \mathrm{gamma}(\alpha, \lambda^2)$ o $X \sim \mathrm{gamma}(\alpha, \beta^2)$ in cui $\lambda = \frac{1}{\beta}$ con $\alpha, \lambda$ e $\beta$ maggiori di $0$. La seconda è usata su Excel.

La [[variabili-aleatorie#Continue|funzione di densità di probabilità]] è:
$$
P(X \le k) = \frac{1}{\Gamma(\alpha)} \lambda^\alpha t^{\alpha - 1} e^{-\lambda t} = \frac{1}{\Gamma(\alpha)} \beta^{-\alpha} t^{\alpha - 1} e^{-\frac{t}{\beta}}
$$

La **forma** è determinata da $\alpha$ mentre la **scala** da $\lambda \beta$.

Se $\alpha = 1$ allora la gamma generalizza l'[[esponenziale]], infatti $\mathrm{gamma}(1, \lambda) \sim \mathrm{expo}(\lambda)$. Si noti che sono **esattamente** uguali.

Se $\alpha = n \ge 1$ **intero** allora si chiama anche [[erlang]].

È [[riproducibile]] se $\lambda$ è fissato, infatti se $X \sim \mathrm{gamma}(\alpha_1, \lambda)$ e $Y \sim \mathrm{gamma}(\alpha_2, \lambda)$ allora $X + Y \sim \mathrm{gamma}(\alpha_1 + \alpha_2, \lambda)$.

Ha [[momenti/media]] $E(X) = \frac{\alpha}{\beta}$ e [[momenti/varianza]] $Var(X) = \frac{\alpha}{\beta^2}$.

<img src="https://upload.wikimedia.org/wikipedia/commons/e/e6/Gamma_distribution_pdf.svg" alt="grafico della distribuzione" width=700 style="background: white">
