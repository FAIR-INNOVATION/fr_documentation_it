Punti di Insegnamento
=================================

.. toctree:: 
   :maxdepth: 6

La gestione dell'insegnamento è suddivisa in due modalità: "Modalità Sistema" e "Modalità Tabella Punti", per consentire, durante la chiamata di un programma del manipolatore, di implementare diversi schemi di ispezione richiamando diverse tabelle di punti, soddisfacendo così le esigenze della ricetta. Successivamente, ogni volta che viene aggiunto un nuovo dispositivo o prodotto, il pacchetto dati della tabella punti può essere scaricato nel robot tramite il sistema supervisore, e i pacchetti dati delle nuove tabelle di punti create dal robot possono anche essere caricati al sistema supervisore.

**Modalità Sistema**: Supporta "importare, esportare, eliminare, rinominare, modificare, sovrascrivere, modificare, visualizzare" il contenuto dei punti di insegnamento, nonché il movimento passo-passo ai punti di insegnamento.

.. image:: points/001.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-1 Interfaccia gestione insegnamento - Modalità Sistema

**Modalità Tabella Punti**: Supporta "aggiungere, applicare, rinominare, eliminare, importare, esportare" tabelle di punti, "eliminare, modificare, visualizzare e sovrascrivere" il contenuto dei punti all'interno della tabella punti, nonché il movimento passo-passo ai punti di insegnamento.

.. image:: points/002.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-2 Interfaccia gestione insegnamento - Modalità Tabella Punti

Nell'angolo in alto a destra dell'interfaccia di gestione dell'insegnamento viene visualizzata la barra di controllo del corpo robot. In questa interfaccia, l'utente può spostare il corpo del robot, quindi eseguire l'operazione di sovrascrittura dei dati del punto di insegnamento.

.. image:: points/003.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-3 Interfaccia gestione insegnamento - Barra di controllo corpo robot

Nell'angolo in alto a destra della tabella dei dati dei punti di insegnamento è possibile inserire il nome del punto di insegnamento per la ricerca; cliccando sul nome del punto di insegnamento nella tabella dei dati, si entra in modalità modifica. Inserendo il nome modificato e cliccando al di fuori del nome del punto di insegnamento, la modifica viene completata.

.. note:: 
   .. image:: points/004.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Importa**
   
   Funzione: Importazione file punto di insegnamento

.. note:: 
   .. image:: points/005.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Esporta**
   
   Funzione: Esportazione file punto di insegnamento

.. note:: 
   .. image:: points/006.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Elimina**
   
   Funzione: Dopo aver selezionato uno o più punti di insegnamento, cliccando il pulsante "Elimina" sopra la tabella, viene richiesto di "Cliccare nuovamente il pulsante Elimina per confermare l'eliminazione". Cliccando nuovamente, le informazioni del punto vengono eliminate;

.. note:: 
   .. image:: points/007.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Sovrascrivi Punto**
   
   Funzione: Cliccare per sovrascrivere il punto di insegnamento con i dati di posizione correnti del robot, e nella finestra di dialogo scegliere "Sincronizzare il programma di insegnamento"

.. image:: points/008.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-4 Sovrascrittura punto di insegnamento

.. note:: 
   .. image:: points/009.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Modifica**
   
   Funzione: Cliccare per confermare la modifica dei valori x, y, z, rx, ry, rz e v del punto di insegnamento

.. important:: 
   I valori modificati di x, y, z, rx, ry, rz del punto di insegnamento non devono superare il campo di lavoro del robot.

.. note:: 
   .. image:: points/010.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Dettagli**
   
   Funzione: Cliccare per visualizzare i dettagli del punto di insegnamento

.. image:: points/011.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-5 Dettagli punto di insegnamento

.. note:: 
   .. image:: points/012.png
      :height: 0.75in
      :align: left

   Nome: **Pulsante Avvia Esecuzione**
   
   Funzione: Cliccare per scegliere il metodo di esecuzione del punto singolo, spostando il robot nella posizione di quel punto; selezionare PTP per movimento punto a punto, selezionare Lin per movimento lineare.

.. image:: points/013.png
   :width: 6in
   :align: center

.. centered:: Grafico 12.1-6 Esecuzione punto di insegnamento