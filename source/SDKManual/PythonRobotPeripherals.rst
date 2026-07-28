Periferiche del Robot
========================

.. toctree:: 
    :maxdepth: 5

Configurazione Pinza
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetGripperConfig(company,device,softversion=0,bus=0)``"
    "Descrizione", "Configura la pinza"
    "Parametri Obbligatori", "- ``company``：Produttore pinza，1-Robotiq，2-Huilin，3-Tianji，4-Dahuan，5-Zhixing；
    - ``device``：Numero dispositivo，Robotiq(0-2F-85 serie)，Huilin(0-NK serie,1-Z-EFG-100)，Tianji(0-TEG-110)，Dahuan(0-PGI-140)，Zhixing(0-CTPM2F20)"
    "Parametri Predefiniti", "- ``softversion``：Numero versione software，non utilizzato al momento，predefinito 0；
    - ``bus``：Posizione bus terminale montaggio dispositivo，non utilizzato al momento，predefinito 0；"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Ottenimento Configurazione Pinza
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperConfig()``"
    "Descrizione", "Ottiene la configurazione della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``[number,company,device,softversion]``： number，Numero pinza;company，Produttore pinza，1-Robotiq，2-Huilin，3-Tianji，4-Dahuan，5-Zhixing ;device，Numero dispositivo，Robotiq(0-2F-85 serie)，Huilin(0-NK serie,1-Z-EFG-100)，Tianji(0-TEG-110)，Dahuan(0-PGI-140)，Zhixing(0-CTPM2F20);softvesion，Numero versione software，non utilizzato al momento，predefinito 0。"

Attivazione Pinza
++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ActGripper(index,action)``"
    "Descrizione", "Attiva la pinza"
    "Parametri Obbligatori", "- ``index``:Numero pinza；
    - ``action``:0-Ripristino，1-Attivazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Controllo Pinza
++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveGripper(index,pos,vel,force,maxtime,block,type,rotNum,rotVel,rotTorque)``"
    "Descrizione", "Controlla la pinza"
    "Parametri Obbligatori", "- ``index``:Numero pinza；
    - ``pos``:Posizione percentuale，intervallo [0~100]；
    - ``vel``:Velocità percentuale，intervallo [0~100];
    - ``force``:Coppia percentuale，intervallo [0~100]；
    - ``maxtime``:Tempo massimo attesa，intervallo [0~30000]，unità [ms]；
    - ``block``:0-Bloccante，1-Non bloccante；
    - ``type``:Tipo pinza，0-Pinza parallela; 1-Pinza rotante；
    - ``rotNum``:rotNum Numero rotazioni；
    - ``rotVel``:Velocità rotazione percentuale [0-100]；
    - ``rotTorque``:Coppia rotazione percentuale [0-100]。"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Ottenimento Stato Movimento Pinza
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperMotionDone()``"
    "Descrizione", "Ottiene lo stato di movimento della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``[fault,status]``：Stato movimento pinza，fault:0-Nessun errore，1-Con errore；status:0-Movimento non completato，1-Movimento completato"

Ottenimento Stato Attivazione Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperActivateStatus()``"
    "Descrizione", "Ottiene lo stato di attivazione della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``gripper_active``：bit0~bit15 corrisponde a numero pinza 0~15，bit=0 non attivato，bit=1 attivato"

Ottenimento Posizione Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurPosition()``"
    "Descrizione", "Ottiene la posizione della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``position``：Posizione percentuale，intervallo 0~100%"

Ottenimento Velocità Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurSpeed()``"
    "Descrizione", "Ottiene la velocità della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``speed``：Velocità percentuale，intervallo 0~100%"

Ottenimento Corrente Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperCurCurrent()``"
    "Descrizione", "Ottiene la corrente della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``current``：Corrente percentuale，intervallo 0~100%"

Ottenimento Tensione Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperVoltage()``"
    "Descrizione", "Ottiene la tensione della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``voltage``：Tensione, unità 0.1V"

Ottenimento Temperatura Pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperTemp()``"
    "Descrizione", "Ottiene la temperatura della pinza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento1 errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``temp``：Temperatura，unità ℃"

Calcolo Punto Pre-Presa - Visione
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputePrePick(desc_pos, zlength, zangle)``"
    "Descrizione", "Calcola il punto di pre-presa - visione"
    "Parametri Obbligatori", "- ``desc_pos``：Posa cartesiana punto di presa pinza;
    - ``zlength``：Offset asse z;
    - ``zangle``：Offset rotazione attorno asse z"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``pre_pos``：Posa cartesiana punto di pre-presa"

Calcolo Punto Ritiro - Visione
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputePostPick(desc_pos, zlength, zangle)``"
    "Descrizione", "Calcola il punto di ritiro - visione"
    "Parametri Obbligatori", "- ``desc_pos``：Posa cartesiana punto di presa;
    - ``zlength``：Offset asse z;
    - ``zangle``：Offset rotazione attorno asse z"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``post_pos``：Posa cartesiana punto di ritiro"

Esempio di Codice Operazioni Pinza Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    company = 4
    device = 0
    softversion = 0
    bus = 2
    index = 2
    act = 0
    max_time = 30000
    block = 0
    status = 0
    fault = 0
    active_status = 0
    current_pos = 0
    current = 0
    voltage = 0
    temp = 0
    speed = 0
    robot.SetGripperConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.GetGripperConfig()
    print(f"gripper config:{company},{device},{softversion},{bus}")
    robot.ActGripper(index, act)
    time.sleep(1)
    act = 1
    robot.ActGripper(index, act)
    time.sleep(1)
    error = robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    time.sleep(1)
    error = robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{error}")
    error, [fault, status] = robot.GetGripperMotionDone()
    print(f"motion status:{fault},{status}")
    error, [fault, active_status] = robot.GetGripperActivateStatus()
    print(f"gripper active fault is:{fault},status is:{active_status}")
    error, [fault, current_pos] = robot.GetGripperCurPosition()
    print(f"fault is:{fault},current position is:{current_pos}")
    error, [fault, current] = robot.GetGripperCurCurrent()
    print(f"fault is:{fault},current current is:{current}")
    error, [fault, voltage] = robot.GetGripperVoltage()
    print(f"fault is:{fault},current voltage is:{voltage}")
    error, [fault, temp] = robot.GetGripperTemp()
    print(f"fault is:{fault},current temperature is:{temp}")
    error, [fault, speed] = robot.GetGripperCurSpeed()
    print(f"fault is:{fault},current speed is:{speed}")
    retval = 0
    prepick_pose = [0.0]*6
    postpick_pose = [0.0]*6
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval, prepick_pose = robot.ComputePrePick(p1Desc, 10, 0)
    print(f"ComputePrePick retval is:{retval}")
    print(f"xyz is:{prepick_pose[0]},{prepick_pose[1]},{prepick_pose[2]};rpy is:{prepick_pose[3]},{prepick_pose[4]},{prepick_pose[5]}")
    retval, postpick_pose = robot.ComputePostPick(p2Desc, -10, 0)
    print(f"ComputePostPick retval is:{retval}")
    print(f"xyz is:{postpick_pose[0]},{postpick_pose[1]},{postpick_pose[2]};rpy is:{postpick_pose[3]},{postpick_pose[4]},{postpick_pose[5]}")
    robot.CloseRPC()

Ottenimento Numero Rotazioni Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotNum()``"
    "Descrizione", "Ottiene il numero di rotazioni della pinza rotante"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``num``：Numero rotazioni"

Ottenimento Velocità Percentuale Rotazione Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotSpeed()``"
    "Descrizione", "Ottiene la velocità percentuale di rotazione della pinza rotante"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``speed``：Velocità rotazione percentuale"

