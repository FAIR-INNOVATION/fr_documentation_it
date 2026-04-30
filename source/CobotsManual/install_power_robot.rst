Installazione del robot e accensione
=========================================================

.. toctree:: 
   :maxdepth: 6

Installazione del braccio del robot
-------------------------------------------

Quando il robot collaborativo è installato sulla base di montaggio, utilizzare il numero appropriato di viti (con una resistenza non inferiore al grado 8.8) per fissare il robot alla base di montaggio; si consiglia di utilizzare due fori di posizione conformi nella base di montaggio con perni per migliorare la precisione di installazione del robot e prevenire il movimento del robot a causa di collisioni o altri motivi. Quando il robot ha requisiti elevati di precisione di movimento, è fondamentale utilizzare i perni per posizionare il robot.

.. centered:: Tabella 1.1-1 Standard dei componenti per l'installazione del robot

.. list-table::
   :widths: 80 50 50 50
   :header-rows: 0
   :align: center

   * - **Modello del robot collaborativo**
     - **Viti**
     - **Torque delle viti**
     - **Specifiche dei fori di posizione**

   * - FR3
     - 4 viti M6
     - ≥10Nm
     - φ5mm

   * - FR3-WMS
     - 4 viti M6
     - ≥10Nm
     - φ5mm

   * - FR3-WML
     - 4 viti M6
     - ≥10Nm
     - φ5mm

   * - FR3-C
     - 4 viti M6
     - ≥10Nm
     - φ5mm

   * - FR5-C
     - 4 viti M6
     - ≥10Nm
     - φ5mm
   
   * - FR5
     - 4 viti M8
     - ≥20Nm
     - φ8mm

   * - FR10
     - 4 viti M8
     - ≥25Nm
     - φ8mm

   * - FR16
     - 4 viti M8
     - ≥25Nm
     - φ8mm

   * - FR20
     - 6 viti M10
     - ≥45Nm
     - φ8mm

   * - FR30
     - 6 viti M10
     - ≥45Nm
     - φ8mm

   * - FR30L
     - 6 viti M10
     - ≥45Nm
     - φ8mm

.. important:: 
   Si consiglia che la base di montaggio del robot soddisfi i seguenti requisiti per garantire una solida e stabile installazione:

   (1) La base di montaggio del robot deve essere sufficientemente solida e avere una capacità di carico sufficiente, in grado di sopportare almeno 5 volte il peso del robot e almeno 10 volte il torque dell'asse 1.

   (2) La superficie della base di montaggio del robot deve essere piana per garantire una stretta aderenza tra la superficie di contatto del robot e la base;

   (3) La base di montaggio del robot deve avere una rigidità sufficiente per fissare il robot senza vibrazioni o risonanza;

   (4) Quando il robot e altri componenti si muovono simultaneamente, la base di montaggio deve essere separata da altri componenti in movimento per evitare interferenze dovute a vibrazioni;

   (5) Se il robot è installato su una piattaforma mobile o su un asse esterno, l'accelerazione della piattaforma mobile o dell'asse esterno deve essere mantenuta il più bassa possibile.

Connessione del quadro di controllo
-------------------------------------------

Questa serie di robot può essere configurata con tre diverse opzioni di ingresso di alimentazione per il quadro di controllo. Le informazioni sul tipo di alimentazione sono disponibili sulla targhetta del quadro di controllo. Il robot deve essere messo a terra elettricamente. Tutti i collegamenti esterni del sistema di controllo del braccio utilizzano connettori staccabili e facili da installare.

A. 30-60VDC  
B. 176-264VAC~50-60Hz  
C. 100-240VAC~50-60HZ

.. note:: I quadri di controllo con ingresso AC sono disponibili in due versioni, a bassa tensione e ad alta tensione. I terminali di collegamento e l'aspetto sono identici, quindi non possono essere distinti solo dall'aspetto. Si prega di confermare tramite la targhetta del quadro di controllo e accertarsi prima di accendere il sistema.

