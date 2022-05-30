---
title: "Covarianza"
---
# Covarianza
Non è propriamente un [[momenti-distribuzioni|momento di una distribuzione]], ma è  definita come:
$$
    Cov(X, Y) \coloneqq E((X - E(X)) \cdot (Y - E(Y))) = E(XY) - E(X) E(Y)
$$

Ha le seguenti proprietà:
- Se $X, Y$ [[indipendenza|indipendenti]] allora $Cov(X, Y) = 0$ (che è il motivo per cui nella [[media]] e nella [[varianza]] se le due variabili sono [[indipendenza|indipendenti]] non si ha il contibuto della covarianza)
- Se $Cov(X, Y) = 0$ allora diremo che $X, Y$ sono scorrelate (**ATTENZIONE**: non è vero il viceversa, quindi scorrelate **non** vuol dire che sono indipendenti)
- $Cov(X, Y) = Cov(Y, X)$
- Tipicamente $Var(X + Y) = Var(X) + Var(Y) + Cov(X, Y)$ quando $X, Y$ non sono [[indipendenza|indipendenti]]
- Tipicamente $E(X Y) = E(X) E(Y) + Cov(X, Y)$ quando $X, Y$ non sono [[indipendenza|indipendenti]]
- $|Cov(X, Y)| \le \sqrt{Var(Y) Var(X)}$
- $Cov(X, X) = Var(X)$ con $Var(X)$ la [[varianza]] di $X$