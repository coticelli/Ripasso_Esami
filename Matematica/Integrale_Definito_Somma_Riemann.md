# 📊 Integrale Definito e Somma di Riemann

L'**integrale definito** nasce storicamente per risolvere il problema del calcolo delle aree di figure con contorni curvi (problema della quadratura del cerchio).

---

## 🏛️ L'Idea di Archimede e la Somma di Riemann

L'idea fondamentale, già avuta da Archimede, è quella di **approssimare** un'area curva con la somma di aree di figure semplici, come i rettangoli.

**La Somma di Riemann** formalizza questa idea:
Data una funzione `f(x)` continua e positiva in un intervallo `[a, b]`:
1.  **Suddivisione:** Si divide l'intervallo `[a, b]` in `n` sottointervalli più piccoli, tutti di ampiezza `Δx = (b-a)/n`.
2.  **Approssimazione:** In ogni sottointervallo, si costruisce un rettangolo che ha per base `Δx` e per altezza il valore della funzione in un punto scelto `cᵢ` all'interno del sottointervallo. L'area di questo rettangolo è `f(cᵢ) · Δx`.
3.  **Somma:** La **somma di Riemann** è la somma delle aree di tutti questi rettangoli:
    `Sₙ = Σ (da i=1 a n) f(cᵢ) · Δx`

---

## ∫ Definizione di Integrale Definito

L'**area esatta** sotto la curva si ottiene facendo tendere il numero di rettangoli all'infinito (`n → ∞`), in modo che la loro base `Δx` diventi infinitesima.

L'**integrale definito** di `f(x)` tra `a` e `b` è il limite della somma di Riemann per `n → ∞`:

`∫ (da a a b) f(x) dx = lim (n→∞) Σ (da i=1 a n) f(cᵢ) · Δx`

Dove:
*   `∫ (da a a b)` è il simbolo di integrale definito.
*   `a` e `b` sono gli **estremi di integrazione** (`a` è l'estremo inferiore, `b` quello superiore).
*   `f(x)` è la funzione integranda.

**Risultato:** L'integrale definito è un **numero reale**, che rappresenta l'**area con segno** tra il grafico della funzione e l'asse x.
*   Se `f(x) > 0`, l'area è positiva.
*   Se `f(x) < 0`, l'area è negativa.

---

## 📜 Teorema Fondamentale del Calcolo Integrale (Formula di Newton-Leibniz)

Questo teorema è il ponte che collega il calcolo differenziale e quello integrale, fornendo un metodo pratico per calcolare gli integrali definiti senza passare dal limite delle somme di Riemann.

**Enunciato:**
Sia `f(x)` una funzione continua in `[a, b]` e sia `F(x)` una sua qualsiasi primitiva.
Allora:
`∫ (da a a b) f(x) dx = F(b) - F(a)`

**Procedura Pratica:**
1.  Trovare una primitiva `F(x)` della funzione `f(x)` (calcolando l'integrale indefinito).
2.  Calcolare il valore della primitiva all'estremo superiore `F(b)`.
3.  Calcolare il valore della primitiva all'estremo inferiore `F(a)`.
4.  Sottrarre i due valori: `F(b) - F(a)`. Questa differenza si indica spesso con `[F(x)] (da a a b)`.
