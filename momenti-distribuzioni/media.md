---
title: "Media"
---
## Media
La media (o *valore atteso*) è il momento primo delle distribuzioni. Viene chiamato anche *valore atteso* perchè è il valore che ci aspettiamo la distribuzione ritorni *in media*. Talvolta viene chiamata anche *speranza matematica*. Rappresenta il *baricentro* della distribuzione: divide la distribuzione a metà (ma non la probabilità a metà perchè quella è la [indici-statistici#Mediana|mediana]]).

Data quindi una distribuzione $f_X(x)$ con X [[variabili-aleatorie#Continue|v.a. continua]] (o definita su un insieme di valori infinitamente non-numerabile), la media si calcola come:
$$
    E(X) = \int_{-\infty}^{+\infty} x f(x) dx
$$

Se invece X è una [[variabili-aleatorie#Discrete|v.a. discreta]] (definita su un insieme di valori finito o infinitamente numerabile) con legge $\phi_X$ allora avremo:
$$
    E(X) = \sum_{i = 1}^{+\infty} x_i \phi_X(x_i)
$$
In questo caso particolare, se $X$ è definita su un insieme infinitamente numerabile di valori allora i possibili valori di $E(X)$ sono:
1) $\sum_{k > 0} x_i \phi_X(x_i) = +\infty \land \sum_{k <> 0} x_i \phi_X(x_i) = -\infty \implies \not \exists E(X)$
2) $\sum_{k > 0} x_i \phi_X(x_i) < +\infty \land \sum_{k <> 0} x_i \phi_X(x_i) > -\infty \implies \exists E(X)$
3) Se uno dei due è ben definito e l'altro no, allora dipende dalla situazione e bisogna guardare proprio i valori.

Viene spesso indicata anche come $\bar X$, $E\{X\}$, $M(X)$, $M\{X\}$.

Si noti che la media è un operatore che possiede la properietà di linearità, infatti $E(aX + b) = aE(X) + b$ e che $E(X + Y) = E(X) + E(Y)$.

Si noti che (dati X e Y delle [[variabili-aleatorie|v.a.]]):
- se $X \ge 0$ allora $E(X) \ge 0$ (e questa proprietà può risultare comoda per verificare di aver fatto i conti correttamente)
- se $X \ge Y$ allora $E(X) \ge E(Y)$
- se X e Y sono [[indipendenti]] allora $E(X Y) = E(X) E(Y)$
- $E(X) = 0 \iff \forall X = 0 \in \mathrm{dom}(X)$, altrimenti $E(X) \not = 0$
- $E(E(\ldots E(X) \ldots) = E(X)$
- se $X$ è [[variabili-aleatorie#Continue|continua]] e $X \ge 0 \iff E(X) = \int_0^{+\infty} 1 - F_X(t) dt$ con $F$ [[variabili-aleatorie#Continue|Cdf]] di $X$
- se $X$ è [[variabili-aleatorie#Discrete|discreata]] e $X \ge 0 \iff E(X) = \sum_{j = 0}^{+\infty} 1 - F_X(t)$ con $F$ [[variabili-aleatorie#Discreta|funzione di ripartizione]] di $X$
- se X è [[variabili-aleatorie#Continue|continua]] e viene trasformata da una funzione $g: \mathbb{R} \to \mathbb{R}$ tale che $\exists g^{-1}$ monotona allora $E(g(X)) = \int_{-\infty}^{+\infty} g(x) f(x) dx$
- se X è [[variabili-aleatorie#Discrete|discreta]] e viene trasformata da una funzione $g: \mathbb{R} \to \mathbb{R}$ tale che $\exists g^{-1}$ monotona allora $E(g(X)) = \sum_{i = 1}^{+\infty} g(x_i) f_X(x_i)$

Sia $Z = (X_1, X_2, \dots, X_n)$ un [[variabili-aleatorie#Vettori Aleatori|vettore aleatorio]] con pdf $f$ (o pmf $\phi$ nel caso discreto) e sia $h: \mathbb{R}^n \to R$ allora basta integrare lungo tutto il supporto (e quindi integrare su tutto $\mathbb{R}$ per $n$ volte) come mostrato sopra.

Questo è l'indice di posizione più utilizzato (alle volte anche impropriamente, poichè spesso la [[indici-statistici#Mediana|mediana]] è più rappresentativa perchè appartenente alla distribuzione).