# ⏳ Tecniche di Pianificazione e Controllo Temporale

La gestione del tempo è una delle aree più critiche del project management. Le tecniche di pianificazione temporale aiutano a creare una schedulazione realistica, a identificare le attività più importanti e a ottimizzare l'uso del tempo.

---

## 1. Stima della Durata delle Attività

Prima di poter schedulare, bisogna stimare quanto durerà ogni attività.

*   **Stima Analogica:** Si basa sulla durata di attività simili svolte in progetti passati.
*   **Stima Parametrica:** Usa una relazione statistica tra dati storici e altre variabili (es. se scrivere 1000 righe di codice richiede 10 ore, allora 2000 righe richiederanno 20 ore).
*   **Stima a Tre Punti (PERT):**
    *   Si stima una durata **Ottimistica (O)**, una **Pessimistica (P)** e una **Più Probabile (M)**.
    *   La durata attesa si calcola con la formula: **`Durata = (O + 4M + P) / 6`**.
    *   Questo metodo aiuta a gestire l'incertezza.

---

## 2. Metodo del Percorso Critico (Critical Path Method - CPM)

Il **CPM** è una tecnica fondamentale per identificare la sequenza di attività che determina la **durata minima totale del progetto**.

*   **Percorso (Path):** Una qualsiasi sequenza di attività collegate da dipendenze dall'inizio alla fine del progetto.
*   **Percorso Critico (Critical Path):** È il **percorso più lungo** attraverso il diagramma di rete del progetto. La sua lunghezza totale definisce la durata minima del progetto.
*   **Float (o Slack):** È il tempo di cui un'attività può ritardare senza influenzare la data di fine del progetto.
    *   Le attività sul **percorso critico** hanno **float pari a zero**. Qualsiasi ritardo su una di queste attività ritarderà l'intero progetto.

**Scopo del CPM:**
*   Identificare le attività su cui il Project Manager deve concentrare la massima attenzione.
*   Capire l'impatto dei ritardi.
*   Ottimizzare la schedulazione.

---

## 3. Tecniche di Ottimizzazione della Schedulazione

A volte, la schedulazione risultante è troppo lunga. Esistono due tecniche per accorciarla:

### Crashing 💥
*   **Cosa si fa:** Si aggiungono **più risorse** (persone, denaro) a un'attività del percorso critico per ridurne la durata.
*   **Conseguenza:** Aumenta i **costi** del progetto.
*   **Esempio:** Pagare gli straordinari al team di sviluppo per finire prima una funzionalità critica.

### Fast Tracking ⏩
*   **Cosa si fa:** Si modificano le dipendenze per eseguire in **parallelo** attività che originariamente erano pianificate in sequenza.
*   **Conseguenza:** Non aumenta i costi, ma aumenta significativamente i **rischi** di rilavorazioni e problemi di comunicazione.
*   **Esempio:** Iniziare a scrivere il codice di un modulo prima che la sua progettazione sia stata completamente approvata.
