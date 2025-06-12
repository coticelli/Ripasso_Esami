# 🏗️ SQL: Manipolazione Schema (DDL) e Dati (DML)

Questa sezione copre i comandi SQL fondamentali per creare e modificare la struttura del database (`DDL`) e per inserire, aggiornare e cancellare i dati al suo interno (`DML`).

---

## 🏛️ DDL (Data Definition Language)

I comandi DDL definiscono lo schema del database. Le loro modifiche sono solitamente permanenti e non possono essere annullate con un `ROLLBACK`.

### 1. `CREATE TABLE`
*   **Scopo:** Creare una nuova tabella nel database.
*   **Sintassi:** Si specificano il nome della tabella, i nomi delle colonne, i loro tipi di dato e i vincoli.
*   **Esempio:**
    ```sql
    CREATE TABLE Studenti (
        ID_Studente INT PRIMARY KEY,
        Matricola VARCHAR(10) UNIQUE NOT NULL,
        Nome VARCHAR(50),
        Cognome VARCHAR(50),
        DataNascita DATE,
        ID_CorsoLaurea INT,
        FOREIGN KEY (ID_CorsoLaurea) REFERENCES CorsiLaurea(ID)
    );
    ```
    *   **`PRIMARY KEY`**: Vincolo di chiave primaria.
    *   **`UNIQUE`**: Assicura che tutti i valori nella colonna siano unici.
    *   **`NOT NULL`**: Impedisce l'inserimento di valori nulli.
    *   **`FOREIGN KEY`**: Crea una relazione con un'altra tabella.

### 2. `ALTER TABLE`
*   **Scopo:** Modificare la struttura di una tabella esistente.
*   **Sintassi e Esempi:**
    *   **Aggiungere una colonna:**
        `ALTER TABLE Studenti ADD COLUMN Email VARCHAR(100);`
    *   **Rimuovere una colonna:**
        `ALTER TABLE Studenti DROP COLUMN DataNascita;`
    *   **Modificare il tipo di dato di una colonna:**
        `ALTER TABLE Studenti MODIFY COLUMN Nome VARCHAR(70);` (Sintassi può variare tra DBMS)

### 3. `DROP TABLE`
*   **Scopo:** Eliminare definitivamente una tabella, inclusi tutti i suoi dati e indici.
*   **Attenzione:** È un'operazione irreversibile!
*   **Sintassi:**
    `DROP TABLE Studenti;`

---

## ✏️ DML (Data Manipulation Language)

I comandi DML agiscono sui dati contenuti nelle tabelle. Queste operazioni fanno parte delle transazioni e possono essere annullate.

### 1. `INSERT INTO`
*   **Scopo:** Aggiungere una o più nuove righe a una tabella.
*   **Sintassi (inserimento di una riga):**
    ```sql
    INSERT INTO Studenti (Matricola, Nome, Cognome)
    VALUES ('S12345', 'Mario', 'Rossi');
    ```
    (Se si specificano valori per tutte le colonne nell'ordine corretto, si può omettere la lista delle colonne).

### 2. `UPDATE`
*   **Scopo:** Modificare i valori in una o più righe esistenti.
*   **Attenzione:** Usare sempre una clausola `WHERE` per specificare quali righe modificare, altrimenti verranno aggiornate **tutte** le righe della tabella!
*   **Sintassi:**
    ```sql
    UPDATE Studenti
    SET Email = 'mario.rossi@example.com'
    WHERE ID_Studente = 1;
    ```

### 3. `DELETE FROM`
*   **Scopo:** Rimuovere una o più righe da una tabella.
*   **Attenzione:** Come per `UPDATE`, usare sempre una clausola `WHERE` per evitare di cancellare tutti i dati.
*   **Sintassi:**
    ```sql
    DELETE FROM Studenti
    WHERE ID_Studente = 1;
    ```
    Per cancellare tutte le righe, si usa `DELETE FROM Studenti;`. Per tabelle molto grandi, `TRUNCATE TABLE Studenti;` è più veloce ma non può essere annullato.
