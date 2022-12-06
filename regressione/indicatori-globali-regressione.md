---
title: "Indicatori globali per la regressione"
---
# Indicatori globali per la regressione
Servono a valutare la bontà del modello dato un insieme di variabili.

Si noti che comunque tipicamente tutte queste stime concordano fra di loro.

## Coefficiente di determinazione $R_D^2$
E' un coefficiente che esprime la quantità di varianza **spiegata** dal modello:
$$
R_D^2 = 1 - \frac{SS_R}{SS_Y}
$$
con $SS_R = \sum_{i = 1}^n (Y_i - [XB]_i)^2 = \sum_{i = 1}^n R_i^2$ e $SS_Y = \sum_{i = 1}^n (Y_i - \bar Y)^2 = \sum_{i = 1}^n Y_i^2 - n \bar Y$

Ovviamente il coefficiente $\frac{SS_R}{SS_Y}$ ci dice la quantità di varianza *non spiegata* dal modello. In altri termini è la frazione della devianza delle $Y_i$ che rimane non spiegata nonostante le $x_i$

Al crescere del numero di variabili, $R^2_D$ aumenta sempre e ottengo $R^2_D$ massimo quando ci sono tutte le variabili in gioco.

Data la sua natura che tende ad aumentare sempre, questo indicatore **non va bene per la selezione delle variabili**

## Coefficiente di determinazione corretto (o adjusted) $R_A^2$
Si misura con
$$
R_A^2 = 1 - \frac{S_e^2}{S_Y^2}
$$
con $S_e^2 \coloneqq \frac{SS_R}{n - p - 1}$ e $S_Y^2 \coloneqq \frac{1}{n - 1} \sum_{i = 1}^n (Y_i - \bar Y)^2 = \frac{1}{n-1} SS_Y$

Questo indicatore non è monotono al crescere del numero di variabili, infatti $R^2_A$ è massimo solo quando il $S_e^2$ è minimo. Rappresenta quindi una stima migliore della bontà del modello di $R_D^2$.

Si noti tuttavia che $S_e^2$ rappresenta un valore casuale, infatti $\frac{S^2_e}{\sigma^2} (n - k - 1) \sim \chi^2(n - k - 1)$ (con $k$ numero di variabili da rimuovere).
