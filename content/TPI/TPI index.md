# Riassunto: Sistema Operativo

## **Cos'è il Sistema Operativo**
Il Sistema Operativo (SO) è parte del **software di base**, un insieme di programmi che permette l'uso del calcolatore. È composto da:
- SO
- Editor
- Compilatori
- [[Linker]]
- Loader: carica programmi in RAM
- Debugger

## **Funzioni principali del SO**

### **1. Gestione delle risorse hardware**
- Supervisiona scrittura/lettura dei dischi.
- Gestisce I/O e l'esecuzione di programmi caricando istruzioni e dati in RAM.

### **2. Interfaccia con l'utente**
- Fornisce supporto tramite interfacce:
  - [Grafica (GUI)](https://it.wikipedia.org/wiki/Interfaccia_grafica)
  - Linea di comando (CUI)

## **Architettura del SO (Cipolla)**

### **Kernel**
Il kernel è il cuore del SO e:
- Permette l’interazione HW-SW.
- È l'unico con accesso diretto all'hardware.
- Gestisce le risorse hardware e i driver principali.
- Media e trasmette i comandi.

### **Funzioni del Kernel**
- **Gestione memoria:** controlla utilizzo RAM.
- **Gestione processi:** decide quali processi possono usare la CPU.
- **Interazione con i driver:** media tra hardware e processi.
- **Chiamate di sistema:** accetta richieste dai processi tramite la shell (GUI o CUI).

---

## **Gestione del processore**
I SO moderni sfruttano il parallelismo hardware per:
- Ridurre i tempi di risposta.
- Aumentare il throughput (processi/unità di tempo).

### **Definizioni**
- **Programma:** insieme di istruzioni in memoria di massa.
- **[[Processi]] (task):** istanza di un programma in esecuzione (risiede in RAM).

### **Ottimizzazioni**
- **Multiprogrammazione:** più programmi in memoria.
- **Scheduling dei job:** scelta dei programmi da caricare in RAM.
- **Scheduling della CPU:** gestione dell'uso della CPU.

---

## **[[Processi]]**

### **Caratteristiche**
Ogni processo è composto da:
- **Codice:** istruzioni del programma.
- **Dati:** variabili globali, locali, temporanee (in registri), e allocate dinamicamente (heap).

### **Tipologie di processi**
- **Indipendenti:** evolvono senza interazioni.
- **Cooperanti:** richiedono scambio di informazioni.
- **Competitori:** competono per le risorse.

### **Distinzioni**
- **Processo utente:** generato da programmi scritti dall’utente.
- **Processo supervisore:** generato dal SO (es. gestione attività).

### **PCB (Process Control Block)**
Ogni processo ha un PCB con:
- PID (Process Identifier)
- Priorità e stato di avanzamento
- Indirizzo del descrittore
- Risorse assegnate

### **Ciclo di vita**
1. **Creazione:** assegnazione PID e inserimento in elenco processi pronti.
2. **Esecuzione:** uso della CPU; può terminare o sospendersi per risorse mancanti.
3. **Attesa:** il processo riprende quando la risorsa è disponibile.

---

## **[[Gestione della memoria]]**

### **Codice rilocabile**
- **Rilocazione statica:** indirizzi calcolati al caricamento.
- **Rilocazione dinamica:** calcolo durante l'esecuzione tramite il registro base.

### **MMU (Memory Management Unit)**
- Traduzione indirizzi logici in fisici:  
  **Indirizzo fisico = Indirizzo logico + Registro di rilocazione**

### **Linking e Binding**
- **Linking:** calcola indirizzi logici.
- **Binding:** trasforma indirizzi logici in fisici:
  - Durante compilazione.
  - Durante caricamento.
  - Durante esecuzione (rilocazione dinamica).

---

### **Problemi e Soluzioni**
1. **Problemi:**
   - Programmi troppo grandi per la RAM.
   - Frammentazione interna ed esterna.

2. **Soluzioni:**
   - **Swapping:** spostamento processi inattivi su disco.
   - **Caricamento dinamico:** caricare solo le parti necessarie.
   - **Overlay:** caricamento alternato di porzioni di programma.
   - **Partizionamento:** memoria suddivisa in blocchi.

---

### **Memoria virtuale**
Permette di caricare solo le parti del programma necessarie.

#### **[[Paginazione]]**
- Memoria divisa in frame (fisici) e pagine (logiche).
- **Page fault:** avviene quando una pagina non è in RAM e viene caricata dal disco.

#### **Segmentazione**
- Memoria divisa in segmenti variabili.
- **Segmentazione fault:** avviene se un indirizzo supera i limiti del segmento.

#### **Segmentazione con paginazione**
Combina vantaggi di entrambi, riducendo frammentazione:
- Indirizzi logici tradotti in componenti fisici (segmento, pagina, spiazzamento).

---

## **Context Switching**
Cambio di contesto tra processi multitasking:
- Stato del processo interrotto salvato per riprendere successivamente.
