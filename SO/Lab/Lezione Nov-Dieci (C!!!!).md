### Nuovo capitolo (C)

>[!IMPORTANT] scriveremo dei programmi c che serviranno a fare operzioni a livello SO che interfacciano, in sostanza i thread e applicazioni che permettono di comunicare tra di loro.

>[!DANGER] 
Inoltre si faranno le GUI!!!!!


------------------------------------------------------------------------
## Storia del c

C nasce dall linguaggio di programmazione B, nei laboratori bell alla fine degl'anni '70.
Sviluppato da ritchie dennis e ken ed il suo amichetto, la sua idea era di impiegarlo per la scrittura di UNIX, un sistema operativo fatto da ritchie e ken che doveva essere ottimizzatissimo.
Nel '78 fanno un libro che parla della storia del liunugaggio e bla bla bla lo abbiamo già fatto in pr1.

------------------------------------------------------------------------
## Struttura del c

- C è compilato, ovvero prima viene converito e poi viene eseguito, al confornto della bash che viene eseguito istruzione per istruzione;
- Inoltre C più vicino al basso che all'alto livello (permette la gestione di memoria, interazione con il SO ecc...);
- Non è orientato all'oggetto, quindi non ha classi, oggetti, eventi, e robe così però usa dei sottoprogrammi, questo definisce un linguaggio procedurale;
- lo si trova in tutti i contesti, dalle vm ai PLC;
- ha un sacco di tipi di dati.
------------------------------------------------------------------------
## Struttura di un programma C
>[!QUESTION] 
 Com'è fatto un programma in c??

Un programma c ha come funzione principale, un main, che è una funzione di ingresso, che è sia un entry point che un exit point.

La compilazione è divisa in:

| Direttiva     | Descrizione                                                                                |
| ------------- | ------------------------------------------------------------------------------------------ |
| preprocessing | macroespansione (sostituisce le macro) , inclusione di librerie, controllo errori e altro. |
| compilazione  | converte il c in assembly                                                                  |
| assembler     | converte il c in linguaggio macchina (bit)                                                 |
| linker        | collegava l'eseguibile al file necessari                                                   |

------------------------------------------------------------------------
## Compilazione: 
Per compilare (linux parlando) si utilizza GCC, che permette l'invocazione della pipeline di compilazione.
Inoltre gcc permette di inserire dei parametri:

1) -c salta il linking (produce il file .o)
2) -D `"<MACRO>=<VAL>)"`,  sostituisce il valore di una macro con il valore specificato
3) -O ottimizza il codice 
4) -g che compila il codice in modalità debug.

GCC produrrà un file chiamato: 'a.out' (nome di default), questo è il file eseguibile.

per cambiare il nome del file di output si usa il parametro: -o

ESEMPIO:

>[!EXAMPLE]
>``` bash
>gcc test.c -o test.out
>```

------------------------------------------------------------------------

## Debugger
Il debugger è un software atto a risolvere dei malfunzionamenti .
>[!BUG] = malfunzionamento (si il termine è stato coniato perchè negl'anni ~70 hanno trovato un animale in mezzo a dei relay di un pc che stava causando dei malfunzionamenti)

#### Come si debugga?
Per debuggare si usa GDB (GNU DEBUGER)
il commando -g di gcc include nel file delle istruzioni atte al debug.
Appena avviato GDB, comparirà una schermata dove è possibile inviare dei comandi al debugger, esse si autocompletano con tab.
#### Comandi ed eseguzione di GDB

Per il codice si usa il commando run;
Per mettere i brakepoint, che sono dei punti in cui il codice si ferma - possono essere utili per sapere i valori di certe variabili in un punto specifico, per questo si usa il comando b, break, breakpoint  seguito dal numero della riga/ nome della funzione;
Per eliminare i break point si usa il comando `delete <NUMERO BRAKEPOINT>`

>[!NOTE] NOTA BENE:
> Il numero del breakpoint è dato a seconda dell'ordine d'inserimento dell brakepoint - letteralmente un First in, first out.

>[!INFO] GDB include delle istruzioni che danno delle info su tutti i comandi, variabili e dati di esecuzione (tra cui le info sui breakpoint - che è infobreak).

Alcune delle più importanti istruzioni di GDB sono:
 I. next va avanti alla riga dopo senza debuggare le funzioni interne
 II. step invece va avanti riga per riga entrando dentro
 III.continue continua fino all prossimo breakpoint 
 IV. finish va avanti fino alla fine della funzione
 V. quit esce dal codice
 VI. esiste una gui tipo DDD che ha l'interfaccia.

Per includere più file si deve fare prima il -c dei due file e poi si fa gcc due file .o
>[!EXAMPLE]
>``` bash
gcc -c file1.c
gcc -c file2.c
>gcc file1.o file2.o
>```


questo unisce i due file.
>[!IMPORTANT] se uno dei due file cambia non è necessario rieseguire l'istruzione di conversione del file invariato, ma bisogna fare l'istruzione per quello cambiato e per il link.

makefile serve ad automatizzare il processo ed è fatto cosi:

1) il suo nome è Makefile con la m maiuscola
2) deve avere il nome dell'output : mettendo il nome dei vari file, nella riga dopo ci vogliono i comandi

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

