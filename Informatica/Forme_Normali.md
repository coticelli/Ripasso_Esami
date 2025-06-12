# 🗃️ Le Forme Normali per la Normalizzazione

La **normalizzazione** è un processo di progettazione dei database relazionali che ha l'obiettivo di ridurre la **ridondanza dei dati** e di eliminare le **anomalie** di inserimento, aggiornamento e cancellazione. Questo processo si attua applicando una serie di regole chiamate **Forme Normali**.

---

## 🤔 Perché Normalizzare?

Un database non normalizzato può soffrire di tre tipi di anomalie:
1.  **Anomalia di Inserimento:** Impossibilità di inserire un'informazione su un'entità se non è associata a un'altra.
    *   *Esempio:* Non posso inserire un nuovo cliente se non ha ancora fatto un ordine.
2.  **Anomalia di Aggiornamento:** Se un dato è replicato in più punti, un aggiornamento potrebbe essere eseguito solo su alcune occorrenze, creando inconsistenze.
    *   *Esempio:* L'indirizzo di un cliente è replicato per ogni suo ordine. Se cambia indirizzo, devo aggiornarlo in ogni record d'ordine.
3.  **Anomalia di Cancellazione:** La cancellazione di un record può causare la perdita involontaria di altre informazioni.
    *   *Esempio:* Se un cliente ha fatto un solo ordine e cancello quell'ordine, perdo anche tutte le informazioni del cliente.

La normalizzazione risolve questi problemi organizzando gli attributi in tabelle ben strutturate.

---

## 🥇 Prima Forma Normale (1FN)

*   **Regola:** Una tabella è in 1FN se **tutti i suoi attributi sono atomici**, cioè non possono essere ulteriormente scomposti. Ogni cella deve contenere un singolo valore.
*   **Obiettivo:** Eliminare i gruppi ripetuti.
*   **Cosa NON fare:** Avere una colonna "NumeriDiTelefono" che contiene più numeri in una singola cella.
*   **Soluzione:** Creare righe separate per ogni valore o, meglio, una tabella separata `Telefoni` collegata tramite chiave esterna.

**Esempio:**

| ID_Studente | Nome  | Corsi_Seguiti           |
| :---------- | :---- | :---------------------- |
| 1           | Mario | "Matematica, Fisica"    |  **NON in 1FN** ❌

**Corretto (in 1FN):**
*Tabella Studenti*
| ID_Studente | Nome  |
| :---------- | :---- |
| 1           | Mario |
*Tabella Iscrizioni*
| ID_Studente | Corso       |
| :---------- | :---------- |
| 1           | Matematica  |
| 1           | Fisica      |

---

## 🥈 Seconda Forma Normale (2FN)

*   **Prerequisito:** La tabella deve essere già in 1FN.
*   **Regola:** Tutti gli attributi non-chiave devono dipendere funzionalmente dall'**intera chiave primaria**, non solo da una sua parte.
*   **Obiettivo:** Eliminare le dipendenze parziali. Si applica solo a tabelle con **chiavi primarie composte** (formate da più di una colonna).

**Esempio:** Chiave Primaria: `(ID_Studente, ID_Corso)`
| ID_Studente | ID_Corso | Nome_Studente | Voto |
| :---------- | :------- | :------------ | :--- |
| 1           | C101     | Mario Rossi   | 28   | **NON in 2FN** ❌
*Problema:* `Nome_Studente` dipende solo da `ID_Studente`, non dall'intera chiave `(ID_Studente, ID_Corso)`. Questo causa ridondanza.

**Corretto (in 2FN):**
*Tabella Studenti*
| ID_Studente | Nome_Studente |
| :---------- | :------------ |
| 1           | Mario Rossi   |
*Tabella Esami*
| ID_Studente | ID_Corso | Voto |
| :---------- | :------- | :--- |
| 1           | C101     | 28   |

---

## 🥉 Terza Forma Normale (3FN)

*   **Prerequisito:** La tabella deve essere già in 2FN.
*   **Regola:** Nessun attributo non-chiave deve dipendere funzionalmente da un altro attributo non-chiave. Devono dipendere solo dalla chiave primaria.
*   **Obiettivo:** Eliminare le **dipendenze transitive**.

**Esempio:** Chiave Primaria: `ID_Ordine`
| ID_Ordine | ID_Cliente | Nome_Cliente | Data       |
| :-------- | :--------- | :----------- | :--------- | **NON in 3FN** ❌
*Problema:* `Nome_Cliente` dipende da `ID_Cliente`, che non è la chiave primaria. Si ha la dipendenza transitiva `ID_Ordine` → `ID_Cliente` → `Nome_Cliente`.

**Corretto (in 3FN):**
*Tabella Clienti*
| ID_Cliente | Nome_Cliente |
| :--------- | :----------- |
| C_01       | Paolo Verdi  |
*Tabella Ordini*
| ID_Ordine | ID_Cliente | Data       |
| :-------- | :--------- | :--------- |
| O_123     | C_01       | 2023-10-26 |
