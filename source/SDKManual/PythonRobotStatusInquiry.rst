Query dello Stato del Robot
==========================================

.. toctree::
    :maxdepth: 5

Ottenere la Posizione Corrente dei Giunti (Gradi)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointPosDegree(flag=1)``"
    "Descrizione", "Ottiene la posizione corrente dei giunti (gradi)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Posizione corrente dei giunti (gradi)"

Ottenere la Posizione Corrente dei Giunti (Radianti)
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointPosRadian(flag=1)``"
    "Descrizione", "Ottiene la posizione corrente dei giunti (radianti)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Posizione corrente dei giunti (radianti)"

Ottenere la Velocità di Feedback dei Giunti - deg/s
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointSpeedsDegree(flag=1)``"
    "Descrizione", "Ottiene la velocità di feedback dei giunti - deg/s"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``speed=[j1,j2,j3,j4,j5,j6]``: Velocità di feedback dei giunti - deg/s"

Ottenere l'Accelerazione di Feedback dei Giunti - deg/s²
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualJointAccDegree(flag=1)``"
    "Descrizione", "Ottiene l'accelerazione di feedback dei giunti - deg/s²"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``acc=[j1,j2,j3,j4,j5,j6]``: Accelerazione di feedback dei giunti - deg/s²"

Ottenere la Velocità Composita TCP di Comando
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetTCPCompositeSpeed(flag=1)``"
    "Descrizione", "Ottiene la velocità composita TCP di comando"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``[tcp_speed,ori_speed]``: tcp_speed-velocità composita lineare, ori_speed-velocità composita di orientamento"

Ottenere la Velocità Composita TCP di Feedback
++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPCompositeSpeed(flag=1)``"
    "Descrizione", "Ottiene la velocità composita TCP di feedback"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``[tcp_speed,ori_speed]``: tcp_speed-velocità composita lineare, ori_speed-velocità composita di orientamento"

Ottenere la Velocità TCP di Comando
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetTCPSpeed(flag=1)``"
    "Descrizione", "Ottiene la velocità TCP di comando"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``speed=[x,y,z,rx,ry,rz]``: Velocità TCP di comando, mm/s"

Ottenere la Velocità TCP di Feedback
++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPSpeed(flag=1)``"
    "Descrizione", "Ottiene la velocità TCP di feedback"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``speed=[x,y,z,rx,ry,rz]``: Velocità TCP di feedback"

Ottenere la Posa Corrente dello Strumento
++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPPose(flag=1)``"
    "Descrizione", "Ottiene la posa corrente dello strumento"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Posa corrente dello strumento"

Ottenere il Numero del Sistema di Coordinate dello Strumento Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualTCPNum(flag=1)``"
    "Descrizione", "Ottiene il numero del sistema di coordinate dello strumento corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``tool_id``: Numero del sistema di coordinate dello strumento"

Ottenere il Numero del Sistema di Coordinate del Pezzo in Lavorazione Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualWObjNum(flag=1)``"
    "Descrizione", "Ottiene il numero del sistema di coordinate del pezzo in lavorazione corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``wobj_id``: Numero del sistema di coordinate del pezzo in lavorazione"

Ottenere la Posa Corrente della Flangia Terminale
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetActualToolFlangePose(flag=1)``"
    "Descrizione", "Ottiene la posa corrente della flangia terminale"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "- ``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``flange_pose=[x,y,z,rx,ry,rz]``: Posa corrente della flangia terminale"

Ottenere la Coppia Corrente dei Giunti
+++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointTorques(flag=1)``"
    "Descrizione", "Ottiene la coppia corrente dei giunti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "``flag``: 0-blocco, 1-non bloccante, predefinito 1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``torques=[j1,j2,j3,j4,j5,j6]``: Coppia dei giunti"

Ottenere l'Ora di Sistema
+++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSystemClock()``"
    "Descrizione", "Ottiene l'ora di sistema"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``t_ms``: Ora di sistema, unità [ms]"

