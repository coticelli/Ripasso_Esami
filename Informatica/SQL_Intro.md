# 🚀 Linguaggio SQL: Introduzione

**SQL (Structured Query Language)** è il linguaggio standard per la gestione e l'interrogazione dei database relazionali. Non è un linguaggio di programmazione completo, ma un linguaggio **dichiarativo**: si specifica *cosa* si vuole ottenere, non *come* ottenerlo.

---

## 🧩 Le 4 Sotto-lingue di SQL

Il linguaggio SQL è convenzionalmente suddiviso in quattro componenti principali:

### 1. **DDL (Data Definition Language)**
*   **Scopo:** Definire e gestire la **struttura** (lo schema) del database.
*   **Comandi principali:**
    *   **`CREATE`**: Crea nuovi oggetti nel database (tabelle, viste, indici).
        *   `CREATE TABLE Studenti (...)`
    *   **`ALTER`**: Modifica la struttura di un oggetto esistente (aggiunge/rimuove colonne, cambia tipi di dati).
        *   `ALTER TABLE Studenti ADD COLUMN Email VARCHAR(100);`
    *   **`DROP`**: Elimina definitivamente un oggetto dal database.
        *   `DROP TABLE Studenti;`

### 2. **DQL (Data Query Language)** o **Query Language**
*   **Scopo:** Interrogare il database per estrarre e leggere i dati.
*   **Comando principale:**
    *   **`SELECT`**: Seleziona i dati da una o più tabelle. È il comando più complesso e potente di SQL.
        *   `SELECT Nome, Cognome FROM Studenti WHERE Eta > 20;`

### 3. **DML (Data Manipulation Language)**
*   **Scopo:** Manipolare i **dati** contenuti nelle tabelle (inserire, aggiornare, cancellare).
*   **Comandi principali:**
    *   **`INSERT INTO`**: Aggiunge nuove righe (record) in una tabella.
        *   `INSERT INTO Studenti (Nome, Cognome) VALUES ('Mario', 'Rossi');`
    *   **`UPDATE`**: Modifica i dati nelle righe esistenti.
        *   `UPDATE Studenti SET Nome = 'Luigi' WHERE ID = 1;`
    *   **`DELETE FROM`**: Rimuove righe da una tabella.
        *   `DELETE FROM Studenti WHERE ID = 1;`

### 4. **DCL (Data Control Language)**
*   **Scopo:** Gestire i **permessi** e i diritti di accesso degli utenti al database.
*   **Comandi principali:**
    *   **`GRANT`**: Concede privilegi a un utente (es. permesso di leggere o scrivere su una tabella).
        *   `GRANT SELECT ON Studenti TO utente_prova;`
    *   **`REVOKE`**: Revoca i privilegi precedentemente concessi.
        *   `REVOKE SELECT ON Studenti FROM utente_prova;`
