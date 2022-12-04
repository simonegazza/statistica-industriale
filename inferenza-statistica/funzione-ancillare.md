---
title: "Funzioni ancillare"
---
# Funzioni ancillare
Sono funzioni utili in statistica in tantissimi contesti. Spesso vengono usate per approssimare un parametro di una [[distribuzione]].

Devono rispettare 3 caratteristiche:
- deve essere nota la [[distribuzione]] a cui fa riferimento
- deve dipendere **solo** dai dati
- deve avere un solo parametro incognito, che è quello che vorremmo stimare

Ad esempio, conoscendo $\sigma$ e cercando di ricavare $\mu$, nel caso gaussiano, abbiamo $\frac{\bar X - \mu}{\sigma} \sqrt{n} \sim \mathcal{N}(0, 1)$
