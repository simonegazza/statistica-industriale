---
title: "Campioni bernoulliano"
---
# Un campione [[bernoulliana|bernoulliano]]
Supponiamo di avere un [[componenti-fondamentali-statistica|campione]] [[bernoulliana|bernoulliano]] $X_1, \ldots, X_n \sim \mathrm{bin}(1, p)$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]]. Sappiamo che, contando il numero di successi, per via del [[processo-bernoulli|processo di Bernoulli]] abbiamo che $X \coloneqq \sum_{i = 1}^n X_i \sim \mathcal{bin}(n, p)$.

Tuttavia quella elencata sopra non è una [[funzione-ancillare|funzione ancillare]], poichè ha più di un parametro incognito.

Allora, usando il [[teorema-limite-centrale|teorema del limite centrale]] dico che approssimo $p \approx \hat p \coloneqq \frac{X}{n} \dot \sim \mathcal{N}(p, \frac{p (1 - p)}{n})$, poi standardizzo e ottenendo che:
$$
\frac{\hat p - p}{\sqrt{\frac{p (1 - p)}{n}}} \dot \sim \mathcal{N}(0, 1)
\text{ e }
\frac{\hat p - p}{\sqrt{\frac{\hat p (1 - \hat p)}{n}}} \dot \sim \mathcal{N}(0, 1)
$$
