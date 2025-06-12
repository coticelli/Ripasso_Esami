# 🐬 MySql & PhpMyAdmin

**MySQL** è uno dei sistemi di gestione di database relazionali (RDBMS) open-source più popolari al mondo. **phpMyAdmin** è un'applicazione web scritta in PHP che fornisce un'interfaccia grafica per amministrare i database MySQL.

---

## 🐬 MySQL: Il Database

*   **Caratteristiche:** È noto per la sua affidabilità, le buone prestazioni e la facilità d'uso. È la componente "M" dello stack **LAMP** (Linux, Apache, MySQL, PHP).
*   **Gestione:** Di solito viene gestito tramite la **riga di comando**, che offre il massimo controllo ma può essere complessa per i principianti.
    *   Accesso alla shell di MySQL: `mysql -u root -p`
    *   Da qui si possono eseguire tutti i comandi SQL (es. `CREATE DATABASE`, `SHOW TABLES;`, `SELECT ...`).

### Passaggi di Installazione e Sicurezza (su Linux)
1.  **Installazione:** `sudo apt-get install mysql-server`
2.  **Script di Sicurezza:** Dopo l'installazione, è fondamentale eseguire lo script di sicurezza per impostare la password di root, rimuovere gli utenti anonimi e disabilitare l'accesso remoto di root.
    `sudo mysql_secure_installation`

---

## 🐘 phpMyAdmin: L'Interfaccia Grafica

**phpMyAdmin** semplifica enormemente la gestione dei database MySQL, permettendo di eseguire la maggior parte dei compiti tramite un'interfaccia web intuitiva, senza dover scrivere comandi SQL a mano.

### Funzionalità Principali
*   **Gestione di Database e Tabelle:** Creare, rinominare, cancellare database e tabelle.
*   **Operazioni sui Dati (CRUD):** Sfogliare, cercare, inserire, modificare e cancellare righe.
*   **Gestione della Struttura:** Aggiungere, modificare ed eliminare colonne e indici.
*   **Esecuzione di Query SQL:** Fornisce una finestra per scrivere ed eseguire query SQL personalizzate.
*   **Gestione degli Utenti:** Creare nuovi utenti e gestire i loro privilegi (permessi).
*   **Import/Export:** Importare dati da file SQL o CSV e esportare database o tabelle in vari formati (SQL, CSV, PDF, etc.).

### Installazione e Configurazione
1.  **Prerequisiti:** È necessario avere uno stack LAMP (o simile) già installato: un web server (Apache), PHP e MySQL.
2.  **Installazione:** `sudo apt-get install phpmyadmin`
3.  **Configurazione:** Durante l'installazione, verrà chiesto di scegliere il web server da configurare (selezionare "apache2") e di configurare il database per phpMyAdmin.
4.  **Accesso:** Una volta installato, è accessibile tramite il browser all'indirizzo `http://indirizzo_ip_server/phpmyadmin`.
5.  **Login:** Si accede usando le credenziali di un utente MySQL (es. l'utente `root` creato durante l'installazione di MySQL).
