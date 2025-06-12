# 🤝 API: Progettazione, Collaudo e Principi REST

Un'**API (Application Programming Interface)** è un insieme di regole e definizioni che permette a diverse applicazioni software di comunicare tra loro. Nel contesto web, un'API espone le funzionalità e i dati di un server in modo che possano essere utilizzati da altre applicazioni (es. un'app mobile, un sito front-end, un altro server).

---

## ✨ Principi dell'Architettura REST

**REST (REpresentational State Transfer)** è uno stile architetturale per la progettazione di API di rete. Non è un protocollo, ma un insieme di principi guida per creare API scalabili, flessibili e facili da usare.

1.  **Client-Server:** Netta separazione tra chi chiede i dati (client) e chi li fornisce (server).
2.  **Stateless (Senza Stato):** Ogni richiesta dal client al server deve contenere tutte le informazioni necessarie per essere compresa. Il server non memorizza lo stato del client tra una richiesta e l'altra.
3.  **Cacheable:** Le risposte del server devono poter essere memorizzate nella cache dal client per migliorare le performance.
4.  **Interfaccia Uniforme:** È il principio chiave. Si basa su:
    *   **Identificazione delle Risorse tramite URI:** Ogni risorsa (es. un utente, un prodotto) ha un identificatore univoco, l'URI (es. `/users/123`).
    *   **Manipolazione delle Risorse tramite Rappresentazioni:** Le risorse vengono manipolate tramite rappresentazioni standard, tipicamente **JSON**.
    *   **Uso dei Metodi HTTP Standard:** Le operazioni sulle risorse vengono eseguite utilizzando i verbi HTTP standard:
        *   `GET`: Legge una risorsa.
        *   `POST`: Crea una nuova risorsa.
        *   `PUT`: Aggiorna completamente una risorsa esistente.
        *   `DELETE`: Elimina una risorsa.

---

##  CRUD: Le Operazioni Fondamentali

**CRUD** è un acronimo che descrive le quattro operazioni di base sulla persistenza dei dati:

| Operazione | Significato      | Metodo HTTP (REST) |
| :--------- | :--------------- | :----------------- |
| **C**reate   | Creare           | `POST`             |
| **R**ead     | Leggere          | `GET`              |
| **U**pdate   | Aggiornare       | `PUT` / `PATCH`    |
| **D**elete   | Cancellare       | `DELETE`           |

Un'API RESTful tipicamente espone endpoint che mappano queste operazioni sulle risorse.
*   `GET /users` -> Leggi la lista di tutti gli utenti.
*   `GET /users/1` -> Leggi i dettagli dell'utente con ID 1.
*   `POST /users` -> Crea un nuovo utente.
*   `PUT /users/1` -> Aggiorna l'utente con ID 1.
*   `DELETE /users/1` -> Cancella l'utente con ID 1.

---

## 🛠️ Collaudo e Mock API

### Collaudo di un'API
*   Verificare che un'API funzioni correttamente è cruciale. Strumenti come **Postman** o l'estensione **Thunder Client** per VS Code permettono di:
    *   Inviare richieste HTTP a qualsiasi endpoint.
    *   Specificare il metodo, gli header, i parametri e il corpo della richiesta.
    *   Visualizzare la risposta del server (status code, body, header).
    *   Creare collezioni di test automatici.

### Mock API
*   **Cos'è:** Una **Mock API** (o API finta) simula il comportamento di un'API reale, ma restituisce dati statici o generati casualmente, senza avere un vero back-end o un database.
*   **Perché usarla?**
    *   Permette agli sviluppatori front-end di iniziare a lavorare e testare l'interfaccia utente **prima** che l'API del back-end sia pronta.
    *   Semplifica lo sviluppo parallelo tra team.
*   **Strumenti:** Si possono usare servizi online come **JSONPlaceholder**, **Mockoon**, o crearla rapidamente con Express.

---

## 🌐 API di Terze Parti

Molte applicazioni moderne si basano sull'integrazione di **API di terze parti** per aggiungere funzionalità senza doverle sviluppare da zero.
*   **Esempi:**
    *   **Stripe API** per gestire i pagamenti.
    *   **Google Maps API** per integrare mappe e geolocalizzazione.
    *   **Twilio API** per inviare SMS e gestire chiamate.
*   **Processo di integrazione:**
    1.  Registrarsi sulla piattaforma del fornitore.
    2.  Ottenere una **chiave API (API Key)**, una stringa segreta che autentica la propria applicazione.
    3.  Leggere la **documentazione** dell'API per capire come formattare le richieste e interpretare le risposte.
