---
title: "Processo di Bernoulli"
---
# Processo di Bernoulli
Il processo di Bernoulli è una successione di variabili aleatorie [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]] della forma $Y_1, Y_2, \ldots Y_n \sim \mathrm{bin}(1,p)$ dette _prove di Bernoulli_.

È la controparte discreta del [[processo-poisson|processo di Poisson]].

Si dimostra che $Y_1 + Y_2 + \ldots + Y_n = S_n$ [[binomiale]] di parametri $n$ e $p$ (ovvero $S_n \sim \mathrm{bin}(n,p)$).

Si dimostra anche che se nominiamo $X$ la variabile aleatoria di che conta il numero di successi fino al primo successo, allora $X$ è [[geometrica]], ovvero $X \sim \mathrm{geom}(p)$ (con $p$ uguale a tutte le prove).

Si dimostra che la [[binomiale-negativa|binomiale negativa o distribuzione di Pascal]] proviene dal processo di Bernoulli contando il numero di prove prima del n-esimo successo, infatti per $n = 1$ è una [[geometrica]] (con $p$ uguale a tutte le prove), ovvero $\mathrm{geom}(1, p) \sim \mathrm{negbin}(1, p)$.