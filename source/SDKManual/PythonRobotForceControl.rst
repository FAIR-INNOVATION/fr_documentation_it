Controllo di Forza del Robot
============================

.. toctree:: 
    :maxdepth: 5

Configurazione del sensore di forza
+++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetConfig(company,device,softversion=0,bus=0)``"
    "Descrizione", "Configurazione del sensore di forza"
    "Parametri obbligatori", "- ``company``：Produttore sensore, 17-Kunwei Technology, 19-Academy 11, 20-Sensore ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xin Jingcheng (XJC), 26-NSR；
    - ``device``：Numero dispositivo, Kunwei (0-KWR75B), Academy 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A), NBIT (0-XLH93003ACS), Xin Jingcheng XJC (0-XJC-6F-D82), NSR (0-NSR-FTSensorA)；"
    "Parametri predefiniti", "- ``softversion``：Numero versione software, non utilizzato attualmente, default 0；
    - ``bus``：Posizione bus terminale dispositivo, non utilizzato attualmente, default 0；"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Ottenere configurazione sensore di forza
+++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetConfig()``"
    "Descrizione", "Ottenere configurazione sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``[number,company,device,softversion,bus]``：number numero sensore;company  produttore sensore forza, 17-Kunwei Technology, 19-Academy 11, 20-Sensore ATI, 21-Zhongke Midian, 22-Weihang Minxin;device  numero dispositivo, Kunwei (0-KWR75B), Academy 11 (0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB10A);softvesion  numero versione software, non utilizzato attualmente, default 0" 

Attivazione sensore di forza
++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Activate(state)``"
    "Descrizione", "Attivazione sensore di forza"
    "Parametri obbligatori", "- ``state``：0-reset, 1-attiva"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

Calibrazione zero sensore di forza
+++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetZero(state)``"
    "Descrizione", "Calibrazione zero sensore di forza"
    "Parametri obbligatori", "- ``state``：0-rimuovi zero, 1-calibrazione zero"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Impostare sistema di riferimento sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SetRCS(ref,coord=[0,0,0,0,0,0])``"
    "Descrizione", "Impostare sistema di riferimento sensore di forza"
    "Parametri obbligatori", "- ``ref``：0-sistema coordinato utensile, 1-sistema coordinato base"
    "Parametri predefiniti", "- ``coord``：[x,y,z,rx,ry,rz] valore sistema coordinato personalizzato, default [0,0,0,0,0,0]"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

        
Impostare peso carico sotto sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorPayload(weight)``"
    "Descrizione", "Impostare peso carico sotto sensore di forza"
    "Parametri obbligatori", " - ``weight``：peso carico kg"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"
  
Impostare centro di gravità carico sotto sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorPayloadCog(x,y,z)``"
    "Descrizione", "Impostare centro di gravità carico sotto sensore di forza"
    "Parametri obbligatori", "
    - ``x``：centro di gravità carico x mm
    - ``y``：centro di gravità carico y mm
    - ``z``：centro di gravità carico z mm
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"
            
Ottenere peso carico sotto sensore di forza
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceSensorPayload()``"
    "Descrizione", "Ottenere peso carico sotto sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``weight``：peso carico kg"
            
Ottenere centro di gravità carico sotto sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceSensorPayloadCog()``"
    "Descrizione", "Ottenere centro di gravità carico sotto sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``x``：centro di gravità carico x mm 
    - ``y``：centro di gravità carico y mm 
    - ``z``：centro di gravità carico z mm"

Calibrazione zero automatica sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ForceSensorAutoComputeLoad()``"
    "Descrizione", "Calibrazione zero automatica sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``weight``：massa sensore kg
    - ``pos=[x,y,z]``：centro di gravità sensore mm"

Ottenere dati forza/coppia sistema di riferimento
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetForceTorqueRCS()``"
    "Descrizione", "Ottenere dati forza/coppia sistema di riferimento"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode 
    - ``data=[fx,fy,fz,tx,ty,tz]``：dati forza/coppia sistema di riferimento"

