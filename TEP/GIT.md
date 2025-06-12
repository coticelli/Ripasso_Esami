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
