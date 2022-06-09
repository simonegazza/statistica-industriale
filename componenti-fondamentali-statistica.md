---
title: "Componenti alla base della statistica"
---
# Componenti alla base della statistica
Supponiamo di avere un insieme di dati $x_1, x_2, \ldots, x_2$ che chiameremo **campione dei dati** che può rappresentare ad esempio un gruppo di persone.
Si spera che il campione di dati raccolto sia una qualche realizzazione di una serie di [[variabili-aleatorie|vv.aa.]] $X_1, X_2, \ldots, X_n$.

Il compito della statistica inferenziale è quello di inferire informazioni sulla legge delle $X_i$ a partire dai dati $x_i$.

Ogni volta che raccogliamo delle informazioni provenienti da questi dati, stiamo raccogliendo una **statistica**. Quindi una statistica è una [[variabili-aleatorie|v.a.]] che è una funzione deterministica di un campione di dati. Quindi si tratta di una qualche $f(x_1, x_2, \ldots, x_n)$.

Di queste statistiche, alcune vanno a stimare qualcosa che poi ci torna effettivamente utile (ad esempio la media campionaria stima la [[media]] vera, la [[cdf-empirica|CdF empirica]] stima la vera [[variabili-aleatorie|CdF]], ecc...).

Uno **stimatore** è una statistica che stima un parametro della nostra [[distribuzione]]. Si dice che uno stimatore di un parametro $\theta$ è una statistica $\Theta = f(x_1, \ldots, x_n)$ la cui legge è in qualche modo concentrata vicino a $\theta$.

Generalmente della stessa grandezza è possibile utilizzare diversi stimatori, tuttavia spesso ci sono alcune scelte che sono considerate preferenziali, ovvero quegli stimatori che si definiscono **corretti** e **consistenti**

## Stimatore consistente
Una famiglia di stimatori $\Theta_n$ di un parametro $\theta$ si dice **consistente** se $\Theta_n \xrightarrow[n \to \infty]{P} \theta$, ovvero sono convergenti al parametro in [[probabilita|probabilità]]. Questa espressione sta ad indicare che
$$
\forall \epsilon \quad P(|\Theta_n - \theta| < \epsilon) \xrightarrow[n \to \infty]{} 0
$$
Operativamente in realtà basta che $E(\Theta_n) \xrightarrow[n \to \infty]{} \theta$ e che $Var(\Theta_n) \xrightarrow[n \to \infty]{} 0$ (e quindi che la [[media]] punti al parametro e la [[varianza]] vada a $0$ o al crescere di $n$).

Si noti che abbiamo considerato una famiglia di stimatori $\Theta_n$ perchè intendiamo che al crescere della numerosità del campione $n$ avremo sempre un nuovo stimatore aggiornato con la nuova numerosità. Quindi lo stimatore è dipendente da $n$, e abbiamo un modo stabilito di aggiornare $\Theta$ usando i nuovi dati a disposizione.

## Stimatore corretto
Uno stimatore $\Theta$ di un parametro $\theta$ si dice **corretto** se
$$
E(\Theta) = \theta
$$
**Altrimenti** tale stimatore si dice **distorto** e ha un erorre sistematico (detto **bias**, in inglese) di valore $E(\Theta) - \theta$.

## Stimatori di massima verosimiglianza
Esiste un metodo per trovare stimatori che siano consistenti (non necessariamente corretti però). Tipicamente si indicano come stimatori di massima likelihood (quindi Maximum Likelihood Estimator, MLE).

Si tratta di osservare i dati e cercare di capire quale sia il valore del parametro $\theta$ che li rende più verosimili (o probabili).

Supponiamo di avere un campione di dati $d_1, d_2, \ldots, d_n$. Immaginiamo di scrivere la [[variabili-aleatorie|PdF]] di ciascun $X_i$ che ha generato il $d_i$. Quindi scriviamo le varie $f_{X_i}(x)$. Ora consideriamo indipendenti (perchè le vediamo come prove ripetute dello stesso esperimento), quindi avremo che la legge del campione statistico è il prodotto delle varie [[variabili-aleatorie|PdF]] delle $X_i$, quindi $f_X(x_1, x_2, \ldots, x_n) = \prod_{i = 1}^n f_{X_i}(x)$. Infine posso andare a sostitiure a ciascuna $x_i$ il valore del dato $d_i$, e questo ci dice quanto erano probabili quei numeri che abbiamo ottenuto.

La funzione $L(\theta) \coloneqq f_X(x_1, x_2, \ldots, x_n)$ sopra citata si chiama funzione di likelihood. Ovvero è la densità congiunta, calcolata nei dati e vista in funzione dei parametri incogniti.

