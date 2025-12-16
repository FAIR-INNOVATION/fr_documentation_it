Impostazioni Parametri del Robot
==============================================

Impostazione Metodo di Installazione
------------------------------------------------------

Il metodo di installazione predefinito del robot è orizzontale. Quando il metodo di installazione del robot viene modificato, è necessario impostare tempestivamente il metodo di installazione effettivo del robot in "Impostazioni Iniziali" -> "Base" -> "Installazione" per garantire il normale funzionamento del robot.

Considerando scenari di distribuzione del robot più flessibili e ricchi, forniamo la funzione di installazione libera. L'utente clicca su "Impostazioni Iniziali" -> "Base" -> "Installazione" per accedere alla pagina di impostazione del metodo di installazione del robot. Regola manualmente gli angoli di "Inclinazione Base" e "Rotazione Base", il modello 3D mostrerà l'effetto dell'installazione corrispondente. Dopo la modifica, clicca il pulsante "Applica" per completare l'impostazione del metodo di installazione del robot.

.. image:: teaching_pendant_software/026.png
   :width: 6in
   :align: center
   
.. centered:: Grafico 3.1-1 Installazione Robot

.. important::
    Dopo aver installato il robot, è necessario impostare correttamente il metodo di installazione del robot, altrimenti influenzerà l'uso della funzione di trascinamento e della funzione di rilevamento collisioni del robot.

Impostazione Carico Estremità
--------------------------------------

In "Impostazioni Iniziali" -> "Base" -> "Carico", nel tipo di identificazione "Identificazione Traiettoria", accedere all'interfaccia di impostazione del carico all'estremità.

.. note:: 
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Applica**
   
   Funzione: Cliccare per applicare il peso del carico e le coordinate del centro di massa corrispondenti al numero del carico

.. note:: 
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Modifica**
   
   Funzione: Cliccare per aprire/chiudere l'interfaccia movimento identificazione

.. note:: 
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Rinomina**
   
   Funzione: Rinominare il nome del carico

.. note:: 
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Svuota**
   
   Funzione: Svuotare le informazioni del carico corrente (impostare peso carico e coordinate centro di massa a 0)

Durante la configurazione del carico all'estremità, è possibile inserire direttamente la massa dello strumento terminale e le corrispondenti coordinate del centro di massa X, Y e Z, quindi cliccare il pulsante "Applica" per impostare.

Allo stesso tempo, è possibile cliccare il pulsante "Modifica" per aprire l'interfaccia "Movimento Identificazione" per l'identificazione automatica del carico. Dopo il completamento dell'esecuzione dell'identificazione, applicare.

.. important:: 
   La massa del carico non deve superare il carico massimo del robot. I carichi corrispondenti ai modelli sono i seguenti:

   - FR3: 3 kg

   - FR5: 5 kg

   - FR10: 10 kg

   - FR16: 16 kg
   
   - FR20: 20 kg
   
   - FR30: 30 kg

   L'intervallo di impostazione delle coordinate del centro di massa è 0-1000, unità mm.

.. image:: base/016.png
   :width: 4in
   :align: center

.. centered:: Grafico 3.2-1 Schema impostazione carico
    
.. important:: 
    Dopo aver installato il carico all'estremità del robot, è necessario impostare correttamente il peso del carico all'estremità e le coordinate del centro di massa, altrimenti influenzerà l'uso della funzione di trascinamento e della funzione di rilevamento collisioni del robot.

Impostazione Coordinate Strumento
-----------------------------------------

In "Impostazioni Iniziali" -> "Base" -> "Coordinate Strumento" accedere alla pagina delle coordinate dello strumento.

.. note:: 
   .. image:: base/071.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Applica**
   
   Funzione: Cliccare per applicare il sistema di coordinate dello strumento

.. note:: 
   .. image:: base/072.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Modifica**
   
   Funzione: Cliccare per aprire/chiudere l'interfaccia di taratura del sistema di coordinate

.. note:: 
   .. image:: base/073.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Rinomina**
   
   Funzione: Rinominare il nome del sistema di coordinate dello strumento

.. note:: 
   .. image:: base/074.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Svuota**
   
   Funzione: Svuotare le informazioni delle coordinate dello strumento corrente

Le coordinate dello strumento consentono di modificare, svuotare e applicare le coordinate dello strumento. Nell'elenco a discesa dei sistemi di coordinate dello strumento, selezionando il sistema di coordinate corrispondente, verranno visualizzati in basso i valori delle coordinate corrispondenti (il nome del sistema di coordinate può essere personalizzato), il tipo di strumento e la posizione di installazione (visualizzato solo per strumenti di tipo sensore). Dopo aver selezionato un sistema di coordinate, cliccando il pulsante "Applica", il sistema di coordinate dello strumento in uso diventa quello selezionato, come mostrato di seguito.

.. image:: base/001.png
   :width: 4in
   :align: center
   
.. centered:: Grafico 3.3-1 Impostazione coordinate strumento

Cliccando "Modifica" è possibile reimpostare il sistema di coordinate dello strumento per quel numero in base alle istruzioni. I metodi di taratura dello strumento sono divisi in metodo a quattro punti e metodo a sei punti. Il metodo a quattro punti taratura solo il TCP dello strumento, cioè la posizione del punto centrale dello strumento, la cui postura è predefinita come coerente con la postura terminale. Il metodo a sei punti aggiunge due punti sulla base del metodo a quattro punti, utilizzati per tarare la postura dello strumento.

.. image:: base/002.png
   :width: 4in
   :align: center

.. centered:: Grafico 3.3-2 Taratura sistema coordinate strumento

.. important:: 
    1. Dopo aver installato lo strumento all'estremità, è necessario effettuare la taratura e l'applicazione del sistema di coordinate dello strumento, altrimenti la posizione e la postura del punto centrale dello strumento durante l'esecuzione delle istruzioni di movimento del robot non corrisponderanno ai valori previsti.

    2. I sistemi di coordinate dello strumento generalmente utilizzano toolcoord1~toolcoord19. Applicare toolcoord0 significa che la posizione centrale del TCP dello strumento si trova al centro della flangia terminale. Durante la taratura del sistema di coordinate dello strumento, è necessario prima applicare il sistema di coordinate dello strumento a toolcoord0, quindi selezionare altri sistemi di coordinate dello strumento per la taratura e l'applicazione.