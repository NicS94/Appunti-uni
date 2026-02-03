
Abbiamo visto un sacco di programmi su linux, ma è noioso fare certi commandi a mano o a volte anche impossibile, per questo esistono dei file (file bash) che permettono di fare degli script di sistema per controllare queste macchine


la bash è programmabile usando il linguaggio bash, che a differenza di c che è compilato il bash è interpretato, questo vuol dire che quando un programma bash crasha, potrebbe aver modificato un file che rimane accessibile a tutti, per questo deve essere gesitito


i file bash si mettono dentro estensioni.sh e si può eseguire se si ha il permesso di lettura usando il comando: bash e subito odpo il nome del file.
Se si ha il permesso di esecuzione basta fare ./file.sh

All'inizio del file ha bisognio dei caratteri #! chiamati SHABANG
in sostanza indica alla bash quale interprete usare, il default è: bin/bash.
```bash
#!bin/bash

```

I commenti si mettono con l'hastag per singola riga e la sequenza:

``` bash
:' 


'
```

Per scriptare si usa un editor di testo classico; si usa GEDIT per convenzione essendo una GUI e perchè offre delle cose differenti.
però per scriptare su shell esistono moltissimi editor di testo, come vi,vim e (nano preinstallato su molte distro)


Variabili:

le variabili non hanno un tipo (non si dichiarano i tipi ) e si dichiarano con l'operatore uguale.
alcuni comandi possono dichiarare dei tipi di variabili tipo expr e let

per ottenere il valore si usa il dollaro e tutto ciò che viene messo dentro una variabile è una stringa si mettono le graffe per evitare problemi di lettura di variabili quando si usano

$var != ${var}


echo $var > "   " 
echo ${var} > "valore"


gli script sono dei veri e propri comandi
ci sono delle varaibili speciali che sono gl'argomenti del file che sono $0 (nome del programma)
$1 (primo argomento)
$2 (secondo argomento)
$n (n esimo argomento)



alcune variabili speciali:

$* tutti i parametri passati come unica stirnga
$@ tutti i parametri passati al comando come array di stringhe
$# il numero dei parametri passati al comando
$? il codice di uscita del job più recente eseguito
$! id relativo al processo leader del job più recente
\$$ id della shell
$0 il nome della shell in uso sul terminale o il nome dello script


input da terminale: si usa il comando read e gli passo la variabile 
read var

${var} > input


per avere più input si mettono gli spazi come c


se metti 2 variabili quando sono richieste una sola ma ne mette molte gli mette tutti in una var, in caso contrario vengnono riempite tutte le variabili tranne quelle vuote

comando clear: cancella lo schermo
per gestire i numeri dobbiamo usare dei comandi specifici tipo: expr

let per assegnare un espressione in un altro modo

le parentesi in questo caso valgono come espressione tutto cio che c'è dentro


exit status si assegna con exit 'codice'

costrutto if then else:


``` bash
if <comando>
	then
		<blocco vero>
	else
		<blocco falso>
fi
```
non è un espressione booleana è semplicemente l'esecuzione di un comando e se il suo exitcode è uguale a 0 entra nel true