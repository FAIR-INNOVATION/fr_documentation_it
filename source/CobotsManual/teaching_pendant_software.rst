Funzionalità di base del software del teach pendant
==============================================================

.. toctree::
   :maxdepth: 6


Informazioni fondamentali
-------------------------

Introduzione al sistema
~~~~~~~~~~~~~~~~~~~~~~~

Il software del teach pendant è un'applicazione dedicata allo sviluppo e al controllo dei robot, eseguita sull'ambiente operativo integrato nel teach pendant. Le sue principali funzioni e caratteristiche tecniche sono le seguenti:

- Consente la stesura di programmi di insegnamento (teaching) per il robot;  
- Visualizza in tempo reale le coordinate di posizione del robot, simula tridimensionalmente il robot fisico e ne permette il controllo diretto;  
- Supporta il movimento manuale monogiro (jogging) su singolo asse nonché il movimento coordinato simultaneo di più assi;  
- Permette la consultazione dello stato degli I/O di controllo;  
- Gli utenti possono modificare la propria password e visualizzare le informazioni di sistema.


Attivazione iniziale del robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Accendere il cabinet di controllo e collegare un cavo Ethernet tra il cabinet e un PC.  

2. Aprire un browser sul PC e accedere all’indirizzo web ``http://192.168.58.2``. Al primo avvio del robot, verrà automaticamente visualizzata la pagina di attivazione.

.. figure:: teaching_pendant_software/058.png
   :width: 4in
   :align: center

.. centered:: Figura 5.1‑1 Interfaccia di attivazione

3. Inserire correttamente il codice seriale (SN) del cabinet di controllo e cliccare sul pulsante **Attiva**.  

4. Il sistema convaliderà il codice SN inserito. Se corretto, l’attivazione verrà completata automaticamente.

.. figure:: teaching_pendant_software/059.png
   :width: 4in
   :align: center

.. centered:: Figura 5.1‑2 Interfaccia di attivazione completata con successo

5. Al termine dell’attivazione, riavviare manualmente il cabinet di controllo.  

6. Dopo il riavvio, accedere nuovamente a ``http://192.168.58.2``: verrà visualizzata la pagina di accesso (login).


Avvio del software
~~~~~~~~~~~~~~~~~~

1. Alimentare il cabinet di controllo;  
2. Sul teach pendant, aprire un browser e accedere all’indirizzo ``http://192.168.58.2``;  
3. Inserire nome utente e password, quindi cliccare su **Accedi** per entrare nel sistema.


Accesso utente e aggiornamento dei permessi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. centered:: Tabella 5.1-1 Utenti predefiniti

.. list-table::
   :widths: 70 70 70 70
   :header-rows: 0
   :align: center

   * - **Codice operatore**
     - **Nome utente predefinito**
     - **Password**
     - **Codice ruolo**

   * - 111
     - admin
     - 123
     - 1

   * - 222
     - MEenginer
     - 222
     - 2

   * - 333
     - PEenginer
     - 333
     - 3
   
   * - 444
     - programmer
     - 444
     - 4
   
   * - 555
     - operator
     - 555
     - 5

   * - 666
     - monitor
     - 666
     - 6


Gli utenti (vedi sezione 15.2.1 *Gestione utenti*) sono suddivisi per impostazione predefinita in sei livelli gerarchici:  
- L’amministratore (**admin**) ha accesso illimitato a tutte le funzionalità;  
- L’operatore (**operator**) e il supervisore (**monitor**) hanno accesso limitato a una parte ristretta delle funzioni;  
- L’ingegnere ME (**MEenginer**), l’ingegnere PE/PQE (**PEenginer**) e il tecnico/capo turno (**programmer**) godono di un livello intermedio di autorizzazioni, con alcune funzioni limitate.  

Per i dettagli completi sui permessi associati ai codici ruolo, fare riferimento alla sezione 15.2.2 *Gestione permessi*.

L’interfaccia di login è illustrata nella figura seguente:

.. figure:: teaching_pendant_software/001.png
   :width: 4in
   :align: center

.. centered:: Figura 5.1‑3 Interfaccia di login


Impostazione multilingua
~~~~~~~~~~~~~~~~~~~~~~~~

- Il sistema supporta nativamente otto lingue: cinese semplificato, cinese tradizionale, inglese (*English*), francese (*français*), coreano (*한국어*), giapponese (*日本語*), russo (*Русский*) e italiano (*italiano*).  

- Ogni pacchetto linguistico deve essere denominato secondo il formato ``[codice_lingua].json`` (es. ``es.json``), dove il codice segue lo standard ISO 639-1.  

- Di seguito è riportata la tabella di corrispondenza tra lingua, denominazione locale e codice ISO:

.. list-table::
   :widths: 70 70 70 70
   :header-rows: 0
   :align: center

   * - **Lingua**
     - **Denominazione locale**
     - **Codice lingua (ISO 639-1)**
     - **Preinstallata**

   * - Cinese
     - 中文（汉语）
     - zh
     - Sì

   * - Cinese
     - 中文（繁體）
     - tc
     - Sì

   * - Inglese
     - English
     - en
     - Sì

   * - Francese
     - français
     - fr
     - Sì
   
   * - Giapponese
     - 日本語
     - ja 
     - Sì

   * - Coreano
     - 한국어
     - ko
     - Sì

   * - Russo
     - Русский
     - ru
     - Sì

   * - Italiano
     - italiano
     - it
     - Sì


1. La selezione della lingua può essere effettuata nell’angolo in alto a destra sia nella pagina di login che in quella di attivazione iniziale.  

.. image:: teaching_pendant_software/062.png
   :width: 6in
   :align: center

.. centered:: Figura 5.1‑5 Selezione lingua nella pagina di attivazione

.. image:: teaching_pendant_software/063.png
   :width: 6in
   :align: center

.. centered:: Figura 5.1‑6 Selezione lingua nella pagina di login

2. Ad esempio, dopo aver scelto una lingua diversa da quella predefinita nella pagina di login, l’interfaccia viene immediatamente aggiornata nella lingua selezionata:  

.. image:: teaching_pendant_software/061.png
   :width: 4in
   :align: center

.. centered:: Figura 5.1‑7 Pagina di login in cinese

.. image:: teaching_pendant_software/001.png
   :width: 4in
   :align: center

.. centered:: Figura 5.1‑8 Pagina di login in inglese

Dopo l’accesso riuscito, il sistema carica modelli e dati correlati; al termine del caricamento, viene visualizzata la pagina iniziale.


Interfaccia iniziale del sistema
---------------------------------------

Dopo l’accesso riuscito, il sistema entra nella **pagina iniziale**, costituita dai seguenti elementi principali:

1. Logo FAIRINO;  
2. Pulsante di ridimensionamento della barra dei menu;  
3. Barra dei menu;  
4. Area di controllo del robot;  
5. Area di stato del robot;  
6. Simulazione 3D del robot — area di interazione con la scena tridimensionale;  
7. Simulazione 3D del robot — area di interazione con il modello del corpo robotico;  
8. Funzionalità ausiliarie integrate al robot;  
9. Stato del robot e delle funzionalità ausiliarie.

Di seguito è riportata una rappresentazione schematica dell’interfaccia iniziale:

.. image:: teaching_pendant_software/002.png
   :align: center
   :width: 6in

.. centered:: Figura 5.2‑1 Schema dell’interfaccia iniziale

Quando si accede alle sezioni *Impostazioni iniziali*, *Programmi di insegnamento → Programmazione testuale*, *Programmi di insegnamento → Programmazione grafica* o alle applicazioni ausiliarie, la finestra della simulazione 3D del robot viene visualizzata in modalità parzialmente espansa. Cliccando sull’icona “Espandi” è possibile tornare all’interfaccia iniziale completa.

.. image:: teaching_pendant_software/054.png
   :align: center
   :width: 6in

.. centered:: Figura 5.2‑2 Icona di espansione della simulazione 3D