Ottenere dati forza/coppia originali sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_GetForceTorqueOrigin()``"
    "Descrizione", "Ottenere dati forza/coppia originali sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode  
    - ``data=[fx,fy,fz,tx,ty,tz]``：dati forza/coppia originali sensore di forza "

Esempio codice configurazione e calibrazione zero automatica sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    ftCoord = [0, 0, 0, 0, 0, 0]
    robot.FT_SetRCS(0, ftCoord)
    robot.SetForceSensorPayload(0.824)
    robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765)
    error,weight = robot.GetForceSensorPayload()
    error,x, y, z = robot.GetForceSensorPayloadCog()
    print(f"the FT load is  {weight}, {x} {y} {z}")
    robot.SetForceSensorPayload(0)
    robot.SetForceSensorPayloadCog(0, 0, 0)
    error,computeWeight, tran = robot.ForceSensorAutoComputeLoad()
    print(f"the result is weight {computeWeight} pos is {tran[0]} {tran[1]} {tran[2]}")
    robot.CloseRPC()

Registrazione identificazione peso carico
++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdIdenRecord(tool_id)``"
    "Descrizione", "Registrazione identificazione peso carico"
    "Parametri obbligatori", "- ``tool_id``：numero sistema coordinato sensore, range [0~14]"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode  "

Calcolo identificazione peso carico
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdIdenCompute()``"
    "Descrizione", "Calcolo identificazione peso carico"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode   
    - ``weight``：peso carico, unità kg  "

Registrazione identificazione centro di gravità carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdCogIdenRecord(tool_id,index)``"
    "Descrizione", "Registrazione identificazione centro di gravità carico"
    "Parametri obbligatori", "- ``tool_id``：numero sistema coordinato sensore, range [0~14];
    - ``index``：numero punto [1~3]"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Calcolo identificazione centro di gravità carico
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_PdCogIdenCompute()``"
    "Descrizione", "Calcolo identificazione centro di gravità carico"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode  
    - ``cog=[cogx,cogy,cogz]``：centro di gravità carico, unità mm  "

Esempio codice identificazione carico sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    error,ft = robot.FT_GetForceTorqueOrigin()
    print(f"ft origin:{ft[0]},{ft[1]},{ft[2]},{ft[3]},{ft[4]},{ft[5]}")
    robot.FT_SetZero(1)
    time.sleep(1)
    tcoord = [0, 0, 35.0, 0, 0, 0]
    robot.SetToolCoord(10, tcoord, 1, 0, 0, 0)
    robot.FT_PdIdenRecord(10)
    time.sleep(1)
    error,weight = robot.FT_PdIdenCompute()
    print(f"payload weight:{weight}")
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 1)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 2)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    time.sleep(1)
    robot.FT_PdCogIdenRecord(10, 3)
    time.sleep(1)
    error,cog = robot.FT_PdCogIdenCompute()
    print(f"FT_PdCogIdenCompute return {error}")
    print(f"cog:{cog[0]},{cog[1]},{cog[2]}")
    robot.CloseRPC()

Protezione collisione
++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Guard(flag,sensor_num,select,force_torque,max_threshold,min_threshold)``"
    "Descrizione", "Protezione collisione"
    "Parametri obbligatori", "- ``flag``：0-disattiva protezione collisione, 1-attiva protezione collisione；
    - ``sensor_num``：numero sensore di forza；
    - ``select``：sei gradi di libertà se rilevare collisione [fx,fy,fz,mx,my,mz], 0-non attivo, 1-attivo；
    - ``force_torque``：forza/coppia rilevamento collisione, unità N o Nm；
    - ``max_threshold``：soglia massima；
    - ``min_threshold``：soglia minima；
    - Intervallo rilevamento forza/coppia:(force_torque-min_threshold,force_torque+max_threshold)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

