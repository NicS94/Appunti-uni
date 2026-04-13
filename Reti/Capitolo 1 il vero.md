# Capitolo 1 -> Come sono fatte le reti

---
Le reti che usiamo sono complessisime, per questo ho deciso di sudividerle  in due macro-categorie, in un comodo
### Pie di pagina

>[!note] Primo blocco:
> ##### Struttura fisica di una rete
>Ovvrero:
 >- Come vengono trasmessi i dati (Tecnologie di trasmissione)
 >- Come sono categorizzate le reti (Topologia delle reti)
 >-  Scale di interconnessione?

>[!note]  Secondo blocco:
>##### Struttura software della rete 
>Diviso in:
>- Come ci si interfaccia con gli altri
>- Suddivisone in livelli
>- Come viene progettato un livello

---

# CAPITIOLO 1 (L'INIZIO)

Benvenuti in questo corso! io son-
Ah no aspe ho ci ho preso troppo la mano

**1 : LE RETI**
---
---
Partiamo da quello che effettivamente tutti si chiedono appena aprono un libro, e vedono acronimi strani tipo: **_'UMTS'**, **'JVM'**, **'POTS'**, **<u>'QUIC'</u>**, **'TDD'**_ che solo a leggerli viene un mal di testa;

Ovvero:

>[!Question] Che cosa è una rete?
> La risposta che i docenti normalmente rispondono è: "Un insieme di nodi collegati tra loro", ma non è molto facile da digerire, lascia molti perchè

>[!info] Chiariamo:
>Una rete, nel contesto di RC, una rete è mezzo di communicazione, il quale assieme a dei nodi (che possono essere pc, router, switch, bridge), permettono grazie ad un canale di communicazione (chiamato comunemente link) come un cavo ethernet, la communicazione tra calcolatori collegati ad essa.
>
>Dove questi calcolatori possono essere dei pc, telefoni, console
>Si. In sostanza sono dei pc;
>
>Questi si chiamano host (Attenzione! ci sono dei casi in cui il nome cambia)

>[!note] Piccoli cenni storici:
>Tanto tempo fa, circa nello scorso secolo, quando ancora i computer erano grandi quanto una stanza, esisteva un concetto chiamato: "Centro di calcolo", che dei computer SINGOLI, accessibili a delle aziende/università, che costavano tantissimo ed erano meno potenti di un attuale caricabatterie PW100.
>Ora questo concetto è morto, ma ne è nato un altro chiamato: "Reti di calcolatori", che in sostanza sono dei 'server', che al loro interno hanno altri pc dove ogni pc senza coerenza, cioè ogni computer è una cosa differente ogni servizio sta in macchine diverse e ogni persona può vedere tutte le macchine, che è diverso da un altro concetto chiamato: "Sistema distribuito", che è un insieme di computer collegati tra loro che lavorano all'unisono, normalmente è un modello concettuale, ma ci sono dei casi in cui è stato applicato tipo il "World Wide Web", che si appoggia su internet implementando un modello a documento (Le pagine web).
>
>

## Quà qualcuno potrebbe dire: 

>[!Question] Fin quà ok ho capito, ma cosa fanno i nodi, chi sono i nodi, si mangiano?
>Beh figliolo, i nodi sono cose molto complesse da capire subito, specialmente se si entra nel dettaglio come faremo nelle prossime slide.
>Per rispondere alla domanda, immagina i nodi come delle persone: possiamo confermare che ogni persona ha un lavoro con un compito differente giusto?
>
>Ecco, anche i nodi possono avere dei compiti diversi, ci sono quelli che trasmettono dati solo quando richiesto, ci sono dei nodi che gestiscono il traffico, ci sono dei nodi che permettono addiritura di anionimizzare il tutto, ci sono dei nodi che ti permettono di parlare con il mondo e molti altri che non è necessario spiegare

---
## Tipi di reti:

