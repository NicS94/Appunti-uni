Test condizioni sui file

per fare dei confronti su un file oppure su due stringhe, si usa il comando test, che può essere rappresentato con le parentesi quadre ('\[]')

>[!IMPORTANT] Mai supporre che la condizione sia sempre giusta.

Parleremo dei costrutti di selezione, iterazione, operazione.
Prima di parlare questi, per aiutarci a comprenderli al meglio;
È prima necessario introdurre l'array.

---
## Array
Le nuove versioni della bash hanno aggiunto il supporto per gli array;
L'array è una variabile che continene una catena di elementi (anche di tipologia differente - per il linguaggio bash non essendo tipicizzato).
Per accedere ai vari elementi, bisogna usare le parentesi quadre, con la posizione dell'elemento, e proprio come c, appena esso viene iniziallizato, ogni cella, assumerà dei valori casuali

> [!EXAMPLE]
>  ```bash 
>arr = (1 2 3 4 5 6 7 192 "ciiao" )
>${arr[9]} > "ciao"
>
>${arr[14233]} > ???
>arr[14233]=69
>${arr[14233]} > 69
>```
>La `@` serve a separare gli elementi _individualmente_, mentre `*` li unisce in una sola stringa.

---
Switch-Case
Lo switch case, nel linguaggio bash, si realizza utilizzando la seguente struttura:
>[!EXAMPLE]
> ```bash
case <str> in
<condizione> ) <comando> '<;; (break) , ;& (esegue tutti i comandi sotto degl altri casi senza controllare i casi), ;;& (continua con i casi successivi)>'
>esac
>```
>

---
###  Costrutto for e foreach:
il costrutto for, è un ciclo determinato il quale viene eseguito tante volte quanto la condizione, questo richiede un assegnamento di un contatore, il quale servirebbe normalmente per terminare il ciclo.

il costrutto del for, nel linguaggio bash è realizzato seguendo questo schema:
>[!EXAMPLE]
>``` bash
for ((assegnamento; condizione di stop; incremento))
>do 
	><istruzioni>
>done
>```
esegue un ciclo finitio a seconda della  condizione inserita

>[!IMPORTANT] Le doppie parentesi indicano ll'inizio di un espressione matematica.

Il costrutto del foreach, è in sostanza una copia del costrutto for, che data una lista e una variabile, esso ciclerà tutti gli elementi della lista inserendo il riferimento dell'elemento del ciclo attuale dentro alla variabile;
In sostanza cicla tutti gli elementi e la variabile è l'elemento attuale.

Nel linguaggio bash è realizzato seguendo questo schema:
>[!EXAMPLE]
>``` bash
for <variabile> in <lista>
do
	><istruzuioni>
	>done
>```
>In questo caso scorre tutta la lista assegnando alla variabile  l'elemento attuale dello scorrimento.


---
### Costrutto while ed Repeat-until

costrutto while, proprio come c, esegue il ciclo un numero illimitato di volte;
Questo è rappresentato sulla bash utilizzando il seguente costrutto:
>[!EXAMPLE]
> ```bash 
>while <condizione>;
>do 
>	<comandi>
>done
>```
>
>Questo ripeterà fino a quando la condizione è true, e si fermerà appena essa diventa false.

costrutto until è il costrutto opposto del while, ovvero ripete fino a quanto la condizione non diventa vera e si scrive nel seguente modo:
>[!EXAMPLE]
>```BASH
>until <condizione>;
>do
>	<comando>
>done
>```
>Questo ripeterà il cliclo quando la condizione è uguale a false, e continuerà così fino a quando la condizione non diventa vera.

---
### Pattern matching
Riprendiamo i caratteri jolly:
i caratteri jolly ora possono servire a trovare un pattern dentro una stringa;

IL "gobling", è un pattern che non si scrive, come nel classico pattern matching, ma come una sorta di comando che permette di fare varie cose come:

>[!EXAMPLE]
>``` bash
[] un qualsiasi carattere interno
>?() un intera espressione che si ripete max 1 volta
*() un intera espresssione che si ripete 0 o più volte
+() stessa cosa ma che si ripete 1 o più volte
>
>{0 9999} tutto ciò che va da 0 a 999
>```
>il globbing si attiva usando il comando shopt -s extglob nella shell.



---
Funzioni:
proprio come c si possono fare delle funzioni, che sono dei segmenti di codici che con  una sola riga, permette l'esecuzione di più comandi, in sostanza come se ci fosse un ponte che collega la macchina da un punto a ad un altro punto per poi riportarla dove era prima. 

>[!EXAMPLE]
>ci sono due modi:
>```bash 
>funcion funzione_a {
>
>}
>```
>e poi:
>```
>funzione_a() {
>
>}
>```
>
>le funzioni funzionano proprio come il comando bash, quindi le variabili $1 $2 $n dentro la funzione, servono per gl'argomenti della funzione.
>per chiamarla, si fa : 
>
>```bash
>funzione_a "pippo" "pluto" "marco"
>```

