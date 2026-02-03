# Configuarzione della bash;


Su linux puoi personalizzare tutto il sistema grazie al sistema dei file (nb: su linux tutto è un file);

Normalmente, quando si devono modificare delle impostazioni dei programmi e salvarli in modo permanente, si usano i file di configurazione.

#### Cosa è contenuto in questi file di config?
Nei file di config ci sono delle variabili che contengono le varie impostazioni che al programma servono, ricordiamo che le variabili sono dei nomi la cui fa riferimento ad una cella di memoria dove sono contenuti dei dati.

Tra le mille variabili che sono contenute su i vari file della bash è la variabile: "$USER", che mostra l'utente attualmente contenuto.

#### Visualizzare, editare e modificare le variabili
L'utente può modificare, creare, aggiungere ed eliminare alcune variabili di sistema. Per convenzione, il nome di tutte le variabili è scritto in caps.
Una variabile è normalmente creata per un singolo utente e dura solamente per la sessione corrente, viene eliminata allo spegnimento o al logout dell'utente, ovviamente ci sono dei modi per salvarla , per salvarle per sempre si edita un file chiamato ".bashrc" che contiene tutte le variabili, NB: questi file sono univoci per utenti, quindi se si cambia utente esse non saranno presenti.  


Varaibili di ambiente: sono delle variabili che sono differenti per utente, alcune sono:


- GROUPS Un array contenente i numeri GID di cui l'utente è membro
- HOSTTYPE Architettura del computer
- OSTYPE Il nome del sistema operativo
- MACHTYPE Architettura e sistema operativo utilizzato
- BASH_VERSION Il numero di versione di bash
- BASH Il percorso completo della copia corrente di bash
- PPID Il PID del processo genitore della shell attuale
- UID User ID dell\u2019utente corrente
- PATH I percorsi di ricerca per i comandi
- HOME La directory home dell'utente
- CDPATH Il percorso di ricerca per il comando cd
- PS1 Il prompt primario (predefinito bash\$)
- PS2 Il prompt secondario (predefinito >)




Quelle più importanti sono:

CDPATH: è la variabile che contiene il percorso di ricerca per i comandi, ovvero la directory in cui sono quando faccio:
```bash
cd path
```

PS1: il prompt primario della bash, ovvero il messaggio prima del comando.

```bash
[UTENTE@os]$>
```

PS2: il prompt secondario della bash, ovvero quel messaggio che compare quando la bash si aspetta altro


PATH: è un array di percorsi possibili, separati dal carattere ':', che dice alla bash dove provare a cercare un determinato comando.
Questa è personalizzabile perchè ovviamente se installo un app in una posizione particolare devo sapere dove trovarla.

### Parametri

Nella documentazione originale di bash si utilizza il termine parametro per
identificare diversi tipi di entità come:
- Parametri posizionali
- Parametri speciali 
- Variabili di shell.
- 
Per evitare delle confusioni ci riferiamo a variabile solo ai primi due.

L’elemento comune tra i parametri e le variabili è il modo con cui li si utilizza quando si vuole leggere il loro contenuto: bisogna usare il simbolo $ davanti al nome (o al simbolo) dell'entità in questione per leggerne il valore, mentre per l’assegnamento (se possibile) non deve essere indicato e si fa facendo:
```bash
	
	[bash $]: echo $PARAM
	> 1234

	[bash $]: PARAM=34
	
	[bash $]: echo $PARAM
	> 34
```


per vedere i valori di un parametro da terminale, si usa il comando "echo" che letteralmente stampa sul terminale quello che gli si mette come parametro;
Esempio:
```bash
	[bash $]: echo $USER
	> Nicola
```
La shell restituirà: ``Nicola``, che risulta l'utente loggato al momento sulla macchina.
invece se si fa:
```bash
	[bash $]: echo USER
	> USER
```
il comando stamperà in output la parola: `USER`.

Per assegnare il valore di una variabile si usa il suo nome = valore;
NB: gli spazi hanno un valore importante, quindi non si possono usare almeno che non si fa il #quoting.
Inoltre durante un assegnamento di una variabile, non si possono usare i numeri come primo caratteree non si possono usare caratteri speciali, e non il "\_" e  se non si specifica il valore esso sarà vuoto.