Ottenimento Coppia Percentuale Rotazione Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetGripperRotTorque()``"
    "Descrizione", "Ottiene la coppia percentuale di rotazione della pinza rotante"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``fault``：0-Nessun errore，1-Con errore
    - ``torque``：Coppia rotazione percentuale"

Esempio di Codice Ottenimento Stato Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    fault = 0
    rotNum = 0.0
    rotSpeed = 0
    rotTorque = 0
    error,fault, rotNum = robot.GetGripperRotNum()
    error,fault, rotSpeed = robot.GetGripperRotSpeed()
    error,fault, rotTorque = robot.GetGripperRotTorque()
    print(f"gripper rot num:{rotNum},gripper rotSpeed:{rotSpeed},gripper rotTorque:{rotTorque}")
    robot.CloseRPC()

Avvio, Arresto Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorStartEnd(status)``"
    "Descrizione", "Avvia o arresta il nastro trasportatore"
    "Parametri Obbligatori", "- ``status``： Stato nastro trasportatore，1-Avvio，0-Arresto"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Registrazione Punto Rilevamento IO
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointIORecord()``"
    "Descrizione", "Registra punto rilevamento IO"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Registrazione Punto A
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointARecord()``"
    "Descrizione", "Registra punto A"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Registrazione Punto di Riferimento
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorRefPointRecord()``"
    "Descrizione", "Registra punto di riferimento"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Registrazione Punto B
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorPointBRecord()``"
    "Descrizione", "Registra punto B"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento1 errcode"

Rilevamento IO Pezzo Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorIODetect(max_t)``"
    "Descrizione", "Rilevamento IO pezzo nastro trasportatore"
    "Parametri Obbligatori", "- ``max_t``： Tempo massimo rilevamento，unità ms"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Posizione Corrente Oggetto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorGetTrackData(mode)``"
    "Descrizione", "Ottiene la posizione corrente dell'oggetto"
    "Parametri Obbligatori", "- ``mode``： 1-Inseguimento presa 2-Inseguimento movimento 3-Inseguimento TPD"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Inizio Inseguimento Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackStart(status)``"
    "Descrizione", "Inizia l'inseguimento del nastro trasportatore"
    "Parametri Obbligatori", "- ``status``： Stato，1-Avvio，0-Arresto"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Fine Inseguimento Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackEnd()``"
    "Descrizione", "Termina l'inseguimento del nastro trasportatore"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Configurazione Parametri Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorSetParam(param, followType, startDis, endDis)``"
    "Descrizione", "Configura i parametri del nastro trasportatore"
    "Parametri Obbligatori", "- ``param``： = [encChannel,resolution,lead,wpAxis,vision,speedRadio] 
                    - ``encChannel``: Canale encoder 1-2
                    - ``resolution``: Risoluzione encoder Numero impulsi per rotazione encoder
                    - ``lead``: Rapporto trasmissione meccanico Distanza movimento nastro per rotazione encoder
                    - ``wpAxis``: Numero sistema coordinate pezzo Seleziona numero sistema coordinate pezzo per funzionalità inseguimento movimento，impostare a 0 per inseguimento presa, inseguimento TPD
                    - ``vision``: Con visione?  0-Senza 1-Con,
                    - ``speedRadio``: Rapporto velocità  Intervallo velocità per inseguimento presa nastro (1-100)  Impostare a 1 per inseguimento movimento, inseguimento TPD"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Compensazione Punto Presa Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorCatchPointComp(cmp)``"
    "Descrizione", "Compensazione punto presa nastro trasportatore"
    "Parametri Obbligatori", "- ``cmp``： Posizione compensazione [x,y,z]"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Movimento Lineare
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorTrackMoveL(name,tool,wobj,vel=20,acc=100,ovl=100,blendR=-1.0)``"
    "Descrizione", "Movimento lineare"
    "Parametri Obbligatori", "- ``name``：cvrCatchPoint o cvrRaisePoint
    - ``tool``: Numero utensile
    - ``wobj``:  Numero pezzo"
    "Parametri Predefiniti", "- ``vel``: Velocità predefinito 20
    - ``acc``: Accelerazione predefinito 100
    - ``ovl``: Fattore scala velocità predefinito 100
    - ``blendR``: [-1.0]-Movimento a posizione (bloccante)，[0~1000]-Raggio smoothing (non bloccante)，unità [mm] predefinito -1.0"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Rilevamento Input Comunicazione Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorComDetect(timeout)``"
    "Descrizione", "Rilevamento input comunicazione nastro trasportatore"
    "Parametri Obbligatori", "- ``timeout``：Tempo attesa timeout ms"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Attivazione Rilevamento Input Comunicazione Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ConveyorComDetectTrigger()``"
    "Descrizione", "Attiva rilevamento input comunicazione nastro trasportatore"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Operazioni Nastro Trasportatore Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    retval = robot.ConveyorStartEnd(1)
    print(f"ConveyorStartEnd retval is:{retval}")
    retval = robot.ConveyorPointIORecord()
    print(f"ConveyorPointIORecord retval is:{retval}")
    retval = robot.ConveyorPointARecord()
    print(f"ConveyorPointARecord retval is:{retval}")
    retval = robot.ConveyorRefPointRecord()
    print(f"ConveyorRefPointRecord retval is:{retval}")
    retval = robot.ConveyorPointBRecord()
    print(f"ConveyorPointBRecord retval is:{retval}")
    retval = robot.ConveyorStartEnd(0)
    print(f"ConveyorStartEnd retval is:{retval}")
    param = [1.0, 10000.0, 200.0, 0.0, 0.0, 20.0]
    retval = robot.ConveyorSetParam(param,0)
    print(f"ConveyorSetParam retval is:{retval}")
    cmp = [0.0, 0.0, 0.0]
    retval = robot.ConveyorCatchPointComp(cmp)
    print(f"ConveyorCatchPointComp retval is:{retval}")
    index = 1
    max_time = 30000
    block = 0
    retval = 0
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    retval = robot.MoveCart(p1Desc, 1, 0, 100.0)
    print(f"MoveCart retval is:{retval}")
    retval = robot.WaitMs(1)
    print(f"WaitMs retval is:{retval}")
    retval = robot.ConveyorIODetect(10000)
    print(f"ConveyorIODetect retval is:{retval}")
    retval = robot.ConveyorGetTrackData(1)
    print(f"ConveyorGetTrackData retval is:{retval}")
    retval = robot.ConveyorTrackStart(1)
    print(f"ConveyorTrackStart retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100)
    print(f"TrackMoveL retval is:{retval}")
    retval = robot.ConveyorTrackEnd()
    print(f"ConveyorTrackEnd retval is:{retval}")
    robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0)
    retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0)
    print(f"MoveGripper retval is:{retval}")
    robot.CloseRPC()

Configurazione dei Parametri di Inseguimento in Posizione per Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStationaryTrackPara(self, trackMode, trackTime, trackDis)``"
    "Descrizione", "Configura i parametri di inseguimento in posizione per nastro trasportatore"
    "Parametri Obbligatori", "
    - ``trackMode``: 0-tempo; 1-distanza; 2-tempo e distanza, una qualsiasi condizione soddisfatta
    - ``trackTime``: Tempo di inseguimento, unità s
    - ``trackDis``: Distanza di inseguimento
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"

Attendi il Completamento del Movimento a Vuoto in Posizione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitStationaryMotionDone(self)``"
    "Descrizione", "Attendi il completamento del movimento a vuoto in posizione"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"

