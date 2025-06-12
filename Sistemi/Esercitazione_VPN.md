# 🛡️ Esercitazione VPN (Site-to-Site con IPsec)

Questa esercitazione riassume i passaggi logici per configurare una **VPN Site-to-Site** utilizzando il protocollo **IPsec** tra due router (es. Cisco), per connettere in modo sicuro due reti locali (LAN) remote attraverso Internet.

**Scenario:**
*   **Sede A:** LAN `192.168.1.0/24`
*   **Sede B:** LAN `192.168.2.0/24`
*   Obiettivo: Permettere a un PC nella Sede A di comunicare con un PC nella Sede B in modo sicuro.

---

## 🏗️ Fasi della Configurazione IPsec (Protocollo IKE)

La configurazione di una VPN IPsec si articola in due fasi principali, gestite dal protocollo **IKE (Internet Key Exchange)**.

### Fase 1: Creazione del Tunnel di Gestione (IKE Phase 1)

*   **Scopo:** Creare un canale di comunicazione sicuro e autenticato tra i due router (i "peer" della VPN) per negoziare i parametri della VPN vera e propria. Questo canale è chiamato **Security Association ISAKMP (o IKE SA)**.
*   **Passaggi di Configurazione:**
    1.  **Creare una policy ISAKMP:** Si definiscono i parametri per proteggere il canale di gestione.
        *   **`authentication pre-share`**: Metodo di autenticazione. Si usa una "pre-shared key", una password segreta condivisa tra i due router.
        *   **`encryption aes`**: Algoritmo di crittografia (es. AES).
        *   **`hash sha`**: Algoritmo di hashing (es. SHA).
        *   **`group 2`**: Gruppo Diffie-Hellman per lo scambio sicuro delle chiavi.
        *   **`lifetime 86400`**: Durata del tunnel di gestione (in secondi).
    2.  **Configurare la Pre-Shared Key:** Si definisce la password segreta e l'indirizzo IP del peer remoto.
        `crypto isakmp key MIA_CHIAVE_SEGRETA address IP_ROUTER_REMOTA`

---

## 🔒 Fase 2: Creazione del Tunnel Dati (IKE Phase 2)

*   **Scopo:** Utilizzare il tunnel sicuro creato nella Fase 1 per negoziare i parametri del tunnel che proteggerà i **dati effettivi degli utenti** (il traffico tra le due LAN). Questo tunnel è chiamato **IPsec SA**.
*   **Passaggi di Configurazione:**
    1.  **Definire il "traffico interessante" con un'Access List (ACL):** Si crea una ACL per specificare quale traffico deve essere crittografato e inviato attraverso la VPN.
        *   **Esempio (sul router della Sede A):**
            `access-list 101 permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255`
            (Permette il traffico IP dalla LAN locale `192.168.1.0` verso la LAN remota `192.168.2.0`).
    2.  **Creare un "Transform Set":** Si definiscono gli algoritmi di crittografia (es. `esp-aes`) e di hashing (es. `esp-sha-hmac`) che verranno usati per proteggere i dati.
        `crypto ipsec transform-set MIO_TRANSFORM_SET esp-aes esp-sha-hmac`
    3.  **Creare una "Crypto Map":** È l'elemento che tiene insieme tutti i pezzi:
        *   Associa l'indirizzo IP del peer remoto.
        *   Associa il transform set definito.
        *   Associa la ACL che definisce il traffico interessante.
        `crypto map MIA_CRYPTO_MAP 10 ipsec-isakmp`
        ` set peer IP_ROUTER_REMOTA`
        ` set transform-set MIO_TRANSFORM_SET`
        ` match address 101`

---

## 🚀 Applicazione della Configurazione

*   **Ultimo passaggio:** Applicare la Crypto Map all'interfaccia del router che si affaccia su Internet (l'interfaccia esterna).
    ```bash
    interface GigabitEthernet0/0
     crypto map MIA_CRYPTO_MAP
    ```

Una volta completata la configurazione su entrambi i router, il tunnel VPN si attiverà non appena verrà generato del "traffico interessante" (es. un ping da un PC della Sede A a un PC della Sede B).
