# 🐘 Sintassi e Utilizzo di Base di PHP

**PHP (Hypertext Preprocessor)** è uno dei linguaggi di scripting **server-side** più diffusi al mondo. Viene eseguito sul server web e il suo scopo principale è generare pagine web dinamiche.

---

## 🤔 Come Funziona PHP?

1.  Un utente, tramite il suo browser (client), richiede una pagina `.php` a un server web.
2.  Il server esegue il codice PHP contenuto nella pagina.
3.  Lo script PHP può interagire con un database, leggere file, elaborare dati inviati da un form, etc.
4.  L'output dello script viene convertito in **semplice HTML**.
5.  Il server invia la pagina HTML finale al browser dell'utente, che la visualizza.

L'utente finale **non vede mai** il codice PHP, ma solo il risultato della sua esecuzione.

---

## ✍️ Sintassi Fondamentale

### Tag di Apertura e Chiusura
Il codice PHP viene inserito all'interno di file (spesso con estensione `.php`) e delimitato dai seguenti tag:
```php
<?php
    // Qui va il codice PHP
?>
