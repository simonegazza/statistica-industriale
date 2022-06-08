---
title: "Teorema di Cochran"
---
# Distribuzione degli stimatori nel caso gaussiano
Supponiamo di avere un [[gaussiana-multidimensionale|vettore gaussiano]] di $X_i \sim \mathcal{N}(\mu, \sigma^2)$ [[indipendenza|indipendenti]], quindi $X \sim \mathcal{N}((\mu, \mu, \ldots, \mu), \Sigma = \sigma^2 I)$ con
$$
\Sigma = \sigma^2 I = \begin{pmatrix}
    \sigma^2 &  0       & \ldots & 0 \\
    0        & \sigma^2 & \ldots & 0\\
    \vdots   & \vdots   & \ddots & \vdots \\
    0        & 0        & \ldots & \sigma^2
\end{pmatrix}
$$

Gli stimatori che si usano sono:
$$
\text{La media campionaria: } \bar X \coloneqq \frac{1}{n} \sum_{i = 1}^n X_i \\
\text{La varianza campionaria: } S_X^2 \coloneqq \frac{1}{n - 1} \sum_{i = 1}^n (X_i - \bar X)^2 \\
\text{La devianza campionaria (o \textit{sum of squares}): } SS_X \coloneqq \sum_{i = 1}^n (X_i - \bar X)^2 = \sum_i X_i^2 - n \bar X^2 \\
$$

