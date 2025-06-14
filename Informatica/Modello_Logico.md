# 🗂️ Modello Logico Relazionale

Il **modello logico relazionale** è il passo successivo alla progettazione concettuale (Modello ER). Il suo obiettivo è tradurre lo schema ER, che è astratto, in una struttura logica implementabile da un **database relazionale (RDBMS)**.

La struttura fondamentale del modello relazionale è la **tabella** (o relazione).

---

## 📖 Regole di Traduzione da ER a Logico Relazionale

Esiste un insieme di regole precise per convertire uno schema ER in uno schema di tabelle, colonne e chiavi.

### 1. **Traduzione delle Entità**
*   **Regola:** Ogni entità dello schema ER diventa una **tabella** (relazione) nello schema logico.
*   **Colonne:** Gli attributi dell'entità diventano le **colonne** (attributi) della tabella.
*   **Chiave Primaria (Primary Key - PK):** L'attributo chiave dell'entità diventa la **chiave primaria** della tabella. La chiave primaria identifica univocamente ogni riga (record) della tabella.

**Esempio:**
*   **Entità ER:** `STUDENTE` con attributi `(Matricola, Nome, Cognome)`.
*   **Tabella Relazionale:** `STUDENTI (Matricola PK, Nome, Cognome)`.

---

## 2. **Traduzione delle Relazioni**

La traduzione di una relazione dipende dalla sua cardinalità.

### A. Relazione **Uno a Molti (1:N)**
*   **Regola:** La relazione **NON** diventa una tabella. Per rappresentare il legame, si aggiunge una **chiave esterna (Foreign Key - FK)** nella tabella sul lato "molti".
*   **Come funziona:** La chiave primaria della tabella sul lato "uno" viene copiata come una nuova colonna (la FK) nella tabella sul lato "molti". Questa colonna crea il collegamento.

**Esempio:**
*   `PROFESSORE(ID_Professore PK, ...)`  **(lato 1)**
*   `CORSO(ID_Corso PK, Nome, ...)` **(lato N)**
*   **Relazione (1:N):** `PROFESSORE` insegna in `CORSO`.
*   **Traduzione:**
    `CORSI(ID_Corso PK, Nome, ..., **ID_Professore_FK**)`
    La colonna `ID_Professore_FK` in `CORSI` si riferisce alla chiave primaria della tabella `PROFESSORI`.

### B. Relazione **Molti a Molti (N:M)**
*   **Regola:** La relazione **DEVE** diventare una nuova tabella, chiamata **tabella di associazione** (o tabella ponte).
*   **Come funziona:** Questa nuova tabella ha come colonne le chiavi primarie delle due entità che mette in relazione. La chiave primaria di questa tabella di associazione è solitamente la **coppia** delle due chiavi esterne.

**Esempio:**
*   `STUDENTE(Matricola PK, ...)`
*   `CORSO(ID_Corso PK, ...)`
*   **Relazione (N:M):** `STUDENTE` frequenta `CORSO`.
*   **Traduzione:** Viene creata una nuova tabella `ISCRIZIONI`.
    `ISCRIZIONI(**Matricola_FK, ID_Corso_FK**)`
    La chiave primaria di `ISCRIZIONI` è `(Matricola_FK, ID_Corso_FK)`.

### C. Relazione **Uno a Uno (1:1)**
*   **Regola:** Simile al caso 1:N. Si può scegliere di mettere la chiave esterna in una delle due tabelle. Generalmente, si sceglie la tabella che partecipa "opzionalmente" alla relazione.

Questo processo di traduzione garantisce la coerenza e l'integrità dei dati, eliminando le ridondanze. Il risultato è uno schema pronto per essere implementato in un DBMS.
