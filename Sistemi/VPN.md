# 🌐 Virtual Private Network (VPN)

Una **VPN** è una tecnologia che crea una connessione sicura e crittografata su una rete pubblica (come Internet), estendendo una rete privata. Permette agli utenti di inviare e ricevere dati come se i loro dispositivi fossero direttamente collegati alla rete privata.

---

## 🤔 Funzionalità e Vantaggi Principali

1.  **Riservatezza e Sicurezza 🔒:** Il traffico all'interno della VPN viene incapsulato e **crittografato**, creando un "tunnel" sicuro. Questo protegge i dati da intercettazioni, specialmente quando si usano reti Wi-Fi pubbliche non sicure.
2.  **Accesso Remoto 🏠:** Permette ai dipendenti di accedere in modo sicuro alle risorse della rete aziendale (file server, stampanti, etc.) da casa o mentre sono in viaggio.
3.  **Anonimato e Privacy 🕵️:** Una VPN nasconde l'indirizzo IP reale dell'utente, sostituendolo con quello del server VPN. Questo aiuta a proteggere la privacy e a bypassare la geolocalizzazione (es. per accedere a contenuti disponibili solo in altri paesi).
4.  **Connessione di Sedi Remote 🏢:** Permette di collegare in modo sicuro le reti di diverse sedi aziendali attraverso Internet, come se fossero un'unica rete locale.

---

## 🚀 Tipi di Implementazione VPN

### 1. Remote-Access VPN (o Remote-to-Site)
*   **Scopo:** Permettere a un singolo utente remoto di connettersi alla rete privata aziendale.
*   **Come funziona:** L'utente installa un software client VPN sul proprio dispositivo (PC, smartphone). Questo client stabilisce un tunnel sicuro con un server VPN (o "concentratore") situato presso la sede aziendale.
*   **Uso tipico:** Telelavoro (smart working), accesso in mobilità.

### 2. Site-to-Site VPN
*   **Scopo:** Collegare due o più reti locali (LAN) di sedi diverse in modo permanente e trasparente per gli utenti.
*   **Come funziona:** Un dispositivo di rete (router o firewall con funzionalità VPN) in ogni sede stabilisce un tunnel permanente con gli altri dispositivi. Gli utenti di una sede possono accedere alle risorse delle altre sedi come se si trovassero sulla stessa LAN, senza bisogno di un client software.
*   **Uso tipico:** Connessione tra la sede centrale di un'azienda e le sue filiali.

---

## 🔒 Protocolli VPN

La sicurezza di una VPN è garantita da protocolli di tunneling e crittografia. I più importanti sono:

### IPsec (Internet Protocol Security)
*   È una **suite di protocolli** che opera al livello di Rete (livello 3). È considerato lo standard per le VPN site-to-site.
*   **Componenti principali:**
    *   **AH (Authentication Header):** Fornisce l'autenticazione dell'origine e l'integrità dei dati, ma non la crittografia.
    *   **ESP (Encapsulating Security Payload):** Fornisce **sia la crittografia** (riservatezza) che l'autenticazione e l'integrità. È il componente più utilizzato.
*   **Modalità:**
    *   **Transport Mode:** Crittografa solo il payload (i dati) del pacchetto IP, lasciando l'header originale in chiaro.
    *   **Tunnel Mode:** Crittografa e incapsula l'**intero pacchetto IP originale** all'interno di un nuovo pacchetto IP. È la modalità usata per le VPN.

### SSL/TLS VPN
*   Utilizza i protocolli SSL/TLS (gli stessi di HTTPS) per creare il tunnel sicuro.
*   **Vantaggio:** Spesso più facile da configurare e meno soggetta a blocchi da parte dei firewall, poiché opera su porte standard (come la 443).
*   **Uso tipico:** Molto comune per le VPN remote-access, spesso accessibili direttamente tramite un browser web (VPN "clientless") o un client leggero. Esempi: OpenVPN, Cisco AnyConnect.
