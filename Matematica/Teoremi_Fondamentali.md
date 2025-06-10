# 🔄 Prove Ripetute e Calcolo Combinatorio

Molti problemi di probabilità coinvolgono il contare il numero di modi in cui certi eventi possono accadere. Il calcolo combinatorio ci fornisce gli strumenti per fare questo, mentre lo schema delle prove ripetute analizza esperimenti con due soli esiti.

---

## 🧮 Strumenti di Calcolo Combinatorio

### 1. Permutazioni Semplici
*   **Domanda:** In quanti modi si possono ordinare `n` oggetti distinti?
*   **Formula:** `Pₙ = n!` (n fattoriale)
    `n! = n · (n-1) · (n-2) · ... · 2 · 1`
*   **Esempio:** Gli anagrammi della parola "CIAO" sono `4! = 24`.

### 2. Disposizioni Semplici
*   **Domanda:** In quanti modi si possono scegliere e ordinare `k` oggetti da un insieme di `n` oggetti distinti? (L'ordine conta).
*   **Formula:** `D(n, k) = n · (n-1) · ... · (n-k+1) = n! / (n-k)!`
*   **Esempio:** In quanti modi 3 persone possono sedersi su 5 sedie? `D(5,3) = 5·4·3 = 60`.

### 3. Combinazioni Semplici
*   **Domanda:** In quanti modi si possono scegliere `k` oggetti da un insieme di `n` oggetti distinti? (L'ordine NON conta).
*   **Formula (Coefficiente Binomiale):**
    `C(n, k) = D(n, k) / k! = n! / [ k! · (n-k)! ]` (si legge "n su k")
*   **Esempio:** Quante possibili cinquine si possono fare al Lotto (estratti 5 numeri da 90)? `C(90, 5)`.

---

## 🎯 Schema delle Prove Ripetute (o di Bernoulli)

Questo schema si applica a un esperimento che ha queste caratteristiche:
1.  Viene ripetuto `n` volte.
2.  Ogni prova è **indipendente** dalle altre.
3.  Ogni prova ha solo **due possibili esiti**: "successo" (S) o "insuccesso" (I).
4.  La probabilità di successo `p` e di insuccesso `q = 1-p` è **costante** in ogni prova.

### Formula di Bernoulli:
La probabilità di ottenere **esattamente `k` successi in `n` prove** è data da:

`P(k successi su n prove) = C(n, k) · pᵏ · qⁿ⁻ᵏ`

**Spiegazione della formula:**
*   `C(n, k)`: Calcola in quanti modi si possono disporre i `k` successi nelle `n` posizioni.
*   `pᵏ`: È la probabilità di ottenere `k` successi.
*   `qⁿ⁻ᵏ`: È la probabilità di ottenere `(n-k)` insuccessi.

**Esempio:** Lancio 5 volte un dado non truccato. Qual è la probabilità che il numero "6" (successo) esca esattamente 2 volte?
*   `n = 5` (prove)
*   `k = 2` (successi)
*   `p = 1/6` (prob. di successo, "esce 6")
*   `q = 5/6` (prob. di insuccesso, "non esce 6")

`P(k=2) = C(5, 2) · (1/6)² · (5/6)³ = 10 · (1/36) · (125/216) ≈ 0.16` (circa il 16%).
