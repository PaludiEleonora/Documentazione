# Dati e protocolli
- La trasmissione di dati tra calcolatori avviene spesso tramite scambio di pacchetti di dati (“protocolli di trasmissione”).
- Al di sopra di questo livello, le applicazioni devono accordarsi su un linguaggio per interpretare i dati scambiati (“protocolli delle applicazioni”).
- per trasmettere un flusso apparentemente continuo di dati, come quando s trasmette della musica o un film, il flusso di dati viene spezzato in pacchetti, spedito, e all’arrivo i pacchetti vengono rimessi in ordine, posti in un buffer, che ricostruisce il flusso di dati.
- una caratteristica di questa tecnica digitale - rispetto alla trasmissione analogica `e che si ha un ritardo (time lag) prodotto dalla necessaria bufferizzazione dei pacchetti in arrivo.

# Dettagli dei pacchetti

I pacchetti sono formati da una parte contenente i <mark>dati veri e propri (”payload”) e da una parte che contiene le informazioni per trasportare i pacchetti a destinazione e verificarne l’integrità</mark> (”header” and ”trailers”)

# Internet 

Internet è essenzialmente una federazione di reti locali (LAN). Le LAN sono collegate tra loro da apparecchi dedicati, i router.
Per identificare una macchina in Internet viene usato un <mark>Indirizzo IP (Internet Protocol).</mark>
 Ci sono attualmente due standard, **IPv4 e IPv6**.
<mark>IPv4 usa indirizzi composti di 4 numeri tra 0 e 255, tipo 131.114.10.97
IPv6 usa indirizzi composti da 8 gruppi di 4 cifre esadecimali ciascuno, tipo 2001:760:2c0c:202::97 (cio`e 2001:0760:2c0c:0202:0000:0000:0000:0097)</mark>

# Protocollo 

Un protocollo è un insieme di regole e convenzioni che determinano come due o più dispositivi o sistemi comunicano tra loro. In informatica e telecomunicazioni, i protocolli stabiliscono il formato, l'ordine dei messaggi, e le azioni da intraprendere in caso di errore o ricezione di un messaggio.

---

## HTTP E HTTPS
Cos'è il protocollo HTTP?

<mark>HTTP (Hypertext Transfer Protocol) è il protocollo utilizzato per trasferire dati sul web. È il linguaggio standard attraverso cui i browser e i server web comunicano. </mark>
 
Caratteristiche principali di HTTP:
1.	Testuale: Le richieste e risposte sono leggibili e basate su testo.
2.	Stateless: Ogni richiesta HTTP è indipendente e non conserva informazioni di stato tra richieste consecutive.
3.	Richieste e Risposte: Si basa su uno schema di scambio in cui il client (ad esempio, il browser) invia una richiesta al server, e il server risponde con i dati richiesti.
 
# Cos'è HTTPS?

<mark>HTTPS (HTTP Secure) è la versione sicura di HTTP</mark>. Aggiunge uno strato di crittografia tramite il protocollo TLS (Transport Layer Security) o il suo predecessore SSL (Secure Sockets Layer).
 
## Differenze principali tra HTTP e HTTPS:
 **Caratteristica**     | **HTTP**                             | **HTTPS**                           |
|-------------------------|--------------------------------------|--------------------------------------|
| **Sicurezza**           | Non crittografato (testo in chiaro).| Crittografato (protetto da TLS).     |
| **Integrità dei dati**  | Dati vulnerabili ad attacchi.       | Dati protetti da manomissioni.       |
| **Certificati SSL**     | Non richiesti.                      | Richiede un certificato SSL/TLS.     |
| **Uso consigliato**     | Non per dati sensibili.             | Ideale per tutte le comunicazioni.   |
 
## Cosa cambia con HTTPS?
-	Sicurezza dei dati: Le informazioni (come credenziali di accesso, dati personali, carte di credito) sono protette.
-	SEO: Google e altri motori di ricerca privilegiano i siti HTTPS nei risultati di ricerca.
-	Fiducia degli utenti: I browser mostrano un'icona di lucchetto accanto agli URL HTTPS, migliorando la percezione della sicurezza.
 
--- 

