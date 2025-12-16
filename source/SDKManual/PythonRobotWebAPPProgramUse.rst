Utilizzo del Programma Robot WebAPP
====================================

.. toctree::
    :maxdepth: 5

Impostazione Caricamento Automatico Programma di Lavoro Predefinito all'Avvio
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadDefaultProgConfig(flag,program_name)``"
    "Descrizione", "Imposta il caricamento automatico all'avvio del programma di lavoro predefinito"
    "Parametri Richiesti", "- ``flag``：1-Carica automaticamente il programma predefinito all'avvio, 0-Non caricare automaticamente il programma predefinito
    - ``program_name``：Nome e percorso del programma di lavoro, ad es. /fruser/movej.lua, dove /fruser/ è il percorso fisso per QX, /usr/local/etc/controller/lua/ è il percorso fisso per LA"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Caricare il Programma di Lavoro Specificato
++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramLoad(program_name)``"
    "Descrizione", "Carica il programma di lavoro specificato"
    "Parametri Richiesti", "- ``program_name``：Nome e percorso del programma di lavoro, ad es. /fruser/movej.lua, dove /fruser/ è il percorso fisso per QX, /usr/local/etc/controller/lua/ è il percorso fisso per LA"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere il Nome del Programma di Lavoro Attualmente Caricato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLoadedProgram()``"
    "Descrizione", "Ottiene il nome del programma di lavoro attualmente caricato"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento- errcode
    - ``program_name``：Nome del programma di lavoro caricato"

Ottenere il Numero di Riga di Esecuzione del Programma di Lavoro Corrente del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurrentLine()``"
    "Descrizione", "Ottiene il numero di riga di esecuzione del programma di lavoro corrente del robot"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento- errcode
    - ``line_num``：Numero di riga di esecuzione del programma di lavoro corrente del robot"

Eseguire il Programma di Lavoro Attualmente Caricato
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramRun()``"
    "Descrizione", "Esegue il programma di lavoro attualmente caricato"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Mettere in Pausa il Programma di Lavoro Corrente in Esecuzione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramPause()``"
    "Descrizione", "Mette in pausa il programma di lavoro corrente in esecuzione"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Riprendere il Programma di Lavoro Corrente in Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramResume()``"
    "Descrizione", "Riprende il programma di lavoro corrente in pausa"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Terminare il Programma di Lavoro Corrente in Esecuzione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramStop()``"
    "Descrizione", "Termina il programma di lavoro corrente in esecuzione"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere lo Stato di Esecuzione del Programma di Lavoro del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetProgramState()``"
    "Descrizione", "Ottiene lo stato di esecuzione del programma di lavoro del robot"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento- errcode
    - ``state``: Stato di esecuzione del programma di lavoro del robot, 1-Programma fermo o nessun programma in esecuzione, 2-Programma in esecuzione, 3-Programma in pausa"

Esempio di Codice per Operazioni sui Programmi LUA del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce una connessione con il controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    program_name = "/fruser/test0610.lua"
    loaded_name = ""
    state = 0
    line = 0
    robot.Mode(0)
    robot.LoadDefaultProgConfig(0, program_name)
    robot.ProgramLoad(program_name)
    robot.ProgramRun()
    time.sleep(1)
    robot.ProgramPause()
    error,state = robot.GetProgramState()
    print(f"program state:{state}")
    error,line = robot.GetCurrentLine()
    print(f"current line:{line}")
    error,loaded_name = robot.GetLoadedProgram()
    print(f"program name:{loaded_name}")
    time.sleep(1)
    robot.ProgramResume()
    time.sleep(1)
    robot.ProgramStop()
    time.sleep(1)
    robot.CloseRPC()

Scaricare File Lua
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LuaDownLoad(fileName, savePath)``"
    "Descrizione", "Scarica un file Lua"
    "Parametri Richiesti", "- ``fileName``：Nome del file Lua da scaricare, es. “test.lua”
    - ``savePath``：Percorso locale per salvare il file, es. “D://Down/”"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Eliminare File Lua
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LuaDelete(fileName)``"
    "Descrizione", "Elimina un file Lua"
    "Parametri Richiesti", "- ``fileName``：Nome del file Lua da eliminare, es. “test.lua”"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere i Nomi di Tutti i File Lua Correnti
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLuaList()``"
    "Descrizione", "Ottiene i nomi di tutti i file Lua correnti"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento- errcode
    - ``lua_num``：Numero di file Lua
    - ``luaNames``：Lista dei nomi dei file Lua"

Caricare File Lua
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.2

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LuaUpload(filePath)``"
    "Descrizione", "Carica un file Lua"
    "Parametri Richiesti", "- ``filePath``：Percorso completo del file da caricare, es. D://test/test.lua"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento- errcode
    - errorStr (restituito se il file Lua contiene errori)"

Esempio di Codice per Caricamento/Scaricamento File Lua del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce una connessione con il controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    rtn,lua_num,luaNames = robot.GetLuaList()
    print(f"res is:{rtn}")
    print(f"size is:{lua_num}")
    for name in luaNames:
        print(name)
    rtn = robot.LuaDownLoad("test0610.lua", "D://zDOWN/")
    print(f"LuaDownLoad rtn is:{rtn}")
    rtn = robot.LuaUpload("D://zDOWN/test0610.lua")
    print(f"LuaUpload rtn is:{rtn}")
    rtn = robot.LuaDelete("test0610.lua")
    print(f"LuaDelete rtn is:{rtn}")
    robot.CloseRPC()