In un certo senso, il MLE è il $L(\hat \theta) \coloneqq \max_\theta L(\theta)$ e quindi $\hat \theta \coloneqq \argmax_\theta L(\theta)$. Si noti sempre che $\hat \theta$ è in realtà una funzione dei $(x_1, x_2, \ldots, x_n)$

Si noti che nei casi più interessanti questa funzione si trova con il calcolatore. Per altro questa cosa si porta dietro dei problemi di spiegabilità perchè l'ha fatta il calcolatore ma non sappiamo come. Tuttavia nei casi semplici è possibile cercare il massimo da un punto di vista teorico.

Per trovare il massimo è necessario derivare, per cui dobbiamo derivare $L(\hat \theta)$ (bisognerebbe controllare anche la derivata seconda, ma nei casi pratici è sempre positiva o nulla). Tuttavia spesso cercare il massimo derivando risulta scomodo. Per cui come stratagemma, dato che ci interessa solo il massimo, andiamo a modificare la funzione in modo che abbia il massimo nello stesso punto ma che sia pià facile da derivare. Quello che si fa tipicamente è applicare il logaritmoalla funzione $L(\hat \theta)$, ottenendo quindi $\log L(\hat \theta)$, e quindi $\hat \theta \coloneqq \argmax_\theta L(\theta) = \argmax_\theta \log(L(\theta))$. In genere si scrive che $l(\theta) \coloneqq \log(L(\theta))$. Tale quantità è detta **log-likelihood**.

A questo punto basta derivare e ottenere la legge di $l(\theta)$. Sostituisco a $\theta$ il $\hat \theta$ e pongo $l(\hat \theta) = 0$. Il risultato è il mio stimatore di massima likelihood.

### Primo esempio: stimatore per un'esponenziale di parametro $\lambda$
Supponiamo di avere $(X_1, X_2 \ldots, X_n) \sim \mathrm{expo}(\lambda)$ con $\lambda > 0$ incognito. Suppongo di aver osservato i numeri $x_1, x_2, \ldots, x_n$. Qual è lo stimatore di massima likelihood?
La distribuzione [[esponenziale]] ha legge $f_{X_i}(t) = \lambda e^{-\lambda t}, t \ge 0$. Quindi la legge del vettore $\bold{X} = (X_1, X_2, \ldots, X_n)$ (seguendo quanto scritto prima) è $f_\bold{X}(t_1, t_2, \ldots, t_n) = \prod_{i = 1}^n \lambda e^{-\lambda t_i} = \lambda^n e^{-\lambda \sum_{i = 1}^n t_i}$. La verosimiglianza è la funzione $L(\lambda) \coloneqq f_\bold{X}(x_1, x_2, \ldots, x_n) = \lambda^n e^{-\lambda \sum_{i = 1}^n x_i}$. Ora dobbiamo massimizzare la funzione: quindi faccio la derivata $\frac{d}{d\lambda} L(\lambda) = \frac{d}{d\lambda} \lambda^n e^{-\lambda \sum_{i = 1}^n x_i}$. Questa funzione da derivare è scomoda, allora applico il logaritmo, che è una funzione crescente e quindi preserva  il massimo. Avremo quindi che $l(\lambda) \coloneqq \log (L(\lambda)) = \frac{d}{d\lambda} (n \log(\lambda) - \lambda \sum_i x_i) = n \frac{d}{d\lambda}(\log(\lambda) - \lambda \frac{1}{n}\sum_i x_i) = n (\frac{1}{\lambda} - \frac{1}{n}\sum_i x_i)$. Ora per massimizzare poniamo $\frac{d}{d\lambda} l(\hat \lambda) = 0$, per cui $n (\frac{1}{\hat \lambda} - \frac{1}{n}\sum_i x_i) = 0$ e quindi
$$
\hat \lambda = \frac{1}{\frac{1}{n}\sum_i x_i} = \frac{1}{\bar x}
$$

### Secondo esempio: multinomiale
Sia $X \sim multin(n, p)$ con $p = (p_1, p_2, \ldots, p_k)$. Il campione è $x_1, x_2, \ldots, x_k$ i conteggi delle diversi categorie (ogni $x_i$ è  una [[multinomiale]]), e ricordiamo che $\sum_i^k x_i = n$. Voglio ottenere il vettore $p$ con lo stimatore di massima verosimiglianza.

Il risultato che mi immagino di ottenere è $\hat p_i = \frac{x_i}{n}$.

