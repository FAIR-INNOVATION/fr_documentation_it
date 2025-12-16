Appendice
=================

.. toctree::
    :maxdepth: 5

Download del Codice Sorgente
------------------------------------------------

Nel sito della documentazione di Faoro (https://fairino-doc-it.readthedocs.io/latest/), trova il modulo "Download materiali", clicca sul pulsante "CPP SDK", nella pagina a destra clicca su "FAIRINO CPP SDK", attendi che il download si completi nel browser.

.. image:: image/001.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1‑1 Download del codice sorgente C++ SDK

Dopo aver decompresso l'archivio, la struttura della directory dei file scaricati è come mostrato in figura, dove:

- windows: file di intestazione e librerie (.lib e .dll) compilati in ambienti come VS2015~VS2019, contenenti le modalità Debug e Release;
- linux: file di intestazione e librerie (.so) per ambienti comuni come gcc, rk3399, rk3568;
- libfairino: codice sorgente del C++ SDK;

.. image:: image/002.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1‑2 Directory del codice sorgente C++ SDK

Compilazione del Codice Sorgente su Piattaforma Windows
--------------------------------------------------------------
① Apri Visual Studio, clicca su "Continua senza codice (W)" in basso a destra;

.. image:: image/003.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2‑1 Aprire Visual Studio

② Clicca in sequenza su "File", "Apri", "CMake (M)", si aprirà una finestra di selezione file, scegli il file "\\libfairino\\CMakeLists.txt" dal codice sorgente C++ SDK scaricato. Visual Studio caricherà automaticamente il progetto in base alle definizioni nel file CMakeLists.txt.

.. image:: image/004.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2‑2 Aprire il progetto CMake

③ In base alle esigenze, scegli la piattaforma di compilazione "x64-Debug" o "x64-Release", ecc., e seleziona l'elemento di avvio come "fairino.dll".

.. image:: image/005.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2‑3 Selezionare l'elemento di avvio

④ Nella barra dei menu, clicca in sequenza su "Compila", "Ricompila fairino.dll", il compilatore inizierà automaticamente la compilazione.

.. image:: image/006.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2‑4 Generare fairino.dll

⑤ Nella directory del progetto a destra, trova la cartella "build", e al suo interno i file fairino.dll e fairino.lib ottenuti dalla compilazione.

.. image:: image/007.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2‑5 Trovare fairino.lib e fairino.dll

⑥ Quando utilizzi il C++ SDK del robot collaborativo, prima trova i file di intestazione compilati dell'SDK del robot nella directory del progetto a destra: /libfairino/src/include/Robot-CN/, copia i tre file di intestazione "robot.h", "robot_error.h" e "robot_type.h" da questa cartella nella directory del progetto, aggiungi fairino.lib alle librerie di collegamento, e infine posiziona fairino.dll nella directory del file eseguibile per poterlo utilizzare.

Compilazione del Codice Sorgente su Piattaforma Linux
-------------------------------------------------------------------

Prima della compilazione del codice sorgente su Linux, assicurati che nel sistema siano installati il compilatore gcc, g++ e il sistema di build cmake (versione 3.10 o superiore).

Nella directory del codice sorgente C++ \\libfairino\\linuxBuild\\, lo script "buildGcc.sh" contiene istruzioni come "cmake ..", "make", copiare i file di intestazione e le librerie finali nella cartella \\linuxBuild\\, ecc. Eseguendo questo script si completerà la compilazione del codice sorgente del C++ SDK.

① Apri un terminale, entra nella directory \\libfairino\\linuxBuild\\, inserisci il comando: "sh buildGcc.sh" e premi invio, l'SDK inizierà a compilare, attendi il completamento della compilazione.

.. image:: image/008.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3‑1 Inserire il comando dello script di compilazione

② Dopo il completamento della compilazione, entra di nuovo nella directory \\libfairino\\linuxBuild\\, trova la cartella \\include\\ e la cartella \\lib\\, che sono rispettivamente le directory dei file di intestazione e delle librerie necessarie.

.. image:: image/009.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3‑2 Risultato della compilazione