# Cosa è Git?
Git è un sistema di controllo di versione distribuito che ti permette di:
•	Tenere traccia delle modifiche al codice nel tempo.
•	Tornare a versioni precedenti se necessario.
•	Collaborare con altre persone senza conflitti.

# Concetti di base
•	Repository: Un progetto Git, una cartella dove tieni il codice e Git tiene traccia delle modifiche.
•	Commit: Una snapshot del tuo codice in un momento specifico.
•	Branch: Una "linea temporale" separata per sviluppare funzionalità senza interferire con la versione principale.
•   Fetch: Carica gli aggiornamenti dal repository remoto, come nuovi commit, branch o tag, e li salva nella tua copia locale, ma non li integra automaticamente nel tuo codice attuale.
•	Scarica i dati (commit, file, ecc.) dal repository remoto senza applicarli direttamente al tuo ramo locale.
•  Merge:
•	Integra i dati scaricati nel tuo ramo attuale, unendoli alle modifiche locali. Se ci sono conflitti, sarà necessario risolverli manualmente.

 
# Verifica l'installazione:
git --version
 
## Configurazione iniziale
Configura il tuo nome e email (questi appariranno nei tuoi commit):
git config --global user.name "Il Tuo Nome"
git config --global user.email "tuo@email.com"
git config –list  verificare info
 

# CREAZIONE DI UN NUOVO PROGETTO GESTITO DA GIT 

## Git init 

Git Init Quando usarlo?
•	Stai creando un nuovo progetto e vuoi gestirlo con Git.
•	Vuoi iniziare a tracciare un progetto esistente che non è ancora un repository Git.


# Comandi 

**Touch doc.txt** ==> Creare Documento vuoto 

**Git status** ==>  per vedere lo stato del repository e per vedere se è stato tutto pushato

**Git add** ==> aggiungere nuovo file specifico 

**Git add .** ==> aggiungere tutto

## Muoversi dentro i percorsi
**CD** ==> cambiare cartelle
**CD..** ==> tornare indietro nel percorso
**LS** ==> vedere cosa c’è nel percorso
**Mkidir** ==> creare una cartella (directory) vuota
**rmdir** ==> cancellare la cartella vuota

## Pullata tipica 
**Git PULL** ==> ottenere gli aggiornamenti degli altri 
**Git reset**  ==> annullare tipo un add 
**Git commit -m** ==> per inserire il commento 
**Git push** ==> per pushare all’interno di github

## Merge 
Se ci troviamo sul main

**git switch sviluppo** ==> per switchare da main a sviluppo

Fare add, commit, push

Andare su produzione

**git merge sviluppo**

**git merge sviluppo --squash** ==> Per i commit  

**:q** ==> quando appare il messaggio

**git push** ==> pusha tutto il merge 

--- 

Se non si vogliono recuperare dei file che non hai o che hai cancellato :
**Git restore .**  ==> recupera tutto 
**Git restore “file”** ==> recupera il file 
**Git log** ==> per vedere i log


# BRANCH
Un branch (in italiano, "ramo") in Git è una versione parallela del tuo progetto, che permette di lavorare su diverse funzionalità, correzioni o esperimenti senza influire direttamente sul ramo principale (di solito chiamato main o master). Ogni branch è come una copia isolata del progetto, dove puoi fare modifiche in modo indipendente.

Comandi per il branch:

**Git branch** ==> Per vedere quali branch ci sono.

**Git branch sviluppo(es.)** ==> Per creare un nuovo branch di sviluppo

**Git checkout sviluppo(es)** ==>  Per spostarci sul nuovo branch
**Git switch sviluppo (es)** ==>Per spostarci sul nuovo branch
**checkout -b sviluppo(es)** ==> Per creare e spostarti direttamente sul branch di sviluppo

MERGE
Passaggi di un merge standard
1.	Posizionati nel ramo in cui vuoi fare il merge: Se vuoi unire sviluppo in main, devi trovarti nel ramo main:
git merge sviluppo  Per mergiare sviluppo con main 
Gestisci eventuali conflitti (se ci sono): Se non ci sono conflitti, Git completerà automaticamente il merge e creerà un commit. Se ci sono conflitti, Git mostrerà messaggi simili a:
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result.
2.	Risolvi i conflitti:
o	Apri i file contrassegnati come in conflitto.
o	Cerca i marcatori di conflitto (<<<<<<<, =======, >>>>>>>) e risolvi manualmente.
3.	Completa il merge: Dopo aver risolto i conflitti, aggiungi i file risolti e crea il commit:
git add file.txt
git commit
 
Tipi di merge
1.	Fast-forward merge
o	Si verifica quando il ramo di destinazione (es. main) non ha nuovi commit rispetto al ramo che vuoi unire.
o	Git "avanza" semplicemente il puntatore del ramo di destinazione.
git merge sviluppo
Git non crea un commit di merge separato; il risultato sembra che i commit del ramo unito siano stati fatti direttamente nel ramo principale.
2.	Merge standard (3-way merge)
o	Si verifica quando entrambi i rami hanno nuovi commit.
o	Git combina i due rami e crea un nuovo commit di merge.
3.	Squash merge
o	Combina tutti i commit di un ramo in un unico commit prima di unirlo al ramo principale.
o	Non tiene traccia della cronologia completa del ramo unito.
git merge --squash sviluppo
git commit -m "Unito ramo sviluppo"
4.	Merge senza commit automatico
o	A volte, potresti voler controllare il commit del merge manualmente.
git merge --no-commit sviluppo
git merge –abort  annullare un merge
 
Gestire conflitti durante un merge
1.	Identifica i file in conflitto Dopo un merge interrotto, esegui:
git status
2.	Risolvi i conflitti manualmente
o	Apri i file indicati.
o	Cerca i marcatori di conflitto, ad esempio:
>>>>>>> sviluppo
o	Scegli quale versione mantenere, oppure combina le modifiche, eliminando i marcatori.
3.	Aggiungi i file risolti Una volta risolti i conflitti:
git add file.txt
4.	Completa il merge Dopo aver aggiunto tutti i file risolti:
git commit
 
Annullare un merge
Se hai iniziato un merge ma vuoi annullarlo, puoi farlo con:
git merge --abort
Questo comando riporta il repository allo stato precedente all'inizio del merge.
 
Strumenti avanzati per il merge
1. Usare un mergetool
Puoi utilizzare un tool grafico per aiutarti a risolvere i conflitti:
bash
Copia codice
git mergetool
Git aprirà uno strumento configurato per la risoluzione dei conflitti (ad esempio, Meld, KDiff3, o Beyond Compare).
2. Controllare un merge prima di eseguirlo
Per vedere cosa cambierà prima di unire un ramo:
bash
Copia codice
git diff <nome-ramo>
git diff --name-only --diff-filter=U
Mostra i file che hanno ancora conflitti irrisolti.
•	Unire ignorando i conflitti in un file specifico: Se vuoi mantenere una versione specifica di un file durante il merge:
git checkout --ours nomefile
git checkout --theirs nomefile
o	--ours: Mantiene la versione del ramo attuale.
o	--theirs: Mantiene la versione del ramo unito.






