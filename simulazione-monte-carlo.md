---
title: "Simulazione Monte Carlo"
---
# Simulazione Monte Carlo
A volte ci sono probabilità o valori attesi che interessano ma che non sappiamo calcolare con la combinatoria. La simulazione Monte Carlo è un metodo che ci consente di calcolare proprio questo.

Un esempio comodo potrebbe essere il $\alpha^*$ di un [[test-statistico|test]] se non ne esiste la funzione ancillare.

Per via della [[legge-grandi-numeri|LGN]] sappiamo che la [[media]] campionaria andrà ad approssimare la [[media]] vera.

Si tratta quindi di ripetere lo stesso esperimento numerose volte, andando ad aumentare la precisione del calcolo delle probabilità in gioco tutte le volte che aumentiamo la numerosità dell'esperimento.

Quindi per stimare una [[probabilita|probabilità]] userò la formula frequentista (casi ottenuti concordi su casi avvenuti); in alternativa bisogna utuilizzare la [[variabili-aleatorie#Variabile Caratteristica|variabile indicatrice]] e si può calcolare come $P(H) = E(\bold{1}_H)$.