Esistono vari tipi di reti come:
- La LAN -> "Local Area Network" un collegamento fisico, che, collega tutti i pc dentro casa. Ogni pc ha un suo numero identificativo (Chiamato IP), che vedremo dopo, questo permette di comunicare tra di loro
- La MAN -> "Metropolitan Area Network" sempre un collegamento fisico, che collega tutti gli edifici di una città una con l'altra, usando un solo "computer", chiamato "router", che con un solo numero, rappresenta tutti i computer collegati ad una LAN.
- La WAN -> "Wide Area Network" sempre un collegamento fisico, che collega le varie città una con l'altra sempre "nascondendo" tutti i dispositivi sotto
- Internet -> La rete più grande possibile, questa collega stati tra di loro, sempre "nascondendo" tutti i dispositivi sotto
Esistono anche delle reti speciali, che non usano un collegamento fisico come le VPN ("Virtual Private Network") che sono dei programmi che girano dentro ai pc che fanno si che attraverso Internet tutti i pc con quelle configurazioni possano vedere e comunicare come se fossero sulla stessa rete in modo SICURO 

# Entriamo nel cure della materia:
 
 >[!question] Perchè dovrei avere una rete in un azzienda?
 >Mettiamo caso che nell'azienda ci siano 200 persone, ogni persona ha il suo computer privato, dove ci scrivono le loro robe come:
 >- documenti
 >- brochure
 >- buste paga
 >- e altro
 >```
 >Domanda: Quanto costerebbe all'azienda, se dovesse avere una stampante per ogni dipendente? 
 >	Risposta? Tanto  
 >Domanda: E con la rete invece?
 >	Risposta: Immagina di avere una rete che oltre a permettere di stampare permette anche di salvare una copia di dati in un datacenter di backup, pensandoci bene, se l'azienda dovesse avere 4 reparti da 50 persone, si risparminano 196 stampanti (che mediamente costano 100 euro a stampante)
 >```
 >Quindi i costi dell'azienda diminuiscono, e di **tanto**. 
 >Per questo la rete LOCALE o "LAN", che sta per: "Local Area Network" è stata inventata

Un altro motivo per cui è stata creata questa rete è per poter avere della ridondanza in caso di guasto di uno dei computer al suo interno o per qualsiasi altro motivo che potrebbe mandare ko un pc.

ovviamente per ogni compito i pc devono poter parlare tra di loro usando un metodo di trasmissione diverso come il "Peer-to-Peer" (P2P) per communicare direttamente con l'altra macchina in modo puro, senza intralci, utile per condividere della musica, posizioni, comunicare con un server in generale e molto altro.
solo che il metodo in se non è per niente sicuro, lasciando ai developer libera interpetazione usato anche per la messaggistica, come le mail, che usano un modo particolare per comunicare e mandare dati, conosciuto come "Messagistica istantanea"

Parliamo ora di categorie di trasmissione serie e sicure come:
- La C2G -> "Consumer to Consumer", che permette a due persone di poter pagare e ricevere i soldi, in modo sicuro, comodamente da casa, usata da siti tipo: "Ebay"
- La B2B -> "Business to Business", che permette a due aziende di poter eseguire ordini e/o comunicare messaggi
- La B2C -> "Business to Consumer", che permette ad una persona di poter comunicare con un azienda, per poter ordinare in modo sicuro delle cose un esempio è Amazon
- Infine la G2C -> "Goverment to Consumer", che permette di eseguire operazioni legali comodamente a casa (come le dichiarazioni delle tasse, ordinare il passaporto ecc...

Parliamo di altre applicazioni della rete
Un esempio è la televisione tramite internet (Come sky), che usa un modo di communicare chiamato: IPTV (basato sulla tecnologia IP, che al posto delle antenne radio, usa una connessione internet per fare dello streaming)
Un altro esempio è la "Ubiquitous computing", in sostanza sono i dispositivi connessi alla rete usati nella vita reale (Sistemi di sicurezza, cancelli smart, lavatrici, ecc)

Ci sono dei dispositivi che possono comunicare con altri dispositivi senza fili, usando le reti Wireless dove il dispositivo si collega ad un nodo (chiamato Access Point) che poi comunica con internet usando una rete cablata
Oppure ci sono apparecchi che comunicano tra di loro usando la corrente di casa
alcuni di questi peremttono di comunicare, solo se sono molto vicini, come il "RFID" ovvero "radio frequency identification", che usa delle schede con un antenna che quando avvicinate ad un lettore che legge il suo codice permette di fare svariate cose dal pagare al aprire la porta dell'motel


 Come applicata una rete di calcolatori?
 