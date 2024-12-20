# Cos'è un Database?

Un database è una raccolta organizzata di dati, memorizzata e accessibile in modo che possano essere facilmente gestiti, modificati e recuperati. I database sono utilizzati per archiviare informazioni in modo strutturato e permettere a software e applicazioni di interagire con i dati.

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

Chiave primaria (Primary Key): La chiave primaria è un campo (o una combinazione di campi) che identifica in modo univoco ogni record in una tabella. Ad esempio, nella tabella "Clienti", id potrebbe essere la chiave primaria, perché ogni cliente ha un ID unico.

Chiave esterna (Foreign Key): Una chiave esterna è un campo in una tabella che crea una relazione con la chiave primaria di un'altra tabella. Questo permette di stabilire una relazione tra i dati di due tabelle. Ad esempio, se avessimo una tabella "Ordini" che fa riferimento alla tabella "Clienti", il campo "id_cliente" nella tabella "Ordini" sarebbe una chiave esterna che punta alla chiave primaria "id" della tabella "Clienti".

Indici: Gli indici sono strutture di dati che migliorano la velocità delle operazioni di ricerca su una tabella. Gli indici permettono di trovare rapidamente i dati, riducendo il tempo necessario per le operazioni di lettura (query).

Query SQL (Structured Query Language): Il SQL è il linguaggio utilizzato per interagire con i database relazionali. Le query SQL permettono di creare, leggere, aggiornare e cancellare dati (operazioni CRUD). Alcuni esempi di query:

SELECT: Recupera dati da una tabella.

sql
Copia codice
SELECT * FROM Clienti WHERE nome = 'Mario';
INSERT: Inserisce nuovi dati in una tabella.

sql
Copia codice
INSERT INTO Clienti (id, nome, email) VALUES (1, 'Mario', 'mario@email.com');
UPDATE: Modifica i dati esistenti in una tabella.

sql
Copia codice
UPDATE Clienti SET email = 'mario.new@email.com' WHERE id = 1;
DELETE: Elimina dati da una tabella.

sql
Copia codice
DELETE FROM Clienti WHERE id = 1;
Normalizzazione del Database
La normalizzazione è il processo di organizzazione dei dati in modo da ridurre la ridondanza e migliorare l'integrità dei dati. Ci sono diverse "forme normali", che sono regole per strutturare i dati in modo efficace. La normalizzazione porta alla creazione di tabelle separate per categorie di dati simili e alla definizione di chiavi esterne per collegarle.

Transazioni
Una transazione è un insieme di operazioni che vengono eseguite come un'unità atomica, il che significa che o tutte le operazioni hanno successo o nessuna di esse viene eseguita. Le transazioni sono particolarmente utili per garantire la consistenza dei dati in caso di errori o interruzioni. Le transazioni supportano i seguenti principi, noti come ACID:

Atomicità: Tutte le operazioni della transazione sono completate o nessuna lo è.
Coerenza: Il database passa da uno stato coerente a un altro stato coerente.
Isolamento: Le operazioni di una transazione non sono visibili ad altre transazioni fino a quando non sono completate.
Durabilità: I cambiamenti apportati dal completamento di una transazione sono permanenti.
Tipi di Database NoSQL
Document-oriented: Memorizzano dati in documenti (tipicamente in formato JSON o BSON). Ogni documento è una collezione di coppie chiave-valore. MongoDB è un esempio di database document-oriented.

Key-Value: Memorizzano i dati come una coppia chiave-valore. Un esempio famoso è Redis.

Column-family: Memorizzano i dati in colonne anziché righe. Ogni "famiglia di colonne" è una struttura che contiene colonne relative a un'entità. Cassandra è un esempio di database column-family.

Graph: Memorizzano i dati come nodi, archi e proprietà, ideali per modellare relazioni complesse. Neo4j è un esempio di database grafico.

Backup e Ripristino
I backup sono essenziali per proteggere i dati da guasti o errori. Un database può essere eseguito in modalità di backup per creare una copia dei suoi dati e recuperare i dati in caso di problemi. Esistono diverse tecniche di backup:

Backup completo: Copia l'intero database.
Backup incrementale: Copia solo i dati modificati dall'ultimo backup.
Ottimizzazione delle Prestazioni
L'ottimizzazione del database è cruciale per garantire che le operazioni sui dati siano rapide ed efficienti. Alcune tecniche di ottimizzazione includono:

Indicizzazione: Come già menzionato, gli indici possono velocizzare le query.
Sharding: Distribuire i dati su più server per migliorare la scalabilità.
Query optimization: Scrivere query SQL efficienti per ridurre i tempi di esecuzione.
Conclusioni
I database sono fondamentali per la gestione e l'archiviazione dei dati. I database relazionali sono molto utilizzati per gestire dati strutturati, mentre i database NoSQL sono ottimizzati per gestire grandi quantità di dati non strutturati. Indipendentemente dal tipo, comprendere la progettazione e l'ottimizzazione di un database è essenziale per sviluppare applicazioni scalabili ed efficienti.

Se hai domande specifiche o vuoi esplorare un argomento più approfondito, fammi sapere!