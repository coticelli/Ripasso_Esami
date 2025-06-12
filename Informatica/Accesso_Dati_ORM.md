# 💾 Accesso ai Dati: Entity Framework (ORM) e Dapper (Micro-ORM)

Nelle applicazioni web moderne, la logica di accesso ai dati è fondamentale. Gli strumenti **ORM (Object-Relational Mapping)** semplificano enormemente l'interazione tra il codice orientato agli oggetti (come C#) e i database relazionali (basati su SQL).

---

## ✨ ORM (Object-Relational Mapping)

*   **Il Problema:** Il mondo della programmazione ad oggetti (classi, oggetti, ereditarietà) e il mondo dei database relazionali (tabelle, righe, chiavi) sono intrinsecamente diversi (un "impedance mismatch"). Scrivere manualmente il codice SQL per convertire i dati da un mondo all'altro è ripetitivo, noioso e soggetto a errori.
*   **La Soluzione (ORM):** Un ORM è una libreria che **automatizza** questa conversione. Permette allo sviluppatore di interagire con il database usando direttamente gli oggetti e le classi del proprio linguaggio di programmazione, senza scrivere SQL.

**Vantaggi:**
*   **Produttività:** Si scrive meno codice e più velocemente.
*   **Astrazione dal DB:** Si può cambiare il database sottostante (es. da SQL Server a SQLite) con modifiche minime al codice.
*   **Sicurezza:** Aiuta a prevenire attacchi di tipo **SQL Injection**.

---

## 🐘 Entity Framework Core (EF Core)

**Entity Framework Core** è l'ORM ufficiale di Microsoft, open-source e cross-platform, per le applicazioni .NET. È un ORM completo ("full-featured").

### Architettura e Workflow
1.  **Model (Modello):** Un insieme di classi C# (chiamate **entità**) che rappresentano le tabelle del database.
    ```csharp
    public class Product
    {
        public int ProductId { get; set; } // Diventa la chiave primaria per convenzione
        public string Name { get; set; }
        public decimal Price { get; set; }
    }
    ```
2.  **DbContext:** È una classe che rappresenta una **sessione** con il database. Contiene le proprietà `DbSet<T>` per ogni entità, che permettono di interrogare e salvare le istanze di quelle entità.
    ```csharp
    public class MyDbContext : DbContext
    {
        public DbSet<Product> Products { get; set; }
    }
    ```
3.  **LINQ (Language-Integrated Query):** Si usano le query LINQ per interrogare i dati. EF Core traduce queste query C# in SQL efficiente ed eseguibile dal database.
    ```csharp
    // Ottenere tutti i prodotti che costano più di 10
    var expensiveProducts = context.Products
                                   .Where(p => p.Price > 10)
                                   .ToList();
    ```

### Approcci di Sviluppo (Workflow)
*   **Code-First:** Si scrivono prima le classi C# e EF Core crea o aggiorna lo schema del database automaticamente (tramite le "migrations"). È l'approccio più comune oggi.
*   **Database-First:** Si parte da un database esistente e EF Core genera le classi C# corrispondenti.

---

## 🦓 Dapper: un Micro-ORM

**Dapper** è un'alternativa a EF Core, spesso definito un **"micro-ORM"**.
*   **Cosa fa:** È una libreria molto leggera che si concentra su una sola cosa: mappare in modo estremamente veloce i risultati di una query SQL a oggetti C#.
*   **Differenza con EF Core:**
    *   Con Dapper, lo sviluppatore **scrive direttamente il codice SQL**.
    *   Non offre funzionalità avanzate come il change tracking automatico o le migrations.
*   **Quando usarlo:** È ideale quando le **prestazioni di lettura sono la massima priorità** e si ha il pieno controllo delle query SQL.

**Esempio con Dapper:**
```csharp
string sql = "SELECT * FROM Products WHERE Price > @ProductPrice";
var products = connection.Query<Product>(sql, new { ProductPrice = 10 });
