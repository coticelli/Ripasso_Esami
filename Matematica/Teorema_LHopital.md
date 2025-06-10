# 🏥 Teorema di De L'Hôpital

Il **Teorema di De L'Hôpital** è una potentissima regola che permette di calcolare limiti di funzioni che si presentano nelle **forme indeterminate** `0/0` e `∞/∞`.

---

## 📜 Enunciato del Teorema

Siano `f(x)` e `g(x)` due funzioni derivabili in un intorno di un punto `x₀` (finito o infinito), con `g'(x) ≠ 0` in tale intorno.

Se il limite del loro rapporto si presenta in una forma indeterminata:
`lim (x→x₀) f(x) / g(x) = 0/0`
oppure
`lim (x→x₀) f(x) / g(x) = ∞/∞`

**Allora**, se esiste (finito o infinito) il limite del rapporto delle loro derivate, questo è uguale al limite originale:

`lim (x→x₀) f(x) / g(x) = lim (x→x₀) f'(x) / g'(x)`

---

## 🤔 Quando e Come si Applica

### ✅ Condizioni Fondamentali per l'Applicazione:
1.  Il limite deve essere del rapporto di due funzioni `f(x) / g(x)`.
2.  La forma indeterminata deve essere **ESCLUSIVAMENTE** `0/0` oppure `∞/∞`.

### ⚠️ Errori Comuni da Evitare:
*   **Non derivare il quoziente!** Non si applica la regola di derivazione di un rapporto `(f/g)'`. Si derivano separatamente il numeratore `f(x)` e il denominatore `g(x)`.
*   **Non applicarlo ad altre forme indeterminate!** Forme come `0 · ∞`, `∞ - ∞`, `1^∞` non possono essere risolte direttamente con De L'Hôpital. Devono prima essere **ricondotte algebricamente** a una forma `0/0` o `∞/∞`.

---

## 🧩 Esempi Pratici

**Esempio 1: Forma `0/0`**
Calcolare `lim (x→0) sin(x) / x`.
1.  Verifico la forma: `sin(0)/0 = 0/0`. OK.
2.  Applico De L'Hôpital:
    `lim (x→0) sin(x) / x = lim (x→0) cos(x) / 1 = cos(0) / 1 = 1`.

**Esempio 2: Forma `∞/∞`**
Calcolare `lim (x→+∞) e^x / x²`.
1.  Verifico la forma: `e^+∞ / (+∞)² = +∞/+∞`. OK.
2.  Applico De L'Hôpital:
    `lim (x→+∞) e^x / x² = lim (x→+∞) e^x / (2x)`. È ancora una forma `∞/∞`.
3.  Posso applicare De L'Hôpital di nuovo:
    `lim (x→+∞) e^x / (2x) = lim (x→+∞) e^x / 2 = +∞ / 2 = +∞`.

**Esempio 3: Riconduzione a forma `0/0`**
Calcolare `lim (x→0⁺) x · ln(x)`.
1.  Forma indeterminata: `0 · (-∞)`. Non posso applicare De L'Hôpital direttamente.
2.  Riscrivo la funzione: `x · ln(x) = ln(x) / (1/x)`.
3.  Ora il limite è `lim (x→0⁺) ln(x) / (1/x) = -∞/+∞`. OK, ora posso applicare De L'Hôpital.
4.  `lim (x→0⁺) (1/x) / (-1/x²) = lim (x→0⁺) -x = 0`.
