---
title: "Teoria dell'affidabilità"
---
# Teoria dell'affidabilità
Studia il tempo di vita di alcuni oggetti. L'[[esponenziale]] ha un ruolo centrale in questo.

Se consideriamo un oggetto soggetto a rottura dopo un tempo casuale $T > 0$. Sia $t > 0$ un tempo, condizionando al fatto che al tempo $t$ l'oggetto non è ancora rotto, quanto vale la probabilità di rottura imminente?
$P(t < T < t + \Delta t | T > t) = \frac{P(t < T < t + \Delta t)}{P(T > t)} = \frac{\int_t^{t + \Delta t} f_T(s) \mathrm{d} s}{1 - F_T(t)} \approx \frac{\Delta t f_T(t)}{1 - F_T(t)}$.

L'intensità delle rotture è dato da $h_T(t) = \lim_{\Delta t \to 0}\frac{P(t < T < t + \Delta t | T > t)}{\Delta t} = \frac{f_T(t)}{1 - F_T(t)}$ che nel caso viene $h_T(t) \equiv \lambda$.

Ci sono altre variabili che modellano bene le rotture di oggetti in funzione di lambda:
1) Esponenziale: in cui non c'è memoria, quindi il tempo di rottura è costante nel tempo
2) Lineare generale: in cui il tempo di rottura è lineare crescente
3) *Bathtube*: di tipo empirico, in cui abbiamo una prima una fase di rodaggio in cui la probabilità di rottura si riduce, fino a stabilizzarsi e diventare costante, poi cresce (più lentamente di come decresceva prima) per via dell'usura.

C'è anche un'altra formula per la rottura che è quella di Weibull: $h_T(t) = \alpha t^{\beta}$.