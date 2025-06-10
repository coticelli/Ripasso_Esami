# 🙂🙁 Concavità, Convessità e Punti di Flesso

Lo studio della **concavità** e della **convessità** di una funzione fornisce informazioni su come "curva" il suo grafico. Questo studio è legato al segno della **derivata seconda** e permette di individuare i **punti di flesso**.

---

## 📈📉 Concavità e Convessità

Sia `f(x)` una funzione derivabile due volte in un intervallo `I`.

### Funzione Convessa 🙂
*   **Definizione:** Una funzione è **convessa** (o con concavità rivolta verso l'alto) in `I` se il suo grafico si trova **al di sopra** della retta tangente in ogni punto dell'intervallo.
*   **Legame con la derivata seconda:**
    Se `f''(x) > 0` per ogni `x` in `I`, allora `f(x)` è convessa in `I`.
*   **Significato intuitivo:** La pendenza della tangente (`f'(x)`) sta aumentando. Il grafico "sorride".

### Funzione Concava 🙁
*   **Definizione:** Una funzione è **concava** (o con concavità rivolta verso il basso) in `I` se il suo grafico si trova **al di sotto** della retta tangente in ogni punto dell'intervallo.
*   **Legame con la derivata seconda:**
    Se `f''(x) < 0` per ogni `x` in `I`, allora `f(x)` è concava in `I`.
*   **Significato intuitivo:** La pendenza della tangente (`f'(x)`) sta diminuendo. Il grafico è "triste".

---

## 🎢 Punti di Flesso

Un **punto di flesso** è un punto del grafico in cui la funzione **cambia la sua concavità** (da convessa a concava, o viceversa).

### Condizione Necessaria
Se `x₀` è un punto di flesso per `f(x)` e la funzione è derivabile due volte, allora la derivata seconda in quel punto deve essere zero:
`f''(x₀) = 0`

### Classificazione dei Flessi
Per classificare i flessi, si studia il segno della derivata seconda `f''(x)` in un intorno di un punto `x₀` che la annulla.

*   **Flesso Ascendente:** La concavità cambia da **concava a convessa**.
    `f''(x) < 0` per `x < x₀`
    `f''(x) > 0` per `x > x₀`
*   **Flesso Discendente:** La concavità cambia da **convessa a concava**.
    `f''(x) > 0` per `x < x₀`
    `f''(x) < 0` per `x > x₀`

Un punto di flesso può essere a **tangente obliqua**, **verticale** o **orizzontale** (in questo caso, è anche un punto stazionario).

### Procedura Pratica
1.  Calcolare la derivata seconda `f''(x)`.
2.  Trovare i candidati punti di flesso risolvendo l'equazione `f''(x) = 0`.
3.  Studiare il segno della derivata seconda risolvendo la disequazione `f''(x) > 0`.
4.  Verificare dove la derivata seconda cambia segno per individuare i punti di flesso e gli intervalli di concavità/convessità.
