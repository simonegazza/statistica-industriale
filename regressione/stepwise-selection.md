---
title: "Stepwise selection"
---
# Stepwise selection
La stepwise selection è un metodo con la quale possiamo affinare la precisione della nostra regressione andando a selezionare le variabili in gioco una a una.

Ci sono due principali tipologie di stepwise:
- **backward**: parte da tutto l'insieme delle variabili e rimuove quelle considerate inutili
- **forward**: si fa una regressione per ogni variabile e, una volta individuata quella poù significativa, si procede aggiungendo una alla volta quelle rimanenti, e si ripete la selezione delle due variabili, poi 3, poi 4, ecc...

## Backward stepwise selection
Si effettua il test di regressione **su una variabile, associata a ciascun $B_i$, alla volta** e si decide se tenerla in base al risultato ottenuto:
- se il [[test-statistico#Il p-value|p-value]] $\alpha^*_i < 0.001$ allora ho la quasi certezza che $\beta_i \not = 0$ e quindi certamente terrò la variabile associata a $B_i$
- se il [[test-statistico#Il p-value|p-value]] $0.001 \le \alpha^*_i < 0.3$ non posso affermare nulla con certezza. Mi resta il dubbio ma tengo la variabile associata a $B_i$
- se il [[test-statistico#Il p-value|p-value]] $\alpha^*_i \ge 0.3$ non vi è alcun indizio che $\beta_i \not = 0$. Posso valutare con più attenzione se togliere la variabile associata a $\beta_i$ dalla selezione

La soglia suggerita è tipicamente il $30\%$.
Se tutte le $\beta_i$ hanno [[test-statistico#Il p-value|p-value]] inferiore alla soglia del 30% allora interrompo la procedura.

Una volta effettuato il test di regressione per ciascuna variabile, la scelta più naturale delle variabili da eliminare è quella con il [[test-statistico#Il p-value|p-value]] più alta. Tuttavia **sarebbe meglio provare ad eliminarne diverse e scegliere quella da togliere**, perchè non è detto che la variabile con $\alpha^*_i$ più alta sia quella più inutile; infatti quando è vera $H_0$ allora $\alpha^*_i \sim \textrm{unif}(0, 1)$ con $\textrm{unif}$ l'[[uniforme]] fra 0 e 1 (e non predilige per forza i valori vicino a $1$).

Si noti che tipicamente se sono presenti forti correlazioni fra le variabili di ingresso, allora i corrispondenti stimatori $B_i$ avranno varianza elevata e i loro [[test-statistico#Il p-value|p-value]] risulteranno alti fino a quando non si ridurrà la correlazione togliendo le variabili.

## Forward stepwise selection
L'idea è quella di procedere per tentativi guidati da indicatori globali come $S_e$:
- al primo step scelgo la varaibile con il minimo [[test-statistico#Il p-value|p-value]] $\alpha_i^*$ o con il minimo $S_e$ o il massimo $R^2$ o ... (sono tutti indicatori equivalenti con solo una variabile)
- negli step successivi aggiungo una sola variabile alla volta rispetto alla precedenti, prendendo sempre quella che minimizza $S_e$ o massimizza $R^2$ insieme alle variabili scelte in precedenza (nota: non posso più guardare il $\alpha_i^*$ perchè non è un indicatore globale).
- mi fermo quando, ad esempio, $S_e$ comincia ad aumentare o $R^2$ comincia a diminuire.

## Metodo misto
Esiste un metodo misto che prevede di mescolare passi forward a passi backward, in particolare si aggiungono variabili fino a quando una delle aggiunte in precedenza non diventa non significativa.
