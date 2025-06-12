# 🏗️ Struttura di un'App .NET Core: Dependency Injection e Servizi

Un'applicazione ASP.NET Core ha una struttura ben definita, progettata per essere modulare e testabile. I concetti chiave che la governano sono il **contenitore dei servizi** e la **Dependency Injection (DI)**.

---

## 📄 I File Fondamentali: `Program.cs` e `appsettings.json`

### `Program.cs`
È il punto di ingresso dell'applicazione, il suo cuore pulsante. Nelle versioni moderne di .NET, questo file gestisce due responsabilità principali:

1.  **Configurazione dei Servizi (il "Builder"):**
    *   In questa parte si "registrano" tutti i servizi che l'applicazione utilizzerà. Un servizio è una classe che svolge un compito specifico (es. accedere al database, inviare email).
    *   La registrazione avviene tramite `builder.Services.Add...()`.
    *   Questo insieme di servizi registrati forma il **Service Container** (o contenitore IoC).

2.  **Configurazione della Pipeline HTTP (l'"App"):**
    *   In questa parte si definisce come l'applicazione risponderà alle richieste HTTP in arrivo.
    *   È una sequenza di componenti chiamati **middleware**. Ogni richiesta attraversa questa "pipeline".
    *   Si configura tramite `app.Use...()` (es. `app.UseRouting()`, `app.UseAuthentication()`, `app.MapRazorPages()`).

```csharp
// Esempio semplificato di Program.cs
var builder = WebApplication.CreateBuilder(args);

// 1. Registrazione dei servizi
builder.Services.AddRazorPages();
builder.Services.AddDbContext<MyDbContext>(options => ...);
builder.Services.AddScoped<IMyCustomService, MyCustomService>(); // Registrazione per DI

var app = builder.Build();

// 2. Configurazione della pipeline HTTP
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();

app.Run();
```
appsettings.json
È il file di configurazione principale. Contiene impostazioni in formato JSON.
ConnectionStrings: Stringhe di connessione al database.
Logging: Livelli di dettaglio per i log.
Impostazioni personalizzate dell'applicazione.
💉 Dependency Injection (DI)
La Dependency Injection è un design pattern fondamentale in .NET Core.
Il Concetto: Invece di una classe che crea al suo interno gli oggetti di cui ha bisogno (le sue "dipendenze"), queste dipendenze le vengono fornite ("iniettate") dall'esterno, tramite il Service Container.
Come funziona:
Registrazione: Nel file Program.cs, si registra un'interfaccia con la sua implementazione concreta (es. builder.Services.AddScoped<IMyService, MyService>();).
Iniezione: Quando una classe (es. un PageModel) ha bisogno di quel servizio, lo richiede nel suo costruttore. Il Service Container ne creerà un'istanza e la passerà automaticamente.
Vantaggi: Promuove un codice disaccoppiato, più facile da mantenere, modificare e testare.
// Esempio di iniezione in un PageModel
public class IndexModel : PageModel
{
    private readonly IMyCustomService _myService;

    // Il servizio viene "iniettato" qui
    public IndexModel(IMyCustomService myService)
    {
        _myService = myService;
    }

    public void OnGet()
    {
        // Ora posso usare il servizio
        var data = _myService.GetData();
    }
}
Use code with caution.
C#
Durata dei Servizi (Lifetimes)
Quando si registra un servizio, se ne specifica la durata:
AddSingleton(): Viene creata una sola istanza per tutta la durata dell'applicazione.
AddScoped(): Viene creata una nuova istanza per ogni richiesta HTTP. Tutti i componenti all'interno della stessa richiesta condividono la stessa istanza. È la durata tipica per il DbContext.
AddTransient(): Viene creata una nuova istanza ogni volta che viene richiesto un servizio.
