---
title: "Triangolare"
---
# Triangolare
La triangolare è una [[distribuzione]] di [[probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \Tau(a, b, c)$, con $a$ e $b$ gli estremi (destro e sinistro rispettivamente) della distribuzione e $c$ la moda della distribuzione.

Viene usata spesso per stimare il minimo, il massimo e la moda quando si hanno pochi dati.

La [[variabili-aleatorie#Continue|funzione di densità di probabilità]] è:
$$
f(x) =
\begin{cases}
    \frac{2}{b - a} \frac{x - a}{c - a} \quad a \le x < c \\
    \frac{2}{b - a} \quad x = c \\
    \frac{2}{b - a} \frac{b - x}{b - c} \quad c < x \le b
   \end{cases}
$$

Date due [[variabili-aleatorie#Continue|vv.aa. continue]] $X, Y \sim \mathrm{unif}(0,1)$ uniformi fra $[0, 1]$, possiamo dire che:
- se $Z \sim \Tau(0, 2, 1)$ allora $Z = X + Y$
- se $Z \sim \Tau(-1, 1, 0)$ allora $Z = X - Y$
- se $Z \sim \Tau(0, 1, 0)$ allora $Z = |X - Y|$

Ha [[media]] $E(X) = \frac{1}{3}(a + b + c)$ e [[varianza]] $Var(X) = \frac{1}{18} (a^2 + b^2 + c^2 - ab - ac - bc)$.

<img src="https://upload.wikimedia.org/wikipedia/commons/4/45/Triangular_distribution_PMF.png" alt="grafico della distribuzione" width=700 style="background: white">