Esempio codice protezione collisione
+++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    sensor_id = 1
    select = [1, 1, 1, 1, 1, 1]
    max_threshold = [10.0, 10.0, 10.0, 10.0, 10.0, 10.0]
    min_threshold = [5.0, 5.0, 5.0, 5.0, 5.0, 5.0]
    ft = None 
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_p3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    error = robot.FT_Guard(1, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.MoveCart(desc_p1, 0, 0, 100.0)
    robot.MoveCart(desc_p2, 0, 0, 100.0)
    robot.MoveCart(desc_p3, 0, 0, 100.0)
    robot.FT_Guard(0, sensor_id, select,[0.0,0.0,0.0,0.0,0.0,0.0], max_threshold, min_threshold)
    robot.CloseRPC()

Controllo forza costante
++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M=None, B=None, threshold=[0.2,0.2], adjustCoeff=[1.0,1.0], polishRadio=0, filter_Sign=0, posAdapt_sign=0, isNoBlock=0)``"
    "Descrizione", "Controllo forza costante"
    "Parametri obbligatori", "- ``flag``：flag attivazione controllo forza costante, 0-off, 1-on；
    - ``sensor_id``：numero sensore di forza；
    - ``select``：sei gradi di libertà se rilevare [fx,fy,fz,mx,my,mz], 0-non attivo, 1-attivo；
    - ``ft``：forza/coppia rilevamento, unità N o Nm；
    - ``ft_pid``：[f_p,f_i,f_d,m_p,m_i,m_d], parametri PID forza, parametri PID coppia；
    - ``adj_sign``：stato avvio/arresto adattativo, 0-disattiva, 1-attiva；
    - ``ILC_sign``: stato avvio/arresto controllo ILC, 0-arresta, 1-addestra, 2-operazione；
    - ``max_dis``：distanza regolazione massima；
    - ``max_ang``：angolo regolazione massimo；"
    "Parametri predefiniti", "- ``M``：parametri massa；
    - ``B``：parametri smorzamento；
    - ``threshold``：Soglia di attivazione per rx, ry [0-10], predefinito 0.2；
    - ``adjustCoeff``：Coefficiente di regolazione della coppia per rx, ry [0-1], predefinito 1；
    - ``polishRadio``：raggio disco levigatura, unità mm；
    - ``filter_Sign``：flag attivazione filtro 0-off; 1-on, default 0-disattiva；
    - ``posAdapt_sign``：flag attivazione adattamento posa 0-off; 1-on, default 0-disattiva；
    - ``isNoBlock``：flag bloccante, 0-bloccante; 1-non bloccante default 0-bloccante；"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

