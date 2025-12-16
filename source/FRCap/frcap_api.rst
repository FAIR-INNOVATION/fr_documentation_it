Spiegazione API
=========================

.. toctree::
   :maxdepth: 6

Istruzioni Act
--------------

Tutte le seguenti istruzioni act utilizzano POST, l'URL è /action/act.

Salvare Punti di Insegnamento
++++++++++++++++++++++++++++++

Nome istruzione: save_point.

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param  string name nome del punto di insegnamento registrato
    * @param  string speed velocità
    * @param  string elbow_speed velocità del gomito
    * @param  string acc accelerazione
    * @param  string elbow_acc accelerazione del gomito
    * @param  string toolnum numero utensile
    * @param  string workpiecenum numero pezzo in lavorazione
    */

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: "save_point",
        data:{
            name: "point1",
            speed: "100",
            elbow_speed: "100",
            acc: "100",
            elbow_acc: "100",
            toolnum: "1",
            workpiecenum: "1"
        }
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200 "success"
    * @return status:404 "fail"
    */

Istruzioni Sta
--------------

Tutte le seguenti istruzioni sta utilizzano POST, l'URL è /action/sta.

Ottenere Dati di Stato del Robot
+++++++++++++++++++++++++++++++++

Nome istruzione: basic.

Parametri istruzione: Nessuno.

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: "basic",
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200
    * @param  object joints posizione giunti
    * @param  object tcp posa cartesiana
    * @param  array exAxisPos posizione assi esterni
    * @return status:404 "fail"
    */
    {
        joints: {
            j1: "90",
            j2: "90",
            j3: "90",
            j4: "90",
            j5: "90",
            j6: "90",
        },
        tcp: {
            x: "100",
            y: "100",
            z: "100",
            rx: "90",
            ry: "90",
            rz: "90",
        },
        exAxisPos: [0,0,0,0]
    }

Istruzioni Get
--------------

Tutte le seguenti istruzioni get utilizzano POST, l'URL è /action/get.

Ottenere Punti di Insegnamento
+++++++++++++++++++++++++++++++

Nome istruzione: get_points().

Parametri istruzione: Nessuno.

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_points"
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200 "success"
    * @param  ${point_name}: object informazioni correlate al punto di insegnamento
    * @return status:404 "fail"
    */

Esempio feedback istruzione:

.. code-block:: c++
    :linenos:

    {
        "localpoint1": {
            "name":"localpoint1",
            "elbow_speed":"1",
            "elbow_acc":"1",
            "x": "1",
            "y": "1",
            "z": "1",
            "rx": "1",
            "ry": "1",
            "rz": "1",
            "j1": "1",
            "j2": "1",
            "j3": "1",
            "j4": "1",
            "j5": "1",
            "j6": "1",
            "toolnum": "1",
            "workpiecenum": "1",
            "speed": "1",
            "acc": "1",
            "E1": "1",
            "E2": "1",
            "E3": "1",
            "E4": "1"
        }
    }

Ottenere Configurazione di Sistema
+++++++++++++++++++++++++++++++++++

Nome istruzione: get_syscfg().

Parametri istruzione: Nessuno.

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: "get_syscfg"
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200 "success"
    * @param  string log_count numero massimo di giorni di log registrati
    * @param  string language pacchetto lingua attualmente in uso
    * @param  string lifespan tempo di timeout
    * @return status:404 "fail"
    */

Esempio feedback istruzione:

.. code-block:: c++
    :linenos:

    {
        log_count:"10",
        language:"zh",
        lifespan:"1800"
    }

Istruzioni Set
--------------

Tutte le seguenti istruzioni set utilizzano POST, l'URL è /action/set.

Inviare Istruzioni Variabili di Sistema
+++++++++++++++++++++++++++++++++++++++

Nome istruzione: 511.

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param int index numero variabile di sistema: 1-20
    * @param int value valore variabile di sistema
    */

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: 511,
        data:{
            content:"SetSysVarValue(2,1)"
        }
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200 1: rappresenta successo, 0: rappresenta fallimento
    * @return status:404 "fail"
    */

Esempio feedback istruzione:

.. code-block:: c++
    :linenos:

    1

Ottenere Istruzioni Variabili di Sistema
+++++++++++++++++++++++++++++++++++++++++

