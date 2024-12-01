# Corso php
## Premessa

Sto seguendo un [corso di php](https://www.youtube.com/watch?v=_WeuUdZQBwI&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=2&ab_channel=EdoardoMidali) per approfondire la mia conoscenza.

Per lavorare in locale sto utilizzando Xamp.
Per raggiungere il progetto bisogna andare su **localhost** oppure su **127.0.0.1** + la cartella del mio progetto.

 > Piccola Nozione :
 >Per inserire la struttura base di html su visual studio ==> ! + tabs

---

## Primo esercizio di php 

Nella nostra pagina html abbiamo creato un piccolo form come riportato qua sotto :

```html
     <form method ="POST" action="esempio.php">
        <label for ="nome">Nome</label>
        <input type ="text" id ="nome" name ="nome">
        <input type="submit" value="invia dati">
    </form>
```

### Come possiamo notare:

Il <mark>**metodo POST**</mark> è stato usato per i nostri dati sensibili <br/>
<mark>Action</mark> esempio.php è dove riporta i dati il form (infatti ho creato una pagina chiamata esempio.php)

### Nella pagina di esempio php :
```php 
     echo "Ciao " . $_POST['nome'];
```

Tramite il metodo post mi sto riprendendo i dati 

---

# Sintassi php

## 3 tipo di variabili:
- **Locali**

- **Globali**

- **Super Globali**

> **Variabili SUPER GLOBALI es $_POST ==> variabili messe a disposizione da php**

## Definizione delle VARIABILI SUPER GLOBALI 

In PHP, le <mark>variabili dichiarate all'esterno delle funzioni sono globali, ma se vuoi accedere a queste variabili all'interno di una funzione, normalmente dovresti usare la parola chiave global o passare la variabile come parametro. Tuttavia, $_GLOBALS ti permette di accedere a tutte le variabili globali senza bisogno di dichiararle come global dentro le funzioni</mark>.

<mark>**$_GLOBALS è un array associativo che mappa il nome della variabile (come stringa) al suo valore**</mark>.

```php 

<?php
$a = 10;  // Variabile globale

function test() {
    // Accesso alla variabile globale 'a' tramite $_GLOBALS
    echo $_GLOBALS['a'];  // Stampa 10
}

test();
```

In questo esempio, la variabile $a è definita a livello globale, e la funzione test() accede al suo valore usando $_GLOBALS['a'] invece di utilizzare la parola chiave global.

Modificare una variabile globale tramite $_GLOBALS:
Puoi anche utilizzare $_GLOBALS per modificare il valore di una variabile globale all'interno di una funzione:

php
Copia codice
<?php
$x = 5;  // Variabile globale

function incrementa() {
    $_GLOBALS['x']++;  // Incrementa la variabile globale 'x' di 1
}

incrementa();
echo $x;  // Stampa 6
?>
In questo esempio, $_GLOBALS['x'] viene utilizzato per accedere e modificare la variabile globale $x all'interno della funzione.

### Riassunto

Le variabili superglobali sono messe a disposizione da php e permettono di poter essere lette anche fuori dalla variabile 







