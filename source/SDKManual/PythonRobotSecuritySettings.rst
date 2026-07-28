Impostazioni Sicurezza Robot
=========================================

.. toctree:: 
    :maxdepth: 5

Impostare Livello Collisione
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAnticollision (mode,level,config)``"
    "Descrizione", "Imposta livello collisione"
    "Parametri Obbligatori", "- ``mode``:0-livello, 1-percentuale;
    - ``level=[j1,j2,j3,j4,j5,j6]``:soglia collisione;
    - ``config``:0-non aggiorna file configurazione, 1-aggiorna file configurazione"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Strategia dopo Collisione
++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCollisionStrategy(strategy,safeTime,safeDistance,safeVel,safetyMargin)``"
    "Descrizione", "Imposta strategia dopo collisione"
    "Parametri Obbligatori", "- ``strategy``：0-errore pausa, 1-continua esecuzione, 2-errore stop, 3-modalità coppia gravità, 4-modalità risposta oscillazione, 5-modalità rimbalzo collisione"
    "Parametri Predefiniti", "- ``safeTime``：tempo arresto sicurezza [1000-2000]ms, default: 1000
    - ``safeDistance``：distanza arresto sicurezza [1-150]mm, default: 100
    - ``safeVel``：velocità arresto sicurezza [50-250]mm/s, default: 250
    - ``safetyMargin[6]``：fattore sicurezza [1-10], default: [10,10,10,10,10,10]"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Inizio Funzione Soglia Rilevamento Collisione Personalizzata, Imposta Soglia Rilevamento Collisione Giunti e TCP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomCollisionDetectionStart(flag, jointDetectionThreshould, tcpDetectionThreshould, block)``"
    "Descrizione", "Inizio funzione soglia rilevamento collisione personalizzata, imposta soglia rilevamento collisione giunti e TCP"
    "Parametri Obbligatori", "- ``flag``： 1-solo rilevamento giunti attivo; 2-solo rilevamento TCP attivo; 3-rilevamento giunti e TCP attivi contemporaneamente
    - ``jointDetectionThreshould``： soglia rilevamento collisione giunti j1-j6
    - ``tcpDetectionThreshould``： soglia rilevamento collisione TCP, xyzabc
    - ``block``： 0-non bloccante; 1-bloccante"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Fine Funzione Soglia Rilevamento Collisione Personalizzata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.0

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomCollisionDetectionEnd()``"
    "Descrizione", "Fine funzione soglia rilevamento collisione personalizzata"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Esempio Codice Impostazione Livello Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    mode = 0
    config = 1
    level1 = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
    level2 = [50.0, 20.0, 30.0, 40.0, 50.0, 60.0]
    rtn = robot.SetAnticollision(mode, level1, config)
    print(f"SetAnticollision mode 0 rtn is {rtn}")
    mode = 1
    rtn = robot.SetAnticollision(mode, level2, config)
    print(f"SetAnticollision mode 1 rtn is {rtn}")
    p1Joint = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    p2Joint = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    p1Desc = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    p2Desc = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100, blendR=2)
    robot.ResetAllError()
    safety = [5, 5, 5, 5, 5, 5]
    rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety)
    print(f"SetCollisionStrategy rtn is {rtn}")
    jointDetectionThreshould = [0.1, 0.1, 0.1, 0.1, 0.1, 0.1]
    tcpDetectionThreshould = [60, 60, 60, 60, 60, 60]
    rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0)
    print(f"CustomCollisionDetectionStart rtn is {rtn}")
    robot.MoveL(desc_pos=p1Desc, tool=0, user=0, vel=100)
    robot.MoveL(desc_pos=p2Desc, tool=0, user=0, vel=100)
    rtn = robot.CustomCollisionDetectionEnd()
    print(f"CustomCollisionDetectionEnd rtn is {rtn}")
    robot.CloseRPC()

Impostare Limite Positivo
+++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLimitPositive(p_limit)``"
    "Descrizione", "Imposta limite positivo"
    "Parametri Obbligatori", "- ``p_limit=[j1,j2,j3,j4,j5,j6]``：sei posizioni giunti"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Limite Negativo
+++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLimitNegative(n_limit)``"
    "Descrizione", "Imposta limite negativo"
    "Parametri Obbligatori", "- ``n_limit=[j1,j2,j3,j4,j5,j6]``：sei posizioni giunti"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Ottenere Angoli Limiti Soft Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetJointSoftLimitDeg(flag=1)``"
    "Descrizione", "Ottiene angoli limiti soft giunti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "``flag``：0-bloccante, 1-non bloccante  default 1"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``[j1min,j1max,j2min,j2max,j3min,j3max, j4min,j4max,j5min, j5max, j6min,j6max]``：asse1~asse6, limite negativo e positivo giunti, unità[mm]"

