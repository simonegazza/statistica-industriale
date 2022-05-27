---
title: "Chi-quadro"
---
# Chi-quadro
La chi-quadro è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \chi^2(k)$ in cui $k$ è il numero di gradi di libertà (g.d.l.).

In realtà è un caso speciale della [[gamma]] in cui $\alpha = \frac{k}{2}$ e $\lambda = \frac{1}{2}$ o $\beta = 2$, quindi $X \sim \mathrm{gamma}(\frac{k}{2}, \frac{1}{2})$.

Si noti che se $Z$ è [[gaussiana|gaussiana standard]] (ovvero $Z \sim \mathcal{N}(0, 1)$) allora $Z^2 \sim \chi^2(1) \sim \gamma(\frac{1}{2}, \frac{1}{2})$.

È possibile dare anche una definizione operativa della chi-quadro: se ho $Z_1, Z_2, \ldots, Z_k \sim \mathcal{N}(0, 1)$ [[gaussiana|gaussiane standard]] [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]], allora $Z_1^2 + Z_2^2 + \ldots + Z_k^2 \sim \chi^2(k)$.

Ha [[media]] $E(X) = k$ e [[varianza]] $Var(X) = 2k$.
<img src="https://upload.wikimedia.org/wikipedia/commons/c/c5/Chi-square_distributionPDF.svg" alt="grafico della distribuzione" width=700 style="background: white">
