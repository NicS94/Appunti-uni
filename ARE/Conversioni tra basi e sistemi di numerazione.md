## Sistemi di numerazione
Nella vita di tutti i giorni, per contare qualcosa, usiamo i numeri;
questi numeri sono chiamati sitema di numerazione nel nostro caso è chiamato sistema decimale perchè fa da 0 a 9, ma ne esistono di molti altri, come quelli in base 2 (binario), quelli in base 4, in base 8, in base 16, IN BASE 2487!!!
si in sostanza sono infiniti.
## Ora parliamo di cose serie: altre basi 
Come detto prima esistono infinite basi, le più conosciute e le più diffuse sono: 
1) Binaria (0,1)
2) Ottale (0,1,2,3,4,5,6,7)
3) Decimale (0,1,2,3,4,5,6,7,8,9)
4) Esadecimale (0,1,2,3,4,5,6,7,8,9) per i numeri, poi si aggiungono dei caratteri per indicare numeri maggiori di 9 (perchè 10 sarebbe l'unione tra 1 e 0) (A,B,C,D,E,F)
5) Base 32 (0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V)
6) Base 64 (A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z,a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,0,1,2,3,4,5,6,7,8,9,+,/)

# Sistema numerico binario
*il sistema di numerazione binario accetta solo due caratteri per creare i numeri (0 ed 1)*

>[!example] Un esempio di parola in binario
>010010 -> 34 in decimale
>1101 -> 12 in decimale
> 0000-> 0 in decimale

## Come convertire da una base ad un altra
Per convertire da decimale ad un altra base, generalmente si usa la divisione successiva dove si divide il numero per la base, se esce un numero con la virgola lo approssimiamo e scriviamo il resto da una parte, dopo che arriviamo allo 0, prendiamo i resti e gli scriviamo dal basso verso l'alto*

>[!example] ### Supponiamo di avere (124)$_{10}$ 
>per converirla in base 2 prendiamo il numero e lo divi per 2;
>quindi 
>
|Numero|Quoziente|Resto|
|---|---|---|
|124|62|0|
|62|31|0|
|31|15|1|
|15|7|1|
|7|3|1|
|3|1|1|
|1|0|1|
>
	>ora scriviamo il numero da sinistra verso destra, partendo dall'basso della tabella verso l'alto ignorando eventuali zeri iniziali, quindi avremo: `1111100`

