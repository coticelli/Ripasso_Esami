# 🔑 Tecniche Crittografiche per la Protezione dei Dati

La **crittografia** è la scienza di scrivere messaggi in codice per renderli incomprensibili a chi non è autorizzato a leggerli. È uno strumento fondamentale per garantire la **riservatezza**, l'**integrità** e l'**autenticazione** dei dati.

---

##  Symmetric vs. Asymmetric Cryptography

### 1. Crittografia Simmetrica (a Chiave Segreta)
*   **Principio:** Viene utilizzata la **stessa chiave** sia per crittografare (cifrare) il messaggio in chiaro (plaintext) sia per decrittografarlo (decrifrare) e ottenere di nuovo il testo in chiaro.
*   **Vantaggi:** Molto **veloce** ed efficiente.
*   **Svantaggio:** Il problema della **distribuzione della chiave**. Come fanno le due parti a scambiarsi la chiave segreta in modo sicuro?
*   **Algoritmi Comuni:**
    *   **DES (Data Encryption Standard):** Un vecchio standard, oggi considerato insicuro a causa della sua chiave a 56 bit.
    *   **3-DES (Triple DES):** Applica DES tre volte per aumentare la sicurezza, ma è lento.
    *   **AES (Advanced Encryption Standard):** Lo standard attuale, considerato molto sicuro e veloce, con chiavi a 128, 192 o 256 bit.

### 2. Crittografia Asimmetrica (a Chiave Pubblica)
*   **Principio:** Utilizza una **coppia di chiavi** matematicamente collegate:
    *   Una **Chiave Pubblica:** Può essere distribuita liberamente a chiunque. Viene usata per **crittografare** i dati.
    *   Una **Chiave Privata:** Deve rimanere segreta e conosciuta solo dal proprietario. Viene usata per **decrittografare** i dati.
*   **Vantaggi:** Risolve il problema della distribuzione della chiave.
*   **Svantaggio:** Molto più **lenta** e computazionalmente intensiva rispetto alla crittografia simmetrica.
*   **Algoritmo Comune:**
    *   **RSA (Rivest-Shamir-Adleman):** L'algoritmo più famoso, basato sulla difficoltà di fattorizzare numeri molto grandi.

**Uso Ibrido:** Nella pratica (es. in HTTPS), si usa un sistema ibrido: la crittografia asimmetrica viene usata solo per scambiare in modo sicuro una chiave di sessione simmetrica, e poi la comunicazione vera e propria avviene usando la crittografia simmetrica, che è più veloce.

---

## ✒️ Firma Digitale e Certificati

### Firma Digitale
*   **Scopo:** Garantire l'**autenticità** (chi ha inviato il messaggio), l'**integrità** (il messaggio non è stato alterato) e il **non ripudio** (il mittente non può negare di averlo inviato).
*   **Come funziona (usando crittografia asimmetrica):**
    1.  Il mittente calcola un **hash** del messaggio.
    2.  Crittografa l'hash con la propria **chiave privata**. Il risultato è la firma digitale.
    3.  Il mittente invia il messaggio originale insieme alla firma digitale.
    4.  Il destinatario decrittografa la firma con la **chiave pubblica** del mittente (ottenendo l'hash originale) e ricalcola l'hash del messaggio ricevuto. Se i due hash corrispondono, la firma è valida.

### Certificato Digitale (Standard X.509)
*   **Il Problema:** Come faccio a fidarmi che una chiave pubblica appartenga davvero a chi dice di essere?
*   **La Soluzione:** Un **certificato digitale** è un "documento d'identità" elettronico che lega un'identità (una persona, un sito web) a una chiave pubblica.
*   **Come funziona:** È emesso da un'entità di fiducia chiamata **Certification Authority (CA)** (es. Let's Encrypt, DigiCert), che verifica l'identità del richiedente e poi "firma" il certificato con la propria chiave privata.
*   I browser e i sistemi operativi hanno una lista preinstallata di CA attendibili. Quando visitiamo un sito HTTPS, il nostro browser controlla la validità del certificato e la firma della CA per autenticare il server.
