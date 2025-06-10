# 🎲 Concetti Base e Concezioni di Probabilità

La teoria della probabilità è la branca della matematica che si occupa di analizzare e misurare l'incertezza degli eventi.

---

## 📝 Definizioni Fondamentali

*   **Esperimento Aleatorio (o Casuale):** Un esperimento il cui esito non può essere previsto con certezza, ma di cui si conoscono tutti i possibili risultati.
    *   *Esempio:* Lancio di un dado.
*   **Spazio Campionario (Ω):** L'insieme di **tutti** i possibili risultati di un esperimento aleatorio.
    *   *Esempio:* Per il lancio di un dado, `Ω = {1, 2, 3, 4, 5, 6}`.
*   **Evento (E):** Un qualsiasi sottoinsieme dello spazio campionario. Può essere:
    *   **Evento Elementare:** Un singolo risultato (es. "esce il 3").
    *   **Evento Composto:** Un insieme di più risultati (es. "esce un numero pari" → `E = {2, 4, 6}`).
    *   **Evento Certo:** Coincide con lo spazio campionario `Ω` (es. "esce un numero minore di 7"). Ha probabilità 1.
    *   **Evento Impossibile (Ø):** L'insieme vuoto, un evento che non può mai verificarsi (es. "esce il 7"). Ha probabilità 0.

---

## 🤔 Le Tre Concezioni di Probabilità

Esistono diversi modi di definire e calcolare la probabilità.

### 1. Concezione Classica (a priori)
*   **Quando si applica:** Quando tutti i risultati possibili di un esperimento sono **equiprobabili** (hanno la stessa probabilità di accadere).
*   **Formula:** La probabilità `P(E)` di un evento E è il rapporto tra il numero di **casi favorevoli** all'evento e il numero di **casi possibili** totali.
    `P(E) = (Numero di casi favorevoli) / (Numero di casi possibili)`
*   **Esempio:** Lancio di un dado non truccato. La probabilità che esca un numero pari è `P(pari) = 3/6 = 1/2`, perché ci sono 3 casi favorevoli (`{2,4,6}`) su 6 casi possibili.
*   **Limiti:** Non si può applicare se i casi non sono equiprobabili o se il numero di casi è infinito.

### 2. Concezione Frequentista (o Statistica, a posteriori)
*   **Quando si applica:** Quando un esperimento è **ripetibile** un gran numero di volte nelle stesse condizioni.
*   **Formula:** La probabilità `P(E)` di un evento E è il valore a cui tende la **frequenza relativa** dell'evento, al crescere del numero di prove.
    `P(E) ≈ f(E) = (Numero di volte che E si è verificato) / (Numero totale di prove)`
*   **Legge dei Grandi Numeri:** All'aumentare del numero di prove, la frequenza relativa si avvicina sempre di più al valore teorico della probabilità.
*   **Esempio:** Per sapere se una moneta è truccata, la lancio 1000 volte. Se esce testa 700 volte, stimo che la probabilità di testa sia circa 0.7.

### 3. Concezione Soggettivista
*   **Quando si applica:** In situazioni uniche, non ripetibili, in cui le altre due definizioni non sono applicabili (es. probabilità di vittoria di una squadra, probabilità di successo di un'operazione chirurgica).
*   **Formula:** La probabilità `P(E)` è il **grado di fiducia** che un individuo razionale (in base alle informazioni che possiede) assegna al verificarsi di un evento. Viene definita come la **somma `p` che si è disposti a scommettere per ricevere una vincita `S`** se l'evento si verifica.
    `p = P(E) · S`
*   **Limiti:** Dipende dal soggetto e dalle sue informazioni.

La teoria moderna, basata sugli assiomi di Kolmogorov, unifica queste concezioni.
