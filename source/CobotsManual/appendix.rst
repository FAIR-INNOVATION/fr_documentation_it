Appendice
==============

.. toctree:: 
  :maxdepth: 5

Appendice 1: Codici di errore del controllore di movimento e relative procedure
----------------------------------------------------------------------------------------

.. csv-table:: 
   :header: "Codice errore principale", "Codice errore secondario", "Descrizione"
   :widths: 20, 10, 70

   "0 - Nessun errore", "0", "Nessun errore"
   "1 - Errore punto comandato", "1", "Errore punto comandato giunto, ripristinabile"
   "1 - Errore punto comandato", "2", "Errore punto obiettivo movimento lineare (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "3", "Errore punto intermedio arco (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "4", "Errore punto obiettivo arco (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "5", "Distanza tra punti comandati arco troppo piccola, ripristinabile"
   "1 - Errore punto comandato", "6", "Errore primo punto intermedio cerchio completo/elica (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "7", "Errore secondo punto intermedio cerchio completo/elica (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "8", "Errore terzo punto intermedio cerchio completo/elica (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "9", "Distanza tra punti comandati cerchio completo/elica troppo piccola, ripristinabile"
   "1 - Errore punto comandato", "10", "Errore punto comandato TPD, ripristinabile"
   "1 - Errore punto comandato", "11", "Utensile TPD non corrispondente all'utensile attuale, ripristinabile"
   "1 - Errore punto comandato", "12", "Scostamento eccessivo tra punto iniziale comando attuale e successivo, ripristinabile"
   "1 - Errore punto comandato", "13", "Errore cambio utensile interno/esterno, ripristinabile"
   "1 - Errore punto comandato", "14", "Errore punto iniziale nuova elica, ripristinabile"
   "1 - Errore punto comandato", "15", "Errore punto comandato nuova curva spline, ripristinabile"
   "1 - Errore punto comandato", "17", "Comando PTP giunto oltre limite, ripristinabile"
   "1 - Errore punto comandato", "18", "Comando TPD giunto oltre limite, ripristinabile"
   "1 - Errore punto comandato", "19", "Comando giunto LIN/ARC oltre limite, ripristinabile"
   "1 - Errore punto comandato", "20", "Velocità comandata nello spazio cartesiano superata, non ripristinabile"
   "1 - Errore punto comandato", "21", "Coppia comandata nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "22", "Comando JOG giunto oltre limite, ripristinabile"
   "1 - Errore punto comandato", "23", "Velocità comandata asse 1 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "24", "Velocità comandata asse 2 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "25", "Velocità comandata asse 3 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "26", "Velocità comandata asse 4 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "27", "Velocità comandata asse 5 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "28", "Velocità comandata asse 6 nello spazio dei giunti oltre limite, ripristinabile"
   "1 - Errore punto comandato", "29", "Velocità di retroazione giunto oltre limite, non ripristinabile"
   "1 - Errore punto comandato", "30", "Scostamento eccessivo tra comando e retroazione giunto, non ripristinabile – richiede riavvio"
   "1 - Errore punto comandato", "31", "Errore punto obiettivo DMP (inclusa incongruenza utensile), ripristinabile"
   "1 - Errore punto comandato", "33", "Configurazione giunti cambia nel prossimo comando (prossimo comando in posizione singolare; usare comando PTP o modificare il punto), ripristinabile"
   "1 - Errore punto comandato", "34", "Configurazione giunti cambia nel comando attuale (prossimo comando in posizione singolare; usare comando PTP o modificare il punto), ripristinabile"
   "1 - Errore punto comandato", "35", "Velocità giunti superata in comando LIN, ripristinabile"
   "1 - Errore punto comandato", "36", "Velocità adattiva LIN supera soglia, ripristinabile"
   "1 - Errore punto comandato", "37", "Traiettoria contiene punti irraggiungibili, ripristinabile"
   "1 - Errore punto comandato", "38", "Traiettoria contiene punti irraggiungibili – posizione singolare, ripristinabile"
   "1 - Errore punto comandato", "49", "Errore comando: tra ARCSTART e ARCEND sono ammessi solo comandi LIN e ARC, ripristinabile"
   "1 - Errore punto comandato", "50", "Errore comando: tra WEAVESTART e WEAVEEND sono ammessi solo comandi LIN e ARC, ripristinabile"
   "1 - Errore punto comandato", "51", "Parametri oscillazione saldatura errati, ripristinabile"
   "1 - Errore punto comandato", "52", "Distanza tra punti comandati oscillazione troppo piccola, ripristinabile"
   "1 - Errore punto comandato", "53", "Traiettoria oscillazione contiene punti irraggiungibili – posizione singolare, ripristinabile"
   "1 - Errore punto comandato", "54", "Traiettoria oscillazione contiene punti irraggiungibili – comando giunto oltre limite, ripristinabile"
   "1 - Errore punto comandato", "55", "Traiettoria oscillazione contiene punti irraggiungibili – anomalia pianificazione (asse Z utensile allineato con direzione avanzamento X), ripristinabile"
   "1 - Errore punto comandato", "56", "Traiettoria oscillazione contiene punti irraggiungibili – anomalia pianificazione (errore waypoint arco), ripristinabile"
   "1 - Errore punto comandato", "65", "Scostamento eccessivo sensore laser, ripristinabile"
   "1 - Errore punto comandato", "66", "Interruzione comando sensore laser – tracciamento cordone terminato anticipatamente, ripristinabile"
   "1 - Errore punto comandato", "81", "Velocità comandata asse esterno oltre limite, ripristinabile"
   "1 - Errore punto comandato", "82", "Scostamento eccessivo tra comando e retroazione asse esterno, non ripristinabile – richiede homing o riavvio"
   "1 - Errore punto comandato", "83", "Anomalia comunicazione periferica estesa (asse esterno/IO), ripristinabile"
   "1 - Errore punto comandato", "84", "Perdita pacchetti comunicazione periferica estesa (asse esterno/IO), ripristinabile"
   "1 - Errore punto comandato", "97", "Tracciamento nastro trasportatore – variazione eccessiva orientamento tra punto iniziale e punto di riferimento, ripristinabile"
   "1 - Errore punto comandato", "113", "Controllo forza costante – superata distanza massima regolazione asse X, ripristinabile"
   "1 - Errore punto comandato", "114", "Controllo forza costante – superata distanza massima regolazione asse Y, ripristinabile"
   "1 - Errore punto comandato", "115", "Controllo forza costante – superata distanza massima regolazione asse Z, ripristinabile"
   "1 - Errore punto comandato", "116", "Controllo forza costante – superato angolo massimo regolazione RX, ripristinabile"
   "1 - Errore punto comandato", "117", "Controllo forza costante – superato angolo massimo regolazione RY, ripristinabile"
   "1 - Errore punto comandato", "118", "Controllo forza costante – superato angolo massimo regolazione RZ, ripristinabile"
   "1 - Errore punto comandato", "119", "Dati sensore esterno errati, ripristinabile"
   "1 - Errore punto comandato", "120", "Movimento esplorativo elicoidale fallito, ripristinabile"
   "1 - Errore punto comandato", "121", "Movimento inserimento rotativo fallito, ripristinabile"
   "1 - Errore punto comandato", "122", "Movimento inserimento lineare fallito, ripristinabile"
   "1 - Errore punto comandato", "123", "Movimento localizzazione superficie fallito, ripristinabile"
   "1 - Errore punto comandato", "129", "Numero massimo punti registrazione coppia superato, ripristinabile"
   "1 - Errore punto comandato", "130", "Errore cambio velocità, ripristinabile"
   "1 - Errore punto comandato", "147", "Errore inseguimento fuoco, ripristinabile"
   "1 - Errore punto comandato", "148", "Velocità orientamento oltre limite, ripristinabile"
   "1 - Errore punto comandato", "149", "Anomalia parola di stato giunto, ripristinabile"
   "2 - Guasto azionamento", "1", "Guasto azionamento asse 1, non ripristinabile"
   "2 - Guasto azionamento", "2", "Guasto azionamento asse 2, non ripristinabile"
   "2 - Guasto azionamento", "3", "Guasto azionamento asse 3, non ripristinabile"
   "2 - Guasto azionamento", "4", "Guasto azionamento asse 4, non ripristinabile"
   "2 - Guasto azionamento", "5", "Guasto azionamento asse 5, non ripristinabile"
   "2 - Guasto azionamento", "6", "Guasto azionamento asse 6, non ripristinabile"
   "3 - Guasto fuori limiti software", "1", "Asse 1 fuori limiti software, ripristinabile"
   "3 - Guasto fuori limiti software", "2", "Asse 2 fuori limiti software, ripristinabile"
   "3 - Guasto fuori limiti software", "3", "Asse 3 fuori limiti software, ripristinabile"
   "3 - Guasto fuori limiti software", "4", "Asse 4 fuori limiti software, ripristinabile"
   "3 - Guasto fuori limiti software", "5", "Asse 5 fuori limiti software, ripristinabile"
   "3 - Guasto fuori limiti software", "6", "Asse 6 fuori limiti software, ripristinabile"
   "4 - Guasto urto", "1", "Urto asse 1, ripristinabile"
   "4 - Guasto urto", "2", "Urto asse 2, ripristinabile"
   "4 - Guasto urto", "3", "Urto asse 3, ripristinabile"
   "4 - Guasto urto", "4", "Urto asse 4, ripristinabile"
   "4 - Guasto urto", "5", "Urto asse 5, ripristinabile"
   "4 - Guasto urto", "6", "Urto asse 6, ripristinabile"
   "4 - Guasto urto", "7", "Urto attrezzo terminale, ripristinabile"
   "5 - Errore numero slave attivi", "1", "Errore numero slave attivi, non ripristinabile"
   "6 - Errore slave", "1", "Slave disconnesso, non ripristinabile"
   "6 - Errore slave", "2", "Stato slave non conforme impostazione, non ripristinabile"
   "6 - Errore slave", "3", "Slave non configurato, non ripristinabile"
   "6 - Errore slave", "4", "Configurazione slave errata, non ripristinabile"
   "6 - Errore slave", "5", "Errore inizializzazione slave, non ripristinabile"
   "6 - Errore slave", "6", "Errore inizializzazione comunicazione mailbox slave, non ripristinabile"
   "7 - Errore I/O", "1", "Errore canale, ripristinabile"
   "7 - Errore I/O", "2", "Errore valore, ripristinabile"
   "7 - Errore I/O", "3", "Timeout attesa WaitDI, ripristinabile"
   "7 - Errore I/O", "4", "Timeout attesa WaitAI, ripristinabile"
   "7 - Errore I/O", "5", "Timeout attesa WaitAxleDI, ripristinabile"
   "7 - Errore I/O", "6", "Timeout attesa WaitAxleAI, ripristinabile"
   "7 - Errore I/O", "7", "Errore funzione già configurata su canale, ripristinabile"
   "7 - Errore I/O", "8", "Timeout accensione arco, ripristinabile"
   "7 - Errore I/O", "9", "Timeout spegnimento arco, ripristinabile"
   "7 - Errore I/O", "10", "Timeout ricerca posizione, ripristinabile"
   "7 - Errore I/O", "11", "Timeout rilevamento I/O nastro trasportatore, ripristinabile"
   "7 - Errore I/O", "12", "Timeout attesa WaitAuxDI, ripristinabile"
   "7 - Errore I/O", "13", "Timeout attesa WaitAuxAI, ripristinabile"
   "7 - Errore I/O", "14", "Timeout ricerca filo, ripristinabile"
   "8 - Errore pinza", "1", "Timeout movimento pinza, ripristinabile"
   "9 - Errore file", "1", "Versione file configurazione zbt errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "2", "Caricamento file configurazione zbt fallito – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "3", "Versione file configurazione user errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "4", "Caricamento file configurazione user fallito – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "5", "Versione file configurazione exaxis errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "6", "Caricamento file configurazione exaxis fallito – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "7", "Modello robot non corrispondente – richiede nuova impostazione, non ripristinabile"
   "9 - Errore file", "8", "Versione file configurazione dhpara errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "9", "Caricamento file configurazione dhpara fallito – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "10", "Modello robot non impostato – non ripristinabile"
   "9 - Errore file", "11", "Versione file configurazione load errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "12", "Caricamento file configurazione load fallito – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "13", "Versione file configurazione speed errata – errore inizializzazione, non ripristinabile"
   "9 - Errore file", "14", "Caricamento file configurazione speed fallito – errore inizializzazione, non ripristinabile"
   "10 - Posizione singolare", "1", "Posizione singolare"
   "11 - Errore comunicazione azionamento", "1", "Errore comunicazione azionamento asse 1, non ripristinabile"
   "11 - Errore comunicazione azionamento", "2", "Errore comunicazione azionamento asse 2, non ripristinabile"
   "11 - Errore comunicazione azionamento", "3", "Errore comunicazione azionamento asse 3, non ripristinabile"
   "11 - Errore comunicazione azionamento", "4", "Errore comunicazione azionamento asse 4, non ripristinabile"
   "11 - Errore comunicazione azionamento", "5", "Errore comunicazione azionamento asse 5, non ripristinabile"
   "11 - Errore comunicazione azionamento", "6", "Errore comunicazione azionamento asse 6, non ripristinabile"
   "12 - Limiti software assi esterni", "1", "Asse 1 fuori limiti software, ripristinabile"
   "12 - Limiti software assi esterni", "2", "Asse 2 fuori limiti software, ripristinabile"
   "12 - Limiti software assi esterni", "3", "Asse 3 fuori limiti software, ripristinabile"
   "12 - Limiti software assi esterni", "4", "Asse 4 fuori limiti software, ripristinabile"
   "13 - Errore parametro impostato", "1", "Numero utensile oltre limite, ripristinabile"
   "13 - Errore parametro impostato", "2", "Soglia completamento posizionamento errata, ripristinabile"
   "13 - Errore parametro impostato", "3", "Livello urto errato, ripristinabile"
   "13 - Errore parametro impostato", "4", "Peso carico errato, ripristinabile"
   "13 - Errore parametro impostato", "5", "Baricentro carico X errato, ripristinabile"
   "13 - Errore parametro impostato", "6", "Baricentro carico Y errato, ripristinabile"
   "13 - Errore parametro impostato", "7", "Baricentro carico Z errato, ripristinabile"
   "13 - Errore parametro impostato", "8", "Tempo filtro DI errato, ripristinabile"
   "13 - Errore parametro impostato", "9", "Tempo filtro AxleDI errato, ripristinabile"
   "13 - Errore parametro impostato", "10", "Tempo filtro AI errato, ripristinabile"
   "13 - Errore parametro impostato", "11", "Tempo filtro AxleAI errato, ripristinabile"
   "13 - Errore parametro impostato", "12", "Intervallo livelli logici DI errato, ripristinabile"
   "13 - Errore parametro impostato", "13", "Intervallo livelli logici DO errato, ripristinabile"
   "13 - Errore parametro impostato", "14", "Numero pezzo oltre limite, ripristinabile"
   "13 - Errore parametro impostato", "15", "Numero asse esterno oltre limite, ripristinabile"
   "13 - Errore parametro impostato", "16", "Canale encoder nastro trasportatore errato, ripristinabile"
   "13 - Errore parametro impostato", "17", "Numero asse pezzo nastro trasportatore errato, ripristinabile"

Appendice 2: Tabella codici guasto azionamenti servo
-----------------------------------------------------------

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center

   * - **Codice guasto**
     - **Nome guasto**
     - **Procedura**

   * - 1
     - Guasto sovracorrente software
     - | 1. Verificare se carico o resistenza del giunto sono aumentati o anomali
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 2
     - Guasto sovratensione
     - Ridurre velocità o accelerazione del robot

   * - 3
     - Guasto sottotensione
     - | 1. Verificare se l’uscita tensione 48V dell’armadio di controllo è anomala
       | 2. Controllare cortocircuiti tra scheda di azionamento e custodia del giunto
       | 3. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 4
     - Guasto surriscaldamento
     - Ridurre carico o velocità del robot

   * - 5
     - Guasto sovraccarico
     - Ridurre carico o velocità del robot

   * - 6
     - Guasto sovravelocità
     - | 1. Controllare se le viti di fissaggio del gruppo encoder magnetico e dell’albero motore sono allentate
       | 2. Eseguire nuovamente la taratura zero dell’encoder
       | 3. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 7
     - Guasto parametro anomalo
     - Riparare o sostituire la scheda di azionamento

   * - 8
     - Guasto “runaway” (perdita controllo velocità)
     - | 1. Controllare se le viti di fissaggio del gruppo encoder magnetico e dell’albero motore sono allentate
       | 2. Eseguire nuovamente la taratura zero dell’encoder
       | 3. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 9
     - Guasto errore di posizione
     - | 1. Verificare se carico o resistenza del giunto sono aumentati o anomali
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 10
     - Guasto overflow posizione
     - | 1. Controllare se i finecorsa meccanici sono allentati
       | 2. Eseguire nuovamente la taratura zero del robot

   * - 11
     - Guasto sovracorrente hardware
     - Riparare o sostituire la scheda di azionamento

   * - 12
     - Guasto abilitazione azionamento disabilitata
     - Non utilizzato

   * - 13
     - Guasto blocco motore
     - | 1. Verificare se l’elettromagnete del freno è eccitato
       | 2. Controllare se si è urtato un finecorsa meccanico
       | 3. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 14
     - Guasto alimentazione potenza
     - Non utilizzato

   * - 15
     - Guasto STO
     - Non utilizzato

   * - 16
     - Guasto taratura zero AD corrente di fase
     - Riparare o sostituire la scheda di azionamento

   * - 17
     - Guasto EEPROM
     - Riparare o sostituire la scheda di azionamento

   * - 18
     - Guasto Hall
     - | 1. Verificare connessione cablaggio Hall, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire il giunto

   * - 19
     - Guasto encoder
     - Riparare o sostituire il gruppo encoder magnetico

   * - 20
     - Guasto taratura zero encoder
     - | 1. Eseguire nuovamente la taratura zero dell’encoder
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 21
     - Guasto segnale Z encoder assente
     - Non utilizzato

   * - 22
     - Guasto conteggio encoder
     - Non utilizzato

   * - 23
     - Guasto overflow dati giri multipli encoder
     - Non utilizzato

   * - 24
     - Guasto clock esterno
     - Riparare o sostituire la scheda di azionamento

   * - 25
     - Guasto sequenza fasi UVW
     - Non utilizzato

   * - 26
     - Guasto FPGA
     - Non utilizzato

   * - 27
     - Guasto homing
     - Non utilizzato

   * - 28
     - Guasto encoder magnetico
     - | 1. Controllare se le viti di fissaggio del gruppo encoder magnetico e dell’albero motore sono allentate
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 29
     - Guasto interruzione cavo motore
     - | 1. Verificare connessione cavo motore, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 30
     - Guasto EtherCAT
     - | 1. Verificare connessione cavo di rete, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 31
     - Guasto EtherCAT_SM_DOG
     - | 1. Verificare connessione cavo di rete, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 32
     - Guasto EtherCAT_FATALSYNC
     - | 1. Verificare connessione cavo di rete, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 33
     - Guasto EtherCAT_SYNC
     - | 1. Verificare connessione cavo di rete, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 34
     - Guasto EtherCAT_RFT
     - | 1. Verificare connessione cavo di rete, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 35
     - Guasto indirizzo asse azionamento
     - | 1. Riconfigurare l’indirizzo asse dell’azionamento
       | 2. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 36
     - Guasto taratura zero robot
     - | 1. Eseguire nuovamente la taratura zero del robot
       | 2. Cancellare la FLASH con JLINK, quindi ricaricare il programma ed eseguire la taratura zero
       | 3. Se il guasto persiste, riparare o sostituire la scheda di azionamento

   * - 37
     - Guasto comunicazione encoder
     - | 1. Verificare connessione cablaggio encoder, cortocircuiti o interruzioni
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 40
     - Guasto modulo encoder magnetico – errore taratura zero
     - | 1. Eseguire nuovamente la taratura zero del gruppo encoder magnetico
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 41
     - Guasto modulo encoder magnetico – guasto giri multipli
     - | 1. Controllare se le viti di fissaggio del gruppo encoder magnetico e dell’albero motore sono allentate
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 42
     - Guasto modulo encoder magnetico – guasto piccolo encoder giri multipli
     - | 1. Verificare se il chip del piccolo encoder giri multipli è anomalo
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 43
     - Guasto modulo encoder magnetico – guasto grande encoder giri multipli
     - | 1. Verificare se il chip del grande encoder giri multipli è anomalo
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 44
     - Guasto modulo encoder magnetico – guasto encoder giro singolo
     - | 1. Verificare se il chip dell’encoder giro singolo è anomalo
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

   * - 45
     - Guasto modulo encoder magnetico – guasto encoder ottico
     - | 1. Verificare se il disco dell’encoder ottico è sporco o non incollato correttamente
       | 2. Se il guasto persiste, riparare o sostituire il gruppo encoder magnetico

Appendice 3: Aggiornamento scheda terminale tramite RS485
-----------------------------------------------------------------------------

Durante l’uso sul campo, potrebbe rendersi necessario aggiornare il firmware per soddisfare nuovi requisiti. In tal caso verrà fornito un nuovo file di aggiornamento (XX_XX_MAIN.bin). L’aggiornamento della scheda terminale avviene tramite interfaccia RS485 (richiede un adattatore USB-RS485). Procedura:

**Passo 1: Cablaggio RS485**  
Sul polso del robot è presente un connettore circolare a 5 pin. La disposizione e la descrizione dei pin sono indicate nella Figura 1. Collegare i pin RS485-A e RS485-B del robot rispettivamente ai pin A e B dell’adattatore USB-RS485, utilizzando un cavo twistato.

.. figure:: appendix/001.png
   :align: center
   :width: 4in

.. centered:: Figura 18.3-1 Disposizione pin connettore circolare

**Passo 2: Connessione hardware**  
Collegare la porta USB dell’adattatore USB-RS485 al PC. Se il dispositivo viene riconosciuto correttamente, nel Gestione dispositivi di Windows comparirà una voce come nell’immagine seguente.

.. figure:: appendix/002.png
   :align: center
   :width: 6in

.. centered:: Figura 18.3-2 Identificazione porta USB-RS485

**Passo 3: Strumento di aggiornamento**  
Dopo aver effettuato il cablaggio, aprire lo strumento “FAI Serial Debug Assistant”, cliccare sul pulsante “Scheda Terminale”. Nella sezione “Impostazioni porta seriale”, selezionare la porta rilevata, impostare baud rate a 115200, 8 bit dati, nessuna parità, 1 bit di stop, quindi aprire la porta. In caso di successo, verrà visualizzato il messaggio “Porta seriale aperta correttamente”.

.. figure:: appendix/003.png
   :align: center
   :width: 4in

.. centered:: Figura 18.3-3 Impostazioni porta seriale

**Passo 4: Aggiornamento firmware**  
Selezionare “Scheda Terminale”, quindi cliccare su “Aggiornamento Firmware”, come mostrato in figura:

.. figure:: appendix/004.png
   :align: center
   :width: 6in

.. centered:: Figura 18.3-4 Aggiornamento firmware scheda terminale

- Cliccare prima su “Cancella Flash”; al completamento, nella finestra di ricezione dati apparirà il messaggio di cancellazione riuscita.
- Cliccare su “Apri file” (file da aggiornare) e selezionare il percorso di salvataggio, come mostrato di seguito. Il nome del file selezionato verrà visualizzato nella casella apposita.

.. figure:: appendix/005.png
   :align: center
   :width: 6in

.. centered:: Figura 18.3-5 Selezione file aggiornamento

- Cliccare su “Invia file”. Quando la barra di avanzamento raggiunge il 100%, l’invio del file di aggiornamento è completato.

**Passo 5: Verifica aggiornamento**  
Dopo il riavvio del sistema, andare nella sezione “Informazioni manutenzione”, selezionare “Interroga versione firmware scheda terminale”. Nella finestra di ricezione dati verrà visualizzata la versione del firmware. Se corrisponde alla versione del file caricato, l’aggiornamento è riuscito; altrimenti è fallito.

.. figure:: appendix/006.png
   :align: center
   :width: 6in

.. centered:: Figura 18.3-6 Interrogazione versione firmware

Appendice 4: Aggiornamento armadio di controllo tramite RS485
--------------------------------------------------------------------

Sull’armadio di controllo del robot è presente un’interfaccia “Alimentazione & Comunicazione”. Collegare i pin A e B dell’adattatore USB-RS485 rispettivamente ai terminali “RS485-A” e “RS485-B” di tale interfaccia.

La procedura di aggiornamento è identica a quella della scheda terminale; basterà selezionare il dispositivo corretto nel software. Si omettono ulteriori dettagli.

.. figure:: appendix/007.png
   :align: center
   :width: 4in

.. centered:: Figura 18.4-1 Interfaccia alimentazione & comunicazione

Appendice 5: Elenco ricambi e componenti soggetti a usura
----------------------------------------------------------------

.. list-table::
   :widths: 40 40 20
   :header-rows: 0
   :align: center

   * - **Componente**
     - **Codice**
     - **Quantità**

   * - Vite M8×30
     - 4.0.08.2006185
     - 4

   * - Spinotto cilindrico tipo A 8×20
     - 4.5.00.2013076
     - 2

   * - Fusibile 5×20 6A
     - 
     - 1