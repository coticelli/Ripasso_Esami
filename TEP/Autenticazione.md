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

---
### **Sezione 3: 🛠️ Strumenti e Metodologie**
---
### File: `GIT.md`
```markdown
# 🛠️ Software di Controllo Versione: GIT

**GIT** è un **sistema di controllo di versione distribuito (DVCS)**. È lo strumento standard de-facto per tracciare le modifiche al codice sorgente durante lo sviluppo del software.

---

## 🤔 Perché Usare un Sistema di Controllo Versione?

*   **Cronologia delle Modifiche:** Permette di avere una cronologia completa di ogni cambiamento fatto al progetto.
*   **Collaborazione:** Rende possibile a più sviluppatori di lavorare sullo stesso progetto contemporaneamente senza sovrascriversi a vicenda.
*   **Branching e Merging:** Permette di creare "rami" (branch) separati per sviluppare nuove funzionalità o correggere bug in modo isolato, per poi "fonderli" (merge) nel ramo principale quando sono pronti.
*   **Backup e Ripristino:** Ogni "clone" del repository è un backup completo del progetto. È facile tornare a una versione precedente funzionante se qualcosa va storto.

---

## 🗺️ I Concetti Fondamentali di GIT

*   **Repository (o "Repo"):** È la "cartella" che contiene tutto il progetto e la sua cronologia.
*   **Working Directory:** La cartella locale sul tuo computer dove stai lavorando ai file.
*   **Staging Area (o "Index"):** Un'area intermedia dove si preparano le modifiche prima di registrarle definitivamente. È un'istantanea dei file che vuoi includere nel prossimo "commit".
*   **Commit:** Una "fotografia" (snapshot) del progetto in un dato momento. Ogni commit ha un ID univoco e un messaggio che descrive le modifiche. È un salvataggio permanente nella cronologia locale.

---

## 🔄 Il Flusso di Lavoro di Base

1.  **Modifichi** i file nella tua **Working Directory**.
2.  **Selezioni** le modifiche che vuoi salvare e le aggiungi alla **Staging Area** con il comando `git add`.
3.  **Registri** le modifiche preparate nella staging area nel tuo repository locale, creando un **Commit** con il comando `git commit`.

---

## 🤝 Lavorare con un Repository Remoto (es. GitHub)

**GitHub, GitLab, Bitbucket** sono piattaforme di hosting che permettono di salvare i propri repository GIT su un server remoto, facilitando la collaborazione e il backup.

*   **`git clone <URL>`**: Scarica una copia completa di un repository remoto sul tuo computer.
*   **`git push`**: Invia i tuoi commit locali al repository remoto, condividendo le tue modifiche con gli altri.
*   **`git pull`**: Scarica le modifiche fatte da altri dal repository remoto e le fonde con la tua versione locale.

---

## 🌱 Branching e Merging

*   **Branch:** Un "ramo" è una linea di sviluppo indipendente. Il ramo principale è solitamente chiamato `main` o `master`.
*   **`git branch <nome-ramo>`**: Crea un nuovo branch.
*   **`git checkout <nome-ramo>`** (o `git switch`): Si sposta su un altro branch per lavorarci.
*   **Merge:** L'operazione di unire le modifiche da un branch a un altro (es. da un "feature branch" al branch `main`).
*   **`git merge <nome-ramo>`**: Fonde il branch specificato nel branch corrente.

Il flusso di lavoro basato su branch è fondamentale per gestire progetti complessi in team.
