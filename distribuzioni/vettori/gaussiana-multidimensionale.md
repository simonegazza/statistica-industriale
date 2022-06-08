---
title: "Gaussiana multidimensionale"
---
# Gaussiana multidimensionale
Un [[vettori-aleatori|vettore aleatorio]] $\bold{Z} = (Z_1, Z_2, \ldots, Z_n)$ ha legge gaussiana $n$-dimensionale se $\forall \bold{v} \in \mathbb{R}^n$ abbiamo che $\bold{v} \cdot \bold{Z}$ ha legge [[gaussiana]].

Si noti che non basta che le componenti siano [[gaussiana|gaussiane]].

Si noti anche che $\bold{v} \cdot \bold{Z} = \sum_{i = 1}^n v_i Z_i$, quindi in particolare se $\bold{Z}$ è gaussiano, allora anche $\sum_{i = 1}^n Z_i$ è [[gaussiana]]. Questo succede anche se le $Z_i$ **non** sono [[indipendenza|indipendenti]] (per la *super* riproducibilità della [[gaussiana]]).

Si noti che può essere non simmetrica in tutte le direzioni. In particolare la [[media]] indicherà le coordinate del centro della distribuzione, la [[varianza]] in realtà è rappresentata dalla [[vettori-aleatori|matrice di covarianza]] che dirà come sono correlate le dimensioni fra loro e quanto si allontanano dal centro. Queste due determinano completamente un vettore gaussiano.

Se la [[vettori-aleatori|matrice di covarianza]] è invertibile allora $\bold{Z}$ ha pdf (altrimenti avrei alcune direzioni in cui trovo una [[delta-dirac|delta di Dirac]]):
$$
    f_Z(x) = (2\pi)^{-\frac{n}{2}} \cdot \sqrt{C(\bold{Z}^{-1})} \cdot e^{-\frac{1}{2}(x - \mu)^T \cdot C(\bold{Z})^{-1}(x - \mu)}
$$
con $C(\bold{Z})$ la matrice di covarianza e $\mu = E(\bold{Z})$.

Se $C(\bold{Z}) = I$ allora le $Z_1, Z_2, \ldots, Z_n \sim \mathcal{N}(0, 1)$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]] e simmetria sferica con $f_Z(x) = (2^\pi)^{-\frac{n}{2}} \cdot 1 \cdot e^{-\frac{1}{2}(x - 0)^T \cdot C(\bold{Z})^{-1}(x - 0)} = C \cdot e^{-\frac{1}{2}\|x\|^2}$. Si noti che sempre in questo caso si verifica che $\|\bold{Z}\|^2 \sim \chi^2(n)$ con $\chi$ la [[chi-quadro|chi quadro]].

Guardando il grafico è possibile tracciare delle curve di livello. Se le variabili sono [[indipendenza|indipendenti]] fra loro, allora le curve di livello sono circolari. Se gli assi sono correlati positivamente (negativamente) allora sono degli ellissi che hanno come diagonale principale quella del primo-terzo (secondo-quarto) quadrante.

Si noti che esiste un caso degere in cui una delle variabili è una [[delta-dirac|delta di Dirac]]; l'effetto ottenuto sarà che la componente lungo un asse sarà $0$.

<img src="https://www.mathworks.com/help/examples/stats/win64/ComputeTheMultivariateNormalPdfExample_01.png" alt="grafico della distribuzione" width=700>

## Verifica
Per verificare che un vettore sia effettivamente gaussiano possiamo:
- controllare che abbia componenti gaussiani indipendenti fra loro (questo lo posso anche generare)
- se $N \in M_{n \times m}$ e $\bold{Z}$ è gaussiano di dimensione $n$ allora $N\bold{Z}$ è un vettore gaussiano di dimensione $m$

# Generazione
Supponiamo di voler generare un [[vettori-aleatori|vettore]] [[gaussiana|gaussiano]] di [[distribuzione|legge]] assegnata $\mathcal{N}(\mu, \Sigma)$. L'unica possibilità è generare la versione di componenti indipendenti $Z \sim \mathcal{N}(?, ?)$ e poi costrure $X = N Z + a$ con $N$ e $a$ opportune. Questo è possibile farlo tramite l'[[analisi-componenti-principali|analisi delle componenti principali]].

Sia $V$ la matrice di autovettori di $\Sigma$ e $\lambda$ il vettore degli autovalori, e supponiamo che $X \sim \mathcal{N}(\mu, \Sigma)$. Allora sappiamo che $V^TX$ è:
1) [[vettori-aleatori|vettore]] [[gaussiana|gaussiano]]
2) $C(V^TX) = diag(\lambda)$
3) $E(V^TX) = V^T\mu$
4) quindi $V^TX \sim \mathcal{N}(V^T\mu, diag(\lambda))$

Possiamo quindi usare $V^T(X-\mu) = V^TX - V^T\mu$, quindi per lo stesso ragionamento ho $Z \sim \mathcal{N}(0, diag(\lambda))$, allora parto dal generare $Z$ come appena descritto, poi $\forall i = 1, 2, \ldots, n$ genero $Z_i \sim \mathcal{N}(0, \lambda_i)$ e successivamente pongo $X \coloneqq VZ + \mu$
