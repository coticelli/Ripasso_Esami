# 🛠️ Software di Controllo Versione (Version Control System - VCS)

Un **sistema di controllo di versione** è un software che traccia e gestisce le modifiche a un insieme di file nel tempo. Permette di richiamare versioni specifiche, confrontare i cambiamenti e collaborare su un progetto senza interferire con il lavoro degli altri.

È uno strumento **fondamentale** per lo sviluppo software moderno.

---

## 🤔 Perché è Indispensabile?

*   **Cronologia Completa 📜:** Mantiene una registrazione storica di ogni singola modifica, permettendo di capire chi ha cambiato cosa, quando e perché.
*   **Collaborazione in Team 🤝:** Permette a più sviluppatori di lavorare sullo stesso codice contemporaneamente. Il VCS aiuta a gestire e fondere (merge) le modifiche provenienti da persone diverse.
*   **Branching e Sperimentazione 🌱:** Si possono creare "rami" (branch) isolati per sviluppare nuove funzionalità o correggere bug senza intaccare la versione stabile del codice. Se un'idea non funziona, si può semplicemente abbandonare il branch.
*   **Backup e Ripristino 💾:** Funziona come un potente sistema di backup. Se viene introdotto un errore, è facile tornare a una versione precedente e funzionante del codice.

---

## 📈 Tipi di Sistemi di Controllo Versione

### 1. Sistemi Centralizzati (CVCS)
*   **Come funzionano:** Esiste un **unico server centrale** che contiene tutto il repository del progetto. Gli sviluppatori effettuano un "checkout" dei file su cui devono lavorare e poi un "commit" per salvare le modifiche sul server centrale.
*   **Esempi:** Subversion (SVN), CVS.
*   **Svantaggi:**
    *   **Single Point of Failure:** Se il server centrale è offline, nessuno può collaborare o salvare le proprie versioni.
    *   Le operazioni (commit, diff) richiedono una connessione di rete.

### 2. Sistemi Distribuiti (DVCS) - Il Modello Moderno
*   **Come funzionano:** Ogni sviluppatore ha sul proprio computer una **copia completa (un "clone") del repository**, inclusa tutta la sua cronologia.
*   **Esempio principale:** **GIT**. Altri sono Mercurial e Bazaar.
*   **Vantaggi:**
    *   **Lavoro Offline:** La maggior parte delle operazioni (commit, creazione di branch, visualizzazione della cronologia) sono locali e velocissime.
    *   **Maggiore Flessibilità:** Permette flussi di lavoro più complessi e non lineari.
    *   **Nessun Single Point of Failure:** Se il server remoto (es. GitHub) non è disponibile, si può continuare a lavorare localmente. Ogni clone è un backup completo.

---

## 🦊 GIT: Il Re dei DVCS

**GIT** è oggi lo standard de-facto per il controllo di versione.

**Concetti chiave di GIT:**
*   **Repository:** La "cartella" del progetto con tutta la cronologia.
*   **Commit:** Una "fotografia" del progetto in un dato momento.
*   **Branch:** Una linea di sviluppo indipendente.
*   **Merge:** L'unione di due branch.
*   **Remote:** Un repository remoto (es. su GitHub, GitLab) usato per la sincronizzazione e la collaborazione.

L'uso di un VCS come GIT è una competenza non negoziabile per qualsiasi sviluppatore software.
