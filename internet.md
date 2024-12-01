# Dati e protocolli
- La trasmissione di dati tra calcolatori avviene spesso tramite scambio di pacchetti di dati (“protocolli di trasmissione”).
- Al di sopra di questo livello, le applicazioni devono accordarsi su un linguaggio per interpretare i dati scambiati (“protocolli delle applicazioni”).
- per trasmettere un flusso apparentemente continuo di dati, come quando s trasmette della musica o un film, il flusso di dati viene spezzato in pacchetti, spedito, e all’arrivo i pacchetti vengono rimessi in ordine, posti in un buffer, che ricostruisce il flusso di dati.
- una caratteristica di questa tecnica digitale - rispetto alla trasmissione analogica `e che si ha un ritardo (time lag) prodotto dalla necessaria bufferizzazione dei pacchetti in arrivo.

# Dettagli dei pacchetti

I pacchetti sono formati da una parte contenente i <mark>dati veri e propri (”payload”) e da una parte che contiene le informazioni per trasportare i pacchetti a destinazione e verificarne l’integrità</mark> (”header” and ”trailers”)

# Internet 

Internet `e essenzialmente una federazione di reti locali (LAN). Le LAN sono collegate tra loro da apparecchi dedicati, i router.
Per identificare una macchina in Internet viene usato un <mark>Indirizzo IP (Internet Protocol).</mark>
 Ci sono attualmente due standard, **IPv4 e IPv6**.
</mark> IPv4 usa indirizzi composti di 4 numeri tra 0 e 255, tipo 131.114.10.97
IPv6 usa indirizzi composti da 8 gruppi di 4 cifre esadecimali ciascuno, tipo 2001:760:2c0c:202::97 (cio`e 2001:0760:2c0c:0202:0000:0000:0000:0097)</mark>





