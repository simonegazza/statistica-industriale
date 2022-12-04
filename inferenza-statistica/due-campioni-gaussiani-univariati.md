---
title: "Due campioni univariati"
---
# Due campioni univariati
Supponiamo di avere $X_1, \ldots, X_m$ con $X_i \sim \mathcal{N}(\mu_X, \sigma_X^2)$ e $Y_1, \ldots, Y_n$ con $Y_i \sim \mathcal{N}(\mu_Y, \sigma_Y^2)$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d.]]
Avremo che $\bar X \approx \mu_X$, $\bar Y \approx \mu_Y$, $S_X^2 \approx \sigma^2_X$ e $S_Y^2 \approx \sigma^2_Y$

Si noti che per ciascuno di questi [[inferenza-statistica|campioni]] possiamo applicare le cose dette nel caso di [[campione-gaussiano-univariato|un singolo campione univariato]], ora però possiamo ragionare sul confronto fra le [[media|medie]] o [[varianza|varianze]] di queste.

Per confrontarle si preferisce sottrarre (o farne il rapporto) e cercare di valutare il loro comportamento.

## Confronto fra le medie
Si noti che $\bar X \sim \mathcal{N}(\mu_X, \frac{\sigma_X^2}{m})$ e $\bar Y \sim \mathcal{N}(\mu_Y, \frac{\sigma_Y^2}{n})$ [[indipendenza|indipendenti]] e che $\bar X - \bar Y \approx \mu_X - \mu_Y$

Da qui possiamo dire che $\bar X - \bar Y \sim \mathcal{N}(\mu_X - \mu_Y, \frac{\sigma_X^2}{m} + \frac{\sigma_Y^2}{n})$

Posso provare a [[gaussiana|standardizzare]] la [[funzione-ancillare|funzione ancillare]] sopra che diventa:
$$
\frac{\bar X - \bar Y - (\mu_X - \mu_Y)}{\sqrt{\frac{\sigma^2_X}{m} + \frac{\sigma^2_Y}{n}}} \sim \mathcal{N}(0, 1)
$$
tuttavia questo è un caso raro perchè richiede $\sigma_X$ e $\sigma_Y$ note.

### Caso speciale: [[varianza|omoschedastico]] $\sigma_X = \sigma_Y = \sigma$
Riprendendo la formula di prima e raccogliendo possiamo scrivere:
$$
    \frac{\bar X - \bar Y - (\mu_X - \mu_Y)}{\sigma \sqrt{\frac{1}{m} + \frac{1}{n}}} \sim \mathcal{N}(0, 1)
$$

Ora posso anche sostiuire a $\sigma^2$ uno [[inferenza-statistica|stimatore]] (e in questo caso va bene sia $S^2_X$ che $S^2_Y$). Tuttavia voglio essere il più preciso possibile e non voglio scegliere uno dei due a priori, quindi ne vorrei fare una media.

Una semplice media aritmetica però non è corretta perchè la precisione di questi stimatori dipende dalla [[inferenza-statistica|numerosità]] dei rispettivi [[inferenza-statistica|campioni]], che non sono necessariamente equivalenti.

