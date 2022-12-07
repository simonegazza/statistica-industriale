---
title: "Overfitting"
---
# Overfitting
È un problema comune e universale a tutto il machine learning, dalla [[regressione]] alle reti neurali. Si ha quando il modello ha troppe variabili (o coefficienti incogniti) rispetto al numero di punti.

Se in questo caso si cerca di alzare il grado della curva che fitta i punti per fare un migliore fit sul dataset, allora si generalizza meglio sul dataset ottenuto, tuttavia si peggiora notevolmente sui punti futuri, per cui il modello non generalizza bene sui dati.

## Regressione
In particolare nella [[regressione]] è meglio se $\frac{n}{p} >> 1$ per evitare l'overfitting (con $n$ il numero di punti nel dataset e $p$ il numero di variabili usate nel modello).

In situazioni di overfitting abbiamo che $(X^T X)^-1$ (ovvero la [[covarianza]] dei $B$) tende ad allontanarsi da una matrice diagonale, gli stimatori diventano sempre più correlati e meno precisi, i test di regressione dei $\beta_i$ sono sempre meno potenti e molti [[test-statistico#Il p-value|p-value]] $\alpha^*_i$ sono alti. **Spesso l'overfitting è caratterizzato da dei $|\beta_i|$ molto alti**.

Per evitare tutte queste problematiche, è meglio la [[stepwise-selection#Forward stepwise selection|forward stepwise selection]], che in crementando $p$ step-by-step ci evita l'overfitting.
Un altro sistema che si può utilizzare prevede di andare a [[design-of-experiment|progettare l'esperimento (DoE)]] fissando in anticipo i valori di input.
