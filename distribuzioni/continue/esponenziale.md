---
title: "Esponenziale"
---
# Esponenziale
L'esponenziale è una [[distribuzione]] di [[probabilita|probabilità]] [[variabili-aleatorie#Continue|continua]].

Si indica con $X \sim \mathrm{expo}(\lambda)$ in cui $\lambda > 0$ è chiamato **rate** o tasso.

La [[variabili-aleatorie#Continue|funzione di densità di probabilità]] è:
$$
P(X \le t) = \lambda e^{-\lambda t}
$$
con $t > 0$.

Rappresenta un tempo di attesa di un certo evento casuale che **ha la stessa [[probabilita|probabilità]] di avvenire in ogni momento**.

Ha l'**assenza di memoria**, per cui $P(T > a + b | T > a) = P(T > b)$, cioè la [[probabilita|probabilità]] di aspettare $a + b$ dopo aver già aspettato $a$ è uguale alla probabilità di aspettare direttamente $b$.

È la versione continua della [[geometrica]].

Modellizza molto bene i tempi di attesa per eventi improvvisi e imprevedibili (richieste ad un server, telefonate, rotture improvvise, decadimenti radioattivi, ecc...).

Si può trovare anche tutte le volte che c'è un [[processo-poisson|processo di Poisson]] alla base, con intertempi $\mathrm{expo}(\lambda)$ [[indipendenza#Indipendenti e identicamente distribuite|i.i.d]].

Ha [[media]] $E(X) = \frac{1}{\lambda}$ e [[varianza]] $Var(X) = \frac{\log 2}{\lambda}$.

<img src="https://upload.wikimedia.org/wikipedia/commons/e/ec/Exponential_pdf.svg" alt="grafico della distribuzione" width=700 style="background: white">
