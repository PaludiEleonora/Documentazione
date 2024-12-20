# Docker

Docker è uno strumento molto potente che permette di creare, gestire e distribuire applicazioni in container. I container sono ambienti isolati che includono tutto il necessario per eseguire un'applicazione (librerie, dipendenze, file di configurazione, ecc.). Questo rende le applicazioni più facili da sviluppare, testare e distribuire.

---

# Cos'è un Container?

Un container è un'unità di esecuzione leggera e portatile che include tutto ciò che serve per eseguire un'applicazione, come il codice, le librerie, le dipendenze e il sistema operativo necessario per eseguire l'applicazione stessa. <br/>
I container sono isolati dal sistema operativo sottostante e tra di loro, ma condividono il kernel del sistema operativo (quindi sono molto più leggeri delle macchine virtuali).

## Caratteristiche principali dei container:

- Isolamento: Ogni container funziona in modo indipendente, senza influenzare gli altri, e ha il proprio file system, le sue risorse di rete, ecc.

- Leggerezza: I container sono molto più leggeri rispetto alle macchine virtuali, poiché non richiedono una copia completa del sistema operativo, ma solo le librerie e i file necessari per l'esecuzione dell'applicazione.

- Portabilità: I container sono indipendenti dal sistema operativo sottostante. Un'applicazione contenuta in un container può essere eseguita su qualsiasi sistema che supporta Docker (Linux, macOS, Windows) senza modifiche.

## Come funziona un container:

Docker crea un contenitore a partire da un'immagine. Un'immagine è come un template o una "foto" di un sistema.
Il contenitore viene eseguito a partire da un'immagine, ma è un'istanza in esecuzione che ha il suo file system, processi e risorse.
Quando un contenitore viene fermato, i cambiamenti fatti al suo interno non sono persi, a meno che non siano stati scritti in volumi (per dati persistenti).


# Cos'è un'Immagine Docker?

Un'immagine Docker è un pacchetto immutabile che contiene il codice dell'applicazione, tutte le librerie e le dipendenze necessarie per eseguire un'applicazione. È essenzialmente il "modello" da cui vengono creati i contenitori.

## Caratteristiche principali delle immagini:

- Immutabilità: Un'immagine non cambia mai. Ogni volta che un contenitore viene creato da un'immagine, l'immagine rimane invariata.

- Layering: Le immagini Docker sono composte da diversi layer. Ogni comando nel Dockerfile (di cui parleremo più avanti) crea un nuovo layer. I container creati da un'immagine condividono questi layer, il che li rende molto efficienti.

- Versatilità: Puoi scaricare immagini preconfigurate da Docker Hub (un repository pubblico di immagini) o creare le tue immagini personalizzate per qualsiasi tipo di applicazione.

## Come si crea un'immagine?

Un'immagine viene creata tramite un Dockerfile, che è un file di testo che contiene una serie di istruzioni su come configurare l'immagine (ad esempio, quale sistema operativo usare, quali pacchetti installare, quale applicazione copiare, ecc.).


# Relazione tra Immagini e Container
La relazione tra immagini e container può essere descritta come segue:

**Le immagini sono come i "modelli" o "template". Sono statiche e immutabili.** <br/>

**I container sono istanze in esecuzione di queste immagini.**<br/>

 <mark>Quando esegui un'immagine, Docker crea un container che è una copia attiva dell'immagine, ma può fare modifiche e scrivere file (se non stai usando volumi per la persistenza). </mark>

# Volume Docker

<mark>Quando crei un container, le modifiche apportate al file system all'interno del container non sono permanenti per impostazione predefinita. Se il contenitore viene rimosso, anche i dati all'interno verranno persi. Tuttavia, puoi usare volumi Docker per mantenere i dati persistenti, anche se il contenitore viene rimosso.</mark>

Ad esempio, se hai un database MySQL in un container, potresti voler conservare i dati del database in un volume, in modo che anche se il contenitore MySQL viene distrutto, i dati non vengano persi.

---

# Come Creare un Progetto con Docker
Per creare un progetto con Docker, segui questi passaggi:

##  Definisci l'ambiente e le dipendenze
Un progetto Docker è tipicamente definito da un file Dockerfile (per costruire immagini) e un file **docker-compose.yml** (per gestire più contenitori).

2. Crea un Dockerfile
Un Dockerfile è un file di testo che contiene le istruzioni per costruire un'immagine Docker personalizzata. Ecco un esempio di Dockerfile per un'applicazione PHP con Apache:

dockerfile
Copia codice
# Usa un'immagine di base con PHP e Apache
FROM php:7.4-apache

# Copia i file PHP nella cartella /var/www/html del contenitore
COPY ./src /var/www/html

# Installa eventuali estensioni PHP
RUN docker-php-ext-install mysqli
Qui stiamo creando un'immagine che:

Usa l'immagine di base php:7.4-apache.
Copia i file dalla cartella src nel tuo progetto nella directory di Apache dentro il contenitore.
Installa l'estensione mysqli di PHP per la connessione al database.
3. Crea un docker-compose.yml
Puoi usare docker-compose.yml per gestire più contenitori e definire come devono essere configurati. Un esempio di file docker-compose.yml per un'applicazione PHP con MySQL potrebbe essere:

yaml
Copia codice
version: '3.7'

services:
  web:
    build: .
    ports:
      - "8080:80"
    volumes:
      - ./src:/var/www/html
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: my_database
In questo esempio:

Il servizio web costruisce l'immagine da un Dockerfile nella stessa cartella e mappa la porta 8080 del computer host alla porta 80 del contenitore.
Il servizio db esegue MySQL con una password di root e crea un database chiamato my_database.
4. Crea la struttura del progetto
La struttura del progetto potrebbe essere la seguente:

bash
Copia codice
/my-project
  ├── Dockerfile
  ├── docker-compose.yml
  └── src/
      └── index.php
Puoi mettere il tuo codice PHP nella cartella src.

5. Costruisci e Avvia il Progetto
Ora puoi costruire e avviare il progetto. Vai nella directory del progetto e esegui:

bash
Copia codice
docker-compose up --build
Questo comando costruisce le immagini (se necessario) e avvia i contenitori definiti nel file docker-compose.yml.

6. Accedi all'applicazione
Se hai configurato il docker-compose.yml per mappare le porte correttamente, puoi accedere al tuo sito su http://localhost:8080.

7. Fermare il Progetto
Per fermare i contenitori, puoi eseguire:

bash
Copia codice
docker-compose down
Considerazioni Aggiuntive
Persistenza dei dati: I dati nel contenitore non sono persistenti per default. Se vuoi che i dati del database siano persistenti, puoi usare i volumi Docker. Ad esempio, nel file docker-compose.yml:

yaml
Copia codice
volumes:
  db_data:
    driver: local
Networking: Docker crea automaticamente una rete per i contenitori, ma puoi definire reti personalizzate nel docker-compose.yml.

Docker Hub: Puoi scaricare immagini preconfigurate da Docker Hub, che è un registry pubblico di immagini Docker (per esempio, immagini per MySQL, Nginx, etc.).

Risorse Utili
Documentazione Docker: https://docs.docker.com/
Documentazione Docker Compose: https://docs.docker.com/compose/
Se hai altre domande o vuoi vedere più esempi, fammi sapere!