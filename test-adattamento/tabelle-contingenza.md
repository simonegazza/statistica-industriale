---
title: "Tabelle di contingenza"
---
# Tabelle di contingenza
Servono per valutare se due variabili aleatorie sono legate da una qualche relazione (simmetrica), senza conoscerne le leggi.

Intuitivamente disporremo i nostri osservati in una tabella in cui la somma delle righe è equivalente fra loro, e anche la somma delle colonne sono equivalenti fra loro, ad esempio:

| occhi \ capelli | biondi | non biondi | Totale |
|-----------------|--------|------------|--------|
| chiari          | 21     | 19         | 40     |
| non chiari      | 9      | 51         | 60     |
| Totale          | 30     | 70         | 100    |

La filosofia di questo [[test-statistico|test]] è simile a quella del [[test-chi-quadro|test del chi quadro]], nel quale tipicamente è previsto che $X$ e $Y$ siano discrete e con pochi valori possibili, altrimenti posso dividere in bins se sono continue. 

Supponiamo di avere $(X_k, Y_k)$ e $k = 1, \ldots, N$ con $N$ la numerosità dei dati, dove $X_i \in \{1, 2, \ldots, m\}$ e $Y_j \in \{1, 2, \ldots, n\}$. Quindi gli $O_{i, j} \coloneqq \# \{k \le N : X_k = i \land Y_k = j\}$, per cui $O_{i, j} \sim \mathrm{bin}(N, p_{i, j})$ con $p_{i, j} = P(X_k = i, Y_k = j)$.

Il [[test-statistico|test]] dice $H_0: X, Y \text{ indipendenti}$ e $H_1: X, Y \text{ non indipendenti}$. Sotto $H_0$ abbiamo che $p_{i, j} = P(X_k = i, Y_k = j) \stackrel{H_0}{=} P(X_k = i)P(Y_k = j) = p_i^{X_k} p_j^{Y_k}$.

Calcolo gli attesi $A_{i, j} \coloneqq E_{H_0}(O_{i, j}) = N p_{i,j} = N p_i^{X_k} p_j^{Y_k}$, dove $p_i^{X_k}$ e $p_j^{Y_k}$ sono incogniti. Gli [[inferenza-statistica#Componenti alla base della statistica inferenziale|stimatori]] sono:
- $p_i^{X_k} = P(X_k = i) \approx \frac{1}{N} \#\{k \le N : X_k = i\} = \sum_{j = 1}^n O_{i, j}$ ovvero il totale sulla riga
- $p_j^{Y_k} = P(Y_k = j) \approx \frac{1}{N} \#\{k \le N : Y_k = j\} = \sum_{i = 1}^m O_{i, j}$ ovvero il totale sulla colonna
- $A_{i, j} \approx N \frac{1}{N} \sum_{h = 1}^n O_{i, h} \frac{1}{N} \sum_{h = 1}^m O_{h, j}$, ovvero
$$
A_{i, j} = \frac{\sum_{h = 1}^n O_{i, h} \sum_{h = 1}^m O_{h, j}}{N}
$$
- sotto $H_0$ ho $(m - 1)(n - 1)$ [[chi-quadro|gradi di libertà]] poichè stimando $p_i^X$ ho $m - 1$ [[chi-quadro|g.d.l]], con $p_j^Y$ ho $n - 1$ [[chi-quadro|g.d.l]], le categorie totali sono $mn$, per cui avrei $mn - 1 - (m - 1) - (n - 1) = mn - m - n - 1 = (m - 1)(n - 1)$.
- Quindi si deduce che 
$$
W \coloneqq \sum_{i = 1}^m \sum_{j = 1}^n \frac{(O_{i, j} - A_{i, j})^2}{A_{i, j}} \stackrel{H_0}{\dot \sim} \chi^2((m - 1)(n - 1))
$$
