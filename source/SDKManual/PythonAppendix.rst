Appendice
=================

.. toctree:: 
    :maxdepth: 5

Download Codice Sorgente
------------------------------------------------

Nel sito di documentazione di FAIR (https://fairino-doc-it.readthedocs.io/latest/), trovare il modulo "Download Materiali", fare clic sul pulsante "Python SDK", quindi nella pagina a destra fare clic su "FAIRINO Python SDK" e attendere il completamento del download del browser.

.. image:: image/025.png
   :width: 6in
   :align: center

.. centered:: Figura 16.1‑1 Download Codice Sorgente Python SDK

Scaricare ed estrarre il Python SDK. La struttura della directory del progetto è mostrata nella figura seguente. La cartella `windows` contiene il Python SDK per sistemi Windows; la cartella `linux` contiene il Python SDK per sistemi Linux.

.. image:: image/026.png
   :width: 6in
   :align: center

.. centered:: Figura 16.1‑2 Esempio Struttura File Python SDK

Prendendo come esempio il sistema Windows, aprire la cartella `windows`. La directory è mostrata nella figura seguente. La cartella `example` contiene esempi di test, la cartella `fairino` contiene il codice sorgente del Python SDK e `libfairino` contiene i file di libreria.

.. image:: image/027.png
   :width: 6in
   :align: center

.. centered:: Figura 16.1‑3 Esempio Struttura File Python SDK per Sistema Windows

Aprire la cartella `windows` utilizzando il software Pycharm. La struttura è mostrata nella figura seguente.

.. image:: image/028.png
   :width: 4in
   :align: center

.. centered:: Figura 16.1‑4 Esempio Struttura File Progetto in Pycharm
 
Compilazione Codice Sorgente
----------------------------------------
La generazione della libreria dinamica Python produce librerie diverse a seconda del tipo di sistema e della versione di Python. Ad esempio, sulla piattaforma Windows il file di libreria generato ha estensione ".pyd", mentre su Linux ha estensione ".so". Inoltre, le librerie dinamiche generate da versioni diverse di Python non possono essere utilizzate in modo intercambiabile. Pertanto, prima di generare la libreria dinamica, è necessario determinare la versione di Python, la piattaforma di utilizzo, ecc. Questo manuale fornisce istruzioni per la compilazione utilizzando Python 3.10, Windows 11 e Ubuntu 22.04.

Compilazione Python SDK su Piattaforma Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Innanzitutto, aprire il file Python SDK scaricato utilizzando Pycharm e aprire il file `setup.py`;

.. image:: image/029.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑1 Apertura File Progetto

Quindi, fare clic nell'angolo in basso a destra per selezionare l'interprete Python. In questo esempio si utilizza Python 3.10;

.. image:: image/030.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑2 Selezione Versione Python
 
Fare clic con il tasto destro sulla cartella `fairino`, selezionare "Apri in", quindi fare clic su "Terminale";

.. image:: image/031.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑3 Apertura Terminale

Nell'interfaccia del terminale, inserire "python setup.py build_ext --inplace" e premere "Invio" per generare la libreria dinamica Python SDK;

.. image:: image/032.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑4 Esecuzione Comando Generazione Libreria Dinamica

Dopo il completamento della generazione della libreria dinamica, nella cartella `fairino` verranno generati `Robot.c` e `Robot.cp310-win_amd64.pyd`. `Robot.c` è il file `Robot.py` convertito in linguaggio C; `Robot.cp310-win_amd64.pyd` è la libreria dinamica Python SDK, dove "cp310" indica la compatibilità con Python 3.10 e "win_amd64" indica la compatibilità con la piattaforma Windows.

.. image:: image/033.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑5 Generazione Libreria Dinamica .pyd
 
Compilazione Python SDK su Piattaforma Linux
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Innanzitutto, verificare la versione di Python. Questo manuale utilizza lo strumento `pyenv` per gestire le versioni di Python nel sistema Linux. Eseguire il comando "pyenv versions" per visualizzare la versione corrente di Python;

.. image:: image/034.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑6 Verifica Versione Python

Quindi, passare alla versione di Python target. Utilizzando Python 3.10 come esempio, eseguire il comando "pyenv global 3.10.3" per passare a Python 3.10;

.. image:: image/035.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑7 Selezione Versione Python

Passare alla directory che contiene il file `Robot.py` eseguendo il comando "cd /home/fairino/fairino-python-sdk-master/fairino-python-sdk-master/linux/fairino" per cambiare directory fino a `Robot.py`.

.. image:: image/036.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑8 Passaggio alla Directory del File Robot.py

Confermare la versione di Python eseguendo il comando "python --version" per visualizzare la versione corrente di Python;

.. image:: image/037.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑9 Verifica Versione Python
 
Nell'interfaccia del terminale, inserire "python setup.py build_ext --inplace" e premere "Invio" per generare la libreria dinamica Python SDK;

.. image:: image/038.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑10 Esecuzione Comando Generazione Libreria Dinamica

Dopo il completamento della generazione della libreria dinamica, nella cartella `fairino` verranno generati `Robot.c` e `Robot.cpython-310-x86_64-linux-gnu.so`. `Robot.c` è il file `Robot.py` convertito in linguaggio C; "Robot.cpython-310-x86_64-linux-gnu.so" è la libreria dinamica Python SDK, dove "python-310" indica la compatibilità con Python 3.10 e "linux-gnu" indica la compatibilità con la piattaforma Linux.

.. image:: image/039.png
   :width: 6in
   :align: center

.. centered:: Figura 16.2‑11 Generazione Libreria Dinamica .so

Note Importanti
----------------------------------

Problemi Potenziali
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Corrispondenza Versioni
++++++++++++++++++++++++++++++
La libreria dinamica Python dipende dall'ambiente di generazione e dalla versione di Python. Pertanto, quando si utilizza una libreria dinamica Python, è necessario verificare che la libreria sia compatibile con il tipo di sistema e che la versione della libreria corrisponda alla versione di Python in uso.

Codici di Errore
++++++++++++++++++++++++++++++
Un valore di ritorno pari a 0 indica un'esecuzione normale. Se il valore di ritorno è diverso da 0, consultare la tabella di riferimento dei codici di errore.