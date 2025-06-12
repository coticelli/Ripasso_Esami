# 🔥 Configurazione ACL e Firewall

**Access Control Lists (ACL)** e **Firewall** sono strumenti fondamentali per il controllo del traffico e la sicurezza di una rete. Sebbene correlati, operano con logiche e capacità diverse.

---

## 📝 ACL (Access Control List)

*   **Cos'è:** Una ACL è una sequenza di **regole (permit/deny)** applicata a un'interfaccia di un router o di uno switch multilayer. Funziona come un filtro per pacchetti.
*   **Come funziona:**
    *   Quando un pacchetto arriva su un'interfaccia con una ACL applicata, il router lo confronta con le regole della lista, **in ordine sequenziale**.
    *   Appena viene trovata una corrispondenza (`match`), l'azione specificata (`permit` o `deny`) viene eseguita e il controllo della lista termina.
    *   Se nessuna regola corrisponde, il pacchetto viene scartato a causa di una **regola implicita di "deny all"** presente alla fine di ogni ACL.

### Tipi di ACL (su router Cisco)

*   **ACL Standard (numeri 1-99):**
    *   Filtrano il traffico basandosi **solo** sull'**indirizzo IP di origine**.
    *   Sono semplici ma poco granulari.
    *   **Regola d'oro:** Vanno posizionate il più vicino possibile alla destinazione del traffico.
    *   **Esempio:** Bloccare tutto il traffico proveniente dalla rete `10.0.0.0/8`.
        ```bash
        access-list 10 deny 10.0.0.0 0.255.255.255
        access-list 10 permit any
        ```

*   **ACL Estese (numeri 100-199):**
    *   Offrono un controllo molto più granulare. Possono filtrare basandosi su:
        *   **Indirizzo IP di origine E di destinazione**.
        *   **Protocollo** di livello 4 (TCP, UDP, ICMP...).
        *   **Porte** di origine e di destinazione (per TCP/UDP).
    *   **Regola d'oro:** Vanno posizionate il più vicino possibile alla sorgente del traffico.
    *   **Esempio:** Permettere solo il traffico web (HTTP) dalla rete A alla rete B.
        ```bash
        access-list 101 permit tcp 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255 eq 80
        ```

### Applicazione di un'ACL a un'interfaccia
```bash
interface GigabitEthernet0/1
 ! Applica l'ACL 101 al traffico in entrata su questa interfaccia
 ip access-group 101 in
```

---

## 🧱 Firewall

*   **Cos'è:** Un firewall è un dispositivo di sicurezza dedicato (hardware o software) che agisce come barriera tra due reti, tipicamente una rete interna fidata e una esterna non fidata (Internet).
*   **Oltre le ACL:** Mentre le ACL sono "stateless" (non tengono traccia delle connessioni), i firewall moderni sono **"stateful"**.

### Stateful Packet Inspection (SPI)
*   È la caratteristica chiave dei firewall moderni.
*   **Come funziona:** Il firewall mantiene una **tabella dello stato** di tutte le connessioni TCP attive che lo attraversano.
*   **Logica di funzionamento:**
    1.  Si creano regole per permettere il traffico **in uscita** dalla rete interna verso Internet (es. permetti le richieste web sulla porta 80).
    2.  Quando un utente interno avvia una connessione verso un sito web, il firewall registra questa connessione nella sua tabella di stato.
    3.  Il traffico di **risposta** proveniente dal sito web viene automaticamente permesso dal firewall, perché lo riconosce come parte di una connessione legittima già stabilita.
*   **Vantaggio:** È molto più sicuro. Permette tutto il traffico di risposta legittimo, bloccando al contempo qualsiasi tentativo di connessione non richiesto proveniente dall'esterno.

**In sintesi:** Le ACL sono filtri statici basati su regole, mentre un firewall stateful offre una protezione dinamica e consapevole del contesto delle connessioni.
