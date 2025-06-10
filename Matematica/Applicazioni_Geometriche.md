# 🗺️ Applicazioni Geometriche degli Integrali

L'integrale definito non è solo un concetto teorico, ma uno strumento potentissimo per calcolare grandezze geometriche come aree e volumi di solidi di rotazione.

---

## 1. Calcolo dell'Area di una Superficie Piana

### A. Area tra il Grafico e l'Asse x
Se `f(x)` è una funzione continua in `[a, b]`:
*   **Se `f(x) ≥ 0`** in `[a, b]`, l'area `A` della regione di piano compresa tra il grafico di `f(x)`, l'asse x e le rette verticali `x=a` e `x=b` è:
    `A = ∫ (da a a b) f(x) dx`
*   **Se `f(x)` cambia segno**, bisogna spezzare l'integrale negli intervalli in cui `f(x)` è positiva o negativa. L'area totale è la somma dei valori assoluti delle aree parziali. Si calcola:
    `A = ∫ (da a b) |f(x)| dx`
    **In pratica:** Si trovano gli zeri di `f(x)`, si calcolano gli integrali definiti su ogni sottointervallo e si sommano i loro valori assoluti.

### B. Area tra due Curve
Se `f(x)` e `g(x)` sono due funzioni continue in `[a, b]` e `f(x) ≥ g(x)` per ogni `x` nell'intervallo, l'area `A` della regione compresa tra i due grafici è data dall'integrale della **funzione differenza**:

`A = ∫ (da a a b) [f(x) - g(x)] dx`

**Procedura Pratica:**
1.  Trovare i punti di intersezione tra le due curve risolvendo l'equazione `f(x) = g(x)`. Questi saranno gli estremi di integrazione `a` e `b`.
2.  Determinare quale delle due funzioni è "sopra" (`f(x)`) e quale è "sotto" (`g(x)`) nell'intervallo `[a, b]`.
3.  Calcolare l'integrale definito della loro differenza `f(x) - g(x)`.

---

## 2. Calcolo del Volume di un Solido di Rotazione

Un **solido di rotazione** è un solido ottenuto ruotando una regione piana attorno a un asse (di solito l'asse x o l'asse y).

### Metodo delle Fette (o dei Dischi)

L'idea è di affettare il solido in tanti dischi sottili di spessore infinitesimo `dx`.

### A. Rotazione attorno all'Asse x
Il volume `V` del solido ottenuto ruotando di 360° attorno all'asse x il grafico di una funzione `f(x)` (con `f(x) ≥ 0`) nell'intervallo `[a, b]` è:

`V = π · ∫ (da a a b) [f(x)]² dx`

**Da dove viene?** Ogni disco infinitesimo ha:
*   **Raggio:** `r = f(x)`
*   **Area di base:** `π · r² = π · [f(x)]²`
*   **Volume del disco:** `(Area di base) · (spessore) = π · [f(x)]² dx`
L'integrale "somma" i volumi di tutti questi dischi.

### B. Rotazione attorno all'Asse y
Se si ha una funzione `x = g(y)` e si ruota il suo grafico attorno all'asse y nell'intervallo `[c, d]` (sull'asse y), la formula è analoga:

`V = π · ∫ (da c a d) [g(y)]² dy`

**Attenzione:** Se la funzione è data come `y = f(x)`, bisogna prima ricavare `x` in funzione di `y`.
