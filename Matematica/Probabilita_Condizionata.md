# ❓ Probabilità Condizionata e Indipendenza

La **probabilità condizionata** misura la probabilità che un evento `B` si verifichi, **sapendo che** un altro evento `A` si è già verificato. Cambia lo spazio campionario di riferimento.

---

## 🧠 Concetto di Probabilità Condizionata

Si indica con `P(B|A)` e si legge "probabilità di B dato A".

*   **Intuizione:** L'informazione che l'evento `A` è accaduto può modificare la probabilità di `B`. Il nostro nuovo "mondo possibile" non è più l'intero spazio campionario `Ω`, ma si è ridotto all'evento `A`.

### Formula:
La probabilità condizionata di `B` dato `A` (con `P(A) > 0`) è definita come:

`P(B|A) = P(A ∩ B) / P(A)`

Da questa formula deriva la **regola del prodotto** (o della probabilità composta):
`P(A ∩ B) = P(A) · P(B|A)`

**Esempio:** Estrazione senza reinserimento da un'urna con 5 palline bianche (B) e 5 nere (N).
*   `P(1ª Nera) = 5/10`.
*   Qual è la probabilità che anche la seconda sia nera, *sapendo che la prima era nera*?
    `P(2ª Nera | 1ª Nera) = 4/9`, perché ora ci sono 4 nere su un totale di 9 palline.
*   Probabilità che entrambe siano nere: `P(1ªN ∩ 2ªN) = P(1ªN) · P(2ªN | 1ªN) = (5/10) · (4/9) = 20/90`.

---

## ⛓️ Eventi Indipendenti

Due eventi `A` e `B` si dicono **stocasticamente indipendenti** se il verificarsi di uno non influenza la probabilità dell'altro.

### Definizione formale:
Due eventi `A` e `B` sono indipendenti se e solo se:
`P(A ∩ B) = P(A) · P(B)`

**Conseguenze:**
Se `A` e `B` sono indipendenti (e `P(A) > 0`), allora:
`P(B|A) = P(B)`
Sapere che `A` si è verificato non cambia la probabilità di `B`.

**Quando si verifica l'indipendenza?**
*   Estrazioni **con reinserimento** da un'urna.
*   Lanci ripetuti di un dado o di una moneta.
*   Eventi che riguardano esperimenti fisicamente separati.

**Esempio:** Lancio di due dadi. L'evento A="esce 4 al primo lancio" e l'evento B="esce 6 al secondo lancio" sono indipendenti.
*   `P(A) = 1/6`, `P(B) = 1/6`.
*   La probabilità che accadano entrambi è `P(A ∩ B) = P(A) · P(B) = (1/6) · (1/6) = 1/36`.
