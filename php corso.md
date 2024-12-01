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

- Contatenazionazione fra stringhe con il punto.
Esempio

 ```php

    echo $stringa .$nome
    echo $stringa . " " .$nomen ."ciao";

```
---

# Funzioni su stringhe

## strlen()

Serve per calcolare la lunghezza di una stringa.

 ```php
    echo strlen($stringa)
  ```

## strtolower();

Serve per trasfomare una stringa in minuscolo.

 ```php
    echo strtolower($stringa)
  ```

## strtoupper();

Serve per trasfomare una stringa in maiuscolo.

```php
    echo strtoupper($stringa)
  ```

## trim()

Serve per rimuovere gli spazi bianch inzio o fine che potrebbero darci dei problemi;

```php
    echo trim($stringa)
  ```

## str_word_count()

Serve per conteggiare le parole dentro ad una stringa

```php
    echo str_word_count($stringa)
  ```

## strrev()

Serve per rovesciare una stringa

```php
    echo strrev($stringa)
  ```

## strpos()

Serve cercare una parola in una stringa (ma è case sensitive)

```php
    echo strpos($stringa , 'ciao')
  ```

## substr()

Serve per prendere una parte di stringa 

```php
    echo substr($stringa , 12, 5)
  ```
  
## str_replace ()

Serve per andare a sostituire una parte del testo 

```php
    echo str_replace('PARAMETRO DA SOSTITUIRE', 'PARAMETRO NUOVO', $stringa)
    echo str_replace('ciao', 'ipsum', $stringa)
  ```

##  explode()

Divide una stringa in un array utilizzando un delimitatore.

```php
    $str = "Ciao mondo PHP";
    $array = explode(" ", $str);
    print_r($array);  // Output: Array ( [0] => Ciao [1] => mondo [2] => PHP )
  ```

##  implode()

Unisce gli elementi di un array in una stringa, utilizzando un delimitatore.

```php
   $array = ["Ciao", "mondo", "PHP"];
echo implode(" ", $array);  // Output: Ciao mondo PHP
  ```

## str_split()

Divide una stringa in un array di caratteri.

```php
        $str = "Ciao";
        print_r(str_split($str)); 
  ```
## Variabili 

Le variabili di php sono debolmente tipizzate e non richiedono che tu specifichi il tipo di dato di una variabile quando la dichiari. Il tipo di una variabile è determinato automaticamente in base al valore che le assegnate. <br/>
PHP **effettua una conversione automatica dei tipi (tipo di casting)** quando necessario, ad esempio, quando si confrontano variabili di tipo diverso o si eseguono operazioni tra variabili.

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

---

### Differenza fra define e const

#### Define

La funzione define() viene utilizzata per dichiarare una **costante**. Le costanti sono simili alle variabili ma non possono essere modificate.
<mark>La particolarità del define è che non viene definito con $ come è tipico delle variabili </mark>

Esempio:

define ('NOME COSTANTE', 'VALORE');
define ('indirizzo', 'Via del corso')

<mark>Sono variabili accessibili a tutti</mark>

Con define(), è possibile anche impostare costanti per i valori booleani o per il risultato di espressioni di tipo stringa o numerico

### Const

Le costanti dichiarate con const sono simili a quelle dichiarate con define(), ma ci sono delle differenze nel loro utilizzo e nelle regole di dichiarazione.
const ADDRESS = "via del corso"

**Definizione di costanti:***
- **define()**: Può essere utilizzato ovunque nel codice, anche all'interno di funzioni e file inclusi.

- **const**: Viene utilizzato per definire costanti a livello globale, ma non può essere usato all'interno di funzioni o all'interno di condizioni (eccetto in classi).

| Caratteristica             | `define()`                               | `const`                              |
|----------------------------|------------------------------------------|--------------------------------------|
| **Ambito di dichiarazione**    | Può essere usato ovunque nel codice      | Usato solo in ambito globale o dentro classi |
| **Dichiara costanti in classi** | No                                       | Sì                                   |
| **Valore dinamico**             | Sì (può usare funzioni o espressioni)    | No (deve essere un valore fisso)     |
| **Utilizzo in funzioni**        | Sì                                       | No                                   |
| **Visibilità**                 | Globale     


---

## Var_dump()

Il var_dumpo() ci aiuta a mostrare sullo schermo il tipo di dato 

# Lezione del 01/12/2024

Riprende il corso da [qui](https://www.youtube.com/watch?v=5bQ6y2URNls&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=6&ab_channel=EdoardoMidali)

---


