Programmazione Rapida del Robot
=================================================

Introduzione Istruzioni di Movimento Semplici
-----------------------------------------------

**Comando PTP**: Cliccare l'icona "Punto a Punto" per accedere all'interfaccia di modifica comando PTP.

È possibile selezionare il punto da raggiungere. L'impostazione del tempo di transizione morbida permette un movimento continuo da questo punto al successivo. È possibile impostare se applicare un offset, scegliendo tra offset basato sul sistema di coordinate base e offset basato sul sistema di coordinate strumento. Verranno visualizzati i campi per impostare gli offset x, y, z, rx, ry, rz. Il percorso specifico PTP è il percorso ottimizzato pianificato automaticamente dal controller di movimento. Cliccando "Aggiungi", "Applica" è possibile salvare questa istruzione.

.. image:: teaching_pendant_software/055.png
   :width: 6in
   :align: center

.. centered:: Grafico 5.1‑1 Interfaccia comando PTP

**Comando Lin**: Cliccare l'icona "Linea" per accedere all'interfaccia di modifica comando Lin.

La funzione di questa istruzione è simile a quella del comando "PTP", ma il percorso per raggiungere il punto con questa istruzione è una linea retta.

.. image:: teaching_pendant_software/057.png
   :width: 6in
   :align: center

.. centered:: Grafico 5.1‑2 Interfaccia comando Lin

Operazioni sul File di Programma
---------------------------------

Utilizzare la barra degli strumenti nella parte superiore dell'albero del programma per modificare l'albero del programma.

.. note:: 
   .. image:: coding/006.png
      :height: 0.75in
      :align: left

   Nome: **Apri**
   
   Funzione: Aprire un file di programma utente

.. note:: 
   .. image:: coding/007.png
      :height: 0.75in
      :align: left

   Nome: **Nuovo**
   
   Funzione: Selezionare un modello per creare un nuovo file di programma
   
.. note:: 
   .. image:: coding/008.png
      :height: 0.75in
      :align: left

   Nome: **Importa**
   
   Funzione: Importare un file nella cartella dei programmi utente

.. note:: 
   .. image:: coding/009.png
      :height: 0.75in
      :align: left

   Nome: **Esporta**
   
   Funzione: Esportare un file di programma utente in un punto locale

.. note:: 
   .. image:: coding/010.png
      :height: 0.75in
      :align: left

   Nome: **Salva**
   
   Funzione: Salvare il contenuto modificato del file.

.. note:: 
   .. image:: coding/011.png
      :height: 0.75in
      :align: left

   Nome: **Salva con nome**
   
   Funzione: Rinominare il file e salvarlo nella cartella dei programmi utente o dei modelli di programma

.. note:: 
   .. image:: coding/012.png
      :height: 0.75in
      :align: left

   Nome: **Copia**
   
   Funzione: Copiare un nodo, consentendone l'uso in altre operazioni (ad esempio: incollarlo in altre posizioni dell'albero del programma)

.. note:: 
   .. image:: coding/013.png
      :height: 0.75in
      :align: left

   Nome: **Incolla**
   
   Funzione: Consente di incollare un nodo precedentemente tagliato o copiato

.. note:: 
   .. image:: coding/014.png
      :height: 0.75in
      :align: left

   Nome: **Taglia**
   
   Funzione: Tagliare un nodo, consentendone l'uso in altre operazioni (ad esempio: incollarlo in altre posizioni dell'albero del programma)

.. note:: 
   .. image:: coding/015.png
      :height: 0.75in
      :align: left

   Nome: **Elimina**
   
   Funzione: Eliminare un nodo dall'albero del programma

.. note:: 
   .. image:: coding/016.png
      :height: 0.75in
      :align: left

   Nome: **Sposta su**
   
   Funzione: Spostare il nodo verso l'alto

.. note:: 
   .. image:: coding/017.png
      :height: 0.75in
      :align: left

   Nome: **Sposta giù**
   
   Funzione: Spostare il nodo verso il basso

.. note:: 
   .. image:: coding/018.png
      :height: 0.75in
      :align: left

   Nome: **Cambia modalità modifica**
   
   Funzione: Passare dalla modalità albero del programma alla modalità di modifica lua e viceversa

Scrittura ed Esecuzione di un Programma
----------------------------------------

La parte sinistra è principalmente dedicata all'aggiunta di comandi di programma. Cliccando le icone sopra le parole chiave si accede all'interfaccia dettagliata a destra per l'aggiunta di comandi di programma. Le operazioni per aggiungere comandi di programma al file si dividono principalmente in due tipi:

- 1. Aprire l'istruzione correlata e cliccare il pulsante Applica per aggiungere l'istruzione al programma;
- 2. Cliccare prima il pulsante "Aggiungi". A questo punto il comando non è salvato nel file di programma, è necessario cliccare "Applica" per salvare il comando nel file.

Il secondo metodo si presenta spesso quando si devono inviare più istruzioni dello stesso tipo. Per questo tipo di comando è stata aggiunta la funzione di pulsante di aggiunta e visualizzazione del contenuto delle istruzioni già aggiunte. Cliccando il pulsante Aggiungi si aggiunge un'istruzione. La sezione delle istruzioni già aggiunte mostra tutte le istruzioni aggiunte. Cliccando "Applica" è possibile salvare le istruzioni aggiunte nel file aperto a destra.

Cliccando il pulsante Avvia, si esegue il programma; cliccando il pulsante Ferma, si interrompe l'esecuzione del programma; cliccando il pulsante Pausa/Riprendi, si mette in pausa/riprende il programma. Durante l'esecuzione del programma, il nodo del programma attualmente in esecuzione viene evidenziato in verde.

In modalità manuale, cliccando la prima icona a destra di un nodo si può far eseguire al robot solo quell'istruzione; la seconda icona serve per modificare il contenuto di quel nodo.

.. image:: coding/001.png
   :width: 6in
   :align: center

.. centered:: Grafico 5.3‑1 Interfaccia albero del programma