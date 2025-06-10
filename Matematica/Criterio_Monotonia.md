# ↗️↘️ Criterio di Monotonia e Studio della Crescenza

Il **criterio di monotonia** (o criterio di crescenza/decrescenza) è uno strumento fondamentale dello studio di funzione che collega il **segno della derivata prima** all'andamento (crescente o decrescente) della funzione.

---

## 📜 Il Teorema (o Criterio di Monotonia)

Sia `f(x)` una funzione continua e derivabile in un intervallo `I`.

1.  Se `f'(x) > 0` per ogni `x` in `I`, allora la funzione `f(x)` è **strettamente crescente** in `I`.
    📈 **In pratica:** Dove la derivata è positiva, la funzione sale.

2.  Se `f'(x) < 0` per ogni `x` in `I`, allora la funzione `f(x)` è **strettamente decrescente** in `I`.
    📉 **In pratica:** Dove la derivata è negativa, la funzione scende.

3.  Se `f'(x) = 0` per ogni `x` in `I`, allora la funzione `f(x)` è **costante** in `I`.
    ➡️ **In pratica:** Dove la derivata è nulla, la funzione è piatta.

---

## 🔎 Come si usa nello studio dei Punti Stazionari

Lo studio del segno della derivata prima ci permette di classificare la natura dei punti stazionari (dove `f'(x) = 0`).

Consideriamo un punto stazionario `x₀`:
1.  **Punto di Minimo Relativo** 🏆 (min)
    *   **Comportamento:** La funzione prima decresce, poi cresce.
    *   **Segno di f'(x):**
        *   `f'(x) < 0` per `x < x₀` (a sinistra)
        *   `f'(x) > 0` per `x > x₀` (a destra)
    *   **Schema:** ` - | + `
                 `  ↘️ x₀ ↗️ `

2.  **Punto di Massimo Relativo** 🥇 (MAX)
    *   **Comportamento:** La funzione prima cresce, poi decresce.
    *   **Segno di f'(x):**
        *   `f'(x) > 0` per `x < x₀` (a sinistra)
        *   `f'(x) < 0` per `x > x₀` (a destra)
    *   **Schema:** ` + | - `
                 `  ↗️ x₀ ↘️ `

3.  **Flesso a Tangente Orizzontale** 🎢
    *   **Comportamento:** La funzione cresce sia prima che dopo `x₀` (o decresce sia prima che dopo). La derivata si annulla in `x₀` ma non cambia segno.
    *   **Segno di f'(x):**
        *   `f'(x) > 0` per `x < x₀` e `f'(x) > 0` per `x > x₀` (crescente)
        *   `f'(x) < 0` per `x < x₀` e `f'(x) < 0` per `x > x₀` (decrescente)
    *   **Schema (crescente):** ` + | + `
                          `  ↗️ x₀ ↗️ `

### Procedura Pratica
1.  Calcolare la derivata prima `f'(x)`.
2.  Trovare i punti stazionari risolvendo `f'(x) = 0`.
3.  Studiare il segno di `f'(x)` risolvendo la disequazione `f'(x) > 0`.
4.  Disegnare uno schema dei segni per determinare gli intervalli di monotonia e la natura dei punti stazionari.
