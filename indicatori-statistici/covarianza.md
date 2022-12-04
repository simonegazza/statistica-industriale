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

# Matrice di correlazione lineare di Pearson
Si tratta di un particolare riscalamento di $C(X)$ tale che le componenti siano tutte confrontabili e abbiano tutte la stessa scala in un range $[-1, 1]$ (per via della disuguaglianza di Cahucy - Schwartz).

Sfrutta il coefficiente di correlazione lineare che è definito come $\rho(X, Y) = \frac{Cov(X, Y)}{\sqrt{Var(X) Var(Y)}}$, infatti la matrice di correlazione di Pearson è il coefficiente di correlazione lineare fra tutte le variabili:
$$
\begin{pmatrix}
\rho(X_1, X_1) & \rho(X_1, X_2) & \ldots & \rho(X_1, X_n) \\
\rho(X_2, X_1) & \rho(X_2, X_2) & \ldots & \rho(X_2, X_n) \\
\vdots      &             & \ddots & \vdots      \\
\rho(X_n, X_1) & \rho(X_n, X_2) & \ldots & \rho(X_n, X_n) \\
\end{pmatrix},
$$

Si noti che $\rho(X, Y)$ è invariante per trasformazione lineare delle componenti.

Quando trattiamo il coefficiente di correlazione lineare [[inferenza-statistica|campionario]] si segna come $r_{XY}$. Si noti che si chiama così perchè ha valore $1$ (o $-1$) quando la correlazione fra le variabili è **esattamente** lineare positiva (negativa). Si noti che, però, un valore più piccolo (grande) di $1$ ($-1$) non indica dipendenza lineare ma comunque indica una dipendenza.
