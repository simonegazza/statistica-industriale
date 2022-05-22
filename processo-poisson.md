---
title: "Processo di Poisson"
---
# Processo di Poisson
Supponiamo di avere una serie di eventi [[indipendenza|indipendenti]] $S_1, S_2, \ldots, S_n$ che si realizzano istantaneamente e che possono accadere continuamente nel tempo. Avremo una collezione di variabili aleatorie chiamata $N_t$ che rappresenta il numero di eventi occorsi dal tempo $0$ al tempo $t$. Tali eventi quindi avvengono con intertempi $T_1, T_2, \ldots T_n$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]].

Se cerchiamo di discretizzare il processo dividendo l'intervallo $[0, t]$ in un gran numero di sotto-intervalli di larghezza $\Delta = \frac{t}{n}$ allora otterremo una $N_t \sim \mathrm{bin}(n, p) \sim \mathrm{Pois}(np)$ [[binomiale]] che va come una [[poissoniana]] con $p$ fissato in modo tale che $x_i \coloneqq \frac{T_i}{\Delta} = T_i \cdot \frac{n}{t} \sim \mathrm{geom}(p)$ [[geometrica]]. Perciò avremo che $\frac{1}{p} = E(x_i) = \frac{1}{\lambda} \cdot \frac{n}{t} \iff \lambda t = np$.

È la controparte continua del [[processo-bernoulli|processo di Bernoulli]].

Sono anche un esempio di catena di Markov a tempo continuo.

Si dimostra che se gli intertempi $T_1, T_2, \ldots T_n$ hanno legge [[esponenziale]] di parametro $\lambda$, ovvero $T_1, T_2, \ldots T_n \sim \mathrm{expo}(\lambda)$, allora il numero di eventi $N_t \sim Pois(\lambda t)$ ha legge [[poissoniana]]. Più generalmente, si dimostra che il numero di eventi intercorsi fra il tempo $a$ e il tempo $b$ è dato come $N_b - N_a$ ed è una [[poissoniana]].
