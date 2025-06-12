# ⚙️ Web Framework: Express.js e Altri Strumenti

Un **web framework** è una libreria o un insieme di strumenti software che fornisce un modo standardizzato e semplificato per costruire e gestire applicazioni web. Invece di scrivere tutto da zero, un framework offre soluzioni pronte per i compiti più comuni, come il routing, la gestione delle richieste HTTP e l'interazione con i database.

---

## ✨ Express.js: Il Framework per Node.js

**Express.js** è il web framework più popolare per **Node.js**. È noto per essere **minimalista, flessibile e non opinionato** (un-opinionated), il che significa che fornisce solo le funzionalità essenziali senza imporre una struttura rigida all'applicazione.

### Caratteristiche Principali
*   **Routing:** Gestisce le richieste HTTP in base all'URL (il "percorso") e al metodo HTTP (GET, POST, PUT, DELETE).
*   **Middleware:** È il concetto centrale di Express. Un middleware è una funzione che ha accesso all'oggetto della richiesta (`req`), all'oggetto della risposta (`res`) e alla funzione successiva (`next`) nella pipeline di gestione della richiesta. Permette di eseguire compiti intermedi come il logging, l'autenticazione, la compressione dei dati, etc.
*   **Gestione di Richieste e Risposte:** Semplifica la lettura dei dati dalla richiesta (parametri, corpo del messaggio) e l'invio di una risposta al client.

**Esempio di base di un server Express:**
```javascript
const express = require('express');
const app = express();
const port = 3000;

// Middleware per il logging di ogni richiesta
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next(); // Passa al middleware successivo
});

// Definizione di una rotta per la homepage
app.get('/', (req, res) => {
  res.send('Ciao Mondo!');
});

// Avvio del server
app.listen(port, () => {
  console.log(`Server in ascolto sulla porta ${port}`);
});
Use code with caution.
Markdown
🎨 Templating Engines
Un templating engine (motore di templating) è uno strumento che permette di generare documenti (tipicamente HTML) combinando un template statico con dati dinamici provenienti dal server.
Scopo: Separare la logica di presentazione (HTML) dalla logica applicativa (JavaScript/Node.js).
Come funziona: Si crea un file di template con una sintassi speciale (segnaposto, cicli, condizioni). Il motore di templating prende questo file, lo popola con i dati forniti dal server e produce un file HTML finale da inviare al client.
Esempi popolari per Express.js:
EJS (Embedded JavaScript): Permette di scrivere JavaScript direttamente all'interno dell'HTML, usando tag speciali come <% ... %>.
Pug (precedentemente Jade): Usa una sintassi basata sull'indentazione, molto concisa e senza tag di chiusura HTML.
Handlebars: Noto per la sua logica minimale e la sintassi chiara.
🖼️ Front-end JavaScript Frameworks
Mentre i web framework come Express gestiscono il back-end, i framework JavaScript front-end gestiscono la logica e l'interattività dell'interfaccia utente direttamente nel browser del client.
Scopo: Creare Single-Page Applications (SPA), applicazioni web dinamiche e reattive che non hanno bisogno di ricaricare l'intera pagina ad ogni interazione.
Come funzionano: Il server invia un'unica pagina HTML iniziale, e poi l'applicazione JavaScript prende il controllo, caricando i dati necessari tramite chiamate API al back-end e aggiornando dinamicamente il DOM.
Framework più popolari:
React: Sviluppato da Facebook, basato su un'architettura a componenti.
Angular: Sviluppato da Google, un framework completo e "opinionated".
Vue.js: Noto per la sua curva di apprendimento dolce e la sua flessibilità.
