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
```

```html
<!-- Esempio di file Razor (Index.cshtml) -->
@page
@model IndexModel
<h2>Pagina di Esempio</h2>
<p>@Model.Messaggio</p>
```

---

## 🚀 Hosting di un'Applicazione ASP.NET Core

"Hosting" significa eseguire un'applicazione web su un server in modo che sia accessibile agli utenti tramite internet.

### Web Server in ASP.NET Core
*   **Kestrel:**
    *   È il **web server cross-platform predefinito** per ASP.NET Core. È estremamente veloce e leggero.
    *   È progettato per essere eseguito come server "edge" (direttamente esposto a internet) o, più comunemente, dietro un **reverse proxy server**.
*   **Reverse Proxy Server (IIS, Nginx, Apache):**
    *   È un server che si trova di fronte a Kestrel e inoltra le richieste HTTP a esso.
    *   **Vantaggi:** Aggiunge un livello di sicurezza, gestisce il load balancing (bilanciamento del carico), il caching e la terminazione SSL.
    *   **IIS (Internet Information Services):** È il web server di Windows. Quando si sviluppa in Visual Studio su Windows, si usa spesso **IIS Express**, una versione leggera di IIS per lo sviluppo locale.

### Hosting su Cloud
Le applicazioni ASP.NET Core sono progettate per essere facilmente ospitate su piattaforme cloud come:
*   **Microsoft Azure:** L'offerta cloud di Microsoft, con un'integrazione nativa per le app .NET.
*   **AWS (Amazon Web Services)** e **Google Cloud Platform (GCP)**.
*   **Hosting condiviso** che supporta .NET Core.

Queste piattaforme semplificano il deployment, la scalabilità e la gestione dell'infrastruttura.
```
