# 🔐 Autenticazione e Autorizzazione in .NET Core

**Autenticazione** e **autorizzazione** sono due concetti di sicurezza fondamentali, ma distinti.

*   **Autenticazione (Chi sei?):** È il processo di **verificare l'identità** di un utente. L'utente fornisce delle credenziali (es. username e password) e il sistema controlla se sono valide.
*   **Autorizzazione (Cosa puoi fare?):** È il processo di **verificare se un utente autenticato ha il permesso** di accedere a una specifica risorsa o di eseguire una determinata azione.

---

## ✨ ASP.NET Core Identity

**ASP.NET Core Identity** è il framework di Microsoft per la gestione dell'autenticazione e dell'autorizzazione. Fornisce un sistema completo e personalizzabile per:
*   Registrazione di nuovi utenti.
*   Login e logout.
*   Gestione delle password (hashing, reset).
*   Gestione dei profili utente.
*   Supporto per l'autenticazione a due fattori (2FA).
*   Integrazione con provider di login esterni (Google, Facebook, Twitter).

Identity gestisce automaticamente la creazione delle tabelle necessarie nel database (tramite EF Core) per memorizzare utenti, ruoli, claims, etc.

---

## 🔑 Autenticazione in .NET Core

Il meccanismo più comune per l'autenticazione nelle applicazioni web tradizionali è basato sui **cookie**.
1.  L'utente invia username e password.
2.  Il server verifica le credenziali.
3.  Se sono corrette, il server crea un **cookie di autenticazione** crittografato e lo invia al browser dell'utente.
4.  Per ogni richiesta successiva, il browser invia automaticamente il cookie. Il server lo decodifica per identificare l'utente senza dover chiedere di nuovo le credenziali.

**In `Program.cs`, si configura così:**
```csharp
builder.Services.AddAuthentication(CookieAuthenticationDefaults.AuthenticationScheme)
    .AddCookie();
builder.Services.AddIdentity<IdentityUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>();

// Nella pipeline HTTP...
app.UseAuthentication(); // Deve venire prima di UseAuthorization
Use code with caution.
Markdown
👮‍♂️ Autorizzazione in .NET Core
Una volta che un utente è autenticato, l'autorizzazione determina cosa può fare.
1. Simple Authorization (Autorizzazione Semplice)
Scopo: Limitare l'accesso a una risorsa solo agli utenti autenticati.
Come si usa: Si applica l'attributo [Authorize] a una pagina Razor o a un controller MVC.
[Authorize]
public class PaginaRiservataModel : PageModel
{
    // ... logica della pagina ...
}
Use code with caution.
C#
2. Role-Based Authorization (Autorizzazione Basata sui Ruoli)
Scopo: Concedere l'accesso solo agli utenti che appartengono a uno o più ruoli specifici (es. "Admin", "Manager", "User").
Come si usa: Si specificano i ruoli nell'attributo [Authorize].
[Authorize(Roles = "Admin,Manager")]
public class PannelloAdminModel : PageModel
{
    // ...
}
Use code with caution.
C#
3. Policy-Based Authorization (Autorizzazione Basata su Policy)
È un modello più flessibile e potente. Permette di definire requisiti di autorizzazione complessi ("policy") che possono basarsi non solo sui ruoli, ma anche su altre informazioni dell'utente (claims), come l'età, la nazionalità, o permessi specifici.