La log-likelihood è $l(p) = \log(\phi_X(x_1, \ldots, x_k)) = \log ( \frac{n!}{x_1! x_2! \ldots x_n!} p_1^{x_1} p_2^{x_2} \ldots p_k^{x_k})$, dove $\phi_X(x_1, \ldots, x_k)$ è la funzione di massa della [[multinomiale]]. Si noti che tutta la parte di $\frac{n!}{x_1! x_2! \ldots x_n!}$ non dipende da $p$, quindi possiamo anche buttarla via (anche se per il momento la teniamo e la segnamo come $C$). Quindi avremo $l(p) = C + x_1 log p_1 + x_2 log p_2 + \ldots + x_k log p_k$.

Dato che siamo in un caso multi-variabile, dobbiamo fare il gradiente di $l(p)$, quindi $\nabla l(p) = \Big(\frac{\partial l}{\partial p_1}(p), \frac{\partial l}{\partial p_2}(p), \ldots, \frac{\partial l}{\partial p_k}(p)\Big)$. Ora siamo costretti ad una semplificazione (perchè altrimenti avremmo bisogno del [moltiplicatore di Lagrange](https://it.wikipedia.org/wiki/Metodo_dei_moltiplicatori_di_Lagrange)), quindi valutiamo solo il caso in cui $k = 2$, quindi $p = (p_1, p_2) \land p_1 + p_2 = 1 \land p = \Big(\frac{\partial l}{\partial p_1}(p), \frac{\partial l}{\partial p_2}(p)\Big)$, quindi $p_2 = 1 - p_1$, e quindi $l(p_1) = C + x_1 \log x_1 + x_2 \log (1 - p_1)$. Ora possiamo dire che $\frac{\partial l}{\partial p_1}(p_1) = \frac{x_1}{p_1} - \frac{x_2}{1 - p_1}$. Per trovare il massimo la derivata dello stimatore uguale a $0$, quindi:
$$
\frac{x_1}{\hat p_1} - \frac{x_2}{1 - \hat p_1} = 0 \iff x_1(1 - \hat p_1) = x_2 \hat p_1 \iff \\ x_1 = \hat p_1 * (x_1 + x_2) \iff \hat p_1 =\frac{x_1}{x_1 + x_2} = \frac{x_1}{n}
$$

Ora possiamo valutare il caso con $k$ qualsiasi: abbiamo che $\nabla_p l(p) = \Big(\frac{x_1}{p_1}, \frac{x_1}{p_1}, \ldots, \frac{x_k}{p_k}\Big)$ e non è mai $0$ come vorremmo, però abbiamo una funzioen $g(p)$ che definisce un vincolo $g(p) = p_1 + p_2 + \ldots + p_k = 1$. Si noti che $\nabla_p g(p) = (1, 1, \ldots, 1)$.
La condizione del moltiplicatore di Lagrange è porre che il gradiente $\nabla_p l(p)$ e $\nabla_p g(p)$ siano paralleli (quindi che $\nabla_p l(p) = \alpha \nabla_p g(p)$).

Quindi avremo che:
$$
\Big(\frac{x_1}{p_1}, \frac{x_1}{p_1}, \ldots, \frac{x_k}{p_k}\Big) = \alpha (1, 1, \ldots, 1) \iff \\ \space \\

\frac{x_1}{p_1} = \alpha, \frac{x_2}{p_2} = \alpha, \ldots, \frac{x_k}{p_k} = \alpha \iff \\ \space \\

p_1 = \frac{x_1}{\alpha}, p_2 = \frac{x_2}{\alpha}, \ldots, p_k = \frac{x_k}{\alpha} = \alpha \\ \space \\

\text{ma so che } 1 = \sum_i p_i = \frac{1}{\alpha} \sum_i x_i \iff \\ \space \\ \alpha = \sum_i x_i \text{ quindi } \hat p_i =\frac{x_i}{\sum_i x_i} = \frac{x_i}{n}
$$

# Proprietà degli stimatori
Supponiamo di avere uno parametro di una [[distribuzione]] $Z \coloneqq a + b X$ e $W \coloneqq c + dY$, le seguenti proprietà sono valide:
- se $Z$ [[media]] allora il suo stimatore è  $\bar Z \coloneqq a + b \bar X$ è lineare.
- se $Z$ [[varianza]] allora il suo stimatore è  $S_Z^2 = S_{ZZ} = b^2 S_X$ è quadratico.
- se $Z$ [[deviazione-standard|deviazione standard]] allora il suo stimatore è  $S_Z = b S_X$
- se $Z$ [[covarianza]] allora il suo stimatore è $S_{ZW} = bd S_{XY}$
- se $Z$ [[covarianza#Matrice di correlazione lineare di Pearson|coefficiente di correlazione lineare]] allora il suo stimatore è  $r_{ZW} = r_{XY}$
