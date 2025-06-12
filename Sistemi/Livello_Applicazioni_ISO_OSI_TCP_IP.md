# 🖥️ Il Livello delle Applicazioni

Il **livello di Applicazione** (Application Layer) è il livello più alto nei modelli di rete ISO/OSI e TCP/IP. È il livello con cui le applicazioni software dell'utente finale interagiscono per comunicare attraverso la rete.

Non fornisce servizi ad altri livelli, ma **utilizza i servizi** del livello sottostante (il livello di Trasporto) per inviare e ricevere dati.

---

## 🆚 ISO/OSI vs. TCP/IP

I due modelli principali descrivono la stratificazione delle reti in modi leggermente diversi:
*   **Modello ISO/OSI (7 Livelli):** È un modello teorico e di riferimento. Il livello applicativo è il 7° e ultimo strato, che si occupa solo di fornire l'interfaccia. Le funzioni di formattazione e gestione della sessione sono delegate ai livelli sottostanti (Presentazione e Sessione).
*   **Modello TCP/IP (4/5 Livelli):** È il modello pratico su cui si basa Internet. Il livello Applicazione del TCP/IP **accorpa le funzionalità dei tre livelli superiori dell'OSI** (Applicazione, Presentazione e Sessione).

| Modello ISO/OSI       | Modello TCP/IP      |
| --------------------- | ------------------- |
| **7. Applicazione**   | \multirow{3}{*}{**Applicazione**} |
| **6. Presentazione**  |                     |
| **5. Sessione**       |                     |
| **4. Trasporto**      | **Trasporto**       |
| **3. Rete**           | **Internet**        |
| **2. Data Link**      | \multirow{2}{*}{**Accesso alla Rete**} |
| **1. Fisico**         |                     |

---

## 🏛️ Architettura Client-Server

È il modello architetturale più comune per le applicazioni di rete:
*   **Client 💻:** Un programma che richiede un servizio. Avvia la comunicazione.
    *   *Esempio:* Un browser web, un client di posta elettronica.
*   **Server 🖥️:** Un programma che rimane costantemente in attesa di richieste da parte dei client e fornisce il servizio richiesto.
    *   *Esempio:* Un web server (Apache, Nginx), un mail server.

La comunicazione avviene attraverso protocolli specifici del livello di Applicazione (HTTP, FTP, SMTP, etc.).

---

## 🤝 Servizi dello Strato di Trasporto

Il livello Applicazione decide quale servizio del livello di Trasporto utilizzare, in base alle proprie necessità:

*   **TCP (Transmission Control Protocol):**
    *   **Caratteristica:** **Affidabile e orientato alla connessione**.
    *   Garantisce che tutti i dati arrivino a destinazione, integri e nell'ordine corretto. Stabilisce una connessione prima di inviare i dati.
    *   **Usato da:** Protocolli che non possono tollerare perdite di dati, come **HTTP/HTTPS, FTP, SMTP**.

*   **UDP (User Datagram Protocol):**
    *   **Caratteristica:** **Veloce e non orientato alla connessione ("best-effort")**.
    *   Non garantisce la consegna, l'ordine o l'integrità dei dati. È molto più leggero e veloce di TCP.
    *   **Usato da:** Protocolli dove la velocità è più importante della precisione assoluta, come lo **streaming video/audio, i giochi online, il DNS**.
