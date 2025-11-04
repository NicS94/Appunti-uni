Sappiamo che su linux tutto è un file, per questo si può dedurre che i dispositivi di input son considerati degli stream di byte.

Abbiamo 3 canali principali logici 
- stdi (standard input)
- stdo (standard output)
- strerr (standard error)
-
i risultati di un programma viene messo nel'output video Codificati in byte e trasmessi in un canale in comune con il dispositivo di output.
è una buona norma in un sistema buonfatto che il risultato giusto viene mandato nel canale stdo e salvare i dettagli di errore nel canale stderr su un file di LOG

linux ci permette di modificare i dispositivi standard di stream, questo si chiama redirezzione (Cambiare canale/dispositivi dove vengono trasmesse eo salvate le nostre informazioni), invece di usare uno schermo lo salviamo su file, come per esempio i file di log;
Per farlo, si devono usare degl'operatori chiamati "OPERATORI DI REDIREZIONE", come < (quello standard)

```bash

[utente@os $]: cat testo
	Ciao
	come
	stai
	
[utente@os $]: head -n 1 < file_testo
	 Ciao
	 
```

Operatore di Output (>)

l'operatore di output, scrive su un file il risultato dell'operazione di un comando sovrascrivendolo e creando il file se non esiste, esiste una variante (>>) che, se esiste il file viene messo il contentuo in aggiunta al restante




Operatore di errore (2>) viene usato per mettere su un file un errore dettagliato, anche quà esiste una variante per aggiungere a fine file (2 >> )



 ### Pipelining 
Serve in sostanza a mettere l'output dello standard output come paramentro di un altro comando;

per esempio: mettiamo di avere un mega ls con 30.000.000 di file, potremmo salvare il risultato del file e metterlo in output con il more(che mostra tantissimi dati alla volta che possono essere visualizzati riga per riga usando le freccie), potremmo provare ad usare gl'operatori "< >", di redirezzione, ma questo fallirà per questo si deve usare un operatore integrato su linux che lo fa in automatico, ovvero l'operatore: "|",ovvero operatore di pipe



### Manipolazioni di una riga

partiamo dai Regex che è una sequenza di caratteri che determinano un pattern, è usata per determinare dei testi che rispettano quel pattern.

i regex sono differenti per tutti non esiste proprio uno standard tranne per alcuni

per eseguirle su linux si usa il comando grep (general regular expression print) 
è usato per cercare delle ricorrenze di una riga in una serie di file

resituisce le righe dei file in cui si trova la re
Di base non tutti i meta-caratteri e le stringhe speciali illustrati in precedenza sono
compresi da grep, ma divengono tutti utilizzabili se si usa l'opzione -E.

comandi disponibili per il comando Grep:
- -i Diventa case-insensitive
- -l Elenca i file dove vi è un match
- -n Indica il numero di linea dei match
- -v Restituisce le righe che NON matchano
- -w Cerca un match nelle parole complete
- -x Cerca un match nelle righe intere
- -c Conta le righe che presentano un match

### Sorting
Il sorting, proprio come abbiamo visto con la Diruberto, permette di riordinare un input di un comando a seconda delle nostre neccessità.
Per fare questo si usa il comando Sort di linux, che data una serie di stringe esso le dividerà (di default usa gli spazzi, tabbature e punti) e gli restituisce ordinati grazie a dei criteri imposti, che di base è in ordine alfabetico il primo carattere.

Alcuni parametri sono:
- -b ignora gli spazi
- -f Ignora la distinzione tra minuscle e maiuscole
- -n Considera numerica la chiave di ordinamento
- -r Ordina in modo crescente 
- -o (file) mette il risultato nel fiile.
- -t (separatore), usa il secondo pavalore come separatore dielle chiabvi
- -k (s1) (s2) Usa i campi da s1 a s2 come chiavi di ordinamento
E se volessimo tipo cambiare tutte le maiuscole in minuscole o numeri?

semplice: si usa il comando "tr", che semplicemente dato un secondo comando 