Riproduzione Traiettoria Robot
==================================

.. toctree::
    :maxdepth: 5

Impostazione Parametri Registrazione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDParam(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Descrizione", "Imposta i parametri di registrazione della traiettoria"
    "Parametri Obbligatori", "- ``name``：Nome traiettoria；
    - ``period_ms``：Periodo di campionamento, valore fisso, 2ms o 4ms o 8ms;"
    "Parametri Predefiniti", "- ``type``：Tipo dati, 1-posizione giunto；
    - ``di_choose``：Selezione DI, bit0~bit7 corrispondono a DI0~DI7 del pannello di controllo, bit8~bit9 corrispondono a DI0~DI1 terminale, 0-non selezionare, 1-selezionare, default 0;
    - ``do_choose``：Selezione DO, bit0~bit7 corrispondono a DO0~DO7 del pannello di controllo, bit8~bit9 corrispondono a DO0~DO1 terminale, 0-non selezionare, 1-selezionare, default 0"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Inizio Registrazione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDStart(name, period_ms, type=1,di_choose=0, do_choose=0)``"
    "Descrizione", "Inizia la registrazione della traiettoria"
    "Parametri Obbligatori", "- ``name``：Nome traiettoria；
    - ``period_ms``：Periodo di campionamento, valore fisso, 2ms o 4ms o 8ms；"
    "Parametri Predefiniti", "- ``type``：Tipo dati, 1-posizione giunto, default 1;
    - ``di_choose``：Selezione DI, bit0~bit7 corrispondono a DI0~DI7 del pannello di controllo, bit8~bit9 corrispondono a DI0~DI1 terminale, 0-non selezionare, 1-selezionare, default 0;
    - ``do_choose``：Selezione DO, bit0~bit7 corrispondono a DO0~DO7 del pannello di controllo, bit8~bit9 corrispondono a DO0~DO1 terminale, 0-non selezionare, 1-selezionare, default 0"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Arresto Registrazione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWebTPDStop()``"
    "Descrizione", "Arresta la registrazione della traiettoria"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Eliminazione Registrazione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTPDDelete(name)``"
    "Descrizione", "Elimina la registrazione della traiettoria"
    "Parametri Obbligatori", "- ``name``: Nome traiettoria"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Esempio Codice
+++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con controller robot, restituisce oggetto robot se connesso
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    robot.SetTPDParam(name, period_ms)
    robot.Mode(1)
    time.sleep(1)
    robot.DragTeachSwitch(1)
    robot.SetTPDStart(name, period_ms)
    print("SetTPDStart")
    time.sleep(10)
    robot.SetWebTPDStop()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Precaricamento Traiettoria
+++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTPD(name)``"
    "Descrizione", "Precaricamento traiettoria"
    "Parametri Obbligatori", "- ``name``: Nome traiettoria"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Riproduzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTPD(name,blend,ovl)``"
    "Descrizione", "Riproduzione traiettoria"
    "Parametri Obbligatori", "- ``name``: Nome traiettoria
    - ``blend``：Smussamento, 0-non smussato, 1-smussato
    - ``ovl``：Fattore di scala velocità, intervallo [0~100]"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Ottenere Posa Iniziale Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTPDStartPose(name)``"
    "Descrizione", "Ottiene la posa iniziale della traiettoria"
    "Parametri Obbligatori", "- ``name``: Nome traiettoria"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "- Codice errore Successo-0 Fallimento- errore
    - ``desc_pose=[x,y,z,rx,ry,rz]``：Posa iniziale traiettoria"

Esempio Codice Registrazione Traiettoria TPD Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con controller robot, restituisce oggetto robot se connesso
    robot = Robot.RPC('192.168.58.2')
    type = 1
    name = "tpd2025"
    period_ms = 4
    di_choose = 0
    do_choose = 0
    ovl = 100.0
    blend = 0
    rtn = robot.LoadTPD(name)
    print(f"LoadTPD rtn is: {rtn}")
    error,start_pose = robot.GetTPDStartPose(name)
    print(f"start pose, xyz is: {start_pose[0]},{start_pose[1]},{start_pose[2]}. "
          f"rpy is: {start_pose[3]},{start_pose[4]},{start_pose[5]}")
    robot.MoveCart(start_pose, 0, 0, 100, 100)
    time.sleep(1)
    rtn = robot.MoveTPD(name, blend, ovl)
    print(f"MoveTPD rtn is: {rtn}")
    time.sleep(5)
    robot.SetTPDDelete(name)
    robot.CloseRPC()

Pre-elaborazione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTrajectoryJ(name,ovl,opt=1)``"
    "Descrizione", "Pre-elaborazione traiettoria"
    "Parametri Obbligatori", "- ``name``: Nome traiettoria, es: /fruser/traj/trajHelix_aima_1.txt;
    - ``ovl``：Percentuale scala velocità, intervallo [0~100];"
    "Parametri Predefiniti", "- ``opt``：1-punto di controllo, default 1"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Riproduzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTrajectoryJ()``"
    "Descrizione", "Riproduzione traiettoria"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Ottenere Posa Iniziale Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTrajectoryStartPose(name)``"
    "Descrizione", "Ottiene la posa iniziale della traiettoria"
    "Parametri Obbligatori", "``name``: Nome traiettoria"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "- Codice errore Successo-0 Fallimento- errore
    - ``desc_pose=[x,y,z,rx,ry,rz]``：Posa iniziale traiettoria"

Ottenere Numero Punti Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTrajectoryPointNum()``"
    "Descrizione", "Ottiene il numero dei punti della traiettoria"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "- Codice errore Successo-0 Fallimento- errore
    - ``pnum``：Numero punti traiettoria"

Impostazione Velocità durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJSpeed(ovl)``"
    "Descrizione", "Imposta la velocità durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``ovl``: Percentuale scala velocità, intervallo [0~100]"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Forza e Coppia durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceTorque(ft)``"
    "Descrizione", "Imposta forza e coppia durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``ft=[fx,fy,fz,tx,ty,tz]``: Unità N e Nm"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Forza lungo direzione X durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFx(fx)``"
    "Descrizione", "Imposta la forza lungo la direzione X durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``fx``: Forza lungo direzione X, unità N"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Forza lungo direzione Y durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFy(fy)``"
    "Descrizione", "Imposta la forza lungo la direzione Y durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``fy``: Forza lungo direzione Y, unità N"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Forza lungo direzione Z durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJForceFz(fz)``"
    "Descrizione", "Imposta la forza lungo la direzione Z durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``fz``: Forza lungo direzione Z, unità N"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Coppia attorno asse X durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTx(tx)``"
    "Descrizione", "Imposta la coppia attorno all'asse X durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``tx``: Coppia attorno asse X, unità Nm"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Coppia attorno asse Y durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTy(ty)``"
    "Descrizione", "Imposta la coppia attorno all'asse Y durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "``ty``: Coppia attorno asse Y, unità Nm"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Impostazione Coppia attorno asse Z durante Esecuzione Traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTrajectoryJTorqueTz(tz)``"
    "Descrizione", "Imposta la coppia attorno all'asse Z durante l'esecuzione della traiettoria"
    "Parametri Obbligatori", "- ``tz``: Coppia attorno asse Z, unità Nm"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Caricamento File Traiettoria J
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TrajectoryJUpLoad(filePath)``"
    "Descrizione", "Carica il file traiettoria J"
    "Parametri Obbligatori", "- ``filePath``: Percorso completo del file traiettoria da caricare, C://test/testJ.txt"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Eliminazione File Traiettoria J
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TrajectoryJDelete(filePath)``"
    "Descrizione", "Elimina il file traiettoria J"
    "Parametri Obbligatori", "- ``filePath``: Percorso completo del file traiettoria da eliminare, C://test/testJ.txt"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Esempio Codice Riproduzione File Traiettoria J Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con controller robot, restituisce oggetto robot se connesso
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "/fruser/traj/traj.txt"
    rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1)
    print(f"LoadTrajectoryJ {traj_file_name}, rtn is: {rtn}")
    rtn,traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos:{traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},"
          f"{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 50, 100, 100)
    rtn,traj_num = robot.GetTrajectoryPointNum()
    print(f"GetTrajectoryStartPose rtn is: {rtn}, traj num is: {traj_num}")
    rtn = robot.SetTrajectoryJSpeed(50.0)
    print(f"SetTrajectoryJSpeed is: {rtn}")
    traj_force = [0.0,0.0,0.0,0.0,0.0,0.0]
    traj_force[0] = 10  # fx = 10
    rtn = robot.SetTrajectoryJForceTorque(traj_force)
    print(f"SetTrajectoryJForceTorque rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFx(10.0)
    print(f"SetTrajectoryJForceFx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFy(0.0)
    print(f"SetTrajectoryJForceFy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJForceFz(0.0)
    print(f"SetTrajectoryJForceFz rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTx(10.0)
    print(f"SetTrajectoryJTorqueTx rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTy(10.0)
    print(f"SetTrajectoryJTorqueTy rtn is: {rtn}")
    rtn = robot.SetTrajectoryJTorqueTz(10.0)
    print(f"SetTrajectoryJTorqueTz rtn is: {rtn}")
    rtn = robot.MoveTrajectoryJ()
    print(f"MoveTrajectoryJ rtn is: {rtn}")
    robot.CloseRPC()

Pre-elaborazione Traiettoria (Anticipazione Traiettoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadTrajectoryLA(name, mode, errorLim, type, precision, vamx, amax, jmax, flag)``"
    "Descrizione", "Pre-elaborazione traiettoria (Anticipazione traiettoria)"
    "Parametri Obbligatori", "- ``name``: Nome file traiettoria
    - ``mode``：Modalità campionamento, 0-non campionare; 1-campionamento a intervalli dati uguali; 2-campionamento con limitazione errore
    - ``errorLim``: Limite errore, effettivo con interpolazione lineare
    - ``type``: Metodo smussamento, 0-smussamento Bezier
    - ``precision``: Precisione smussamento, effettiva con smussamento Bezier
    - ``vamx``: Velocità massima impostata, mm/s
    - ``amax``: Accelerazione massima impostata, mm/s2
    - ``jmax``: Massima derivate accelerazione impostata, mm/s3
    - ``flag``: Interruttore attivazione anticipazione velocità costante 0-non attivare; 1-attivare"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Riproduzione Traiettoria (Anticipazione Traiettoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveTrajectoryLA()``"
    "Descrizione", "Riproduzione traiettoria (Anticipazione traiettoria)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Restituito", "Codice errore Successo-0 Fallimento- errore"

Esempio Codice Riproduzione Traiettoria (Anticipazione Traiettoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con controller robot, restituisce oggetto robot se connesso
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt")
    print(f"Upload TrajectoryJ A {rtn}")
    traj_file_name = "/fruser/traj/traj.txt"
    rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 50, 200, 1000, 0)
    print(f"LoadTrajectoryLA {traj_file_name}, rtn is: {rtn}")
    rtn, traj_start_pose = robot.GetTrajectoryStartPose(traj_file_name)
    print(f"GetTrajectoryStartPose is: {rtn}")
    print(f"desc_pos: {traj_start_pose[0]},{traj_start_pose[1]},{traj_start_pose[2]},{traj_start_pose[3]},{traj_start_pose[4]},{traj_start_pose[5]}")
    time.sleep(1)
    robot.SetSpeed(50)
    robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100)
    rtn = robot.MoveTrajectoryLA()
    print(f"MoveTrajectoryLA rtn is: {rtn}")
    robot.CloseRPC()