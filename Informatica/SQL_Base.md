# 🔎 Elementi Base del Linguaggio SQL

**SQL (Structured Query Language)** è il linguaggio standard per interagire con i database relazionali. Permette di creare, modificare e interrogare i dati contenuti nelle tabelle.

SQL si divide principalmente in due sottolinguaggi:
*   **DDL (Data Definition Language):** Per definire la struttura del database (creare/modificare/eliminare tabelle).
*   **DML (Data Manipulation Language):** Per manipolare i dati (inserire, aggiornare, cancellare e interrogare).

---

## 🎯 DML: Le Quattro Operazioni Fondamentali (CRUD)

Le operazioni **CRUD (Create, Read, Update, Delete)** sono il cuore del DML.

### 1. **SELECT (Read - Leggere i dati)**
È il comando più usato. Serve a estrarre dati da una o più tabelle.

**Sintassi di base:**
```sql
SELECT Colonne
FROM Tabella
WHERE Condizione;
```
*   `SELECT *`: Seleziona **tutte** le colonne.
*   `WHERE`: **Filtra** le righe in base a una condizione (es. `WHERE Eta > 18`).
*   `ORDER BY`: **Ordina** i risultati (es. `ORDER BY Cognome ASC`).

**Join per interrogare più tabelle:**
Per combinare dati da due tabelle correlate (es. `STUDENTI` e `CORSI`), si usa una clausola `JOIN`.
```sql
SELECT S.Nome, C.NomeCorso
FROM STUDENTI S
JOIN ISCRIZIONI I ON S.Matricola = I.Matricola_FK
JOIN CORSI C ON I.ID_Corso_FK = C.ID_Corso;
```
---

### 2. **INSERT (Create - Inserire nuovi dati)**
Aggiunge una nuova riga (record) in una tabella.

**Sintassi:**
```sql
INSERT INTO Tabella (Colonna1, Colonna2, Colonna3)
VALUES (Valore1, Valore2, Valore3);
```
---

### 3. **UPDATE (Update - Modificare dati esistenti)**
Modifica una o più righe esistenti in una tabella.

**Sintassi:**
```sql
UPDATE Tabella
SET Colonna1 = NuovoValore1, Colonna2 = NuovoValore2
WHERE Condizione;
```
**⚠️ Attenzione!** La clausola `WHERE` è **fondamentale**. Se viene omessa, l'aggiornamento verrà applicato a **TUTTE** le righe della tabella.
---

### 4. **DELETE (Delete - Cancellare dati)**
Rimuove una o più righe da una tabella.

**Sintassi:**
```sql
DELETE FROM Tabella
WHERE Condizione;
```
**⚠️ Attenzione!** Anche qui, omettere la clausola `WHERE` causerà la cancellazione di **TUTTE** le righe della tabella.
---

## 🏗️ DDL: Definire la Struttura

Il DDL serve per creare e gestire gli oggetti del database.

*   **`CREATE TABLE`**: Crea una nuova tabella, specificando i nomi e i tipi di dato delle colonne.
    ```sql
    CREATE TABLE STUDENTI (
        Matricola INT PRIMARY KEY,
        Nome VARCHAR(50) NOT NULL,
        Cognome VARCHAR(50) NOT NULL,
        DataNascita DATE
    );
    ```
*   **`ALTER TABLE`**: Modifica la struttura di una tabella esistente (aggiungendo/rimuovendo colonne).
*   **`DROP TABLE`**: Elimina permanentemente una tabella e tutti i suoi dati.
```
