---
title: "Test del chi quadro"
---
# [[Test-statistico|Test]] del [[chi-quadro|chi quadro]]
È un gruppo di [[test-statistico|test]] di adattamento (ovvero che verificano se un dato [[inferenza-statistica|campione]] appartiene ad una data [[distribuzione]]).

## Te[[test-statistico|Test]]st del [[chi-quadro|chi quadro]] elementare
Abbiamo un [[inferenza-statistica|campione]] $X_1, X_1, \ldots, X_n$ con [[distribuzione]] incognita. Vogliamo verificare che la [[distribuzione]] $\varphi$ abbia [[distribuzione|legge]] [[variabili-aleatorie#Discrete|discreta]] e che assuma un numero piccolo di valori possibili $k$. Faremo quindi un'[[test-statistico|ipotesi]] sulla distribuzione che chiameremo $\varphi_0$ che sarà assegnata e completamente specificata. Successivamente verificheremo che $\varphi = \varphi_0$.

Si noti che per ottenere una risposta accurata, sarà necessario avere $n$ molto grande (e si noti che più $k$ è grande, più $n$ dovrà essere grande, e anche se non c'è una vera [[distribuzione|legge]] che li lega, la rule of thumb dice che $n \ge 5k$).

Il [[test-statistico|Test]] si svolge nel seguente modo:
- [[test-statistico|ipotesi]] $H_0: \varphi = \varphi_0$, $H_1:  \varphi \not = \varphi_0$
- si determinano gli **osservati** $O_j \coloneqq \# \{i \le n : X_i = j\}$ con $j = 1, \ldots, k$; ovvero conto il numero di volte che è uscito $j$ negli $X_i$
- sappiamo quindi che $O_j \sim \mathrm{bin}(n, \varphi(j)) \stackrel{H_0}{=} \mathrm{bin}(n, \varphi_0(j))$
- si determinano gli **attesi** $A_j \coloneqq E_{H_0}(O_j) = n \varphi_0(j)$; ovvero i risultati che mi aspetterei in media sotto $H_0$
- calcolo la **statistica del [[test-statistico|test]]** $W \coloneqq \sum_{j = 1}^k \frac{(O_j - A_j)^2}{A_j}$; in un certo senso corrisponde alla distanza media degli $O_j$ dagli $A_j$
- si noti che, se gli $A_j$ sono abbastanza grandi, allora $W \stackrel{H_0}{\dot \sim} \chi^2(k -1)$. Quando diciamo "$A_j$ abbastanza grandi" intendiamo la seguente rule of thumb: tutti gli $A_j$ devono essere maggiori di $1$ e almeno il $80\%$ di questi deve essere maggiore di 5.
- sotto $H_1$ avremo che $W$ sarà maggiore, quindi il [[test-statistico|test]] è unilaterale, per cui $\alpha^* \coloneqq 1 - F_{\chi^2 (k - 1)} (W)$
- questo [[test-statistico|test]] è poco [[test-statistico#Potenza del test|potente]], e spesso è necessario che gli $A_j >> 1$ per poter rilevare differenze anche modeste fra $\varphi$ e $\varphi_0$

## [[test-statistico|Test]] del [[chi-quadro|chi quadro]] esteso a [[distribuzione|legge]] qualsiasi
È possibile estendere il [[test-statistico|test]] del [[chi-quadro|chi quadro]] elementare visto sopra a leggi discrete con tanti valori possibili e anche a leggi continue. Ricordiamo che $\varphi_0$ debba restare completamente specificata.

Il [[test-statistico|test]] funziona nel seguente modo:
- fisso $k$
- divido $\mathbb{R}$ in $k$ insiemi (chiamati *bin*, ovvero cestini)
- conto quanti dati cadono in ciascun insieme
- il resto del [[test-statistico|test]] procede allo stesso modo del [[test-statistico|test]] elementare

Si noti che **a parità di k, il [[test-statistico|test]] è più [[test-statistico#Potenza del test|potente]] (e l'approssimazione migliore) se gli $A_j$ sono il più grande possibile**, questo ci suggerisce che **è meglio fare bins equiprobabili e non larghi uguali**.

Attenzione però perchè **la [[test-statistico#Potenza del test|potenza]] del [[test-statistico|test]] resta legata al numero di bins e alla loro posizione**. Questo per dire che tanti intervalli fitti riducono di molto la [[test-statistico#Potenza del test|potenza]] del [[test-statistico|test]], anche se equiprobabili.

### Esempio per l'estensione a [[distribuzione|legge]] qualsiasi
Supponiamo di avere un [[inferenza-statistica|campione]] di dati e di ritenere che questi provengano da una [[esponenziale]] di parametro $1$, quindi $F_0 \sim \mathrm{expo}(1)$. Avremo $H_0: F = F_0$ e $H_1:  F \not = F_0$. Supponiamo di prendere $k = 7$ e dividere quindi $\mathbb{R}$ in $7$ bins. Si noti che l'ultimo bin sarà un intervallo aperto verso destra. Gli attesi vengono calcolati come $A_j = n P_{H_0}(X_i \in B_j) = n \int_{B_j} f_0(t) dt$

## Estensione a [[distribuzione|legge]] specificata a meno di parametri
[[test-statistico|test]] che si può usare anche per la [[gaussiana|gaussianità]]. Il [[test-statistico|test]] procede esattamente come quello a [[distribuzione|legge]] qualsiasi, l'unica differenza è che bisogna togliere dal numero di gradi di libertà della [[chi-quadro|chi quadro]] anche il numero di parametri stimato $p$. Quindi il [[test-statistico|test]] verrebbe svolto in questo modo: 

### Esempio per l'estensione a [[distribuzione|legge]] specificata a meno di parametri
Se volessimo valutare la [[gaussiana|gaussianità]] di un certo [[inferenza-statistica|campione]] ($H_0: X \sim \mathcal{N}$ e $H_1:  X \not \sim \mathcal{N}$), possiamo calcolare $\mu \approx \bar X$ e $\sigma \approx S$ dal [[inferenza-statistica|campione]] e fare il [[test-statistico|test]] a [[distribuzione|legge]] qualsiasi con $X \sim \mathcal{N}(\bar X, S^2)$, però quando faccio il [[test-statistico|test]] imposto $W \stackrel{H_0}{\dot \sim} \chi^2(k - p - 1)$.