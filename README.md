# Unity_Project

# Descrizione del Progetto

* Genere
Blackened è un videogioco stealth con visuale in prima persona. Il giocatore deve attraversare diversi livelli uno dopo l’altro senza far suonare l’allarme della struttura dove è ambientato questo gioco. Inoltre, il giocatore dovrà affrontare delle guardie che gli impediranno di avanzare, provando ad ucciderlo o facendo suonare l’allarme. Il giocatore è un hacker, quindi può hackerare diversi dispostivi tecnologici per superare gli ostacoli che si troverà davanti. Blackened ha anche una forte componente action-fps perché il player può portare con sé diverse armi che gli permettono di giocare con molti approcci diversi. 

* Storia e Ambientazione 
Ispirato dai fatti della serie tv MR ROBOT, BLACKENED* racconta la storia di un attivista che ha come obiettivo quello di portare alla luce tutti i crimini ambientali commessi dalla Ecorp, la multinazionale che detiene ormai il monopolio su qualsiasi bene prodotto. Per raggiunge tale obiettivo il protagonista dovrà: 

Rubare un primo pacchetto di dati sensibili contenuti nella server room. 

Rubare un secondo pacchetto di dati contenuto all’interno del computer del capo. 

Ovviamente nel portare a termine la sua missione il protagonista dovrà passare da un piano all’altro dell’edifico evitando di essere avvistato dalle guardie che saranno l’ostacolo primario del gioco. Di volta in volta sarà necessario anche forzare dei sistemi di sicurezza con il fine di raggiungere aree protette. Sta al giocatore decidere se giocare in modalità “Coscienza pulita” evitando inutili spargimenti di sangue oppure se uccidere le guardie, diventando così un assassino proprio come il capo della Ecorp. 

# Progettazione ed Implementazione 

* Player
Il player possiede diversi script, grazie al quale può compiere diverse azioni all’interno di ciascuna scena.
-Fps input: Permette al personaggio di compiere dei movimenti lungo l’asse x e l’asse y, di avere lungo l’asse y una forza applicata che rappresenta la gravità ed      inoltre permette di impostare e modificare la velocità del giocatore. Viene definita una nuova posizione in base ai tasti premuti.
-MouseLook :Tramite il mouse permette al giocatore di compiere degli spostamenti rotatori in orizzontale ed in verticale all’interno del mondo.	 

* Camera
La camera contiene gli script MouseLook e RayShooter. Il primo viene utilizzato per permettere al giocatore di guardarsi intorno dando l’impressione di “girare con la testa”, il secondo è utile per capire con quale oggetto il giocatore vuole interagire. Lo script RayShooter è fondamentale per l’implementazione dello script Laptop perché è utile a capire se il tipo di oggetto con qui si vuole interagire è una cam, un device o un enemy. Sulla base delle informazioni raccolte lo script Laptop poi decide quale interfaccia mostrare a schermo… 

* Raycast
Il RayCasy ci permette  di generare un raggio, a partire da un punto di origine  verso una direzione e con una lunghezza massima oltre il quale il raggio non può arrivare. Grazie a questo strumento possiamo rilevare tutte le intersezioni che ci sono tra il raggio ed un qualsiasi collider che sia all’interno della scena. Per quanto riguarda le armi il RayCast è stato fondamentale perché ci ha permesso di capire se effettivamente l’arma ha colpito un oggetto oppure un nemico.  
Physics.RayCast :Grazie a tale metodo possiamo capire se il raycast ha colpito qualcosa, in tal caso infatti restituirà true. Physics.Raycast(posizione iniziale, direzione, out hit, lunghezza)  
RaycastHit: ci permette di avere delle informazioni importanti sull’oggetto che è stato colpito dal raggio.  

* Managers
I vari Manager presenti all’interno del progetto, ci permettono di gestire diverse aree in modo facile ed efficiente. 
Abbiamo un Manager di livello superiore che gestisce tutti i manager, esso contiene il metodo Awake che è un metodo base che offre la classe MonoBehaviour , tale metodo viene eseguito ancor prima del metodo start e ci consente di inizializzare i manager di ogni area, tutti gli script possono accedere ad ogni Manager tramite la classe Managers.  
Ogni Manager che partecipa a tale struttura implementa l’interfaccia IGameManager.

* AudioManager e Suoni
L’audioManager ci consente di gestire i suoni all’interno del progetto.  
Contiene un array di suoni, questo ci permette di accedere e riprodurre tali suoni facilmente da qualsiasi script accedendo all’istanza di AudioManager.  
Uno dei metodi principale è Startup() che viene dichiarato nell’interfaccia  IGameManager, ci permette di inizializzare i suoni che sono presenti nell’array e di far partire  i suoni che sono caratterizzati dal campo playOnAwake.   
Uno strumento molto importante per la gestione dei suoni sono i mixers, la loro funzione principale è quello di controllare il flusso del segnale delle sorgenti audio che vengono riprodotti. Un aspetto importante che riguarda i mixers è che a partire da un determinato mixer audio possiamo  creare un gruppo di mixer	, questo ci consente di far gestire determinate tipologie di sorgenti audio a mixer diversi.  

* InventoryManager e Inventario
L’inventoryManager ci consente di gestire l’inventario del giocatore.  
Il funzionamento dell’ inventoryManager è molto semplice, al suo interno vi è un Dizionario che tiene traccia di tutti gli oggetti collezionabili che il giocatore ha ottenuto. 
Le funzioni principali che ci permettono di gestire l’inventario sono: 
StartUp(): ci permette di inizializzare l’inventario 
AddItem():ci permette di aggiungere un oggetto collezionabile all’interno dell’inventario. 
ConsumeItem():una volta utilizzato l’oggetto ci permette di ridurre la sua quantità all’interno dell’inventario. 

* GameController
È uno prefab su cui è attaccato uno script e serve per controllare le funzioni vitali del gioco. Le funzioni più importanti sono: 
StartGame(): per avviare il gioco dal Menu principale. 
QuitGame(): per uscire dal gioco dal Menu di pausa. Una volta premuto quit bisogna ricominciare il gioco da capo. 
GameOver(): per terminare una sessione di gioco nel caso in cui il player dovesse perdere. Una volta premuto space il gioco riparte dall’ultimo livello raggiunto. 
NextLevel(): per passare al prossimo livello e settare una nuova scena. 
ReachGaol1() e ReachGoal2(): per settare le variabili che tengono traccia degli obiettivi raggiunti. Una volta raggiungi i due obiettivi il gioco termina con la schermata di vittoria. 

 
