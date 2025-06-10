# 📖 Paradigma Razor Pages (ASP.NET Core)

**Razor Pages** è un moderno framework, introdotto con ASP.NET Core, per la creazione di applicazioni web in modo **page-centric** (orientato alla pagina). Offre un'alternativa più semplice e organizzata al pattern MVC per molte applicazioni web.

---

## 🤔 Razor Pages vs MVC: Qual è la differenza?

*   **MVC (Model-View-Controller):** La logica è distribuita in tre componenti separati:
    *   **Model:** I dati.
    *   **View:** L'interfaccia utente (il file `.cshtml`).
    *   **Controller:** Gestisce le richieste e collega Model e View.
    L'approccio MVC è ottimo per applicazioni molto grandi e complesse, ma può essere macchinoso per operazioni semplici.

*   **Razor Pages:** La logica e l'interfaccia utente relative a una singola pagina sono **strettamente collegate e tenute insieme**. Questo rende il codice più facile da trovare e da gestire, specialmente per applicazioni basate su form e visualizzazione di dati.

---

## 🏗️ La Struttura di una Razor Page

Ogni Razor Page è composta da due file collegati:

1.  **File `.cshtml` (La Vista)**
    *   Contiene il markup **HTML** e la sintassi **Razor** (`@`).
    *   È responsabile della presentazione e della visualizzazione dei dati.

2.  **File `.cshtml.cs` (Il Modello / "Code-behind")**
    *   Contiene una classe C# che eredita da `PageModel`.
    *   Questa classe agisce sia da modello che da "mini-controller" per la sua pagina.

### La Classe `PageModel`
*   **Proprietà:** Contiene le proprietà (es. `@Model.UtenteCorrente`) che espongono i dati alla pagina `.cshtml`.
*   **Handler Methods:** Metodi speciali che gestiscono le richieste HTTP. I più comuni sono:
    *   `OnGet()`: Viene eseguito quando la pagina viene richiesta con il metodo **GET** (es. quando l'utente visita la pagina per la prima volta). Ideale per caricare dati da visualizzare.
    *   `OnPost()`: Viene eseguito quando viene inviato un form alla pagina con il metodo **POST**. Ideale per elaborare i dati inseriti dall'utente.

### Esempio Pratico:

**File `Saluta.cshtml`:**
```csharp
@page
@model MyApp.Pages.SalutaModel

<h1>Saluta</h1>

<form method="post">
    <input type="text" asp-for="NomeUtente" />
    <button type="submit">Invia</button>
</form>

@if (!string.IsNullOrEmpty(Model.Messaggio))
{
    <p>@Model.Messaggio</p>
}
```

File Saluta.cshtml.cs:
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;

namespace MyApp.Pages
{
    public class SalutaModel : PageModel
    {
        [BindProperty] // Collega questa proprietà all'input del form
        public string NomeUtente { get; set; }

        public string Messaggio { get; private set; }

        public void OnGet()
        {
            // Eseguito al primo caricamento della pagina
        }

        public void OnPost()
        {
            // Eseguito quando il form viene inviato
            Messaggio = $"Ciao, {NomeUtente}!";
        }
    }
}