Area di controllo
~~~~~~~~~~~~~~~~~

.. note:: 
   .. image:: teaching_pendant_software/003.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di abilitazione (Enable)**  
   Funzione: Abilita il movimento del robot.

.. note:: 
   .. image:: teaching_pendant_software/004.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di avvio (Start)**  
   Funzione: Carica ed esegue il programma di insegnamento corrente.

.. note:: 
   .. image:: teaching_pendant_software/005.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di arresto (Stop)**  
   Funzione: Arresta l’esecuzione del programma di insegnamento corrente.

.. note:: 
   .. image:: teaching_pendant_software/006.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di pausa/riprendi (Pause/Resume)**  
   Funzione: Mette in pausa o riprende l’esecuzione del programma di insegnamento corrente.

.. important::
   L’istruzione di pausa non è valida se inserita alla fine di un programma: in tal caso non viene rilevata né eseguita.

Barra di Stato
~~~~~~~~~~~~~~~~~~

.. note:: 
   .. image:: teaching_pendant_software/011.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato Errore di Esecuzione Robot**
   
    Funzione: Indica un errore durante l'esecuzione del robot. Nascosto quando non ci sono errori.

.. note:: 
   .. image:: teaching_pendant_software/007.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato Robot**
   
    Funzione: Stopped (Fermo), Running (In Esecuzione), Pause (Pausa), Drag (Trascinamento)

.. note:: 
   .. image:: teaching_pendant_software/010.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Sistema di Coordinate dell'Utensile Robot, Sistema di Coordinate del Pezzo, Sistema di Coordinate dell'Asse Esteso e ID Carico**
   
    Funzione: In alto a sinistra – ID del sistema di coordinate dell'utensile corrente. In alto a destra – ID del sistema di coordinate del pezzo corrente. In basso a sinistra – ID del sistema di coordinate dell'asse esteso corrente. In basso a destra – ID del carico corrente.

.. note:: 
   .. image:: teaching_pendant_software/009.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Percentuale Velocità di Esecuzione**
   
    Funzione: Velocità di funzionamento corrente del robot (in percentuale).

.. note:: 
   .. image:: teaching_pendant_software/012.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Automatica**
   
    Funzione: Modalità di funzionamento automatico del robot. Quando è abilitata la funzione "Passa alla Modalità Automatica con Regolazione Velocità Globale" e viene specificata una velocità, la velocità globale si adatterà automaticamente alla velocità specificata.

.. note:: 
   .. image:: teaching_pendant_software/013.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Manuale**
   
    Funzione: Modalità manuale del robot per operazioni di insegnamento.

.. note:: 
   .. image:: teaching_pendant_software/065.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Pulsante Comprimi/Espandi Stato Robot**
   
    Funzione: Comprime o espande la visualizzazione del Sistema di Coordinate dell'Utensile, Sistema di Coordinate del Pezzo, Sistema di Coordinate dell'Asse Esteso, Carico, Stato di Trascinamento Robot, Modalità Locale/Remota, Stato Connessione Robot, Modalità BOOT e Informazioni Account.

Fare clic sul pulsante di compressione per visualizzare le seguenti informazioni di stato.

.. note:: 
   .. image:: teaching_pendant_software/008.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **ID Sistema di Coordinate dell'Utensile**
   
    Funzione: Visualizza l'ID del sistema di coordinate dell'utensile attualmente applicato.

.. note:: 
   .. image:: teaching_pendant_software/027.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **ID Sistema di Coordinate del Pezzo**
   
    Funzione: Visualizza l'ID del sistema di coordinate del pezzo attualmente applicato.
   
.. note:: 
   .. image:: teaching_pendant_software/028.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **ID Sistema di Coordinate dell'Asse Esteso**
   
    Funzione: Visualizza l'ID del sistema di coordinate dell'asse esteso attualmente applicato.

.. note:: 
   .. image:: teaching_pendant_software/066.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Carico**
   
    Funzione: Visualizza il peso del carico attualmente applicato e le coordinate X, Y, Z del suo centro di massa.

