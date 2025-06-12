# 🔑 Installazione OpenSSL e Creazione Certificati Digitali

**OpenSSL** è una libreria software open-source e uno strumento a riga di comando estremamente potente per lavorare con la crittografia SSL/TLS. Permette di generare chiavi private, creare richieste di certificato, firmare certificati e molto altro.

---

## 🧐 A Cosa Serve Creare Certificati Digitali?

In un ambiente di laboratorio o di sviluppo, spesso non è necessario (o possibile) ottenere un certificato da una Certification Authority (CA) pubblica. Creare i propri certificati permette di:
*   Testare e configurare servizi che richiedono HTTPS (come un web server Apache o Nginx).
*   Creare una propria **CA interna (privata)** per un'azienda, in modo da poter firmare i certificati per i server interni.
*   Comprendere a fondo il funzionamento della Public Key Infrastructure (PKI).

---

## 🚀 I Passaggi per Creare un Certificato Autofirmato (Self-Signed)

Un certificato **autofirmato** è un certificato firmato con la propria chiave privata, invece che da una CA di fiducia. I browser non si fideranno di questi certificati (mostrando un avviso di sicurezza), ma sono perfetti per lo sviluppo.

### Passaggio 1: Generare una Chiave Privata
La prima cosa da fare è creare una chiave privata. L'algoritmo più comune è RSA.
*   **Comando:**
    ```bash
    openssl genpkey -algorithm RSA -out server.key -pkeyopt rsa_keygen_bits:2048
    ```
    *   `genpkey`: Comando per generare una chiave.
    *   `-algorithm RSA`: Specifica l'algoritmo.
    *   `-out server.key`: Salva la chiave privata nel file `server.key`.
    *   `-pkeyopt rsa_keygen_bits:2048`: Specifica la lunghezza della chiave a 2048 bit (un valore comune e sicuro).

### Passaggio 2: Creare una Richiesta di Firma di Certificato (CSR)
Una **CSR (Certificate Signing Request)** è un file che contiene le informazioni sul richiedente (es. il nome del dominio) e la sua chiave pubblica. Questo file viene normalmente inviato a una CA per essere firmato.
*   **Comando:**
    ```bash
    openssl req -new -key server.key -out server.csr
    ```
    *   `req`: Comando per gestire le richieste di certificato.
    *   `-new`: Crea una nuova richiesta.
    *   `-key server.key`: Usa la chiave privata creata in precedenza.
    *   `-out server.csr`: Salva la CSR nel file `server.csr`.
    *   Verranno chieste diverse informazioni, come il Paese, la città e, soprattutto, il **Common Name (CN)**, che deve corrispondere al nome di dominio del server (es. `www.miosito.lab`).

### Passaggio 3: Firmare la Richiesta e Creare il Certificato
In questo caso, useremo la nostra stessa chiave privata per firmare la CSR, creando così un certificato autofirmato.
*   **Comando:**
    ```bash
    openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
    ```
    *   `x509`: Comando per gestire i certificati in formato X.509.
    *   `-req`: Indica che l'input è una CSR.
    *   `-days 365`: Imposta la validità del certificato a 365 giorni.
    *   `-in server.csr`: Specifica il file CSR di input.
    *   `-signkey server.key`: Usa la nostra chiave privata per firmare.
    *   `-out server.crt`: Salva il certificato finale nel file `server.crt`.

A questo punto, i file `server.key` (la chiave privata) e `server.crt` (il certificato pubblico) possono essere usati per configurare un web server per HTTPS.
