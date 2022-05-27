---
title: "Bernoulliana"
---
# Bernoulliana
La Bernoulliana è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie|discrete]].

Si indica con $X \sim \mathrm{bin}(1, p)$ in cui il parametro $p \in [0,1]$ indica la [[probabilita|probabilità]] del verificarsi di un singolo [[evento]] (una sola volta).

Questa [[distribuzione]] ha solo due valori possibili: $0$ o $1$. Se l'[[evento]] si verifica, la bernoulliana avrà valore $1$, se non si verifica avrà valore $0$. Quindi:
$$
\mathrm{bin}(1,p) = \bigg\{
    \begin{array}{lr}
        p & \text{for } P(X = 1)\\
        1-p & \text{for } P(X = 0)
    \end{array}
$$

Si noti che il [[processo-bernoulli|processo di Bernoulli]] ci consente di trasformare $n$ ripetizioni della stessa Bernoulliana (avente la stessa probabilità $p$) in una [[binomiale]], sommando le ripetizioni.

Ha [[media]] $E(X) = p$ e [[varianza]] $Var(X) = p(1-p)$.

<img src="https://upload.wikimedia.org/wikipedia/commons/7/74/Bernoulli_Distribution.PNG" alt="grafico della distribuzione" width=700>
