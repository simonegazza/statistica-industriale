---
title: "Dirichlet"
---
# Dirichlet
La Dirichlet è un [[vettori-aleatori|vettore aleatorio]] di [[probabilita|probabilità]] [[variabili-aleatorie#Continue|continuo]].

Si indica con $X \sim \mathrm{Dirichlet}(\alpha)$ in cui $\alpha = (\alpha_1, \alpha_2, \ldots, \alpha_n)$, con $n$ la dimensione del vettore (e quindi della distribuzione). Si noti che si tratta di un vettore aleatorio tale che $X_i \in [0,1]$. Si noti che le varie $X_i$ **non** sono [[indipendenza|indipendenti]] fra loro, poichè $X_1 + X_2 + \ldots + X_n = 1$.

La [[variabili-aleatorie#Discrete|funzione di densità di probabilità]] è:
$$
f_X(x) = C_\alpha \cdot x_1^{\alpha_1 - 1} \cdot x_2^{\alpha_2 - 1} \cdots \cdot x_n^{\alpha_n - 1} = C_\alpha \cdot \prod_{i = 1}^n x_i^{\alpha_i - 1}
$$
con $C_\alpha$ un qualche coefficiente

Si noti che per $n = 2$ la Dirichlet è bene una [[beta]].

Si noti che tipicamente le $X_i \propto \alpha_i$.

Ha [[media]] $E(\bold{X}) = (E(X_1), E(X_2), \ldots, E(X_n)) = (\frac{\alpha_1}{\sum_{i = 1}^n \alpha_i}, \frac{\alpha_2}{\sum_{i = 1}^n \alpha_i}, \ldots, \frac{\alpha_n}{\sum_{i = 1}^n \alpha_i})$.

Caso per $n = 2$ al variare di $\alpha_1 = \alpha_2 = a$
<img src="https://upload.wikimedia.org/wikipedia/commons/5/54/LogDirichletDensity-alpha_0.3_to_alpha_2.0.gif" alt="grafico della distribuzione" width=700>

È possibile generare la multinomiale in 2 modi differenti (entrambi intuitivamente simili a quello che si fa per la generazione della [[multinomiale]]):
- posso generare le $n$ [[gamma]] $T_i \sim \mathrm{gamma}(\alpha_1, 1)$. Si noti che il secondo parametro della [[gamma]] è stato messo a $1$ perchè comunque la generazione è indipendente rispetto a quel parametro (perchè corrisponde ad una dilatazione, che tanto riscaleremo e inoltre così che se sia $\lambda$ o $\beta$ il valore sarà sempre 1). Avrò che le $X_i = \frac{T_i}{\sum_{i = 1}^n T_i}$
- genero $\bold{X}$ componente per componente direttamente: infatti $X_1 = \mathrm{beta}(\alpha, \beta)$, $X_2 = \mathrm{bin}(\alpha - X_1, \frac{\beta_2}{\beta_2 + \ldots + \beta_k})$, $X_2 = \mathrm{bin}(\alpha - X_1 - X_2, \frac{\beta_3}{\beta_3 + \ldots + \beta_k})$, $\ldots$
