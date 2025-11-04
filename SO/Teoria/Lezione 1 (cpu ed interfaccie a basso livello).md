##### Un calcolatore / sistema hardware che non usa un sistema operativo come appoggio, dove il suo codice viene eseguito direttamente dal processore viene chiamato: "bare metal".



![[Pasted image 20251028081718.png]]
>[!info] La struttura di un sistema bare metal

### Processore
Il componente che permette di eseguire le istruzioni si chiama: processore;
Ogni processore ha una sua lingua differente la quale si occupa di poter risolvere un algoritmo ben definito, questo si chiama: "Instruction set", che è una serie di stringhe in binario univoche per il processore, questo lo definiamo: "codice macchina";
Come noi esseri umani, anche il processore non capisce altri instruction set / linguaggi di programmazione, se non il suo prioritario, ma con degl'algoritmi particolari che vedremo dopo si può fare.

#### Instruction set
ogni instruction set, per decenza, ha una sua definizione con un linguaggio assemblativo, che contiene istruzioni _human-readable_, ovvero leggibili da un essere umano.
Tuttavia, per scrivere i programmi, ormai si usano dei linguaggi di programmazione ad alto livello (per alto livello quà s'intende per un linguaggio di programmazione differente dall'assembly), come il C, dove non è necessario conoscere l'IS dell processore, questo si fa grazie alla compilazione, che grazie al compilatore, che è un programma eseguito a basso livello, converte il codice da alto livello all'instructionset dell processore attuale.
Questo vuol dire fino a quanto si ha un compilatore per quel'archittetura, lo stesso codice ad alto livello può essere usato per più processori differenti, al confronto dell'assembly, che è univoco.

il compilatore converte il codice in assembly il quale poi con l'assemblatore lo converte in codice macchina, che poi grazie al  linker and loader, che mette in memoria i dati necessari, come le variabili.

|                                      | ![[Pasted image 20251028083507.png]] |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20251028081718.png]] |                                      |

### Esecuzione delle istruzioni
Un processore, per eseguire le sue istruzioni, deve prima di tutto avercele salvate in una memoria, che si chiama: memoria istruzioni, questa appunto contiene tutte le istruzioni necessarie per eseguire le istruzioni, queste celle di memoria devono avere delle sequenze di bit nel formato dell'IS della cpu, per operare sulle variabili o comunque per fare delle operazioni in generale, si ha un altra memoria.
Il caricamento dell' istruzione dalla memoria ai registri è detto fetch dell'istruzione.

