Appendice
=========

.. toctree:: 
    :maxdepth: 5

Download Codice Sorgente
------------------------------------------------

Nel sito della documentazione Faro (https://fairino-doc-it.readthedocs.io/latest/), trovare il modulo "Scarica Materiali", cliccare sul pulsante "Java SDK", nella pagina a destra cliccare su "FAIRINOJavaSDK", attendere il completamento del download dal browser.

.. image:: image/019.png
   :width: 6in
   :align: center

.. centered:: Figura 16.1‑1 Download codice sorgente Java SDK

Scompattare l'archivio compresso, la struttura delle cartelle è mostrata in figura, dove:

fairino_Java_SDK_maven: Codice sorgente (.java) e file di libreria (.jar) compilati da compilatore in ambiente sistema Windows;

.. image:: image/020.png
   :width: 4in
   :align: center

.. centered:: Figura 16.1‑2 Struttura directory file Java SDK

Entrare nella cartella fairino_Java_SDK_maven, contiene le directory come mostrato in figura, dove:

- lib: File jar delle dipendenze utilizzate nel codice sorgente;
- src: File del codice sorgente Java SDK;
- target: File di libreria (.jar) generati dal codice sorgente Java SDK;

.. image:: image/021.png
   :width: 6in
   :align: center

.. centered:: Figura 16.1‑3 Directory codice sorgente e file di libreria Java SDK

Compilazione Codice Sorgente su Piattaforma Windows
-------------------------------------------------------------
① Installare e configurare lo strumento di build – Maven

Sito per scaricare e installare Maven: Welcome to Apache Maven – Maven

Dopo installazione e configurazione, come mostrato sotto, digitando `maven --version` nel terminale verranno visualizzate le seguenti informazioni

.. image:: image/022.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑1 Installazione e configurazione Maven

② Aprire il terminale nella directory del codice sorgente Java SDK, digitare `mvn package`, per generare i file di libreria (.jar),

.. image:: image/023.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑2 Compilazione Java SDK in file di libreria
 
③ Nella directory del codice sorgente, trovare la cartella "target", e al suo interno trovare i file fairino-jar-with-dependencies.jar e fairino.jar ottenuti dalla compilazione, come mostrato in figura

.. image:: image/024.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑3 File jar generati

④ Per utilizzare il Java SDK del robot collaborativo, prima in un progetto IDEA, fare clic in sequenza su File->Project Structure->Libraries, aggiungere il file .jar generato nel passaggio precedente. Nel file, utilizzare `import fairino.*;` per utilizzare il file .jar generato.