# SSL
## Cos'è SSL?
SSL (Secure Sockets Layer) è un protocollo di sicurezza che consente di cifrare la comunicazione tra un client (come un browser) e un server (ad esempio, il server di un sito web). SSL è stato il precursore del moderno TLS (Transport Layer Security), che è più sicuro e attualmente il protocollo utilizzato.
In pratica, SSL/TLS permette di stabilire una connessione sicura su una rete insicura (come internet) per proteggere i dati scambiati da intercettazioni e manomissioni.
 
---

# SMTP
SMTP (Simple Mail Transfer Protocol) è un protocollo di comunicazione utilizzato per l'invio di email su Internet. SMTP definisce le regole e le procedure per trasferire i messaggi di posta elettronica tra i server di posta. È uno dei principali protocolli usati nel sistema di posta elettronica.
Come funziona SMTP?
Quando invii una email, il tuo client di posta (come Outlook, Gmail, Thunderbird, o un'applicazione web) utilizza SMTP per inviare il messaggio al server di posta in uscita (generalmente chiamato "server SMTP"). Da lì, il server invia il messaggio al server di posta del destinatario, che si occupa di distribuirlo alla casella di posta del destinatario.

---

#DNS
Il DNS (Domain Name System) è un sistema utilizzato per tradurre i nomi di dominio (come www.example.com) in indirizzi IP numerici (come 192.168.1.1) che i computer e i server utilizzano per comunicare tra loro su Internet.
Cos'è un dominio e perché serve il DNS?
Quando vuoi visitare un sito web, ad esempio, digiti un nome come www.google.com nel tuo browser. Tuttavia, i computer e i server non capiscono i nomi come "google.com", ma solo indirizzi numerici (indirizzi IP). Il DNS agisce come una "rubrica telefonica" di Internet, traducendo i nomi di dominio in indirizzi IP che i computer possono comprendere.
In sintesi:
Il DNS è un sistema fondamentale che rende Internet usabile, traducendo i nomi di dominio in indirizzi IP che i computer possono comprendere. Senza di esso, dovremmo fare affidamento sugli indirizzi IP per accedere ai siti web, il che sarebbe molto più complicato.

---

# TCP /UDP 
TCP (Transmission Control Protocol) e UDP (User Datagram Protocol) sono protocolli di comunicazione utilizzati per trasmettere dati in una rete, come ad esempio su Internet. Entrambi fanno parte della suite di protocolli TCP/IP (Transmission Control Protocol/Internet Protocol), che è la base per la maggior parte delle comunicazioni su Internet.
Vediamo nel dettaglio cosa sono e come funzionano:
1. TCP (Transmission Control Protocol)

Il TCP è un protocollo di trasmissione orientato alla connessione. Ciò significa che stabilisce una connessione tra il mittente e il destinatario prima di iniziare a trasferire i dati. Inoltre, si occupa di garantire che i dati vengano ricevuti correttamente, nel giusto ordine, e senza errori.

Il UDP è un protocollo di trasmissione senza connessione. A differenza di TCP, non stabilisce una connessione tra il mittente e il destinatario prima di inviare i dati e non garantisce la consegna dei pacchetti.

## Differenze principali tra TCP e UDP:

Caratteristica	TCP	UDP
Tipo di protocollo	Orientato alla connessione	Senza connessione
Affidabilità	Alta, garantisce la consegna dei dati	Bassa, non garantisce la consegna
Controllo errori	Sì, con meccanismi di ritrasmissione	No, i pacchetti possono essere persi
Controllo congestione	Sì, gestisce la congestione della rete	No, non gestisce la congestione
Velocità	Più lento, a causa dei controlli	Più veloce, senza controllo
Utilizzo tipico	Navigazione web, email, trasferimenti file	Streaming, giochi online, DNS
Quando usare TCP e quando usare UDP?
•	Usa TCP quando:
o	È fondamentale che i dati siano ricevuti correttamente (es. trasferimento di file, navigazione web, email).
o	Hai bisogno di un controllo accurato degli errori e del flusso di dati.
•	Usa UDP quando:
o	La velocità è importante e puoi tollerare una perdita di qualche dato (es. streaming video o audio, giochi online, VoIP).
o	Non è necessario un controllo rigoroso sull'ordine o sulla consegna dei pacchetti.
In sintesi, TCP è più affidabile e preciso, ma più lento, mentre UDP è più veloce ma meno sicuro, con la possibilità che alcuni pacchetti vengano persi lungo la strada.