Esempio di Codice per il Movimento di Inseguimento in Posizione su Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5) 
        j1 = [-35.146, -102.684, 120.805, -100.401, -90.295, 150.105]
        d1 = [-121.814, -348.341, 209.978, -173.152, -3.585, -5.446]

        ex = [0.0, 0.0, 0.0, 0.0]
        zeroOff = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        tool = 1
        workpiece = 1

        para = [0, 10000, 200, 0, 0, 10]
    
        rtn = robot.ConveyorSetParam(para= para)
        print(f"ConveyorSetParam rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, desc_pos=d1, tool=tool, user=workpiece,
                    vel=100, acc=100, ovl=100, exaxis_pos=ex,
                    blendT=-1, offset_flag=0, offset_pos=zeroOff)

        print("--- Step 1: SetDO(6,1) ---")
        rtn = robot.SetDO(6, 1, 0, 0)
        print(f"  SetDO(6,1) rtn={rtn}")

        print("--- Step 2: ConveyorTrackStart(2) ---")
        rtn = robot.ConveyorTrackStart(2)
        print(f"  ConveyorTrackStart(2) rtn={rtn}")

        print("--- Step 3: ConveyorIODetect(10000) ---")
        rtn = robot.ConveyorIODetect(10000)
        print(f"  ConveyorIODetect(10000) rtn={rtn}")

        print("--- Step 4: ConveyorGetTrackData(2) ---")
        rtn = robot.ConveyorGetTrackData(2)
        print(f"  ConveyorGetTrackData(2) rtn={rtn}")

        print("--- Step 5: SetStationaryTrackPara(0,5,5) ---")
        rtn = robot.SetStationaryTrackPara(0, 5, 5)
        print(f"  SetStationaryTrackPara(0,5,5) rtn={rtn}")

        print("--- Step 6: MoveStationary() ---")
        rtn = robot.MoveStationary()
        print(f"  MoveStationary() rtn={rtn}")

        rtn = robot.WaitStationaryMotionDone()
        print(f"  WaitStationaryMotionDone() rtn={rtn}")

        print("--- Step 7: ConveyorTrackEnd() ---")
        rtn = robot.ConveyorTrackEnd()
        print(f"  ConveyorTrackEnd() rtn={rtn}")

        print("--- Step 8: SetDO(6,0) ---")
        rtn = robot.SetDO(6, 0, 0, 0)
        print(f"  SetDO(6,0) rtn={rtn}")

        robot.CloseRPC()


    if __name__ == "__main__":
        main()

Configurazione Sensore Termine
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorConfig(idCompany, idDevice, idSoftware, idBus)``"
    "Descrizione", "Configurazione sensore termine"
    "Parametri Obbligatori", "
    - ``idCompany``: Produttore，18-JUNKONG；25-HUIDE
    - ``idDevice``: Tipo，0-JUNKONG/RYR6T.V1.0
    - ``idSoftware``: Versione software，0-J1.0/HuiDe1.0 (non ancora disponibile)
    - ``idBus``: Posizione montaggio，1-Porta termine n.1；2-Porta termine n.2...8-Porta termine n.8 (non ancora disponibile)
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Configurazione Sensore Termine
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorConfigGet()``"
    "Descrizione", "Ottiene la configurazione del sensore termine"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``idCompany``: Produttore，18-JUNKONG；25-HUIDE
    - ``idDevice``: Tipo，0-JUNKONG/RYR6T.V1.0"
        
Attivazione Sensore Termine
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorActivate(actFlag)``"
    "Descrizione", "Attiva sensore termine"
    "Parametri Obbligatori", "``actFlag``： 0-Ripristino；1-Attivazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``coord``: Valori sistema coordinate [x,y,z,rx,ry,rz]"

Scrittura Registro Sensore Termine
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleSensorRegWrite(devAddr, regHAddr, regLAddr, regNum, data1, data2, isNoBlock)``"
    "Descrizione", "Scrittura registro sensore termine"
    "Parametri Obbligatori", "- ``devAddr``：Numero indirizzo dispositivo 0-255
    - ``regHAddr``：Indirizzo registro alto 8 bit
    - ``regLAddr``：Indirizzo registro basso 8 bit
    - ``regNum``：Numero registri 0-255
    - ``data1``：Valore registro scritto 1
    - ``data2``：Valore registro scritto 2
    - ``isNoBlock``：Bloccante? 0-Bloccante; 1-Non bloccante"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Esempio di Codice Sensore Termine
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.AxleSensorConfig(18, 0, 0, 1)
    error, company, type = robot.AxleSensorConfigGet()
    print(f"company is:{company},type is:{type}")
    rtn = robot.AxleSensorActivate(1)
    print(f"AxleSensorActivate rtn is:{rtn}")
    time.sleep(1)
    rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0)
    print(f"AxleSensorRegWrite rtn is:{rtn}")
    robot.CloseRPC()

Ottenimento Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExDevProtocol()``"
    "Descrizione", "Ottiene il protocollo delle periferiche robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode; 
    - ``protocol``: Numero protocollo periferiche robot 4096-Scheda controllo asse espansione；4097-ModbusSlave；4098-ModbusMaster"

Impostazione Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExDevProtocol(protocol)``"
    "Descrizione", "Imposta il protocollo delle periferiche robot"
    "Parametri Obbligatori", "- ``protocol``：Numero protocollo periferiche robot 4096-Scheda controllo asse espansione；4097-ModbusSlave；4098-ModbusMaster"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Impostazione Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    protocol = 4096
    rtn = robot.SetExDevProtocol(protocol)
    print(f"SetExDevProtocol rtn:{rtn}")
    rtn, protocol = robot.GetExDevProtocol()
    print(f"GetExDevProtocol rtn:{rtn},protocol is:{protocol}")
    robot.CloseRPC()

Ottenimento Parametri Comunicazione Termine
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleCommunicationParam()``"
    "Descrizione", "Ottiene i parametri di comunicazione del termine"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``baudRate``：Baud rate: supporta 1-9600，2-14400，3-19200，4-38400，5-56000，6-67600，7-115200，8-128000
    - ``dataBit``：Bit dati: supporta (8,9)，attualmente comunemente 8
    - ``stopBit``：Bit stop:1-1，2-0.5，3-2，4-1.5，attualmente comunemente 1
    - ``verify``：Bit verifica:0-Nessuno，1-Dispari，2-Pari, attualmente comunemente 0
    - ``timeout``：Tempo timeout:1~1000ms，questo valore deve essere impostato in combinazione con le periferiche per un parametro temporale ragionevole
    - ``timeoutTimes``：Numero timeout:1~10，principalmente per ritrasmissione in caso di timeout，riduce eccezioni occasionali e migliora l'esperienza utente
    - ``period``：Intervallo temporale comandi periodici:1~1000ms，utilizzato principalmente per l'intervallo tra ogni invio di comandi periodici"

Impostazione Parametri Comunicazione Termine
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleCommunicationParam(baudRate, dataBit, stopBit, verify, timeout, timeoutTimes, period)``"
    "Descrizione", "Imposta i parametri di comunicazione del termine"
    "Parametri Obbligatori", "- ``baudRate``：Baud rate: supporta 1-9600，2-14400，3-19200，4-38400，5-56000，6-67600，7-115200，8-128000
    - ``dataBit``：Bit dati: supporta (8,9)，attualmente comunemente 8
    - ``stopBit``：Bit stop:1-1，2-0.5，3-2，4-1.5，attualmente comunemente 1
    - ``verify``：Bit verifica:0-Nessuno，1-Dispari，2-Pari, attualmente comunemente 0
    - ``timeout``：Tempo timeout:1~1000ms，questo valore deve essere impostato in combinazione con le periferiche per un parametro temporale ragionevole
    - ``timeoutTimes``：Numero timeout:1~10，principalmente per ritrasmissione in caso di timeout，riduce eccezioni occasionali e migliora l'esperienza utente
    - ``period``：Intervallo temporale comandi periodici:1~1000ms，utilizzato principalmente per l'intervallo tra ogni invio di comandi periodici"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Impostazione Tipo Trasferimento File Termine
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleFileType(type)``"
    "Descrizione", "Imposta il tipo di trasferimento file del termine"
    "Parametri Obbligatori", "- ``type``：1-File aggiornamento MCU,2-File LUA"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Impostazione Abilitazione Esecuzione LUA Termine
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaEnable(enable)``"
    "Descrizione", "Imposta l'abilitazione dell'esecuzione LUA del termine"
    "Parametri Obbligatori", "- ``enable``：0-Non abilitato；1-Abilitato"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Recupero Errore Anomalo File LUA Termine
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRecoverAxleLuaErr(enable)``"
    "Descrizione", "Recupero errore anomalo file LUA termine"
    "Parametri Obbligatori", "- ``status``：0-Non recuperare；1-Recupera"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode "

