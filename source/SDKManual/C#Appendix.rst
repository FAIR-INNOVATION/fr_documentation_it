Appendice
=================

.. toctree:: 
    :maxdepth: 5

Download del codice sorgente
------------------------------------------------
Nel sito della documentazione Faro (https://fairino-doc-it.readthedocs.io/latest/), trovare il modulo "Download materiali", fare clic sul pulsante "C#SDK", nella pagina a destra fare clic su "FAIRINOC#SDK" e attendere il completamento del download da parte del browser.

.. image:: image/001.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.1‑1 Download del codice sorgente #SDK
    
Scaricare e decomprimere l'SDK C#. La struttura della directory del progetto è mostrata nella figura seguente. Tra questi, il file "examples" contiene esempi di test, il file "src" contiene l'SDK C#, "Fairino.sln" è la soluzione del progetto. "Dlls" contiene i file di libreria.

.. image:: image/010.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.1‑2 Esempio della struttura dei file dell'SDK C#

Trovare il file di soluzione denominato "fairino.sln", aprirlo con un doppio clic. La struttura dei file è mostrata nella figura seguente.

.. image:: image/011.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.1‑3 Esempio della struttura dei file del progetto in Visual Studio 2022

Compilazione del codice sorgente su piattaforma Windows
-----------------------------------------------------------------

Compilazione dell'SDK C#
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Fare clic sul progetto FRRobot, fare clic con il tasto destro e selezionare Proprietà, scegliere la versione del framework .NET.

.. image:: image/012.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑1 Impostazione delle proprietà

.. image:: image/013.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑2 Selezione del framework .NET

.. image:: image/014.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑3 Generazione del progetto FRRobot in modalità Release

Impostare Visual Studio 2022 in modalità Release, rigenerare il progetto FRRobot. Nella cartella \bin\Release verrà generata la libreria a collegamento dinamico (dll).

.. image:: image/015.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑4 Impostazione della modalità Release

.. image:: image/016.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑5 Rigenerazione del progetto FRRobot in modalità Release

.. image:: image/016.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑6 Generazione della libreria a collegamento dinamico (dll)

Utilizzo dell'SDK C#
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Fare clic con il tasto destro sul progetto "testFrRobot" e selezionarlo come progetto di avvio.

.. image:: image/017.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑7 Impostazione come progetto di avvio
 
L'interfaccia di test dell'SDK C# è mostrata nella figura seguente.

.. image:: image/018.png
   :width: 6in
   :align: center

.. centered:: Grafico 15.2‑8 Interfaccia di test dell'SDK C#

Note importanti
---------------------------------------

Problemi che potrebbero verificarsi
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Gestione dell'assenza di effetto nell'aggiornamento del codice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Dopo aver riscritto il codice e riavviato il progetto, se si nota che il progetto esegue ancora il vecchio codice, considerare i seguenti passaggi:

Rigenerare il progetto: Seguire le istruzioni del passo 3.2 per rigenerare o aggiornare la configurazione e i file del progetto.

Codici di errore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Quando il valore restituito è 0, indica un funzionamento normale. Se il valore restituito è diverso da 0, consultare la tabella di riferimento dei codici di errore.