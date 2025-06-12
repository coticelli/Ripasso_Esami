# 📄 Sviluppo con Razor Pages e Hosting

**Razor Pages** è un modello di programmazione all'interno di ASP.NET Core che rende la creazione di applicazioni web basate su pagine più semplice e produttiva rispetto al pattern MVC tradizionale.

---

## ✨ Cos'è Razor Pages?

*   **Approccio orientato alla pagina:** Ogni "pagina" dell'applicazione è composta da due file strettamente collegati:
    1.  Un file **`.cshtml`** (il file Razor) che contiene il markup HTML e la sintassi Razor per la logica di presentazione.
    2.  Un file **`.cshtml.cs`** (il file "code-behind") che contiene la classe C# `PageModel`, responsabile della gestione della logica della pagina.
*   **Convenzione su configurazione:** Il routing è basato sulla posizione dei file nella cartella `Pages`. Una richiesta a `/Products/Index` verrà automaticamente mappata al file `Pages/Products/Index.cshtml`.
*   **Ideale per:** Applicazioni basate su moduli (form), dove l'interazione dell'utente è centrata su una singola pagina (es. pagine di login, creazione di un record, visualizzazione di dettagli).

### La Sintassi Razor
Razor è un motore di templating che permette di mescolare codice C# con il markup HTML in modo pulito e leggibile.
*   **Carattere `@`:** Viene usato per passare dal markup HTML al codice C#.
    *   `<h1>@Model.TitoloPagina</h1>` (visualizza una proprietà del modello)
    *   `@{ var messaggio = "Ciao mondo"; } <p>@messaggio</p>` (blocco di codice)
*   **Handler Methods:** Nel file `PageModel`, metodi speciali come `OnGet()`, `OnPost()`, `OnPostDeleteAsync()` gestiscono le richieste HTTP (GET, POST, etc.) dirette alla pagina.

```csharp
// Esempio di PageModel (Index.cshtml.cs)
public class IndexModel : PageModel
{
    public string Messaggio { get; private set; }

    // Metodo handler per le richieste GET
    public void OnGet()
    {
        Messaggio = "Questa pagina è stata caricata alle " + DateTime.Now.ToLongTimeString();
    }
}
<!-- Esempio di file Razor (Index.cshtml) -->
@page
@model IndexModel
<h2>Pagina di Esempio</h2>
<p>@Model.Messaggio</p>
