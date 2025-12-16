Stato dell'informazione
===================================

.. toctree:: 
   :maxdepth: 6

Registro di sistema
-----------------------

L'accesso alla sezione "Stato dell'informazione - Registro di sistema" mostra, per impostazione predefinita, tutti i dati del registro del giorno corrente.

I dati del registro sono suddivisi in livelli, attualmente distinti in: tutti, avviso di errore, configurazione di base, configurazione di sicurezza, configurazione di periferica, operazioni sull'entità, programma di insegnamento, applicazione strumento, impostazioni di sistema e importazione/esportazione file.

Nell'angolo in alto a destra della tabella dei dati c'è una casella di input di ricerca, dove gli utenti possono inserire il contenuto da filtrare secondo le loro esigenze. L'interfaccia è la seguente:

.. image:: status/001.png
   :width: 6in
   :align: center

.. centered:: Figura 13.1‑1 Interfaccia del registro di sistema

Interrogazione dello stato
------------------------------------

Utilizzo delle funzioni
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Accendere lo scatola di controllo e connettere il cavo di rete al PC;
2. Aprire il browser sul PC e visitare l'indirizzo 192.168.58.2, accedere con l'account admin e la password 123, entrare nella pagina;
3. Fare clic su "Stato dell'informazione" - "Interrogazione dello stato" nel menu a sinistra per accedere all'interfaccia di interrogazione dello stato, come mostrato nella figura sotto;

.. image:: status/002.png
   :width: 6in
   :align: center

.. centered:: Figura 13.2‑1 Interrogazione dello stato

.. note:: 
   .. image:: status/006.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome:**Pulsante di query**
   
   Funzione: Fare clic per inviare l'istruzione di query grafico/dati tracciato, rappresenta lo stato non interrogato

.. note:: 
   .. image:: status/007.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome:**Pulsante di spostamento verso destra**
   
   Funzione: Fare clic per aggiungere l'elemento selezionato a sinistra nell'elenco secondario a destra

.. note:: 
   .. image:: status/008.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome:**Pulsante di eliminazione**
   
   Funzione: Fare clic per eliminare l'elemento secondario selezionato a destra

.. note:: 
   .. image:: status/009.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome:**Pulsante di svuotamento**
   
   Funzione: Fare clic per svuotare tutti gli elementi secondari a destra

4. Selezionare la visualizzazione del grafico, compilare il tempo ondulatorio, scegliere i parametri da interrogare dall'elenco a sinistra nella configurazione dei parametri, fare clic sul pulsante "spostamento verso destra" per configurare i parametri nell'elenco a destra;

.. note:: Il tempo ondulatorio può essere definito nell'intervallo (10-30s), la configurazione dei parametri consente di selezionare fino a 6 opzioni.

5. Fare clic sul pulsante "query" per iniziare la query, in base alla configurazione dei parametri, viene visualizzato un grafico a linee dei dati in tempo reale, come mostrato nella figura sotto;

.. image:: status/003.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑2 Visualizzazione del grafico

Esportazione del grafico
~~~~~~~~~~~~~~~~~~~~~~~~

1. Fare clic sulla finestra di dialogo del titolo del grafico per modificarlo direttamente, come mostrato nella figura sotto:

.. image:: status/004.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑3 Rinominare il titolo del grafico

2. Dopo aver fatto clic con successo sul pulsante di arresto della query, viene visualizzato il pulsante di download, fare clic per scaricare, il browser propone il download del file del grafico con il nome del titolo del grafico. Come mostrato nella figura sotto:

.. image:: status/005.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑4 Esportazione del grafico

Visualizzazione dei dati
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Dopo aver arrestato la query, fare clic sul pulsante della vista dati nell'angolo in alto a destra del grafico, come mostrato nella figura sotto:

.. image:: status/010.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑5 Pulsante della vista dati

2. I dati nella vista sono come mostrato nella figura, il contenuto dei dati supporta la copia.

.. image:: status/011.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑6 Visualizzazione dei dati

Filtro dei dati
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Dopo aver arrestato la query, inserire i valori minimo/massimo x/y, l'intervallo dei dati del grafico cambierà di conseguenza, come mostrato nella figura sotto:

.. image:: status/012.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑7 Interfaccia di filtro dei dati

2. Fare clic sul pulsante di ripristino, l'intervallo dei dati del grafico tornerà alle impostazioni predefinite, come mostrato nella figura sotto:

.. image:: status/013.png
   :width: 6in
   :align: center

.. centered:: Figura13.2‑8 Ripristino dei dati