# 🛡️ La Sicurezza delle Reti

La sicurezza delle reti (network security) è l'insieme delle policy e delle pratiche adottate per prevenire e monitorare accessi non autorizzati, usi impropri, modifiche o negazioni di servizio a una rete di computer e alle sue risorse.

---

## ❗ Rischi e Minacce Comuni

*   **Malware:** Software malevolo (virus, worm, trojan, ransomware, spyware) progettato per danneggiare o sfruttare un sistema.
*   **Phishing:** Tentativi di frode per ottenere informazioni sensibili (credenziali, dati bancari) fingendosi un'entità affidabile (es. una banca).
*   **Denial of Service (DoS) / Distributed Denial of Service (DDoS):** Attacchi che mirano a rendere una risorsa di rete (come un sito web) indisponibile ai suoi utenti legittimi, sovraccaricandola di traffico inutile.
*   **Man-in-the-Middle (MitM):** Un attaccante si interpone segretamente tra due parti che comunicano, intercettando e potenzialmente alterando i messaggi.
*   **Accesso Non Autorizzato:** Tentativi di ottenere l'accesso a sistemi o dati senza permesso, spesso sfruttando password deboli o vulnerabilità del software.

---

## 🔒 Protocolli e Tecnologie di Difesa

### SSL/TLS (Secure Sockets Layer / Transport Layer Security)
*   È il protocollo crittografico che fornisce comunicazioni sicure su una rete di computer. È il fondamento di **HTTPS**.
*   **Funzionamento (Handshake TLS):**
    1.  Il client si connette al server e chiede una connessione sicura.
    2.  Il server risponde inviando il suo **certificato digitale**.
    3.  Il client verifica il certificato e, se valido, usa la chiave pubblica del server per scambiare in modo sicuro una **chiave di sessione simmetrica**.
    4.  Da quel momento, tutta la comunicazione viene crittografata con la chiave simmetrica, che è molto più veloce.

### Firewall
*   È un dispositivo di sicurezza di rete (hardware o software) che monitora e controlla il traffico di rete in entrata e in uscita, basandosi su un insieme di regole di sicurezza predefinite.
*   **Funzione:** Agisce come una barriera tra una rete interna fidata e una rete esterna non fidata (come Internet).
*   **Tipi comuni:**
    *   **Packet-filtering Firewall:** Opera a livello 3 (Rete) e 4 (Trasporto). Esamina l'header dei pacchetti (IP sorgente/destinazione, porta sorgente/destinazione) e decide se bloccarli o inoltrarli.
    *   **Stateful Inspection Firewall:** Mantiene traccia dello stato delle connessioni attive.
    *   **Next-Generation Firewall (NGFW):** Firewall più avanzati che includono funzionalità come l'ispezione profonda dei pacchetti (DPI), la prevenzione delle intrusioni (IPS) e il controllo delle applicazioni.

### ACL (Access Control List)
*   È una **lista di regole (permessi)** applicata alle interfacce di un router o di un firewall.
*   **Scopo:** Specificare quale traffico è autorizzato a entrare o uscire da una rete.
*   **Criteri:** Le regole possono basarsi su indirizzi IP sorgente/destinazione, protocolli (TCP, UDP), numeri di porta e altri parametri. Le regole vengono lette in ordine e, alla prima corrispondenza, l'azione (di solito `permit` o `deny`) viene eseguita. Ogni ACL ha una regola implicita di `deny all` alla fine.

### DMZ (Demilitarized Zone)
*   È una **sottorete fisica o logica** che si trova tra la rete interna privata di un'organizzazione e la rete esterna pubblica.
*   **Scopo:** Ospitare i server che devono essere accessibili da Internet (es. web server, mail server, DNS server), isolandoli dalla rete interna.
*   **Architettura:** In una configurazione tipica con due firewall, la DMZ si trova nello spazio tra il firewall esterno e quello interno. Se un attaccante compromette un server nella DMZ, non avrà comunque accesso diretto alla rete aziendale interna.