.. note:: 
   .. image:: teaching_pendant_software/014.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato di Trascinamento Robot**
   
    Funzione: Il robot può attualmente essere trascinato.

.. note:: 
   .. image:: teaching_pendant_software/015.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato di Trascinamento Robot**
   
    Funzione: Il robot attualmente non può essere trascinato.

.. note:: 
   .. image:: teaching_pendant_software/068.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Locale Robot**
   
    Funzione: Il robot è attualmente controllato dalla centralina di controllo.

.. note:: 
   .. image:: teaching_pendant_software/067.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Remota Robot**
   
    Funzione: Il robot può attualmente essere controllato solo tramite PLC.

.. note:: 
   .. image:: teaching_pendant_software/017.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato connessione**  
   Funzione: Indica che il robot è connesso correttamente al sistema.

.. note:: 
   .. image:: teaching_pendant_software/016.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato disconnessione**  
   Funzione: Indica che il robot non è connesso.

.. note:: 
   .. image:: teaching_pendant_software/018.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Informazioni account**  
   Funzione: Visualizza nome utente, livello di autorizzazione e fornisce il pulsante per il logout.

Barra dei menu
~~~~~~~~~~~~~~~~~

La struttura della barra dei menu è riportata nella tabella seguente:

.. centered:: Tabella 5.2‑1 Struttura dei menu del teach pendant

+----------------------------+----------------------------+
|         Livello 1          |         Livello 2          |
+============================+============================+
|    Impostazioni iniziali   |            Base            |
+----------------------------+----------------------------+
|                            |          Sicurezza         |
+----------------------------+----------------------------+
|                            |         Periferiche        |
+----------------------------+----------------------------+
| Programmi di insegnamento  |   Programmazione testuale  |
+----------------------------+----------------------------+
|                            |   Programmazione grafica   |
+----------------------------+----------------------------+
|                            |   Programmazione a nodi    |
+----------------------------+----------------------------+
|                            |   Punti di insegnamento    |
+----------------------------+----------------------------+
|    Informazioni stato      |        Log di sistema      |
+----------------------------+----------------------------+
|                            |      Consultazione stato   |
+----------------------------+----------------------------+
|  Applicazioni ausiliarie   |          Strumenti         |
+----------------------------+----------------------------+
|                            |    Pacchetti tecnologici   |
+----------------------------+----------------------------+
|     Impostazioni sistema   | /                          |
+----------------------------+----------------------------+


Simulazione 3D del robot
------------------------

Barra di controllo della scena 3D
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Visualizzazione tridimensionale dei sistemi di coordinate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nell’area virtuale 3D del robot all’interno della WebApp vengono creati vari sistemi di coordinate virtuali. A titolo di esempio, la figura seguente mostra il sistema di coordinate di base (*Base CS*), con l’asse X in rosso, Y in verde e Z in blu.

.. note:: 
   .. image:: teaching_pendant_software/021.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Sistema di coordinate di base (Base CS)**  
   Descrizione: Viene visualizzato per impostazione predefinita nell’area virtuale 3D del robot, fissato al centro della base del robot. Può essere disattivato manualmente.

.. note:: 
   .. image:: teaching_pendant_software/022.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Sistema di coordinate dello strumento (Tool CS)**  
   Descrizione: Visualizzato per impostazione predefinita e attivabile/disattivabile manualmente. All’avvio della WebApp e dopo l’accesso riuscito, il sistema recupera il nome e i parametri del sistema di coordinate dello strumento attualmente in uso, quindi lo inizializza.

.. important::
   Durante l’utilizzo di un diverso sistema di coordinate dello strumento, una volta eseguita con successo l’istruzione di cambio, il sistema rimuove prima il sistema di coordinate precedentemente visualizzato nell’area virtuale 3D, quindi invia i nuovi parametri all’API di generazione del sistema di coordinate per creare e visualizzare il nuovo sistema.

