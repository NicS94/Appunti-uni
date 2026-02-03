Processo 

il processo è in sostanza l'istanza dell'comando, ovvero l'avvio di un proggramma
quando facciamo un commando potrebbe aprire altri comandi che a loro volta ne aprono altri, questo si chiama job, lavoro
un esempio la pipeline è un insieme di proccessi, quindi crea un job.

alcune shell permettono l'esecuzione del job

il job può essere eseguito in foreground eo in background
nel primo caso viene mostrato a schermo ciò che fa nel secondo la shell è libera e continua ad aspettare input

ovviamente se è in background non può interagire con l'utente


facciamo un esempio: "find / -name "*.txt" > output 2> error.txt &

la shell restituisce il numero del lavoro e il suo pid, solo però del primo job che viene chiamato, in caso il job chiami altri job non verranno stampati


quando  un job viene sospeso in output compare il suo numero e i suoi dati.

per vedere tutti i processi si usa il comando jobs;
l'opzione -l mostra il pid di ogni processo

l'output restituisce un simbolo:
+ + che dice il primo job disponibile
+ - è il job che diventerà il primario all fine di quell che ha il +
per modificare il certo job si usa il simbolo %n se si sa il suo id
%stringa se si conosce il suo nome 
%?


il comando fg, porta un job in foreground, senza numero, si riferisce a quello che ha il + nel comando jobs
stessa cosa per il comando bg che fa il resume del j\*b e lo mette in background.
i segnali vengono inviati ai job con il commando kill 
i più comuni sono : 
- SIGSUS (19) sospende;
- SIGTERM (9) termina;
- SIGRES (18) per riprendere.
il segnale si specifica con il -
quello di default è il segnale 9
si mette il pid come terzo parametro
si mette il % per identificare il numero del job, normalmente viene inviato a quello con il +.

il comando ps, mostra i porcessi assocciati al terminale corrente.
il comando tty mostra il nome del terminale attuale.
il comando top mostra tutti i processi e le loro info (tipo il taskmanager).