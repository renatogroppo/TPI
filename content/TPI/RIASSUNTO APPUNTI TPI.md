
==Il sistema operativo==
Il SO (sistema operativo) fa parte del software di base, inteso come insieme di programmi che consentono all’utente di utilizzare un calcolatore

Il software di base è costituito da:

- SO 
- editor
- compilatori
- linker
- loader è un componente del sistema operativo responsabile del caricamento di un programma in RAM
- debugger

==funzione numero uno del SO==
Il SO svolge la funzione di gestore di risorse hardware (le risorse sono gli elementi hardware o software del PC) Il SO supervisiona la scrittura e lettura dei dischi, la ricezione e la trasmissione dei dati attraverso tutti i dispositivi di I/O, l’esecuzione dei programmi caricando istruzioni e dati in RAM.

==funzione numero due del SO==

Il SO fornisce all’utente il supporto (un’interfaccia grafica o a linea di comando) per impartire i comandi necessari al funzionamento del computer. 


==SO architettura a cipolla==

Il kernel è un insieme di programmi del SO che:

● permette l’interazione tra HW e SW 

● è l’unico autorizzato ad accedere direttamente all’hardware, 

● gestisce le risorse HW nel modo più efficiente possibile controllandone tutti gli accessi 

● è responsabile dei driver più importanti 

● è responsabile per la trasmissione e la mediazione dei comandi

  

==le funzioni sono:==

● Gestire la memoria: controlla quanta RAM viene usata e dove. 

● Gestire i processi: determina quali processi possono usare la CPU, quando e per quanto tempo. 

● Interagire coi Driver del dispositivo: si occupa dell’intermediazione tra l’hardware e i processi. 

● Gestire chiamate di sistema: accetta richieste di servizio dai processi.

l’utente può accedere alle chiamate di sistema grazie alla shell (interfaccia grafica) che avvolge il kernel per proteggerlo, l’interfaccia può essere grafica (GUI) o a linea di comando (CUI).

==**Gestore del processore**==

  

I SO moderni sfruttano le potenzialità di parallelismo dell’hardware per minimizzare i tempi di risposta del sistema ed aumentare il throughput del sistema (numero di programmi eseguiti per unità di tempo).

 *Importante distinguere tra:*

● Programma: insieme di istruzioni, memorizzato su memoria di massa.

● Processo o task: istanza di programma in evoluzione, cioè che è eseguito dal processore, quindi deve risiedere in RAM.

  

L’ottimizzazione del tempo di CPU si ha con la multiprogrammazione (ossia la contemporanea presenza di più programmi in memoria). La gestione del sistema prevede:

 ● Scheduling dei job: insieme di strategie e meccanismi usati per la scelta dei programmi che dal disco devono essere caricati in RAM 

● Scheduling della CPU: insieme di strategie e meccanismi usati per assegnare e sospendere l’utilizzo della CPU da parte dei vari processi 

I SO multitasking aumentano il throughput “portando avanti” in parallelo più processi e riducendo al minimo l’inattività della CPU.

  

==**Processi**==

Un intero sistema o un insieme di processi che possono essere eseguiti in parallelo sui processori alternando nell’esecuzione.

  

*Ogni processo è costituito da due parti: 

● codice (composto dalle istruzioni); 

● dati del programma, a loro volta suddivisi in:

 – variabili globali, allocate nella RAM nell’area dati globali

 – variabili locali e non locali memorizzate in uno stack 

 – variabili temporanee introdotte dal compilatore (tra cui PC o IP) caricate nei registri del processore

 – variabili allocate dinamicamente durante l’esecuzione, memorizzate in un heap*.
 
E’ possibile avere in esecuzione contemporaneamente più istanze di un programma, ossia più processi originati dallo stesso codice. I processi possono essere:

● Indipendenti: un processo può evolvere autonomamente senza necessità di scambiare dati con altri processi 

● Cooperanti: due o più processi per evolvere necessitano di scambiarsi informazioni 

● Competitori: due processi possono ostacolarsi a vicenda, per usare la medesima risorsa, compromettendo la terminazione delle loro elaborazioni

Un programma può generare più processi, ma ogni processo è associato ad un solo programma.

==processo utente==: processo generato da un programma scritto dall’utente

==processo supervisore==: processo generato da un programma del SO( es. gestore dell attività) 

==i processi supervisori in esecuzione sulla cpu== (in background) hanno un’importanza maggiore rispetto ai processi utente.
quando un programma va in esecuzione viene creato il processo(memorizzato in memoria centrale)
PCB: strutture che contengono le informazioni relative allo stato del processore ovvero:

-PID(process identifier)

-indirizzo del descrittore di processo che lo ha generato(puntatore)

-la priorità

-lo stato di avanzamento

-immagine nella memoria

-informazioni relative alle altre risorse assegnate nel processo

un processo può avviarne altri(copie). questo processo viene chiamato”processo padre”, mentre i processi “copie” vengono chiamati “processi figli”

