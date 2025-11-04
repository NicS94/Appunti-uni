I computer nella norma sono utilizzati con l'intento di avere più utenti che creano e modificano i propri file.
Per avere i file privati, ed evitare di poter far editare/eseguire dei file ad degl'utenti i cui non devono neanche sapere l'esistenza di questi file, è stato inventato il sistema di permessi.
I permessi, nel caso di linux, sono una serie di bit messi in un file (generalmente all'inizio di esso), i quali determinano a quale tipologia di utenti è consenta la modifica eo l'accesso al file.

Su linux è predisposto il seguente comando:
```bash
ls -l
```
che restituisce:

```bash
-rw-rw-rw 1 Utente Gruppo 100 10 oct 2025 9:14 File.ext
```

`Dove: il primo carattere sta per il tipo del file ('-' regolare/testo, 'd' directory, 'l': collegamento,'b' :perifierica a blocchi con buffer, 'c': periferica a caratteri con buffer, 'u' periferica a caratteri senza buffer, 'p' file FIFO, 's': socket);` 
`I successivi 3 caratteri, sono i permessi per il proprietario, ovvero il primo account creato sul sistema;`
`Gl'atri 3 caratteri successivi, sono i permessi per il grippo associato al file;
`I successivi 3 caratteri, sono i permessi per tutti gl'altri utenti, ovvero gl'account successivi a quello creato per primo sul sistema.`

Questi caratteri sono rispettivamente una rappresentazione binaria del permesso ma con dei caratteri, quindi se si ha per esempio nel primo carattere la r, si ha il permesso di leggerlo, nel secondo se ho la w posso scriverci, infine nel terzo se ho la x, posso eseguirlo.
questo si applica agl'altri 3 blocchi, e se si ha un '-' al posto del carattere vuol dire che non è attivo quel permesso, è come farlo in binario 000 -> 001... 

Dopo i permessi c'è un numero, che rappresenta il numero di collegamenti associati al file;
Poi il nome utente proprietario del file;
La dimensione in byte del file;
Le 3 stringhe dopo sono la data di creazione;
E infine il nome del file.

Per modificare i permessi si usa il comando chmod che serve a modificare i permessi di un file.
 Prende come parametro due stringhe, una regex e un percorso: primo parametro sono gl'utenti afflitti (admin u, gruppo associato al file g, tutti gl'utenti: o, tutti:'a') seguito da un + o - per mettere o togliere e poi i permessi da modificare si possono modificare più gruppi alla volta mettendoli prima del simblolo,il secondo parametro è il nome del file.

Un gruppo è un insieme di utenti, utilizzato in Linux per semplificare la gestione dei permessi di accesso ai file;
Ogni utente ha il proprio gruppo, chiamato: gruppo primario, il quale avrà lo stesso nome dell'account se invariato, che si può modificare usando il comando chgrp;
che accetta due argomenti:
il primo è il nome del nuovo gruppo di utenti, che deve esistere e bisogna appartenerci, e poi il nome del file.
Ogni utente può entrare in altri gruppi secondari i quali possono avere certi permessi per certi file

	Chmod u+rw file -> verra aggiutno all'admin i permmessi di rw

chmod funziona anche in modalità numerica, ovvero si possono usare i numeri per specificare quali permessi dare a quale gruppo, si va da 0 a 7 per gruppo (max 3 numeri), si converte il numero in binario e si applica il binario:

ex: 
chmod 754 file -> viene convertito il 7 in binario (111) e viene applicato il permesso che vale 1 al primo account (rwx) quindi posso sia leggere che scrivere che eseguire,poi si prende il secondo numero (5 in questo caso) e lo si converte in binario 5 -> 101 e lo si applica al gruppo del file (r-e), quindi il gruppo può leggere, eseguire ma non scrivere sul file, infine si prende il terzo numero (4) e lo si converte in binario 4-> 100 e lo si da a tutti gl'altri utenti (r--) ovvero tutti possono vedere il file ma ne modificarlo o eseguirlo 
	
Siccome windows fa schifo, I comandi chmod, chown e chgrp non funzionano sul filesystems: **FAT16 / FAT32 / exFAT ed NTFS** (create con l'operazione t vfat del comando mount)
Per esempio il filesystem FAT non supporta i permessi sui file, come fa linux.
Se si prova ad esseguire il comando, il terminale restituirà la riga: "Operation not permitted" fallendo l'operazione;
In altre parole, una partizione Windows avrà root come proprietario di default, ovvero il default quando si crea un file.

Generalmente un utente possiede una propria directory (home directory dell’utente) dove può creare, modificare, eseguire e leggere qualsiasi file fatto all'suo interno.
L'accesso esterne alla home directory è solitamente inibito per sicurezza
per esempio: evitare un accidentale danneggiamento di file di sistema vitali.

Esiste un utente chiamato: root, il quale può modificare qualisasi file, ovunque nel file system (al confronto di windows che chiede dei permessi speciali).


Quando si crea un file questo riceve dei permessi che dipendono dai permessi di
default che riceve ogni tipo di file e dal valore di una maschera che li filtra Il comando umask (user mask) permette di vedere e modificare tale maschera
Per modificare il proprietario, si usa il comando Chown, ovvero change owner, permessa solamente dall'superutente (root)


Chown: comando che permette di cambiate l'utente proprietario del file, ovviamente questo utente deve esistere nel sistema, accetta in input due parametri: il primo è il nome del nuovo proprietario e il percorso del/dei file, per più file su usa il '*'

```
$ ls -l
> ---------- 1 Nicola casa 4096 11 set 00:00 dati
$ chown Matteo ./*

$ ls -l
> ---------- 1 Matteo casa 4096 11 set 00:00 dati
```


il nome del file è un rifferimento alla cella di memoria in cui sono immagazinati i dati
Link è un collegamento che permette di saltare da una parte ad un altra dell'FS

diviso in:
link fisico (il collegamento dal nome del file, alla cella fisica di memoriae un i-node, dove sono immagazinati i dati)
per eliminare il file, bisogna eliminare tutti i link fisici.

i link fisici non possono essere creati per le cartelle o directory perchè se usassimo i link fisici per le cartelle, si romperebbe il file system.

i link simbolici sono dei puntatori alla risorsa, creato come un file puntatore che punta quella risorsa specifica questi possono essere usati nei casi in cui il precedente non funziona

Per creare un link simbolico si usa il comando ln con l'opzione -s e di default viene creato con il permesso 777 (rwxrwxrwx) e come tipo di file ha l'opzione 'l'

Ogni partizione e file system ha una propria organizzazione degli i-node
