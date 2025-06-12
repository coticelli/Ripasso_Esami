# 🏗️ Il Pattern Model-View-Controller (MVC)

**Model-View-Controller (MVC)** è un **design pattern architetturale** utilizzato per organizzare il codice di un'applicazione con interfaccia utente. Il suo scopo principale è la **separazione delle responsabilità (Separation of Concerns)**, suddividendo l'applicazione in tre componenti interconnessi ma distinti.

---

## 🧩 I Tre Componenti

### 1. Model (Modello) 📦
*   **Cosa fa:** È il "cervello" dell'applicazione.
*   **Responsabilità:**
    *   Gestisce i **dati** dell'applicazione e la loro logica.
    *   Contiene la **logica di business** (le regole su come i dati possono essere creati, modificati e letti).
    *   Comunica con il database.
    *   È completamente **indipendente dall'interfaccia utente**. Non sa nulla di come i dati verranno visualizzati.

### 2. View (Vista) 🖼️
*   **Cosa fa:** È ciò che l'utente **vede**.
*   **Responsabilità:**
    *   **Presenta i dati** all'utente in un formato specifico (es. una pagina HTML).
    *   Riceve i dati dal Model, ma non li modifica direttamente.
    *   Dovrebbe essere "stupida": la sua unica logica è quella di visualizzazione.

### 3. Controller (Controllore) 🎮
*   **Cosa fa:** È l'intermediario, il "vigile urbano".
*   **Responsabilità:**
    *   **Riceve l'input dell'utente** dalla View (es. un click su un pulsante, l'invio di un form).
    *   **Interagisce con il Model** per aggiornare i dati o per recuperare le informazioni richieste.
    *   **Seleziona la View** appropriata da mostrare all'utente come risposta.

---

## 🔄 Il Flusso di una Richiesta MVC

1.  L'**utente** interagisce con la **View**.
2.  La View invia la richiesta al **Controller**.
3.  Il **Controller** riceve la richiesta e "parla" con il **Model**, chiedendogli di eseguire un'azione (es. "recupera tutti i prodotti" o "salva questo nuovo utente").
4.  Il **Model** elabora la richiesta, interagisce con il database se necessario, e restituisce i dati al Controller.
5.  Il **Controller** prende i dati dal Model e li passa alla **View** appropriata.
6.  La **View** usa i dati ricevuti per generare la risposta finale (es. la pagina HTML) e la mostra all'utente.

---

## 👍 Vantaggi del Pattern MVC

*   **Organizzazione del Codice:** Mantiene il codice pulito e ordinato, rendendolo più facile da capire e mantenere.
*   **Sviluppo Parallelo:** Permette a sviluppatori front-end (che lavorano sulla View) e back-end (che lavorano su Model e Controller) di lavorare contemporaneamente.
*   **Riusabilità:** Il Model può essere riutilizzato con diverse View (es. una pagina web e un'app mobile possono usare lo stesso Model).
*   **Testabilità:** La separazione rende più facile testare i singoli componenti in modo isolato.
