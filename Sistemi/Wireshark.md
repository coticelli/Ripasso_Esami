# 🦈 Analisi del Traffico con Wireshark

**Wireshark** è un analizzatore di protocolli di rete (o "packet sniffer") open-source e gratuito. È uno strumento potentissimo che permette di **catturare e ispezionare** il traffico dati che passa attraverso un'interfaccia di rete in tempo reale.

---

## 🤔 A Cosa Serve Wireshark?

*   **Didattica e Apprendimento:** È uno strumento insostituibile per vedere "dal vivo" come funzionano i protocolli di rete (TCP, UDP, IP, HTTP, DNS, etc.) e per capire la struttura dei pacchetti.
*   **Troubleshooting di Rete:** Aiuta gli amministratori di rete a diagnosticare problemi di connettività, lentezza o errori di comunicazione.
*   **Analisi di Sicurezza:** Permette di individuare traffico sospetto, tentativi di intrusione o attività malware.

---

## 🎨 L'Interfaccia di Wireshark

L'interfaccia principale è divisa in tre pannelli:

1.  **Packet List Pane (Lista dei Pacchetti):**
    *   È il pannello superiore. Mostra un elenco di tutti i pacchetti catturati in ordine cronologico.
    *   Per ogni pacchetto, visualizza informazioni riassuntive come il numero, l'ora, l'IP sorgente e destinazione, il protocollo e una breve descrizione.

2.  **Packet Details Pane (Dettagli del Pacchetto):**
    *   È il pannello centrale. Mostra una vista dettagliata e gerarchica del pacchetto selezionato nella lista.
    *   Permette di espandere e analizzare ogni singolo strato del modello di rete (dal livello fisico fino al livello applicazione), visualizzando tutti i campi e i valori di ogni protocollo.

3.  **Packet Bytes Pane (Byte del Pacchetto):**
    *   È il pannello inferiore. Mostra il contenuto grezzo del pacchetto in formato esadecimale e ASCII. Evidenzia la parte di dati corrispondente al campo selezionato nel pannello dei dettagli.

---

## ⚙️ Funzionalità Essenziali

### 1. Cattura del Traffico
*   Per iniziare, si seleziona un'interfaccia di rete (es. "Wi-Fi" o "Ethernet") e si avvia la cattura. Wireshark inizierà a registrare tutto il traffico che passa su quell'interfaccia.

### 2. Filtri
La cattura del traffico può generare migliaia di pacchetti in pochi secondi. I filtri sono essenziali per isolare solo il traffico di interesse.
*   **Capture Filters:** Vengono applicati **prima** di avviare la cattura. Catturano solo i pacchetti che corrispondono al filtro, riducendo la dimensione del file di cattura. (Es: `host 192.168.1.1`).
*   **Display Filters:** Vengono applicati **dopo** la cattura, per nascondere temporaneamente i pacchetti non rilevanti dalla visualizzazione. Sono molto più flessibili e potenti.
    *   `ip.addr == 192.168.1.1` (mostra traffico da o verso questo IP)
    *   `http` (mostra solo il traffico HTTP)
    *   `tcp.port == 80` (mostra traffico sulla porta 80)
    *   `dns` (mostra solo le richieste e risposte DNS)

### 3. "Follow TCP Stream"
*   Questa funzione è estremamente utile per analizzare conversazioni basate su TCP (come HTTP).
*   Facendo clic destro su un pacchetto TCP e selezionando "Follow > TCP Stream", Wireshark ricostruisce e mostra l'intera conversazione tra client e server in un formato leggibile, come una chat.
