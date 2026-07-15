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
