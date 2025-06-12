# 🏗️ Architetture Software e il Framework ASP.NET Core

Lo sviluppo di applicazioni moderne si basa su architetture ben definite che separano le responsabilità e migliorano la manutenibilità. ASP.NET Core è un framework Microsoft potente e flessibile per costruire questo tipo di applicazioni.

---

## 🏛️ Architetture Software Comuni

### Architettura Client-Server
*   È il modello fondamentale del web.
*   **Client:** Il software che richiede un servizio (es. un browser web). È responsabile della presentazione (UI).
*   **Server:** Il software che fornisce il servizio richiesto (es. un web server che ospita un sito). È responsabile della logica di business e dell'accesso ai dati.
*   La comunicazione avviene tramite protocolli di rete, come HTTP.

### Architettura a 3 Livelli (3-Tier)
È una specializzazione del modello client-server che suddivide l'applicazione server in tre livelli logici separati:
1.  **Presentation Layer (Livello di Presentazione):** L'interfaccia utente (UI) con cui l'utente interagisce. Nel web, è il codice (HTML, CSS, JS) che viene eseguito nel browser.
2.  **Business Logic Layer (Livello di Logica Applicativa):** Il "cervello" dell'applicazione. Contiene le regole di business, i processi e i calcoli. È qui che viene gestita la logica principale.
3.  **Data Access Layer (Livello di Accesso ai Dati):** Responsabile della comunicazione con il database. Gestisce tutte le operazioni di lettura, scrittura, aggiornamento e cancellazione dei dati.

**Vantaggi:** Maggiore manutenibilità, scalabilità e riusabilità dei componenti.

---

## ✨ Il Framework ASP.NET Core

**ASP.NET Core** è un framework open-source, cross-platform e ad alte prestazioni sviluppato da Microsoft per la creazione di moderne applicazioni web e servizi basati su cloud.

### Caratteristiche Principali:
*   🚀 **Alte Prestazioni:** È uno dei framework web più veloci disponibili.
*   🖥️ **Cross-Platform:** Le applicazioni possono essere sviluppate e ospitate su Windows, macOS e Linux.
*   🔧 **Modulare e Leggero:** Costruito su un sistema di pacchetti (NuGet) che permette di includere solo le dipendenze strettamente necessarie.
*   💉 **Dependency Injection (DI) Integrata:** Ha un supporto nativo per il pattern della Dependency Injection, che promuove un codice più pulito, disaccoppiato e testabile.
*   🌐 **Supporto per Sviluppo Moderno:** Ideale per creare API RESTful, microservizi e applicazioni web tradizionali.

### Modelli di Sviluppo in ASP.NET Core
ASP.NET Core supporta diversi paradigmi di sviluppo:
*   **ASP.NET Core MVC (Model-View-Controller):** Un pattern classico per applicazioni complesse che separa nettamente la logica (Controller), i dati (Model) e la presentazione (View).
*   **Razor Pages:** Un modello più semplice e orientato alla pagina, ideale per applicazioni basate su form e con una logica meno complessa. Ogni pagina ha il suo file di markup (`.cshtml`) e il suo file di logica C# (`.cshtml.cs`).
*   **Blazor:** Un framework per costruire interfacce utente interattive lato client usando C# invece di JavaScript.
