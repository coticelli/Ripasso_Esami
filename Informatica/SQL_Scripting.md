# 📜 Scripting SQL: Viste, Stored Procedure e Trigger

Oltre alle query interattive, SQL permette di creare oggetti programmabili memorizzati direttamente nel database per automatizzare compiti, semplificare operazioni complesse e migliorare la sicurezza.

---

## 1. Viste (Views)

*   **Cos'è:** Una **vista** è una tabella virtuale basata sul risultato di una query `SELECT`. Non contiene dati propri, ma li mostra dinamicamente prelevandoli dalle tabelle sottostanti ogni volta che viene interrogata.
*   **Scopo:**
    *   **Semplificazione:** Nascondere la complessità di query con molti join.
    *   **Sicurezza:** Limitare l'accesso degli utenti solo a determinate colonne o righe di una tabella.
    *   **Indipendenza logica:** Se la struttura delle tabelle sottostanti cambia, si può modificare la vista senza dover cambiare le applicazioni che la usano.

*   **Sintassi per la creazione:**
    ```sql
    CREATE VIEW VistaClientiMilano AS
    SELECT Nome, Cognome, Email
    FROM Clienti
    WHERE Citta = 'Milano';
    ```

*   **Come si usa:** Una volta creata, una vista può essere interrogata come una normale tabella:
    `SELECT * FROM VistaClientiMilano;`

---

## 2. Stored Procedure

*   **Cos'è:** Una **stored procedure** è un insieme di uno o più comandi SQL precompilati e memorizzati nel database, che possono essere eseguiti con un singolo comando. Può accettare parametri in input e restituire valori in output.
*   **Scopo:**
    *   **Efficienza:** Essendo precompilata, l'esecuzione è più veloce.
    *   **Riusabilità:** Si scrive una volta e si richiama più volte da diverse applicazioni.
    *   **Sicurezza:** Si possono concedere a un utente i permessi per eseguire una stored procedure senza dargli accesso diretto alle tabelle sottostanti.
    *   **Manutenibilità:** La logica di business è centralizzata nel database, rendendo più facili gli aggiornamenti.

*   **Sintassi (esempio in T-SQL per SQL Server):**
    ```sql
    CREATE PROCEDURE InserisciNuovoStudente
        @Matricola VARCHAR(10),
        @Nome VARCHAR(50),
        @Cognome VARCHAR(50)
    AS
    BEGIN
        INSERT INTO Studenti (Matricola, Nome, Cognome)
        VALUES (@Matricola, @Nome, @Cognome);
    END;
    ```
*   **Come si esegue:**
    `EXEC InserisciNuovoStudente 'S54321', 'Anna', 'Verdi';`

---

## 3. Trigger

*   **Cos'è:** Un **trigger** è un tipo speciale di stored procedure che viene eseguita **automaticamente** dal DBMS in risposta a un determinato evento di modifica dei dati (un `INSERT`, `UPDATE` o `DELETE`) su una specifica tabella.
*   **Scopo:**
    *   **Mantenere l'integrità referenziale complessa:** Eseguire controlli che non possono essere definiti con i vincoli standard.
    *   **Auditing e Logging:** Registrare automaticamente le modifiche apportate ai dati (chi ha modificato cosa e quando).
    *   **Automatizzare azioni a cascata:** Es. Quando viene aggiornato un prodotto, aggiornare automaticamente i prezzi negli ordini aperti.

*   **Sintassi (esempio concettuale):**
    ```sql
    CREATE TRIGGER LogAggiornamentoStipendio
    ON Impiegati
    AFTER UPDATE
    AS
    BEGIN
        -- Logica per inserire un record in una tabella di log
        -- quando lo stipendio di un impiegato viene modificato.
    END;
    ```
*   **Attenzione:** I trigger sono potenti ma possono rendere il comportamento del database difficile da comprendere e debuggare. Vanno usati con cautela.
