# ⚡ Le Transazioni e le Proprietà ACID

Nei sistemi di database (DBMS), una **transazione** è una sequenza di una o più operazioni (come letture, scritture, aggiornamenti, cancellazioni) che vengono eseguite come un'**unica unità logica di lavoro**.

L'obiettivo di una transazione è garantire che il database passi da uno stato consistente a un altro stato consistente, anche in caso di errori o accessi concorrenti.

**Esempio classico:** Un bonifico bancario. La transazione consiste in due operazioni:
1.  Sottrarre 100€ dal conto A.
2.  Aggiungere 100€ al conto B.

Queste due operazioni devono avvenire **insieme**, come un blocco atomico. O entrambe hanno successo, o entrambe falliscono.

---

## 🔥 Le Proprietà ACID

Per garantire l'integrità e l'affidabilità dei dati, ogni transazione deve rispettare quattro proprietà fondamentali, note con l'acronimo **ACID**.

### 1. **A** - Atomicità (Atomicity)
*   **Concetto:** "Tutto o niente".
*   **Significato:** Una transazione è un'unità indivisibile. O tutte le operazioni che la compongono vengono eseguite con successo e rese permanenti (**COMMIT**), oppure, in caso di fallimento di una qualsiasi operazione, tutte le modifiche precedenti vengono annullate, riportando il database allo stato iniziale (**ROLLBACK**).
*   **Esempio:** Nel bonifico, se l'accredito sul conto B fallisce, anche l'addebito sul conto A deve essere annullato. Non è possibile che il denaro "sparisca".

### 2. **C** - Consistenza (Consistency)
*   **Concetto:** La transazione porta il database da uno stato valido a un altro stato valido.
*   **Significato:** Ogni transazione deve rispettare tutti i vincoli di integrità del database (es. chiavi primarie, chiavi esterne, vincoli di unicità, tipi di dati). Una transazione che viola un vincolo non può essere completata con successo.
*   **Esempio:** Non è possibile trasferire più denaro di quello disponibile sul conto (violerebbe un vincolo di `saldo ≥ 0`).

### 3. **I** - Isolamento (Isolation)
*   **Concetto:** Transazioni concorrenti non devono interferire tra loro.
*   **Significato:** Se più transazioni vengono eseguite contemporaneamente, i loro effetti devono essere gli stessi che si otterrebbero se venissero eseguite una dopo l'altra (in sequenza). Ogni transazione opera in un "ambiente isolato", ignara delle altre.
*   **Esempio:** Se due persone tentano di acquistare l'ultimo biglietto disponibile per un concerto contemporaneamente, solo una delle due transazioni deve avere successo. L'isolamento impedisce che entrambe le transazioni vedano il biglietto come disponibile.

### 4. **D** - Durabilità (Durability)
*   **Concetto:** Una volta che una transazione è stata completata con successo (COMMIT), le sue modifiche sono permanenti e definitive.
*   **Significato:** Le modifiche devono sopravvivere a qualsiasi successivo malfunzionamento del sistema (es. crash del software, riavvio del server). Il DBMS garantisce che i dati siano stati scritti in modo permanente su un supporto di memorizzazione non volatile (come un hard disk).

---

## 📝 Comandi SQL per le Transazioni

I comandi principali per gestire le transazioni in SQL sono:

*   **`BEGIN TRANSACTION`** (o `START TRANSACTION`): Inizia una nuova transazione.
*   **`COMMIT`**: Rende definitive e permanenti tutte le modifiche fatte dall'inizio della transazione.
*   **`ROLLBACK`**: Annulla tutte le modifiche fatte dall'inizio della transazione, riportando il database allo stato precedente.

```sql
BEGIN TRANSACTION;

-- Addebita 100 dal conto con ID 1
UPDATE Conti SET Saldo = Saldo - 100 WHERE ID_Conto = 1;

-- Accredita 100 sul conto con ID 2
UPDATE Conti SET Saldo = Saldo + 100 WHERE ID_Conto = 2;

-- Se tutto è andato bene, conferma le modifiche
COMMIT;

-- In caso di errore (gestito da un blocco TRY...CATCH o simile), si eseguirebbe:
-- ROLLBACK;
