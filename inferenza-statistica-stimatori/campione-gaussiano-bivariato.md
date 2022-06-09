---
title: "Un campione gaussiano bivariato"
---
# Un campione bivariato
Questa casistica assomiglia molto a [[campioni-gaussiani-univariati|due campioni univariati]], tuttavia in questo caso la numerosità è la stessa ($n = m$) e i dati sono accoppiati (a formare [[vettori-aleatori|vettori aleatori]]).
Per cui avremo $(X_1, Y_1), \ldots, (X_n, Y_n)$ con
$$
(X_i, Y_i) \sim \mathcal{N} \bigg((\mu_X, \mu_Y),
\begin{pmatrix}
\sigma_X^2 & \gamma     \\
\gamma     & \sigma_Y^2 \\
\end{pmatrix}\bigg)
$$
Si noti che indicheremo con $\gamma$ è la [[covarianza]].

Dati di questo tipo possono essere, ad esempio, statura e peso di un insieme di persone.

Avremo quindi i seguenti stimatori: $\bar X \approx \mu_X$, $\bar Y \approx \mu_Y$, $S_X^2 \approx \sigma_X^2$, $S_Y^2 \approx \sigma_Y^2$ e $S_{XY} \coloneqq \frac{1}{n-1}\sum_{i = 1}^n (X_i - \bar X)(Y_i - \bar Y) \approx \gamma$ con $S_{XY}$ la [[covarianza]] campionaria.

Talvolta potrebbe capitare di dover usare anche il [[covarianza#Matrice di correlazione lineare di Pearson|coefficiente di correlazione lineare campionario]] definito come $r_{XY} \coloneqq \frac{S_{XY}}{S_X S_Y} = \frac{1}{n-1} \sum_{i = 1}^n \frac{X_i - \bar X}{S_X} \cdot \frac{Y_i - \bar Y}{S_Y}$. Si noti che con la seconda formula abbiamo anche standardizzato le variabili prima del prodotto. Inoltre, se uso la seconda formula otterrò che le variabili vengono standardizzate (e chiameremo le corrispondenti variabili standardizzate come $\tilde X$ e $\tilde Y$) e avremo anche che $S_{\tilde X \tilde Y} = r_{XY}$. Standardizzandole in questo modo i concetti di [[covarianza]] e [[covarianza#Matrice di correlazione lineare di Pearson|correlazione]] diventano coincidenti perchè abbiamo fissato che la [[varianza]] è $1$. Si noti che però capire quando è giusto farlo e quando non lo è viene con l'esperienza.
