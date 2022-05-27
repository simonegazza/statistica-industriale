---
title: "Delta di Dirac"
---
# Delta di Dirac
La delta di Dirac è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \delta(a)$ con $a \in \mathbb{R}$.

È definita tramite convoluzione con un'altra funzione $g(x)$, in modo tale che la convoluzione fra la delta di Dirac e la funzione $g$ ritorni la funzione $g$ stessa, ovvero:
$$
(\delta * g)(x) = \int_{-\infty}^{+\infty} \delta(x - \alpha) g(\alpha) d\alpha = g(\alpha)
$$
Si noti che non esiste un'espressione in forma chiusa di tale funzione. Tuttavia, facendo un abuso di notazione, potremmo scrivere che:
$$
\delta(x) = \begin{cases}
    0 \quad x \neq a \\
    +\infty \quad x = a
   \end{cases}
$$

Si noti che rispetta le seguenti proprietà:
- è lineare
- $\delta(a) = \delta(-a)$
- $\int_{-\infty}^{+\infty} \delta(x) dx = 1$

In particolare ci aspetteremmo che (dato che differisce dalla funzione identicamente nulla in un solo punto, ovvero un insieme di misura nulla) il suo integrale abbia valore $0$, tuttavia non è così.

Grazie a questa proprietà rappresenta il ponte di collegamento fra le [[distribuzione|distribuzione discrete]] e le [[distribuzione|distribuzioni continue]]. Infatti è possibile applicare ad una [[distribuzione|distribuzione discreta]] una quantità infinitamente non-numerabile di delta di Dirac e ottenere una [[distribuzione|distribuzione discreta]]. Risulta molto utile anche per le [[variabili-aleatorie|vv.aa. miste]], rendendole così trattabili in maniera continua.

Ha [[media]] $E(X) = a$ e [[varianza]] $Var(X) = 0$.

<img src="https://upload.wikimedia.org/wikipedia/commons/7/78/Dirac_distribution_PDF.png" alt="grafico della distribuzione" width=700 style="background: white">