Ciclo di vita di un processo 

Mancano gli stati new ready running….

- Quando è creato un nuovo processo, gli viene assegnato un identificatore (PID, Process Identifier) e viene inserito nell’elenco dei processi pronti.
    
- Quando gli viene assegnata la CPU, il processo passa nello stato di esecuzione, dal quale può uscire per tre motivi: 
    

– termina la sua esecuzione, 

– termina il suo tempo di CPU, cioè il quanto di tempo a sua disposizione.

– gli manca la disponibilità di una risorsa: per poter evolvere necessita di una risorsa al momento non disponibile e quindi il processo si sospende e passa nello stato di attesa formando

-  Dallo stato di sospeso (in WL) un processo esce solo quando ottiene la risorsa attesa.
    

  

==Descrittore di processo==

  

Il SO per ogni processo deve mantenere delle informazioni, che istante per istante tengano traccia di cosa sta “facendo il processo”. L’insieme di queste informazioni è detto descrittore di processo

  

==GESTIONE MEMORIA SINTESI

Codice rilocabile:  
Quando un programma viene caricato in memoria, gli indirizzi relativi (logici) sono trasformati in indirizzi assoluti (fisici).

- Rilocazione statica: calcolo fatto al caricamento del programma, sommando l'indirizzo base agli offset.
    
- Rilocazione dinamica: durante l'esecuzione, ogni indirizzo logico è sommato al valore del registro base.
    

==MMU (Memory Management Unit):  ==
Dispositivo hardware che traduce indirizzi logici in fisici. Usa la formula:  
Indirizzo fisico = Indirizzo logico + Registro di rilocazione.

**Linking e Binding:

- Linking: calcola indirizzi logici.
    
- Binding: converte indirizzi logici in fisici:
    

- Durante la compilazione (indirizzi assoluti).
    
- Durante il caricamento (rilocazione statica).
    
- Durante l'esecuzione (rilocazione dinamica).
    

  

**Gestione della memoria:

- Per caricare un processo, la memoria deve avere spazio contiguo e sufficiente.
    
- Problemi:
    

- Programmi grandi che superano la RAM.
    
- Frammentazione dovuta al continuo caricamento e scaricamento di processi.
    
- Solo alcune istruzioni sono realmente eseguite.
    

**Soluzioni:

1. Swapping: spostare processi inattivi su disco (rallentamenti possibili).
    
2. Caricamento dinamico: caricare solo le parti del programma necessarie.
    
3. Overlay: frazionare il programma e caricare le parti in memoria alternandole.
    
4. Partizionamento: dividere la memoria in blocchi di dimensioni fisse o variabili.
    

**Partizioni fisse:

- Blocchi creati staticamente all'inizializzazione del sistema.
    
- Le partizioni possono essere di dimensioni diverse.
    
- Problemi:
    

- Frammentazione esterna: memoria totale sufficiente ma non contigua.
    
- Frammentazione interna: memoria sprecata quando processi piccoli occupano partizioni grandi.
    
- Soluzione: singola coda d'ingresso per assegnare i job.
    

**Partizioni variabili:

- Blocchi creati dinamicamente.
    
- Strategie di allocazione:
    

- First-fit: prima zona libera abbastanza grande.
    
- Best-fit: zona più piccola sufficiente, ma può lasciare zone inutilizzabili.
    
- Worst-fit: zona più grande.
    
- Next-fit: cerca da dove è avvenuta l’ultima allocazione.
    

  

==Memoria virtuale:  ==
Permette di ridurre la frammentazione, caricando in memoria centrale solo le parti del programma in uso.

**Paginazione:

- La memoria è divisa in frame (fisici) e pagine (logiche) della stessa dimensione.
    
- Page fault: avviene quando una pagina necessaria non è in memoria e il SO la carica dal disco.
    
- Ogni programma ha una tabella delle pagine che indica quali sono in RAM e quali su disco (bit di validità: 1 se in memoria, 0 altrimenti).
    

**Segmentazione:

- La memoria è divisa in segmenti di dimensioni variabili, associati a funzioni del programma (codice, dati, stack).
    
- Ogni segmento ha un indirizzo base e un limite.
    
- Segmentazione fault: avviene se un indirizzo supera il limite del segmento.  

**Segmentazione con paginazione:

- Combina i vantaggi di entrambe.
    
- Ogni segmento è suddiviso in pagine logiche, caricate in frame fisici senza frammentazione.
    
- Gli indirizzi logici hanno tre componenti: segmento, pagina, spiazzamento, tradotti in frame e spiazzamento fisico tramite MMU e tabelle.
    

Il context switching (o cambio di contesto) è un concetto fondamentale nella gestione dei processi di un sistema operativo multitasking. Si verifica quando la CPU sospende l’esecuzione di un processo per passare a un altro. Durante questo passaggio, lo stato del processo interrotto viene salvato, in modo che possa riprendere l’esecuzione esattamente da dove era stato interrotto in un momento successivo.

**