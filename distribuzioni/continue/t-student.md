---
title: "T di Student"
---
# T di Student
La T di Student è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \mathrm{t}(k)$ in cui $k \in \mathbb{N}^+$.

La [[variabili-aleatorie#Continue|funzione di densità di probabilità]] è:
$$
P(X \le k) = c_k(1 + \frac{1}{k}x^2)^{- \frac{k+1}{2}}
$$

Si noti che $\mathrm{t}(k) \xrightarrow[k \to +\infty]{} \mathcal{N}(0, 1)$

È possibile dare anche una definizione operativa, seconda la quale se $Z \sim \mathcal{N}(0, 1)$ e $W \sim \chi^2(k)$ [[indipendenza|indipendenti]], allora:
$$
    Z \cdot \bigg(\frac{W}{k}\bigg)^{-\frac{1}{2}} \sim \mathrm{t}(k)
$$

Ha [[media]] $E(X) = 0$ se $k > 1$ (non è definita altrimenti) e [[varianza]] $Var(X) = \frac{k}{k-2}$ se $k > 2$ (non è definita altrimenti).

<img src="https://upload.wikimedia.org/wikipedia/commons/4/41/Student_t_pdf.svg" alt="grafico della distribuzione" width=700 style="background: white">
