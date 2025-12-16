Avvio Rapido del Robot
==================================

.. toctree:: 
   :maxdepth: 5

Installazione del Braccio Robotico e della Scatola di Controllo
----------------------------------------------------------------------------------

Installare e collegare il braccio robotico e la scatola di controllo secondo le sezioni 3.5 e 3.6 in 3. Installazione Hardware.

-  Prendere il braccio robotico dalla confezione, installarlo utilizzando 4 viti M8 con resistenza non inferiore a grado 8.8. Montare il braccio robotico su una superficie solida e antivibrante. Se fissato con una piastra di alluminio, lo spessore dell'alluminio deve essere di almeno 16 mm; se fissato con una piastra di acciaio, lo spessore dell'acciaio deve essere di almeno 8 mm;

-  Posizionare la scatola di controllo sui suoi piedini;

-  Collegare il cavo ad alta potenza del corpo del braccio robotico all'interfaccia ad alta potenza della scatola di controllo;

-  Inserire il connettore del pulsantiered nella porta insegnatore della scatola di controllo;

-  Assicurarsi che il pulsante di alimentazione della scatola di controllo sia spento (pulsante su 0) e collegare il cavo di alimentazione alla presa di alimentazione;

-  Inserire la spina di alimentazione della scatola di controllo.

.. warning:: 
   (1) Se il robot non è posizionato in sicurezza su una superficie solida, potrebbe ribaltarsi e causare lesioni.
   
   (2) Non accendere e spegnere rapidamente l'alimentazione della scatola di controllo. Si consiglia che il tempo tra OFF e il successivo ON dell'interruttore di alimentazione della scatola di controllo sia superiore a 1 minuto.

Avvio del Robot tramite Insegnatore
---------------------------------------------

La scatola di controllo collega il braccio robotico, l'insegnatore e qualsiasi dispositivo periferico tramite ingressi/uscite elettrici fisici. È necessario accendere la scatola di controllo per alimentare il braccio robotico.

-  Premere il pulsante di alimentazione della scatola di controllo per accenderla;

-  Dopo l'avvio del robot, questo si trova in modalità manuale e non abilitato. Se è necessario operare il robot in modalità manuale, è necessario premere l'interruttore abilitante a tre posizioni sull'insegnatore: OFF (rilasciare) ⇒ ON ⇒ OFF (premere). Quando l'interruttore è in stato ON, trascinare o controllare il movimento del robot.

-  Se non è necessario operare il robot in modalità manuale, è possibile utilizzare il selettore rotante a chiave sull'insegnatore per cambiare la modalità operativa del robot: Automatica, Manuale, Personalizzata;

-  Quando si passa il robot in stato manuale, controllare che non ci siano anomalie all'interno o all'esterno dello spazio di sicurezza e operare il funzionamento della macchina con cautela;

-  Quando si passa il robot in stato automatico, controllare le misure di sicurezza e ripristinarle allo stato normale, quindi operare il funzionamento della macchina con cautela;

-  Se l'insegnatore non si accende normalmente, verificare che le connessioni del dispositivo siano normali.

Controllo del Movimento del Robot tramite Pulsantiered
-------------------------------------------------------------------

Fare riferimento a 3.6.3. Definizione LED terminale in 3. Installazione Hardware per controllare il robot. I pulsantiered esistenti sono divisi in: Pulsantiered 60 (POE)(BX01), Pulsantiered 60 (POE)(BX02)-V1.0, Pulsantiered 60 (POE)(BX02)-V2.0. Prendendo come esempio il Pulsantiered 60 (POE)(BX01), la procedura operativa è la seguente.

Senza Insegnatore
~~~~~~~~~~~~~~~~~~~~~~~

-  **Step1**: Accendere l'interruttore di alimentazione della scatola di controllo del robot, avviare il robot, attendere che il LED terminale sia verde fisso, quindi è possibile operare il robot come mostrato di seguito:

.. figure:: quick_start_robot/001.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-1 Schema LED terminale verde

-  **Step2**: Tenere premuto il "Pulsante 2" del pulsantiered per entrare in modalità senza insegnatore. Il LED terminale lampeggia ciano tre volte, come mostrato di seguito:

.. figure:: quick_start_robot/002.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-2 Schema LED terminale ciano

-  **Step3**: Tenere premuto il "Pulsante 1" del pulsantiered per passare il robot in modalità trascinamento. A questo punto il LED terminale è bianco ciano, come nel Grafico 4.3-3. Spostare il robot in una posizione qualsiasi, tenere premuto il "Pulsante 1" per uscire dalla modalità trascinamento, premere brevemente il "Pulsante 2" del pulsantiered per registrare il punto P1. Il LED terminale lampeggia viola tre volte, come nel Grafico 4.3-4.