Utilizzerò una media pesata della forma $S_p \coloneqq \theta_X S_X + \theta_Y S_Y$ con $\theta_X + \theta_Y = 1$ (e questo rimane [[inferenza-statistica#Stimatore corretto|corretto]] e [[inferenza-statistica#Stimatore consistente|consistente]] perchè è una combinazione lineare di [[inferenza-statistica|stimatori]] [[inferenza-statistica#Stimatore corretto|corretti]] e [[inferenza-statistica#Stimatore consistente|consistenti]]).

Ora si tratta di assegnare il peso corretto a ciascuno dei due [[inferenza-statistica|stimatori]]. Dato che comunque il risultato sarà uno [[inferenza-statistica#Stimatore corretto|stimatore corretto]] e [[inferenza-statistica#Stimatore consistente|consistente]], vorrei prendere quello che ha varianza minore fra tutti quelli disponibili. Per farlo prendo $\theta_X \propto m - 1$ e $\theta_X \propto n - 1$ che si rivela essere:
$$
\theta_X = \frac{m - 1}{m + n - 2} \text{ e } \theta_Y = \frac{n - 1}{m + n - 2}
$$

$S_p$ è detto [[inferenza-statistica|stimatore]] **pooled**, quindi
$$
S_p^2 = \frac{m - 1}{m + n - 2} S_X^2 + \frac{n - 1}{m + n - 2} S_Y^2
$$

Dello [[inferenza-statistica|stimatore]] pooled possiamo anche trovarne la distribuzione: partendo da $\frac{S_X^2}{\sigma^2}(m-1) \sim \chi^2(m-1)$ e da $\frac{S_Y^2}{\sigma^2}(n-1) \sim \chi^2(n-1)$ e sapendo che sono [[indipendenza|indipendenti]], allora possiamo sommarle perchè le [[chi-quadro|chi quadro]] sono riproducibili, quindi
$$
\frac{S_p^2}{\sigma^2}(m + n - 2) = \frac{S_X^2}{\sigma^2}(m-1) + \frac{S_Y^2}{\sigma^2}(n-1) \sim \chi^2(m + n - 2)
$$

Possiamo tornare all'intento originario (cioè sostituire a $\sigma$ il mio nuovo $S_p$); devo assicurarmi però che la [[chi-quadro]] associata allo [[inferenza-statistica|stimatore]] della [[varianza]] e la [[gaussiana|gaussiana standard]] per la stima della [[media]] siano [[indipendenza|indipendenti]].

Per il [[teorema-cochran|teorema di Cochran]] su $X$ so che $\bar X$ è [[indipendenza|indipendente]] da $S_X$ e applicandolo su $Y$ ho la conferma che $\bar Y$ è [[indipendenza|indipendente]] da $S_Y$. Si noti che so anche che poi queste stime sono [[indipendenza|indipendenti]] fra di loro (a due a due) perchè il [[inferenza-statistica|campione]] di dati $X$ e $Y$ sono [[indipendenza|indipendenti]] per ipotesi. Quindi $\bar X, \bar Y$ e $S_p$ sono [[indipendenza|indipendenti]].

Posso finalmente concludere che
$$
\frac{\bar X - \bar Y - (\mu_X - \mu_Y)}{S_p\sqrt{\frac{1}{m} + \frac{1}{n}}} \sim t(m + n - 2)
$$
[[funzione-ancillare|funzione ancillare]] per $\mu_X - \mu_Y$ nel caso [[varianza|omoschedastico]].

Si noti in questi caso, avendo a disposizione due [[inferenza-statistica|campioni]] [[varianza|omoschedastici]], possiamo usare lo [[inferenza-statistica|stimatore]] pooled al posto dello [[inferenza-statistica|stimatore]] semplice di $S_X$, così da ottenere una precisione maggiore. Otteniamo quindi $\frac{\bar X - \mu_X}{S_p}\sqrt{m} \sim t(m + n - 2)$. Si noti che i gradi di libertà della [[t-student|t di Student]] sono rimasti gli stessi (perchè si usa sempre il numero di gradi di libertà corrispondenti a quelli dello [[inferenza-statistica|stimatore]] di $\sigma$ utilizzato) ma usiamo uno [[inferenza-statistica|stimatore]] pooled.

Nota: poter utilizzare lo [[inferenza-statistica|stimatore]] pooled con la [[media]] dei campioni di una sola delle due [[distribuzione|distribuzioni]] non deve sconvolgere, infatti in questo modo otteniamo uno [[inferenza-statistica|stimatore]] migliore per la stessa [[varianza]] (che usa infatti anche i dati di un'altra distribuzione per essere più preciso), ma bisogna tenere sempre conto che stiamo facendo inferenza solo su una delle due medie.

### Caso non-omoschedastico $\sigma_X \not = \sigma_Y$
Semplicemente come già visto
$$
\frac{\bar X - \bar Y - (\mu_X - \mu_Y)}{\sqrt{\frac{\sigma^2_X}{m} + \frac{\sigma^2_Y}{n}}} \sim \mathcal{N}(0, 1)
$$

#### Caso $m, n >>1$
Nei casi il cui la numerosità dei dati è alta c'è poca differenza fra un [[gaussiana|gaussiana standard]] e una [[t-student|t di Student]], per cui scegliamo una delle due (e spesso sceglieremo la [[gaussiana|gaussiana standard]]), per cui possiamo dire che
$$
\frac{\bar X - \bar Y - (\mu_X - \mu_Y)}{\sqrt{\frac{S^2_X}{m} + \frac{S^2_Y}{n}}} \dot \sim \mathcal{N}(0, 1)
$$
Si noti che non va esattamente come una [[gaussiana|gaussiana standard]] ma approssimiamo la [[distribuzione]] in questo modo (perchè stiamo usando le [[varianza|varianze]] [[inferenza-statistica|campionarie]] e non quelle esatte).

## Confronto fra le varianze
Ricordiamo che $\bar X \sim \mathcal{N}(\mu_X, \frac{\sigma_X^2}{m})$ e $\bar Y \sim \mathcal{N}(\mu_Y, \frac{\sigma_Y^2}{n})$ [[indipendenza|indipendenti]].

Siamo interessati al caso in cui $\sigma_X = \sigma_Y \implies \frac{\sigma_X}{\sigma_Y} = 1$.

Piccola nota: non sembra ci sia una vera ragione per la quale si preferisca fare i rapporti e non le differenze per le varianze, forse perchè entrambi sono positivi.

Lo [[inferenza-statistica|stimatore]] di cui siamo interessati è $\frac{S_X}{S_Y} \approx \frac{\sigma_X}{\sigma_Y}$. La sua [[distribuzione]] è
$$
\frac{S_X^2}{\sigma_X^2} \frac{\sigma_Y^2}{S_Y^2} \sim F(m-1; n-1)
$$
con $F$ la [[f-fisher|F di Fisher]] (creata appositamente per queste occasioni), che è la [[funzione-ancillare|funzione ancillare]] per $\frac{\sigma_X}{\sigma_Y}$.
