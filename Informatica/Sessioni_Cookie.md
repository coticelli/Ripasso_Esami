# 🍪 Gestione di Sessioni e Cookie

Cookie e sessioni sono due meccanismi fondamentali per mantenere lo stato e memorizzare informazioni tra le diverse richieste HTTP, che per natura sono "stateless" (senza memoria).

---

## 🍪 Cosa sono i Cookie?

*   **Definizione:** Un **cookie** è un piccolo file di testo che un server web invia al browser di un utente. Il browser lo memorizza e lo invia automaticamente al server ad ogni richiesta successiva verso quel sito.
*   **Utilizzi Comuni:**
    *   **Autenticazione:** Memorizzare l'identità dell'utente dopo il login.
    *   **Personalizzazione:** Ricordare le preferenze dell'utente (es. lingua, tema scuro).
    *   **Tracciamento (Tracking):** Monitorare le abitudini di navigazione per scopi statistici o pubblicitari.
*   **Tipi di Cookie:**
    *   **Cookie di sessione:** Vengono cancellati quando il browser viene chiuso.
    *   **Cookie persistenti:** Hanno una data di scadenza e rimangono sul computer dell'utente fino a quella data.

### Cookie e GDPR
Il **GDPR (General Data Protection Regulation)** impone regole severe sull'uso dei cookie, specialmente quelli non strettamente necessari (come quelli di tracciamento e profilazione).
*   È necessario ottenere il **consenso esplicito** dell'utente prima di installare cookie non essenziali.
*   Bisogna fornire un'informativa chiara (cookie policy) che spieghi quali cookie vengono usati e per quale scopo.
*   Per questo motivo, quasi tutti i siti oggi mostrano un **cookie banner**.

---

## 🛋️ Cos'è la Gestione delle Sessioni?

*   **Definizione:** Una **sessione** è un meccanismo che permette di memorizzare dati specifici di un utente **lato server** per la durata della sua visita.
*   **Come funziona:**
    1.  Quando un utente visita un sito per la prima volta, il server crea un **ID di sessione univoco**.
    2.  Questo ID viene inviato al browser dell'utente e memorizzato in un **cookie di sessione**.
    3.  Ad ogni richiesta successiva, il browser invia il cookie con l'ID di sessione.
    4.  Il server usa questo ID per recuperare i dati specifici di quell'utente (es. il carrello della spesa) che sono memorizzati sul server stesso.

**Differenza chiave tra Cookie e Sessione:**
*   **Cookie:** I dati sono memorizzati sul **client** (browser). Adatti per piccole quantità di dati non sensibili.
*   **Sessione:** I dati sono memorizzati sul **server**. Il client ha solo un piccolo ID. Adatta per dati più grandi o sensibili.

### Gestione delle Sessioni in ASP.NET Core
*   **Configurazione:** La gestione delle sessioni deve essere abilitata esplicitamente in `Program.cs`.
    ```csharp
    // Registrazione del servizio
    builder.Services.AddSession(options =>
    {
        options.IdleTimeout = TimeSpan.FromMinutes(20); // La sessione scade dopo 20 min di inattività
        options.Cookie.HttpOnly = true;
        options.Cookie.IsEssential = true;
    });

    // Aggiunta del middleware alla pipeline (prima di MapRazorPages/MapControllers)
    app.UseSession();
    ```
*   **Utilizzo:** Si può accedere all'oggetto sessione tramite l'oggetto `HttpContext`.
    ```csharp
    // Scrivere nella sessione
    HttpContext.Session.SetString("NomeUtente", "MarioRossi");
    HttpContext.Session.SetInt32("ArticoliCarrello", 5);

    // Leggere dalla sessione
    var nome = HttpContext.Session.GetString("NomeUtente");
