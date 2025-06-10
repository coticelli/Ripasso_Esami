# 🏛️ Assiomi di Kolmogorov e Classificazione Eventi

L'approccio assiomatico, introdotto dal matematico russo Andrej Kolmogorov nel 1933, ha fondato la moderna teoria della probabilità su basi rigorose, superando i limiti delle definizioni classica, frequentista e soggettivista.

---

## ✅ I Tre Assiomi della Probabilità

Qualunque sia il modo in cui viene definita, una funzione `P` è una misura di probabilità se associa ad ogni evento `E` dello spazio campionario `Ω` un numero reale che soddisfa i seguenti tre assiomi (regole fondamentali):

### 1. Assioma di Non-Negatività
La probabilità di un qualsiasi evento è sempre un numero non negativo.
`P(E) ≥ 0` per ogni evento `E`.

### 2. Assioma di Normalizzazione
La probabilità dell'evento certo (cioè l'intero spazio campionario) è uguale a 1.
`P(Ω) = 1`

**Conseguenze:**
*   `0 ≤ P(E) ≤ 1`: La probabilità di qualsiasi evento è sempre un numero compreso tra 0 e 1.
*   `P(Ø) = 0`: La probabilità dell'evento impossibile è 0.

### 3. Assioma di Additività (o della Somma)
Se due eventi `A` e `B` sono **incompatibili** (o mutuamente esclusivi), cioè non possono verificarsi contemporaneamente (`A ∩ B = Ø`), allora la probabilità che si verifichi uno o l'altro (`A ∪ B`) è la somma delle loro probabilità.

`P(A ∪ B) = P(A) + P(B)`

Questo assioma si estende anche a un numero infinito di eventi a due a due incompatibili.

---

## 🔗 Classificazione degli Eventi e Operazioni

### Evento Contrario (o Complementare)
Dato un evento `E`, il suo evento contrario `E̅` è l'evento "non si verifica E".
*   **Formula:** La probabilità dell'evento contrario è 1 meno la probabilità dell'evento.
    `P(E̅) = 1 - P(E)`
    Questa formula è utilissima per calcolare la probabilità di eventi complessi (es. "esce almeno una testa").

### Unione di Eventi (Evento Somma) - `A ∪ B`
È l'evento che si verifica se si verifica **almeno uno** tra `A` e `B` ("A o B").

*   **Regola della Somma (caso generale):** Vale per qualsiasi coppia di eventi, anche compatibili.
    `P(A ∪ B) = P(A) + P(B) - P(A ∩ B)`
    Si sottrae la probabilità dell'intersezione per non contarla due volte.

### Intersezione di Eventi (Evento Prodotto) - `A ∩ B`
È l'evento che si verifica se si verificano **entrambi** gli eventi `A` e `B` contemporaneamente ("A e B").
Il calcolo di `P(A ∩ B)` è legato al concetto di probabilità condizionata.
