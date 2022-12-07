---
title: "Tipologie di variabili e loro gestione"
---
# Tipologie di variabili e loro gestione
Ci sono diverse tipologie di variabili:
- **dicotomiche**: assumono valori solo due, generalmente di vero/falso (o simili: $0/1$, V/F, M/F, $-1/1$, ecc...)
- **categoriche**: variabili tipo le regioni, i titoli di studio, ecc...
- **numeriche**: ritmo cardiaco, statura, reddito, numero di processi, ecc...

## Dicotomiche
Possono essere usate tranquillamente come variabili di ingresso a qualsiasi modello, e generalmente sono codificate con una coppia di numeri (in genere $0/1$). Queste sono le variabili scelte nel [[design of experiment (DoE)]].

Nel caso particolare della **[[regressione]] non possono essere usate come variabile di risposta** (perchè la [[regressione]] risponde sempre con valori continui). Esistono altre analisi e altri modelli (come la [[discriminant analysis]] (ovvero una regressione standard fuori ipotesi) o la [[regressione logistica]] che usa un [[inferenza-statistica#Stimatori di massima verosimiglianza|MLE]] [[bernoulliana|bernoulliano]]).

## Categoriche
Si dividono ulteriormente in:
- nominali (le $20$ regioni, le stagioni, il tiupo di carburante, ecc...)
- oridnali (titolo di studio, classifiche, gravità di sintomi, ecc...)

Le **nominali** sono tipicamente variabili che **non posso codificare con un numero** (questo perchè altrimenti andrei anche involontariamente a ordinarle), come ad esempio nel caso delle regioni (che non hanno un ordine intrinseco particolare).

Tuttavia a questa regola non si applica alle **ordinali che possono essere numerate**, ad esempio in determinati contesti può essere opportuno codificare i titoli di studio con un numero, se si tratta di indicare il numero di anni di studio proprio. Si noti che non è necessario rispettare un qualche valore di ordine intrinseco in questo caso (ad esempio se consideriamo che tutti i gradi abbiano un loro valore al di là degli anni di studio, possiamo numerarli con $0, 10, 20$, ecc...)

Una scelta opportuna, soprattutto nel caso delle regioni, è quella di fare l'**esplosione dicotomica**, in cui le $n$ variabili vengono trasformate in $n-1$ dicotomiche $0/1$, in cui al più solo una di queste sarà vera in ogni momento.
Tipicamente quindi quello che si fa è che l'ultima variabile non viene codificata, così che sia intrinsecamente codificata lasciando le altre a $0$.

Tipicamente comunque **prima di poterle utilizzare come input** in un modello, **vanno  gestite** in qualche modo. **Vanno direttamente bene nell'[[anova]]**, tuttavia nella **[[regressione]] bisogna fare l'esplosione dicotomica**, altrimneti risultano linearmente dipendenti. Si noti che questo spesso va a peggiorare molto il rapporto $\frac{n}{p}$.

Nota riguardo la [[regressione]] e l'esplosione dicotomica: se si riesce a provare tramite il [[regressione#Test di regressione|test di regressione]] che uno di questi coefficienti (dopo l'esplosione dicotomica) va a zero, allora sappiamo che la variabile associata a quel coefficiente si comporta come la variabile che è stata lasciata per ultima nell'esplosione dicotomica (ovvero quella che non compare esplicitamente). Si dice quindi che se la [[stepwise-selection#Backward stepwise selection|stepwise backward]] elimina una di queste dicotomiche, allora non viene distinta da quella di default. Questo porta l'effetto di fondere le categorie fra loro

Possono essere utilizzate come variabili di output, in random forest, classification trees o reti neurali.

## Numeriche
Si dividono in due tipologie:
- di tipo *differenza*: ad esempio Q.I., peso, altezza, consumi, ecc...
- di tipo *rapporto*: ad esempio reddito, abitanti di città, intensità sonora in DB, ecc.... Sono tipicamente variabili che occupano diversi ordini di grandezza e sempre positive. È tipicamente necessario fare prima il **logaritmo** di queste variabili prima di procedere, poichè soggiace una distribuzione [[lognormale]].

Si noti che **le trasformazioni di carattere lineare non modificano la [[regressione]]** e non cambiano neanche i [[regressione#Test di regressione|test]] di p-value, $R_D^2$ e $R_A^2$.

**Le trasformazioni non-lineari invece possono essere usate per migliorare la distribuzione** di alcune variabili durante la [[regressione]], in particolare quando la coda destra delle distribuzioni è particolarmente lunga (ad esempio con $\sqrt{}$, $\log$, o altro). Si noti inoltre che talvolta (soprattutto quando la [[varianza]] è proporzionale alla [[media]]) le trasformazioni lineari possono rendere omoschedastico il problema.

Si noti che **se si è applicato il logaritmo alla variabile di risposta, allora sarà necessario elevare alla base del logaritmo quando si vuole ottenere una qualche stima per un punto futuro**.

## Standardizzazione (o normalizzazione o trasformazione lineare standard)
Si tratta di portare a [[media]] $0$ e [[varianza]] $1$ le variabili considerate, ovvero per farlo basta banalmente fare
$$
\tilde x_{i,j} \coloneqq \frac{x_{i, j} - \bar x_j}{s_j}
$$
con:
- $\bar x_j$ la media della feature $j$
- $s_j$ la varianza campionaria della feature $j$

**Farlo per tutte le variabili ci porta ad avere coefficienti confrontabili nella [[regressione]]**.