>[!question] E per fare da binario a decimale?
>per converire da binario a decimale, si parte dal bit di destra e si moltiplica il numero che c'è per la base elevato ll'esponente (l'esponente è il numero di volte che ti sei spostato a sinistra partendo da 0) e si sommano tutti i risultati ottenuti

>[!example] ### Suppponiamo di avere il numero (1111100)$_2$
>contiamo il numero delle cifre e facciamo una tabella con le potenze:
>
|Potenza| $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
|-----| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
>|Valore|64|32|16|8|4|2|1|
|numero da convertire| 1     | 1     | 1     | 1     | 1     | 0     | 0     |
>
>#### Ora che abbiamo più del necessario, andiamo a combiare le righe:
>```
>partiamo da destra, la cifra è 0, moltiplichiamola per $2^0$ che è 1
>$0*1$ fa 0, quindi mettiamo zero;
>Facciamo la stessa cosa per quello dopo, che è 0 e lo moltiplico per $2^0$ (che è 2), $0*2$ fa 0 quindi 0;
>Ora abbiamo un uno, facciamo la stessa cosa, quindi: $1*2^2$ che fa 4;
>Andiamo avanti, abbiamo un altro uno, facciamo come prima  $1*2^3$ che fa 8;
>Dopo abbiamo un altro uno, continuando $1*2^4$ fa 16
>Poi un altro 1, quindi abbiamo $1*2^5$ che fa 32
>Poi un altro 1, applicando $1*2^6$ che fa 64 
> ```
>#### Otterremo quindi una cosa del genere:
>| | | | | | | | | | | | | |TOTALE|
>| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---- | --- | --- | --- |
>|64|+|32|+|16|+|8|+|4|+|0|+|0| (124)$_{10}$|

>[!info] Che confrontando con il risultato di prima è corretto!

>[!note] Si possono anche fare delle operazioni matematiche sui numeri binari
>come la somma, che funziona proprio come in matematica
> 
| BINARIO | DECIMALE | OPERATORE |
| ---- | ---- | ---- |
| 0101  |  5   | +   |
| 0110  | 6   | =   |
| 1011 | 11  |     |
> $0+0 = 0$
> $0+1 = 1$ 
> $1+0 = 1$ 
> $1+1 = 0$ con riporto di 1 

>[!Question] Cosa succede se sommando i due numeri il risultato non può essere espresso con il numero di bit?
>Tutti i bit disponibili diventano 1 e ne rimane uno fuori, questo si chiama _Overflow_
>
| BINARIO   | DECIMALE | OPERATORE |
| --------- | -------- | --------- |
| 1111      | 15        | +         |
| 1010      | 10       | =         |
| $^1$ 1111 | 15??    |           |
Alla fine, arriviamo ad uno stato in cui chiediamo un prestito, ma non abbiamo un numero, quindi tutto diventa 1 (che non ha senso)
>Per risolvere si può aggiungere il bit, ma non sempre è possibile (ex: EEPROM)


>[!note] #### La sottrazione
>Che anche lei funziona come la matematica
>
| BINARIO | DECIMALE | OPERATORE |
| ---- | ---- | ---- |
| 1010 |  10   | -   |
| 0110  | 6   | =   |
| 0100 | 4 |     |
> $0-0 = 0$ 
> $1-0 = 1$ 
> $0-1 = 1$ con richiesta dal successivo
> $1-1 = 0$
> tutte le altre operazioni sono somme o sottrazioni ripetute

>[!Question] Cosa succede se sottraggo un numero troppo grande?
>Tutti i bit diventano 0, questo si chiama _Underflow_
>
| BINARIO   | DECIMALE | OPERATORE |
| --------- | -------- | --------- |
| 0010      | 2        | -         |
| 1010      | 10       | =         |
| $^1$ 0000 | ?        |           |
Alla fine, arriviamo ad uno stato in cui chiediamo un prestito, ma non abbiamo un numero, quindi tutto diventa 0 (che non ha senso)

### Complementi
per risolvere il problema della sottrazione e per avere dei numeri negativi, si usano i complementi ad 1 e 2
il complemento ad uno, serve ad esprimere il numero negativo sacrificando un bit che viene chiamato: _bit di segno_.
Si esegue in questo modo:
- Assicurati di avere al meno un bit in più rispetto al numero più grande che vuoi rappresentare, quindi se vuoi scrivere massimo 4, devi usare 4 bit (1 per il segno e 3 per il numero)
- Converti il numero in binario (se lo hai già fatto vai allo step successivo)
- Inverti tutti i numeri (1->0) e (0->1)

>[!example] Supponiamo di volere il numero -10 usando un byte
>Facciamoci la domanda: Posso scrivere 10 usando 7 bit?
>$2^7 = 128$ quindi SI  
>
>
>convertiamo 10 in binario:
>
| NUMERO | RESTO |
| ------ | ----- |
| 10     | 0     |
| 5      | 1     |
| 2      | 0     |
| 1      | 1     |
| 0      | 0     |
> ### In questo caso si aggiungono i bit a sinistra perchè voglio lavorare su 8 bit, ottenendo:
> 
|0|0|0|0|1|0|1|0|
|---|---|---|---|---|---|---|---|
> ### Applichiamo il complemento ad 1
> Partiamo da destra:
> 0 diventa 1
> 1 diventa 0
> 0 diventa 1
> 1 diventa 0
> 0 diventa 1
> 0 diventa 1
> 0 diventa 1
> 0 diventa 1
> Abbiamo ottenuto il numero negativo:
> 
| 1   | 1   | 1   | 1   | 0  | 1   | 0  | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
> il bit più a sinistra se settato ad 1 indica che il numero è negativo
### Proviamo a fare un addizione (che alla fine sottrae)
proviamo a fare  22-10 

| BINARIO  | DECIMALE | OPERATORE |
| -------- | -------- | --------- |
| 00010110 | 22       | +         |
| 11110101 | -10      | =         |
| 00001100 | 12       |           |
>[!Important] Se durante una sommma c'è un solo riporto al di fuori il risultato è corretto, ma se sfora di uno no 

>[!bug] Abbiamo un problema: in questo caso il range va da +0 a $2^{n-1}$ e - 0 a -$2^{n-1}$ 
>Questo vuole dire che abbiamo 2 zeri (-0 [11111111] e +0 [00000000] ) ; 
>Abbiamo bisognio di trovare un metodo diverso per rappresentarli

Ecco che viene in gioco il Complemento a due

---
### Complemento a 2
Per rappresentare tutti i numeri possibili usiamo il complemento a due (che è il complemento ad 1, ma aggiungiamo un uno dopo averlo convertito con il complemento ad 1).
Evita il caso +0 e -0

>[!example] Supponiamo di volere -5
>Facciamo il complemento ad 1 
>5 -> 000 101 -> 111 010 
>Aggiungiamo 1
>
| BINARIO | OPERAZIONE |
| ------- | ---------- |
| 111 010 | +          |
| 000 001 | =          |
| 111 011 |            |
> Ecco il numero!

>[!Important] Anche in questo caso se durante una sommma c'è un solo riporto al di fuori il risultato è corretto, ma se sfora di uno no 

---
# Sistema numerico Esadecimale
il sistema esadecimale, è un sistema numerico dove ogni cifra ha un peso che va da 0 a 15.
per convertire da esadecimale a decimale dobbiamo usare lo stesso sistema che abbiamo usato per convertire dal binario, ma al posto della base 2 mettiamo la base 16

>[!example] ### Supponiamo di avere il numero (FA4F)$_{16}$
>proviamo a fare la conversione come prima:
>
|POTENZA|  16$^3$   | 16$^2$   |16$^1$ | 16$^0$
|---| --- | --- | --- | --- 
|VALORE|  4096   |   256  | 16 | 1 | 
|HEX|  F   |   A  | 4 | F | 
>
>Ricordiamo i valori
>F->(15)$_{10}$
>4->(4)$_{10}$
>A->(10)$_{10}$
>
>Applichiamo l'algoritmo di prima:
> 
| HEX |  F   |   A  | 4 | F | |  
| ------| --------- | -------- | ------ | ------|  --- |  
| CONVERSIONE A DECIMALE| $15*4096$ | $10*256$ | $4*16$ | $15*1$ |   |  
| VALORE$_{10}$| 61440     | 2560     | 64     | 15     |  |  
|TOTALE|      |      |      |      | (64079)$_{10}$ |  


---
# Conversione tra basi

>[!question] Come convertiamo da una base ad una base?
>ci sono due modi: 
>1) Se le basi hanno il MCD in comune, se dividi le due basi e ti da un numero, devi raggruppare o separare di quei numeri
>2) Usi una base in comune (10)

