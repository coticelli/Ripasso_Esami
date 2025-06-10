# 📉 Studio Completo di una Funzione

Lo studio completo di una funzione `y = f(x)` è una procedura che, attraverso una serie di passaggi standard, permette di analizzare le caratteristiche principali di una funzione e di tracciarne il **grafico qualitativo**.

---

## 🗺️ La Guida Passo-Passo

Ecco i 9 passi fondamentali per uno studio completo:

### 1. **Dominio (o Campo di Esistenza)**
*   **Obiettivo:** Determinare l'insieme di tutti i valori di `x` per cui la funzione è definita.
*   **Cosa fare:** Impostare e risolvere le condizioni di esistenza in base al tipo di funzione:
    *   **Fratta:** Denominatore ≠ 0.
    *   **Irrazionale (indice pari):** Radicando ≥ 0.
    *   **Logaritmica:** Argomento > 0.

### 2. **Simmetrie e Periodicità**
*   **Obiettivo:** Verificare se la funzione è pari, dispari o periodica.
*   **Cosa fare:**
    *   **Funzione Pari:** Se `f(-x) = f(x)`. Il grafico è simmetrico rispetto all'asse y.
    *   **Funzione Dispari:** Se `f(-x) = -f(x)`. Il grafico è simmetrico rispetto all'origine.
    *   **Periodicità:** Si verifica principalmente per le funzioni goniometriche.

### 3. **Intersezioni con gli Assi**
*   **Obiettivo:** Trovare i punti in cui il grafico interseca l'asse x e l'asse y.
*   **Cosa fare:**
    *   **Asse y (ascissa x=0):** Calcolare `f(0)`. Esiste solo se `x=0` appartiene al dominio.
    *   **Asse x (ordinata y=0):** Risolvere l'equazione `f(x) = 0`.

### 4. **Segno della Funzione**
*   **Obiettivo:** Determinare gli intervalli in cui `f(x) > 0` (grafico sopra l'asse x) e `f(x) < 0` (grafico sotto l'asse x).
*   **Cosa fare:** Risolvere la disequazione `f(x) > 0`.

### 5. **Comportamento agli Estremi del Dominio (Limiti e Asintoti)**
*   **Obiettivo:** Studiare cosa fa la funzione quando `x` si avvicina ai punti di frontiera del dominio o tende a `±∞`.
*   **Cosa fare:** Calcolare i limiti.
    *   **Asintoto Verticale:** Se `lim (x→x₀) f(x) = ±∞`, allora la retta `x = x₀` è un asintoto verticale.
    *   **Asintoto Orizzontale:** Se `lim (x→±∞) f(x) = L` (finito), allora la retta `y = L` è un asintoto orizzontale.
    *   **Asintoto Obliquo:** Se non c'è asintoto orizzontale, cercare `y = mx + q` con `m = lim (x→±∞) f(x)/x` e `q = lim (x→±∞) [f(x) - mx]`.

### 6. **Derivata Prima: Monotonia e Punti Stazionari**
*   **Obiettivo:** Determinare dove la funzione cresce o decresce e trovare massimi e minimi relativi.
*   **Cosa fare:**
    1.  Calcolare `f'(x)`.
    2.  Trovare i punti stazionari risolvendo `f'(x) = 0`.
    3.  Studiare il segno di `f'(x)` per trovare gli intervalli di monotonia e classificare i punti stazionari (massimi, minimi, flessi a tangente orizzontale).

### 7. **Studio dei Punti di Non Derivabilità**
*   **Obiettivo:** Analizzare i punti del dominio in cui la funzione non è derivabile.
*   **Cosa fare:** Calcolare il limite destro e sinistro della derivata prima nei punti sospetti (es. dove si annulla il denominatore della derivata) per identificare cuspidi, punti angolosi o flessi a tangente verticale.

### 8. **Derivata Seconda: Concavità e Flessi**
*   **Obiettivo:** Determinare gli intervalli di concavità/convessità e trovare i punti di flesso.
*   **Cosa fare:**
    1.  Calcolare `f''(x)`.
    2.  Trovare i candidati punti di flesso risolvendo `f''(x) = 0`.
    3.  Studiare il segno di `f''(x)` per trovare gli intervalli di concavità e classificare i flessi.

### 9. **Grafico della Funzione**
*   **Obiettivo:** Disegnare un grafico qualitativo.
*   **Cosa fare:** Riportare su un piano cartesiano tutte le informazioni raccolte nei passaggi precedenti e unire i punti in modo coerente.
