# Corso php

## Premessa
[corso di php](https://www.youtube.com/watch?v=_WeuUdZQBwI&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=2&ab_channel=EdoardoMidali).

Per lavorare in locale sto utilizzando Xamp.
Per raggiungere il progetto bisogna andare su **localhost** oppure su **127.0.0.1** + la cartella del mio progetto.

 > Piccola Nozione :
 > Per inserire la struttura base di html su visual studio ==> ! + tabs

---

# Tecniche di Stampa in PHP

echo, print - Per l'output di base (stringhe, variabili, ecc.)

print_r(), var_dump() - Per il debug e la visualizzazione di variabili complesse (array, oggetti)

printf(), sprintf() - Per formattare e stampare variabili

var_export() - Per stampare una rappresentazione leggibile di una variabile

| Funzione      | Supporta più argomenti? | Restituisce valore? | Usa principale                           |
|---------------|-------------------------|---------------------|------------------------------------------|
| `echo`        | ✅ Sì (separati da virgole)  | ❌ No               | Stampa veloce e generica                 |
| `print`       | ❌ No                    | ✅ Sì (sempre `1`)   | Quasi mai usato, meno efficiente di `echo`|
| `print_r()`   | ❌ No                    | ✅ Sì (se `true` come 2° parametro) | Debug di array e oggetti                |
| `var_dump()`  | ❌ No                    | ❌ No               | Debug avanzato di variabili (tipo e valore) |

---

#   Sintassi PHP
isset ==> Sarebbe If set => Serve per sapere se è stato settato qualcosa

$_SERVER['PHP_SELF'] ==> ricarica la pagina php

- Contatenazionazione 

 ```php

    echo $stringa . $nome
    echo $stringa . " " .$nome ."ciao";

```

---
## Cast 

 Con il termine CAST, ci riferiamo alla conversione di un tipo di dato in un altro.

str_replace() è una funzione che sostituisce parti di una stringa con altre. Non effettua un vero e proprio cast, ma manipola il contenuto testuale.

$valore = "123.45";
$intVal = (int) $valore;   // Convertito in intero (123)
$floatVal = (float) $valore; // Convertito in float (123.45)
$stringVal = (string) $valore; // Convertito in stringa

# Funzioni su stringhe

## strlen()

Serve per calcolare la lunghezza di una stringa.

 ```php
    echo strlen($stringa)

  ```
##strval()
##number_format()

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

Serve per rimuovere gli spazi bianchi inzio o fine che potrebbero darci dei problemi;

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
    print_r($array);
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
---

## Variabili 

Le variabili di php sono **debolmente tipizzate e non richiedono che tu specifichi il tipo di dato** di una variabile quando la dichiari.
Il tipo di una variabile è determinato automaticamente in base al valore che le assegnate. <br/>
PHP **effettua una conversione automatica dei tipi (tipo di casting)** quando necessario, ad esempio, quando si confrontano variabili di tipo diverso o si eseguono operazioni tra variabili.

## 3 tipo di variabili:

- **Locali**

- **Globali**

- **Super Globali**

> **Variabili SUPER GLOBALI es $_POST ==> variabili messe a disposizione da php**

## Definizione delle VARIABILI SUPER GLOBALI 

In PHP, le <mark>variabili dichiarate all'esterno delle funzioni sono globali, ma se vuoi accedere a queste variabili all'interno di una funzione, normalmente dovresti usare la parola chiave **global** o passare la variabile come parametro. Tuttavia, **$_GLOBALS** ti permette di accedere a tutte le variabili globali senza bisogno di dichiararle come global dentro le funzioni</mark>.

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

> In questo esempio, la variabile $a è definita a livello globale, e la funzione test() accede al suo valore usando $_GLOBALS['a'] invece di utilizzare la parola chiave global.

Modificare una variabile globale tramite $_GLOBALS:
Puoi anche utilizzare $_GLOBALS per modificare il valore di una variabile globale all'interno di una funzione:

```php 

<?php
$x = 5;  // Variabile globale

function incrementa() {
    $_GLOBALS['x']++;  // Incrementa la variabile globale 'x' di 1
}

incrementa();
echo $x;  // Stampa 6
?>

```
In questo esempio, $_GLOBALS['x'] viene utilizzato per accedere e modificare la variabile globale $x all'interno della funzione.

### Riassunto

**Le variabili superglobali sono messe a disposizione da php e permettono di poter essere lette anche fuori dalla variabile**

---

### Differenza fra define e const

#### Define()

La funzione define() viene utilizzata per dichiarare una **costante**.<br/>
<mark>**Le costanti sono simili alle variabili ma non possono essere modificate.**</mark>
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

Il var_dump() ci aiuta a mostrare sullo schermo il tipo di dato 
Può essere utilizzato anche per capire se un numero è intero o no tipo var_dump(is_float($numero )) o var_dump(is_int())

## print_r()

print_r() è una funzione in PHP utilizzata per stampare in modo leggibile il contenuto di una variabile, in particolare per esaminare il contenuto di array o oggetti. È molto utile durante il debugging per vedere come sono strutturati i dati.

# Lezione del 01/12/2024

Riprende il corso da [qui](https://www.youtube.com/watch?v=5bQ6y2URNls&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=6&ab_channel=EdoardoMidali)

---
# Lezione del 02/12/2024

# Array
Array è una collezione di elementi.

Dichiarare un array:

``` php 

$citta = array('milano','roma')
$citta = ['roma','Milano']

for($i= 0; $i < count($citta); i++){
  echo $citta[i]
}

```
## metodi sort() e rsort()
Metodo per ordinare un array

**sort()** in ordine crescente 

**rsort** è reverse sort

``` php 

sort($citta)

```

# Array associativi

Un array associativo in PHP è una <mark>struttura dati che consente di memorizzare valori associandoli a chiavi personalizzate</mark>, invece di utilizzare solo indici numerici come negli array normali. È particolarmente utile per rappresentare coppie chiave-valore.

Serve per :

- Rappresentare dati strutturati
- Rendere il codice più leggibile
- Mappare valori

Esempio di array associativo 

``` php  

$persona = [
  "nome" = "Eleonora",
  "età" = 23
]
$echo $persona ["nome"]

```

## loop foreach

Il costrutto foreach è <mark>utilizzato per iterare su tutti gli elementi di un array (sia indicizzati che associativi)</mark>. Con un array associativo, il foreach permette di accedere sia alla chiave che al valore di ogni elemento.


``` php 

foreach ($array as $chiave => $valore) {
    // Codice che utilizza $chiave e $valore
}

$persona = [
    "nome" => "Mario",
    "cognome" => "Rossi",
    "età" => 30
];

foreach ($persona as $chiave => $valore) {
    echo "La chiave è $chiave e il valore è $valore\n";
}

```

# Array multidimensionali 

Un array multidimensionale è essenzialmente un array all'interno di un altro array. Ogni elemento può essere un array numerico, un array associativo o una combinazione di entrambi.

## Metodi per ordinare Arry associativi per chiave k => chiave 

ksort() in ordine crescente 
krsort è reverse sort

## Metodi per ordinare Arry associativi per chiave a => valore

ksort() in ordine crescente 
krsort è reverse sort

# array_push() array_pop() array_unchift() array_shift()

array_push() ($citta, 'Napoli') ==> inserito nuovo elemento

array_pop($citta) ==> togliere ultimo elemento 

array_unshift() ($citta, 'Napoli') ==> aggiunge un elemento in avanti 
 
array_shift() ==> toglie il primo elemento 

---

# Funzioni

Le funzioni sono un blocco di codice riutilizzabili nel tempo. Possiamo creare delle funzioni anonime. Le variabili all'interno di una funzione valgono solo dentro alla funzione. il modo per richiamare una variabile anche fuori è $GLOBALS['numero']. Però non è consigliato. Bisogna utilizzare return.
dentro le parentesi tonde vanne messi degli argomenti. Sarebbe meglio tipizzare le funzioni

``` php  
$prova = function(){
  echo 'ciao';
}

$prova();

function somma(int $valore1, int $valore2 ): inte{
  $somma = $valore1 + $valore2;
  return $somma;
}

echo $somma
```

tipizzando così i valori il return potrebbe dare qualche errore più specifico


Riprende il corso da [qui](https://www.youtube.com/watch?v=zeCA3XHt-mo&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=12&ab_channel=EdoardoMidali)
---

# DATE 
Le date si basano tutti da **"UNIX Timestamp"** che è una unità di misura universale e che parte dal <mark>"1 Gennaio 1970 00:00:00"</mark>.
Tutti i computer hanno all'interno questa data ed infatti tramide **DATE()** puoi calcolare la quantità dei secondi passati da quella data.

## DATE()
Esempio di utilizzo di DATE();

``` php 
$data = date('d-m-Y' , 0);
echo $data 
```
Con echo darà 1970 (da dove tutto è partito)

## Legenda per il formato della data

d - Numero del giorno
D - Nome giorno abbreviato 
l - Nome completo
m - Numero del mese 
M - Nome del mese 
y - Anno con due cifre finali
Y - Anno con 4 cifre

## Legenda per il formato del tempo 

h - Ore in formato da 12(anglosassone) quindi serve l'aggiunta di **am e pm**
H - Ore in formato da 24( le nostre). ESEMPIO date('h:i:sa')
i - Minuti
s - Secondi
a - Am e pm in minuscolo
A - Am e ph in maiuscolo 

# TIMESTAMP CORRENTE

## time() per ottenere il tempo corrente 

``` php 

$data = date('d-m-Y H:i:s' , time());

echo $data;

```

## mktime()  per ottenere timestamp da una data 

``` php
$data = mktime( 14, 49, 00, 12, 09, 2024);

``` 
Se fai a fare un echo è un timestamp da oggi 

## strtotime()

Passa dalla stringa al tempo

 ``` php

$data = strtotime('09-12-2024')

$data = date('d-m-Y', strtotime("now" +7 days"));

 ```

# INCLUDERE FILE PHP

## REQUIRE() 
Inserire un file con require() significa che il file deve essere obbligatoriamente richiamato.

 ```php
<?php

require('esempio.php');

?>
 ```

 ## INCLUDE() 
 Con include invece il file verrà cercato ma se non è presente non è problema

 ```php
<?php

include('esempio.php');

?>
 ```
---

#REGEX
REGULAR EXPRESSION 

Le regex (espressioni regolari) in PHP sono uno strumento potente per la ricerca, il confronto e la manipolazione di stringhe. Puoi usarle per verificare se una stringa soddisfa un certo schema, estrarre informazioni o fare sostituzioni.

## Sintassi 
. * + [] () {} ^ $ | \

[] ==> classi di caratteri che vogliamo trovare 
[^] ==> classe di caratteri negato 

[a-z] ==> creare un pattern /tutti i caratteri minuscoli dalla a alla z
[A-Z] ==> Tutti i caratteri maiuscoli
[a-Z] ==> Tutti i caratteri sia in maiuscolo che in minuscolo
[0-9] ==> tutti i numeri dallo 0 al 9
[a-z0-9] ==> Tutti i caratteri non speciali

## Classe predefinite 
\d ==> Shortcut da [0-9]
\D ==> S. nega da [0-9]
\s ==> S. toglie tab, newline, spazi
\w ==> S. prende tutti i caratteri
|W ==> S. nega tutti i caratteri 


## Quantificatori 
Permettono di moltiplicare i caratteri che stiamo guardando

p+ ==> ona o più p
p* ==> zero o più occorrenze della lettera p
p? 0 o una
p{2} Esattamente
p{2,3} almeno due p max 3
p{,3} Massimo  3

## Ancora

Ci aiuta a capire se è all'inizio o alla fine della frase

^p all'inzio
p$ alla fine

## Caratteri speciali 
Questi sono i caratteri speciali principali usati nelle regex:

| **Carattere** | **Significato**                                                                 |
|---------------|---------------------------------------------------------------------------------|
| `.`           | Qualsiasi carattere eccetto una nuova riga.                                     |
| `^`           | Inizio della stringa (o inizio di una linea in modalità multilinea).            |
| `$`           | Fine della stringa (o fine di una linea in modalità multilinea).                |
| `*`           | Zero o più ripetizioni dell'elemento precedente.                                |
| `+`           | Una o più ripetizioni dell'elemento precedente.                                 |
| `?`           | Zero o una ripetizione dell'elemento precedente.                                |
| `{n}`         | Esattamente `n` ripetizioni dell'elemento precedente.                           |
| `{n,}`        | Almeno `n` ripetizioni.                                                        |
| `{n,m}`       | Tra `n` e `m` ripetizioni.                                                     |
| `[]`          | Definisce una classe di caratteri. Es.: `[a-z]` indica un intervallo di lettere minuscole. |
| `()`          | Raggruppamento e cattura.                                                      |
| `\`           | Carattere di escape per specificare caratteri speciali. Es.: `\.` corrisponde a un punto reale. |


## preg_match
Cerca una corrispondenza con la regex in una stringa.

## preg_match_all

Cerca **tutte** le corrispondenze.

ESEMPIO
 ```php
$testo = "Oggi è una bella giornata"
$pattern = "/è/";
$matches = preg_match_all($pattern, $testo, $array);
echo $matches . "match che sono stati trovati.";
 ```

## preg_replace

Sostituisce le corrispondenze trovate.

## preg_split
Divide una stringa in base a uno schema.

Esempio 
 ```php
$pattern = '/\d+/'; // Cerca uno o più numeri.
$string = 'Oggi è il 9 dicembre 2024';
if (preg_match($pattern, $string, $matches)) {
    echo "Trovato: " . $matches[0]; // Restituisce la prima corrispondenza.
}
 ```
## preg_grep()

 ```php
i ==> modificatore regex ( case sesitive)

$pattern = "/^M/i";
$names = array["Marco Rossi", "Giovanni Allevi"];
$matches =preg_grep($pattern, $names);

foreach($matches as $match){
  echo $match . <"br">
}
 ```

## Modificatori delle regex
I modificatori sono aggiunti dopo il delimitatore di chiusura (/) per modificare il comportamento della regex.

| **Carattere** | **Significato**                                                                 |
|---------------|---------------------------------------------------------------------------------|
| `.`           | Qualsiasi carattere eccetto una nuova riga.                                     |
| `^`           | Inizio della stringa (o inizio di una linea in modalità multilinea).            |
| `$`           | Fine della stringa (o fine di una linea in modalità multilinea).                |
| `*`           | Zero o più ripetizioni dell'elemento precedente.                                |
| `+`           | Una o più ripetizioni dell'elemento precedente.                                 |
| `?`           | Zero o una ripetizione dell'elemento precedente.                                |
| `{n}`         | Esattamente `n` ripetizioni dell'elemento precedente.                           |
| `{n,}`        | Almeno `n` ripetizioni.                                                        |
| `{n,m}`       | Tra `n` e `m` ripetizioni.                                                     |
| `[]`          | Definisce una classe di caratteri. Es.: `[a-z]` indica un intervallo di lettere minuscole. |
| `()`          | Raggruppamento e cattura.                                                      |
| `\`           | Carattere di escape per specificare caratteri speciali. Es.: `\.` corrisponde a un punto reale. |


Ritornare [Qui](https://www.youtube.com/watch?v=nkWMaGB6TTY&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=14&ab_channel=EdoardoMidali)

---


# METODO GET E METODO POST

## POST

Il metodo POST serve per trasmettere delle informazioni sensibili.
> Nel form prende name
esempio 

 ```php

if ($_SERVER["REQUEST_METHOD"] == "POST"){
    $nome = htmlspecialchars($_POST['nome']);
    $regex = '/^[_a-z0-9-]+(\.[_a-z0-9-]+)*@[a-z0-9-]+(\.[a-z0-9-]+)*(\.[a-z]{2,3})$/'; 
    if (preg_match($regex, $nome)){
  echo('Indirizzo email valido');}
else{
  echo('Indirizzo email non valido');}
}

<form method="POST" action="">
<input type="text" id="nome" name="nome">
<input type ="submit" value ="ok" id="bottone">
</form>
 ```

Questo non comparirà a schermo

## GET

Il metodo get serve per stampare informazioni nell'url quindi informazioni che non hanno problemi se vengono trovare.

ESEMPIO

 ```php
$nomeBat =isset($_GET['nomebat']);
$cognome = isset($_GET['cognome']);

echo $nomeBat . $cognome;

<form method="GET" action="">
    <input type="text" id="nomebat" name ="nomebat">
    <input type="text" id="cognome" name="cognome">
    <input type="submit" value="invia">
</form>
 ```
---

# Lavorare con i file

fopen ==> Aprire un file 

## Modalità di apertura

r ==> Leggere

r+ ==> Leggere e scrivere 

w ==> Scrivere ( ma va a pulire il file e scrivere la parte nuova) 

w+ ==> leggere e scrivere 

a ==> Append (attaccca sotto. Se non trova il file lo crea)

a+ ==> append più read ==> preserva il contenuto ma se non lo trova lo cerca di trovare

x => solo scrive ci da un errore se va a scrivere ( controllo se esiste sennò errre)

x+ ==> + read 


fread ==> Aprire il file

fread ($file, "20") ==> prende le prime 20 lettere

fread ($file, filesize($nomeFile))

file_get_contents($nomeFile)

file_put_contents ($nomeFile, $testo)

fwrite ==> Per scrivere sopra. Ma non legge il file

rename($nomeFile, "nome_nuovo.txt") ==> Rinomina il file 

unlink($nomeFile) ==>  Eliminare un file con unlink 


# Gestire Cartella

Approfondire il discorso.
Ho saltato lezione 17 e lezione 18

mkdir = Creazione Cartella 

Riprende il corso da [qui](https://www.youtube.com/watch?v=2ydO5IvUoT0&list=PLP5MAKLy8lP_zqdyjNaPjh95NG40Op8he&index=17&ab_channel=EdoardoMidali)

# Cosa sono i Cookie

File di testo che vengono salvati sul pc dell'utente. Dati non sensibili

setcookie("username" , "Luca", time()+60*60*24*30); ==> Creare un cookie;

name ==> nome del cookie

value ==> Valore del cookie (Esempio Luca)

path ==> Dove sarà dispoibile

# Sessioni 

Sono comparazioni con i cookie


session_start();

$_SESSION["user_id"] = 23;

echo $_SESSION["user_id"] ;

unset($_SESSION["user_id"]);

session_destroy();

# JSON

**JSON è un formato testuale per rappresentare dati strutturati, derivato da JavaScript, ma utilizzabile con quasi tutti i linguaggi di programmazione.**

## Caratteristiche principali
- Leggibile da umani e macchine.
- Leggero per la trasmissione dati.
- Strutturato come coppie chiave-valore.
- Standardizzato (RFC 8259).

## Struttura base

Tipi di dati supportati

- Oggetti: Raccolte di coppie chiave-valore racchiuse in {}.
- Array: Liste ordinate racchiuse in [].
- Valori primitivi:
- Stringhe ("testo")
- Numeri (42, 3.14)
- Booleani (true, false)
- Null (null)

Esempio semplice

{
  "nome": "Mario",
  "eta": 30,
  "lingue": ["italiano", "inglese"],
  "isStudente": false,
  "indirizzo": {
    "citta": "Roma",
    "CAP": "00100"
  }
}

## Vantaggi dell'utilizzo di JSON

Compatibilità multi-linguaggio: Supportato dalla maggior parte dei linguaggi di programmazione.
Efficiente: Richiede meno spazio rispetto ad altri formati come XML.
Leggibile: Più facile da leggere rispetto ad altri formati strutturati.

## Funzioni principali in PHP per JSON
PHP fornisce due funzioni principali:

json_encode(): Per convertire un array o un oggetto PHP in una stringa JSON.
json_decode(): Per convertire una stringa JSON in un array o oggetto PHP.

## Convertire array PHP in JSON

<?php
$data = [
    "nome" => "Mario",
    "eta" => 30,
    "lingue" => ["italiano", "inglese"]
];

$json = json_encode($data);
echo $json;
// Output: {"nome":"Mario","eta":30,"lingue":["italiano","inglese"]}
?>

## Convertire JSON in oggetto PHP


$json = '{"nome":"Mario","eta":30,"lingue":["italiano","inglese"]}';

$data = json_decode($json); // Senza `true`, restituisce un oggetto
echo $data->nome;
// Output: Mario
?>

## Funzioni principali 

- json_encode(): Per convertire un array o un oggetto PHP in una stringa JSON.
- json_decode(): Per convertire una stringa JSON in un array o oggetto PHP.
- JSON_PRETTY_PRINT: Indenta il JSON per renderlo leggibile.
- JSON_UNESCAPED_SLASHES: Non escapa le barre (/).
- JSON_UNESCAPED_UNICODE: Non escapa i caratteri Unicode.
- JSON_NUMERIC_CHECK: Converte stringhe numeriche in numeri.

## Gestione di errori
Principali errori JSON
Ecco alcune costanti di errore che json_last_error() può restituire:

JSON_ERROR_NONE: Nessun errore.
JSON_ERROR_SYNTAX: Errore di sintassi.
JSON_ERROR_UTF8: Problemi con la codifica UTF-8.






