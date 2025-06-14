# 🌊 Modelli Classici di Sviluppo

I modelli classici di sviluppo software, noti anche come modelli a cascata o predittivi, sono caratterizzati da un approccio **sequenziale e lineare**. Le fasi del progetto vengono eseguite una dopo l'altra, e ogni fase deve essere completata prima di poter iniziare la successiva.

---

## 1. Modello a Cascata (Waterfall Model)

È il più antico e famoso dei modelli classici. Il suo nome deriva dal fatto che il flusso del progetto "scorre" verso il basso come l'acqua di una cascata.

### Le Fasi della Cascata
1.  **Requisiti (Requirements):**
    *   Raccolta e analisi completa di tutti i requisiti del software. Questa fase si chiude con un documento "congelato".
2.  **Progettazione (Design):**
    *   Progettazione dell'architettura del software e del database, basandosi sui requisiti definiti.
3.  **Implementazione (Implementation / Coding):**
    *   Scrittura del codice sorgente.
4.  **Test (Verification / Testing):**
    *   Verifica completa del software per trovare e correggere i bug.
5.  **Installazione (Deployment):**
    *   Rilascio del software in produzione.
6.  **Manutenzione (Maintenance):**
    *   Correzione di bug e aggiunta di piccole migliorie dopo il rilascio.

### Vantaggi e Svantaggi
*   **Vantaggi 👍:**
    *   **Semplice** da capire e da gestire.
    *   **Rigido e disciplinato:** Ogni fase ha deliverable e scadenze chiare.
    *   **Documentazione** completa.
*   **Svantaggi 👎:**
    *   **Pochissima flessibilità:** È molto difficile e costoso tornare indietro per modificare i requisiti una volta che una fase è stata approvata.
    *   **Feedback tardivo:** Il cliente vede il prodotto funzionante solo alla fine del processo.
    *   **Rischio elevato:** Se i requisiti iniziali sono sbagliati o incompleti, l'intero progetto è a rischio.

**Quando usarlo?** È adatto solo per progetti molto piccoli, semplici e con requisiti estremamente chiari e stabili fin dall'inizio.

---

## 2. Modello a V (V-Model)

Il Modello a V è una variante del modello a cascata che mette in evidenza la relazione tra ogni fase di sviluppo e la sua corrispondente fase di test.

### La Struttura a V
*   **Lato Sinistro (Discesa - Verification):** Contiene le fasi di sviluppo, come nel modello a cascata.
    *   Analisi dei Requisiti
    *   Progettazione del Sistema
    *   Progettazione dell'Architettura
    *   Progettazione dei Moduli
*   **Base (Punta della V):**
    *   Codifica (Coding)
*   **Lato Destro (Salita - Validation):** Contiene le fasi di test. Ogni livello di test valida il livello di progettazione corrispondente.
    *   **Unit Testing:** Testa i singoli moduli (corrisponde alla Progettazione dei Moduli).
    *   **Integration Testing:** Testa come i moduli interagiscono tra loro (corrisponde alla Progettazione dell'Architettura).
    *   **System Testing:** Testa l'intero sistema rispetto ai requisiti di sistema (corrisponde alla Progettazione del Sistema).
    *   **Acceptance Testing:** Test di accettazione da parte dell'utente (corrisponde all'Analisi dei Requisiti).

Il vantaggio principale del Modello a V è che **la pianificazione dei test inizia fin dalle prime fasi del progetto**, migliorando la qualità del prodotto finale. Tuttavia, mantiene la stessa rigidità e sequenzialità del modello a cascata.
