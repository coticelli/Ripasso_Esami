# 📈 Punti di Non Derivabilità e Teorema di Fermat

---

## 🚦 Punti di Non Derivabilità

Un punto `x₀` è detto di **non derivabilità** per una funzione `f(x)` se la funzione è continua in `x₀` ma la sua derivata prima non esiste in quel punto. Questo accade quando il limite del rapporto incrementale destro e sinistro sono diversi o infiniti.

Esistono tre tipi principali di punti di non derivabilità:

### 1. Punto Angoloso 📐
*   **Definizione:** Derivata destra `f'_+(x₀)` e derivata sinistra `f'_(x₀)` sono entrambe **finite**, ma **diverse** tra loro.
    `f'_+(x₀) ≠ f'_(x₀)`
*   **Graficamente:** La funzione presenta uno "spigolo". Le due tangenti destra e sinistra hanno pendenze diverse.
*   **Esempio:** `f(x) = |x|` in `x₀ = 0`.

### 2. Cuspide 뾰
*   **Definizione:** Derivata destra `f'_+(x₀)` e derivata sinistra `f'_(x₀)` sono entrambe **infinite** e di **segno opposto**.
    `f'_+(x₀) = +∞` e `f'_(x₀) = -∞` (o viceversa).
*   **Graficamente:** La funzione ha una "punta" acuta. Le tangenti destra e sinistra tendono entrambe a diventare verticali.
*   **Esempio:** `f(x) = √|x|` in `x₀ = 0`.

### 3. Flesso a Tangente Verticale 🧗
*   **Definizione:** Derivata destra `f'_+(x₀)` e derivata sinistra `f'_(x₀)` sono entrambe **infinite** e dello **stesso segno**.
    `f'_+(x₀) = f'_(x₀) = +∞` oppure `f'_+(x₀) = f'_(x₀) = -∞`
*   **Graficamente:** La funzione "si appiattisce" e la retta tangente in quel punto è verticale. Il punto è anche un punto di flesso.
*   **Esempio:** `f(x) = ³√x` in `x₀ = 0`.

---

## ⛰️ Teorema di Fermat sui Punti Stazionari

Questo teorema stabilisce un legame fondamentale tra i punti di massimo/minimo e la derivata prima.

### Enunciato del Teorema:
Sia `f(x)` una funzione definita in un intervallo `[a, b]` e sia `x₀` un punto interno a tale intervallo.
Se:
1.  `x₀` è un punto di **massimo o minimo relativo** per `f(x)`.
2.  `f(x)` è **derivabile** in `x₀`.

**Allora** la derivata prima in quel punto è necessariamente zero:
`f'(x₀) = 0`

### Cosa significa in pratica?
*   Il teorema di Fermat ci dice che i punti di massimo o minimo relativo di una funzione derivabile **vanno cercati tra i punti stazionari**, cioè i punti che annullano la derivata prima.
*   **Attenzione:** non è vero il contrario! Se `f'(x₀) = 0`, non è detto che `x₀` sia un punto di massimo o minimo. Potrebbe essere un flesso a tangente orizzontale (es. `f(x) = x³` in `x=0`).

Il Teorema di Fermat fornisce una **condizione necessaria ma non sufficiente** per l'esistenza di un massimo o minimo relativo.
