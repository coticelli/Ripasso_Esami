# 🛠️ Tecniche di Integrazione

Non tutti gli integrali sono immediati. Esistono diverse tecniche per ricondurre integrali complessi a forme più semplici.

---

## 1. Metodo di Scomposizione

Questo metodo si basa sulla **linearità dell'integrale**. Se la funzione integranda è una somma algebrica di più termini, si può spezzare l'integrale nella somma di integrali più semplici.

`∫ [f(x) + g(x) - h(x)] dx = ∫ f(x) dx + ∫ g(x) dx - ∫ h(x) dx`

**Quando si usa?** Utile soprattutto per integrare **funzioni polinomiali** e **funzioni razionali fratte** dopo averle scomposte in fratti semplici.

**Esempio (Funzione Razionale Fratta):**
`∫ (2x+3) / (x²+3x-4) dx`
1.  Scompongo il denominatore: `x²+3x-4 = (x+4)(x-1)`.
2.  Cerco A e B tali che `(2x+3) / [(x+4)(x-1)] = A/(x+4) + B/(x-1)`. Trovo `A=1` e `B=1`.
3.  L'integrale diventa: `∫ [1/(x+4) + 1/(x-1)] dx = ∫ 1/(x+4) dx + ∫ 1/(x-1) dx = ln|x+4| + ln|x-1| + c`.

---

## 2. Integrazione per Sostituzione

Questo metodo è l'analogo della regola di derivazione di una funzione composta (derivazione a catena). L'idea è di cambiare la variabile di integrazione `x` con una nuova variabile `t` per semplificare l'integrale.

`∫ f(g(x)) · g'(x) dx`
1.  Pongo `t = g(x)`.
2.  Differenzio: `dt = g'(x) dx`.
3.  Sostituisco tutto nell'integrale: `∫ f(t) dt`.

**Procedura Pratica:**
1.  **Scegliere la sostituzione:** Individuare una parte dell'integranda `g(x)` la cui derivata `g'(x)` compare anch'essa (a meno di una costante).
2.  **Sostituire:** Porre `t = g(x)` e calcolare `dt` in funzione di `dx`. Sostituire `x` e `dx` con `t` e `dt`.
3.  **Risolvere:** Calcolare il nuovo integrale in `t`.
4.  **Tornare alla variabile originale:** Sostituire di nuovo `t` con `g(x)`.

**Esempio:** `∫ 2x · cos(x²) dx`
1.  Noto che `2x` è la derivata di `x²`.
2.  Pongo `t = x²`. Differenzio: `dt = 2x dx`.
3.  Sostituisco: `∫ cos(t) dt`.
4.  Risolvo: `sin(t) + c`.
5.  Torno a `x`: `sin(x²) + c`.

---

## 3. Integrazione per Parti

Questo metodo è l'analogo della regola di derivazione di un prodotto di funzioni. Si usa quando l'integranda è il prodotto di due funzioni di tipo diverso (es. un polinomio e una funzione logaritmica/esponenziale).

### La Formula:
`∫ f(x) · g'(x) dx = f(x) · g(x) - ∫ f'(x) · g(x) dx`

**Come si usa?**
1.  Scegliere quale funzione è il **fattore finito `f(x)`** (da derivare) e quale è il **fattore differenziale `g'(x)`** (da integrare).
2.  Applicare la formula. Si ottiene un nuovo integrale che si spera sia più semplice dell'originale.

**Consiglio per la scelta di `f(x)` (Regola LIATE):**
Scegliere come `f(x)` la funzione che viene prima in questo ordine di priorità:
**L** - Logaritmiche
**I** - Inverse trigonometriche (arcsin, etc.)
**A** - Algebriche (polinomi)
**T** - Trigonometriche (sin, cos)
**E** - Esponenziali

**Esempio:** `∫ x · e^x dx`
1.  Seguendo LIATE, `x` è algebrica (A) ed `e^x` è esponenziale (E). Scelgo:
    `f(x) = x`   →   `f'(x) = 1`
    `g'(x) = e^x` →   `g(x) = ∫ e^x dx = e^x`
2.  Applico la formula:
    `∫ x · e^x dx = x · e^x - ∫ 1 · e^x dx = x · e^x - e^x + c`.
