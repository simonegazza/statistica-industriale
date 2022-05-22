---
title: "Variabili aleatorie"
---
# Variabili aleatorie
Sono dei generatori di numeri casuali, che spesso seguono una legge data. Chiedersi se P(X = 4) con X variabile aleatoria (talvolta abbreviato con v.a.) è chiedersi la probabilità che tale generatore di numeri casuali dia il valore 4.

Più formalmente: sono funzioni misurabili tali che $X: S \to \mathbb{R}$ con $S$ l'insieme degli eventi di quella varibile aleatoria. Si noti che l'insieme $S$ può coincidere a sua volta con $\mathbb{R}$.

Si noti che i valori ritornati sono [[probabilita|probabilità]] e che quindi devono rispettare le proprietà che la contraddistinguono.

## Tipologie
Esistono due tipi di v.a.: continue o discrete. In realtà ne esiste anche un terzo tipo, ovvero quelle miste, che però generalmente (quando si riesce) sono trattate a pezzi, riconducendosi al caso continue o discrete.

### Discrete
Assumono un valore finito o numerabile di valori. Per descriverle si utilizza la *funzione di massa della probabilità* (**PMF**) spesso indicata con $\phi_X: \mathbb{R} \to [0, 1]$. Si noti che $\phi_X(k) = P(X = k)$.

È possibile definire una *funzione di ripartizione* che corrisponde a fare la somma della variabile aleatoria fino ad un certo valore, ovvero come:
$$
    F_X(t) = \sum_{i = -\infty}^{t}\phi_X(i)
$$
Si noti che tale funzione assume un grafico simile ad una funzione a gradini crescente.

### Continue
Assumono valori continui e si descrivono tramite la *funzione di densità di probabilità* (**pdf**) spesso indicata come $f_X: \mathbb{R} \to [0, 1+\infty)$. Si noti che $P(X \in A) = \int_A f_X(t) dt$. Porre particolare **attenzione** quando viene richiesta la probabilità di un singolo punto, che dato che è l'integrale allora la si definisce come $0$.

Una nota riguardo le variabili aleatorie continue: nelle variabili aleatorie discrete è possibile andare ad assegnare a ciascun punto del dominio una data probabilità in maniera quasi diretta. Questo non è così scontato per le variabili aleatorie continue, poichè, dato che possono assumere infiniti valori, può risultare complicato assegnare a ciascuno di questi una probabilità, che si tramuterebbe nel dire che ognuno di questi ha probabilità $0$ (che è poi coerente con quanto visto sopra richiedendo la probabilità in un sol punto). Tuttavia possiamo superare questa limitazione andando a considerare una funzione che somma i contributi di ciascun valore precedente al valore richiesto.

Introduciamo quindi una funzione detta *funzione di ripartizione della probabilità* (**Cdf**) di una v.a. X continua come:
$$
    F_X(t) \coloneqq P(X \le t) = \int_{-\infty}^t f_X(u) du
$$
e da qui segue che $f_X(t) = F_X'(t)$.
Si noti inoltre che $P(a \le X \le b) = \int_a^b f_X(u) du = F_X(b) - F_X(a)$ e che $P(a \ge X) = 1 - P(X \le a) = F_X(a)$.
Si noti infine che, per quanto detto prima, $P(X \le a) = P(X < a)$.

# Osservazione
Si noti che conoscere una qualunque fra $\phi_X, f_X o F_X$ è sufficiente per farci calcolare la probabilità di qualunque $X$, e quindi per conosere la legge e quindi la distribuzione di $X$.

# Trasformazioni lineari
È possibile trasformare linearmente una variabile aleatoria generalemtne senza preoccuparsi troppo delle conseguenze (anche se è sempre necessario controllare le proprietà della [[probabilita|probabilità]]). Possiamo dire in generale che se $X$ è v.a. di *pmf* $f_X$ allora $Y = \alpha X + \beta$ si trasforma come $g_Y(t) = \frac{1}{|\beta|} f_X(\frac{t - \alpha}{\beta})$.

Attenzione alle trasformazioni di tipo non lineare, poichè possono causare diversi problemi e rompere diverse proprietà della [[probabilita|probabilità]].

# Richiesta di intervalli particolari
Se la variabile aleatoria è continua allora per chiedere una coda destra basta fare $F_X(a)$, mentre per ottenere una coda sinistra basta ottenere $1 - F_X(b)$, per richiedere l'intervallo centrale bisogna fare $F_X(b) - F_X(a)$.

Se la variabile è discreta allora per chiedere una coda destra basta fare $F_X(a)$, mentre per ottenere una coda sinistra basta ottenere $1 - F_X(b)$, per richiedere l'intervallo centrale bisogna fare $F_X(b - 1) - F_X(a)$.

Si noti che talvolta può essere richiesto che $P(X \in [a, b]) = 90\%$. In tal caso generalmente quello che si fa è porre simmetria sull'intervallo, andando quindi a porre che $P(X < a) = 0.05 = P(X > b)$, e ricavando sia $a$ che $b$ invertendo le formule.

# Generazione di una variabile aleatoria con distribuzione nota
Uso l'inverso della *Cdf* della distribuzione (ovvero $F^-1$) come legge e utilizzo una [[uniforme]] $U \sim \mathrm{unif}(0, 1)$ per generare tanti valori quanto necessari da dare in pasto a $F^-1$.

Supponiamo di avere una distribuzione [[esponenziale]] $X \sim \mathrm{expo}(\lambda)$ che quindi ha *Cdf* $F(t) = 1 - e^{-\lambda t}$ con $t > 0$. In Excel utilizzeremo la funzione $Gamma.inv(RAND(), 1, 1/\lambda)$ dove $RAND()$ corrisponde alla nostra [[uniforme]] descritta sopra.

# Excel
Quando si cerca di generare una v.a. in Excel si usa, nell'ultimo parametro della corrispondente funzione inversa, true o false a seconda che si voglia la *Cdf* o la *pmf*.
Esempio: so che $X \sim \mathrm{gamma}(\alpha, \beta)$ e chiedo di trovare $x$ sapendo che $P(X < x) \ge 5\%$. Quindi $0.05 \le P(\mathrm{gamma}(\alpha, \beta) \le x) = F_X(x)$. Quindi per invertire posso applicare $F^{-1}_\mathrm{gamma}$ poichè (in generale) $F$ e $F^{-1}$ sono sempre crescenti. Quindi $F^{-1}_\mathrm{gamma}(0.05) \le F^{-1}_\mathrm{gamma}(F_X(x))$ quindi $x \ge F^{-1}_\mathrm{gamma}(0.05)$.
