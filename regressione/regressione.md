---
title: "Regressione"
---
# Regressione
L'idea generale della regressione è quella di avere una serie di punti $\bold{X}$ e dei loro risultati $Y$ affetti da rumore; quello che vogliamo è cercare di carpirne la legge che li genera.
Tipicamente quindi, andremo a stimare il *vettore di risposta* (ovvero dei risultati)
$$
\bold{Y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_p x_p + e 
$$
$$
\bold{Y} = \bold{X\beta} + e
$$
$$
\bold{Y} \sim \mathcal{N}(\bold{X\beta}; \sigma^2 \bold{I})
$$
dove:
- $\bold{Y} \in \mathbb{R}^n$ [[vettori-aleatori|vettore aleatorio]] di [[gaussiana|gaussiane]]
- $\beta \in \mathbb{R}^{p+1}$ sono i coefficienti
- $\bold{X} \in M_{n, p+1}$ dati, detti *livelli d'ingresso*, composto da $x_i \in \mathbb{R}^n$
- $p$ il numero di caratteristiche per ogni livello d'ingresso
- $n$ il numero di punti
- $I \in M_{n,n}$ matrice identità
- $\sigma$ incognita

Riusciremo attraverso questo framework non solo a capire la legge che lega $\bold{X}$ e $\bold{Y}$, ma anche a capire se determinate caratteristiche sono inutili e arrivare a prevedere, sia puntualmente che con un intervallo di confidenza, dei punti futuri.

Cominceremo da un esempio semplice, quello della *regressione lineare semplice*, andando poi progressivamente a riproporre i concetti alzando in complicatezza e dimensione progressivamente.

## Regressione lineare semplice
Supponiamo di avere un [[campione-gaussiano-bivariato|campione bivariato]] costituito dai punti $(x_1, y_1), (x_2, y_2), \ldots, (x_n, y_n) \in \mathbb{R}^2$, avremo che
$$
Y = \beta_0 + \beta_1 x + e
$$
con $e \sim \mathcal{N}(0; \sigma^2)$ e $\sigma$ incognita. Si noti che è possibile, alternativamente, esprimere $Y$ anche in questo modo:
$$
Y \sim \mathcal{N}(\beta_0 + \beta_1 x_1; \sigma^2)
$$
Come si può notare quindi, tipicamente si lavora sotto l'ipotesi di [[varianza|omoschedasticità]].
Si noti che $x$ viene scelta come la *causa* (perchè deve essere la variabile indipendente), mentre $Y$ è scelta come *effetto* (perchè variabile dipendente).

<img src="https://miro.medium.com/max/1200/1*N1-K-A43_98pYZ27fnupDA.jpeg" width=700>

### Parametri e stimatori per la regressione lineare semplice
Abbiamo 3 parametri incogniti che sono $\beta_0, \beta_1$ e $\sigma^2$. Denotiamo i loro [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] rispettivamente con $B_0, B_1, S_e^2$. Possiamo cercare ora di ricavare le loro formule a partire dal [[teorema-cochran|teorema di Cochran]]: il nostro modello prevede di prende $\bold{Y} = (Y_1, Y_2, \ldots, Y_n)$ con le $Y_i \sim \mathcal{N}(\beta_0 + \beta_1 x_i; \sigma^2)$ tutti indipendenti fra di loro.
Quindi abbiamo che $\bold{Y} \sim \mathcal{N}(\bold{\mu}; \sigma^2 \bold{I})$ con $\bold{\mu} = (\beta_0 + \beta_1 x_1, \beta_0 + \beta_1 x_2, \ldots, \beta_0 + \beta_1 x_n) = \beta_0 (1, 1, \ldots, 1)_{1\times n} + \beta_1 (x_1, x_2, \ldots, x_n)$. Quindi se nominiamo $e = (1, 1, \ldots, 1)_{1\times n}$ abbiamo che
$$
\bold{\mu} = \beta_0 \bold{e} + \beta_1 \bold{x}
$$
dove ricordiamo $\bold{e}, \bold{x} \in \mathbb{R}^n$ e $\beta_0, \beta_1 \in \mathbb{R}$.
Quindi possiamo dire che $\bold{\mu} \in V$ dove $V \coloneqq \mathrm{Span}(\bold{e}, \bold{x})$ sottospazio vettoriale di dimensione $2$. Quindi tutte le medie degli $Y_i$ appartengono al sottospazio $V$; questo verifica le ipotesi del [[teorema-cochran|teorema di Cochran]]. Sappiamo quindi che il [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] sarà il punto $\hat \mu = \pi_V(Y) \in V$ che minimizza la distanza da $Y$, ovvero:
$$
\hat \mu \coloneqq \argmin_{\mu \in V} \| Y - \mu \|^2
$$

Possiamo procedere con i conti:
$$
\varphi(B_0, B_1) = \| Y - \mu \|^2 = \sum_{i = 1}^n (Y_i - \mu_i)^2 = \sum_{i = 1}^n [Y_i - (B_0 + B_1 x_i)]^2 = \sum_{i = 1}^n (Y_i - B_0 - B_1 x_i)^2 \\
\frac{\partial}{\partial B_0}\varphi(B_0, B_1) = 0 \qquad \frac{\partial}{\partial B_1}\varphi(B_0, B_1) = 0 \\
\frac{\partial}{\partial B_0} \sum_{i = 1}^n (Y_i - B_0 - B_1 x_i)^2 = 0 \qquad \frac{\partial}{\partial B_1} \sum_{i = 1}^n (Y_i - B_0 - B_1 x_i)^2 = 0 \\
-2 \sum_{i = 1}^n (Y_i - B_0 - B_1 x_i) = 0 \qquad -2 \sum_{i = 1}^n x_i (Y_i - B_0 - B_1 x_i) = 0 \\
\text{divido per } n \text{ entrambe le equazioni}\\
\bar Y - B_0 - B_1 \bar x = 0 \qquad \overline{Yx} - B_0\bar{x} - B_1 \overline{x^2} = 0 \\
B_0 = \bar Y - B_1 \bar x \qquad \overline{Yx} - (\bar Y - B_1 \bar x)\bar{x} - B_1 \overline{x^2} = 0 \\
B_0 = \bar Y - B_1 \bar x \qquad  B_1 = \frac{\overline{Yx} - \bar Y \bar x}{\overline{x^2} - \bar x^2}
$$

Quindi possiamo affermare che $B_0$ e $B_1$ sono [[inferenza-statistica#Stimatore consistente|consistenti]] e [[inferenza-statistica#Stimatore corretto|corretti]] poichè il [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] $\bold{\hat \mu} = B_0 e + B_1 \bold{x}$ lo è per il [[teorema-cochran|teorema di Cochran]].

Definiamo ora
$$
SS_R \coloneqq \|Y - \mu \|^2 = \varphi(B_0, B_1) = \sum_{i = 1}^n (Y_i - B_0 - B_1 x_i)^2 = \sum_{i = 1}^n R_i^2
$$
con gli $R_i = Y_i - B_0 - B_1 x_i$ detto *residui* e $SS_R$ detta *sum of squares of residuals*.
Quindi, visti i conti fatti prima, possiamo affermare che **la retta di regressione trovata è quella che minimizza la somma dei residui** al quadrato.

Possiamo infine trarre un'ultima conclusione dal [[teorema-cochran|teorema di Cochran]], ovvero che
$$
S_e \coloneqq\frac{SS_R}{\sigma^2} \sim \chi^2(n-2)
$$
che è uno [[inferenza-statistica|stimatore]] [[inferenza-statistica#Stimatore corretto|corretto]] e[[inferenza-statistica#Stimatore consistente|consistente]].

### Distribuzione degli stimatori per la regressione
Si noti che come detto in precedenza $S_e \coloneqq\frac{SS_R}{\sigma^2} \sim \chi^2(n - 2)$ quindi $S_e \approx \sigma$. Questa funzione ancillare si può descrivere anche come $\frac{S_e^2}{\sigma^2}(n-2) \sim \chi^2(n - 2)$.

Ora analizziamo lo stimatore $B_1 \approx \beta_1$. ricordiamo che $B_1 \coloneqq \frac{\overline{Yx} - \bar Y \bar x}{\overline{x^2} - \bar x^2}$. Possiamo dimostrare che $B_1$ è [[gaussiana|gaussiano]], [[inferenza-statistica#Stimatore corretto|corretto]] e [[inferenza-statistica#Stimatore consistente|consistente]]:
- [[gaussiana|gaussiano]] perchè è combinazione lineare di [[gaussiana|gaussiane]], infatti:
$$
B_1 \coloneqq \frac{\overline{Yx} - \bar Y \bar x}{\overline{x^2} - \bar x^2} \\
= \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \sum_{i = 1}^n x_i Y_i - \frac{1}{\overline{x^2} - \bar x^2} \bar x \frac{1}{n} \sum_{i = 1}^n Y_i \\
= \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n}  \sum_{i = 1}^n (x_i - \bar x) Y_i
$$
- [[inferenza-statistica#Stimatore corretto|corretto]] perchè
$$
E(B_1) = E\Big[\frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \sum_{i = 1}^n (x_i - \bar x) Y_i \Big] \\
= \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \sum_{i = 1}^n (x_i - \bar x) E(Y_i) \\
= \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \sum_{i = 1}^n [(x_i - \bar x) (\beta_0 + \beta_1 x_i)] \\
= \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \beta_0 \sum_{i = 1}^n (x_i - \bar x) + \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \beta_1 \sum_{i = 1}^n x_i^2 - x_i \bar x \\
= \frac{1}{\overline{x^2} - \bar x^2} \beta_0 (\bar x - \bar x) + \frac{1}{\overline{x^2} - \bar x^2} \beta_1 (\overline{x^2} - \bar x^2)\\
= 0 + \beta_1
$$
- [[inferenza-statistica#Stimatore consistente|consistente]] perchè
$$
Var(B_1) = Var\Bigg[\frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \sum_{i = 1}^n (x_i - \bar x) Y_i\Bigg] \\
= \sum_{i = 1}^n Var \Bigg[ \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} (x_i - \bar x) Y_i \Bigg] \qquad \text{per indipendenza delle } Y_i \\
= \sum_{i = 1}^n \Bigg[ \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} (x_i - \bar x) \Bigg]^2 Var(Y_i)\\
= \sum_{i = 1}^n \Bigg[ \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} (x_i - \bar x) \Bigg]^2 \sigma^2 \\
= \sigma^2 \sum_{i = 1}^n \Bigg[ \frac{1}{\overline{x^2} - \bar x^2} \frac{1}{n} \Bigg]^2 (x_i^2 + \bar x^2 - 2 x_i \bar x) \\
= \frac{\sigma^2}{n} \Bigg( \frac{1}{\overline{x^2} - \bar x^2} \Bigg)^2 \Big(\overline{x^2} - \bar x^2 \Big) \\
= \frac{\sigma^2}{n \Big(\overline{x^2} - \bar x^2\Big)} \xrightarrow[n \to +\infty]{} 0\\
$$

Si noti che per fare inferenza su $\beta_1$ è possibile usare le seguenti funzioni:
$$
\frac{B_1 - \beta_1}{\sigma \sqrt{\frac{1}{n\big(\overline{x^2} - \bar x^2\big)}}} \sim \mathcal{N}(0, 1)
\qquad
\frac{B_1 - \beta_1}{S_e \sqrt{\frac{1}{n\big(\overline{x^2} - \bar x^2\big)}}} \sim t(n - 2)
$$
Si noti che solo la seconda è una [[funzione-ancillare|funzione ancillare]] poichè non si conosce $\sigma$.

Inoltre, $B_0$ può essere stimato nel seguente modo:
$$
B_0 \sim \mathcal{N}\Bigg(\beta_0, \sigma^2 \frac{\overline{x^2}}{n \big(\overline{x^2} - \bar x^2 \big)}\Bigg)
$$
Quindi possiamo considerare il vettore $B = (B_0, B_1)$ come
$$
B \sim \mathcal{N}\Bigg(\beta, \sigma^2 \frac{\overline{x^2}}{n \big(\overline{x^2} - \bar x^2 \big)} K \Bigg)
$$
con $\beta = (\beta_0, \beta_1)$ e $K = \begin{pmatrix}
\overline{x^2} & -\bar x \\
-\bar x    & 1       \\
\end{pmatrix}$

## Regressione lineare muplipla
In questo caso il modello cambia, infatti ora consideriamo
$$
Y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots \beta_n x_n + e \qquad \text{con } e \sim \mathcal{N}(0, \sigma^2) \\
Y \sim \mathcal{N}(\beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots \beta_n x_n, \sigma^2)\\
Y \sim \mathcal{N}(\bold{X} \bold{\beta}, \sigma^2 \bold{I})\\
Y_i \sim \mathcal{N}\bigg( \sum_{i = 0}^p[\bold{X} \bold{\beta}]_i, \sigma^2 \bold{I}\bigg) \text{ indipendenti fra loro, con } [\bold{X}\bold{\beta}]_i = \sum^p_{j = 0} x_{i,j}\beta_j

$$
Utilizzeremo in particolar modo la notazione matriciale, come vista sopra; si noti che tipicamente $n >> p$ altrimenti si rischia l'[[overfitting]].

Applicando il [[teorema-cochran|teorema di Cochran]] e derivando rispetto alle componenti di $B$ possiamo verificare che
$$
\bold{B} = (\bold{X}^T\bold{X})^{-1}\bold{X}^T\bold{Y} = \bold{NY}
$$
Si noti che $\bold{X}^T\bold{X}$ è quadrata ed invertibile se e solo se $X$ è di rango massimo.
Sempre il [[teorema-cochran|teorema di Cochran]] ci dice anche che $\bold{B}$ è il [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] di $\bold \beta$ ed è indipendente da
$$
S_e \approx \sigma \qquad S_e \coloneqq \sqrt{\frac{SS_R}{n - p - 1}} \qquad SS_R = \| \bold{Y} - \bold{XB}\|^2 \qquad \frac{S_e^2}{\sigma^2}(n - p - 1) \sim \chi^2(n - p - 1)
$$
Ora possiamo guardare la [[distribuzione]] di $\bold{B}$. Sappiamo che è combinazione lineare di [[gaussiana|gaussiane]], quindi sarà anche essa [[gaussiana]]. Calcoliamone i momenti:
$$
E(\bold{B}) = \bold{NX\beta} = (\bold{X}^T\bold{X})^{-1}\bold{X}^T\bold{X}\bold{\beta} = \bold{\beta} \\
Cov(\bold{B}) = Cov(NY) = \bold{N}\bold{N}^T Cov(\sigma^2 \bold{I}) = \bold{N} \bold{N}^T \sigma^2 = (\bold{X}^T\bold{X})^{-1}\bold{X}^T \bold{X}(\bold{X}^T\bold{X})^{-1} \sigma^2 = \sigma^2(\bold{X}^T\bold{X})^{-1}
$$
$$
B \sim \mathcal{N}(\bold{\beta}, \sigma^2(\bold{X}^T\bold{X})^{-1})
$$
Ora possiamo calcolare direttamente
$$
SS_R = \| \bold{Y} - XB \|^2 = \bold{Y}^T\bold{Y} - \bold{Y}^T\bold{X}(\bold{X}^T\bold{X})^{-1}\bold{X}^T\bold{Y}
$$

Ora che abbiamo trovato le [[distribuzione|distribuzioni]] di $\bold{B}$ possiamo trovare le [[funzione-ancillare|funzioni ancillari]]:
$$
\frac{B_i - \beta_i}{S_e \sqrt{\big[ \bold{X}^T \bold{X} \big]_{i,i}}} \sim t(n - p - 1) 
\qquad
\frac{S_E^2}{\sigma^2}(n - p - 1) \sim \chi^2 (n - p - 1)
$$

## Regressione polinomiale
Può capitare (spesso) che la regressione non mi soddisfi, e che guardando il grafico dei [[validazione#Regressione|residui]] si possono notare certe volte andamenti non-lineari. In questo caso, vorremmo introdurre termini di grado superiore, in modo tale che ci sia un maggiore fit fra curva e dati.
È possibile aggiungere alla regressione delle variabili *dummy*, ovvero che sono monomi di grado $2$ o superiore di variabili già incontrate. In questo modo la non-linearità verra corretta e $SS_R$ si ridurrà.
È possibile anche aggiungere dei *termini di interazione* fra due (o più) variabili, in modo tale che queste possano migliorare ulteriormente il fit dei dati.

Resta molto importante una regola, ovvero la **regola gerarchica: si tengono tutte le variabili corrispondenti a monomi che dividono un monomio nel modello**.

## Regressione pesata
Si usa quando i dati non sono [[varianza|omoschedastici]], ad esempio quando le $Y_i \sim \mathrm{Pois}(\mu_i) \stackrel{\cdot}{\sim} \mathcal{N}(\mu_i, \mu_i)$ oppure quando $Y_i \sim \mathcal{N}(\mu_i, (\mu_i \plusmn 10\% \mu_i)^2)$ o quando $Y_i \sim \mathrm{bin}(n_i, p_i)$ o se il grafico dei residui cresce al crescere delle $x_i$.
Se supponiamo di conoscere la varianza $r_i$ allora possiamo pensare di ottenere il [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] in questo modo:
$$
\frac{\partial}{\partial w_i}l(\bold{B}) = \sum_{i = 0}^n \frac{1}{w_i} \bigg( Y_i - \sum_{j = 0}^p x_{i,j} B_j \bigg)^2 =: \tilde SS_R \qquad w_i = \frac{1}{r_i^2}
$$
Alternativamente è possibile dividere gli $X_{i, j}$ e gli $Y_i$ in questo modo: $\tilde X_{i, j} \coloneqq \frac{X_{i, j}}{r_i}$ e $\tilde X_i \coloneqq \frac{Y_i}{r_i}$ e si ottiene $SS_R = \sum_{i = 0}^n \frac{1}{r_i^2} \bigg( Y_i - \sum_{j = 0}^p x_{i,j} B_j \bigg)^2$

## Regressione logistica
Supponiamo di avere un [[inferenza-statistica|campione]] del tipo
$$
Y_i \sim \mathrm{bin} (1, \sigma(\sum_{j = 0}^p \beta_j x_{i,j})) \qquad \text{con }\sigma(x) = (1 + e^{-x})^{-1}
$$
<img src="https://www.saedsayad.com/images/LogReg_1.png" width=700>

In questo caso notiamo che $P(X = k) = \sigma(z_i)^k (1 - \sigma(z_i))^k$, per cui la regressione in questo caso, invece di $SS_R$ minimizza
$$
-l(\beta) \coloneqq log \prod_{i = 1}^n P(Y_i = y_i) = \sum_{i = 1}^n \Big[ y_i \log\sigma(z_i) + (1 - y_i) \log(1- \sigma(z_i) \Big] 
$$


## Test di regressione
Test utilizzato per verificare che la $Y$ dipenda davvero da $x_i$.
Verificare che la $Y$ dipenda dalla $x_i$ equivale a chiedersi se il corrispettivo $\beta_i = 0$. Da qui nascono le ipotesi di questo test:
$$
H_0: \beta_i = 0 \qquad H_1: \beta_i \not = 0
$$

### Caso della regressione lineare semplice
Come abbiamo visto prima, lo [[inferenza-statistica|stimatore]] e la [[funzione-ancillare|funzione ancillare]] sono $\frac{B_i - \beta_i}{S_e \sqrt{\frac{1}{n\big(\overline{x^2} - \bar x^2\big)}}} \sim t(n - 2)$, per cui, la statistica del test è $T \stackrel{H_0}{\coloneqq} \frac{B_i}{S_e \sqrt{\frac{1}{n\big(\overline{x^2} - \bar x^2\big)}}}$

Se il [[test-statistico|test]] dice $H_0$ (e quindi $T \in \mathrm{RA}_T = [-q, q]$ con $q = F^{-1}_{t(n-2)}(1 - \frac{\bar \alpha}{2})$ e $F^{-1}_{t(n-2)}$ la [[variabili-aleatorie#Continue|funzione di ripartizione]] inversa della [[t-student|t di student]] con $n - 2$ gradi di libertà) allora possiamo provare ad ignorare $x_i$ e riprovare a fare la regressione senza.

Nota: nel caso $n = 2$, se il test dice $H_0$, allora posso trattare le $Y_i$ come un normalissimo [[campione-gaussiano-univariato|campione univariato]] $Y_i \sim \mathcal{N}(\mu, \sigma^2)$.

### Caso della regressione lineare multipla
$$
\frac{B_i - \beta_i}{S_e \sqrt{\big[ \bold{X}^T \bold{X} \big]_{i,i}}} \sim t(n - p - 1)
\qquad
T \coloneqq \frac{B_i}{S_e \sqrt{\big[ \bold{X}^T \bold{X} \big]_{i,i}}}
$$
In questi casi, per rapidità, spesso di predilige il [[test-statistico#Il p-value|p-value]] calcolato come $\alpha^* = 2 - 2 F_{t(n - p - 1)}(|T|)$
### Test alternativo per la regressione
Tipicamente quando uso la [[stepwise-selection|stepwise forward o backward]] risulta comodo proporre un altro test a quello comunemente usato che non usa la [[t-student|t di student]] ma usa la [[f-fisher|F di Fisher]]. 
Si noti che sono test equivalenti, tuttavia i software automatici spesso chiedono il valore della $F$ e non del [[test-statistico#Il p-value|p-value]] $\alpha*_i$, in particolare:
- **$F$ to enter**: valore della [[f-fisher|F di Fisher]] per la quale **tenere** la variabile per la [[stepwise-selection|stepwise forward]]
- **$F$ to remove**: valore della [[f-fisher|F di Fisher]] per la quale **rimuovere** la variabile per la [[stepwise-selection|stepwise backward]]

I valori che sono considerati buoni corrispondono a quelli del $30\%$, come nella [[stepwise-selection|stepwise selection]].

## Intervallo di confidenza per $Y$ medio (detta anche *riposta media*)
Possiamo cercare di stimare la retta di regressione in due modi: o con una stima di tipo puntuale (e quindi applicando quello che abbiamo trovato prima, ovvero $Y(X) = \bold{BX}$; nel caso della regressione lineare semplice questo diventa $y(x) = B_0 + B_1 x$) o con un intervallo di confidenza. In questa sezione espanderemo questa seconda alternativa.

Si noti che **questo intervallo si stringe sempre di più al crescere degli $n$ punti disponibili**.

### Caso della regressione lineare semplice
Nel caso della regressione lineare semplice il valore incognito da stimare è $y(x) = \beta_0 + \beta_1 x$ (al variare di $x$). Sappiamo che, dato che è combinazione lineare di [[gaussiana|gaussiane]], $y(x) \sim \mathcal{N} (?,?)$. Facendo i conti, è possibile trovare che:
$$
B_0 + B_1 x \sim \mathcal{N}\bigg(\beta_0 + \beta_1 x, \frac{\sigma^2}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg] \bigg)
$$
da qui possiamo ricavare gli [[test-statistico#Intervalli di confidenza|intervalli di confidenza]] e dedurre che 
$$
\beta_0 + \beta_1 x \in B_0 + B_1 x \plusmn q S_e \sqrt{\frac{1}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg]} \qquad \text{con } q = F^{-1}_{t(n-2)}\bigg(1 - \frac{\bar\alpha}{2} \bigg)
$$

### Caso della regressione lineare multipla
Nel caso della regressione lineare multipla, dato un punto nuovo fissato $\bold{\tilde x} = (1, \tilde x_1, \tilde x_2, \ldots, \tilde x_p) \in \mathbb{R}^{p + 1}$ la risposta media corrispondente è
$$
\beta_0 + \beta_1 \tilde x_1 + \beta_2 \tilde x_2 + \ldots + \beta_p \tilde x_p = \bold{\tilde x}^T \bold{\beta} \approx \bold{\tilde x}^T\bold{B} \sim \mathcal{N}(\bold{\tilde x}^T \bold{\beta}, \sigma^2(\bold{X}^T\bold{X})^{-1}\bold{\tilde x})
$$
$$
\frac{\bold{\tilde x}^T\bold{B} - \bold{\tilde x}^T\bold{\beta}}{S_e \sqrt{\bold{\tilde x}^T (\bold{X}^T\bold{X})^{-1}\bold{\tilde x}}} \sim t(n - p - 1)
$$

Possiamo ora vederne gli intervalli di confidenza, preso un $\tilde Y \sim \mathcal{N}(\bold{\tilde x}^T \bold{\beta}, \sigma^2)$:
$$
\bold{\tilde x}^T\bold{\beta} \in \bold{\tilde x}^T\bold{B} \plusmn q S_e \sqrt{\bold{\tilde x}^T(\bold{X}^T\bold{X})^{-1}\bold{\tilde x}}  \qquad \text{con } q = F^{-1}_{t(n - p - 1)}\bigg(1 - \frac{\bar \alpha}{2} \bigg)
$$

## Intervallo di predizione per $\tilde Y$ futuro
Supponiamo di avere un valore $\tilde x$ che non abbiamo mai visto fino ad ora. Vorremmo poter avere un intervallo che contiene la maggior parte dei possibili punti futuri. Questo intervallo è di tipo tubolare intorno alla risposta media stimata $\bold{BX}$ e la sua larghezza è circa $2q\sigma$, con $q = F^{-1}_{t(n-2)}\bigg(1 - \frac{\bar\alpha}{2} \bigg)$.

### Caso della regressione lineare semplice
Determiniamo ora l'[[test-statistico#Intervalli di predizione|intervallo di predizione]], sapendo che $\tilde Y \approx \beta_0 + \beta_1 x \approx B_0 + B_1 x$ (che corrisponde alla stima puntuale per punto futuro) e che siamo nel caso lineare semplice:
$$
\tilde Y - (B_0 + B_1 x) \sim \mathcal{N}\bigg(0, \sigma^2 + \frac{\sigma^2}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg] \bigg)
$$
$$
\frac{\tilde Y - (B_0 + B_1 x)}{\sigma \sqrt{1 + \frac{1}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg]}} \sim \mathcal{N}(0, 1) \implies \frac{\tilde Y - (B_0 + B_1 x)}{S_e \sqrt{1 + \frac{1}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg]}} \sim \mathcal{N}(0, 1)
$$
Da qui possiamo evincere, facendo i conti, che:
$$
\tilde Y \in B_0 + B_1 x \plusmn qS_e \sqrt{1 + \frac{1}{n} \bigg[ 1 + \frac{(x - \bar x)^2}{\overline{x^2} - \bar x^2} \bigg]}
$$

### Caso della regressione lineare multipla
Operiamo gli stessi conti fatti in precedenza:
$$
\bold{\tilde Y} - \bold{\tilde x}^T\bold{\beta} \sim \mathcal{N}(0, \sigma^2 + \sigma^2 \bold{\tilde x}^T (\bold{X}^T\bold{X})^{-1} \bold{\tilde x})
$$
la cui [[funzione-ancillare|funzione ancillare]] e [[test-statistico#Intervalli di predizione|intervallo di predizione]] sono
$$
\frac{\bold{\tilde Y} - \bold{\tilde x}^T\bold{\beta}}{S_e \sqrt{1 + \bold{\tilde x}^T (\bold{X}^T\bold{X})^{-1} \bold{\tilde x}}} \sim t(n - p - 1)
\qquad
\bold{\tilde Y} \in \bold{\tilde x}^T\bold{\beta} \plusmn q S_e \sqrt{1 + \bold{\tilde x}^T (\bold{X}^T\bold{X})^{-1} \bold{\tilde x}} \quad \text{ con } q = F^{-1}_{t(n - p - 1)}(1 - \frac{\bar \alpha}{2})
$$
