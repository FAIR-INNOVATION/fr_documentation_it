Altre Interfacce
=================

.. toctree:: 
    :maxdepth: 5

Ottenimento Chiave Pubblica SSH
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSSHKeygen()``"
    "Descrizione", "Ottiene la chiave pubblica SSH"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``keygen``：Chiave pubblica"

Invio Comando SCP
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSSHScpCmd(mode, sshname, sship, usr_file_url, robot_file_url)``"
    "Descrizione", "Invio comando SCP"
    "Parametri Obbligatori", "- ``mode``：0-Upload (controller superiore -> controller), 1-Download (controller -> controller superiore)
    - ``sshname``：Nome utente controller superiore
    - ``sship``：Indirizzo IP controller superiore
    - ``usr_file_url``：Percorso file controller superiore
    - ``robot_file_url``：Percorso file controller robot"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Calcolo Valore MD5 File Percorso Specificato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeFileMD5(file_path)``"
    "Descrizione", "Calcola il valore MD5 del file nel percorso specificato"
    "Parametri Obbligatori", "- ``file_path``：Percorso file incluso nome file, percorso predefinito cartella Traj: /fruser/traj/, es. /fruser/traj/trajHelix_aima_1.txt"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``md5``：Valore MD5 file"

Esempio di Codice Comandi SSH, MD5 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    file_path = "/fruser/airlab.lua"
    md5 = ""
    emerg_state = 0
    si0_state = 0
    si1_state = 0
    sdk_com_state = 0
    ssh_keygen = ""
    retval,ssh_keygen = robot.GetSSHKeygen()
    print(f"GetSSHKeygen retval is: {retval}")
    print(f"ssh key is: {ssh_keygen}")
    ssh_name = "fr"
    ssh_ip = "192.168.58.45"
    ssh_route = "/home/fr"
    ssh_robot_url = "/root/robot/dhpara.config"
    retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url)
    print(f"SetSSHScpCmd retval is: {retval}")
    print(f"robot url is: {ssh_robot_url}")
    error, md5 = robot.ComputeFileMD5(file_path)
    print(f"md5 is: {md5}")
    robot.CloseRPC()

Impostazione Periodo Feedback Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStateSamplePeriod(period)``"
    "Descrizione", "Imposta il periodo di feedback porta 20004 robot"
    "Parametri Obbligatori", "- ``period``：Periodo feedback porta 20004 robot (ms)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Ottenimento Periodo Feedback Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotRealtimeStateSamplePeriod()``"
    "Descrizione", "Ottiene il periodo di feedback porta 20004 robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``period``：Periodo feedback porta 20004 robot (ms)"

Esempio di Codice Configurazione Periodo Feedback Stato Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.SetRobotRealtimeStateSamplePeriod(10)
    error,getPeriod = robot.GetRobotRealtimeStateSamplePeriod()
    print(f"period is {getPeriod}")
    time.sleep(1)
    robot.CloseRPC()

Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SoftwareUpgrade(filePath, block)``"
    "Descrizione", "Aggiornamento software robot"
    "Parametri Obbligatori", "- ``filePath``：Percorso completo pacchetto aggiornamento software
    - ``block``：Bloccare fino al completamento aggiornamento true: bloccante; false: non bloccante"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode "

Ottenimento Stato Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSoftwareUpgradeState()``"
    "Descrizione", "Ottiene lo stato di aggiornamento software robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``state``：Stato aggiornamento pacchetto software robot, 0: inattivo o upload pacchetto aggiornamento in corso, 1~100: percentuale completamento aggiornamento, -1: aggiornamento software fallito, -2: verifica fallita, -3: verifica versione fallita, -4: decompressione fallita, -5: aggiornamento configurazione utente fallito, -6: aggiornamento configurazione periferiche fallito, -7: aggiornamento configurazione assi di espansione fallito, -8: aggiornamento configurazione robot fallito, -9: aggiornamento parametri DH fallito"

Esempio di Codice Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    error = robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", False)
    print(f"SoftwareUpgrade error is {error}")
    while True:
        curState = robot.GetSoftwareUpgradeState()
        print(f"upgrade state is {curState}")
        time.sleep(3)
    robot.CloseRPC()

Download Database Tabella Punti
+++++++++++++++++++++++++++++++

.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableDownLoad(point_table_name, save_file_path)``"
    "Descrizione", "Download database tabella punti"
    "Parametri Obbligatori", "- ``point_table_name``：Nome tabella punti da scaricare    pointTable1.db;
    - ``save_file_path``:Percorso di memorizzazione tabella punti scaricata   C://test/;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Upload Database Tabella Punti
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableUpLoad(point_table_file_path)``"
    "Descrizione", "Upload database tabella punti"
    "Parametri Obbligatori", "- ``point_table_file_path``：Percorso completo tabella punti da caricare   C://test/pointTable1.db"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Aggiornamento File Lua Tabella Punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PointTableUpdateLua(point_table_name, lua_file_name)``"
    "Descrizione", "Aggiornamento file Lua tabella punti"
    "Parametri Obbligatori", "- ``point_table_name``：Nome tabella punti da attivare pointTable1.db, quando la tabella punti è vuota, cioè "", indica l'aggiornamento del programma Lua al programma iniziale non applicando la tabella punti
    - ``lua_file_name``: Nome file Lua da aggiornare testPointTable.lua"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Operazioni Tabella Punti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    save_path = "D://zDOWN/"
    point_table_name = "point_table_FR5.db"
    rtn = robot.PointTableDownLoad(point_table_name, save_path)
    print(f"download : {point_table_name} fail: {rtn}")
    upload_path = "D://zDOWN/point_table_FR5.db"
    rtn = robot.PointTableUpLoad(upload_path)
    print(f"retval is: {rtn}")
    point_tablename = "point_table_FR5.db"
    lua_name = "test0610.lua"
    rtn,error = robot.PointTableUpdateLua(point_tablename, lua_name)
    print(f"retval is: {rtn}")
    robot.CloseRPC()

