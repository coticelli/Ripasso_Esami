# 📦 Database "Embedded": SQL Server Compact e SQLite

**SQL Server Compact (SQL CE)** e **SQLite** sono due esempi di **database "embedded"** (o "incorporati"). A differenza dei database server tradizionali (come SQL Server o MySQL) che richiedono un processo server separato, i database embedded sono **librerie leggere** che vengono integrate direttamente all'interno dell'applicazione che li utilizza.

---

## 🤔 Caratteristiche Comuni dei Database Embedded

*   **Serverless:** Non c'è bisogno di un processo server in esecuzione. Il motore del database è una libreria `.dll` o `.so` che fa parte dell'applicazione.
*   **Self-Contained (Autocontenuto):** L'intero database (tabelle, indici, dati) è memorizzato in un **singolo file** su disco. Questo lo rende estremamente portatile.
*   **Zero-Configuration:** Non richiedono installazione o configurazione complessa. Basta includere la libreria e creare il file del database.
*   **Transazionali (ACID):** Supportano le transazioni, garantendo l'integrità dei dati (Atomic, Consistent, Isolated, Durable).
*   **Basati su SQL:** Utilizzano una versione standard o leggermente semplificata del linguaggio SQL per l'interrogazione e la manipolazione dei dati.

---

## 🚀 SQLite: Il Gigante Invisibile

**SQLite** è il motore di database embedded più diffuso al mondo. È gratuito, open-source e incredibilmente affidabile.

### Dove si trova?
*   📱 **Applicazioni mobili:** È il database di default su **Android** e **iOS**.
*   🌐 **Browser web:** Usato da Chrome, Firefox e Safari per memorizzare cronologia, segnalibri, etc.
*   💻 **Applicazioni desktop:** Usato da un'enorme quantità di software, da Skype a Dropbox.
*   ✈️ **Sistemi embedded:** Aerei, automobili e dispositivi IoT.

### Punti di forza di SQLite:
*   **Piccolissimo e velocissimo.**
*   **Estremamente affidabile e robusto.**
*   **Cross-platform:** Funziona su quasi ogni sistema operativo.
*   **Pubblico dominio:** Completamente libero da usare per qualsiasi scopo.

---

## 🪟 SQL Server Compact (SQL CE)

**SQL Server Compact** è la versione embedded del database di Microsoft. Era popolare per lo sviluppo di applicazioni desktop e mobili in ambiente Windows, specialmente con .NET.

### Caratteristiche principali:
*   **Integrazione con Visual Studio:** Perfettamente integrato con l'ambiente di sviluppo di Microsoft.
*   **Sintassi T-SQL:** Usa una sintassi molto simile a quella di SQL Server.
*   **Legacy:** È considerato un prodotto **legacy (obsoleto)** da Microsoft, che ora incoraggia l'uso di altre soluzioni come SQLite o SQL Server Express LocalDB per le nuove applicazioni.

**Conclusione:** Per lo sviluppo di nuove applicazioni che richiedono un database locale e leggero, **SQLite è oggi la scelta standard e raccomandata** grazie alla sua portabilità, affidabilità e al vasto supporto della comunità.