Ottenimento Stato Abilitazione Esecuzione LUA Termine
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableStatus()``"
    "Descrizione", "Ottiene lo stato di abilitazione dell'esecuzione LUA del termine"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode 
    - ``enable``：0-Non abilitato；1-Abilitato"

Imposta i tipi di dispositivo abilitati per l'end-effector LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaEnableDeviceType(self, forceSensorEnable, gripperEnable, IOEnable, dexhandEnable)``"
    "Descrizione", "Imposta i tipi di dispositivo abilitati per l'end-effector LUA"
    "Parametri obbligatori", "
    - ``forceSensorEnable``: Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    - ``gripperEnable``: Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    - ``IOEnable``: Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    - ``dexhandEnable``: Stato abilitazione mano destra, 0-disabilitato; 1-abilitato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore, 0-successo; diverso da zero-errore"

Ottiene i tipi di dispositivo abilitati per l'end-effector LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableDeviceType()``"
    "Descrizione", "Ottiene i tipi di dispositivo abilitati per l'end-effector LUA"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore, 0-successo; diverso da zero-errore
    - ``forceSensorEnable``: Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    - ``gripperEnable``: Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    - ``IOEnable``: Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    - ``dexhandEnable``: Stato abilitazione mano destra, 0-disabilitato; 1-abilitato"

Ottiene i dispositivi dell'end-effector attualmente configurati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaEnableDevice()``"
    "Descrizione", "Ottiene i dispositivi dell'end-effector attualmente configurati"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore, 0-successo; diverso da zero-errore
    - ``forceSensorEnable[8]``: Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    - ``gripperEnable[8]``: Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    - ``IOEnable[8]``: Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    - ``dexhandEnable``: Stato abilitazione mano destra, 0-disabilitato; 1-abilitato"

Imposta le funzioni di controllo azione pinza abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleLuaGripperFunc(id, func)``"
    "Descrizione", "Imposta le funzioni di controllo azione pinza abilitate"
    "Parametri obbligatori", "
    - ``id``: Numero dispositivo pinza
    - ``func``: 0-abilitazione pinza; 1-inizializzazione pinza; 2-impostazione posizione; 3-impostazione velocità; 4-impostazione coppia; 6-lettura stato pinza; 7-lettura stato inizializzazione; 8-lettura codice guasto; 9-lettura posizione; 10-lettura velocità; 11-lettura coppia; 12-impostazione giri per pinza rotante; 13-impostazione velocità rotazione pinza rotante; 14-impostazione coppia rotazione pinza rotante; 15-lettura stato pinza rotante; 16-lettura stato inizializzazione pinza rotante; 17-lettura giri pinza rotante; 18-lettura velocità pinza rotante; 19-lettura coppia pinza rotante; 20-impostazione movimento sincrono multiasse; 21-comando clear guasti; 22-stato funzionamento singolo asse; 23-stato funzionamento tutti gli assi;"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore, 0-successo; diverso da zero-errore"

Ottiene le funzioni di controllo azione pinza abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxleLuaGripperFunc(id)``"
    "Descrizione", "Ottiene le funzioni di controllo azione pinza abilitate"
    "Parametri obbligatori", "- ``id``: Numero dispositivo pinza"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore, 0-successo; diverso da zero-errore
    - ``func``: 0-abilitazione pinza; 1-inizializzazione pinza; 2-impostazione posizione; 3-impostazione velocità; 4-impostazione coppia; 6-lettura stato pinza; 7-lettura stato inizializzazione; 8-lettura codice guasto; 9-lettura posizione; 10-lettura velocità; 11-lettura coppia; 12-impostazione giri per pinza rotante; 13-impostazione velocità rotazione pinza rotante; 14-impostazione coppia rotazione pinza rotante; 15-lettura stato pinza rotante; 16-lettura stato inizializzazione pinza rotante; 17-lettura giri pinza rotante; 18-lettura velocità pinza rotante; 19-lettura coppia pinza rotante; 20-impostazione movimento sincrono multiasse; 21-comando clear guasti; 22-stato funzionamento singolo asse; 23-stato funzionamento tutti gli assi;"

Scrittura File Slave Ethercat Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SlaveFileWrite(type,slaveID,fileName)``"
    "Descrizione", "Scrittura file slave Ethercat robot"
    "Parametri Obbligatori", "- ``type``：Tipo file slave，1-Aggiornamento file slave；2-Aggiornamento file configurazione slave
    - ``slaveID``：Numero slave
    - ``fileName``：Nome file da caricare"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Upload File LUA Protocollo Aperto Termine
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AxleLuaUpload(filePath)``"
    "Descrizione", "Upload file LUA protocollo aperto termine"
    "Parametri Obbligatori", "- ``filePath``：Percorso file Lua locale .../AXLE_LUA_End_DaHuan.lua"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Modalità Boot Slave Ethercat Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSysServoBootMode(filePath)``"
    "Descrizione", "Imposta la modalità boot slave Ethercat robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Operazioni File LUA Termine Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua")
    param = [7, 8, 1, 0, 5, 3, 1]  # Corrisponde ai parametri AxleComParam
    robot.SetAxleCommunicationParam(7, 8, 1, 0, 5, 3, 1)
    error,getParam0,getParam1,getParam2,getParam3,getParam4,getParam5,getParam6 = robot.GetAxleCommunicationParam()
    print(f"GetAxleCommunicationParam param is:{getParam0} {getParam1} {getParam2} {getParam3} {getParam4} {getParam5} {getParam6}")
    robot.SetAxleLuaEnable(1)
    error,luaEnableStatus = robot.GetAxleLuaEnableStatus()
    robot.SetAxleLuaEnableDeviceType(0, 1, 0)
    error,forceEnable, gripperEnable, ioEnable = robot.GetAxleLuaEnableDeviceType()
    print(f"GetAxleLuaEnableDeviceType param is:{forceEnable} {gripperEnable} {ioEnable}")
    func = [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1]
    robot.SetAxleLuaGripperFunc(1, func)
    error,getFunc = robot.GetAxleLuaGripperFunc(1)
    error,getforceEnable, getgripperEnable, getioEnable = robot.GetAxleLuaEnableDevice()
    print("\ngetforceEnable status:", end=" ")
    for i in range(8):
        print(f"{getforceEnable[i]},", end="")
    print("\ngetgripperEnable status:", end=" ")
    for i in range(8):
        print(f"{getgripperEnable[i]},", end="")
    print("\ngetioEnable status:", end=" ")
    for i in range(8):
        print(f"{getioEnable[i]},", end="")
    print()
    robot.ActGripper(1, 0)
    time.sleep(2)
    robot.ActGripper(1, 1)
    time.sleep(2)
    robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0)
    while True:
        error,pkg = robot.GetRobotRealTimeState()
        print(f"gripper pos is:{pkg.gripper_position}")
        time.sleep(0.1)
    robot.CloseRPC()
    