-  **Step4**: Spostare il robot, premere brevemente il "Pulsante 2" del pulsantiered per registrare il punto P2. Il LED terminale lampeggia viola tre volte, come nel Grafico 4.3-4.

.. figure:: quick_start_robot/003.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-3 Schema LED terminale bianco ciano

.. figure:: quick_start_robot/004.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-4 Schema LED terminale viola

-  **Step5**: Tenere premuto il "Pulsante 1" del pulsantiered per uscire dalla modalità trascinamento. A questo punto si è in modalità manuale, il LED terminale è verde, come nel Grafico 4.3-5. Premere brevemente il "Pulsante 1" per passare il robot in modalità automatica. A questo punto il LED terminale è blu, come nel Grafico 4.3-6.

-  **Step6**: Premere brevemente il "Pulsante 3" del pulsantiered per eseguire il programma. Il LED terminale lampeggia blu due volte, come nel Grafico 4.3-6.

.. figure:: quick_start_robot/005.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-5 Schema LED terminale verde

.. figure:: quick_start_robot/006.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-6 Schema LED terminale blu

-  **Step7**: Premere brevemente il "Pulsante 3" del pulsantiered per fermare l'esecuzione del programma. Il LED terminale lampeggia rosso tre volte, come mostrato di seguito:

.. figure:: quick_start_robot/007.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-7 Schema LED terminale rosso

Con Insegnatore
~~~~~~~~~~~~~~~~~~~~~~

-  **Step1**: Avviare il robot, attendere che il LED terminale verde smetta di lampeggiare, quindi è possibile operare il robot.

-  **Step2**: Accendere l'insegnatore e accedere all'interfaccia di modifica programma.

-  **Step3**: Selezionare un modello vuoto per creare un nuovo file di programma.

-  **Step4**: Premere brevemente il pulsante 1 del pulsantiered per passare il robot in modalità manuale. A questo punto il LED terminale è verde.

-  **Step5**: Tenere premuto il pulsante 1 del pulsantiered per passare il robot in modalità trascinamento. A questo punto il LED terminale è bianco ciano. Spostare il robot in una posizione qualsiasi, premere brevemente il pulsante 2 del pulsantiered per registrare il punto P1. Il LED terminale lampeggia viola tre volte. Aggiungere manualmente l'istruzione "PTP(p1,100,-1,0)" al file di programma.

.. figure:: quick_start_robot/008.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-8 Registrazione e aggiunta punto P1

-  **Step6**: Spostare il robot, premere brevemente il pulsante 2 del pulsantiered per registrare il punto P2. Il LED terminale lampeggia viola tre volte. Aggiungere manualmente l'istruzione "PTP(p2,100,-1,0)" al programma.

.. figure:: quick_start_robot/009.png
   :align: center
   :width: 4in

.. centered:: Grafico 4.3-9 Registrazione e aggiunta punto P2  

-  **Step7**: Salvare il contenuto del file di programma.

-  **Step8**: Tenere premuto il pulsante 1 del pulsantiered per uscire dalla modalità trascinamento. A questo punto si è in modalità manuale, il LED terminale è verde. Premere brevemente il pulsante 1 del pulsantiered per passare il robot in modalità automatica. A questo punto il LED terminale è blu.

-  **Step9**: Premere brevemente il pulsante 3 del pulsantiered per eseguire il programma. Il LED terminale lampeggia blu due volte.

Controllo del Movimento del Robot tramite Insegnatore
---------------------------------------------------------------

Cliccare il pulsante "Programmazione Insegnamento" nel menu di primo livello a sinistra dell'insegnatore, cliccare il sottomenu "Programmazione Programma" per accedere all'interfaccia di insegnamento programma. Questa interfaccia implementa principalmente la scrittura e la modifica dei programmi di insegnamento del robot.

Dopo aver cliccato il pulsante icona "Nuovo", l'utente assegna un nome al file e seleziona un modello come contenuto del nuovo file. Cliccando Nuovo, la creazione avviene con successo e il file di programma viene aperto.

.. figure:: quick_start_robot/010.png
   :align: center
   :width: 6in
   
.. centered:: Grafico 4.4-1 Schema esecuzione programma insegnamento

.. warning:: 
   La testa e il busto non devono trovarsi all'interno dell'area raggiungibile dal robot (area di lavoro). Non mettere le dita in punti dove il robot potrebbe afferrarle.

.. important:: 
   - Non far muovere il robot dentro se stesso o dentro altri oggetti, poiché ciò potrebbe causare danni al robot.
   - Questa è solo una guida di avvio rapido per insegnare come utilizzare facilmente il robot collaborativo FR. La guida presuppone un ambiente sicuro e innocuo, e un utente attento e cauto. Non aumentare la velocità o l'accelerazione oltre i valori predefiniti. Effettuare sempre una valutazione del rischio prima di mettere il robot in funzione.