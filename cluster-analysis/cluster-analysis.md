---
title: "Cluster Analysis"
---
# Cluster Analysis
Fa parte dell'unsupervised learning tipicamente, anche se ci sono eccezioni. È un insieme di tecniche utili a dividere i dati in cluster in assenza di una variabile *etichetta*.

Attenzione, perchè esiste il problema analogo nel supervised learning che è la classidicazione, in cui si hanno effettivamente delle etichette con cui addestrare il modello. La differenza fra questi due metodi sta sostanzialmente nel fatto che in certi casi abbiamo le etichette già predefinite (supervised) e in altri casi no (unsupervised).

Esistono diversi algoritmi ottimi per il clustering, qui ne vedremo alcuni

## Tree joining
<img src="https://www.researchgate.net/publication/336422945/figure/fig1/AS:812809667506183@1570800334755/Neighbor-joining-tree-analysis-A-A-neighbor-joining-tree-was-constructed-from-the.png" alt="k-means clusters" width=700>
**L'unico algoritmo che ci permette di decidere il numero di cluster a posteriori**, unisce i punti uno alla volta, preferendo sempre prima i più vicini, costruendo un albero genealogico delle unioni. L'albero è chiamato **dendogramma**. 

È parametrico rispetto ad una funzione di distanza (presi due cluster, tipicamente si sceglie la distanza massima fra due punti appartenenti ai due diversi cluster) chiamata **linkage** (invece l'azione di unire i sotto alberi / cluster è detta **tree-joining**). Esistono tuttavia diverse forme di linkage:
- linkage **completo**: tutti i punti del cluster sono a distanza $\le$ di quella stabilita (funzione di distanza uguale a quella descritta sopra). Questo in particolare produce sempre cluster di forma sferica (che è quello che spesso si avvicina di più alle richieste dei clienti perchè controlla la distanza) ed è particolarmente adatto alla segmentazione (quando non ci sono cluster naturali).
- linkage **singolo**: la distanza fra i due cluster è quella tra i due punti più vicini. Questo produce cluster naturali dalla forma irregolare e produce configurazioni frastagliate. Se i punti sono tanti rispetto alle dimensioni (in genere in situazioni di [[overfitting]]) allora si ottengono cluster casuali.
- numerose vie di mezzo: ad esempio linkage **centroid** (che si basa sui baricentri), linkage **medio** (che si basa sulla media distanza dei punti), linkage di **Wand** (si basa su una specie di M-[[anova]])

Una volta terminata la fase di clustering, è possibile scegliere a che altezza dell'albero tagliare il dendogramma per ottenere la clusterizzazione desiderata.

## K-Means
<img src="https://static.javatpoint.com/tutorial/machine-learning/images/k-means-clustering-algorithm-in-machine-learning.png" alt="k-means clusters" width=700 style="background-color:white">
È necessario stabilire a priori in numero di cluster, anche se tipicamente si procede per tentativi. È un metodo di ottimizzazione iterativa: ad ogni iterazione assegno ai dati $k$ punti di riferimento più vicini e creo dei cluster a seconda di questa assegnazione, poi calcolo nuovamente i punti di riferimento come baricentro dei cluster. Produce dei cluster simili al linkage completo se si indovina $k$.

## (Variational) Autoencoders
<img src="https://tikz.net/janosh/autoencoder.png" alt="k-means clusters" width=700 style="background-color:white" >

Sono reti neurali che ha dimensione dell'input pari a quella dell'output e presenta una strozzatura in mezzo. Quindi avremo in ingresso un vettore di dimensione $p$ è in uscita un vettore sempre di dimensione $p$, tuttavia la strozzatura centrale avrà dimensione $k < p$ detto spazio latente.

Si pone $k$ pari al numero di cluster che si vogliono ottenere e si addestra il modello facendolo passare solo per lo strato di encoder iniziale, tagliando poi la rete allo spazio latente. Si noti che è possibile restingere l'insieme di valori dello spazio latente al simplesso $\{(z_1, z_2, \ldots, z_n) \in \mathbb{R}^k : z_i \ge 0 \land \sum_{i = 1}^k z_i = 1\}$ in modo che l'econder restituisca proprio le probabilità dell'appartenenza ad un singolo cluster.
