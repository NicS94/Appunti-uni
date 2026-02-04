### Sistemi di numerazione
Nella vita di tutti i giorni, per contare qualcosa, usiamo i numeri;
questi numeri sono chiamati sitema di numerazione nel nostro caso è chiamato sistema decimale perchè fa da 0 a 9, ma ne esistono di molti altri, come quelli in base 2 (binario), quelli in base 4, in base 8, in base 16, IN BASE 2487!!!
si in sostanza sono infiniti.

# Sistema di numerazione binario
il sistema di numerazione binario accetta solo due caratteri per creare i numeri (0 ed 1)

>[!example] Un esempio di parola in binario
>010010 -> 34 in decimale
>1101 -> 12 in decimale
> 0000-> 0 in decimale

## Come convertire da una base ad un altre
per convertire da decimale ad un altra base, generalmente si usa la divisione successiva dove si divide il numero per la base, se esce un numero con la virgola lo approssimiamo e scriviamo il resto da una parte, dopo che arriviamo allo 0, prendiamo i resti e gli scriviamo dal basso verso l'alto

>[!example] ### Supponiamo di avere (124)$_{10}$ 
>per converirla in base 2 prendiamo il numero e lo divi per 2;
>quindi 
>
>|  numero | Risultato  |   resto  |
>| ---| --- | --- |
>| 124 |62 |   0  |
>| 62 | 31 |0 |
>|31|15.5|1|
>|15|7.5|1|
>|7|3.5|1|
>|3|1.5|1|
>|1|0.5|1|
>|0|0|0 |
>|0|0| 0|
>
>ora scriviamo il numero da sinistra verso destra, partendo da su ignorando gli zeri iniziali, quindi avremo: `001111100` $\implies$ `1111100`

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

## Ora parliamo di cose serie: altre basi 
Come detto prima esistono infinite basi, le più conosciute e le più diffuse sono: 
Binaria (0,1)
Ottale (0,1,2,3,4,5,6,7)
Decimale (0,1,2,3,4,5,6,7,8,9)
Esadecimale (0,1,2,3,4,5,6,7,8,9) per i numeri, poi si aggiungono dei caratteri per indicare numeri maggiori di 9 (perchè 10 sarebbe l'unione tra 1 e 0) (A,B,C,D,E,F)
Base 32 (0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V)
Base 64 (A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z,a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,0,1,2,3,4,5,6,7,8,9,+,/)