---
title: "Anova"
---
# Anova
Si tratta di una variante della [[regressione]] con variabili di ingresso [[tipologie-variabili#Categoriche|categoriche]]. Ce ne sono 3 tipologie principali:
- anova **a una via**: una sola variabile di ingresso
- anova **a due vie**: due variabili di ingresso con esattamente un'osservazione per combinazione delle due variabili
- anova **a due vie con repliche**: più di un'osservazione per combinazione

Il framework comunque **è molto rigido**, e spesso chiede di non avere troppe categorie

## Anova ad una via
Come detto, ammette una variabile [[tipologie-variabili#Categoriche|categorica]], in cui ogni categoria può avere una [[media]] differente. Si noti tuttavia che la variabile di risposta $Y$ è [[tipologie-variabili#Numeriche|numerica]] e presenta rumore additivo [[gaussiana|gaussiano]] [[varianza|omoschedastico]].
In questo caso, il modello è
$$
Y = \mu_x + e \qquad \text{con } e \sim \mathcal{N}(0, \sigma^2), x \in \{1, 2, \ldots, m\} \text{ categorie}
$$

Si noti che ogni categoria deve avere la propria [[media]], che può essere diversa da quella delle altre categorie, $\mu(x)$.

Nella formalizzazione del modello avremo quindi che $Y \sim \mathcal{N}(\mu(x), \sigma^2)$ e quindi **i nostri dati sono $m$ campioni di tipo gaussiano indipendenti fra loro [[gaussiana|gaussiani]]**.

Vi sono **due modi** principali di organizzare i dati per questo modello: nel primo caso organizziamo i dati **per colonne** (e questo è il modo voluto dalla teoria), andando elencare in $m$ colonne i dati dei [[inferenza-statistica#Componenti alla base della statistica inferenziale|campioni]] [[gaussiana|gaussiani]] di ogni categoria, nel secondo caso andremo a raccogliere i dati riga per riga in triplette $(\mathrm{id}, x, y)$ con $x$ la categoria e $y$ la risposta.

Quindi il nostro [[inferenza-statistica#Componenti alla base della statistica inferenziale|campione]] totale sarà formato da $Y_{i,j} \sim \mathcal{N}(\mu_i, \sigma^2)$ [[indipendenza|indipendenti]], con $i = x$ categoria. I parametri incogniti di questo modello sono le [[media|medie]] $\mu_i$ e $\sigma$. Gli [[inferenza-statistica#Componenti alla base della statistica inferenziale|stimatori]] a nostra disposizione sono
$$
\mu_i \approx Y_{i, *} \coloneqq \frac{1}{n_i} \sum_{j = 1}^{n_i} Y_{i, j} \sim \mathcal{N}(\mu_i, \frac{\sigma^2}{n_i})\\
\sigma^2 \approx S_i^2 \coloneqq \frac{1}{n_i - 1} \sum_{j = 1}^{n_i} (Y_{i, j} - Y_{i, *})^2
$$

Questi $S_i$ in particolare sono $m$ [[inferenza-statistica#Componenti alla base della statistica inferenziale|stimatori]] [[indipendenza|indipendenti]] di $\sigma^2$, per cui lo stimatore di tipo [[due-campioni-gaussiani-univariati|pooled]] è l'unico modo di metterli assieme, ovvero:
$$
\sigma^2 \approx S_W^2 \coloneqq S_p^2 \coloneqq \sum_{i = 1}^m \frac{n_i - 1}{N - m} S_i^2 = \frac{1}{N - m} \sum_{i = 1}^m \sum_{j = 1}^{n_i} (Y_{i, j} - Y_{i, m})^2 =: \frac{SS_W}{N - m} \qquad \text{ con } N \coloneqq \sum_{i = 1}^m n_i \\
\frac{S_W^2}{\sigma^2} (N - m) \sim \chi^2(N - m) \\
R_{i, j} \coloneqq Y_{i,j} - Y_{i, *}
$$
Si noti che $S_W$ è anche detta **[[varianza]] within** (ovvero *entro i campioni*)

### Test fondamentale dell'anova ad una via
Diremo $H_0: \mu_1 = \mu_2 = \ldots = \mu_m$ e $H_1: \text{almeno una diversa}$.

Calcoliamo anche un secondo stimatore, detto **$S_B$ stimatore between della [[varianza]] sotto $H_0$**
$$
S_B \coloneqq \sqrt{\frac{SS_B}{N - 1}} \qquad
SS_B \coloneqq SS_Y - SS_W \qquad \text{ con } SS_Y \coloneqq \sum_{i = 1}^m \sum_{j = 1}^{n_i} (Y_{i,j} \bar Y)^2
$$

Sotto $H_0$ abbiamo che $\frac{SS_B^2}{\sigma^2} \sim \chi^2(m - 1)$ indipendente da $SS_W$. Possiamo quindi scrivere la statistica del test:
$$
T \coloneqq \frac{S_B^2}{S_W^2} = \frac{SSB/(m - 1)}{SS_W/(N - m)} \stackrel{H_0}{\sim} F(m - 1; N - m) 
$$

Si noti che $S_B^2$ (che assomiglia alla [[varianza]] campionaria) viene tanto più grande quanto è più è falsa $H_0$, quindi faremo un test unilaterale.

Se $H_0$ si può accettare, allora forse conviene ignorare la categoria e studiare i campioni come [[gaussiana|gaussiani]] [[indipendenza#Indipendenti e identicamente distribuite|i.i.d.]]

## Anova a due vie (con repliche)
In questo caso abbiamo due variabili di ingresso $x_1 \in \{1, 2, \ldots, m\}$ e $x_2 \in \{1, 2, \ldots, n\}$ e $l$ numero di replice.

I dati possono essere disposto in due modi differenti: $x_1$ sulle righe e $x_2$ sulle colonne, raggruppati in $l$ repliche per valore, fino ad avere $m$ gruppi di repliche consecutive su $n$ colonne; oppure possiamo disporre di dati in $N$ quadruple $(\mathrm{id}, x_1, x_2, Y)$, però in questo caso occorre contare le repliche e vanno gestite (tipicamente eliminandole) fino ad ottenere un $l$ costante.

In queto modello abbiamo $Y_{i, j, k} \sim \mathcal{N}(\mu_{i, j}, \sigma^2)$ con $i = 1, \ldots, m$ numerosità di $x_1$, $j = 1, \ldots, n$ numerosità di $x_2$, $k = 1, \ldots, l$ repliche. Questo modello ha quindi $(\mu_{i, 1}, \mu_{i, 1}, \ldots, \mu_{m, m}, \sigma)$ stimabili solo se $l \ge 2$.
Tipicamente, **nell'anova <ins>a due vie (senza repliche)</ins> si cerca di ricondursi ad un modello additivo più semplice** di questo tipo
$$
\mu_{i, j} = \mu + \alpha_i + \beta_j
$$
con **$\alpha_i$ effetto della riga e $\beta_j$ e della colonna**.
Invece, **nell'anova <ins>a due vie con repliche</ins> si cerca di ricondursi al seguente modello**
$$
\mu_{i, j} = \mu + \alpha_i + \beta_j + \gamma_{i,j}
$$
con **$\gamma_{i,j}$ il termine di interazione**

Si noti che questa riscrittura è sempre possibile perchè si impone che gli effetti di righe, colonne e interazioni abbiano media nulla.

Si noti anche che **esiste un test** $H_0: \forall i, j \quad  \gamma_{i, j} = 0$ e $H_1: \exists \gamma_{i, j} \not = 0$ **che ci consente di eliminare le repliche** (quindi poi $l = 1$) dove si sostituiscono i dati originali $Y_{i, j, k}$ con le medie $Y_{i, j, *}$. Tuttavia se viene $H_1$ si deve tenere **il modello generalissimo ed è più difficile da interpretare**.

### Test fondamentale dell'anova a due vie (senza repliche)
In realtà son **due** test, uno per le righe e uno per le colonne
$$
\text{righe } H_0: \alpha_1 = \alpha_2 = \ldots = \alpha_m = 0 \qquad H_1: \exists i | \alpha_i \not = 0 \\
\text{colonne } H_0: \beta_1 = \beta_2 = \ldots = \beta_n = 0 \qquad H_1: \exists j | \beta_j \not = 0
$$
che ci dice che $Y$ non dipende da $x_1$ (intuitivamente, le righe) e $Y$ non dipende da $x_2$ (ovvero le colonne).

Abbiamo i seguenti stimatori:
$$
Y_{i, j} \sim \mathcal{N}(\mu + \alpha_i + \beta_j, \sigma^2) \\
Y_{i, *} \sim \mathcal{N} \bigg(\mu + \alpha_i, \frac{\sigma^2}{n} \bigg) \\
Y_{*, j} \sim \mathcal{N} \bigg(\mu + \beta_j, \frac{\sigma^2}{m} \bigg) \\
Y_{i, j} \sim \mathcal{N} \bigg(\mu, \frac{\sigma^2}{mn} \bigg) \\

\text{righe: } SS_R \coloneqq n \sum_{i = 1}^m (X_{i, *} - X_{*,*})^2 \qquad \frac{SS_R}{\sigma^2} \sim \chi^2(m - 1) \\
\text{colonne: } SS_C \coloneqq m \sum_{j = 1}^n (X_{*, j} - X_{*,*})^2 \qquad \frac{SS_C}{\sigma^2} \sim \chi^2(n - 1) \\
\text{errore: } SS_E \coloneqq \sum_{i = 1}^m \sum_{j = 1}^n (X_{i, j} - X_{i,*} - X_{*, j} + X_{*, *})^2 = \sum_{i = 1}^m \sum_{j = 1}^n R_{i,j} \qquad \frac{SS_E}{\sigma^2} \sim \chi^2((n - 1)(m - 1)) \\
\sigma^2 \approx S_e^2 = \frac{SS_E}{(m-1)(n-1)} \text{ con } \frac{SS_E}{\sigma^2} \sim \chi^2((m - 1)(n - 1)) \text{ sempre corretto e indipendente dalle ipotesi }
$$
e le rispettive [[test-statistico#Funzionamento di un test statistico|statistiche]] e [[funzione-ancillare|funzioni ancillari]]
$$
\text{righe: } T \coloneqq D_{ts} \coloneqq \frac{SS_r}{SS_e} (n - 1) \sim F(m - 1; N) \qquad \alpha^* = P(F(m - 1; N) \ge D_{ts})
$$
$$
\text{colonne: } T \coloneqq D_{ts} \coloneqq \frac{SS_c}{SS_e} (m - 1) \sim F(n - 1; N) \qquad \alpha^* = P(F(n - 1; N) \ge D_{ts})
$$
**unilaterali sinistri**.

### Test fondamentale dell'anova a due vie con repliche
In questo caso abbiamo **tre** test:
$$
\text{righe } H_0: \alpha_1 = \alpha_2 = \ldots = \alpha_m = 0 \qquad H_1: \exists i | \alpha_i \not = 0 \\
\text{colonne } H_0: \beta_1 = \beta_2 = \ldots = \beta_n = 0 \qquad H_1: \exists j | \beta_j \not = 0 \\
\text{interazioni } H_0: \gamma_{i, 1} = \gamma_{1, 2} = \ldots = \gamma_{n, m} = 0 \qquad H_1: \exists i,j | \gamma_{i,j} \not = 0
$$
Con i seguenti stimatori:
$$
\text{righe: } SS_R \coloneqq nl \sum_{i = 1}^m (X_{i, *, *} - X_{*, *, *})^2 \qquad \frac{SS_R}{\sigma^2} \sim \chi^2(m - 1) \\
\text{colonne: } SS_C \coloneqq ml \sum_{j = 1}^n (X_{*, j, *} - X_{*, *, *})^2 \qquad \frac{SS_C}{\sigma^2} \sim \chi^2(n - 1) \\
\text{interazione: } SS_I \coloneqq l \sum_{i = 1}^m \sum_{j = 1}^n (X_{i, j, *} - X_{i, *, *} - X_{*, j, *} + X_{*, *, *})^2 \sim \chi^2((n - 1)(m - 1)) \\
\text{errore: } SS_E \coloneqq \sum_{k = 1}^l \sum_{i = 1}^m \sum_{j = 1}^n (X_{i, j, k} - X_{i,*})^2 = \sum_{i = 1}^m \sum_{j = 1}^n R_{i,j} \qquad \frac{SS_E}{\sigma^2} \sim \chi^2(nm(l - 1)) \\
$$
e le seguenti [[test-statistico#Funzionamento di un test statistico|statistiche]] e [[funzione-ancillare|funzioni ancillari]]:
$$
\text{righe: } T \coloneqq F_r \coloneqq \frac{SS_r / (m - 1)}{SS_e / (nm(l - 1))} \sim F(m - 1; nm(l - 1)) \qquad \alpha^* = P(F(m - 1; nm(l - 1)) \ge F_r)
$$
$$
\text{colonne: } T \coloneqq F_c \coloneqq \frac{SS_c / (n - 1)}{SS_e / (nm(l - 1))} \sim F(n - 1; nm(l - 1)) \qquad \alpha^* = P(F(n - 1; nm(l - 1)) \ge F_c)
$$
$$
\text{interazioni: } T \coloneqq F_i \coloneqq \frac{SS_I / ((n - 1)(m - 1))}{SS_e / (nm(l - 1))} \sim F(m - 1; N) \qquad \alpha^* = P(F((n - 1)(m - 1); nm(l - 1)) \ge F_i)
$$
$$
\sigma^2 \approx S_e^2 = \frac{SS_E}{mn(l-1)} \text{ con } \frac{SS_E}{\sigma^2} \sim \chi^2(mn(l-1)) \text{ sempre corretto e indipendente dalle ipotesi }
$$

Si noti che il test di interazione ci dice se usare il modello additivo o quello generale.

**Se l'esito sull'effetto di una variabile (riga o colonna) è $H_0$ allora si può considerare di eliminare quella variabile e ridursi all'anova ad una via.**
