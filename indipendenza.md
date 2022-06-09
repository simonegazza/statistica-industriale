---
title: "Indipendenza"
---
# Indipendenza di variabili aleatorie
Consideriamo due [[variabili-aleatorie|v.a.]] $X$ e $Y$. Diremo che sono indipendenti se il realizzarsi di $X$ non modifica in alcun modo (la [[probabilita|probabilità]]) del realizzarsi di $Y$.

Ovvero quando la probabilità di $P(A|B) = P(A)$ e $P(B|A) = P(B)$.

Si noti che questo vuol dire che $P(A \cap B) = P(A) P(B)$

# Indipendenti e identicamente distribuite
Una sequenza di [[variabili-aleatorie|variabili aleatorie]] è detta indipendente e identicamente distribuita (abbreviato in i.i.d.) se:
- le [[variabili-aleatorie|variabili]] hanno tutte la stessa [[distribuzione|distribuzione di probabilità]];
- le [[variabili-aleatorie|variabili]] sono tutte indipendenti.

# Dimostrare l'indipendenza di variabili
Vorremmo poter avere un modo di dire che due variabili sono indipendenti in qualche modo (in un caso [[gaussiana|gaussiano]]). Tipicamente avendo a che fare con [[distribuzione|distribuzioni]], è normale che il calcolo della [[covarianza]] fra due variabili non sia esattamente $0$, anche se molto probabilmente queste due variabili sono scorrelate.
Tuttavia possiamo affermare che, per $n>>1$ le oscillazioni di $r_{XY}$ siano approssimativamente dell'ordine di $\sqrt{n}$, in particolare possiamo dire che:
$$
r_{XY} \cdot \sqrt{n - 3} \dot \sim \mathcal{N}(0, 1)
$$
con $r_{XY}$ il [[covarianza#Matrice di correlazione lineare di Pearson|coefficiente di correlazione lineare campionario]].
Questo ci da una misura spannometrica dell'indipendenza di due variabili.
Quindi sempre spannometricamente, seguendo quanto scritto sopra, se $|r_{XY}| \lesssim \frac{2}{\sqrt{n}}$ allora possiamo concludere che sono indipendenti

Se avessimo il [[covarianza#Matrice di correlazione lineare di Pearson|coefficiente di correlazione lineare]] vero $\rho = \rho(X, Y) = \frac{\gamma}{\sigma_X \sigma_Y}$ (con $\gamma$ la [[covarianza]] otteniamo che
$$
r_{XY} \dot \sim  \mathcal{N}(\rho, \frac{1}{n-3})
$$
