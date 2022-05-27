---
title: "Cdf empirica"
---
# Cdf empirica
Se supponiamo di avere una serie di dati allora possiamo provare ad ottenre la [[variabili-aleatorie#Continue|CdF]] empirica, che è la distribuzione che la serie di dati ha. Questa distribuzione approssimerà alla distribuzione reale dei dati e ci darà buoni indizi sull'analisi da applicare successivamente.

Per farlo bisogna:
- ordinare i dati empirici, in modo da ottenere l'inversa della [[variabili-aleatorie#Continue|CdF]]
- "ribaltare" il grafico lungo $y = x$ in modo da ottenere la [[variabili-aleatorie#Continue|CdF]] empirica

## Formalmente
Supponiamo di avere un campione $x_1, x_2, \ldots x_n$ proveniente da una distribuzione con [[variabili-aleatorie#Continue|CdF]] $F$. Ordino il campione come $x_{(1)}, x_{(2)}, \ldots x_{(n)}$. Allora posso stimare la [[variabili-aleatorie#Continue|CdF]] $F$ come
$$
F(t) \coloneqq P(X \le t) \approx \frac{\#\{x_i : x_i \le t\}}{n} =: \hat F(t)
$$

Si noti che questa corrisponderebbe alla stima della probabilità in ogni punto della [[variabili-aleatorie#Continue|CdF]].

Una osservazione importante da fare è che $\hat F(x_{(i)}) = \frac{i}{n}$, quindi i punti del tipo $(x_{(i)}, \frac{i - \frac{1}{2}}{n})$ per $i = 1, \ldots, n$ ci danno un'approssimazione del grafico di $\hat F$.

Si noti che abbiamo usato $\frac{i - \frac{1}{2}}{n}$, e quindi siamo partiti da $\frac{1}{2n}$ e siamo arrivati a $\frac{n - \frac{1}{2}}{n}$. Questo per evitare di avere dei punti che vadano a $0$ o a $1$ (infatti abbiamo fatto uno spostamento di mezzo punto), perchè questo altrimenti costituisce un problema di allineamento.

Dato che i punti hanno una forma del tipo $(x_{(i)}, \frac{i - \frac{1}{2}}{n})$, la $\hat F$ è costante a tratti

Altra osservazione: per vedere l'andamento (**e solo l'andamento**, non stiamo parlando anche dei valori che questa assume, ma solo una **visione qualitativa**) non è necessario dividere per $n$.

<img src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Empirical_CDF%2C_CDF_and_Confidence_Interval_plots_for_various_sample_sizes_of_Normal_Distribution.png" alt="CdF empirica" width=700 style="background: white">