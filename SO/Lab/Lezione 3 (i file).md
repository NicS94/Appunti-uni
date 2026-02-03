I computer nella norma sono utilizzati con l'intento di avere più utenti che creano e modificano i propri file.
Per evitare di poter far editare/eseguire dei file ad utenti non autorizzati, è stato necessario inventare un sistema di permessi.
I permessi, nel caso di linux sonn contenuti in un file chiamato Index node (I node), unico per file che contiene i metadati di esso (come data di creazione, permessi, e molte altre cose), i quali determinano a quale tipologia di utenti è consenta la modifica eo l'accesso al file.

---
### Analisi del comando ls

Su linux è predisposto il seguente comando:
>[!EXAMPLE] Esempio
>```bash
ls -l
>```

>[!INFO] 
>Esso restituisce il seguente:
>
>```bash
>-rw-rw-rw 1 Utente Gruppo 100 10 oct 2025 9:14 File.ext
>```
>


>[!INFO] Dove: il primo carattere sta per il tipo del file.
>Questi sono:
> - '-' regolare/testo;
> - 'd' directory;
> - 'l': collegamento;
> - 'b' :perifierica a blocchi con buffer;
>- 'c': periferica a caratteri con buffer;
>- 'u' periferica a caratteri senza buffer;
>- 'p' file FIFO;
>- 's': socket.


I successivi 3 caratteri, sono i permessi per il proprietario (Owner), ovvero i permessi del primo account creato sul sistema;
I la successiva serie di 3 caratteri, sono i permessi del gruppo di utenti dell'owner;
l'ultima serie di 3 caratteri, invece, indica i permessi per tutti gl'altri utenti del sistema.

Questi caratteri sono rispettivamente una rappresentazione binaria del permesso ma con dei caratteri per renderlo più leggibile.
 
>[!EXAMPLE] Esempio:
> Se si ha per esempio nel primo carattere la r e i restanti vuoti (r--), si ha il solo il permesso di leggerlo ma non di modificarlo od eseguirlo;
> se nella seconda posizione ho il carattere w e i restanti vuoti (-w-), è possibile scriverci, ma non visualizzarlo nell'esplora risorse.
> Se nella terza posizione ho la x e i restanti vuoti (--x), posso solamente eseguirlo.
> Questo si applica anche agl'altri 3 blocchi, e se si ha un '-' al posto del carattere vuol dire che non è attivo quel permesso, si possono fare dei mix dei permessi, come rwx o rw o rx o wx ecc..

Dopo i permessi c'è un numero, che rappresenta il numero di collegamenti associati al file
Poi il nome utente proprietario del file;
La dimensione in byte del file;
Le 3 stringhe dopo è la data dell'ultima modifica del file;
E infine il nome del file.

---
### Analisi del comando chmod

>[!QUESTION] Come si fa a modificare i permessi di un file?

>[!INFO] 
>Per modificare i permessi si usa il comando chmod che serve a modificare i permessi di un file.

 chmod, Prende come parametri d'ingresso  il comando e due stringhe, un espressione ed un percorso: 
 primo parametro sono gli utenti afflitti e va messo prima dell'espressione:

> - [ ] Owner u;
 >- [ ] Gruppo utenti dell'Owner g;
 >- [ ] Tutti gl'utenti: o;
 >- [ ] Tutte le persone e gruppi:'a';

 >[!NOTE] Nota bene:
 >può essere seguito da un + o - per mettere o togliere i permessi da modificare 

---
### Definizione di gruppo

Un gruppo è un insieme di utenti, utilizzato dal File system di Linux per semplificare la gestione dei permessi ai file.

#### Come funziona il sistema

Ogni utente ha il proprio gruppo base, definito come gruppo primario, il quale avrà lo stesso nome dell'account (se invariato);
per modificare il nome di questo gruppo, si può usare il comando =='chgrp'== [^1] .

Ogni utente può entrare in altri gruppi secondari i quali avranno permessi diversi (valogno i permessi del gruppo autorizzato più forte)

>[!Example] Si fà nel seguente modo:
> ``` bash
> Chmod u+rw file.txt
> ```
> Verranno inseriti all'admin anche i permmessi di rw.

>[!IMPORTANT] Nota bene:
chmod funziona anche in modalità numerica, ovvero si possono usare i numeri per specificare quali permessi dare a quale gruppo, il comando accetta 3 numeri che vanno da 0 a 7, questa è la sua maschera in binario,in sostanza lo 0 binario disattiva il permesso e l'1 lo attiva, questo sovrascriverà tutti i permessi del file

