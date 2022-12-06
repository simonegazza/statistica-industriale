---
title: "Problema dei test multipli"
---
# Problema dei test multipli
Quando si fa un test, si imposta un [[test-statistico|livello di significatività]] $\bar \alpha$ che è tipicamente il $5\%$.

Se faccio un solo [[test-statistico|test]], questa soluzione va benissimo. Tuttavia se faccio molti [[test-statistico|test]], è probabile che almeno uno di essi abbia [[test-statistico#Errori del test|un errore di prima specie]].

Banalmente la dimostrazione di questo fatto la si può vedere in questo modo:
$$
P(\text{almeno un errore di I specie | vera } H_0 \text{ in tutti i test}) \\
= P(\cup_{i = 1}^n \{ \text{dico } H_1 \text{ nel test } i \} \text{ | vera } H_0 \text{ in tutti i test}) \\
\stackrel{\text{indip.}}{=} \sum_{i = 1}^n P(\text{dico } H_1 \text{ nel test } i \text{| vera } H_0 \text{ nel test } i) \\
= n \bar \alpha =: A
$$
con $A$ il [[test-statistico|livello di significatività]] *globale*

Quindi se scegliamo un [[test-statistico|livello di significatività]] $\bar \alpha = 5\%$ e facciamo $20$ [[test-statistico|test]], allora in media ne troveremo sicuramente almeno uno in errore.

Tipicamente, prima di applicare una qualsiasi correzione, è bene **ridurre il numero $n$ di [[test-statistico|test]] il più possibile**, tenendo conto che bisogna deciderli **ancora prima di vedere i dati, per evitare il cherry-pick** (anche inconscio).

Si noti che nel discorso fatto non abbiamo fatto non abbiamo detto nulla sulla natura dei [[test-statistico|test]]. Genericamente questo discorso si applica a tutti i [[test-statistico|test]].

## Correzione di Bonferroni
Fisso il [[test-statistico|livello di significatività]] globale al $5\%$ e poi pongo che il [[test-statistico|livello di significatività]] del singolo test $i$, $\bar \alpha_i = \frac{A}{n}$ con $n$ il numero di test.
Questo garantisce di avere una probabilità di [[test-statistico#Errori del test|errori di prima specie]]controllata però ha il altissimo prezzo di ridurre la potenza dei test.