Esempio codice controllo forza costante con smorzamento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    sensor_id = 10
    select = [0, 0, 1, 0, 0, 0]
    ft_pid = [0.0008, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 1000.0
    max_ang = 20.0
    ft = [0.0] * 6 
    epos = [0.0] * 4
    j1 = [80.765, -98.795, 106.548, -97.734, -89.999, 94.842]
    j2 = [43.067, -84.429, 92.620, -98.175, -90.011, 57.144]
    desc_p1 = [5.009, -547.463, 262.053, -179.999, -0.019, 75.923]
    desc_p2 = [-347.966, -547.463, 262.048, -180.000, -0.019, 75.923]
    offset_pos = [0.0] * 6
    M = [2.0, 2.0]
    B = [15.0, 15.0]
    threshold = [1.0, 1.0]
    adjustCoeff = [1.0, 0.8]
    polishRadio = 0.0
    filter_Sign = 0
    posAdapt_sign = 1
    isNoBlock = 0
    ft[2] = -10.0 
    while True:
        rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control start rtn is {rtn}")
        rtn = robot.MoveL(desc_pos=desc_p1, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.MoveL(desc_pos=desc_p2, tool=1, user=0, vel=100, acc=100, ovl=100, blendR=-1, blendMode = 0, exaxis_pos=epos, search=0, offset_flag=0, offset_pos=offset_pos)
        rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold,adjustCoeff, 0, 0, 1, 0)
        print(f"FT_Control end rtn is {rtn}")
    robot.CloseRPC()
    return 0

Ricerca spirale
+++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_SpiralSearch(rcs, ft, dr=0.7, max_t_ms=60000, max_vel=5)``"
    "Descrizione", "Ricerca spirale"
    "Parametri obbligatori", "- ``rcs``：sistema di riferimento, 0-sistema coordinato utensile, 1-sistema coordinato base
    - ``ft``：soglia forza o coppia (0~100), unità N o Nm;"
    "Parametri predefiniti", "- ``dr``：avanzamento raggio per giro, unità mm default 0.7;
    - ``max_t_ms``：tempo ricerca massimo, unità ms default 60000;
    - ``max_vel``：velocità lineare massima, unità mm/s default 5"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

Inserzione Rotazionale
++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_RotInsertion(rcs, ft, orn, angVelRot=3, angleMax=45, angAccmax=0, rotorn=1, strategy=0)``"
    "Descrizione", "Inserzione Rotazionale"
    "Parametri Richiesti", "- ``rcs``: Sistema di coordinate di riferimento, 0 - Sistema di coordinate utensile, 1 - Sistema di coordinate base;
    - ``ft``: Soglia forza o coppia (0~100), unità N o Nm;
    - ``orn``: Direzione forza/coppia, 1 - Lungo l'asse Z, 2 - Attorno all'asse Z;"
    "Parametri Predefiniti", "- ``angVelRot``: Velocità angolare di rotazione, unità °/s, predefinita 3;
    - ``angleMax``: Angolo di rotazione massimo, unità °, predefinito 45;
    - ``angAccmax``: Accelerazione angolare massima, unità °/s^2, attualmente non utilizzata, predefinita 0;
    - ``rotorn``: Direzione di rotazione, 1 - Senso orario, 2 - Senso antiorario, predefinita 1;
    - ``strategy``: Strategia di elaborazione per forza/coppia non rilevata, 0 - Errore; 1 - Avviso, continua movimento"
    "Valore di Ritorno", "Codice di errore. Successo - 0, Fallimento - errcode"

Esempio Codice per Ricerca a Spirale, Inserzione Lineare e Altri Comandi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1=[-11.904,-99.669,117.473,-108.616,-91.726,74.256]
    j2=[-45.615,-106.172,124.296,-107.151,-91.282,74.255]
    j3=[-29.777,-84.536,109.275,-114.075,-86.655,74.257]
    j4=[-31.154,-95.317,94.276,-88.079,-89.740,74.256]
    desc_pos1=[-419.524,-13.000,351.569,-178.118,0.314,3.833]
    desc_pos2=[-321.222,185.189,335.520,-179.030,-1.284,-29.869]
    desc_pos3=[-487.434,154.362,308.576,176.600,0.268,-14.061]
    desc_pos4=[-443.165,147.881,480.951,179.511,-0.775,-15.409]
    offset_pos=[0.0]*6
    epos=[0.0]*4
    tool=0
    user=0
    vel=100.0
    acc=100.0
    ovl=100.0
    oacc=100.0
    blendT=0.0
    blendR=0.0
    flag=0
    search=0
    blendMode=0
    velAccMode=0
    robot.SetSpeed(20)
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,oacc=oacc,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    rtn=robot.MoveCart(desc_pos=desc_pos4,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendT=blendT,config=-1)
    print(f"MoveCarterrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j1,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.MoveL(desc_pos=desc_pos2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,blendR=blendR,blendMode=blendMode,exaxis_pos=epos,search=search,offset_flag=flag,offset_pos=offset_pos,config=-1,velAccParamMode=velAccMode)
    print(f"movelerrcode:{rtn}")
    rtn=robot.MoveC(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,offset_flag_p=flag,offset_pos_p=offset_pos,desc_pos_t=desc_pos4,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,offset_flag_t=flag,offset_pos_t=offset_pos,ovl=ovl,blendR=blendR,config=-1,velAccParamMode=velAccMode)
    print(f"movecerrcode:{rtn}")
    rtn=robot.MoveJ(joint_pos=j2,tool=tool,user=user,vel=vel,acc=acc,ovl=ovl,exaxis_pos=epos,blendT=blendT,offset_flag=flag,offset_pos=offset_pos)
    print(f"movejerrcode:{rtn}")
    rtn=robot.Circle(desc_pos_p=desc_pos3,tool_p=tool,user_p=user,vel_p=vel,acc_p=acc,exaxis_pos_p=epos,desc_pos_t=desc_pos1,tool_t=tool,user_t=user,vel_t=vel,acc_t=acc,exaxis_pos_t=epos,ovl=ovl,offset_flag=flag,offset_pos=offset_pos,oacc=oacc,blendR=-1,velAccParamMode=velAccMode)
    print(f"circleerrcode:{rtn}")
    robot.CloseRPC()
    return 0

Inserimento lineare
+++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_LinInsertion(rcs, ft, disMax, linorn, lin_v=1.0, lin_a=1.0)``"
    "Descrizione", "Inserimento lineare"
    "Parametri obbligatori", "- ``rcs``：sistema di riferimento, 0-sistema coordinato utensile, 1-sistema coordinato base；
    - ``ft``：soglia forza o coppia (0~100), unità N o Nm;
    - ``disMax``：distanza inserimento massima, unità mm;
    - ``linorn``：direzione inserimento:0-direzione negativa, 1-direzione positiva"
    "Parametri predefiniti", "- ``lin_v``：velocità lineare, unità mm/s default 1;
    - ``lin_a``：accelerazione lineare, unità mm/s^2, non utilizzato attualmente default 1"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode "

Esempio codice comandi ricerca spirale, inserimento lineare ecc.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:
    
    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    status = 1
    sensor_num = 1
    gain = [0.0001, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 5.0
    ft = [0.0,0.0,-10.0,0.0,0.0,0.0]
    rcs = 0
    dr = 0.7
    fFinish = 1.0
    t = 60000.0
    vmax = 3.0
    force_goal = 20.0
    lin_v = 0.0
    lin_a = 0.0
    disMax = 100.0
    linorn = 1
    angVelRot = 2.0
    forceInsertion = 1.0
    angleMax = 45
    orn = 1
    angAccmax = 0.0
    rotorn = 1
    select1 = [0, 0, 1, 1, 1, 0]
    robot.FT_Control(status, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax)
    print(f"FT_SpiralSearch rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select1, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select2 = [1, 1, 1, 0, 0, 0]
    gain[0] = 0.00005
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select2, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select3 = [0, 0, 1, 1, 1, 0]
    ft[2] = -10.0
    gain[0] = 0.0001
    robot.FT_Control(1, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn)
    print(f"FT_RotInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select3, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    select4 = [1, 1, 1, 0, 0, 0]
    ft[2] = -30.0
    robot.FT_Control(1, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn)
    print(f"FT_LinInsertion rtn is {rtn}")
    robot.FT_Control(0, sensor_num, select4, ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Localizzazione superficie
+++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_FindSurface (rcs, dir, axis, disMax, ft, lin_v=3.0, lin_a=0.0)``"
    "Descrizione", "Localizzazione superficie"
    "Parametri obbligatori", "- ``rcs``： sistema di riferimento, 0-sistema coordinato utensile, 1-sistema coordinato base；
    - ``dir``：direzione movimento, 1-direzione positiva, 2-direzione negativa；
    - ``axis``：asse movimento, 1-x, 2-y, 3-z；
    - ``disMax``：distanza ricerca massima, unità mm;
    - ``ft``：soglia forza terminazione azione, unitàN；"
    "Parametri predefiniti", "- ``lin_v``：velocità linea ricerca, unitàmm/s default 3;
    - ``lin_a``：accelerazione linea ricerca, unitàmm/s^2 default 0;"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Inizio calcolo posizione piano intermedio
++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_CalCenterStart()``"
    "Descrizione", "Inizio calcolo posizione piano intermedio"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Fine calcolo posizione piano intermedio
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_CalCenterEnd()``"
    "Descrizione", "Fine calcolo posizione piano intermedio"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode
    - ``pos=[x,y,z,rx,ry,rz]``：posizione piano intermedio"

Esempio codice localizzazione superficie
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    rcs = 0
    dir = 1
    axis = 1
    lin_v = 3.0
    lin_a = 0.0
    maxdis = 50.0
    ft_goal = 2.0
    desc_pos = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    xcenter = [0, 0, 0, 0, 0, 0]
    ycenter = [0, 0, 0, 0, 0, 0]
    ft = [-2.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.FT_CalCenterStart()
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,xcenter = robot.FT_CalCenterEnd()
    print(f"xcenter:{xcenter[0]},{xcenter[1]},{xcenter[2]},{xcenter[3]},{xcenter[4]},{xcenter[5]}")
    robot.MoveCart(xcenter, 9, 0, 60.0)
    robot.FT_CalCenterStart()
    dir = 1
    axis = 2
    lin_v = 6.0
    maxdis = 150.0
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    robot.MoveCart(desc_pos, 9, 0, 100.0)
    robot.WaitMs(1000)
    dir = 2
    robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal)
    error,ycenter = robot.FT_CalCenterEnd()
    print(f"ycenter:{ycenter[0]},{ycenter[1]},{ycenter[2]},{ycenter[3]},{ycenter[4]},{ycenter[5]}")
    robot.MoveCart(ycenter, 9, 0, 60.0)
    robot.CloseRPC()

Avvio controllo conformità
++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_ComplianceStart(p, force)``"
    "Descrizione", "Avvio controllo conformità"
    "Parametri obbligatori", "- ``p``: coefficiente regolazione posizione o coefficiente conformità
    - ``force``：soglia forza attivazione conformità, unitàN"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode  "

Arresto controllo conformità
++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FT_ComplianceStop()``"
    "Descrizione", "Arresto controllo conformità"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice controllo conformità
++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    company = 24
    device = 0
    softversion = 0
    bus = 1
    index = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    error,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    flag = 1
    sensor_id = 1
    select = [1, 1, 1, 0, 0, 0]
    ft_pid = [0.0005, 0.0, 0.0, 0.0, 0.0, 0.0]
    adj_sign = 0
    ILC_sign = 0
    max_dis = 100.0
    max_ang = 0.0
    ft = [-10.0, -10.0, -10.0, 0.0, 0.0, 0.0]
    offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0]  # Sostituisce DescPose(0, 0, 0, 0, 0, 0)
    epos = [0.0,0.0,0.0,0.0]  # Sostituisce ExaxisPos(0, 0, 0, 0)
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]  # JointPos
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_p1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]  # DescPose
    desc_p2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    p = 0.00005
    force = 30.0
    rtn = robot.FT_ComplianceStart(p, force)
    print(f"FT_ComplianceStart rtn is {rtn}")
    count = 3
    while count > 0:
        robot.MoveL(desc_pos=desc_p1,tool= 0,user= 0,vel= 100.0)
        robot.MoveL(desc_pos=desc_p2,tool= 0,user= 0,vel= 100.0)
        count -= 1
    robot.FT_ComplianceStop()
    print(f"FT_ComplianceStop rtn is {rtn}")
    flag = 0
    robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0)
    robot.CloseRPC()

Inizializzazione filtro identificazione carico
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyDynFilterInit()``"
    "Descrizione", "Inizializzazione filtro identificazione carico"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode  "

Inizializzazione variabili identificazione carico
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyDynVarInit()``"
    "Descrizione", "Inizializzazione variabili identificazione carico"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode  "

Programma principale identificazione carico
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyMain(joint_torque, joint_pos, t)``"
    "Descrizione", "Programma principale identificazione carico"
    "Parametri obbligatori", "- ``joint_torque``： coppia giunti j1-j6；
    - ``joint_pos``：posizione giunti j1-j6
    - ``t``：periodo campionamento"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Ottenere risultati identificazione carico
++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LoadIdentifyGetResult(gain)``"
    "Descrizione", "Ottenere risultati identificazione carico"
    "Parametri obbligatori", "- ``gain``：coefficiente termine gravità double[6], coefficiente termine centrifugo double[6]"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``weight``：peso carico
    - ``cog=[x,y,z]``：coordinate centro di gravità carico"

Esempio codice identificazione carico robot
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    retval = robot.LoadIdentifyDynFilterInit()
    print(f"LoadIdentifyDynFilterInit retval is: {retval}")
    retval = robot.LoadIdentifyDynVarInit()
    print(f"LoadIdentifyDynVarInit retval is: {retval}")
    error, posJ = robot.GetActualJointPosDegree(0)
    posJ[1] += 10  # Modifica giunto 2
    error, joint_toq = robot.GetJointTorques(0)
    joint_toq[1] += 2  # Modifica coppia giunto 2
    tmpTorque = joint_toq.copy()
    retval = robot.LoadIdentifyMain(tmpTorque, posJ, 1)
    print(f"LoadIdentifyMain retval is: {retval}")
    gain = [0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0]
    weight = [0.0]
    load_pos = [0.0, 0.0, 0.0]
    retval, weight, load_pos = robot.LoadIdentifyGetResult(gain)
    print(f"LoadIdentifyGetResult retval is: {retval} ; weight is {weight}  cog is {load_pos[0]} {load_pos[1]} {load_pos[2]}")
    robot.CloseRPC()

Trascinamento assistito da sensore di forza
++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``EndForceDragControl(status, asaptiveFlag, interfereDragFlag, ingularityConstraintsFlag, M, B, K, F, Fmax, Vmax, forceCollisionFlag=0)``"
    "Descrizione", "Trascinamento assistito da sensore di forza"
    "Parametri obbligatori", "- ``status``：stato controllo, 0-disattiva; 1-attiva
    - ``asaptiveFlag``：flag attivazione adattativo, 0-disattiva; 1-attiva
    - ``interfereDragFlag``：flag trascinamento zona interferenza, 0-disattiva; 1-attiva
    - ``ingularityConstraintsFlag``：strategia punti singolari, 0-evitare; 1-attraversare
    - ``forceCollisionFlag``：flag rilevamento collisione robot durante trascinamento assistito; 0-disattiva; 1-attiva
    - ``M=[m1,m2,m3,m4,m5,m6]``：coefficiente inerzia
    - ``B=[b1,b2,b3,b4,b5,b6]``：coefficiente smorzamento
    - ``K=[k1,k2,k3,k4,k5,k6]``：coefficiente rigidezza
    - ``F=[f1,f2,f3,f4,f5,f6]``：soglia forza sei dimensioni trascinamento
    - ``Fmax``：limite forza trascinamento massima
    - ``Vmax``：limite velocità giunti massima"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"
        
Ottenere stato interruttore trascinamento sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetForceAndTorqueDragState()``"
    "Descrizione", "Ottenere stato interruttore trascinamento sensore di forza"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice errore Successo-0  Fallimento- errcode
    - ``dragState``：stato controllo trascinamento assistito da sensore di forza, 0-disattiva; 1-attiva
    - ``sixDimensionalDragState``：stato controllo trascinamento assistito sei dimensioni, 0-disattiva; 1-attiva"
    
Attivazione automatica sensore di forza dopo cancellazione errore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForceSensorDragAutoFlag(status)``"
    "Descrizione", "Attivazione automatica sensore di forza dopo cancellazione errore"
    "Parametri obbligatori", "- ``status``：stato controllo, 0-disattiva; 1-attiva"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"
    
Esempio codice trascinamento assistito da sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    robot.SetForceSensorDragAutoFlag(1)
    M = [15.0, 15.0, 15.0, 0.5, 0.5, 0.1]
    B = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    K = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    F = [10.0, 10.0, 10.0, 1.0, 1.0, 1.0]
    robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100)
    time.sleep(5)
    drag_state = 0
    six_dimensional_drag_state = 0
    error,drag_state, six_dimensional_drag_state = robot.GetForceAndTorqueDragState()
    print(f"the drag state is {drag_state} {six_dimensional_drag_state}")
    robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100)
    robot.CloseRPC()
    