Esempio Codice Impostazione Limiti Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    plimit = [170.0, 80.0, 150.0, 80.0, 170.0, 160.0]
    robot.SetLimitPositive(plimit)
    nlimit = [-170.0, -260.0, -150.0, -260.0, -170.0, -160.0]
    robot.SetLimitNegative(nlimit)
    error,neg_deg = robot.GetJointSoftLimitDeg(0)
    print(f"limite positivo deg: {neg_deg[1]}, {neg_deg[3]}, {neg_deg[5]}, {neg_deg[7]}, {neg_deg[9]}, {neg_deg[11]}")
    print(f"limite negativo deg: {neg_deg[0]}, {neg_deg[2]}, {neg_deg[4]}, {neg_deg[6]}, {neg_deg[8]}, {neg_deg[10]}")
    robot.CloseRPC()

Impostare Metodo Rilevamento Collisione Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetCollisionDetectionMethod(method, thresholdMode)``"
    "Descrizione", "Imposta metodo rilevamento collisione robot"
    "Parametri Obbligatori", "
    - ``method``：metodo rilevamento collisione: 0-modalità corrente; 1-doppio encoder; 2-corrente e doppio encoder entrambi attivi
    - ``thresholdMode``：modalità soglia livello collisione; 0-modalità soglia fissa livello collisione; 1-soglia rilevamento collisione personalizzata  
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Impostare Attivazione/Disattivazione Rilevamento Collisione in Stato Statico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStaticCollisionOnOff(status)``"
    "Descrizione", "Imposta attivazione/disattivazione rilevamento collisione in stato statico"
    "Parametri Obbligatori", "
    - ``status``： 0-disattivato; 1-attivato
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Esempio Codice Impostazione Metodo Rilevamento Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetCollisionDetectionMethod(0,0)
    rtn = robot.SetStaticCollisionOnOff(1)
    print(f"SetStaticCollisionOnOff On rtn is {rtn}")
    time.sleep(5)
    rtn = robot.SetStaticCollisionOnOff(0)
    print(f"SetStaticCollisionOnOff Off rtn is {rtn}")
    robot.CloseRPC()

Rilevamento Potenza Coppia Giunti
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetPowerLimit(status, power)``"
    "Descrizione", "Rilevamento potenza coppia giunti"
    "Parametri Obbligatori", "
    - ``status``：0-disattivato; 1-attivato
    - ``power``：imposta potenza massima (W)
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"
    
Esempio Codice Rilevamento Potenza Coppia Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    robot.SetPowerLimit(1, 200)
    error,torques = robot.GetJointTorques(1)
    count = 100
    robot.ServoJTStart()
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)  # ritardo 1ms
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Imposta i Parametri di Velocità di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetVelReducePara(enable, maxTCPVel, strategy, maxJointVel=[45.0, 45.0, 45.0, 45.0, 45.0, 45.0])``"
    "Descrizione", "Imposta i parametri di velocità di sicurezza"
    "Parametri Obbligatori", "
    - ``enable``: 0-disabilitato; 1-abilitato in modalità manuale; 2-abilitato in tutte le modalità (limitazione automatica della velocità non supportata)
    - ``maxTCPVel``: Limite massimo di velocità TCP; [0-1000] mm/s
    - ``strategy``: Strategia post-superamento velocità; 0-stop e allarme; 1-limitazione automatica della velocità; 2-stop e allarme con disabilitazione
    - ``maxJointVel``: Velocità massima per 6 giunti (°/s), default [45.0, 45.0, 45.0, 45.0, 45.0, 45.0]
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore, 0-successo; diverso da zero-errore"

Esempio di Codice SDK per Impostare i Parametri di Velocità di Sicurezza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time


    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        j1 = [10.220, -11.121, -118.086, -46.739, 82.036, 131.503]
        j2 = [89.782, -11.122, -118.086, -46.740, 82.036, 131.504]

        epos = [0.0, 0.0, 0.0, 0.0]
        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]

        robot.SetSpeed(20)

        maxJointVel = [100.0, 100.0, 100.0, 100.0, 100.0, 100.0]

        rtn = robot.SetVelReducePara(0, 200, 0, maxJointVel)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaA param error rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        maxJointVel = [20.0, 20.0, 20.0, 20.0, 20.0, 20.0]
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVel)
        print(f"SetVelReduceParaB reduce vel rtn is {rtn}")

        robot.MoveJ(joint_pos=j1, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
        robot.MoveJ(joint_pos=j2, tool=1, user=2, vel=100, acc=100, ovl=100,
                    exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)

        robot.CloseRPC()

    if __name__ == "__main__":
        main()