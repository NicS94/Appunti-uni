0Test condizioni sui file

per fare dei confronti su un file o su due stringhe si usa il comando test, che può essere rappresentato con '\[]'

Nb: mai supporre che l'input sia sempre giusto


Switch case:
per fare lo switch case si usa il comando 
```bash
case <str> in
<condizione> ) <comando> '<;; (break) , ;& (esegue tutti i comandi sotto degl altri casi senza controllare i casi), ;;& (continua con i casi successivi)>'

esac

```
per finire  si usa il commando 
```bash 
	esac
```

pattern matching
i caratteri jolly ora servono a trovare un pattern dentro una stringa, i gobling star sono i pattern differenti che non si scrivono come il classico pattern matching ma con un commando ti permette di fare delle cose varie;

```
[] un qualsiasi carattere interno

?() un intera espressione che si ripete max 1 volta
*() un intera espresssione che si ripete 0 o più volte
+() stessa cosa ma che si ripete 1 o più volte

{0 9999} tutto ciò che va da 0 a 999
```
il globbing si attiva ocn il commando shopt -s extglob

costrutto for:

``` bash
for ((assegnamento; condizione di stop; incremento))
do 
	<istruzioni>
done
```
esegue un ciclo finitio a seconda della  condizione inserita

costrutto foreach
``` bash
for <variabile> in <lista>
do
	<istruzuioni>
done
```
In questo caso scorre tutta la lista e la variabile  è l'elemento attuale dello scorrimento


costrutto while:
```bash 
while <condizione>
do 
	<commandi>
done
```

costrutto until è il costrutto opposto del while, ovvero ripete fino a quanto la condizione non diventa vera.

Array:
le nuove versioni della bash hanno implementato gl'array, che è una variabile che continene una catena di elementi di tipo diversi accessibili con le parentesi quadre, l'array appena inizializzati hanno valori casuali, funziona come il c

```bash 
arr = (1 2 3 4 5 6 7 192 "ciiao" )
${arr[9]} > "ciao"

${arr[14233]} > ???
arr[14233]=69
${arr[14233]} > 69
```

si usa la chiocchiola per convertire l'array in un tipo


Funzioni:
proprio come c si possono fare delle funzioni 

ci sono due modi:
```bash 
funcion funzione_a {

}
```
e poi:
```
funzione_a() {

}
```

le funzioni funzionano proprio come il commando bash, quindi le variabili $1 $2 $n dentro la funzione, servono per gl'argomenti della funzione.
per chiamarla, si fa : 

```bash
funzione_a "pippo" "pluto" "marco"
```

