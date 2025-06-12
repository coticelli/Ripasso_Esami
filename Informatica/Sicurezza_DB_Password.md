# 🛡️ Sicurezza del Database: Salted Password Hashing

Memorizzare le password degli utenti in chiaro (plain text) in un database è una delle pratiche di sicurezza più gravi e pericolose. Se il database viene compromesso, tutte le password degli utenti sono immediatamente esposte.

Per proteggere le password, si usa una tecnica chiamata **hashing**, resa ancora più sicura dall'aggiunta di un **salt**.

---

## 🎲 Cos'è l'Hashing?

*   **Definizione:** Un **algoritmo di hash** (come SHA-256, BCrypt, Argon2) è una funzione matematica che prende un input di qualsiasi lunghezza (la password) e produce un output di lunghezza fissa, chiamato **hash** o **digest**.
*   **Caratteristiche Fondamentali:**
    1.  **Unidirezionale (One-Way):** È computazionalmente impossibile risalire dalla stringa di hash alla password originale. Non è crittografia, non si può "decifrare".
    2.  **Deterministico:** Lo stesso input produrrà sempre lo stesso output.
    3.  **Resistente alle collisioni:** È estremamente improbabile che due input diversi producano lo stesso hash.

**Processo di base:**
1.  L'utente inserisce la password.
2.  L'applicazione calcola l'hash della password.
3.  L'hash (e non la password) viene memorizzato nel database.
4.  Al login, l'utente inserisce di nuovo la password. L'applicazione ne calcola l'hash e lo confronta con quello salvato nel database. Se corrispondono, l'accesso è concesso.

---

##🧂 Cos'è il "Salting"? (Salted Hashing)

*   **Il Problema dell'Hashing Semplice:** Se due utenti scelgono la stessa password (es. "password123"), avranno lo stesso hash. Un malintenzionato potrebbe usare delle **"rainbow tables"** (tabelle precalcolate di hash per le password più comuni) per scoprire rapidamente le password.
*   **La Soluzione: il Salt:** Un **salt** è una stringa di dati casuale e unica che viene generata per ogni utente.
    *   **Processo di Salted Hashing:**
        1.  Quando un utente si registra, si genera un salt casuale.
        2.  Questo salt viene **aggiunto** alla password in chiaro.
        3.  Si calcola l'hash della combinazione `(password + salt)`.
        4.  Nel database vengono memorizzati sia l'**hash** risultante sia il **salt** unico di quell'utente.

**Perché è più sicuro?**
*   Anche se due utenti hanno la stessa password, i loro salt saranno diversi, e quindi anche i loro hash finali saranno **completamente diversi**.
*   Questo rende le rainbow tables inutili, perché un attaccante dovrebbe creare una rainbow table per ogni singolo salt.

**ASP.NET Core Identity** implementa automaticamente un meccanismo di salted hashing robusto (usando algoritmi moderni come PBKDF2 o IdentityV3) senza che lo sviluppatore debba gestirlo manualmente.