Verificare se il Movimento del Robot è Completato
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotMotionDone()``"
    "Descrizione", "Verifica se il movimento del robot è completato"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``state``: Stato del movimento del robot, 0-non completato, 1-completato"

Verificare la Lunghezza della Coda di Movimento del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetMotionQueueLength()``"
    "Descrizione", "Verifica la lunghezza della coda di movimento del robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``len``: Lunghezza della coda"

Ottenere lo Stato di Arresto di Emergenza del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotEmergencyStopState()``"
    "Descrizione", "Ottiene lo stato di arresto di emergenza del robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``state``: Stato di arresto di emergenza, 0-normale, 1-arresto di emergenza"

Ottenere lo Stato di Comunicazione SDK-Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSDKComState()``"
    "Descrizione", "Ottiene lo stato di comunicazione SDK-robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``state``: Stato di comunicazione, 0-normale, 1-anomalo"

Ottenere il Segnale di Arresto di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSafetyStopState()``"
    "Descrizione", "Ottiene il segnale di arresto di sicurezza"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``[si0_state,si1_state]``: si0_state segnale di arresto di sicurezza SI0, 0-invalido, 1-valido; si1_state segnale di arresto di sicurezza SI1, 0-invalido, 1-valido"

Ottenere la Temperatura Corrente dei Driver dei Giunti (°C)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointDriverTemperature()``"
    "Descrizione", "Ottiene la temperatura corrente dei driver dei giunti (°C)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``data=[t1,t2,t3,t4,t5,t6]``: Temperatura corrente di ciascun giunto"