.. note:: 
   .. image:: teaching_pendant_software/023.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Sistema di coordinate del pezzo (Wobj CS)**  
   Descrizione: Disattivato per impostazione predefinita; può essere attivato manualmente. Il flusso operativo è identico a quello del sistema di coordinate dello strumento.

.. note:: 
   .. image:: teaching_pendant_software/024.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Sistema di coordinate dell’asse esteso (EAxis CS)**  
   Descrizione: Disattivato per impostazione predefinita; può essere attivato manualmente. Il flusso operativo è identico a quello del sistema di coordinate dello strumento.


Tracciato virtuale 3D e importazione modelli strumento
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. note:: 
   .. image:: teaching_pendant_software/020.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Disegno tracciato**  
   Descrizione: Cliccando questo pulsante si attiva la funzione di tracciamento. Durante l’esecuzione di un programma di insegnamento, il modello 3D del robot traccia la traiettoria effettiva del movimento.

.. note:: 
   .. image:: teaching_pendant_software/029.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Importa modello strumento**  
   Descrizione: Cliccando questo pulsante si apre una finestra modale per caricare un file modello. Una volta caricato con successo, il modello viene visualizzato all’estremità del braccio robotico. I formati supportati sono STL e DAE.


Barra di controllo del corpo robotico
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

TCP
++++++

**Movimento manuale in coordinate di base (Base Jogging)**: Nel sistema di coordinate di base, tenendo premuto il pulsante corrispondente è possibile muovere il robot linearmente lungo gli assi X, Y, Z oppure ruotarlo attorno agli assi RX, RY, RZ. Questa funzione è concettualmente analoga al *jogging* monogiro in coordinate articolari. Vedere figura seguente:

.. image:: teaching_pendant_software/030.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3-1 Esempio di Base Jogging

.. important:: 
   Il movimento si arresta immediatamente rilasciando il pulsante. In caso di emergenza, utilizzare il pulsante di arresto d’urgenza.

**Movimento manuale in coordinate dello strumento (Tool Jogging)**: Selezionando il sistema di coordinate dello strumento, è possibile muovere il robot linearmente lungo gli assi X, Y, Z oppure ruotarlo attorno agli assi RX, RY, RZ, mantenendo costante l’orientamento del TCP. Vedere figura seguente:

.. image:: teaching_pendant_software/031.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3-2 Esempio di Tool Jogging

**Movimento manuale in coordinate del pezzo (Wobj Jogging)**: Selezionando il sistema di coordinate del pezzo, è possibile muovere il robot linearmente lungo gli assi X, Y, Z oppure ruotarlo attorno agli assi RX, RY, RZ, rispetto al sistema di coordinate del pezzo. Vedere figura seguente:

.. image:: teaching_pendant_software/032.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3-3 Esempio di Wobj Jogging

Movimento articolare (Joint)
++++++++++++++++++++++++++++

In modalità *Joint*, i sei cursori centrali rappresentano gli angoli attuali di ciascun asse. Il movimento articolare comprende due modalità: *jogging* monogiro e movimento coordinato multi-asse.

**Jogging monogiro**: L’utente controlla il movimento di un singolo giunto azionando i pulsanti circolari posti ai lati. Vedere figura seguente. Questa modalità è disponibile solo in modalità manuale e nel sistema di coordinate articolare. È particolarmente utile per spostare il robot fuori da una condizione di superamento dei limiti (soft limit) o per effettuare grossolani spostamenti rapidi.

.. image:: teaching_pendant_software/033.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3-4 Esempio di jogging monogiro

.. important::
   Il parametro *Soglia di movimento prolungato* definisce la distanza massima percorsa dal robot quando si tiene premuto un pulsante (intervallo ammesso: 0–300 mm o gradi). Se il pulsante viene rilasciato durante il movimento, il robot si ferma istantaneamente; se invece viene tenuto premuto fino al completamento, il movimento termina esattamente alla distanza impostata.