Una variabile ha vita solo all'interno della shell nella quale viene creata, pertanto
cambiando shell, il sistema non riconosce piu quella variabile perchè sparisce, infatti quando si modificano i valori nel file ".bashrc", questi rimangono salvati su esso, e quando si apre un altra shell essa copia semplicemente le variabili dal file di config, e anche modificando il file di configurazione, i parametri appena salvati, non saranno visibili a tutte le shell già eseguite.
La variabile può essere resa visibile ai processi figli del processo shell corrente
‘esportandola’ mediante il comando export. Ad esempio

```bash
			TERMINALE 1                              TERMINALE 2
`#############################################################################
 #                                      #                                    #
 #	[bash $]: sudo su                   #  [bash $]: echo $MYVAR             #
 #	[ROOT \#]: MYVAR='testo di prova'   #  > myvar doesn\'t exist            #
 #  >                                   #  [bash $]: echo $MYVAR             #
 #	[ROOT \#]: export MYVAR             #  > myvar doesn\'t exist            #
 #  >                                   #                                    #
 #############################################################################
					TERMINALE 3 (APERTO DOPO L\'EXPORT)
 #############################################################################    # [bash $]: echo $MYVAR                                                     #
 # > 'testo di prova'                                                        #
 #############################################################################
```

Ora la variabile MYVAR è visibile anche da processi generati dalla shell corrente (ad
esempio, da uno script o un altra shell ma non da nuovi processi generati diversamente (ad esempio, un nuovo terminale aperto durante la
sessione corrente.

Per visualizzare le variabili definite per l'utente si può usare il comando set, mentre per visualizzare le variabili di ambiente occorre usare il comando env mostra le variabili della shell.


### Archivi
Gl'archivi su linux, sono un unione di file e cartelle che vengono messi all'interno di un file singolo.
Per creare un archivio e modificarlo si usa il comando: "TAR", il suo nome proviene dal passato: Tape ARchive, ovvero archivio su nastro.
È possibile modificare un archivio creato con il comando tar aggiungendo nuovi file o
eliminandone alcuni già presenti questo potrebbe essere utile per fare dei backup.

il comando tar è costruito nel seguente modo: 
```bash
tar [opzioni] [nome archivio] [nome files e/o directories]
```

partiamo dalle opzioni base (che a volte contengono una versione estesa):

- -f indica che la stringa successiva sarà il nome dell'archivio, se non specificata verrà preso il nome del primofile da archiviare e messo, questo potrbbe dare problemi
- -c serve per creare l'archivio
- -x serve ad estrare il contenuto dell'archivio che permette di navigare le cartelle e i file.
- -z serve a comprimere il file con gzip, invoca il programma, questo cambia l'estensione a .tar.gz, è opzionale per i file non compressi ed è obbligatorio per i file .gz

Un comando utile che potrebbe aiutare con il comando tar è il comando: "find", che serve a cercare un file in determinato percorso, generalmente è organizzato in questo modo: 
```bash
find percorso -name nomefile -print
```
dove:
- name nome è il nome del file o cartella dove si cerca
- print è l'opzione che serve a mettere il risultato della ricerca

##### Caratteri jolly 
Esistono dei "Caratteri jolly" che hanno delle funzioni particolari:

"*.estensione" è il carattere che ignora tutto quello che c'è prima del contenuto a sinistra del simbolo
"." indica la directory attuale.

- "!!" Riesegue l'ultimo comando appena eseguito
- "!n" Riesegue l'n-esimo comando presente nella storia. Es: !1 esegue il primo comando sulla history, !-1 esegue l'ultimo comando eseguito
- "!stringa" Riesegue l'ultimo comando che inizia con i caratteri indicati nella stringa.
- "!stringa:p"  Visualizza l'ultimo comando che inizia con i caratteri indicati nella stringa
- "!?comando?" Ricerca il comando specificato tra punti interrogativi history Visualizza l'elenco di tutti i comandi eseguiti

- "fc n" Permette di modificare l'n-esimo comando con l'editor predefinito
- "fc -e" 'nome' 4 Permette di modificare l\u2019 n-esimo comando con l'editor specificato
- "^comando1^comando2" Riesegue l'ultimo comando eseguito che contiene la parola ‘comando1’ sostituendola con ‘comando2‘
- "$[\text TAB ]$ " Autocompleta il nome di un file o di un comando
- AltGr + ì Permette di inserire un simbolo tilde ( ~ )
- AltGr + ' Permette di inserire un apice inverso ($`$) anche noto come backquote o backtick


