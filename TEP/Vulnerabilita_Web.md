# 🚨 Prevenzione delle Vulnerabilità Web Comuni

La sicurezza di un'applicazione web non riguarda solo l'autenticazione, ma anche la protezione da attacchi comuni che sfruttano le vulnerabilità del codice e del protocollo HTTP.

---

## 💉 SQL Injection

*   **Cos'è:** Un attacco in cui un malintenzionato "inietta" codice SQL dannoso all'interno di un campo di input di un'applicazione (es. un form di login o una barra di ricerca).
*   **Obiettivo:** Manipolare le query SQL eseguite dal server per bypassare l'autenticazione, leggere dati sensibili, modificare o cancellare dati.
*   **Esempio di attacco (su un campo password):** ` ' OR '1'='1 `
    Se la query è costruita concatenando le stringhe, potrebbe diventare `SELECT * FROM Utenti WHERE Username='admin' AND Password='' OR '1'='1'`, restituendo sempre un risultato vero e garantendo l'accesso.
*   **Come si previene:**
    *   **Query Parametrizzate (Prepared Statements):** È la difesa più efficace. I valori forniti dall'utente non vengono inseriti direttamente nella stringa SQL, ma passati come parametri separati. Il driver del database si occupa di "sanitizzare" l'input.
    *   **Usare un ORM (come Entity Framework):** Gli ORM usano query parametrizzate per impostazione predefinita, rendendo le applicazioni molto più sicure contro questo tipo di attacco.

---

## 🎭 Cross-Site Request Forgery (CSRF o XSRF)

*   **Cos'è:** Un attacco che costringe un utente autenticato a eseguire un'azione indesiderata su un sito web su cui è attualmente loggato, a sua insaputa.
*   **Come funziona:** Un malintenzionato crea una pagina web, un'email o un'immagine malevola che, quando viene cliccata dall'utente, invia una richiesta a un altro sito (es. la sua banca). Poiché l'utente è già autenticato su quel sito, il suo browser invia automaticamente i cookie di autenticazione e il server esegue l'azione (es. "trasferisci 100€").
*   **Come si previene in ASP.NET Core:**
    *   **Token Anti-Forgery:** ASP.NET Core genera automaticamente un token univoco e nascosto per ogni form. Quando il form viene inviato, il server controlla che il token ricevuto corrisponda a quello generato. Poiché la pagina malevola dell'attaccante non può conoscere questo token, la richiesta viene bloccata.
    *   Si abilita con l'attributo `[ValidateAntiForgeryToken]` e l'helper `<form method="post">` in Razor Pages.

---

## 🌐 Cross-Origin Resource Sharing (CORS)

*   **Non è una vulnerabilità, ma un meccanismo di sicurezza** implementato dai browser per prevenire che una pagina web possa effettuare richieste a un dominio (origine) diverso da quello da cui è stata servita (la **Same-Origin Policy**).
*   **Il Problema:** A volte, è legittimo che un'applicazione client (es. scritta in JavaScript) in esecuzione su `dominio-A.com` debba chiamare un'API ospitata su `api.dominio-B.com`. Di default, il browser bloccherebbe questa richiesta.
*   **La Soluzione (CORS):** È una specifica che permette al server (`api.dominio-B.com`) di comunicare al browser quali altri domini sono autorizzati a fare richieste.
*   **Come si configura in ASP.NET Core:**
    *   Si definisce una "policy" CORS in `Program.cs`, specificando quali origini, metodi HTTP (GET, POST) e header sono permessi.
    *   Si applica la policy globalmente o a specifici endpoint.

```csharp
// Esempio di configurazione CORS in Program.cs
builder.Services.AddCors(options =>
{
    options.AddPolicy("MyPolicy", builder =>
    {
        builder.WithOrigins("https://www.mio-sito-client.com")
               .WithMethods("GET", "POST")
               .WithHeaders("Content-Type");
    });
});

// ...

app.UseCors("MyPolicy");