**Movimento coordinato multi-asse**: L’utente regola i sei cursori centrali per impostare la posizione desiderata del robot. La posizione finale può essere verificata osservando il modello 3D. Se la posizione non soddisfa le aspettative, è possibile cliccare su **Ripristina**, per riportare il modello alla posizione iniziale. Una volta confermata la posizione, cliccando su **Applica**, il robot fisico eseguirà il movimento corrispondente.

.. image:: teaching_pendant_software/034.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3-5 Esempio di movimento coordinato multi-asse

.. important:: 
   Nella modalità multi-asse, il valore impostato per il quinto giunto (j5) non deve essere inferiore a 0,01°. Se il valore richiesto è minore, impostare inizialmente 0,011° e quindi effettuare un fine aggiustamento tramite *jogging* monogiro sul giunto j5.

Movimento cartesiano (Move)
+++++++++++++++++++++++++++++++

Selezionando *Move*, è possibile inserire direttamente i valori cartesiani (X, Y, Z, RX, RY, RZ). Cliccando su **Calcola posizione articolare**, il sistema calcola e visualizza gli angoli corrispondenti. Dopo aver verificato l’assenza di rischi, cliccare su **Muovi a questo punto** per far eseguire al robot il movimento verso la posizione specificata.

.. image:: teaching_pendant_software/035.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑6 Esempio di movimento cartesiano

.. important:: 
   Se la posizione specificata non è raggiungibile, verificare innanzitutto se la posa cartesiana eccede il volume di lavoro del robot; quindi controllare se il percorso dalla posa corrente a quella obiettivo attraversa una configurazione singolare. In tal caso, modificare leggermente la posa corrente o inserire un punto intermedio per evitare la singolarità.

Barra funzionalità integrate al robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Registrazione punti di insegnamento
++++++++++++++++++++++++++++++++++++++++++

L’area di controllo manuale consente di definire i sistemi di coordinate durante la modalità di insegnamento, visualizzando in tempo reale gli angoli articolari e le coordinate cartesiane del robot, e permettendo di memorizzare i punti di insegnamento con nome personalizzato.

I punti salvati ereditano il sistema di coordinate attualmente in uso.

Esistono due modalità di registrazione:

- **Registrazione rapida**: Il punto viene registrato automaticamente con nome generato in modo sequenziale;  
- **Registrazione nominativa**: Il nome del punto è personalizzabile, composto da un prefisso + nome definito dall’utente.  

Per i punti rilevati da sensori, selezionare il tipo di sensore già calibrato, inserire il nome del punto e cliccare su **Aggiungi**: la posizione salvata corrisponderà alla posizione effettivamente rilevata dal sensore.

.. image:: teaching_pendant_software/036.png
   :width: 5in
   :align: center

.. image:: teaching_pendant_software/060.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑7 Area di controllo manuale

.. important:: 
   Alla prima utilizzazione, impostare una velocità bassa (ad es. 30%) per acquisire familiarità con il comportamento del robot e prevenire incidenti.

I/O
+++

Questa interfaccia consente il controllo manuale degli I/O digitali e analogici (0–10 V) presenti nel cabinet di controllo e all’estremità del braccio robotico.

.. image:: teaching_pendant_software/037.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑8 Interfaccia di configurazione I/O


TPD (Programmazione tramite insegnamento)
+++++++++++++++++++++++++++++++++++++++++

La funzione TPD (*Teach Pendant Programming*) opera come segue:

- **Passo 1 – Registrazione posizione iniziale**: Nell’area di controllo a sinistra del modello 3D, registrare la posizione corrente del robot. Inserire un nome nel campo di testo e cliccare su **Salva**. Se l’operazione va a buon fine, viene visualizzato il messaggio *Punto salvato con successo*.  

- **Passo 2 – Configurazione parametri registrazione traiettoria**: Entrare nella sezione TPD e configurare i parametri di registrazione: nome file traiettoria, tipo di posa (cartesiana/articolare), periodo di campionamento, nonché gli ingressi (DI) e uscite (DO) da associare. Durante la registrazione, è possibile attivare l’uscita DO associata tramite l’ingresso DI corrispondente.

