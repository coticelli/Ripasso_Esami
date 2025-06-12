# 📧 I Protocolli Email: SMTP, POP3 e IMAP

Il sistema di posta elettronica si basa su un insieme di protocolli standardizzati che gestiscono l'invio, la ricezione e la gestione dei messaggi. I tre protocolli fondamentali sono SMTP, POP3 e IMAP.

---

## 📤 SMTP (Simple Mail Transfer Protocol) - Il Protocollo per l'Invio

**SMTP** è il protocollo standard utilizzato per **inviare** e **inoltrare** i messaggi di posta elettronica.

*   **Scopo Principale:** Trasferire le email da un client di posta al mail server del mittente, e da questo ai mail server dei destinatari.
*   **Funzionamento:** È un protocollo di tipo "push". Spinge i messaggi attraverso la rete.
*   **Porte comuni:**
    *   **Porta 25:** La porta standard per la comunicazione tra server.
    *   **Porta 587 (con STARTTLS):** La porta consigliata per l'invio di email da un client al proprio server (submission).
    *   **Porta 465 (SMTPS):** Una porta più vecchia per SMTP su SSL/TLS.
*   **Analogia:** Pensa a SMTP come al **servizio postale** che ritira la tua lettera e la consegna all'ufficio postale del destinatario.

---

## 📥 POP3 (Post Office Protocol version 3) - Scaricare la Posta

**POP3** è un protocollo utilizzato per **scaricare** i messaggi di posta elettronica da un server a un client locale.

*   **Scopo Principale:** Permettere a un utente di recuperare le proprie email e leggerle offline.
*   **Funzionamento:**
    1.  Il client si connette al server.
    2.  **Scarica tutti i messaggi** sul dispositivo locale (es. sul computer).
    3.  Per impostazione predefinita, **cancella i messaggi dal server** dopo averli scaricati.
*   **Vantaggi:** Semplice, consumo minimo di spazio sul server.
*   **Svantaggi:** Non è adatto per l'accesso da più dispositivi. Se scarichi le email sul PC, non le vedrai più sullo smartphone.
*   **Porte comuni:** **110** (standard), **995** (POP3S, con SSL/TLS).
*   **Analogia:** Pensa a POP3 come all'azione di **andare all'ufficio postale, ritirare tutta la corrispondenza e portarsela a casa**, svuotando la casella.

---

## 🔄 IMAP (Internet Message Access Protocol) - Sincronizzare la Posta

**IMAP** è un protocollo più moderno e flessibile per accedere ai messaggi di posta elettronica.

*   **Scopo Principale:** Permettere a un utente di **gestire le proprie email direttamente sul server**.
*   **Funzionamento:**
    1.  Il client si connette al server e visualizza una **copia sincronizzata** delle email.
    2.  **I messaggi rimangono sempre sul server**.
    3.  Qualsiasi operazione (lettura, cancellazione, spostamento in cartelle) eseguita sul client viene replicata sul server e, di conseguenza, su tutti gli altri dispositivi collegati allo stesso account.
*   **Vantaggi:** Ideale per l'accesso da più dispositivi (PC, smartphone, tablet). Supporta la gestione di cartelle sul server.
*   **Svantaggi:** Richiede una connessione a Internet costante e più spazio di archiviazione sul server.
*   **Porte comuni:** **143** (standard), **993** (IMAPS, con SSL/TLS).
*   **Analogia:** Pensa a IMAP come alla gestione della tua posta **direttamente nella casella postale**, organizzandola in cartelle senza mai portarla via.
