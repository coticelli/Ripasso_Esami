# ∫ Primitive e Integrali Indefiniti

Il calcolo integrale nasce per risolvere due problemi principali: trovare una funzione conoscendo la sua derivata (problema delle primitive) e calcolare l'area di una regione di piano (integrale definito).

---

## 👩‍👧 Concetto di Primitiva

Una funzione `F(x)` è detta **primitiva** di una funzione `f(x)` in un intervallo `I` se `F(x)` è derivabile in `I` e la sua derivata è `f(x)` per ogni `x` in `I`.
`F'(x) = f(x)`

**Esempio:** `F(x) = x³` è una primitiva di `f(x) = 3x²`, perché la derivata di `x³` è `3x²`.

### L'insieme di tutte le primitive
Se `F(x)` è una primitiva di `f(x)`, allora anche `F(x) + c`, con `c` costante reale qualsiasi, è una primitiva.
**Teorema:** L'insieme di **tutte e sole** le primitive di una funzione `f(x)` è dato dalla famiglia di funzioni `F(x) + c`.

---

##  📚 Integrale Indefinito

L'**integrale indefinito** di una funzione `f(x)` è l'insieme di tutte le sue primitive e si indica con il simbolo:
`∫ f(x) dx = F(x) + c`
Dove:
*   `∫` è il simbolo di integrale.
*   `f(x)` è la **funzione integranda**.
*   `dx` indica che la variabile di integrazione è `x`.
*   `F(x) + c` è l'insieme delle primitive.

**In pratica:** L'integrazione indefinita è l'**operazione inversa della derivazione**.

---

## 📏 Proprietà degli Integrali Indefiniti

L'integrale indefinito gode di due proprietà di linearità, che derivano direttamente dalle proprietà delle derivate:

1.  **Integrale di una somma:** L'integrale di una somma di funzioni è uguale alla somma degli integrali delle singole funzioni.
    `∫ [f(x) + g(x)] dx = ∫ f(x) dx + ∫ g(x) dx`

2.  **Trasporto di una costante (omogeneità):** Una costante moltiplicativa può essere "portata fuori" dal simbolo di integrale.
    `∫ k · f(x) dx = k · ∫ f(x) dx`

---

## 📝 Tabella degli Integrali Immediati

Gli integrali immediati si ottengono "leggendo al contrario" la tabella delle derivate fondamentali. Ecco alcuni esempi chiave:

| Funzione `f(x)`          | Integrale Indefinito `∫ f(x) dx`       |
| ------------------------ | ------------------------------------- |
| `k`                      | `kx + c`                              |
| `x^α` (con α ≠ -1)     | `(x^(α+1)) / (α+1) + c`                 |
| `1/x`                    | `ln|x| + c`                           |
| `e^x`                    | `e^x + c`                             |
| `a^x`                    | `(a^x) / ln(a) + c`                   |
| `sin(x)`                 | `-cos(x) + c`                         |
| `cos(x)`                 | `sin(x) + c`                          |
| `1 / cos²(x)`            | `tan(x) + c`                          |
| `1 / √(1-x²)`          | `arcsin(x) + c`                       |
| `1 / (1+x²)`             | `arctan(x) + c`                       |

Molti altri integrali si possono ricondurre a questi tramite le **tecniche di integrazione**.
