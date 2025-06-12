# 🛠️ Installazione Servizi: FTP, DNS, Apache

Questa guida riassume i passaggi concettuali per l'installazione e la configurazione di alcuni dei servizi di rete più comuni in un ambiente server, tipicamente basato su Linux.

---

## 📂 Installazione di un Server FTP (es. vsftpd)

**vsftpd (Very Secure FTP Daemon)** è un server FTP molto popolare e sicuro per sistemi Linux.

**Passaggi di Installazione e Configurazione:**
1.  **Installazione del Pacchetto:**
    `sudo apt-get update`
    `sudo apt-get install vsftpd`
2.  **Configurazione di Base (`/etc/vsftpd.conf`):**
    *   `anonymous_enable=NO`: Disabilita l'accesso anonimo (fortemente consigliato).
    *   `local_enable=YES`: Permette agli utenti locali del sistema di effettuare il login.
    *   `write_enable=YES`: Permette agli utenti di caricare file (scrivere).
    *   `chroot_local_user=YES`: "Ingabbia" gli utenti nella loro home directory per motivi di sicurezza, impedendo loro di navigare nel resto del file system.
3.  **Creazione di un Utente FTP:**
    *   Si crea un utente di sistema standard che verrà utilizzato per l'accesso FTP.
    `sudo adduser nome_utente_ftp`
4.  **Riavvio del Servizio:**
    `sudo systemctl restart vsftpd`
5.  **Configurazione del Firewall:**
    *   Aprire le porte necessarie (tipicamente la 21 per il controllo e un range di porte per la modalità passiva).

---

## 📖 Installazione di un Server DNS (es. BIND9)

**BIND (Berkeley Internet Name Domain)** è il software DNS più utilizzato su Internet.

**Passaggi di Installazione e Configurazione:**
1.  **Installazione del Pacchetto:**
    `sudo apt-get install bind9`
2.  **Configurazione dei File Principali:**
    *   `/etc/bind/named.conf.options`: Contiene le opzioni globali, come i server a cui inoltrare le richieste (forwarders).
    *   `/etc/bind/named.conf.local`: È qui che si definiscono le **zone** che il server gestirà.
3.  **Creazione di un File di Zona:**
    *   Si crea un file di zona per il dominio da gestire (es. `/etc/bind/db.miodominio.com`).
    *   Questo file contiene i **record DNS**, come:
        *   **SOA (Start of Authority):** Informazioni autoritative sulla zona.
        *   **NS (Name Server):** Indica i name server per il dominio.
        *   **A (Address):** Mappa un nome a un indirizzo IPv4 (es. `www` -> `1.2.3.4`).
        *   **AAAA:** Mappa un nome a un indirizzo IPv6.
        *   **CNAME (Canonical Name):** Crea un alias per un altro nome.
        *   **MX (Mail Exchange):** Indica il server di posta per il dominio.
4.  **Verifica e Riavvio:**
    *   Controllare la sintassi dei file di configurazione (`named-checkconf`, `named-checkzone`).
    *   Riavviare il servizio: `sudo systemctl restart bind9`.

---

## 🌐 Installazione di un Web Server Apache e Virtual Host

**Apache HTTP Server** è uno dei web server più diffusi al mondo. I **Virtual Host** permettono di ospitare più siti web sullo stesso server con un unico indirizzo IP.

**Passaggi di Installazione e Configurazione:**
1.  **Installazione di Apache:**
    `sudo apt-get install apache2`
2.  **Creazione della Struttura delle Directory:**
    *   Creare una cartella per ogni sito web in `/var/www/` (es. `/var/www/sito1.com`, `/var/www/sito2.org`).
    *   Creare un file `index.html` di base in ogni cartella.
3.  **Creazione dei File di Configurazione dei Virtual Host:**
    *   Creare un file di configurazione per ogni sito in `/etc/apache2/sites-available/` (es. `sito1.com.conf`).
    *   **Contenuto tipico del file:**
        ```apache
        <VirtualHost *:80>
            ServerAdmin admin@sito1.com
            ServerName sito1.com
            ServerAlias www.sito1.com
            DocumentRoot /var/www/sito1.com
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
        </VirtualHost>
        ```
4.  **Abilitazione dei Siti e Riavvio:**
    *   Abilitare i nuovi file di configurazione: `sudo a2ensite sito1.com.conf`.
    *   Ricaricare la configurazione di Apache: `sudo systemctl reload apache2`.
