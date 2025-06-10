# 🗺️ Progettazione Concettuale: Modello ER (Entità-Relazione)

Il **Modello Entità-Relazione (ER)** è uno strumento grafico per la **progettazione concettuale** di un database. Il suo scopo è descrivere la realtà di interesse in modo chiaro e formale, prima di pensare a come verrà implementata tecnicamente.

Permette di rappresentare i dati e le loro connessioni in modo indipendente da qualsiasi specifico software di database (DBMS).

---

## 🧱 Componenti Fondamentali del Modello ER

### 1. Entità (Entity)
*   **Cos'è:** Un oggetto (concreto o astratto) del mondo reale che ha un'esistenza autonoma e su cui vogliamo memorizzare informazioni.
*   **Rappresentazione Grafica:** Un **rettangolo**.
*   **Esempi:** STUDENTE, CORSO, PROFESSORE, ORDINE.

### 2. Attributo (Attribute)
*   **Cos'è:** Una proprietà o caratteristica che descrive un'entità.
*   **Rappresentazione Grafica:** Un'**ellisse** collegata all'entità.
*   **Esempi:** Per l'entità STUDENTE, gli attributi potrebbero essere `Matricola`, `Nome`, `Cognome`.
*   **Attributo Chiave (Primary Key):** È un attributo (o un insieme di attributi) che **identifica univocamente** ogni istanza di un'entità. Viene rappresentato con il nome sottolineato. Es: `Matricola`.

### 3. Relazione (Relationship) o Associazione
*   **Cos'è:** Un legame logico che esiste tra due o più entità.
*   **Rappresentazione Grafica:** Un **rombo** collegato alle entità che mette in relazione.
*   **Esempi:** Uno STUDENTE è **iscritto a** un CORSO. La relazione è "Iscritto a".

---

## 🔗 Cardinalità della Relazione

La cardinalità specifica **quante istanze** di un'entità possono essere associate a un'istanza dell'altra entità, e viceversa.

### 1. **Uno a Uno (1:1)**
*   Ad ogni istanza di A corrisponde **una e una sola** istanza di B, e viceversa.
*   *Esempio:* `PRESIDE` --- (Dirige) ---> `ISTITUTO` (un preside dirige un solo istituto).

### 2. **Uno a Molti (1:N)**
*   Ad ogni istanza di A possono corrispondere **molte** istanze di B, ma a ogni istanza di B corrisponde **una e una sola** istanza di A.
*   *Esempio:* `PROFESSORE` --- (Insegna in) ---> `CORSO` (un professore può insegnare in più corsi, ma un corso ha un solo professore).

### 3. **Molti a Molti (N:M)**
*   Ad ogni istanza di A possono corrispondere **molte** istanze di B, e viceversa.
*   *Esempio:* `STUDENTE` --- (Frequenta) ---> `CORSO` (uno studente può frequentare più corsi e un corso può essere frequentato da più studenti).

La cardinalità si scrive sui lati della relazione.

Lo schema ER è il punto di partenza per la successiva progettazione logica, dove verrà tradotto in tabelle (modello relazionale).
