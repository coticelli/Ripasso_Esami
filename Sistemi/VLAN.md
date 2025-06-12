# 🌐 VLAN (Virtual Local Area Network)

Una **VLAN** è una rete locale **logica** creata all'interno di una rete locale fisica. Permette di raggruppare un insieme di dispositivi, indipendentemente dalla loro posizione fisica, come se si trovassero sullo stesso segmento di rete (dominio di broadcast).

---

## 🤔 Perché usare le VLAN?

Le VLAN offrono diversi vantaggi rispetto a una singola, grande LAN (flat network):

1.  **Sicurezza 🛡️:** Isola i gruppi di utenti. Il traffico di una VLAN non può raggiungere un'altra VLAN senza passare attraverso un dispositivo di livello 3 (router o switch multilayer). Es: si può creare una VLAN per gli ospiti separata da quella aziendale.
2.  **Prestazioni 🚀:** Riduce il **dominio di broadcast**. Il traffico di broadcast (es. richieste ARP), generato da un dispositivo, viene confinato solo all'interno della sua VLAN, riducendo il traffico non necessario e migliorando le prestazioni generali della rete.
3.  **Flessibilità e Scalabilità 地理:** Gli host possono essere raggruppati logicamente per funzione o dipartimento, anche se si trovano in piani o edifici diversi. Spostare un utente in un altro gruppo è una semplice configurazione software, senza bisogno di ricablare.
4.  **Gestione Semplificata 🛠️:** Semplifica l'amministrazione della rete e l'applicazione di policy di sicurezza specifiche per ogni gruppo.

---

## 🏷️ Tipi di Assegnazione VLAN

### 1. VLAN Port-Based (Static VLAN)
*   È il metodo più comune.
*   **Come funziona:** Ogni porta di uno switch viene assegnata manualmente a una specifica VLAN.
*   **Vantaggio:** Semplice da configurare e sicura.
*   **Svantaggio:** Poco flessibile. Se un dispositivo si sposta su un'altra porta, bisogna riconfigurare la porta per la VLAN corretta.

### 2. VLAN Tagged (IEEE 802.1Q)
*   Questo standard permette di estendere le VLAN su più switch.
*   **Come funziona:**
    *   **Porta di Accesso (Access Port):** Appartiene a una sola VLAN. I frame che entrano o escono da questa porta sono standard (non "taggati").
    *   **Porta di Trunk (Trunk Port):** Può trasportare il traffico di **multiple VLAN** tra due switch. Per fare ciò, ogni frame che passa attraverso un trunk viene "etichettato" (tagged) con un **VLAN ID**, un numero che identifica la VLAN di appartenenza. L'altro switch legge il tag per sapere a quale VLAN inoltrare il frame.

---

## 🤝 Protocollo Cisco VTP (VLAN Trunking Protocol)

**VTP** è un protocollo proprietario Cisco che semplifica la gestione delle VLAN in una rete di grandi dimensioni con molti switch.

*   **Scopo:** Permettere a un amministratore di configurare le VLAN su un unico switch (il **server VTP**) e far sì che queste informazioni vengano propagate automaticamente a tutti gli altri switch nella stessa rete (i **client VTP**).
*   **Vantaggi:**
    *   Riduce il rischio di errori di configurazione.
    *   Garantisce la coerenza della configurazione VLAN in tutta la rete.
    *   Semplifica l'aggiunta, la modifica e la rimozione di VLAN.

**Modalità operative di uno switch in VTP:**
*   **Server:** Può creare, modificare ed eliminare VLAN e propaga queste informazioni.
*   **Client:** Riceve le informazioni dal server e aggiorna la propria configurazione, ma non può modificarle localmente.
*   **Transparent:** Non partecipa al VTP, ma inoltra gli annunci VTP ricevuti sulle sue porte di trunk. Gestisce le proprie VLAN localmente.