.. image:: teaching_pendant_software/038.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑9 Configurazione registrazione TPD

- **Passo 3 – Verifica modalità robot**: Assicurarsi che il robot sia in **modalità manuale**. Se non lo fosse, cambiarla. La modalità di trascinamento (*drag mode*) può essere attivata in due modi: tenendo premuto il pulsante all’estremità del braccio oppure cliccando sul relativo pulsante nell’interfaccia. Per la registrazione TPD si raccomanda l’attivazione tramite interfaccia.

.. image:: teaching_pendant_software/039.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑10 Modalità robot

.. important:: 
   Prima di attivare la modalità di trascinamento tramite interfaccia, verificare che il carico e il baricentro dello strumento siano stati correttamente impostati, e che i coefficienti di compensazione dell’attrito siano adeguati. Confermare il corretto funzionamento del trascinamento tenendo premuto il pulsante all’estremità; solo dopo aver verificato tutto, procedere con l’attivazione tramite interfaccia.

- **Passo 4 – Avvio registrazione**: Cliccare su "Avvia registrazione", quindi trascinare manualmente il robot per insegnare la traiettoria. Inoltre, se è stata configurata l’opzione *Avvio/Arresto registrazione TPD* sugli ingressi digitali (DI), è possibile avviare la registrazione tramite segnale esterno. Nota: per poter attivare questa funzione via segnale esterno, è necessario aver già configurato i parametri TPD nella pagina web.

- **Passo 5 – Arresto registrazione**: Al termine dell’insegnamento, cliccare su "Arresta registrazione". Quindi disattivare la modalità di trascinamento tramite l’apposito pulsante. Il messaggio *Registrazione traiettoria completata con successo* conferma l’esito positivo. Analogamente al passo 4, anche l’arresto può essere comandato via segnale esterno, purché configurato.

- **Passo 6 – Programmazione TPD**: Cliccare su "Nuovo", selezionare il modello vuoto e accedere alla sezione *Programmazione PTP*. Selezionare il punto iniziale appena salvato e cliccare su "Aggiungi": verrà inserita una istruzione PTP nel programma. Successivamente, accedere alla sezione *Programmazione TPD*, selezionare la traiettoria registrata, impostare l’eventuale livellamento (*smoothing*) e il fattore di scala della velocità, quindi cliccare su "Aggiungi": verrà inserita una istruzione "MoveTPD".

.. image:: teaching_pendant_software/040.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑11 Programmazione TPD

- **Passo 7 – Riproduzione traiettoria**: Dopo aver completato la stesura del programma, passare alla "modalità automatica", quindi cliccare sull’icona *Avvia esecuzione* in alto: il robot riprodurrà la traiettoria insegnata.

- **Passo 8 – Modifica traiettoria**: Nell’area di editing TPD è possibile visualizzare, analizzare e tagliare la traiettoria per ottimizzarne la lunghezza e la precisione. Selezionando una traiettoria, i suoi punti vengono mostrati nello spazio 3D del robot. Utilizzando i cursori *Start* e *End*, è possibile simulare e ritagliare la porzione di traiettoria da utilizzare.

Eliminazione file TPD e gestione anomalie:

- **Eliminazione file traiettoria**: Accedere alla sezione TPD, selezionare il file da eliminare e cliccare su "Elimina traiettoria". Se l’operazione ha successo, viene visualizzato un messaggio di conferma.

- **Gestione anomalie**:

  + **Numero massimo di punti superato**: Ogni traiettoria può contenere al massimo 20.000 punti. Superato tale limite, il controller cessa la registrazione e invia all’insegnatore un allarme *Numero massimo di punti superato*: in tal caso, cliccare subito su "Arresta registrazione".  

  + **Intervallo tra istruzioni TPD troppo ampio**: Se l’insegnatore segnala *Intervallo tra istruzioni TPD troppo ampio*, verificare innanzitutto se il robot è tornato alla posizione iniziale di partenza. Se anche in tale condizione l’errore persiste, eliminare la traiettoria corrente e registrarne una nuova.  

  + In caso di altre anomalie impreviste durante l’uso della funzione TPD, fermare immediatamente il robot tramite insegnatore o pulsante di emergenza, quindi indagare sulla causa.

