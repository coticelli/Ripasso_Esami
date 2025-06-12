# 🛠️ Ambiente di Sviluppo: MS Visual Studio e Database Supportati

**Microsoft Visual Studio** è l'ambiente di sviluppo integrato (IDE) di riferimento per la creazione di applicazioni .NET. Offre un insieme completo di strumenti che semplificano la scrittura del codice, il debug, il test e la pubblicazione.

---

## ✨ Visual Studio: l'IDE per .NET

Un IDE come Visual Studio va ben oltre un semplice editor di testo. Le sue funzionalità chiave includono:

*   **Editor di Codice Avanzato:**
    *   **IntelliSense:** Suggerimenti e completamento automatico del codice, che aumentano la velocità e riducono gli errori.
    *   Evidenziazione della sintassi e analisi del codice in tempo reale.
*   **Debugger Potente:**
    *   Permette di eseguire il codice passo-passo, impostare **breakpoint** (punti di interruzione), ispezionare il valore delle variabili e analizzare lo stack delle chiamate per trovare e risolvere i bug.
*   **Template di Progetto:**
    *   Fornisce modelli pre-configurati per avviare rapidamente nuovi progetti (es. "ASP.NET Core Web App (Razor Pages)", "API Web", "App Console").
*   **Gestore di Pacchetti NuGet:**
    *   Un'interfaccia grafica per cercare, installare e gestire le librerie di terze parti (pacchetti) di cui il progetto ha bisogno (come Entity Framework, Dapper, etc.).
*   **Integrazione con Git:**
    *   Strumenti integrati per il controllo di versione, che permettono di clonare repository, eseguire commit, push, pull e gestire i branch direttamente dall'IDE.
*   **Strumenti di Pubblicazione (Publish):**
    *   Procedure guidate per distribuire (eseguire il "deploy") l'applicazione su server locali, server remoti o piattaforme cloud come Microsoft Azure.

---

## 🗃️ Database Supportati in ASP.NET Core

Grazie a Entity Framework Core (e ad altri ORM), le applicazioni ASP.NET Core possono interagire con un'ampia varietà di database relazionali e non. La scelta dipende dalle esigenze del progetto.

### Database Relazionali Comuni
*   **Microsoft SQL Server:**
    *   Il database di punta di Microsoft, estremamente potente e robusto. Ideale per applicazioni enterprise.
    *   **SQL Server Express:** Una versione gratuita per sviluppo e piccole applicazioni.
    *   **LocalDB:** Una versione ancora più leggera, installata con Visual Studio, perfetta per lo sviluppo locale senza dover installare un'istanza completa di SQL Server.
*   **SQLite:**
    *   Un motore di database **server-less**, basato su un singolo file.
    *   **Vantaggi:** Leggerissimo, zero configurazione, multipiattaforma.
    *   **Uso ideale:** Sviluppo, test, prototipazione rapida, piccole applicazioni o applicazioni mobile.
*   **MySQL e PostgreSQL:**
    *   Due dei più popolari database relazionali **open-source**. Sono potenti, affidabili e lo standard de-facto in molti ambienti di hosting Linux.
    *   Sono pienamente supportati da EF Core tramite l'installazione di un apposito pacchetto "provider".

### Database In-Memory
*   EF Core fornisce un **provider "In-Memory"** che non si connette a un vero database, ma salva i dati nella memoria RAM dell'applicazione.
*   **Non è un database persistente:** I dati vengono persi ogni volta che l'applicazione si riavvia.
*   **Uso principale:** **Test automatici**. Permette di eseguire test unitari e di integrazione in modo estremamente veloce e isolato, senza la necessità di una connessione a un database reale.
