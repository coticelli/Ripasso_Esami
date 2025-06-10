# 🔄 Tecniche ORM (Object-Relational Mapping)

Un **ORM (Object-Relational Mapper)** è una tecnica di programmazione che funge da "traduttore" automatico tra il mondo a **oggetti** della tua applicazione (es. classi C#) e il mondo **relazionale** del tuo database (tabelle SQL).

---

## 🎯 Il Problema che Risolve l'ORM

Senza un ORM, per salvare un oggetto `Studente` nel database, un programmatore dovrebbe scrivere manualmente codice SQL come:
`INSERT INTO Studenti (Nome, Cognome, DataNascita) VALUES ('Mario', 'Rossi', '2005-10-20');`
Questo processo è:
*   **Ripetitivo:** Va fatto per ogni operazione CRUD (Create, Read, Update, Delete) e per ogni classe.
*   **Soggetto a errori:** È facile commettere errori di sintassi SQL.
*   **Vulnerabile:** Può esporre a rischi di sicurezza come la **SQL Injection** se non gestito correttamente.
*   **Legato al database:** Cambiare tipo di database (es. da SQL Server a SQLite) richiede di riscrivere le query.

---

## 🌉 Come Funziona un ORM

Un ORM automatizza tutto questo. Il programmatore interagisce solo con oggetti e metodi del suo linguaggio di programmazione, e l'ORM si occupa della traduzione.

1.  **Mapping (Mappatura):** Si definisce una corrispondenza tra le classi del programma e le tabelle del database.
    *   Classe `Studente` → Tabella `Studenti`
    *   Proprietà `Nome` → Colonna `Nome`

2.  **Astrazione:** L'ORM fornisce un oggetto speciale (spesso chiamato `DbContext` o `Session`) che rappresenta la connessione al database.

3.  **Interazione:** Il programmatore usa semplici metodi su questo oggetto per manipolare i dati.

### Esempio con Entity Framework Core (l'ORM di Microsoft)

**Invece di scrivere SQL:**
```sql
UPDATE Studenti SET Cognome = 'Verdi' WHERE Matricola = 123;
Use code with caution.
Si scrive codice C#:
// 1. Trova lo studente da modificare
var studente = context.Studenti.Find(123);

if (studente != null)
{
    // 2. Modifica la proprietà dell'oggetto
    studente.Cognome = "Verdi";

    // 3. Salva le modifiche (EF Core genera ed esegue l'SQL per te)
    context.SaveChanges();
}
```
✨ Vantaggi Principali di un ORM
✅ Produttività: Si scrive molto meno codice, accelerando lo sviluppo.
✅ Manutenibilità: Il codice è più pulito, più leggibile e più facile da mantenere.
✅ Indipendenza dal Database: È più facile cambiare il sistema di database sottostante senza modificare il codice dell'applicazione.
✅ Sicurezza: Molti ORM gestiscono automaticamente la parametrizzazione delle query, proteggendo da attacchi di SQL Injection.
Entity Framework (EF) Core è l'ORM standard e raccomandato per lo sviluppo di applicazioni .NET.
