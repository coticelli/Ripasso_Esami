# 📋 Analisi dei Requisiti e UML: Use Case Diagram

L'**analisi dei requisiti** è il processo di definire le aspettative degli utenti e le funzionalità che un sistema deve fornire. L'**UML** è un linguaggio grafico che aiuta a visualizzare questi requisiti.

---

## 1. Analisi dei Requisiti

Un **requisito** è una condizione o una capacità che un sistema deve possedere per soddisfare un contratto, uno standard o le esigenze di uno stakeholder.

### Tipi di Requisiti
*   **Requisiti Funzionali ✅:**
    *   **Cosa** deve fare il sistema. Descrivono le funzionalità e le interazioni.
    *   *Esempio:* "Il sistema deve permettere all'utente di registrarsi con username e password."
*   **Requisiti Non Funzionali ⚙️:**
    *   **Come** il sistema deve comportarsi. Descrivono le qualità del sistema (performance, sicurezza, usabilità).
    *   *Esempio:* "La pagina di login deve caricarsi in meno di 2 secondi."

Una buona analisi dei requisiti è fondamentale per il successo di un progetto, perché previene incomprensioni e costose modifiche in fasi avanzate.

---

## 2. UML (Unified Modeling Language)

**UML** non è un linguaggio di programmazione, ma un **linguaggio di modellazione visuale** standardizzato. Fornisce un insieme di diagrammi per descrivere, visualizzare e documentare i diversi aspetti di un sistema software.

---

## 3. Il Diagramma dei Casi d'Uso (Use Case Diagram)

È uno dei diagrammi UML più importanti. Il suo scopo è descrivere le **funzionalità principali di un sistema dal punto di vista dell'utente**.

### Componenti Fondamentali
*   **Attore (Actor) 🧍:**
    *   Rappresenta un ruolo esterno che interagisce con il sistema (un utente, un altro sistema, un dispositivo hardware).
    *   Viene disegnato come uno "stick man".

*   **Caso d'Uso (Use Case) 🔄:**
    *   Rappresenta una singola funzionalità o interazione che il sistema offre all'attore per raggiungere un obiettivo.
    *   Viene disegnato come un'**ellisse** con dentro il nome dell'azione (es. "Effettua Login", "Aggiungi al Carrello").

*   **Sistema (System Boundary) ⬜:**
    *   Un **rettangolo** che delimita i confini del sistema. I casi d'uso sono all'interno, gli attori all'esterno.

*   **Associazione (Association) ―:**
    *   Una linea continua che collega un attore a un caso d'uso, indicando che l'attore partecipa a quella funzionalità.

### Relazioni tra Casi d'Uso
*   **`<<include>>` (Inclusione):** Un caso d'uso ne include un altro. La funzionalità inclusa è **obbligatoria** per l'esecuzione del caso d'uso principale. (Es: "Effettua Pagamento" `<<include>>` "Verifica Carta di Credito").
*   **`<<extend>>` (Estensione):** Un caso d'uso ne estende un altro. La funzionalità estesa è **opzionale** e si verifica solo a determinate condizioni. (Es: "Effettua Login" può essere `<<extend>>` da "Recupera Password").

**Esempio (Bancomat):**
L'attore `Cliente` è associato ai casi d'uso `Preleva Contanti`, `Controlla Saldo` e `Effettua Ricarica`.
