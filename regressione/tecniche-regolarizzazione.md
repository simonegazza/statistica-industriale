---
title: "Tecniche di regolarizzazione per la regressione"
---
# Tecniche di regolarizzazione per la regressione
Non sempre è possibile ricavare $\bold{B}$ in maniera algebrica (ad esempio quando la matrice $\bold{X}$ non ha rango massimo e quindi non è invertibile per poter trovare $\bold{B}$), quindi è possibile usare un ottimizzatore iterativo e imporre condizioni su questo iteratore. In particolare, il compito dell'iteratore sarà minimizzare, passo per passo, il calcolo $\bold{B} = (\bold{X}^T\bold{X})^{-1}\bold{X}\bold{B}$ con $\bold{B}$ incognito.

## Regolarizzazione $l^q$
Posso pensare che, invece di minimizzare solo $SS_R$ come faccio di solito, posso regolarizzare
$$
SS_R + \lambda \sum_{i = 0}^p |B_i|^q
$$
dove:
- se $q = 1$ sto facendo una regressione *LASSO (Least Absolute Shrinkage and Selection Operator)*, in cui pongo il vincolo che $\sum_{i = 0}^p |B_i| \le \alpha$ con $\alpha$ iperparametro. In particolare in questo caso c'è anche un effetto di selezione delle variabili (perchè diversi $B_i$ saranno a zero al minimo)
- se $q = 2$ faccio una regressione *RIDGE regression*

È importante notare che gli *iperparametri* $\alpha$ e $\lambda$ vanno scelti con cura. Tipicamente si usano i test di validazione e si fanno diverse prove.
Per fare in modo che questi coefficienti abbiano senso, **bisogna prima [[standardizzare]] tutti i $B_i$**.