Ottenere la Coppia Corrente dei Driver dei Giunti (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointDriverTorque()``"
    "Descrizione", "Ottiene la coppia corrente dei driver dei giunti (Nm)"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``data=[j1,j2,j3,j4,j5,j6]``: Coppia dei giunti [fx,fy,fz,tx,ty,tz]"

Ottenere lo Stato del Robot
+++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotRealTimeState()``"
    "Descrizione", "Ottiene lo stato del robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``robot_state_pkg``: Struttura dello stato del robot"

Esempio di Codice per la Query dello Stato del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce la connessione con il controller del robot, restituisce un oggetto robot se ha successo
    robot = Robot.RPC('192.168.58.2')
    error,[yangle, zangle] = robot.GetRobotInstallAngle()
    print(f"yangle:{yangle},zangle:{zangle}")
    error,j_deg = robot.GetActualJointPosDegree(0)
    print(f"joint pos deg:{j_deg[0]},{j_deg[1]},{j_deg[2]},{j_deg[3]},{j_deg[4]},{j_deg[5]}")
    error,jointSpeed = robot.GetActualJointSpeedsDegree(0)
    print(f"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}")
    error,jointAcc = robot.GetActualJointAccDegree(0)
    print(f"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}")
    error,[tcp_speed, ori_speed] = robot.GetTargetTCPCompositeSpeed(0)
    print(f"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,[tcp_speed, ori_speed] = robot.GetActualTCPCompositeSpeed(0)
    print(f"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}")
    error,targetSpeed = robot.GetTargetTCPSpeed(0)
    print(f"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}")
    error,actualSpeed = robot.GetActualTCPSpeed(0)
    print(f"GetActualTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}")
    error,tcp = robot.GetActualTCPPose(0)
    print(f"tcp pose:{tcp[0]},{tcp[1]},{tcp[2]},{tcp[3]},{tcp[4]},{tcp[5]}")
    error,flange = robot.GetActualToolFlangePose(0)
    print(f"flange pose:{flange[0]},{flange[1]},{flange[2]},{flange[3]},{flange[4]},{flange[5]}")
    error,id = robot.GetActualTCPNum(0)
    print(f"tcp num:{id}")
    error,id = robot.GetActualWObjNum(0)
    print(f"wobj num:{id}")
    error,jtorque = robot.GetJointTorques(0)
    print(f"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}")
    error,t_ms = robot.GetSystemClock()
    print(f"system clock:{t_ms}")
    error,config = robot.GetRobotCurJointsConfig()
    print(f"joint config:{config}")
    error,motionDone = robot.GetRobotMotionDone()
    print(f"GetRobotMotionDone:{motionDone}")
    error,len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength:{len}")
    error,emergState = robot.GetRobotEmergencyStopState()
    print(f"GetRobotEmergencyStopState:{emergState}")
    error,comstate = robot.GetSDKComState()
    print(f"GetSDKComState:{comstate}")
    error,[si0_state, si1_state] = robot.GetSafetyStopState()
    print(f"GetSafetyStopState:{si0_state} {si1_state}")
    error,temp = robot.GetJointDriverTemperature()
    print(f"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}")
    error,torque = robot.GetJointDriverTorque()
    print(f"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}")
    error,pkg = robot.GetRobotRealTimeState()
    robot.CloseRPC()

Soluzione di Cinematica Inversa
++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKin(type,desc_pos,config=-1)``"
    "Descrizione", "Cinematica inversa, posa cartesiana per risolvere la posizione dei giunti"
    "Parametri Obbligatori", "- ``type``: 0-posa assoluta (sistema di coordinate base), 1-posa relativa (sistema di coordinate base), 2-posa relativa (sistema di coordinate strumento)
    - ``desc_pose``: [x,y,z,rx,ry,rz], posa dello strumento, unità [mm][°]"
    "Parametri Predefiniti", "- ``config``: Configurazione dei giunti, [-1]-risolvi con riferimento alla posizione corrente dei giunti, [0~7]-risolvi secondo la configurazione dei giunti, predefinito -1"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Soluzione di cinematica inversa, posa cartesiana per risolvere la posizione dei giunti"

Soluzione di Cinematica Inversa - Posizione di Riferimento Specificata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinRef(type,desc_pos,joint_pos_ref)``"
    "Descrizione", "Cinematica inversa, posa dello strumento per risolvere la posizione dei giunti, risolvi con riferimento alla posizione dei giunti specificata"
    "Parametri Obbligatori", "- ``type``: 0-posa assoluta (sistema di coordinate base), 1-posa relativa (sistema di coordinate base), 2-posa relativa (sistema di coordinate strumento)
    - ``desc_pos``: [x,y,z,rx,ry,rz] posa dello strumento, unità [mm][°]
    - ``joint_pos_ref``: [j1,j2,j3,j4,j5,j6], posizione di riferimento dei giunti, unità [°]"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``joint_pos=[j1,j2,j3,j4,j5,j6]``: Soluzione di cinematica inversa, posa dello strumento per risolvere la posizione dei giunti"

Soluzione Cinematica Inversa, Spazio Cartesiano Include Posizione Asse Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinExaxis(type, desc_pos, exaxis, tool, workPiece)``"
    "Descrizione", "Soluzione cinematica inversa, spazio cartesiano include posizione asse esteso"
    "Parametri Obbligatori", "- ``type``: 0-Posa assoluta (sistema coordinate base), 1-Posa incrementale (sistema coordinate base), 2-Posa incrementale (sistema coordinate utensile)
    - ``desc_pos``: Posa cartesiana
    - ``exaxis``: Posizione asse esteso
    - ``tool``: Numero utensile
    - ``workPiece``: Numero pezzo"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0 Fallimento- errcode
    - ``joint_pos``: Posizione giunto"

Esempio Codice Soluzione Cinematica Inversa con Posizione Asse Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    desc = [99.957, -0.002, 29.994, -176.569, -6.757, -167.462]
    exaxis = [100.0, 0.0, 0.0, 0.0]
    jointPos = [0.0] * 6
    offsetPos = [0.0] * 6
    rtn,pkg = robot.GetRobotRealTimeState()
    toolnum = pkg.tool
    workPcsNum = pkg.user
    rtn, jointPos = robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum)
    print(f"GetInverseKinExaxis joint is {jointPos[0]},{jointPos[1]},{jointPos[2]},{jointPos[3]},{jointPos[4]},{jointPos[5]}")
    robot.ExtAxisMove(exaxis, 100, -1)
    robot.MoveJ(joint_pos=jointPos, desc_pos=desc, tool=toolnum, user=workPcsNum, vel=100.0, acc=100.0, ovl=100.0, exaxis_pos=exaxis, blendT=-1, offset_flag=0, offset_pos=offsetPos)
    robot.CloseRPC()
    return 0

Soluzione di Cinematica Inversa - Esistenza della Soluzione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetInverseKinHasSolution(type,desc_pos,joint_pos_ref)``"
    "Descrizione", "Cinematica inversa, verifica se esiste una soluzione per la posa dello strumento per risolvere la posizione dei giunti"
    "Parametri Obbligatori", "- ``type``: 0-posa assoluta (sistema di coordinate base), 1-posa relativa (sistema di coordinate base), 2-posa relativa (sistema di coordinate strumento)
    - ``desc_pos``: [x,y,z,rx,ry,rz] posa dello strumento, unità [mm][°]
    - ``joint_pos_ref``: [j1,j2,j3,j4,j5,j6], posizione di riferimento dei giunti, unità [°]"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``result``: True-esiste soluzione, False-nessuna soluzione"

Soluzione di Cinematica Diretta
+++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForwardKin(joint_pos)``"
    "Descrizione", "Cinematica diretta, posizione dei giunti per risolvere la posa dello strumento"
    "Parametri Obbligatori", "- ``joint_pos``: [j1,j2,j3,j4,j5,j6]: Posizione dei giunti, unità [°]"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``desc_pos=[x,y,z,rx,ry,rz]``: Soluzione di cinematica diretta, posizione dei giunti per risolvere la posa dello strumento"

Esempio di Codice per il Calcolo della Cinematica Diretta/Inversa del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce la connessione con il controller del robot, restituisce un oggetto robot se ha successo
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    error, inverseRtn = robot.GetInverseKin(0, desc_pos=desc_pos1, config=-1)
    print(f"dcs1 GetInverseKin rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, inverseRtn = robot.GetInverseKinRef(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef rtn is {inverseRtn[0]}, {inverseRtn[1]}, {inverseRtn[2]}, "
          f"{inverseRtn[3]}, {inverseRtn[4]}, {inverseRtn[5]}")
    error, hasResult = robot.GetInverseKinHasSolution(0, desc_pos=desc_pos1, joint_pos_ref=j1)
    print(f"dcs1 GetInverseKinRef result {hasResult}")
    error, forwordResult = robot.GetForwardKin(j1)
    print(f"jpos1 forwordResult rtn is {forwordResult[0]}, {forwordResult[1]}, {forwordResult[2]}, "
          f"{forwordResult[3]}, {forwordResult[4]}, {forwordResult[5]}")
    robot.CloseRPC()

Query dei Dati dei Punti di Gestione dell'Insegnamento del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotTeachingPoint(name)``"
    "Descrizione", "Interroga i dati dei punti di gestione dell'insegnamento del robot"
    "Parametri Obbligatori", "``name``: Nome del punto"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``[x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4]``: Dati del punto"

Ottenere i Parametri di Compensazione DH
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDHCompensation()``"
    "Descrizione", "Ottiene i parametri di compensazione DH"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``dhCompensation=[cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]``: Valori di compensazione dei parametri DH del robot (mm)"

Ottenere il Codice SN del Controllore
++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotSN()``"
    "Descrizione", "Ottiene il codice SN del controllore"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``SNCode``: Codice SN del controllore"

Esempio di Codice per la Query dei Dati dei Punti di Gestione dell'Insegnamento del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce la connessione con il controller del robot, restituisce un oggetto robot se ha successo
    robot = Robot.RPC('192.168.58.2')
    name = "P1"
    rtn, data = robot.GetRobotTeachingPoint(name)
    print(f"{rtn} name is: {name}")
    for i in range(20):
        print(f"data is: {data[i]}")
    rtn,que_len = robot.GetMotionQueueLength()
    print(f"GetMotionQueueLength rtn is: {rtn}, queue length is: {que_len}")
    retval,dh = robot.GetDHCompensation()
    print(f"retval is: {retval}")
    print(f"dh is: {dh[0]} {dh[1]} {dh[2]} {dh[3]} {dh[4]} {dh[5]}")
    error,sn = robot.GetRobotSN()
    print(f"robot SN is {sn[0]}")
    robot.CloseRPC()

Ottenere il Sistema di Coordinate dello Strumento per Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolCoordWithID(id)``"
    "Descrizione", "Ottiene il sistema di coordinate dello strumento per numero"
    "Parametri Obbligatori", "- ``id``: Numero del sistema di coordinate dello strumento"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate del Pezzo in Lavorazione per Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWObjCoordWithID(id)``"
    "Descrizione", "Ottiene il sistema di coordinate del pezzo in lavorazione per numero"
    "Parametri Obbligatori", "- ``id``: Numero del sistema di coordinate del pezzo in lavorazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate dello Strumento Esterno per Numero
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExToolCoordWithID(id)``"
    "Descrizione", "Ottiene il sistema di coordinate dello strumento esterno per numero"
    "Parametri Obbligatori", "- ``id``: Numero del sistema di coordinate dello strumento esterno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate dell'Asse Esteso per Numero
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExAxisCoordWithID(id)``"
    "Descrizione", "Ottiene il sistema di coordinate dell'asse esteso per numero"
    "Parametri Obbligatori", "- ``id``: Numero del sistema di coordinate dell'asse esteso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere Massa del Carico e Centro di Gravità per Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayloadWithID(id)``"
    "Descrizione", "Ottiene massa del carico e centro di gravità per numero"
    "Parametri Obbligatori", "- ``id``: Numero del sistema di coordinate dell'asse esteso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``weight``: Massa del carico
    - ``cog``: Centro di gravità del carico"

Ottenere il Sistema di Coordinate dello Strumento Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurToolCoord()``"
    "Descrizione", "Ottiene il sistema di coordinate dello strumento corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate del Pezzo in Lavorazione Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurWObjCoord()``"
    "Descrizione", "Ottiene il sistema di coordinate del pezzo in lavorazione corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate dello Strumento Esterno Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurExToolCoord()``"
    "Descrizione", "Ottiene il sistema di coordinate dello strumento esterno corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Ottenere il Sistema di Coordinate dell'Asse Esteso Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table::
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetCurExAxisCoord()``"
    "Descrizione", "Ottiene il sistema di coordinate dell'asse esteso corrente"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore: Successo-0  Fallimento-errcode
    - ``coord``: Valore del sistema di coordinate"

Esempio di Codice per Ottenere i Sistemi di Coordinate e il Carico del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce la connessione con il controller del robot, restituisce un oggetto robot se ha successo
    robot = Robot.RPC('192.168.58.2')
    id = 1
    toolCoord = [0.0] * 6
    extoolCoord = [0.0] * 6
    wobjCoord = [0.0] * 6
    exAxisCoord = [0.0] * 6
    for i in range(100):
        print(f"L'ID corrente è:{id}")
        coordSet0 = [0.0] * 6
        coordSet = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
        etcp = [10.0, 20.0, 30.0, 40.0, 50.0, 60.0]
        etool = [0.1, 0.2, 0.3, 0.4, 0.5, 0.6]
        cog = [1.0, 2.0, 3.0]
        if i % 2 == 0:
            robot.SetToolCoord(id, coordSet, 0, 0, 1, 0)
            time.sleep(0.1)
            robot.SetWObjCoord(id, coordSet, 0)
            time.sleep(0.1)
            robot.ExtAxisActiveECoordSys(id, 1, coordSet, 1)
            time.sleep(0.1)
            rtn = robot.SetExToolCoord(id, etcp, etool)
            time.sleep(0.1)
            rtn = robot.SetLoadWeight(id, 1.5)
            time.sleep(0.1)
            rtn = robot.SetLoadCoord(cog[0],cog[1],cog[2],id)
            time.sleep(0.1)
        else:
            robot.SetToolCoord(id, coordSet0, 0, 0, 1, 0)
            time.sleep(0.1)
            robot.SetWObjCoord(id, coordSet0, 0)
            time.sleep(0.1)
            robot.ExtAxisActiveECoordSys(id, 1, coordSet0, 1)
            time.sleep(0.1)
            rtn = robot.SetExToolCoord(id, coordSet0, coordSet0)
            time.sleep(0.1)
            rtn = robot.SetLoadWeight(id, 0)
            time.sleep(0.1)
            rtn = robot.SetLoadCoord(coordSet0[0],coordSet0[1],coordSet0[2] , id)
            time.sleep(0.1)
        rtn, toolCoord = robot.GetCurToolCoord()
        print(f"GetToolCoord {toolCoord[0]},{toolCoord[1]},{toolCoord[2]},{toolCoord[3]},{toolCoord[4]},{toolCoord[5]}")
        rtn, wobjCoord = robot.GetCurWObjCoord()
        print(f"GetWObjCoord {wobjCoord[0]},{wobjCoord[1]},{wobjCoord[2]},{wobjCoord[3]},{wobjCoord[4]},{wobjCoord[5]}")
        rtn, extoolCoord = robot.GetCurExToolCoord()
        print(f"GetExToolCoord {extoolCoord[0]},{extoolCoord[1]},{extoolCoord[2]},{extoolCoord[3]},{extoolCoord[4]},{extoolCoord[5]}")
        rtn, exAxisCoord = robot.GetCurExAxisCoord()
        print(f"GetExAxisCoord {exAxisCoord[0]},{exAxisCoord[1]},{exAxisCoord[2]},{exAxisCoord[3]},{exAxisCoord[4]},{exAxisCoord[5]}")
        weight = 0.0
        getCog = [0.0] * 3
        rtn, weight = robot.GetTargetPayload(0)
        rtn, getCog = robot.GetTargetPayloadCog(0)
        print(f"GetTargetPayload {weight},{getCog[0]},{getCog[1]},{getCog[2]}")
        
        rtn, toolCoord = robot.GetToolCoordWithID(id)
        print(f"GetToolCoordWithID {id},{toolCoord[0]},{toolCoord[1]},{toolCoord[2]},{toolCoord[3]},{toolCoord[4]},{toolCoord[5]}")
        rtn, wobjCoord = robot.GetWObjCoordWithID(id)
        print(f"GetWObjCoordWithID {id},{wobjCoord[0]},{wobjCoord[1]},{wobjCoord[2]},{wobjCoord[3]},{wobjCoord[4]},{wobjCoord[5]}")
        rtn, extoolCoord = robot.GetExToolCoordWithID(id)
        print(f"GetExToolCoordWithID {id},{extoolCoord[0]},{extoolCoord[1]},{extoolCoord[2]},{extoolCoord[3]},{extoolCoord[4]},{extoolCoord[5]}")
        rtn, exAxisCoord = robot.GetExAxisCoordWithID(id)
        print(f"GetExAxisCoordWithID {id},{exAxisCoord[0]},{exAxisCoord[1]},{exAxisCoord[2]},{exAxisCoord[3]},{exAxisCoord[4]},{exAxisCoord[5]}")
        weight = 0.0
        getCog = [0.0] * 3
        rtn, weight, getCog = robot.GetTargetPayloadWithID(id)
        print(f"GetTargetPayloadWithID {id},{weight},{getCog[0]},{getCog[1]},{getCog[2]}")
        time.sleep(0.5)
        print(f"volte {i}")