.. important:: 
   Durante l’uso della funzione TPD, seguire scrupolosamente tutti i messaggi e le indicazioni forniti dall’insegnatore.

Movimento assi estesi (Eaxis)
++++++++++++++++++++++++++++++++++++++++++++

La funzione *Eaxis* consente il *jogging* manuale degli assi estesi, previa configurazione completa degli stessi (vedi Capitolo 4 – *Periferiche robotiche – Configurazione assi estesi*).

.. image:: teaching_pendant_software/041.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑12 Interfaccia Eaxis

Forza/torque (FT)
++++++++++++++++++++++

Consente di selezionare il sistema di coordinate di riferimento da utilizzare durante il trascinamento assistito da sensore di forza/torque.

.. image:: teaching_pendant_software/042.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑12 Interfaccia FT

Punto fisso di rotazione (centro di rotazione remota)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Questa funzione è principalmente utilizzata in applicazioni mediche (es. chirurgia percutanea): una volta impostato il punto fisso di rotazione, l’estremità del robot ruoterà sempre attorno a tale punto, mantenendolo costantemente fisso nello spazio.

.. image:: teaching_pendant_software/043.png
   :width: 5in
   :align: center

.. centered:: Figura 5.3‑13 Interfaccia punto fisso di rotazione

Barra stato del robot e funzionalità integrate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Robot
+++++

Visualizza il modello del robot, la rigidità, i dati articolari e le coordinate.

.. image:: teaching_pendant_software/044.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑14 Stato robot

Programma
+++++++++

Visualizza informazioni sul programma correntemente in esecuzione e sui sotto-programmi attivi.

.. image:: teaching_pendant_software/045.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑15 Stato programma

I/O
+++++++++

Visualizza lo stato degli I/O: negli ingressi/uscite digitali, un punto verde indica livello alto (1), bianco indica livello basso (0); negli ingressi/uscite analogici, il valore visualizzato è compreso tra 0 e 100 (100 = 10 V).

.. image:: teaching_pendant_software/046.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑16 Stato I/O


Assi estesi (ExAxis)
++++++++++++++++++++

Visualizza lo stato di servomotori degli assi estesi (controller + PLC).

.. image:: teaching_pendant_software/047.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑17 Stato assi estesi (controller + PLC)

Pinza (Gripper)
+++++++++++++++

Visualizza lo stato corrente della pinza robotica.

.. image:: teaching_pendant_software/048.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑18 Stato pinza

Controllo forza/torque (FT)
+++++++++++++++++++++++++++++++++

Visualizza lo stato corrente del sistema di controllo forza/torque.

.. image:: teaching_pendant_software/049.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑19 Stato controllo forza/torque

Trasportatore (Conveyer)
++++++++++++++++++++++++

Visualizza lo stato corrente del sistema di trasporto (nastro trasportatore).

.. image:: teaching_pendant_software/050.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑20 Stato trasportatore

Servo
+++++

Visualizza lo stato degli assi estesi gestiti da controller + servocontroller.

.. image:: teaching_pendant_software/051.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑21 Stato assi estesi (controller + servocontroller)

Lucidatura (Polish)
+++++++++++++++++++

Visualizza lo stato corrente dell’applicazione di lucidatura.

.. image:: teaching_pendant_software/052.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑22 Stato lucidatura

Saldatura (Weld)
++++++++++++++++

Visualizza lo stato corrente dell’applicazione di saldatura.

.. image:: teaching_pendant_software/053.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑23 Stato saldatura

Board I/O
+++++++++

Visualizza lo stato della scheda I/O interna.

.. image:: teaching_pendant_software/069.png
   :width: 3in
   :align: center

.. centered:: Figura 5.3‑24 Stato scheda I/O