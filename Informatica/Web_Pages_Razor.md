# 📄 Web Pages con Sintassi Razor

**Razor** non è un linguaggio, ma un **motore di template (templating engine)**. È una sintassi che permette di inserire codice **server-side (C#)** direttamente all'interno del markup **HTML**, in modo pulito e fluido.

---

## ✨ La Magia del Simbolo `@`

Il carattere `@` è il cuore della sintassi Razor. Indica al motore di passare dalla modalità HTML a quella C# e viceversa.

### Usi Principali del Simbolo `@`:

1.  **Visualizzare una variabile:**
    ```csharp
    <p>Il nome dell'utente è: @Model.NomeUtente</p>
    ```

2.  **Eseguire un blocco di codice C#:**
    ```csharp
    @{
        // Blocco di codice C#
        var saluto = "Buongiorno";
        var nome = "Maria";
        var messaggioCompleto = saluto + ", " + nome;
    }
    <p>@messaggioCompleto</p>
    ```

3.  **Strutture di controllo (if, for, foreach):**
    Razor è abbastanza intelligente da capire dove finisce il blocco di codice C# e ricomincia l'HTML.
    ```csharp
    @if (Model.Prodotti.Count > 0)
    {
        <ul>
            @foreach (var prodotto in Model.Prodotti)
            {
                <li>@prodotto.Nome - Prezzo: @prodotto.Prezzo €</li>
            }
        </ul>
    }
    else
    {
        <p>Non ci sono prodotti disponibili.</p>
    }
    ```
---

## 🎯 Il Concetto di "Modello" (`@Model`)

In contesti come Razor Pages o MVC, `@Model` è una parola chiave speciale che rappresenta l'**oggetto dati** passato dal codice C# (il "back-end") alla pagina Razor (il "front-end"). Contiene tutte le informazioni che la pagina deve visualizzare.

**Conclusione:** La sintassi Razor è lo strumento che permette di creare pagine web **dinamiche** in ASP.NET, mescolando la struttura statica dell'HTML con la potenza logica del C#.