Il pannello di collegamento del robot collaborativo è mostrato nel diagramma sottostante:

.. image:: installation/037.png
   :width: 6in
   :align: center

.. centered:: Diagramma 1.2-1 Pannello di collegamento del quadro di controllo

L'interfaccia della scatola dei tasti è predefinita come porta di controllo del teach pendant. L'indirizzo IP è 192.168.58.2. Collega l'interfaccia della scatola dei tasti al computer utilizzando un cavo di rete, con l'indirizzo IP del computer impostato su 192.168.58.10 o in un segmento di rete simile. Apri Google Chrome e inserisci 192.168.58.2 per accedere alla pagina del teach pendant.

Conoscere la scatola dei tasti e il LED finale
------------------------------------------------

Scatola dei tasti
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Scatola dei tasti 60 (POE) (BX01)
++++++++++++++++++++++++++++++++++++++++++

.. figure:: installation/058.png
	:align: center
	:width: 6in

.. centered:: Diagramma 1.3-1 Scatola dei tasti 60 (POE)

Scatola dei tasti 60 (POE) (BX02)-V1.0
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. image:: installation/059.png
   :width: 6in
   :align: center

.. centered:: Diagramma 1.3-2 Pannello di collegamento del quadro di controllo

.. centered:: Tabella 1.3-1 Descrizione dei tasti del pannello del quadro di controllo

.. list-table::
   :widths: 50 200
   :header-rows: 0
   :align: center

   * - **Nome del tasto**
     - **Funzione**

   * - Tasto di emergenza
     - Quando il tasto di emergenza è premuto, il robot entra in modalità di arresto di emergenza

   * - Avvio/fermata
     - Avvia/ferma l'esecuzione del programma

   * - Porta di rete
     - Connessione al teach pendant via web

   * - Spegnimento
     - Non abilitato

   * - Salvataggio punto
     - Salva il punto di insegnamento

   * - Modalità insegnamento
     - Entra/esce dalla modalità di insegnamento

   * - Modalità di esecuzione
     - Passa dalla modalità automatica alla manuale

   * - Modalità di trascinamento
     - Entra/esce dalla modalità di trascinamento

Scatola dei tasti 60 (POE) (BX02)-V2.0
++++++++++++++++++++++++++++++++++++++++++++

.. image:: installation/079.png
   :width: 6in
   :align: center

.. centered:: Diagramma 1.3-3 Pannello di collegamento del quadro di controllo

.. centered:: Tabella 1.3-2 Descrizione dei tasti del pannello del quadro di controllo

.. list-table::
   :widths: 50 200
   :header-rows: 0
   :align: center

   * - **Nome del tasto**
     - **Funzione**

   * - Tasto di emergenza
     - Quando il tasto di emergenza è premuto, il robot entra in modalità di arresto di emergenza

   * - Avvio/fermata
     - Avvia/ferma l'esecuzione del programma

   * - Porta di rete
     - Connessione al teach pendant via web

   * - Ripristino IP
     - Ripristina l'indirizzo IP della porta di rete

   * - Salvataggio punto
     - Salva il punto di insegnamento

   * - Reset completo
     - Cancella tutti gli errori recuperabili

   * - Modalità di esecuzione
     - Passa dalla modalità automatica alla manuale

   * - Modalità di trascinamento
     - Entra/esce dalla modalità di trascinamento

LED finale
~~~~~~~~~~~~~~

.. centered:: Tabella 1.3-3 Definizione dei LED finali

