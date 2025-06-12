#  layered models

Le architetture di rete a strati (o livelli) sono modelli concettuali che suddividono il complesso processo di comunicazione di rete in una serie di **livelli (layers)** più piccoli e gestibili. Ogni livello ha un compito specifico e offre servizi al livello superiore, nascondendo i dettagli di come questi servizi vengono implementati.

---

## 🤔 Perché Usare i Livelli?

*   **Modularità:** Suddividere il problema in parti più piccole lo rende più facile da capire e sviluppare.
*   **Interoperabilità:** Standardizzare le funzioni di ogni livello permette a dispositivi di produttori diversi di comunicare tra loro.
*   **Astrazione:** Un livello non ha bisogno di conoscere i dettagli implementativi dei livelli sottostanti, ma solo i servizi che offrono.
*   **Semplificazione della Manutenzione:** Si può modificare l'implementazione di un livello senza dover cambiare gli altri.

---

## 🏛️ I Modelli di Riferimento: ISO/OSI e TCP/IP

### Modello ISO/OSI (Open Systems Interconnection)
È un modello teorico di riferimento composto da **7 livelli**. È fondamentale per la comprensione dei concetti di rete, anche se non è implementato alla lettera.
1.  **Fisico:** Trasmissione dei bit sul mezzo fisico (cavi, onde radio).
2.  **Data Link:** Gestisce l'accesso al mezzo e il framing dei dati, indirizzamento fisico (MAC).
3.  **Rete:** Instradamento dei pacchetti attraverso la rete (routing), indirizzamento logico (IP).
4.  **Trasporto:** Fornisce una comunicazione affidabile end-to-end (TCP) o non affidabile (UDP).
5.  **Sessione:** Gestisce l'apertura, la chiusura e la sincronizzazione delle sessioni tra host.
6.  **Presentazione:** Formattazione, crittografia e compressione dei dati.
7.  **Applicazione:** Fornisce l'interfaccia per le applicazioni utente (HTTP, FTP, SMTP).

### Modello TCP/IP
È il modello pratico su cui si basa Internet. È più semplice e raggruppa le funzioni in **4 o 5 livelli**.

| Modello ISO/OSI      | Modello TCP/IP (comune) |
| -------------------- | ----------------------- |
| 7. Applicazione      | \multirow{3}{*}{**Applicazione**} |
| 6. Presentazione     |                         |
| 5. Sessione          |                         |
| 4. Trasporto         | **Trasporto**           |
| 3. Rete              | **Internet (o Rete)**   |
| 2. Data Link         | \multirow{2}{*}{**Accesso alla Rete**} |
| 1. Fisico            |                         |

---

## 📦 Incapsulamento e Decapsulamento

È il processo fondamentale della comunicazione a strati.
*   **Incapsulamento (in trasmissione):** Mentre i dati scendono lungo lo stack, ogni livello aggiunge le proprie informazioni di controllo (**header**). L'unità di dati di ogni livello (PDU - Protocol Data Unit) viene "incapsulata" nel payload del livello sottostante.
    *   Dati → **Segmento** (Trasporto) → **Pacchetto** (Rete) → **Frame** (Data Link) → Bit (Fisico)
*   **Decapsulamento (in ricezione):** Il processo inverso. Mentre i dati salgono lo stack, ogni livello legge e rimuove il proprio header, passando i dati al livello superiore.