>[!EXAMPLE] Esempio
>
>``` BASH
chmod 752 file 
>```
>Si prendono le cifre una per una
>quindi viene convertito il 7 in binario (111) e viene applicato il permesso al primo account (in questo caso rwx) ciò significa che l'owner del file può sia leggere che scrivere che eseguire il file;
>
>Passando al numero successivo 5, convertendolo in binario esce 101, essendo il secondo carattere, il permesso: (r-x) verrà applicato al gruppo dell'owner, il suo gruppo quindi può sia leggere che eseguire il file, ma non modificarlo.
> infine si prende il terzo numero (2) e lo si converte in binario (010), questo permesso (-w-) verrà assegnato a tutti gli utenti, questi non possono vedere il file nel loro esplora risorse, ma  possono solo modificarlo [^2]

>[!ATTENTION] Attenzione 
>Siccome windows fa <span style="color: #FF1122;">schifo</span>, I comandi chmod, chown e chgrp non funzionano sul filesystem:<span style="color: #32a852;">' **FAT16 / FAT32 / exFAT e NTFS**</span> (Create usando il paramentro `-t vfat` del comando mount[^3])
Per esempio il filesystem FAT non supporta i permessi sui file, come fa linux.
Se si prova ad esseguire il comando, il terminale restituirà la riga: "Operation not permitted" fallendo l'operazione;
In altre parole, una partizione Windows avrà root come proprietario di default, ovvero il default quando si crea un file.

---
### Utenti e superutenti

Parliamo un pò degl'utenti:
un utente possiede una propria directory (home directory dell’utente) dove può creare, modificare, eseguire e leggere qualsiasi file fatto all'suo interno.
L'accesso esterne alla home directory è solitamente inibito per sicurezza

>[!EXAMPLE] Per esempio:
>evitare un accidentale danneggiamento di file di sistema vitali.

#### Superutenti
Esiste un utente chiamato: root, il quale può modificare qualisasi file ovunque nel file system (al confronto di windows che chiede dei permessi speciali).


Quando si crea un file questo riceve dei permessi che dipendono dai permessi della maschera.
Il comando umask (user mask) permette di vedere e modificare tale maschera.
Per modificare il proprietario, si usa il comando Chown, eseguibile solamente dall'superutente (root)

---
### Analisi del comando chown

il comando chown è un comando di linux che permette di cambiate l'utente proprietario di un file;
Per far si che il comando funzioni, l'utente di destinazione deve per forza esistere nel sistema.
chown accetta in input due parametri: il primo è il nome del nuovo proprietario e il percorso del/dei file, su usa il simbolino '\*'.

>[!EXAMPLE] Esempio
>``` bash
>$ ls -l
> ---------- 1 Nicola casa 4096 11 set 00:00 dati
$ chown Matteo ./*
>
>$ ls -l
> ---------- 1 Matteo casa 4096 11 set 00:00 dati
>```

--- 
### File
il file è un insieme di record, che sono a loro volta un insieme concreto e definito di dati.

il nome del file, su linux è un riferimento alla cella nella memoria, in cui sono immagazinati i sudetti record.

>[!NOTE] Nota:
>esistono dei tipi di file speciali che si chiamano link, che sono un collegamento che permettono di saltare da una parte ad un altra dell'File system.

divisi in:
- link fisici: sono il collegamento dal nome del file alla cella fisica di memoria, il nome del file è un i-node, ovvero un index node, dove sono immagazinati i metadati;
  per eliminare il file, bisogna eliminare tutti i link fisici, inoltre questi non possono essere creati per le cartelle o subdirectory perchè se usassimo i link fisici si romperebbe il file system, tutto sommato le cartelle non sono realmente salvate in memoria

 - link simbolici, che sono dei puntatori alla risorsa, è come un file puntatore che punta quella risorsa specifica.
   questi possono essere usati nei casi in cui il precedente non funziona.

>[!NOTE] Nota: 
>Per creare un link simbolico si usa il comando ln con l'opzione -s
> di default viene creato con il permesso 777 (rwxrwxrwx) e come tipo di file ha il valore 'l'.

>[!IMPORTANT] Ogni partizione e file system ha una propria organizzazione degli i-node.


[^1]: Il comando chgrp, è un comando che permette di cambiare i parametri di un gruppo e va a modificare il file /etc/group, file che contiene le informazioni sui gruppi.
	Per modificare il nome di un gruppo si fa semplicemente: ```chgrp Marco IForti```, questo cambierà il nome del gruppo da "Marco" a "IForti". 
	[Clicca quì per saperne di più (In inglese)....](https://www.gnu.org/software/coreutils/manual/html_node/chgrp-invocation.html#chgrp-invocation)

[^2]:Ragebait al livello mas[...↩](https://www.youtube.com/watch?v=dQw4w9WgXcQ)

[^3]:Il comando mount, serve ad "Attaccare" una periferica al computer, e permette la visualizzazione del file.
	la sua sintassi è: `mount <paramentro> <periferica> <cartella>` [Per saperne di più...](https://manpages.ubuntu.com/manpages/jammy/en/man8/mount.8.html)
	