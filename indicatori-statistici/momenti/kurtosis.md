---
title: "Kurtosis"
---
# Kurtosis
La kutosis è il [[momenti-distribuzioni|momento quarto centrato]] ed è definito come:
$$
    kr(X) = \frac{E((X - E(X))^4)}{Var(X)^2} \\
    \text{ oppure } \\
    kr(X) = \frac{E((X - E(X))^4)}{Var(X)^2} - 3
$$

Vi sono due formule perchè talvolta si decide di sottrarre $3$ che è il valore di kurtosis della gaussiana. Questo viene fatto poichè così si è in grado di confrontare direttamente con la gaussiana nel caso in cui venga più o meno di zero.

Si noti che non è lineare e neanche quadratica, in particolare: $kr(aX + b) = kr(X)$.

Si noti che non dipende dalla posizione (sull'asse delle ascisse) della [[distribuzione]], poichè è stata centrata e non dipende dalla larghezza della [[distribuzione]] poichè è standardizzata.

Indica quanto è "piatta" la [[distribuzione]] sulla [[media]], infatti:
<img src="https://www.johndcook.com/generalized_normal_thick.svg" alt="grafico della distribuzione" width=700>
