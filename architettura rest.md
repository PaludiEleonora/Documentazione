# Architettura REST o RESTful?

## Definizione di REST
REST (Representational State Transfer) è uno stile di architettura per la progettazione di sistemi distribuiti, come le API.
L’idea principale è di usare le operazioni standard del protocollo **HTTP (GET, POST, PUT, DELETE)** per interagire con le risorse (dati).

## Caratteristiche principali delle API RESTful
Per essere "RESTful", una API deve rispettare alcune regole:

- Risorse identificate tramite URI
Ogni "risorsa" (es. un utente, un prodotto) deve avere un URI unico.
Esempio:
/users → lista di utenti
/users/123 → utente con ID 123

- Stateless
Ogni richiesta al server deve essere indipendente e contenere tutte le informazioni necessarie (ad esempio, autenticazione tramite token o dati nel body della richiesta).
Non si mantengono dati di sessione sul server.

- Operazioni HTTP

Le operazioni sulle risorse sono mappate ai metodi HTTP:

GET → Recupera risorse

POST → Crea nuove risorse

PUT o PATCH → Aggiorna risorse esistenti

DELETE → Elimina risorse

## Formati standard

I dati scambiati tra client e server sono tipicamente in formato **JSON o XML**, con JSON come formato più comune.

## Codice di stato HTTP

Le risposte includono codici di stato per indicare il successo o il fallimento dell'operazione:
**200 OK → Operazione riuscita**
**201 Created → Risorsa creata**
**404 Not Found → Risorsa non trovata**
**500 Internal Server Error → Errore del server**

## Come creare una API RESTful con PHP**
Ecco una guida passo-passo per creare una semplice API RESTful in PHP.

Scenario
Creeremo una API per gestire una lista di utenti. Le funzionalità includono:

Recuperare la lista degli utenti (GET).
Aggiungere un utente (POST).
Aggiornare un utente (PUT).
Eliminare un utente (DELETE).
Passo 1: Struttura del progetto
Crea la seguente struttura per il progetto:


project/
├── api/
│   └── users.php
└── database/
    └── db.php
Passo 2: Connettiamoci al database
Nel file db.php, configuriamo la connessione al database.

php
Copia codice
<?php
class Database {
    private $host = "localhost";
    private $db_name = "api_db";
    private $username = "root";
    private $password = "";
    public $conn;

    public function getConnection() {
        $this->conn = null;

        try {
            $this->conn = new PDO("mysql:host=" . $this->host . ";dbname=" . $this->db_name, $this->username, $this->password);
            $this->conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        } catch(PDOException $exception) {
            echo "Connection error: " . $exception->getMessage();
        }

        return $this->conn;
    }
}
?>
Passo 3: Creiamo il file users.php
Questo file gestirà tutte le richieste relative agli utenti.

php
Copia codice
<?php
header("Content-Type: application/json");

// Inclusione del database
include_once '../database/db.php';

$database = new Database();
$conn = $database->getConnection();

// Recuperiamo il metodo HTTP
$method = $_SERVER['REQUEST_METHOD'];

// Gestiamo le richieste
switch ($method) {
    case 'GET':
        // Recupera utenti
        $stmt = $conn->prepare("SELECT * FROM users");
        $stmt->execute();
        $users = $stmt->fetchAll(PDO::FETCH_ASSOC);
        echo json_encode($users);
        break;

    case 'POST':
        // Aggiunge un utente
        $data = json_decode(file_get_contents("php://input"));
        $stmt = $conn->prepare("INSERT INTO users (name, email) VALUES (:name, :email)");
        $stmt->bindParam(':name', $data->name);
        $stmt->bindParam(':email', $data->email);

        if ($stmt->execute()) {
            echo json_encode(["message" => "Utente aggiunto con successo!"]);
        } else {
            echo json_encode(["message" => "Errore nell'aggiunta dell'utente."]);
        }
        break;

    case 'PUT':
        // Aggiorna un utente
        $data = json_decode(file_get_contents("php://input"));
        $stmt = $conn->prepare("UPDATE users SET name = :name, email = :email WHERE id = :id");
        $stmt->bindParam(':name', $data->name);
        $stmt->bindParam(':email', $data->email);
        $stmt->bindParam(':id', $data->id);

        if ($stmt->execute()) {
            echo json_encode(["message" => "Utente aggiornato con successo!"]);
        } else {
            echo json_encode(["message" => "Errore nell'aggiornamento dell'utente."]);
        }
        break;

    case 'DELETE':
        // Elimina un utente
        $data = json_decode(file_get_contents("php://input"));
        $stmt = $conn->prepare("DELETE FROM users WHERE id = :id");
        $stmt->bindParam(':id', $data->id);

        if ($stmt->execute()) {
            echo json_encode(["message" => "Utente eliminato con successo!"]);
        } else {
            echo json_encode(["message" => "Errore nella cancellazione dell'utente."]);
        }
        break;

    default:
        echo json_encode(["message" => "Metodo non supportato"]);
}
?>
Passo 4: Database MySQL
Crea un database chiamato api_db con una tabella users:

sql
Copia codice
CREATE DATABASE api_db;

USE api_db;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL
);
Passo 5: Testa l'API
Puoi testare l’API usando strumenti come:

Postman (grafico)
cURL (linea di comando)
Esempi di richieste
GET (Recupera utenti):
ruby
Copia codice
curl -X GET http://localhost/project/api/users.php
POST (Aggiungi un utente):
json
Copia codice
curl -X POST -H "Content-Type: application/json" -d '{"name": "Mario", "email": "mario@example.com"}' http://localhost/project/api/users.php
PUT (Aggiorna un utente):
json
Copia codice
curl -X PUT -H "Content-Type: application/json" -d '{"id": 1, "name": "Luigi", "email": "luigi@example.com"}' http://localhost/project/api/users.php
DELETE (Elimina un utente):
ruby
Copia codice
curl -X DELETE -H "Content-Type: application/json" -d '{"id": 1}' http://localhost/project/api/users.php
Cosa fare dopo
Autenticazione e sicurezza:
Implementa token JWT o un sistema API key per proteggere la tua API.
Modularità:
Suddividi il codice in più file e usa framework come Laravel o Slim per facilitare lo sviluppo di API.
Documentazione:
Usa strumenti come Swagger per documentare la tua API.