.. list-table::
   :widths: 120 100
   :header-rows: 0
   :align: center

   * - **Funzione**
     - **Colore LED**

   * - Comunicazione non stabilita
     - "Spento", "Rosso", "Verde", "Blu" alternati

   * - Modalità automatica
     - Blu acceso fisso

   * - Modalità manuale
     - Verde acceso fisso

   * - Modalità trascinamento
     - Ciano acceso fisso

   * - Salvataggio punto (solo quando si usa la scatola dei tasti)
     - Viola lampeggia due volte

   * - Modalità non associata (solo quando si usa la scatola dei tasti)
     - Azzurro lampeggia due volte

   * - Inizio esecuzione (solo quando si usa la scatola dei tasti)
     - Blu lampeggia due volte

   * - Ferma esecuzione (solo quando si usa la scatola dei tasti)
     - Rosso lampeggia due volte

   * - Errore (solo quando si usa la scatola dei tasti)
     - Rosso acceso fisso

   * - Reset zero completato
     - Ciano lampeggia tre volte

   * - Disabilitato
     - Giallo lampeggia due volte

Abilitazione all'accensione
-------------------------------------------

Prima di accendere, assicurarsi che il pulsante di emergenza della scatola dei tasti sia in stato di rilascio. Premere il pulsante rosso sul quadro di controllo per accendere l'alimentazione. Dopo l'abilitazione, il LED finale deve essere verde fisso.

Spegnimento
----------------

.. important:: 
  Quando si spegne questo dispositivo, assicurarsi di fermare tutti i programmi in esecuzione, disabilitare le funzioni di verifica dello stato e confermare che lo stato di funzionamento sia "Stopped". Questa operazione è volta a proteggere la sicurezza dei dati e dei dispositivi, evitando perdite di dati o danni al sistema causati da un'interruzione improvvisa dell'alimentazione.

.. image:: installation/078.png
   :width: 6in
   :align: center

.. centered:: Diagramma 1.5-1 Pulsante di spegnimento

Batteria a Bottone del Box di Controllo
----------------------------------------------------------------

Cause Comuni della Perdita dell'Ora
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Questo dispositivo utilizza una batteria a bottone esterna come alimentazione di riserva per l'orologio in tempo reale (RTC), utilizzata per mantenere il conteggio dell'ora quando l'alimentazione principale è disconnessa.

Se si verifica una perdita dell'ora (cioè, dopo il riavvio viene visualizzata una data errata), di solito è causata da una o più delle seguenti ragioni:

.. list-table::
   :widths: 40 40 60
   :header-rows: 0
   :align: center

   * - **Categoria della Causa**
     - **Descrizione Specifica**
     - **Suggerimenti per la Risoluzione**

   * - Batteria a bottone scarica
     - Il dispositivo non è stato acceso per più di 3 mesi, causando il consumo naturale dell'energia della batteria.
     - Misurare la tensione della batteria con un multimetro (rimuoverla per la misurazione). Se la tensione è inferiore a 2,5V, è necessario ricaricarla.

   * - Batteria danneggiata
     - La batteria ha raggiunto la fine della sua vita utile.
     - Verificare se la batteria presenta perdite o gonfiori. È necessario sostituire la batteria. Modello batteria: MS621FE-FL11E, 3V/5,5mAH, ricaricabile.

   * - Scarsa contatto dei terminali della batteria
     - I terminali della batteria sono ossidati, deformati, o il dispositivo ha subito vibrazioni che hanno causato il distacco momentaneo della batteria dai contatti.
     - Verificare che la batteria sia inserita saldamente nei terminali, pulire i contatti, reinstallare la batteria e assicurarsi che sia bloccata saldamente.

   * - Batteria non installata o installata al contrario
     - L'utente non ha installato la batteria di riserva, o ha invertito la polarità durante l'installazione.
     - | Confermare che la batteria sia installata con la polarità corretta (polo positivo rivolto verso l'alto).
       .. image:: installation/131.png
          :width: 2in
          :align: center

   * - Guasto del circuito di ricarica della batteria
     - La batteria a bottone ricaricabile non è in grado di accumulare carica normalmente.
     - Il circuito di ricarica deve essere ispezionato da personale di manutenzione qualificato.

.. warning:: La batteria a bottone utilizzata in questo dispositivo è il modello [MS621FE-FL11E, 3V/5,5mAH, ricaricabile]. Assicurarsi di scegliere il metodo di gestione corretto in base al modello. È severamente vietato installare batterie non ricaricabili.

Identificazione delle Anomalie Temporali e Calibrazione Manuale
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Metodo di Identificazione delle Anomalie
   
Dopo il riavvio del robot, verificare prima l'ora corrente visualizzata sulla pagina del dispositivo. Confrontarla con l'ora di sistema del computer:

- Se corrispondono, l'ora è normale e non sono necessarie ulteriori operazioni.

.. image:: installation/132.png
   :width: 4in
   :align: center

.. centered:: Figura 1.6-1 Anomalia dell'Ora di Sistema

- Se non corrispondono (ad esempio, data errata, deviazione significativa di ore/minuti/secondi), viene determinata un'anomalia temporale. Procedere con i seguenti passaggi di calibrazione.
  
2) Passaggi di Calibrazione

