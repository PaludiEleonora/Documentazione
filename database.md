# Cos'è un Database?

Un database è una raccolta organizzata di dati, memorizzata e accessibile in modo che possano essere facilmente gestiti, modificati e recuperati. I database sono utilizzati per archiviare informazioni in modo strutturato e permettere a software e applicazioni di interagire con i dati.

---

# Transazioni

Una transazione è un insieme di operazioni che vengono eseguite come un'unità atomica, il che significa che o tutte le operazioni hanno successo o nessuna di esse viene eseguita. Le transazioni sono particolarmente utili per garantire la consistenza dei dati in caso di errori o interruzioni. Le transazioni supportano i seguenti principi, noti come ACID:

# Proprietà fondamentali per un database

- Atomicity (Atomicità)
Una transazione è considerata un'unità indivisibile di lavoro. O viene completata interamente, oppure, in caso di errore, non produce alcun effetto.
Esempio: Se trasferisci soldi tra due conti, entrambe le operazioni (diminuzione di un conto e aumento dell'altro) devono avvenire insieme o non avvenire affatto.

- Consistency (Coerenza)
Una transazione deve portare il database da uno stato valido a un altro stato valido, rispettando tutte le regole definite (come vincoli di integrità, trigger, ecc.).
Esempio: Se un account non può avere un saldo negativo, una transazione che lo porterebbe in uno stato incoerente non viene completata.

- Isolation (Isolamento)
Ogni transazione deve essere eseguita come se fosse l'unica attiva nel database, indipendentemente dalle altre transazioni in corso. Questo evita che i dati vengano modificati da altre transazioni nel mezzo del processo.
Esempio: Se due persone leggono o scrivono nello stesso record, il risultato finale deve essere lo stesso come se le transazioni fossero avvenute una dopo l'altra.

- Durability (Durabilità)
Una volta completata una transazione, i suoi effetti devono essere permanenti, anche in caso di crash del sistema o interruzioni.
Esempio: Dopo aver confermato un pagamento, i dati relativi al pagamento rimangono nel database anche se il server si spegne subito dopo.


# Tipi di Database

## Database Relazionale (RDBMS):

I database relazionali memorizzano i dati in tabelle, che sono composte da righe e colonne. Ogni tabella può essere correlata ad altre tabelle tramite chiavi primarie e chiavi esterne. <br/>

Esempi: MySQL, PostgreSQL, Oracle Database, SQL Server.

## Database NoSQL:

I database NoSQL (Not Only SQL) sono progettati per gestire dati non strutturati o semi-strutturati. Possono memorizzare dati in diversi formati, come documenti, key-value, grafi o colonne.
Esempi: MongoDB (documento), Redis (key-value), Cassandra (colonne), Neo4j (grafi).
Database In-Memory:

I database in-memory sono progettati per memorizzare i dati principalmente nella memoria RAM anziché su disco, per garantire velocità elevata nell'accesso e nelle operazioni sui dati.
Esempi: Redis, Memcached.
Concetti Fondamentali di Database Relazionali
Tabelle: Una tabella è una struttura fondamentale in un database relazionale. È composta da righe e colonne, dove ogni riga rappresenta un record e ogni colonna rappresenta un campo (attributo) del record. Esempio di tabella "Clienti":

id	nome	email
1	Mario	mario@email.com
2	Lucia	lucia@email.com

---

**Righe (Record)**: Ogni riga di una tabella rappresenta un record e contiene un set di valori per ciascuna colonna. Ad esempio, un singolo cliente nella tabella di sopra è un record.

**Colonne (Campi)**: Ogni colonna in una tabella rappresenta un attributo o una proprietà di un'entità. Ad esempio, la colonna "nome" contiene il nome del cliente, la colonna "email" contiene l'indirizzo email.

**Chiave primaria (Primary Key)**: La chiave primaria è un campo (o una combinazione di campi) che identifica in modo univoco ogni record in una tabella. Ad esempio, nella tabella "Clienti", id potrebbe essere la chiave primaria, perché ogni cliente ha un ID unico.

**Chiave esterna (Foreign Key):** Una chiave esterna è un campo in una tabella che crea una relazione con la chiave primaria di un'altra tabella. Questo permette di stabilire una relazione tra i dati di due tabelle. Ad esempio, se avessimo una tabella "Ordini" che fa riferimento alla tabella "Clienti", il campo "id_cliente" nella tabella "Ordini" sarebbe una chiave esterna che punta alla chiave primaria "id" della tabella "Clienti".

**Indici:** Gli indici sono strutture di dati che migliorano la velocità delle operazioni di ricerca su una tabella. Gli indici permettono di trovare rapidamente i dati, riducendo il tempo necessario per le operazioni di lettura (query).

Query SQL (Structured Query Language): Il SQL è il linguaggio utilizzato per interagire con i database relazionali. Le query SQL permettono di creare, leggere, aggiornare e cancellare dati (operazioni CRUD). Alcuni esempi di query:


SELECT * FROM Clienti WHERE nome = 'Mario';
INSERT: Inserisce nuovi dati in una tabella.

INSERT INTO Clienti (id, nome, email) VALUES (1, 'Mario', 'mario@email.com');
UPDATE: Modifica i dati esistenti in una tabella.

UPDATE Clienti SET email = 'mario.new@email.com' WHERE id = 1;
DELETE: Elimina dati da una tabella.

DELETE FROM Clienti WHERE id = 1;

---

Normalizzazione del Database
La normalizzazione è il processo di organizzazione dei dati in modo da ridurre la ridondanza e migliorare l'integrità dei dati. Ci sono diverse "forme normali", che sono regole per strutturare i dati in modo efficace. La normalizzazione porta alla creazione di tabelle separate per categorie di dati simili e alla definizione di chiavi esterne per collegarle.

---

# Tipi di Database NoSQL

Document-oriented: Memorizzano dati in documenti (tipicamente in formato JSON o BSON). Ogni documento è una collezione di coppie chiave-valore. MongoDB è un esempio di database document-oriented.

Key-Value: Memorizzano i dati come una coppia chiave-valore. Un esempio famoso è Redis.

Column-family: Memorizzano i dati in colonne anziché righe. Ogni "famiglia di colonne" è una struttura che contiene colonne relative a un'entità. Cassandra è un esempio di database column-family.

Graph: Memorizzano i dati come nodi, archi e proprietà, ideali per modellare relazioni complesse. Neo4j è un esempio di database grafico.

---

## Backup e Ripristino
I backup sono essenziali per proteggere i dati da guasti o errori. Un database può essere eseguito in modalità di backup per creare una copia dei suoi dati e recuperare i dati in caso di problemi. Esistono diverse tecniche di backup:

- Backup completo: Copia l'intero database.
- Backup incrementale: Copia solo i dati modificati dall'ultimo backup.
Ottimizzazione delle Prestazioni
L'ottimizzazione del database è cruciale per garantire che le operazioni sui dati siano rapide ed efficienti. Alcune tecniche di ottimizzazione includono:


> Conclusioni
> I database sono fondamentali per la gestione e l'archiviazione dei dati. I database relazionali sono molto  
> utilizzati per gestire dati strutturati, mentre i database NoSQL sono ottimizzati per gestire grandi quantità di 
> dati non strutturati. Indipendentemente dal tipo, comprendere la progettazione e l'ottimizzazione di un database è
> essenziale per sviluppare applicazioni scalabili ed efficienti.

---

# Comani Base

Creazione di un database

CREATE DATABASE nome_database;


Eliminazione di un database
Attenzione: elimina definitivamente il database.

DROP DATABASE nome_database;


Selezione di un database (nel caso di più database)
USE nome_database;


# Comandi per la gestione delle tabelle

I comandi seguenti servono per creare, modificare o eliminare le tabelle.

Creazione di una tabella

CREATE TABLE nome_tabella (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(50),
    eta INT,
    email VARCHAR(100)
);

Visualizzazione della struttura di una tabella

DESCRIBE nome_tabella;

Modifica di una tabella
Aggiungere una colonna:

ALTER TABLE nome_tabella ADD colonna_nuova VARCHAR(100);


Modificare una colonna:

ALTER TABLE nome_tabella MODIFY colonna_nuova INT;

Rinominare una colonna:

ALTER TABLE nome_tabella CHANGE colonna_vecchia colonna_nuova VARCHAR(50);

Eliminare una colonna:

ALTER TABLE nome_tabella DROP COLUMN colonna_da_rimuovere;


Eliminazione di una tabella
Attenzione: elimina definitivamente la tabella.

DROP TABLE nome_tabella;


# Comandi per l’inserimento, lettura, aggiornamento e cancellazione (CRUD)

Inserire dati in una tabella

INSERT INTO nome_tabella (colonna1, colonna2) VALUES ('valore1', 'valore2');

Leggere i dati da una tabella (SELECT)

SELECT * FROM nome_tabella;

Solo alcune colonne:

SELECT colonna1, colonna2 FROM nome_tabella;

Con una condizione:

SELECT * FROM nome_tabella WHERE eta > 18;

Con ordinamento:

SELECT * FROM nome_tabella ORDER BY nome ASC; -- ASC: crescente, DESC: decrescente

Con limite di righe:

SELECT * FROM nome_tabella LIMIT 5;

Aggiornare dati in una tabella

UPDATE nome_tabella
SET nome = 'Mario', eta = 30
WHERE id = 1;

Eliminare dati da una tabella

DELETE FROM nome_tabella WHERE id = 1;
Nota: Senza la clausola WHERE, elimina tutti i dati:

DELETE FROM nome_tabella;



# Comandi per le query avanzate

Filtri e condizioni
Clausola WHERE con operatori logici:

SELECT * FROM nome_tabella
WHERE eta > 18 AND nome = 'Mario';


## Operatori IN e BETWEEN:

SELECT * FROM nome_tabella WHERE eta BETWEEN 20 AND 30;
SELECT * FROM nome_tabella WHERE nome IN ('Mario', 'Luigi');

Filtrare valori NULL:

SELECT * FROM nome_tabella WHERE email IS NULL;
SELECT * FROM nome_tabella WHERE email IS NOT NULL;

## Raggruppare e aggregare dati

GROUP BY e HAVING:

SELECT eta, COUNT(*) AS numero_persone
FROM nome_tabella
GROUP BY eta
HAVING numero_persone > 2;

## Unire tabelle (JOIN)

INNER JOIN:

SELECT utenti.nome, ordini.totale
FROM utenti
INNER JOIN ordini ON utenti.id = ordini.utente_id;

LEFT JOIN:

SELECT utenti.nome, ordini.totale
FROM utenti
LEFT JOIN ordini ON utenti.id = ordini.utente_id;

# Cosa è una Vista in SQL?

Una vista (view) è una query salvata che restituisce un set di dati come se fosse una tabella. Tuttavia, una vista non memorizza i dati effettivi; si basa sui dati presenti nelle tabelle sottostanti.

## Caratteristiche principali delle viste:

- Astrattezza: Nasconde la complessità delle query. Una vista può combinare dati da più tabelle, raggrupparli o applicare filtri.

- Riutilizzabilità: Può essere usata come una tabella virtuale in altre query.

- Sicurezza: Puoi limitare l'accesso ai dati sensibili consentendo agli utenti di accedere solo alle viste, senza mostrare le tabelle sottostanti.

## Come creare una vista

CREATE VIEW nome_vista AS
SELECT nome, eta
FROM utenti
WHERE eta > 18;

Questa vista restituisce solo i nomi e le età degli utenti maggiorenni.

Come utilizzare una vista
Usare una vista è simile a usare una tabella:

SELECT * FROM nome_vista;

# Dove viene salvata una vista?

Una vista non memorizza fisicamente i dati come farebbe una tabella. Invece:

Viene salvata nel catalogo del database (il cosiddetto data dictionary), che memorizza la definizione della vista.
Ogni volta che esegui una query su una vista, il database esegue la query sottostante della vista per generare i dati in tempo reale.
In pratica, la vista è solo una "query predefinita" salvata nel database.