### Primo caso:
>[!example] mettiamo caso di avere (37541)$_8$ e lo vogliamo convertire in binario
dividiamo le due basi (8/2) -> 4, quindi va bene, ora proviamo a vedere quanti bit mi servono per ottenere il numero massimo della base (2$^3$ -> 7) 
ora sappiamo che ogni cifra della base 8 sono 3 bit in binario
ora converitamo:
>
| OCT| (3)$_8$   | (7)$_8$   | (5)$_8$   | (4)$_8$   | (1)$_8$   |
| --- |---| --------- | --------- | --------- | --------- | 
|BIN| (011)$_2$ | (111)$_2$ | (101)$_2$ | (100)$_2$ | (001)$_2$ |  
> #### Uniamo il risultato con la colla vinillica :
> 011111101100001
> 

>[!note] NOTA BENE:
>Questa volta non si possono ignorare i bit vuoti

>[!info] Quà si può notare perchè è conveniente converitre in basi più grandi
supponiamo di avere due fogli a4 dove ci stanno precisamente **2.000** caratteri, il numero più grande scrivibile è un numero così grande che non è scrivibile ($10^{602}$), 
se lo convertissi in oct, lo stesso numero richiederebbe solo 667 cifre ottali
se lo convertissi in hex, lo stesso numero richiederebbe solo 500 cifre esadecimali
se lo convertissi in base32, sarebbero solo 400
se proprio volessimo sgarrare, potremmo arrivare ad una base che occuperebbe un solo carattere
Questo vuol dire che possiamo scrivere numeri più grandi se usiamo basi più grandi.
