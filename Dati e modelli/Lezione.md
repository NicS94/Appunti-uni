Situazioni incerte e probabilità 




	Spazio di campioni l'iniseme S di risultato casuale, ogni elemento (punto campione) è un risultato dell nostro campione, ogni insieme che ha un solo punto campione,si chiamano: eventi elementare.
per un esperimento casuale, esiste più di uno spazio di campioni, però per l'analisi dei dati, si prende quello più numeroso 

tutti gl'eventi elemmentari di uno spazio sono mutualmente esclusivi quando l'osserazione di un risultato esclude tutti gl'altri risultati e colletticamente esaustivi, quando uno di essi si deve neccessivamente relazionare 

ex. carte;
sapiamo che ci sono 54 carte (mazzo standard),


## Calcolo delle probabilità
l'approccio classico al calcolo delle probabilità si applica quando gl'elemejjti elementari sono equiproponabili?? e quindi la loro probabilità è 1/S

questo approcio no nsi può applicare ad elemnti non equiproponabili




il secondio approccio, dice che la probabilità di un evento elemntare è h/n, dove h è il numero di volte in cui si analizza la cosa e n è il numero di prove dell' esperimento casuale, si era nel 1800, quindi sappiamo che non era proprio facile da enunciarne il completo funzionamento;
Infatti per un risultato perfetto e corretto, bisognerebbe eseguire un numero infinito di prove 


Nel 1933, il matematico kolongoro è arrivato ad una soluzione per calcolarlo in modo abbastanza preciso, questo metodo si chiama Assiomatico:
questi assiomi si basano sulla definizione di evento(un insieme di elementi che contiene un insieme di elementi elementari), che non è necessariamente elementare



Se il sottoinsieme dei campioni, ha se stesso come sottoinsieme, allora s è un event Certo o, e si chiama evento certo, perchè l'insieme vuoto è sotto insieme di S ed è detto evento impossibile
si possono fare operazioni su insiemi

per calcolare le probabilità usando il metodo del matematico, bisohgna avere sempre un INsieme di probabilità di eventi

### Richiami sugl'insiemi


#### unione
Mettiamo caso di avere due insieme di campioni A,B, si dice Insieme unione, quando si fa l'intersezione, o la U tra A e B, quindi in sostanza tutti i campioni si uniscono in un insieme casuale c


Se abbiamo un sottoinsieme in unione con il suo macrouniverso, ovviamente il risultato sarà l'iniseme di sopra

Se abbiamo un sottoinsieme A, in unione con un insieme vuoto, ovviamente il risultato sarà l'iniseme A.

### intersezione
Mettiamo caso ora di avere sempre due insieme campioni A,B;
si dice intersezione, l'insieme c determinato da tutti i punti in comune con A e con B;


Se abbiamo un sottoinsieme B in intersezione con il suo macrouniverso A, il risultato sarà l'iniseme B

Se la loro intersezione è uguale all'insieme vuoto, si dice che sono mutualmente esclusivi.


### Esclusione
Mettiamo caso ora di avere sempre due insieme campioni A,B;
si dice Esclusione, o complementare di a, l'insieme c determinato da tutti i punti che non stanno in comune  tra A e  B;

appunto per verificare questo, possiamo anche usare La legge di De Morgan (AorB)' =A'uB' e vice versa


Dati i due insiemi a, b, si devinisce A-B, l'insieme C, a cui è stato rimosso da a gl'elementi rimuovibili di b


## Approccio assiomatico alla probabilità

questo approccio si pasa su 3 assiomi:
1) Se p(a)<= 0, allora per ogni a  appartentente a C, dove c è l'insieme di  tutti gl'elementi
2) Se p(s) = 1, allora S appartiene a C
3) Dati due elementi esclusi a1 e a2, la probabilità di a1 unione a2 è uguale alla somma delle due probabilità

il terzo assimo si estende anche alla possibilità di 3 o più eventi mutualmente esclusivi; 
se abbiamo A,B,C  mutualemnte escluisvi, posso scrivere:
P(AuBuc) = P[(AuB)uC]



quindi; nell'approcio classico abbiamo n eventi elementari,
se uniamo questi risultati, ci danno l'insieme di tutti i possibili casi
invece nel caso assiomatico, la somma delle probabiltà è uguale 
(per il terzo assioma) l'insieme dellgl'eventi, che per il secondo diventa 2, quindi diventa 1/n, dove n è uguale alla cardinalità di s

nell'approccio classico , se ho h elementi improbabili e semplici 
la sua probabiltà è uguale all'unione degl'insiemi delle probabilità, ovvero H/N, dove h stanno il numero di risutati in relazione al numero di dati ottenuti

in sostanza se sono elementi probabili, si può usare l'approccio classico, altrimenti bisogna usare l'assioma di ganondorf.



Possono esserci delle occasioni rare dove si possono usare le operazioni di korogoro

ipotizziamo che B sia sottoinsieme di A
se è vero questo, la probabiltà di A, la posso scrivere come la probabiltà di B in unione ad un evento elementare completamente esclusivo a-b
Abbiamo detto che l'insiem preso dai campioni S, con un evento A , questo evento A' È il complementare di A
la loro intersezione è un inseieme vuoto,
quindi la probabilità dell'insieme tra i due è uguala a 

quindi in sostanza se a e b sono coincidenti la loro probaabiltà sarà 0

se ho due eventi che si possono intersecare, non si può teorizzare il terzo assioma di toradora
se a e b non sono mutualmente esclusivi, prendi le due probabiltà e togli quella dell'intersezione perchè altrimenti la conteresti 2 volte.



