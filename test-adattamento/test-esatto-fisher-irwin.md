---
title: "Test esatto di Fisher-Irwin"
---
# Test esatto di Fisher-Irwin
Nel caso particolare di [[tabelle-contingenza|tabelle di contingenza]] 2x2 si può fare il test in modo esatto. Infatti, assumendo che le grandezze siano disposte in questo modo:
| $X \backslash Y$ | $Y_1$      | $Y_2$      |   |
|------------------|------------|------------|---|
| $X_1$            | $O_{1, 1}$ | $O_{1, 2}$ | a |
| $X_2$            | $O_{2, 1}$ | $O_{2, 2}$ | b |
|                  | c          | d          | n |

Intuitivamente infatti possiamo pensare che l'estrazione casuale di un [[inferenza-statistica|campione]], senza rimessa dall'insieme di dati di $X$ e $Y$ abbia legge [[ipergeometrica]] $\text{hygp}$

Ad esempio, avremo che:
$$
P(O_{1, 1} = k) \sim \text{hypg}(a, c, n) = \frac{\binom{c}{k} \binom{d}{a - k}}{\binom{n}{a}}
$$
poichè estraggo $a$ dati dalla categoria $c$ su un totale di $n$. In particolare si noti che:
$$
P(O_{1, 1} = k) \sim \text{hypg}(a, c, n) = \frac{\binom{c}{k} \binom{d}{a - k}}{\binom{n}{a}} \qquad
P(O_{1, 2} = k) \sim \text{hypg}(a, d, n) = \frac{\binom{d}{k} \binom{c}{d - k}}{\binom{n}{a}} \qquad \\
P(O_{2, 1} = k) \sim \text{hypg}(b, c, n) = \frac{\binom{c}{k} \binom{d}{b - k}}{\binom{n}{b}} \qquad
P(O_{2, 2} = k) \sim \text{hypg}(b, d, n) = \frac{\binom{d}{k} \binom{d}{b - k}}{\binom{n}{b}} \qquad
$$

Si noti che il [[test-statistico#Il p-value|p-value]] di questo test si calcola in due modi:
- $\alpha^* = P(O_{i, j} \ge k) = 1 - P(O_{i, j} \le k) = 2 P(O_{i, j} \le k)$ utile soprattutto (ma non solo) quando l'[[ipergeometrica]] è simmetrica
- $\alpha^* = P(O_{i, j} \ge k) + P(\text{altri esiti con probabilità minore di } O_{i, j})$ sempre valido anche quando l'[[ipergeometrica]] non è simmetrica
