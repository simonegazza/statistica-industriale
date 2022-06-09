---
title: "Diagramma QQ"
---
# Diagramma QQ
Ci è molto utile per verificare che i dati siano [[gaussiana|gaussiani]], in modo da poter applicare i metodi statistici che ci interessano. Infatti il diagramma QQ produce una retta se e solo se i dati di costruzione erano [[gaussiana|gaussiani]].

Per ottenere il diagramma, supponiamo di avere un set di dati come $x_1, x_2, \ldots, x_n$:
- ordino i dati
- calcoliamo $\Phi^{-1}(\frac{i - \frac{1}{2}}{n})$ per $i = 1, \ldots, n$
- plottiamo i punti $(\Phi^{-1}(\frac{i - \frac{1}{2}}{n}), x_{(i)})$

Questo perchè $x_{(i)} \approx \hat F(\frac{i - \frac{1}{2}}{n}) \approx F^{-1}(x_{(i)}) = \frac{i}{n}$

## Ricavare dati dal diagramma QQ
Possiamo ricavare anche alcuni risultati interessanti dal diagramma QQ.

In particolare si noti che con dati come $x_1, x_2, \ldots, x_n$ generati da $X \sim \mathcal{N}(\mu, \sigma)$ allora so che la $F(t) = \Phi(\frac{t - \mu}{\sigma})$ quindi $F^{-1}(y) = \mu + \sigma \Phi^{-1}(y)$. Quindi i punti che sono plottati dal diagramma QQ sono della forma $(z_i, \mu + \sigma z_i))$ con $z_i = \Phi^{-1}(\frac{i - \frac{1}{2}}{n})$

Per cui i dati della [[gaussiana]] che possiamo ricavare sono:
- l'intercetta è la [[media]] $\mu$
- la pendenza è la [[deviazione-standard|deviazione standard]] $\sigma$.