Se è stata confermata un'anomalia temporale, seguire le seguenti operazioni per sincronizzare l'ora di sistema:

- Aprire il browser per accedere al WebApp e navigare all'interfaccia: "Impostazioni di Sistema -> Impostazioni Generali -> Ora".

.. image:: installation/133.png
   :width: 6in
   :align: center

.. centered:: Figura 1.6-2 Interfaccia di Aggiornamento dell'Ora di Sistema

- Fare clic sul pulsante "Aggiorna" nell'interfaccia. Il sistema completerà automaticamente la sincronizzazione dell'ora. Dopo la sincronizzazione, tornare alla pagina del robot e l'ora dovrebbe essere ripristinata alla normalità.

Precauzioni per la Ricarica e la Manutenzione della Batteria a Bottone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Condizioni di Ricarica

- Dopo che l'alimentazione principale del dispositivo è collegata (220V AC), il circuito di ricarica viene attivato automaticamente.
- La temperatura ambiente dovrebbe essere compresa tra 0℃ e 45℃. Le temperature elevate riducono l'efficienza di ricarica e accorciano la durata della batteria.

2) Tempo di Ricarica

- Una batteria completamente scarica richiede circa [5 ore] per essere completamente ricaricata. La funzione di mantenimento dell'ora funziona normalmente durante questo periodo.

3) Azioni Vietate

- Non utilizzare caricabatterie esterni per caricare direttamente la batteria a bottone all'interno del dispositivo.
- Non installare batterie non ricaricabili nel dispositivo, poiché ciò potrebbe causare pericolo.

Sostituzione e Smaltimento della Batteria
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1) Ciclo di Sostituzione

- Di solito può essere utilizzata per più di [5 anni]. Sostituire se si verifica una perdita frequente dell'ora.

2) Passaggi di Sostituzione

- Scollegare l'alimentazione principale del dispositivo.
- Aprire il coperchio superiore.
- Rimuovere la vecchia batteria, prestando attenzione alla direzione della polarità.
- Saldare una nuova batteria qualificata dello stesso modello (polo positivo rivolto verso l'alto).
- Chiudere il coperchio, riaccendere e calibrare l'ora corrente.

3) Smaltimento

- Non gettare la batteria nel fuoco né esporla all'acqua.
- Riciclare le batterie esauste secondo le normative locali (le batterie a bottone contengono tipicamente litio o metalli pesanti).

Supporto Tecnico
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Se il problema persiste dopo aver seguito i passaggi precedenti, contattare il nostro team di supporto tecnico e fornire le seguenti informazioni:

- Modello e numero di serie del dispositivo.
- Il modello di batteria utilizzato (controllare l'incisione sulla superficie della batteria).
- Fenomeno del guasto (ad esempio, ora persa immediatamente dopo l'interruzione di corrente / persa dopo essere rimasto spento per una notte).