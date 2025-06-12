# 🔎 SQL: Query Avanzate e Aggregazione

Le query `SELECT` possono diventare molto complesse, combinando dati da più tabelle, utilizzando subquery e raggruppando i risultati con funzioni di aggregazione.

---

## 🎯 Subquery (o Query Annidate)

Una **subquery** è una query `SELECT` inserita all'interno di un'altra query SQL. Può essere usata in diverse clausole.

### 1. Subquery nella Clausola `WHERE`
*   **Scopo:** Filtrare i risultati della query principale basandosi sull'output della subquery. La subquery restituisce un singolo valore o un insieme di valori.
*   **Esempio:** Trovare tutti gli studenti che hanno un'età superiore alla media.
    ```sql
    SELECT Nome, Cognome
    FROM Studenti
    WHERE Eta > (SELECT AVG(Eta) FROM Studenti);
    ```
*   **Operatori comuni:** `IN`, `NOT IN`, `ANY`, `ALL`.
    *   **`IN`**: Verifica se un valore è presente nell'insieme di risultati della subquery.
    ```sql
    SELECT * FROM Ordini WHERE ID_Cliente IN (SELECT ID FROM Clienti WHERE Citta = 'Milano');
    ```

### 2. Subquery nella Clausola `FROM`
*   **Scopo:** Utilizzare il risultato di una subquery come se fosse una tabella temporanea (chiamata **derived table**) su cui la query principale può operare.
*   **Requisito:** La subquery deve avere un **alias** (un nome temporaneo).
*   **Esempio:** Selezionare i nomi dei clienti e il numero totale dei loro ordini.
    ```sql
    SELECT C.Nome, T.ConteggioOrdini
    FROM Clienti AS C
    JOIN (
        SELECT ID_Cliente, COUNT(*) AS ConteggioOrdini
        FROM Ordini
        GROUP BY ID_Cliente
    ) AS T ON C.ID = T.ID_Cliente;
    ```

---

## 📊 Funzioni di Aggregazione e Raggruppamento

Le **funzioni di aggregazione** eseguono un calcolo su un insieme di valori e restituiscono un singolo valore di riepilogo.

*   **`COUNT(*)`**: Conta il numero totale di righe.
*   **`COUNT(colonna)`**: Conta il numero di valori non-NULL in una colonna.
*   **`SUM(colonna)`**: Somma i valori di una colonna numerica.
*   **`AVG(colonna)`**: Calcola la media dei valori di una colonna numerica.
*   **`MIN(colonna)`**: Trova il valore minimo in una colonna.
*   **`MAX(colonna)`**: Trova il valore massimo in una colonna.

---

## 👥 Clausole `GROUP BY` e `HAVING`

### `GROUP BY`
*   **Scopo:** Raggruppa le righe che hanno gli stessi valori in colonne specificate, permettendo di applicare le funzioni di aggregazione a ogni gruppo.
*   **Esempio:** Contare quanti studenti ci sono in ogni città.
    ```sql
    SELECT Citta, COUNT(*) AS NumeroStudenti
    FROM Studenti
    GROUP BY Citta;
    ```

### `HAVING`
*   **Scopo:** Filtrare i risultati **dopo** che sono stati raggruppati con `GROUP BY`. `HAVING` lavora sui risultati delle funzioni di aggregazione.
*   **Differenza con `WHERE`:** `WHERE` filtra le righe *prima* del raggruppamento, `HAVING` filtra i gruppi *dopo*.
*   **Esempio:** Mostrare solo le città che hanno più di 10 studenti.
    ```sql
    SELECT Citta, COUNT(*) AS NumeroStudenti
    FROM Studenti
    GROUP BY Citta
    HAVING COUNT(*) > 10;
    ```

**Ordine logico di esecuzione in una query `SELECT`:**
1. `FROM` e `JOIN`
2. `WHERE`
3. `GROUP BY`
4. `HAVING`
5. `SELECT`
6. `ORDER BY`
