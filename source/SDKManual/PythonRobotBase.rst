Fondamenti Robot
=======================

.. toctree:: 
    :maxdepth: 5

Istanziazione Robot
++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RPC(ip)``"
    "Descrizione", "Istanzia un oggetto robot"
    "Parametri Obbligatori", "- ``ip``：Indirizzo IP del robot, IP predefinito di fabbrica è '192.168.58.2'"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Successo: ritorna un oggetto robot
    - Fallimento: l'oggetto creato viene distrutto"

Chiudere Connessione RPC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CloseRPC()``"
    "Descrizione", "Chiude connessione RPC"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Nessuno"

Interrogare Numero Versione SDK
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSDKVersion()``"
    "Descrizione", "Interroga numero versione SDK"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento-errcode
    - ``sdk``：Numero versione SDK, numero versione controller"

Ottenere IP Controller
+++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetControllerIP()``"
    "Descrizione", "Interroga IP controller"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``ip``：IP controller"

Controllare Entrata/Uscita Modalità Insegnamento Trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DragTeachSwitch(state)``"
    "Descrizione", "Controlla entrata/uscita modalità insegnamento trascinamento"
    "Parametri Obbligatori", "- ``state``：1-entra modalità insegnamento trascinamento, 0-esce modalità insegnamento trascinamento"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Interrogare Se Robot è in Modalità Trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``IsInDragTeach()``"
    "Descrizione", "Interroga se robot è in modalità insegnamento trascinamento"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``state``：0-non in modalità insegnamento trascinamento, 1-in modalità insegnamento trascinamento"

Controllare Abilitazione/Disabilitazione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RobotEnable(state)``"
    "Descrizione", "Controlla abilitazione/disabilitazione robot"
    "Parametri Obbligatori", "- ``state``：1-abilitato, 0-disabilitato"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode "

Controllare Cambio Modalità Manuale/Automatica Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``Mode(state)``"
    "Descrizione", "Controlla cambio modalità manuale/automatica robot"
    "Parametri Obbligatori", "- ``state``：0-modalità automatica, 1-modalità manuale"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Spegnere Sistema Operativo Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ShutDownRobotOS()``"
    "Descrizione", "Spegne sistema operativo robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Inizializzare Parametri Log
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoggerInit(output_model=1, file_path="", file_num=5)``"
    "Descrizione", "Inizializza parametri log"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``output_model``：Modalità output, 0-output diretto; 1-output bufferizzato; 2-output asincrono, default 1
    - ``file_path``：Percorso salvataggio file + nome, nome deve essere formato xxx.log, es. /home/fr/linux/fairino.log. Percorso predefinito programma esecuzione, nome predefinito: fairino_anno+mese+data.log (es: fairino_2024_03_13.log);
    - ``file_num``：Numero file archiviazione rolling, 1~20 file, valore predefinito 5. Singolo file limite superiore 50M;"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Livello Filtro Log
+++++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoggerLevel(lvl=1)``"
    "Descrizione", "Imposta livello filtro log"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``lvl``：Valore livello filtro, valore più piccolo produce meno log output, 1-error, 2-warning, 3-inform, 4-debug, valore predefinito 1"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Controllo Fondamentale Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    error,version = robot.GetSDKVersion()
    print(f"SDK version: {version}")
    error,ip = robot.GetControllerIP()
    print(f"controller ip: {ip}")
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(state=1)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.DragTeachSwitch(state=0)
    time.sleep(1)
    error,state = robot.IsInDragTeach()
    print(f"drag state: {state}")
    time.sleep(3)
    robot.RobotEnable(0)
    time.sleep(3)
    robot.RobotEnable(1)
    robot.Mode(0)
    time.sleep(1)
    robot.Mode(1)
    robot.CloseRPC()

Ottenere Versione Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSoftwareVersion()``"
    "Descrizione", "Ottiene versione software robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``robotModel``：Modello robot
    - ``webVersion``：Versione web
    - ``controllerVersion``：Versione controller"

Ottenere Informazioni Versione Hardware Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlaveHardVersion()``"
    "Descrizione", "Ottiene informazioni versione hardware robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``ctrlBoxBoardVersion``：Versione box controllo
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Ottenere Informazioni Versione Firmware Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlaveFirmVersion()``"
    "Descrizione", "Ottiene informazioni versione firmware robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``ctrlBoxBoardVersion``：Versione box controllo
    - ``driver1Version``
    - ``driver2Version``
    - ``driver3Version``
    - ``driver4Version``
    - ``driver5Version``
    - ``driver6Version``
    - ``endBoardVersion``"

Esempio Codice Versione Software/Firmware Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    rtn,robotModel, webversion, controllerVersion = robot.GetSoftwareVersion()
    print(f"Getsoftwareversion rtn is: {rtn}")
    print(f"robotmodel is: {robotModel}, webversion is: {webversion}, controllerVersion is: {controllerVersion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetHardwareversion()
    print(f"GetHardwareversion rtn is: {rtn}")
    print(f"GetHardwareversion get hardware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    rtn,ctrlBoxBoardversion, driver1version, driver2version,driver3version, driver4version, driver5version,driver6version, endBoardversion = robot.GetFirmwareVersion()
    print(f"GetFirmwareversion rtn is: {rtn}")
    print(f"GetFirmwareversion get firmware version is: {ctrlBoxBoardversion}, {driver1version}, {driver2version}, "
          f"{driver3version}, {driver4version}, {driver5version}, {driver6version}, {endBoardversion}\n")
    robot.CloseRPC()