# 📡 Wireless e Reti Mobili

Le tecnologie wireless permettono la comunicazione tra dispositivi senza l'uso di cavi fisici, utilizzando le onde radio. Questa sezione copre le reti Wi-Fi (WLAN) e le reti cellulari.

---

## 🏛️ Topologie di Rete Wireless

*   **Infrastruttura (Infrastructure Mode):** È la topologia più comune. I dispositivi wireless (client) si collegano a un punto centrale chiamato **Access Point (AP)**, che a sua volta è collegato alla rete cablata. L'AP gestisce la comunicazione tra i client.
*   **Ad-Hoc (o Peer-to-Peer):** I dispositivi si collegano direttamente tra loro senza un Access Point. È una rete decentralizzata, usata per connessioni temporanee (es. Wi-Fi Direct).

---

## 📱 La Rete Cellulare

La rete cellulare fornisce connettività wireless su un'area geografica molto vasta.
*   **Architettura:** Il territorio è suddiviso in aree geografiche chiamate **celle**.
*   **Componenti:**
    *   **Stazione Radio Base (BTS/NodeB):** Una torre con antenne che serve una singola cella.
    *   **Dispositivo Mobile:** Comunica con la stazione radio base più vicina.
    *   **Handover:** Il processo che permette a un dispositivo mobile di passare senza interruzioni da una cella all'altra mentre si muove.
*   **Evoluzione (Generazioni):** 1G (analogico), 2G (digitale, SMS), 3G (internet mobile), 4G/LTE (banda larga mobile), **5G** (altissima velocità, bassissima latenza, supporto per IoT).

---

## 🌐 Reti Wi-Fi (WLAN - Standard IEEE 802.11)

Lo standard **IEEE 802.11** definisce le specifiche per le reti locali wireless (Wi-Fi). Esistono diverse versioni (`a`, `b`, `g`, `n`, `ac`, `ax`/Wi-Fi 6) che operano su diverse bande di frequenza (2.4 GHz e 5 GHz) e offrono velocità crescenti.

### Componenti di una WLAN
*   **Stazione (STA):** Qualsiasi dispositivo con una scheda di rete wireless (PC, smartphone).
*   **Access Point (AP):** Il dispositivo che crea la rete wireless e fa da ponte con la rete cablata.
*   **SSID (Service Set Identifier):** Il **nome della rete Wi-Fi** che viene trasmesso dall'Access Point per permettere ai client di identificarla e connettersi.

---

## 🔒 Autenticazione e Sicurezza Wi-Fi

La sicurezza è cruciale nelle reti wireless, poiché chiunque nel raggio d'azione può intercettare il segnale.

### 1. WEP (Wired Equivalent Privacy)
*   È il primo protocollo di sicurezza, introdotto con lo standard 802.11.
*   **Stato:** **Obsoleto e insicuro**. Presenta gravi vulnerabilità crittografiche che lo rendono facilmente "craccabile" in pochi minuti. **Non deve mai essere usato**.

### 2. WPA (Wi-Fi Protected Access)
*   Creato come soluzione temporanea per sostituire WEP.
*   **Miglioramenti:** Introduce il protocollo **TKIP (Temporal Key Integrity Protocol)**, che cambia dinamicamente le chiavi di crittografia, rendendo gli attacchi molto più difficili.

### 3. WPA2 (Wi-Fi Protected Access II)
*   È stato lo standard di sicurezza per molti anni e ancora oggi è considerato robusto.
*   **Miglioramenti:** Sostituisce TKIP con il protocollo **CCMP**, basato sull'algoritmo di crittografia **AES (Advanced Encryption Standard)**, che è molto più sicuro.
*   **Modalità:**
    *   **WPA2-Personal (o WPA2-PSK):** Usa una **Pre-Shared Key** (la password del Wi-Fi) che è la stessa per tutti gli utenti. Adatta per reti domestiche e piccoli uffici.
    *   **WPA2-Enterprise:** Non usa una password condivisa. Ogni utente si autentica individualmente tramite un server centrale (solitamente un server **RADIUS**), usando credenziali uniche. Adatta per reti aziendali di grandi dimensioni.

### 4. WPA3
*   È lo standard più recente. Offre una sicurezza ancora maggiore, specialmente contro gli attacchi di "brute-force" per indovinare la password.
