---
title: "Validazione di un modello"
---
# Validazione di un modello
Procedura utile ad evitare l'[[overfitting]]. Tipicamente si sviluppa in questo modo:
- si mette da parte una frazione dei dati (circa il $10\%$), che chiamo **insieme di validazione**
- lancio il modello sul restante pezzo dei dati
- verifico che alcuni parametri non siano molto minori dei quelli che ha il modello con i dati di validazione: se non è così sono in [[overfitting]]

Tipicamente questo è un modo onesto e senza bias di misurare le performance del modello.

I dati disponibili quindi vengono divisi generalmente in 3:
- **training set**: insieme di dati usati per allenare il modello. Sono i dati che vengono usati più spesso.
- **validation set**: insieme di dati usati per controllare che il modello non vada in overfitting. Sono tipicamente utilizzati un numero di volte minore rispetto al training set.
- **test set**: insieme di dati che vengono tenuti nascosti e si guardano solo alla fine, perchè così si fa un controllo effettivo sulla bontà vera del modello.

## Cross-validation
Tecnica che prevede di dividere a metà l'insieme di dati disponibili per il modello (escludendo già a priori il test set) e allenare il modello, poi successivamente si scambiano test set e validation set

## $k$-fold cross-validation
Si divide il dataset in $k$ blocchi e si usano $k-1$ blocchi per il training e $1$ per il test, ciclando su di essi. Si noti che per $k = 2$ rientriamo nella cross validation.

## Jacknife
$k$-fold cross-validation con $k = n$ con $$

## [[Regressione]]
Per la verifica durante [[regressione]] dei parametri che uso per valutare la bontà del modello sono i residui. Si noti in particolare che una misura molto utile per capire come sta andando il modello sono i **residui standardizzati**, ovvero, nel caso lineare:
$$
\frac{Y_i - (\beta_0 + \beta_1 x_i)}{\sqrt{SS_R / (n - 2)}} \mathcal{N}(0, 1)
$$
Se il modello presenta delle forti non linearità, è possibile vederlo direttamente nel *diagramma di dispersione* (ovvero il grafico dei residui) quando presenta regolarità geometriche. Inoltre sbilanciamenti particolari verso il lato destro o sinistro possono indicare la necessità di linearizzare (nel senso di applicare il logaritmo) una o più variabili.
Tipicamente comunque è bene osservare che i residui standardizzati devono bene o male tutti cadere all'interno dell'intervallo $[-1.96; +1.96]$ (che corrisponde alla zona in cui una [[gaussiana|gaussiana standard]] si distribuisce per il $95\%$ dei valori)

Per mitigare l'[[overfitting]] cerco di ridurre il numero di variabili che uso.
Usando la validazione si risce anche a guidare un  po' meglio la selezione delle variabili in un constesto di [[stepwise-selection|stepwise selction]].
