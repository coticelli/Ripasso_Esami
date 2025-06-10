# 🛑 Punti Stazionari e i Teoremi di Rolle e Lagrange

---

## 📍 Punti Stazionari

Un punto `x₀` interno al dominio di una funzione `f(x)` si dice **stazionario** se la funzione è derivabile in `x₀` e la sua derivata prima in quel punto è zero.
`f'(x₀) = 0`

**Significato geometrico:** In un punto stazionario, la **retta tangente al grafico della funzione è orizzontale**.

I punti stazionari sono i "candidati" a essere punti di massimo, minimo o flesso a tangente orizzontale. La loro natura viene determinata studiando il segno della derivata prima (criterio di monotonia) o il segno della derivata seconda.

---

## 📜 Teorema di Rolle

Il Teorema di Rolle è un caso particolare del Teorema di Lagrange e garantisce l'esistenza di almeno un punto stazionario sotto certe condizioni.

### Enunciato del Teorema:
Sia `f(x)` una funzione che soddisfa tre ipotesi:
1.  È **continua** nell'intervallo chiuso `[a, b]`.
2.  È **derivabile** nell'intervallo aperto `(a, b)`.
3.  Assume **valori uguali** agli estremi dell'intervallo: `f(a) = f(b)`.

**Allora** esiste **almeno un punto** `c` interno all'intervallo `(a, b)` in cui la derivata prima si annulla:
`f'(c) = 0`

**Significato geometrico:** Se una curva continua e derivabile parte da una certa quota e arriva alla stessa quota, deve esserci almeno un punto in mezzo in cui la sua tangente è orizzontale.

---

## 📜 Teorema di Lagrange (o del Valor Medio)

Il Teorema di Lagrange è una generalizzazione del Teorema di Rolle e uno dei pilastri del calcolo differenziale.

### Enunciato del Teorema:
Sia `f(x)` una funzione che soddisfa due ipotesi:
1.  È **continua** nell'intervallo chiuso `[a, b]`.
2.  È **derivabile** nell'intervallo aperto `(a, b)`.

**Allora** esiste **almeno un punto** `c` interno all'intervallo `(a, b)` tale che:
`f'(c) = (f(b) - f(a)) / (b - a)`

### Significato geometrico:
Il teorema afferma che, in un arco di curva continuo e derivabile, c'è almeno un punto `c` in cui la **pendenza della retta tangente** (`f'(c)`) è **esattamente uguale alla pendenza della retta secante** che unisce i due punti estremi dell'arco (`(f(b) - f(a)) / (b - a)`).

In altre parole, esiste un punto in cui la tangente è parallela alla corda che congiunge gli estremi.
