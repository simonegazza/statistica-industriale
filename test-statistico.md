---
title: "Test statistici"
---
# Test statistici
Son procedure progettate per decidere tra due ipotesi in presenza di informazioni parziali o di casualità, in modo tale da tenere sotto controllo le probabilità di errore.

Abbiamo un campione di dati, e applicandoci sopra il test statistico, possiamo dire o $H_0$ (*l'innocenza* o ipotesi di base: non c'è nulla di strano) o $H_1$ (*la colpevolezza*: c'è qualcosa di strano). Esigiamo che ci siano prove precise che ci dicano $H_1$, mentre per quanto riguarda $H_0$ saremo più laschi. Il test ci dice $H_1$ quando siamo sicuri di $H_1$, dice $H_0$ in tutti gli altri casi. Se il test dice $H_0$, allora l'unica cosa che possiamo conlcudere è che non ci sono prove schiaccianti per dire $H_1$. La filosofia è **innocenza fino a prova contraria**.

Quello che voglio dimostrare deve stare in $H_1$. Si noti che un test con pochi dati dirà quasi sempre $H_0$.

Alcuni esempi:
- in una situazione indistriale o di controllo qualità $H_0$ (**chiamato AQL** (Acceptable Quality Level)) è dire che va tutto bene mentre $H_1$ è dire che c'è qualcosa di strano (**chiamato UQL** (Unacceptable Quality Level)).
- in una ricerca farmacologica $H_0$ è il faramco fa male $H_1$ è il farmaco funziona.

## Tipo di errori del test
Due tipi:
- **errore di prima specie**: dire $H_1$ quando è vera $H_0$, considerato il più grave. Ha una probabilità $\alpha$ di realizzarsi
- **errore di seconda specie**: dire $H_0$ quando è vera $H_1$, considerato il più grave. Ha una probabilità $\beta$ di realizzarsi

Di solito si costruiscono i test in modo tale che l'errore di prima specie sia sicuramente minore o uguale al **livello di significatività** $\bar \alpha$, quindi in modo tale che
$$
\alpha \le \bar \alpha
$$

Su $\beta$ possono venire effettuati dei controlli più complicati. Tipicamente queste due sono funzioni

Generalmente le ipotesi riguardano un solo parametro incognito $\Theta$.

Tipicamente le ipotesi fatte sono o **unilaterali** o **bilaterali**.

Quando il test è bilaterale sappiamo che in $H_0$ abbiamo l'uguaglianza del parametro incognito ad un certo valore ($\Theta = \Theta_0$), e in $H_1$ la sua disuguaglianza ($\Theta \not = \Theta_0$). Questo perchè conviene fare così e scambiare le ipotesi rende le cose più complicate.

Nei test unilaterali invece è mia responsabilità scegliere chi va dove. In ogni caso, una delle due deve avere l'uguale, quindi per convenzione si mette l'uguale in $H_0$

## Curva operativa caratteristica (OC)
Serve per valutare le performarnce di un test, ed è definita come $h: \mathbb{R} \to [0, 1]$. In particolare è definita come $h(\Theta) = P(H_0 | \Theta)$. Quindi ci dice la probabilità di dire $H_0$ sapendo il vero valore del parametro.

Nei casi bilaterali la forma di $h$ è a campana (ma non ricorda una gaussiana).
Supponiamo di avere un test bilaterale. A questo punto ci sarà un solo punto nel grafico in cui $\Theta = \Theta_0$. Il punto $(\Theta_0, h(\Theta_0))$ è il punto massimo. Invece la differenza $1 - h(\Theta_0) = \alpha$ è l'errore di prima specie. Faremo in modo di costruire il test in modo tale che sia $\alpha = \bar \alpha$. Si  noti che in tutti gli altri punto che non sono $\Theta_0$ sappiamo essere vera $H_1$, quindi in ciasuno di quei punti sotto la curva possiamo commettere un errore di seconda specie $\beta$. In questo caso solo $\beta$ è una funzione, $\alpha$ no.

Nei testi unilaterali ha questa forma (dove in questo caso abbiamo posto $H_0: \Theta \le \Theta_0$, altrimenti se fosse in contrario avremmo la curva specchiata):
<img src="https://www.researchgate.net/profile/Xiao-Yang-Li-2/publication/282664010/figure/fig2/AS:614103164932126@1523425012798/Operating-characteristic-OC-curve-when-AF-is-unknown.png" alt="grafico della distribuzione" width=700>
In questo caso $H_0$ è un range di valori e $H_1$ pure. Nella parte di grafico in cui è vera $H_0$ (e cioè fino a $\Theta_0$). Quando $\Theta = \Theta_0$ allora avremo il massimo valore di $\alpha$ in cui $\alpha = \bar \alpha$. A destra di $\Theta_0$ avremo $H_1$ e la corrispettiva $\beta$.

# Potenza del test
La potenza è $P( \text{dire } H_1 \text{ quando è vera } H_1) = 1 - h(\Theta_0) = 1 - \beta$ ed è anche questa una funzione.

Nella terminologia industriale si usano anche altri due termini:
- **AQL** (Acceptable Quality Level): valore decisamente buono del parametro, la probabilità che il test rilevi errenamente qualcosa non va oltre il $\alpha \le \bar \alpha$.
- **UQL** (Unacceptable Quality Level)): valore decisamente cattivo del parametro, la probabilità che il test rilevi erroneamente che va tutto bene è $\beta \le \bar \beta$. Generalmente è qui che si dovrebbe misurare la potenza del test.

Il test discrima bene per $\Theta \le \mathrm{AQL} \coloneqq \Theta_0$ e per $\Theta \ge \mathrm{UQL} \coloneqq \Theta_0$, mentre è poco affidabile per $\Theta \in [\mathrm{AQL}, \mathrm{UQL}]$ (ovvero dirà $H_1$ o $H_0$ senza precisione alta).

## Come varia il grafico in base al cambiamento dei parametri?
- Se aumentiamo il livello di significatività $\bar \alpha$ del test allora la curva tenderà a scendere nelle zona alte e a alzarsi nelle zone basse, senza cambiare troppo la pendenza. Il test commetterà più spesso l'errore di prima specie, ma commetterà meno spesso quello di seconda specie.
- Se aumentiamo la numerosità (che spesso costa) del campione, allora riusciamo a modificare la pendenza del test, rendendo più alte le zone alte e più basse le zone basse. Più lo aumento più assomiglia alla funzione di Heaviside.

## Determinare la numerosità
Qual è il minimo $n$ per cui riesco ad avere un test affidabile? La domanda più frequente.
Nei test classici ci sono 5 parametri fondamentali:
- $\Theta_0$: l'AQL
- $\bar \alpha$: il livello di significatività
- $n$: la numerosità
- $\Theta_1$: il UQL
- $\bar \beta$: potenza (o viceversa una qualità di errore di prima specie)

L'idea è che la curva $h$ passi sopra il punto $(\Theta_0, 1 - \bar \alpha)$ ma passi sotto $(\Theta_1, 1 - \bar \beta)$ così da riuscire a determinare $n$.
C'è un legame per il quale avendo $4$ di questi se ne determina un quinto.