Ottenimento Stato Pulsante SmartTool
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSmarttoolBtnState()``"
    "Descrizione", "Ottiene lo stato del pulsante SmartTool"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``state``：Stato pulsante manopola SmartTool;(bit0:0-Comunicazione normale；1-Comunicazione interrotta；bit1-Annulla operazione；bit2-Svuota programma；bit3-Tasto A；bit4-Tasto B；bit5-Tasto C；bit6-Tasto D；bit7-Tasto E；bit8-Tasto IO；bit9-Manuale/Automatico；bit10-Inizia)"

Esempio di Codice Pulsante SmartTool
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    while True:
        error,state = robot.GetSmarttoolBtnState()
        print(f"{state:016b}")
        time.sleep(0.1)

Impostazione Rilevamento Forza Carico Prima Abilitazione Trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTorqueDetectionSwitch(flag)``"
    "Descrizione", "Imposta il rilevamento della forza del carico prima dell'abilitazione del trascinamento"
    "Parametri Obbligatori", "- ``flag``：0-Disattiva；1-Attiva"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Funzione Accensione/Spegnimento Periferica Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingLaserOnOff(OnOff, weldId)``"
    "Descrizione", "Funzione accensione/spegnimento periferica laser"
    "Parametri Obbligatori", "- ``OnOff``：0-Spegni；1-Accendi"
    "Parametri Predefiniti", "- ``weldId``：ID saldatura predefinito 0"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Funzione Inizio/Fine Inseguimento Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingTrackOnOff(OnOff, coordId)``"
    "Descrizione", "Funzione inizio/fine inseguimento laser"
    "Parametri Obbligatori", "- ``OnOff``：0-Spegni；1-Accendi
    - ``coordId``：Numero sistema coordinate utensile periferica laser"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ricerca Posizione Laser - Direzione Fissa
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSearchStart_xyz(direction, vel, distance, timeout, posSensorNum)``"
    "Descrizione", "Ricerca posizione laser - direzione fissa"
    "Parametri Obbligatori", "- ``direction``：0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    - ``vel``：Velocità unità%
    - ``distance``：Distanza massima ricerca unità mm
    - ``timeout``：Tempo timeout ricerca unità ms
    - ``posSensorNum``：Numero sistema coordinate utensile calibrato laser"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ricerca Posizione Laser - Direzione Arbitraria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSearchStart_point(directionPoint, vel, distance, timeout, posSensorNum)``"
    "Descrizione", "Ricerca posizione laser - direzione arbitraria"
    "Parametri Obbligatori", "- ``directionPoint``：Coordinate xyz punto input ricerca,[x,y,z]
    - ``vel``：Velocità unità%
    - ``distance``：Distanza massima ricerca unità mm
    - ``timeout``：Tempo timeout ricerca unità ms
    - ``posSensorNum``：Numero sistema coordinate utensile calibrato laser"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Configurazione IP Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSensorConfig(ip, port)``"
    "Descrizione", "Configurazione IP laser"
    "Parametri Obbligatori", "- ``ip``：Indirizzo IP periferica laser
    - ``port``：Numero porta periferica laser"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Configurazione Periodo Campionamento Periferica Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserTrackingSensorSamplePeriod(period)``"
    "Descrizione", "Configurazione periodo campionamento periferica laser"
    "Parametri Obbligatori", "- ``period``：Periodo campionamento periferica laser unità ms"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Caricamento Driver Periferica Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadPosSensorDriver(type)``"
    "Descrizione", "Caricamento driver periferica laser"
    "Parametri Obbligatori", "- ``type``：Tipo protocollo driver periferica laser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Scaricamento Driver Periferica Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``UnLoadPosSensorDriver()``"
    "Descrizione", "Scaricamento driver periferica laser"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Registrazione Traiettoria Saldatura Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorRecord1(status, delayTime)``"
    "Descrizione", "Registrazione traiettoria saldatura laser"
    "Parametri Obbligatori", "- ``status``：0-Arresta registrazione 1-Inseguimento in tempo reale  2-Inizia registrazione
    - ``delayTime``：Tempo ritardo unità ms"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Riproduzione Traiettoria Saldatura Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorReplay(delayTime, speed)``"
    "Descrizione", "Riproduzione traiettoria saldatura laser"
    "Parametri Obbligatori", "- ``delayTime``：Tempo ritardo unità ms
    - ``speed``：Velocità unità%"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
    
Riproduzione Inseguimento Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveLTR()``"
    "Descrizione", "Riproduzione inseguimento laser"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Riproduzione Traiettoria Saldatura Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserSensorRecordandReplay(delayMode, delayTime, delayDisExAxisNum, delayDis, sensitivePara, int trackMode, int triggerMode, double runTime, speed)``"
    "Descrizione", "Riproduzione Traiettoria Cordone di Saldatura Laser"
    "Parametri Richiesti", "- ``delayMode``: Modalità 0-Tempo Ritardo 1-Distanza Ritardo
    - ``delayTime``: Tempo di ritardo in millisecondi (ms)
    - ``delayDisExAxisNum``: Numero Asse Esteso
    - ``delayDis``: Distanza di ritardo in millimetri (mm)
    - ``sensitivePara``: Coefficiente di Sensibilità della Compensazione
    - ``trackMode``: Tipo Tracciamento a Punto Fisso. 0-Movimento Asincrono Asse Esteso; 1-Robot
    - ``triggerMode``: Metodo di Attivazione Tracciamento a Punto Fisso. 0-Durata Tracciamento; 1-IO
    - ``runTime``: Durata Tracciamento a Punto Fisso del Robot in secondi (s)
    - ``speed``: Velocità in percentuale (%)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice Errore. Successo - 0, Fallimento - errcode"

Movimento al Punto Inizio Registrazione Saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserRecordStart(moveType, ovl)``"
    "Descrizione", "Movimento al punto inizio registrazione saldatura"
    "Parametri Obbligatori", "- ``moveType``：0-PTP 1-LIN
    - ``ovl``：Velocità unità%"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Movimento al Punto Fine Registrazione Saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserRecordEnd(moveType, ovl)``"
    "Descrizione", "Movimento al punto fine registrazione saldatura"
    "Parametri Obbligatori", "- ``moveType``：0-PTP 1-LIN
    - ``ovl``：Velocità unità%"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Movimento al Punto Ricerca Sensore Laser
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToLaserSeamPos(moveFlag, ovl, dataFlag, plateType, trackOffectType, offset)``"
    "Descrizione", "Movimento al punto ricerca sensore laser"
    "Parametri Obbligatori", "- ``moveFlag``：Tipo movimento：0-PTP；1-LIN
    - ``ovl``：Fattore scala velocità，0-100
    - ``dataFlag``：Selezione dati cache saldatura：0-Esegue dati pianificati；1-Esegue dati registrati
    - ``plateType``：Tipo pannello：0-Pannello ondulato；1-Pannello trapezoidale；2-Pannello recinzione；3-Bidone olio；4-Pannello corazzato ondulato
    - ``trackOffectType``：Tipo offset sensore laser：0-Nessun offset；1-Offset sistema base；2-Offset sistema utensile；3-Offset dati originali sensore laser
    - ``offset``：Valore offset"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Informazioni Coordinate Punto Ricerca Sensore Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserSeamPos(trackOffectType, offset)``"
    "Descrizione", "Ottiene le informazioni coordinate del punto ricerca sensore laser"
    "Parametri Obbligatori", "- ``trackOffectType``：Tipo offset sensore laser：0-Nessun offset；1-Offset sistema base；2-Offset sistema utensile；3-Offset dati originali sensore laser
    - ``offset``：Valore offset"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``jPos``：Posizione giunti[°]
    - ``descPos``：Posizione cartesiana[mm]
    - ``tool``：Sistema coordinate utensile
    - ``user``：Sistema coordinate pezzo
    - ``exaxis``：Posizione asse espansione[mm]"

