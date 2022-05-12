---
title: "Processo di Bernoulli"
---

Il processo di Bernoulli è una successione di variabili aleatorie i.i.d (indipendenti identicamente distribuite) della forma $Y_1, Y_2, \ldots Y_n \sim \mathrm{bin}(1,p)$ dette _prove di Bernoulli_.

Si dimostra che $Y_1 + Y_2 + \ldots + Y_n = S_n$ [[binomiale]] di parametri $n$ e $p$ (ovvero $S_n \sim \mathrm{bin}(n,p)$).

Si dimostra anche che se nominiamo $X$ la variabile aleatoria di che conta il numero di successi fino al primo successo, allora $X$ è [[geometrica]], ovvero $X \sim \mathrm{geom}(p)$ (con $p$ uguale a tutte le prove).

Si dimostra che la [[binomiale-negativa|binomiale negativa o distribuzione di Pascal]] proviene dal processo di Bernoulli contando il numero di prove prima del n-esimo successo, infatti per $n = 1$ è una [[geometrica]] (con $p$ uguale a tutte le prove), ovvero $\mathrm{geom}(1, p) \sim \mathrm{negbin}(1, p)$.

Si dimostra che prendendo eventi che si realizzano istantaneamente $S_1, S_2, \ldots, S_n$, con intertempi $T_1, T_2, \ldots, T_n$ di tipo $\mathrm{expo}(\lambda)$ indipendenti e identicamente distribuiti, e contando il numero di realizzazioni degli eventi $N_t$ dal momento $0$ al momento $t$ allora si ottiene una [[esponenziale]] di tipo $N_t \sim \mathrm{expo}(\lambda)$.