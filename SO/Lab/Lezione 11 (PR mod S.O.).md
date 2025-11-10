La scorsa volta abbiamo parlato della programmazione di c

La programmazione di sistema è in sostanza l'uso delle system call che servono ad interagire con il sistema attraverso il kernel per fare delle cose fighe tipo creare i processi.

Come sappiamo l'informatica è basata sull'astrazione, ogni livello è sempre più segreto.

le API permettono di usare certe funzioni per fare certe cose.


---
## System calls

per creare una system call, si usa un prototipo di funzione, che è differente per system call ed è:

pid_t fork(void)-> restituisce null per errore.

questo permette di-