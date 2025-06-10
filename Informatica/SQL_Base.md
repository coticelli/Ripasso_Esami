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
