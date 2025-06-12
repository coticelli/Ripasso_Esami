# 🛡️ HTTP Accesso Protetto

L'accesso protetto a risorse web tramite HTTP può essere implementato a diversi livelli. I due meccanismi più comuni gestiti direttamente dal web server (come Apache) sono l'**autenticazione di base** e la configurazione di **HTTPS**.

---

## 1. Autenticazione HTTP di Base (Basic Auth)

*   **Cos'è:** Un meccanismo semplice che richiede all'utente di fornire un nome utente e una password per accedere a una directory o a un intero sito.
*   **Come funziona:**
    1.  Il browser richiede una risorsa protetta.
    2.  Il server risponde con un codice di stato `401 Unauthorized`.
    3.  Il browser mostra una finestra di dialogo di login nativa.
    4.  L'utente inserisce le credenziali.
    5.  Il browser le invia al server (codificate in Base64) in un header HTTP `Authorization`.
*   **Svantaggio principale:** Le credenziali, anche se codificate, viaggiano in **testo quasi in chiaro**. La codifica Base64 non è crittografia e può essere facilmente decodificata. **È fondamentale usare Basic Auth solo su una connessione HTTPS.**

### Configurazione su Apache
1.  **Creare un file delle password:**
    *   Si usa il comando `htpasswd` per creare un file che conterrà gli username e le password hashate.
    ```bash
    # Crea un nuovo file per il primo utente
    sudo htpasswd -c /etc/apache2/.htpasswd nome_utente
    # Aggiunge altri utenti allo stesso file
    sudo htpasswd /etc/apache2/.htpasswd altro_utente
    ```
2.  **Modificare la configurazione del sito:**
    *   Nel file di configurazione del Virtual Host o in un file `.htaccess`, si aggiunge una direttiva `<Directory>` per specificare la cartella da proteggere.
    ```apache
    <Directory /var/www/miosito/privato>
        AuthType Basic
        AuthName "Area Riservata"
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
    </Directory>
    ```

---

## 2. Configurazione HTTPS su Apache

Configurare HTTPS significa abilitare la crittografia SSL/TLS per il proprio sito web. Questo richiede una chiave privata e un certificato digitale (autofirmato o emesso da una CA).

### Prerequisiti
*   Avere a disposizione i file della **chiave privata** (`server.key`) e del **certificato pubblico** (`server.crt`).
*   Il modulo SSL di Apache deve essere abilitato: `sudo a2enmod ssl`.

### Passaggi di Configurazione
1.  **Copiare i file del certificato:** Spostare i file `.key` e `.crt` in una directory sicura accessibile da Apache (es. `/etc/ssl/private/` e `/etc/ssl/certs/`).
2.  **Configurare il Virtual Host per la porta 443:**
    *   Creare o modificare un file di configurazione del sito per gestire il traffico sulla porta 443 (la porta standard di HTTPS).
    ```apache
    <VirtualHost *:443>
        ServerName www.miosito.com
        DocumentRoot /var/www/miosito

        # Abilita il motore SSL
        SSLEngine on

        # Specifica i percorsi del certificato e della chiave
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key

        # ... altre configurazioni ...
    </VirtualHost>
    ```
3.  **Abilitare il sito e riavviare Apache:**
    `sudo a2ensite nome-sito-ssl.conf`
    `sudo systemctl restart apache2`
4.  **(Opzionale ma consigliato) Reindirizzare HTTP a HTTPS:** Configurare il Virtual Host sulla porta 80 per reindirizzare automaticamente tutto il traffico verso la versione HTTPS.