Impostare interruttore e parametri trascinamento misto sei dimensioni e impedenza giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ForceAndJointImpedanceStartStop(status, impedanceFlag, lamdeDain, KGain, BGain, dragMaxTcpVel, dragMaxTcpOriVel)``"
    "Descrizione", "Impostare interruttore e parametri trascinamento misto sei dimensioni e impedenza giunti"
    "Parametri obbligatori", "- ``status``：stato controllo, 0-disattiva; 1-attiva
    - ``impedanceFlag``：flag attivazione impedenza, 0-disattiva; 1-attiva
    - ``lamdeDain``：[D1,D2,D3,D4,D5, D6] guadagno trascinamento
    - ``KGain``：[K1,K2,K3,K4,K5,K6] guadagno rigidezza
    - ``BGain``：[B1,B2,B3,B4,B5,B] guadagno smorzamento
    - ``dragMaxTcpVel``：limite velocità lineare massima terminale trascinamento
    - ``dragMaxTcpOriVel``：limite velocità angolare massima terminale trascinamento"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice trascinamento misto sei dimensioni e impedenza giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    lamde_dain = [3.0, 2.0, 2.0, 2.0, 2.0, 3.0]
    k_gain = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    b_gain = [150.0, 150.0, 150.0, 5.0, 5.0, 1.0]
    rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    time.sleep(5)
    robot.DragTeachSwitch(0)
    rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamde_dain, k_gain, b_gain, 1000, 180)
    print(f"ForceAndJointImpedanceStartStop rtn is {rtn}")
    robot.CloseRPC()