Nome istruzione: 512.

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param int index numero variabile di sistema: 1-20
    */

Esempio istruzione:

.. code-block:: c++
    :linenos:

    {
        cmd: 512,
        data:{
            content:"GetSysVarValue(2)"
        }
    }

Feedback istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return status:200
    * @param int value valore variabile di sistema
    * @return status:404 "fail"
    */

Esempio feedback istruzione:

.. code-block:: c++
    :linenos:

    1

Istruzioni better-sqlite3
-------------------------

Interrogare Prima Riga di Record nel Database
+++++++++++++++++++++++++++++++++++++++++++++

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nome database (include percorso assoluto)
    * @param string sql istruzione sql
    * @return string result prima riga di record interrogata
    */

Contenuto istruzione:

.. code-block:: c++
    :linenos:

    queryget(string db_name, string sql);

Interrogare Tutti i Record nel Database
++++++++++++++++++++++++++++++++++++++++

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nome database (include percorso assoluto)
    * @param string sql istruzione sql
    * @return string result tutti i record interrogati
    */

Contenuto istruzione:

.. code-block:: c++
    :linenos:

    queryall(string db_name, string sql);

Eseguire Istruzioni Database
++++++++++++++++++++++++++++

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param string db_name nome database (include percorso assoluto)
    * @param string sql istruzione sql
    * @param object obj parametri richiesti per esecuzione istruzione sql
    * @return \
    */

Contenuto istruzione:

.. code-block:: c++
    :linenos:

    exec(string db_name, string sql, object obj);

Istruzioni Socket
-----------------

Socket Send
++++++++++++++++++

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @param string send_content contenuto inviato istruzione comunicazione socket
    * @return \
    */

Contenuto istruzione:

.. code-block:: c++
    :linenos:

    socket_cmd.send(string send_content);//8065
    socket_file.send(string send_content);//8067

Socket Recv
+++++++++++

Parametri istruzione:

.. code-block:: c++
    :linenos:

    /**
    * @return string recv_content contenuto risposta istruzione comunicazione socket
    */

Contenuto istruzione:

.. code-block:: c++
    :linenos:

    socket_cmd.recv();//8065
    socket_file.recv();//8067

Istruzioni Operazioni File
--------------------------

Scrivere Contenuto File
+++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename percorso file
    * @param string content contenuto da scrivere
    * @return true/false
    */

    write(filename, content);

Leggere Contenuto File
++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename percorso file
    * @return String contenuto file
    */

    read(filename);

Modificare Permessi File
++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String filename percorso file
    * @param Number mode modalità permessi (es. 0644)
    * @return true/false
    */

    chmod(filename, mode);

Leggere Contenuto Directory, Include Sottodirectory
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @param String path percorso file
    * @return Array array nomi file
    */

    readdir(path);

Istruzioni Compressione/Decompressione
--------------------------------------

.. note::
    Distinguere versioni LA e QX:

    Importazione modulo LA: var execSync = require('child_process').execSync;

    Importazione modulo QX: var tar_utils = require('/usr/local/etc/node/sys/tools/tar_utils');

Creare File Compresso tar.gz
+++++++++++++++++++++++++++++

Esempio creazione file compresso tar.gz (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zcvf ' + FILENAME + '-C ' + DIR;
    execSync(cmd);

Descrizione istruzione creazione file compresso tar.gz (QX):

.. code-block:: c++
    :linenos:

    /**
    * @param {Array|String} sourcePaths array percorsi file/directory sorgente o percorso singolo
    * @param String targetFile percorso file compresso target
    * @param Function callback funzione callback, parametro (error)
    * @param String basePath percorso base, default '/'
    * @return \
    */

    createTarGz(sourcePaths, targetFile, callback, basePath);

Decomprimere File tar.gz
++++++++++++++++++++++++

Esempio decompressione file tar.gz (LA):

.. code-block:: javascript
    :linenos:

    var cmd = 'cd / && tar -zxvf ' + FILENAME;
    execSync(cmd);

Descrizione istruzione decompressione file tar.gz (QX):

.. code-block:: c++
    :linenos:

    /**
    * @param String sourceFile percorso file compresso sorgente
    * @param String targetDir directory target decompressione
    * @param Function callback funzione callback, parametro (error)
    * @return \
    */
    extractTarGz(sourceFile, targetDir, callback);