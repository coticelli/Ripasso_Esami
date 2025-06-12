# 🌐 Sistemi Distribuiti: Introduzione e Concetti Chiave

Un **sistema distribuito** è un insieme di computer autonomi e interconnessi che appaiono all'utente finale come un unico sistema coerente. Invece di avere un'unica grande macchina, la potenza di calcolo e i dati sono distribuiti su più nodi che comunicano tra loro attraverso una rete.

---

## 👍 Benefici (Vantaggi) dei Sistemi Distribuiti

1.  **Scalabilità (Scalability) 📈:**
    *   È facile aumentare la capacità del sistema aggiungendo nuovi computer (nodi). Questo si chiama **scalabilità orizzontale** ed è generalmente più economico e flessibile della scalabilità verticale (potenziare un singolo server).

2.  **Affidabilità e Disponibilità (Reliability & Availability) ✅:**
    *   Grazie alla **ridondanza**, se un nodo del sistema si guasta, gli altri possono continuare a funzionare, garantendo che il servizio rimanga disponibile. Il sistema è resiliente ai guasti (fault-tolerant).

3.  **Performance 🚀:**
    *   Più computer possono lavorare in parallelo su un problema, riducendo i tempi di elaborazione e gestendo un numero maggiore di richieste contemporaneamente.

4.  **Condivisione delle Risorse 🤝:**
    *   Permettono la condivisione di hardware (stampanti, dischi), software e dati tra utenti geograficamente distribuiti.

---

## 👎 Svantaggi e Sfide

1.  **Complessità 🧠:**
    *   Progettare, implementare e debuggare un sistema distribuito è molto più complesso di un sistema centralizzato.

2.  **Sicurezza 🔒:**
    *   Ci sono più punti di attacco. I dati viaggiano sulla rete e devono essere protetti da intercettazioni e accessi non autorizzati.

3.  **Sincronizzazione e Consistenza 🔄:**
    *   Mantenere i dati coerenti su tutti i nodi è una sfida enorme. Se un dato viene aggiornato su un nodo, come e quando viene propagato agli altri?

4.  **Latenza di Rete ⏳:**
    *   La comunicazione tra i nodi introduce ritardi (latenza) che devono essere gestiti.

---

## ✨ Il Concetto di Trasparenza

La **trasparenza** è l'obiettivo principale di un sistema distribuito: **nascondere la sua natura distribuita** all'utente e allo sviluppatore. L'intero sistema dovrebbe apparire come un normale computer singolo.

### Tipi di Trasparenza
*   **Trasparenza all'Accesso:** Gli utenti accedono a risorse locali e remote nello stesso modo.
*   **Trasparenza alla Posizione:** Gli utenti non sanno (e non devono sapere) dove si trova fisicamente una risorsa.
*   **Trasparenza alla Migrazione:** Le risorse possono essere spostate da un nodo all'altro senza che gli utenti se ne accorgano.
*   **Trasparenza alla Concorrenza:** Più utenti possono accedere alle stesse risorse contemporaneamente in modo controllato, senza interferire tra loro.
*   **Trasparenza al Guasto:** Il sistema può mascherare il guasto e il ripristino di un nodo, continuando a funzionare senza interruzioni per l'utente.