Controllo avvio/arresto impedenza
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ImpedanceControlStartStop(status, workSpace, forceThreshold, m, b, k, maxV, maxVA, maxW, maxWA)``"
    "Descrizione", "Controllo avvio/arresto impedenza"
    "Parametri obbligatori", "- ``status``：0-disattiva; 1-attiva
    - ``workSpace``：0-spazio giunti; 1-spazio cartesiano
    - ``forceThreshold``：soglia forza attivazione (N)
    - ``m``：parametri massa
    - ``b``：parametri smorzamento
    - ``k``：parametri rigidezza
    - ``maxV``：velocità lineare massima (mm/s)
    - ``maxVA``：accelerazione lineare massima (mm/s2)
    - ``maxW``：velocità angolare massima (°/s)
    - ``maxWA``：accelerazione angolare massima (°/s2)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice controllo avvio/arresto impedenza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    j1 = [102.622, -135.990, 120.769, -73.950, -90.848, 35.507]
    j2 = [93.674, -80.062, 82.947, -92.199, -90.967, 26.559]
    desc_pos1 = [136.552, -149.799, 449.532, 179.817, -1.172, 157.123]
    desc_pos2 = [136.540, -561.048, 449.542, 179.819, -1.172, 157.122]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 200.0
    ovl = 100.0
    blendT = -1.0
    blendR = -1.0
    flag = 0
    search = 0
    robot.SetSpeed(20)
    company = 17
    device = 0
    softversion = 0
    bus = 1
    robot.FT_SetConfig(company, device, softversion, bus)
    time.sleep(1)
    rnt,[company, device, softversion, bus] = robot.FT_GetConfig()
    print(f"FT config:{company},{device},{softversion},{bus}")
    time.sleep(1)
    robot.FT_Activate(0)
    time.sleep(1)
    robot.FT_Activate(1)
    time.sleep(1)
    time.sleep(1)
    robot.FT_SetZero(0)
    time.sleep(1)
    robot.FT_SetZero(1)
    time.sleep(1)
    forceThreshold = [30.0, 30.0, 30.0, 5.0, 5.0, 5.0]
    m = [0.1, 0.1, 0.1, 0.02, 0.02, 0.02]
    b = [1.0, 1.0, 1.0, 0.08, 0.08, 0.08]
    k = [0.0] * 6
    rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    print(f"ImpedanceControlStartStop errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos1,tool= tool,user= user,vel= vel,speedPercent=1)
    rtn = robot.MoveL(desc_pos=desc_pos2,tool= tool,user= user,vel= vel,speedPercent=1)
    print(f"movel errcode:{rtn}")
    robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100)
    robot.CloseRPC()

Abilita Funzione di Compensazione Coppia e Coefficienti di Compensazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SerCoderCompenParams(status, torqueCoeff)``"
    "Descrizione", "Abilita Funzione di Compensazione Coppia e Coefficienti di Compensazione"
    "Parametri Obbligatori", "- ``status``：Interruttore, 0-Disabilita; 1-Abilitata
    - ``torqueCoeff``：Coefficienti di compensazione coppia J1-J6 [0-1]"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore 0-Successo  Errore- errcode"