### ALIAS 
Scrivere frequentemente dei comandi complessi contenenti numerose opzioni alla lunga è fastidioso, per questo si possono utilizzare dei sinonimi più facili da ricordare e da digitare. Consideriamo questo esempio Il comando mount monta la prima partizione del disco /dev/sda1 (specificando la formattazione del filesystem con l'opzione -t vfat) sulla directory di destinazione /mnt/mydir. 
Supponiamo che tale partizione contenga i file di Windows: sarebbe interessante poter sostituire tale comando con un semplice montaWindows.

Per creare il sinonimo di un altro comando si usa il comando `alias`. 
Per creare l'alias montaWindows occorre usare il seguente comando:

```bash 
 [bash $]: alias montaWindows='mount -t vfat /dev/sda1 /mnt/mydir'
```

Un alias puè essere utile per modificare il comportamento di alcuni comandi, come il comando rm, modificandolo a modo che  cancelli i file irreversibilmente senza chiedere conferma
Possiamo creare un alias di rm che includa tale opzione.
``` bash
[bash $]: alias rm='rm-i'
```

Per eliminare l'alias rm è possibile usare il comando unalias:
```bash 
[bash $]: unalias rm
```

Da questo momento, digitando il comando rm il sistema chiederà conferma prima di
cancellare qualsiasi file.


#quoting 
## QUOTING
Un compito molto importante delle shell Unix è quello di rimpiazzare variabili e
simboli speciali con il valore che rappresentano. 
Esistono però contesti in cui abbiamo bisogno della funzione opposta, ossia evitare che alcuni simboli speciali vengano interpretati ed espansi, per questo si usa il quoting.
Sfortunatamente anche i simboli che proteggono dall'espansione sono soggetti a loro volta ad un procedimento di sostituzione: 
quando la shell ha terminato l'interpretazione di una istruzione con caratteri speciali, questi devono essere rimossi in modo da non lasciare tracce per un eventuale programma che ricevere questi dati in forma di argomenti.

Il quoting è un meccanismo di aggiunta di deliminatori per evitare che vengano interpretati male alcuni simboli, si usano:

- ( \ ) Backslash è il carattere di escape, consente di neutralizzare singoli caratteri speciali.
- ( ' ) Single Quotes Gli apici singoli disattivano qualsiasi carattere speciale (da non confondere con le backquotes).
- ( $"$ ) Double Quotes Gli apici doppi o virgolette disattivano qualsiasi carattere speciale ad eccezione di dollaro ( $ ), backquotes ( $`$ ), backslash $( \text {\\} )$, Gli apici potrebbero sembrare intercambiabili tra loro, ma esiste una differenza: gli apici doppi non neutralizzano i caratteri dollaro ( $ ) , backquotes $( ` ) \text {e backslash} ( \text \\)$

Il quoting è usato in operazioni di tutto il giorno, per esempio voglio accedere ad un file o una cartella che contiene degli spazi all’interno del nome. Se il carattere di spazio non viene disattivato, il comando potrebbe considerare la stringa, come una sequenza di argomenti e restituire un errore.

#### Command substitution

La command substitution è simile al quoting, ma ha lo scopo di interpretare come comando la stringa racchiusa tra i caratteri di backquotes $( ` )$ (noto anche come backtick).
Sul terminale, si può digitare una backquote con la shortcut AltGR + ',
Una forma alternativa ed equivalente prevede di incapsulare il testo tra $( ... ) questa forma può essere innestata.

La command substitution è spesso utilizzata negli script che compiono azioni automatiche e che richiedono parametri (ad esempio per un backup periodico automatico che richiede di volta in volta una data diversa).

Se si desidera che caratteri speciali vengano riconosciuti come parte di stringhe è necessario utilizzare le single quotes per racchiudere la stringa.
Se si desidera effettuare l'escape di un singolo carattere si può utilizzare il backslash
(ad esempio il simbolo $ lo richiede obbligatoriamente)