Si noti che su un grafico avremo che il centro della distribuzione (e quindi la [[media]]) sta su una retta, e la distribuzione stessa è una sfera (se vista dall'alto). Ora la realizzazione di un punto $X$, genera un vettore $\pi_v(X) = (\bar X, \bar X, \ldots, \bar X)$. Il vettore della proiezione è $X - \pi_x(v) = (X_1 - \bar X, X_2 - \bar X, \ldots, X_n - \bar X)$, quindi per il teorema di Pitagora avrà che $\| X - \pi_x(v) \| = (X_1 + \bar X)^2 + (X_2 - \bar X)^2 +  \ldots + (X_n - \bar X)^2 = SS_X$.

Quindi la distanza è sostanzialmente la varianza campionaria (a meno di una costante) e la proiezione che è la media aritmetica.

# Teorema di Cochran
$\bar X \sim \mathcal{N}(\mu, \frac{\sigma^2}{n})$ [[gaussiana]], $\frac{SS_X}{\sigma^2} \sim \chi^2(n-1)$ [[chi-quadro|chi quadro]] e fra loro [[indipendenza|indipendenti]].
Intuitivamente: la direzione su cui giace la [[media]] è una [[gaussiana]]. Anche la proiezione su cui giace un punto osservato è una [[gaussiana]].
Entrambi gli [[statistica-componenti-fondamentali|stimatori]] sopra elencati sono [[statistica-componenti-fondamentali#Stimatore corretto|corretti]] e [[statistica-componenti-fondamentali#Stimatore consistente|consistenti]]. Si noti che $E(S_X) < E(S_X^2) = \sigma^2$ e quindi $E(S_X) < \sigma$, quindi $S_X$ stima per difetto $\sigma$.
Intuitivamente il teorema di Cochram dice che se prendi una [[gaussiana]] sferica e la giri sugli assi, questa rimane sferica. Ci sono diversi enunciati, uno di questi è il seguente.

## Formalmente (soprattutto per applicazioni pratiche)
Supponiamo di avere $X_1, X_2, \ldots, X_n \sim \mathcal{N}(\mu_i, \sigma)$ [[gaussiana|gaussiane]] [[indipendenza|indipendenti]] con $\sigma$ comune a tutte le [[variabili-aleatorie|vv.aa.]] (quindi i dati sono detti essere **omoschedastici**). Supponiamo di sapere che $\mu = (\mu_1, \mu_2, \ldots, \mu_n) \in V \subseteq \mathbb{R}^n$ con $k = \dim(V)$
Allora:
1) il [[statistica-componenti-fondamentali#Stimatori di massima verosimiglianza|MLE]] di $\mu$ è ortogonale a $\pi_V(X)$, quindi $\mu \perp \pi_V(X)$
2) $\pi_V(X)$ è [[statistica-componenti-fondamentali#Stimatore corretto|corretto]]
3) $W \coloneqq \| X - \pi_V(X) \|^2$ è [[indipendenza|indipendente]] da $\pi_V(X)$ e $\frac{W}{\sigma^2} \sim \chi^2(n-k)$ [[chi-quadro|chi quadro]].

## Dimostrazione
Premesse: siano $v_1, \ldots, v_k$ base ortonormale di $V_k$ che estendo a base di $\mathbb{R}^n$ come $v_1, \ldots, v_k, v_{k+1}, \ldots, v_n$.
Si noti inoltre che $\pi_V(x) = \sum_{i = 1}^k (v_i \cdot x) v_i$ con $(v_i \cdot x)$ prodotto scalare.
Si noti anche che $x = \sum_{i = 1}^n (v_i \cdot x) v_i$
Quindi $x - \pi_V(x) = \sum_{i = k + 1}^n (v_i \cdot x) v_i$.

### Dimostrazione di 1
la likelihood è
$$
L(X) = f_X(x_1, x_2, \ldots, x_n) = \\
(2\pi)^{-\frac{n}{2}} \cdot \sqrt{C(\bold{X}^{-1})} \cdot e^{-\frac{1}{2}(x - \mu)^T \cdot C(\bold{X})^{-1}(x - \mu)} = \\
k \cdot e^{-\frac{1}{2}(x - \mu)^T \cdot C(\bold{X})^{-1}(x - \mu)}
$$
con $k = (2\pi)^{-\frac{n}{2}} \cdot \sqrt{C(\bold{X}^{-1})}$
Ora si noti che però $C(X) = (\sigma^2 I)^{-1} = \frac{1}{\sigma^2}I$, e quindi avrò che
$$
L(X) = k \cdot e^{-\frac{1}{2\sigma^2}\|x - \mu\|^2}
$$
Ora bisogna massimizzarlo, però si tratta di un esponenziale con segno meno, quindi devo minimizzare l'espressione:
$$
\hat \mu = \argmax_{\mu \in V} L(\mu) = \argmin_{\mu \in V} \| x-\mu \|^2
$$
Quindi lo stimatore di $\mu$ detto $\hat \mu$ deve essere quello che minimizza la distanza. Dato che minimizza la distanza stiamo parlando della proiezione ortogonale. Da qui si ricava che:
$$
\hat \mu =\pi_V(x) \quad \square.
$$

### Dimostrazione di 2
Ora dobbiamo dimostrare che $\pi_V(X)$ è [[statistica-componenti-fondamentali#Stimatore corretto|corretto]].
$$
E(\pi_V(X)) = E\Bigg(\sum_{i = 1}^k (v_i \cdot X) v_i\Bigg) \stackrel{lin.}{=} \\
\sum_{i = 1}^k (v_i \cdot E(X)) v_i = \sum_{i = 1}^k (v_i \cdot \mu) v_i \stackrel{def.}{=} \\ \space \\
 \pi_V(\mu) \stackrel{\mu \in V}{=} \mu \quad \square.
$$

### Dimostrazione di 3
In questa dimostrazione devo intuitivamente ruotare la sfera e mettermi nel riferimento giusto. Ruotiamo il riferimento cartesiano in modo da usare le componenti $v_1, \ldots, v_n$. Usiamo come matrice $N$ che ha (tutti) i versori sulle righe:
$$
N = \begin{pmatrix}
    - & v_1    & - \\
    - & v_2    & - \\
      & \vdots &   \\
    - & v_n   & - \\
\end{pmatrix}
$$
Dato che la matrice è quadrata e ha sulle righe dei versori ortonormali, allora la matrice stessa è ortogonale (per costruzione).

Questo implica che $N^T N = NN^T = I$, e cioè $N^T = N^{-1}$ per cui questa è una rotazione di $\mathbb{R}^n$.

Questa è una matrice costruita in modo tale che se applicata ad un versore, ritorna un vettore colonna:
$$
e_i = \begin{pmatrix}
    0 \\
    \vdots \\
    0 \\
    1 \\
    0 \\
    \vdots \\
    0
\end{pmatrix}
$$

Prendiamo ora un generico vettore (non aleatorio) $x \in \mathbb{R}^n$

Ora posso applicare $N$ alla proiezione, al vettore $x$ e a $x - \pi_V(x)$ quindi, cominciando dalla proiezione:
$$
N \pi_V(x) = N \sum_{i = 1}^k (v_i \cdot x) v_i
$$
Sappiamo tuttavia che il prodotto scalare genera un numero e che l'applicazione della matrice ad un numero è commutativa, quindi possiamo scrivere:
$$
N \sum_{i = 1}^k (v_i \cdot x) v_i = \sum_{i = 1}^k (v_i \cdot x) N v_i \stackrel{def.}{=} \sum_{i = 1}^k (v_i \cdot x) e_i
$$
Quindi il vettore $N \pi_V(x) = (v_1 \cdot x_1, \ldots,  v_k \cdot x_k, 0, \ldots, 0)$

Allo stesso modo anche l'applicazione al vettore $x$ risulta:
$$
N x = N \sum_{i = 1}^n (v_i \cdot x) v_i = \sum_{i = 1}^n (v_i \cdot x) N v_i \stackrel{def.}{=} \sum_{i = 1}^n (v_i \cdot x) e_i
$$

Possiamo applicare la stessa cosa a $x - \pi_V(x)$:
$$
N (x - \pi_V(x)) = N \sum_{i = k + 1}^n (v_i \cdot x) v_i = \sum_{i = k + 1}^n (v_i \cdot x) N v_i \stackrel{def.}{=} \sum_{i = k + 1}^n (v_i \cdot x) e_i
$$
Quindi il vettore $N (x - \pi_V(x)) = (0, \ldots, 0, v_{k + 1} \cdot x_{k + 1}, \ldots, v_n \cdot x_n)$

Ora possiamo prendere $X \sim \mathcal{N}(\mu, \sigma^2 I)$, e fare $Z \coloneqq NX \sim \mathcal{N}(N\mu, \sigma^2 NIN^T = \sigma^2I)$, in cui la matrice di covarianza è rimasta la stessa di prima per le proprietà di $N$. Si noti che ciascuna $Z_i \sim \mathcal{N}([N\mu]_i, \sigma^2)$ (con $[N\mu]_i$ la $i$-esima componente del vettore $N\mu$).

$Z$ ha componenti [[indipendenza|indipendenti]]. In particolare i [[vettori-aleatori|vettori]] $(Z_1, \ldots, Z_k, 0, \ldots, 0)$ e $(0, \ldots, 0, Z_{k + 1}, \ldots, Z_n)$ sono [[indipendenza|indipendenti]].

Però, visto quello scritto sopra, questi [[vettori-aleatori|vettori]] sono anche uguali a $N\pi_V(X)$ e $N(X - \pi_V(X))$. Per cui $N\pi_V(X) = (Z_1, \ldots, Z_k, 0, \ldots, 0)$ e $N(X - \pi_V(X)) = (0, \ldots, 0, Z_{k + 1}, \ldots, Z_n)$

Dato che questi due sono [[indipendenza|indipendenti]], allora anche i [[vettori-aleatori|vettori]] originali sono [[indipendenza|indipendenti]], quindi mi basta moltiplicare entrambi per $N^T$ per scoprire i [[vettori-aleatori|vettori]] originali, quindi $\pi_V(X)$ e $X - \pi_V(X)$ sono [[indipendenza|indipendenti]].

Ora dobbiamo mostrare che $W \coloneqq \| X - \pi_V(X) \|^2 = \|N(X - \pi_V(X))\|^2$ poichè $N$ è una rotazione, quindi non cambia la norma del [[vettori-aleatori|vettore]].

Tuttavia, per quanto visto sopra:
$$
\|N(X - \pi_V(X))\|^2 = \|(0, \ldots, 0, Z_{k + 1}, \ldots, Z_n)\|^2 = \sum_{i = k + 1}^n Z_i^2
$$
Ma tutti questi $Z_i$ sono della forma $Z_i \sim \mathcal{N}(0, \sigma^2)$ quindi
$$
\frac{W}{\sigma} = \sum_{i = k + 1}^n \bigg(\frac{Z_i}{\sigma}\bigg)^2 \sim \chi^2(n-k) \quad \square.
$$