Esempio di Codice Configurazione Parametri e Debug Sensore Periferica Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.LaserTrackingSensorConfig("192.168.58.20", 5020)
    robot.LaserTrackingSensorSamplePeriod(20)
    robot.LoadPosSensorDriver(101)
    robot.LaserTrackingLaserOnOff(0, 0)
    time.sleep(3)
    robot.LaserTrackingLaserOnOff(1, 0)
    robot.CloseRPC()

Esempio di Codice Scansione Traiettoria Laser e Riproduzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    i = 0
    while i<10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(2, 10)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 50,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserSensorRecord1(0, 10)
        robot.MoveToLaserRecordStart(1, 30)
        robot.LaserSensorReplay(10, 100)
        robot.MoveLTR()
        robot.LaserSensorRecord1(0, 10)
        i = i+1
    robot.CloseRPC()

Esempio di Codice Ricerca Posizione Laser e Inseguimento in Tempo Reale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua")
    robot.UnloadCtrlOpenLUA(0)
    robot.LoadCtrlOpenLUA(0)
    time.sleep(8)
    time.sleep(8)
    i = 0
    while i < 10:
        startjointPos = [56.205, -117.951, 141.872, -118.149, -94.217, -122.176]
        startdescPose = [-97.552, -282.855, 26.675, 174.182, -1.338, -91.707]
        exaxisPos = [0.0] * 4
        offdese = [0.0] * 6
        directionPoint = [0.0] * 3
        robot.MoveL(desc_pos=startdescPose,tool= 1,user= 0,vel= 100,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3)
        robot.LaserTrackingSearchStop()
        robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese)
        robot.LaserTrackingTrackOnOff(1, 3)
        endjointPos = [68.809, -87.100, 121.120, -127.233, -95.038, -109.555]
        enddescPose = [-103.555, -464.234, 13.076, 174.179, -1.344, -91.709]
        robot.MoveL(desc_pos=enddescPose,tool= 1,user= 0,vel= 20,acc= 100,ovl= 100,blendR= -1,exaxis_pos= exaxisPos,search= 0,offset_flag= 0, offset_pos= offdese,overSpeedStrategy= 1,speedPercent= 1)
        robot.LaserTrackingTrackOnOff(0, 3)
        i = i + 1
        print(i)
    robot.CloseRPC()

Esempio di Codice Inseguimento Laser Sincrono con Asse Espansione e Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    startexaxisPos = [0.0, 0.0, 0.0, 0.0]
    seamexaxisPos = [-10.0, 0.0, 0.0, 0.0]
    endexaxisPos = [-30.0, 0.0, 0.0, 0.0]
    offdese = [0.0] * 6
    seamjointPos = [0.0] * 6
    seamdescPose = [0.0] * 6
    i=0
    while i < 10:
        startjointPos = [58.337, -119.628, 146.037, -116.358, -92.224, -117.654]
        startdescPose = [-53.375, -255.363, 0.919, 178.054, 1.077, -94.026]
        robot.ExtAxisSyncMoveJ(joint_pos=startjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= startexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
        ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2)
        robot.LaserTrackingSearchStop()
        tool = 0
        user = 0
        rnte, seamjointPos, seamdescPose, tool, user, startexaxisPos = robot.GetLaserSeamPos(0, offdese)
        print(f"{seamjointPos[0]},{seamjointPos[1]},{seamjointPos[2]},{seamjointPos[3]},{seamjointPos[4]},{seamjointPos[5]},{seamdescPose[0]},{seamdescPose[1]},{seamdescPose[2]},{seamdescPose[3]},{seamdescPose[4]},{seamdescPose[5]}")
        if ret == 0:
            robot.ExtAxisSyncMoveJ(joint_pos=seamjointPos, tool=1,user= 0,vel= 100,acc= 100, ovl=100,exaxis_pos= seamexaxisPos,blendT= -1,offset_flag= 0,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(1, 2)
            endjointPos = [70.580, -90.918, 126.593, -125.154, -92.162, -105.403]
            enddescPose = [-53.375, -419.020, 0.920, 178.054, 1.076, -94.026]
            robot.ExtAxisSyncMoveL(desc_pos=enddescPose, tool=1,user= 0,vel= 20,acc= 100, ovl=100,blendR= -1,exaxis_pos= endexaxisPos,offset_pos= offdese)
            robot.LaserTrackingTrackOnOff(0, 2)
        i = i+1
        print(i)
    robot.CloseRPC()

Controllo Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSuckerCtrl(slaveID, len, ctrlValue)``"
    "Descrizione", "Controllo ventosa a matrice"
    "Parametri Obbligatori", "- ``slaveID``: Numero stazione slave
    - ``len``: Lunghezza
    - ``ctrlValue``: Valore di controllo 1-Aspirazione a vuoto massimo 2-Aspirazione a vuoto impostato 3-Arresto aspirazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Ottenere Stato Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSuckerState(slaveID)``"
    "Descrizione", "Ottiene lo stato della ventosa a matrice"
    "Parametri Obbligatori", "- ``slaveID``: Numero stazione slave"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode
    - ``state``: Stato aspirazione 0-Oggetto rilasciato 1-Aspirazione pezzo riuscita 2-Nessun oggetto aspirato 3-Oggetto distaccato
    - ``pressValue``: Pressione di vuoto corrente unità kPa
    - ``error``: Codice errore corrente della ventosa"

Attendere Stato Ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitSuckerState(slaveID, state, ms)``"
    "Descrizione", "Attende lo stato della ventosa"
    "Parametri Obbligatori", "- ``slaveID``: Numero stazione slave
    - ``state``: Stato aspirazione 0-Oggetto rilasciato 1-Aspirazione pezzo riuscita 2-Nessun oggetto aspirato 3-Oggetto distaccato
    - ``ms``: Tempo massimo di attesa"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Esempio di Codice per Comando di Controllo Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire la connessione con il controller del robot, in caso di successo restituisce un oggetto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("C://Progetto/PerifericheSDK/CtrlDev_sucker.lua")
    time.sleep(2)
    robot.UnloadCtrlOpenLUA(1)
    robot.LoadCtrlOpenLUA(1)
    time.sleep(1)
    ctrl = bytearray(20)
    ctrl[0] = 1
    robot.SetSuckerCtrl(0, 1, ctrl)
    for i in range(100):
        rtn, state, press_value, error = robot.GetSuckerState(1)
        print(f"sucker1 state is {state}, pressValue is {press_value}, error num is {error}")
        rtn, state, press_value, error = robot.GetSuckerState(12)
        print(f"sucker12 state is {state}, pressValue is {press_value}, error num is {error}")
        time.sleep(0.1)
    ret = robot.WaitSuckerState(1, 1, 100)
    print(f"WaitSuckerState result is {ret}")
    ctrl[0] = 3
    robot.SetSuckerCtrl(1, 1, ctrl)
    robot.SetSuckerCtrl(12, 1, ctrl)
    robot.CloseRPC()

Caricare File Lua di Protocollo Aperto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaUpload(filePath)``"
    "Descrizione", "Carica file Lua di protocollo aperto"
    "Parametri Obbligatori", "- ``filePath``: Percorso locale del file Lua di protocollo aperto"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Ottenere Parametri Scheda Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetFieldBusConfig()``"
    "Descrizione", "Ottiene i parametri della scheda stazione slave"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode
    - ``type``: 0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    - ``version``: Versione protocollo
    - ``connState``: 0-Non connesso 1-Connesso"

Scrivere DO Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWriteDO(DOIndex, writeNum, status)``"
    "Descrizione", "Scrive DO stazione slave"
    "Parametri Obbligatori", "- ``DOIndex``: Numero DO
    - ``writeNum``: Numero di valori da scrivere
    - ``status``: Valori da scrivere, massimo 8"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Scrivere AO Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWriteAO(AOIndex, writeNum, status)``"
    "Descrizione", "Scrive AO stazione slave"
    "Parametri Obbligatori", "- ``AOIndex``: Numero AO
    - ``writeNum``: Numero di valori da scrivere
    - ``status``: Valori da scrivere, massimo 8"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Leggere DI Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveReadDI(DIIndex, readNum)``"
    "Descrizione", "Legge DI stazione slave"
    "Parametri Obbligatori", "- ``DIIndex``: Numero DI
    - ``readNum``: Numero di valori da leggere"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode
    - ``status[8]``: Valori letti, massimo 8"

Leggere AI Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveReadAI(AIIndex, readNum)``"
    "Descrizione", "Legge AI stazione slave"
    "Parametri Obbligatori", "- ``AIIndex``: Numero AI
    - ``readNum``: Numero di valori da leggere"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode
    - ``status[8]``: Valori letti, massimo 8"

Attendere Ingresso DI Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWaitDI(DIIndex, status, waitMs)``"
    "Descrizione", "Attende ingresso DI esteso"
    "Parametri Obbligatori", "- ``DIIndex``: Numero DI
    - ``status``: 0-Livello basso; 1-Livello alto
    - ``waitMs``: Tempo massimo di attesa (ms)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Attendere Ingresso AI Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FieldBusSlaveWaitAI(AIIndex, waitType, value, waitMs)``"
    "Descrizione", "Attende ingresso AI esteso"
    "Parametri Obbligatori", "- ``AIIndex``: Numero AI
    - ``waitType``: 0-Maggiore di; 1-Minore di
    - ``value``: Valore AI
    - ``waitMs``: Tempo massimo di attesa (ms)"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Esempio di Codice per Comandi Interfaccia Modalità Stazione Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire la connessione con il controller del robot, in caso di successo restituisce un oggetto robot
    robot = Robot.RPC('192.168.58.2')
    robot.OpenLuaUpload("D://zUP/Periferiche/CtrlDev_field.lua")
    time.sleep(2)
    robot.SetCtrlOpenLUAName(3,"CtrlDev_field.lua")
    robot.UnloadCtrlOpenLUA(3)
    robot.LoadCtrlOpenLUA(3)
    time.sleep(8)
    rtn,type, version, conn_state = robot.GetFieldBusConfig()
    print(f"type is {type}, version is {version}, connState is {conn_state}")
    # Write digital outputs
    ctrl = [1, 0, 1]  # DO0=1, DO1=0, DO2=1
    robot.FieldBusSlaveWriteDO(0, 3, ctrl)
    # Write analog output
    ctrl_ao = [0x1000]  # AO2 = 0x1000
    robot.FieldBusSlaveWriteAO(2, 1, ctrl_ao)
    for i in range(100):
        rtn,di = robot.FieldBusSlaveReadDI(0, 4)
        print(f"DI0 is {di[0]}, DI1 is {di[1]}, DI2 is {di[2]}, DI3 is {di[3]}")
        rtn, ai = robot.FieldBusSlaveReadAI(0, 3)
        print(f"AI0 is {ai[0]}, AI1 is {ai[1]}, AI2 is {ai[2]}")
        time.sleep(0.01)
    ret = robot.FieldBusSlaveWaitDI(0, 1, 100)
    print(f"FieldBusSlaveWaitDI result is {ret}")
    ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00, 100)
    print(f"FieldBusSlaveWaitAI result is {ret}")
    robot.CloseRPC()

