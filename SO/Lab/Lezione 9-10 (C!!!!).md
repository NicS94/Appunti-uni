### Nuovo capitolo (C)


>[!IMPORTANT]  La scorsa lezione abbiamo fatto solo esercizi bash; <br><br> Da ora in poi, scriveremo dei programmi c che serviranno a fare operzioni a livello SO, e che interfacceranno altri programmi. <br><br>In sostanza i thread e applicazioni che permettono di comunicare tra di loro.

>[!ERROR] Inoltre si faranno le GUI!!!!!


------------------------------------------------------------------------
## Storia del c

C nasce dall linguaggio di programmazione B, nei laboratori bell alla fine degl'anni '70.
Sviluppato da ritchie dennis e ken ed il suo amichetto, la sua idea era di impiegarlo per la scrittura di UNIX, un sistema operativo fatto da ritchie e ken che doveva essere ottimizzatissimo.
Nel '78 fanno un libro che parla della storia del liunugaggio e... bla bla bla lo abbiamo già fatto in pr1.

------------------------------------------------------------------------
## Struttura del c

- C è compilato, ovvero prima viene converito e poi viene eseguito, al confornto della bash che viene eseguito istruzione per istruzione;
- Inoltre C è più vicino al basso che all'alto livello (permette la gestione di memoria, interazione con il SO ecc...);
- Non è orientato ad oggetti, quindi, non ha classi, oggetti, eventi, e robe così però usa dei sottoprogrammi, questo lo definisce un linguaggio procedurale;
- lo si trova in tutti i contesti, dalle vm ai PLC;
- ha un sacco di tipi di dati.
------------------------------------------------------------------------
## Struttura di un programma C

>[!QUESTION]  Com'è fatto un programma in c??
> Un programma c ha come funzione principale, un main, che è una funzione di ingresso, che è sia un entry point che un exit point.

La compilazione è divisa in:

| Direttiva     | Descrizione                                                                                |     |
| ------------- | ------------------------------------------------------------------------------------------ | --- |
| preprocessing | macroespansione (sostituisce le macro) , inclusione di librerie, controllo errori e altro. |     |
| compilazione  | converte il c in assembly                                                                  |     |
| assembler     | converte il c in linguaggio macchina (bit)                                                 |     |
| linker        | collega il codice in linguaggio macchina a quello compilato delle funzioni di libreria (standard o meno) usate nel programma (come `printf`) per creare un unico eseguibile                                                 |     |

------------------------------------------------------------------------
## Compilazione: 
Per compilare un programma C su linux, si utilizza <span style="color: #32F852;">'GCC'</span>, che permette l'invocazione della pipeline di compilazione.
Inoltre <span style="color: #32F852;">'GCC'</span> permette di inserire dei parametri di input;
Alcuni di questi sono:

1) <span style="color: #cc8c1d;"> -c </span> salta il linking (produce il file .o)
2) <span style="color: #cc8c1d;"> -D </span> <span style="color: #ee54ff;">"&lt;MACRO&gt; </span> = <span style="color: #ee54ff;"> &lt;VAL&gt;"</span>,  sostituisce il valore di una macro con il valore specificato
3) <span style="color: #cc8c1d;"> -O </span> ottimizza il codice 
4) <span style="color: #cc8c1d;"> -g </span> che compila il codice in modalità debug.

<span style="color: #32a852;">'GCC'</span> produrrà un file chiamato: 'a.out' (nome di default), questo è il file eseguibile.

per cambiare il nome del file di output si usa il parametro: -o



>[!EXAMPLE] ESEMPIO:
>``` bash
>gcc test.c -o test.out
>```

------------------------------------------------------------------------

# Debugging
Il debugger è un software atto a risolvere dei malfunzionamenti .
>[!BUG] = malfunzionamento (si il termine è stato coniato perchè negl'anni ~70 hanno trovato un animale in mezzo a dei relay di un pc che stava causando dei malfunzionamenti)

>[!QUESTION] Come si debugga???
Per debuggare si usa <span style="color: #32F852;">'GDB'</span> (<span style="color: #DF0A10;">G</span>NU <span style="color: #DF0A10;">D</span>E<span style="color: #DF0A10;">B</span>UGER)
il commando -g di <span style="color: #32a852;">'GCC'</span> include nell'output delle istruzioni atte al debug.
Appena avviato <span style="color: #32F852;">GDB</span>, comparirà una schermata dove è possibile inviare dei comandi al debugger, esse si autocompletano con tab.
#### Comandi ed eseguzione di GDB

Per il codice si usa il commando <span style="color: #9bA8FF;">'run'</span>;
Per mettere i brakepoint, che sono dei punti in cui il codice si ferma - possono essere utili per sapere i valori di certe variabili in un punto specifico, per questo si usa il comando '<span style="color: #9bA8FF;">b</span>,<span style="color: #9bA8FF;"> break</span>,<span style="color: #9bA8FF;"> breakpoint</span>'  seguito dal numero della riga/ nome della funzione;
Per eliminare i break point si usa il comando <span style="color: #9bA8FF;">delete </span><span style="color: #ee54ff;"> &lt;NUMERO BRAKEPOINT&gt;</span>

>[!NOTE] NOTA BENE:
> Il numero del breakpoint è dato a seconda dell'ordine d'inserimento dell brakepoint - letteralmente un First in, first out.

>[!INFO] GDB include delle istruzioni che danno delle info su tutti i comandi, variabili e dati di esecuzione (tra cui le info sui breakpoint - che è infobreak).

Alcune delle più importanti istruzioni di GDB sono:
 - I.<span style="color: #9bA8FF;"> next </span>va avanti alla riga dopo senza debuggare le funzioni interne
 - II.<span style="color: #9bA8FF;"> step </span>invece va avanti riga per riga entrando dentro
 - III.<span style="color: #9bA8FF;">continue </span>continua fino all prossimo breakpoint 
 - IV. <span style="color: #9bA8FF;">finish</span> va avanti fino alla fine della funzione
 - V. <span style="color: #9bA8FF;">quit</span> esce dal codice
 - VI. esiste un debugger con GUI come <span style="color: #32F852;">'DDD' </span>che ha l'interfaccia e permetto di visualizzare tutte le informazioni in modo grafico mostrando variabili e strutture dati complesse con rettangoli e freccie per i puntatori, facilitando il debugging.

Per includere più file si deve fare prima il -c dei due file e poi si fa <span style="color: #32F852;">''GCC'</span> due file .o
>[!EXAMPLE] ESEMPIO
>``` bash
gcc -c file1.c
gcc -c file2.c
>gcc file1.o file2.o
>```
>questo unisce i due file.



>[!IMPORTANT] se uno dei due file cambia non è necessario rieseguire l'istruzione di conversione del file invariato, ma bisogna fare l'istruzione per quello cambiato e per il link.

--- 
### Makefile
per automatizzare il processo di compilazione, in caso avessimo tantissimi file, è stato inventato un sistema chiamato: 'makefile' che legge un file chiamato "Makefile", con la emme maiuscola.

#### Struttura di un makefile
partiamo dalle basi: 
un makefile al suo interno è composto da un insieme di regole e di comandi da eseguire.



>[!INFO] il clean serve per rimuovere certi file non volontari, usata raramente, ed è priva di dipendenze, quindi può essere eseguita da sola.

>[!EXAMPLE]
>```
>a.out: file1.o file2.o
>	gcc file1.o file2.o
>file1.o: file.h file1.c
>     gcc -c file1.c
> file2.o: file.h file2.c
> 	gcc -c file2.c
> clean: 
> 	rm -fr *.o
> ```
> 

