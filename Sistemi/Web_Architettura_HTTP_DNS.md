# 📂 Il Protocollo FTP (File Transfer Protocol)

**FTP** è un protocollo standard del livello applicativo progettato specificamente per il **trasferimento di file** tra un client e un server su una rete TCP/IP.

---

## 🏛️ Architettura a Due Canali

La caratteristica distintiva di FTP è che utilizza **due connessioni TCP separate** per funzionare:

### 1. Canale di Controllo (Control Connection)
*   **Porta:** Il server ascolta sulla porta **21**.
*   **Scopo:** Gestire i **comandi** e le risposte tra client e server.
*   **Funzionamento:** Rimane aperta per tutta la durata della sessione FTP. Qui passano comandi come `USER` (username), `PASS` (password), `LIST` (elenca file), `RETR` (recupera file), `STOR` (memorizza file).

### 2. Canale Dati (Data Connection)
*   **Porta:** Porta **20** (in modo attivo) o una porta dinamica (in modo passivo).
*   **Scopo:** Trasferire i **dati effettivi** dei file o l'output dei comandi di elenco (`LIST`).
*   **Funzionamento:** Viene aperta e chiusa per ogni singolo trasferimento di file.

---

## ↔️ Modalità di Connessione: Attiva vs. Passiva

Il modo in cui viene stabilito il Canale Dati definisce le due modalità operative di FTP.

### Modalità Attiva (Active Mode)
1.  Il client si connette dalla sua porta `N` alla porta `21` del server (Canale di Controllo).
2.  Il client comunica al server su quale porta `N+1` è in ascolto.
3.  È il **server** che avvia la connessione dalla sua porta `20` verso la porta `N+1` del client per stabilire il Canale Dati.
*   **Problema:** Spesso bloccata dai firewall lato client, perché è una connessione in entrata non richiesta.

### Modalità Passiva (Passive Mode) - La più comune
1.  Il client si connette dalla sua porta `N` alla porta `21` del server (Canale di Controllo).
2.  Il client invia il comando `PASV`.
3.  Il server risponde indicando una porta dinamica `P` su cui è in ascolto.
4.  È il **client** che avvia la connessione dalla sua porta `M` verso la porta `P` del server per stabilire il Canale Dati.
*   **Vantaggio:** Più "firewall-friendly", perché entrambe le connessioni vengono avviate dal client.

---

## 🔒 Sicurezza di FTP

*   FTP standard è **intrinsecamente insicuro**: sia le credenziali (username e password) sia i dati viaggiano in **testo in chiaro** sulla rete e possono essere facilmente intercettati.
*   **Alternative Sicure:**
    *   **FTPS (FTP over SSL/TLS):** Aggiunge un livello di crittografia SSL/TLS a FTP.
    *   **SFTP (SSH File Transfer Protocol):** Non è FTP su SSH, ma un protocollo completamente diverso che utilizza il canale sicuro di SSH per il trasferimento di file. È considerato più moderno e sicuro.