Download Log Controller
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RbLogDownload(savePath)``"
    "Descrizione", "Download log controller"
    "Parametri Obbligatori", "- ``savePath``：Percorso salvataggio file D://zDown/"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Download Tutte le Fonti Dati
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AllDataSourceDownload(savePath)``"
    "Descrizione", "Download tutte le fonti dati"
    "Parametri Obbligatori", "- ``savePath``：Percorso salvataggio file D://zDown/"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Download Pacchetto Backup Dati
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DataPackageDownload(savePath)``"
    "Descrizione", "Download pacchetto backup dati"
    "Parametri Obbligatori", "- ``savePath``：Percorso salvataggio file D://zDown/"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Download Dati Controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.RbLogDownload("D://zDOWN/")
    print(f"RbLogDownload rtn is {rtn}")
    rtn = robot.AllDataSourceDownload("D://zDOWN/")
    print(f"AllDataSourceDownload rtn is {rtn}")
    rtn = robot.DataPackageDownload("D://zDOWN/")
    print(f"DataPackageDownload rtn is {rtn}")
    robot.CloseRPC()

Impostazione Aggiornamento Encoder
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetEncoderUpgrade(path)``"
    "Descrizione", "Imposta l'aggiornamento encoder"
    "Parametri Obbligatori", "- ``path``：Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
    
Impostazione Aggiornamento Firmware Giunti
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetJointFirmwareUpgrade(type, path)``"
    "Descrizione", "Imposta l'aggiornamento firmware giunti"
    "Parametri Obbligatori", "- ``type``：Tipo file aggiornamento; 1-Aggiornamento firmware; 2-Aggiornamento file configurazione slave
    - ``path``：Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Aggiornamento Firmware Pannello di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCtrlFirmwareUpgrade(type, path)``"
    "Descrizione", "Imposta l'aggiornamento firmware pannello di controllo"
    "Parametri Obbligatori", "- ``type``：Tipo file aggiornamento; 1-Aggiornamento firmware; 2-Aggiornamento file configurazione slave
    - ``path``：Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
    
Impostazione Aggiornamento Firmware Estremità
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetEndFirmwareUpgrade(type, path)``"
    "Descrizione", "Imposta l'aggiornamento firmware estremità"
    "Parametri Obbligatori", "- ``type``：Tipo file aggiornamento; 1-Aggiornamento firmware; 2-Aggiornamento file configurazione slave
    - ``path``：Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
       
Aggiornamento File Configurazione Parametri Completi Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointAllParamUpgrade(path)``"
    "Descrizione", "Aggiornamento file configurazione parametri completi giunti"
    "Parametri Obbligatori", "- ``path``：Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Aggiornamento Firmware Slave Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.RobotEnable(0)
    time.sleep(0.2)
    rtn = robot.JointAllParamUpgrade("D://zUP/MT/joint0603/jointallparameters.db")
    print(f"robot JointAllParamUpgrade rtn is {rtn}")
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Cbd_Asix_V2.0.bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/MT/FAIR_Cobot_Axle_Asix_V2.4.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    robot.SetSysServoBootMode()
    time.sleep(0.2)
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/MT/FR_CTRL_PRIMCU_FV201412_MAIN_U4_T01_20250630(MT).bin")
    print(f"robot SetCtrlFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/MT/FR_END_FV2010010_MAIN_U1_T01_20250603.bin")
    print(f"robot SetEndFirmwareUpgrade rtn is {rtn}")
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/MT/FR_SERVO_FV504215_MAIN_U7_T07_20250603.bin")
    print(f"robot SetJointFirmwareUpgrade rtn is {rtn}")
    robot.CloseRPC()
       
Aggiornamento Sistema Operativo Robot (Pannello di Controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``KernelUpgrade(filePath)``"
    "Descrizione", "Aggiornamento sistema operativo robot (pannello di controllo LA)"
    "Parametri Obbligatori", "- ``filePath``：Percorso completo pacchetto aggiornamento sistema operativo"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
       
Ottenimento Risultato Aggiornamento Sistema Operativo Robot (Pannello di Controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetKernelUpgradeResult()``"
    "Descrizione", "Ottiene il risultato dell'aggiornamento sistema operativo robot (pannello di controllo LA)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
       
Generazione Log MCU Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``RobotMCULogCollect()``"
    "Descrizione", "Generazione log MCU robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"