Abilita/Disabilita Funzione di Trasmissione Trasparente dell'End-Effector SDK Interface
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxleGenComEnable(mode)``"
    "Descrizione", "Abilita la funzione di trasmissione trasparente generale dell'end-effector"
    "Parametri Obbligatori", "- ``mode``: Abilitazione, 0-disabilita, 1-abilita"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Trasmissione e Ricezione Dati Non Periodici della Funzione di Trasmissione Trasparente dell'End-Effector SDK Interface
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SndRcvAxleGenComCmdData(len_snd, sndBuff, len_rcv)``"
    "Descrizione", "L'end-effector invia dati non periodici e attende risposta"
    "Parametri Obbligatori", "
    - ``len_snd``: Lunghezza dei dati da inviare;
    - ``sndBuff[]``: Dati da inviare;
    - ``len_rcv``: Lunghezza dei dati da ricevere;
    - ``rcvBuff[]``: Dati di risposta;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Esempio di Codice per Comunicazione Dati Non Periodici del DIO Health Care Moxibustion Head basato sulla Funzione di Trasmissione Trasparente dell'End-Effector
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    from ctypes import sizeof
    # Stabilire la connessione con il controller del robot, in caso di successo restituisce un oggetto robot
    robot = Robot.RPC('192.168.58.2')

    import time


    def testAxleGenCom(self):

        led_on = [0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79]
        led_off = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        version = [0xAB, 0xBA, 0x11, 0x00, 0x76]
        state = [0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B]
        cycleState = [0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78]
        cnt = 1

        p1Joint = [88.708, -86.178, 140.989, -141.825, -89.162, -49.879]
        p1Desc = [188.007, -377.850, 260.207, 178.715, 2.823, -131.466]
        p2Joint = [112.131, -75.554, 126.989, -139.027, -88.044, -26.477]
        p2Desc = [368.003, -377.848, 260.211, 178.715, 2.823, -131.465]

        exaxisPos = [0, 0, 0, 0]
        offdese = [0, 0, 0, 0, 0, 0]

        #Abilita la funzione di trasmissione trasparente dell'end-effector
        robot.SetAxleGenComEnable(1)
        robot.SetAxleLuaEnable(1)

        while cnt <= 10000:
            #Legge il numero di versione
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(len_snd=5, sndBuff=version, len_rcv=10)
            print(ret)
            print(rcvdata)
            print(f"hard version : {rcvdata[4]},hard code:{rcvdata[5]}, soft version:{rcvdata[6]} {rcvdata[7]}, soft code:{rcvdata[8]}")
            if ret != 0:
                break
            time.sleep(1)
            # Legge lo stato di presenza della testa di moxibustione
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, state, 6)
            print(f"state : {rcvdata[4]} ")
            time.sleep(1)
            # Accende il laser della testa di moxibustione
            ret,rcvdata = robot.SndRcvAxleGenComCmdData(6, led_on, 6)
            print(f"led on rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p1Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,
                            offset_flag=0, offset_pos=offdese)
            time.sleep(4)
            # Spegne il laser della testa di moxibustione
            ret, rcvdata = robot.SndRcvAxleGenComCmdData(6, led_off, 6)
            print(f"led off rcv data is: {rcvdata[0]}, {rcvdata[1]}, {rcvdata[2]}, {rcvdata[3]}, {rcvdata[4]}, {rcvdata[5]}")
            robot.MoveJ(joint_pos=p2Joint, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=exaxisPos, blendT=-1,offset_flag=0, offset_pos=offdese)
            time.sleep(1)
            print(f"***********************complate No. {cnt} SDK test*****************************")
            cnt = cnt + 1

        robot.CloseRPC()
        return 0

    testAxleGenCom(robot)
    
