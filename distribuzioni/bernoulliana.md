---
title: "Bernoulliana"
---
La Bernoulliana è una distribuzione di probabilità discreta.

Si indica con $X \sim \mathrm{bin}(1, p)$ in cui il parametro $p \in [0,1]$ indica la probabilità del verificarsi di un singolo evento (una sola volta).

Questa distribuzione di probabilità ha solo due valori possibili: $0$ o $1$. Se l'evento si verifica, la bernoulliana avrà valore $1$, se non si verifica avrà valore $0$. Quindi:
$$
\mathrm{bin}(1,p) = \bigg\{
    \begin{array}{lr}
        p & \text{for } P(X = 1)\\
        1--p & \text{for } P(X = 0)
    \end{array}
$$

Si noti che il _processo di Bernoulli_ ci consente di trasformare $n$ ripetizioni della stessa Bernoulliana (avente la stessa probabilità $p$) in una binomiale.
Più formalmente: il processo di Bernoulli è una successione di variabili aleatorie i.i.d (indipendenti identicamente distribuite) della forma $X_1, X_2, \ldots X_n \sim bin(1,p)$ dette _prove di Bernoulli_. Si dimostra che $X_1 + X_2 + \ldots + X_n = S_n$ [[binomiale]] di parametri $n$ e $p$ (ovvero $S_n \sim bin(n,p)$).

Ha media $E(X) = p$ e $Var(X) = p(1-p)$.

<img src="https://upload.wikimedia.org/wikipedia/commons/7/74/Bernoulli_Distribution.PNG" alt="grafico della distribuzione" width=700>

