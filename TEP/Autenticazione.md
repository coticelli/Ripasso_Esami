# 🔒 Il Problema dell'Autenticazione: JWT, Cookie e Sessioni

Nelle applicazioni web, il protocollo HTTP è **stateless** (senza stato), il che significa che ogni richiesta è indipendente dalle altre. L'autenticazione è il processo che permette al server di "ricordare" chi è un utente tra una richiesta e l'altra.

---

## 🍪 Gestione Classica: Cookie e Sessioni

Questo è l'approccio tradizionale, spesso usato in applicazioni web "monolitiche" (come quelle basate su Razor Pages o MVC).

### Come funziona
1.  **Login:** L'utente invia username e password.
2.  **Verifica:** Il server controlla le credenziali.
3.  **Creazione della Sessione:** Se le credenziali sono valide, il server crea una **sessione** (un'area di memoria sul server associata a quell'utente) e genera un **ID di sessione univoco**.
4.  **Invio del Cookie:** Il server invia questo ID di sessione al browser dell'utente, memorizzandolo in un **cookie**.
5.  **Richieste Successive:** Ad ogni richiesta successiva, il browser invia automaticamente il cookie. Il server usa l'ID di sessione per recuperare i dati dell'utente memorizzati sul server e lo considera autenticato.

**Vantaggi:** Semplice da implementare con i framework moderni. I dati sensibili rimangono sul server.
**Svantaggi:** Richiede memoria sul server per ogni utente attivo. Non scala bene in architetture distribuite o con microservizi.

---

## ✨ Approccio Moderno per API e SPA: JWT

**JWT (JSON Web Token)** è uno standard aperto (RFC 7519) per creare "token di accesso" che permettono a un'applicazione di trasmettere in modo sicuro le informazioni sull'identità di un utente. È l'approccio preferito per le **API RESTful** e le **Single-Page Applications (SPA)**.

### Struttura di un JWT
Un JWT è una stringa composta da tre parti separate da un punto, codificate in Base64: `Header.Payload.Signature`.

1.  **Header (Intestazione):** Contiene i metadati del token, come il tipo (`JWT`) e l'algoritmo di firma (`HS256`, `RS256`).
2.  **Payload (Dati):** Contiene i "claims", cioè le informazioni sull'utente (come `sub` per l'ID utente, `name` per il nome, `exp` per la data di scadenza) e altri dati. **Attenzione:** il payload è solo codificato, non crittografato, quindi non dovrebbe contenere dati sensibili.
3.  **Signature (Firma):** È la parte che garantisce l'autenticità del token. Viene creata firmando l'header e il payload con una **chiave segreta** (nota solo al server).

### Flusso di Autenticazione con JWT
1.  **Login:** L'utente invia username e password.
2.  **Verifica e Creazione del Token:** Il server verifica le credenziali e, se corrette, crea un JWT firmato con la sua chiave segreta.
3.  **Invio del Token:** Il server invia il JWT al client.
4.  **Memorizzazione sul Client:** Il client memorizza il token (solitamente nel `localStorage` o `sessionStorage` del browser).
5.  **Richieste Successive:** Per ogni richiesta a un'API protetta, il client include il JWT nell'**header HTTP `Authorization`**, usando lo schema `Bearer`.
    `Authorization: Bearer <il_tuo_jwt>`
6.  **Verifica sul Server:** Il server riceve il token, ne verifica la firma usando la propria chiave segreta e, se la firma è valida, considera l'utente autenticato e processa la richiesta.

**Vantaggi:**
*   **Stateless:** Il server non ha bisogno di memorizzare lo stato della sessione. Perfetto per la scalabilità.
*   **Portabilità:** Può essere usato tra domini e servizi diversi (microservizi).