Scarica File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaDownload(fileName, savePath)``"
    "Descrizione", "Scarica file Lua di protocollo aperto"
    "Parametri Obbligatori", "
    - ``fileName``: Nome del file di protocollo aperto `CtrlDev_XXX.lua`;
    - ``savePath``: Percorso di salvataggio del file di protocollo aperto;
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Elimina File Lua di Protocollo Aperto Specificato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``OpenLuaDelete(fileName)``"
    "Descrizione", "Elimina file Lua di protocollo aperto specificato"
    "Parametri Obbligatori", "
    - ``fileName``: Nome del file Lua di protocollo aperto da eliminare `CtrlDev_XXX.lua`
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Elimina Tutti i File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AllOpenLuaDelete()``"
    "Descrizione", "Elimina tutti i file Lua di protocollo aperto"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Esempio di Codice SDK per Operazioni su File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from time import sleep
    import time
    from fairino import Robot

    # Stabilire la connessione con il controller del robot
    robot = Robot.RPC('192.168.58.2')


    def TestCtrlOpenLuaOperate(self):
        # Carica file Lua sul robot
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua")
        print(f"OpenLuaUpload rtn is {rtn}")
        
        # Scarica file Lua dal robot
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/")
        print(f"OpenLuaDownload rtn is {rtn}")
        
        # Imposta nome Lua di protocollo aperto di controllo
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua")
        print(f"SetCtrlOpenLUAName rtn is {rtn}")
        
        # Ottiene nome Lua di protocollo aperto di controllo
        rtn, name = robot.GetCtrlOpenLUAName()
        print(f"ctrl open lua names : {name[0]}, {name[1]}, {name[2]}, {name[3]}")
        
        # Carica Lua di protocollo aperto di controllo
        rtn = robot.LoadCtrlOpenLUA(1)
        print(f"LoadCtrlOpenLUA rtn is {rtn}")
        time.sleep(2)
        
        # Scarica Lua di protocollo aperto di controllo
        rtn = robot.UnloadCtrlOpenLUA(1)
        print(f"UnloadCtrlOpenLUA rtn is {rtn}")
        
        # Elimina file Lua specificato
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua")
        print(f"OpenLuaDelete rtn is {rtn}")
        
        # Elimina tutti i file Lua
        rtn = robot.AllOpenLuaDelete()
        print(f"AllOpenLuaDelete rtn is {rtn}")
        
        # Chiudi connessione
        robot.CloseRPC()
        time.sleep(1)


    # Chiama la funzione di test
    TestCtrlOpenLuaOperate(robot)

Controllo del Movimento della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsMove(self, idstart, slaveNum, pos, speed, force, max_time)``"
    "Descrizione", "Controllo del movimento della mano destra"
    "Parametri Obbligatori", "
    - ``idstart``: Numero stazione slave iniziale;
    - ``slaveNum``: Numero di slave;
    - ``pos[16]``: Posizione (-360~360);
    - ``speed[16]``: Percentuale di velocità, intervallo [0~100];
    - ``force[16]``: Percentuale di coppia, intervallo [0~100];
    - ``max_time``: Tempo massimo di attesa, intervallo [0~30000], unità ms;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"
        
Controllo del Reset e Attivazione della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsAct(self, id, act)``"
    "Descrizione", "Controllo del reset e attivazione della mano destra"
    "Parametri Obbligatori", "
    - ``id``: Numero stazione slave;
    - ``act``: 0-reset 1-attivazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"
        
Cancellazione dell'Errore della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ClearDexterousHandsError(self)``"
    "Descrizione", "Cancellazione dell'errore della mano destra"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"
    
Impostazione delle Funzioni di Controllo Azione Mano Destra Abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDexterousHandsFunc(self, id, func)``"
    "Descrizione", "Imposta le funzioni di controllo azione mano destra abilitate"
    "Parametri Obbligatori", "
    - ``id``: Numero stazione slave della mano destra;
    - ``func``: Array di funzioni, 32 elementi
        0-attivazione presa, 1-inizializzazione pinza, 2-impostazione posizione, 3-impostazione velocità, 4-impostazione coppia,
        6-lettura stato pinza, 7-lettura stato inizializzazione, 8-lettura codice guasto, 9-lettura posizione, 10-lettura velocità,
        11-lettura coppia, 12-impostazione giri rotazione, 13-impostazione velocità rotazione, 14-impostazione coppia rotazione,
        15-lettura stato pinza rotante, 16-lettura stato inizializzazione rotazione, 17-lettura giri rotazione, 18-lettura velocità rotazione,
        19-lettura coppia rotazione, 20-impostazione movimento sincrono multiasse, 21-comando clear guasti, 22-stato funzionamento singolo asse,
        23-stato funzionamento tutti gli assi"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"
    
Ottenimento delle Funzioni di Controllo Azione Mano Destra Abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDexterousHandsFunc(self, id)``"
    "Descrizione", "Ottiene le funzioni di controllo azione mano destra abilitate"
    "Parametri Obbligatori", "
    - ``id``: Numero stazione slave della mano destra;
    - ``func``: Array di funzioni, 32 elementi
        0-attivazione presa, 1-inizializzazione pinza, 2-impostazione posizione, 3-impostazione velocità, 4-impostazione coppia,
        6-lettura stato pinza, 7-lettura stato inizializzazione, 8-lettura codice guasto, 9-lettura posizione, 10-lettura velocità,
        11-lettura coppia, 12-impostazione giri rotazione, 13-impostazione velocità rotazione, 14-impostazione coppia rotazione,
        15-lettura stato pinza rotante, 16-lettura stato inizializzazione rotazione, 17-lettura giri rotazione, 18-lettura velocità rotazione,
        19-lettura coppia rotazione, 20-impostazione movimento sincrono multiasse, 21-comando clear guasti, 22-stato funzionamento singolo asse,
        23-stato funzionamento tutti gli assi"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"

Esempio di Codice per Configurazione e Movimento della Mano Destra sull'End-Effector  
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:  
     
    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')

    def main(self):

        id = 1                 
        slaveNum = 4         
        max_time = 8000      
        speed = [0] * 16     
        force = [0] * 16     

        for i in range(16):
            force[i] = 50 if i < 4 else 0

        def set_positions(v1, v2, v3, v4):
            pos = [0.0] * 16
            pos[0] = v1
            pos[1] = v2
            pos[2] = v3
            pos[3] = v4
            return pos

        j1 = [-53.426,-85.916,109.280,-86.236,-96.663,-28.560]
        j2 = [-91.877,-85.917,109.281,-86.236,-96.663,-28.560]
        epos = [0, 0, 0, 0]
        offset_pos = [0, 0, 0, 0, 0, 0]

        ret = robot.ClearDexterousHandsError()
        print(f"ClearDexterousHandsError -> {ret}")

        setFunc = [0] * 32
        setFunc[2] = 1   
        setFunc[4] = 1   
        setFunc[9] = 1   
        setFunc[10] = 1  
        setFunc[11] = 1  
        setFunc[22] = 1  

        ret = robot.SetDexterousHandsFunc(id, setFunc)
        print(f"SetDexterousHandsFunc(abilitazione init + funzioni posizione/coppia) -> {ret}")

        ret, getFunc = robot.GetDexterousHandsFunc(id)
        print(f"GetDexterousHandsFunc -> {ret}")
        if ret == 0:
            print("GetDexterousHandsFunc :")
            for i in range(len(getFunc)):
                print(f"  [{i}]={getFunc[i]}", end="")
                if (i + 1) % 8 == 0:
                    print()  
                elif i < len(getFunc) - 1:
                    print(", ", end="")
            if len(getFunc) % 8 != 0:

        ret = robot.SetDexterousHandsAct(id, 1)
        print(f"SetDexterousHandsAct() -> {ret}")
        if ret != 0:
            return
            pos = set_positions(20, 20, 20, 20)
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
        print(f"ret: {ret}")
        time.sleep(5)

        for iteration in range(1, 11):
            robot.MoveJ(joint_pos=j1, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(10, 10, 10, 10)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

            robot.MoveJ(joint_pos=j2, tool=1, user=0, vel=100, acc=100, ovl=100,
                        exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

            pos = set_positions(50, 50, 50, 50)
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time)
            time.sleep(1)

    main(robot)    