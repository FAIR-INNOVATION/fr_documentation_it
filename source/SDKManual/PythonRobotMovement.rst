Movimento del Robot
===========================

.. toctree:: 
    :maxdepth: 5

Jog Inching
+++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``StartJOG(ref,nb,dir,max_dis,vel=20.0,acc=100.0)``"
    "Descrizione", "Jog inching"
    "Parametri obbligatori", "- ``ref``：0-joint inching,2-sistema base inching,4-sistema utensile inching,8-sistema pezzo inching；
    - ``nb``：1-1° giunto(asse x),2-2° giunto(asse y),3-3° giunto(asse z),4-4° giunto(rx),5-5° giunto(ry),6-6° giunto(rz);
    - ``dir``：0-direzione negativa，1-direzione positiva;
    - ``max_dis``：angolo/distanza massimo singolo inching，unità ° o mm;"
    "Parametri predefiniti", "- ``vel``：percentuale velocità，[0~100] default 20;
    - ``acc``：percentuale accelerazione，[0~100] default 100;"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Arresto decelerazione jog inching
+++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``StopJOG(ref)``"
    "Descrizione", "Arresto decelerazione jog inching"
    "Parametri obbligatori", "- ``ref``：1-arresto joint inching,3-arresto sistema base inching,5-arresto sistema utensile inching,9-arresto sistema pezzo inching"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Arresto immediato jog inching
+++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ImmStopJOG()``"
    "Descrizione", "Arresto immediato jog inching"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice controllo inching robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    for i in range(6):
        robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.ImmStopJOG()
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(5)
        time.sleep(1)
    for i in range(6):
        robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0)
        time.sleep(1)
        robot.StopJOG(9)
        time.sleep(1)
    robot.CloseRPC()

Movimento spazio giunti
+++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveJ(joint_pos, tool, user, desc_pos = [0.0,0.0,0.0,0.0,0.0,0.0], vel = 20.0, acc = 0.0, ovl = 100.0, exaxis_pos = [0.0,0.0,0.0,0.0], blendT = -1.0, offset_flag = 0, offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descrizione", "Movimento spazio giunti"
    "Parametri obbligatori", "- ``joint_pos``: posizione giunti target，unità[°]；
    - ``tool``: numero utensile，[0~14]；
    - ``user``: numero pezzo，[0~14]；"
    "Parametri predefiniti", "- ``desc_pos``: posa cartesiana target，unità [mm][°] default valore iniziale [0.0,0.0,0.0,0.0,0.0,0.0]，valore default chiamata cinematica diretta restituisce valore;
    - ``vel``: percentuale velocità，[0~100] default 20.0;
    - ``acc``: percentuale accelerazione，[0~100]，non aperto attualmente；
    - ``ovl``: fattore scala velocità，[0~100] default 100.0;
    - ``exaxis_pos``: asse esterno 1 posizione ~ asse esterno 4 posizione default [0.0,0.0,0.0,0.0];
    - ``blendT``:[-1.0]-movimento a posizione (bloccante)，[0~500.0]-tempo smooth (non bloccante)，unità [ms] default -1.0;
    - ``offset_flag``:[0]-nessun offset，[1]-offset sistema pezzo/base，[2]-offset sistema utensile default 0;
    - ``offset_pos``: quantità offset posa，unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0];"
    "Valore restituito", "Codice errore  Successo-0  Fallimento- errcode"

Movimento Lineare nello Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveL(desc_pos, tool, user, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0,blendR=-1.0, blendMode = 0,exaxis_pos=[0.0, 0.0, 0.0, 0.0], search=0, offset_flag=0,offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],oacc = 100.0,config=-1,velAccParamMode=0,overSpeedStrategy=0,speedPercent=10)``"
    "Descrizione", "Movimento Lineare nello Spazio Cartesiano"
    "Parametri Obbligatori", "- ``desc_pos``: Posa cartesiana target, unità [mm][°]；
    - ``tool``: Numero utensile, [0~14]；
    - ``user``: Numero pezzo/utente, [0~14]；"
    "Parametri Predefiniti", "- ``joint_pos``: Posizioni target dei giunti, unità [°] Valore iniziale predefinito è [0.0,0.0,0.0,0.0,0.0,0.0], valore predefinito è il risultato della cinematica inversa；
    - ``vel``: Percentuale di velocità, [0~100] Predefinito 20.0；
    - ``acc``: Percentuale di accelerazione, [0~100], attualmente non disponibile Predefinito 0.0；
    - ``ovl``: Fattore di scala velocità, [0~100] Predefinito 100.0；
    - ``blendR``:[-1.0]-Blocca fino al completamento del movimento (bloccante), [0~1000]-Raggio di transizione (non bloccante), unità [mm] Predefinito -1.0；
    - ``blendMode``: Metodo di transizione; 0-Transizione tangente； 1-Transizione a spigolo, predefinito 0；
    - ``exaxis_pos``: Posizione asse esterno 1 ~ Posizione asse esterno 4 Predefinito [0.0,0.0,0.0,0.0]；
    - ``search``:[0]-Nessuna ricerca filo, [1]-Ricerca filo；
    - ``offset_flag``:[0]-Nessuno scostamento, [1]-Scostamento nel sistema di coordinate pezzo/base, [2]-Scostamento nel sistema di coordinate utensile Predefinito 0；
    - ``offset_pos``: Valore di scostamento della posa, unità [mm][°] Predefinito [0.0,0.0,0.0,0.0,0.0,0.0]；
    - ``oacc``: Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²) Predefinito 100；
    - ``config``: Configurazione spazio giunti per soluzione inversa, [-1]-Risolvi con riferimento alle posizioni correnti dei giunti, [0~7]-Risolvi secondo una specifica configurazione dello spazio giunti, predefinito -1
    - ``velAccParamMode``: Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²) Predefinito 0
    - ``overSpeedStrategy``: Strategia di gestione sovravelocità, 0-Strategia disabilitata; 1-Standard; 2-Ferma con errore in caso di sovravelocità; 3-Riduzione adattiva della velocità, predefinito 0
    - ``speedPercent``: Percentuale di soglia di riduzione velocità consentita [0-100], predefinito 10%
    "
    "Valore di Ritorno", "Codice di errore 0-Successo  Errore- errcode"

Movimento ad Arco Circolare nello Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveC(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=100.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], offset_flag_p=0,offset_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_t=20.0, acc_t=100.0, exaxis_pos_t=[0.0, 0.0, 0.0, 0.0], offset_flag_t=0,offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],ovl=100.0, blendR=-1.0,oacc=100.0,config=-1,velAccParamMode=0)``"
    "Descrizione", "Movimento ad Arco Circolare nello Spazio Cartesiano"
    "Parametri Obbligatori", "- ``desc_pos_p``: Posa cartesiana del punto di percorso, unità [mm][°]；
    - ``tool_p``: Numero utensile del punto di percorso, [0~14];
    - ``user_p``: Numero pezzo/utente del punto di percorso, [0~14];
    - ``desc_pos_t``: Posa cartesiana del punto target, unità [mm][°];
    - ``tool_t``: Numero utensile, [0~14]；
    - ``user_t``: Numero pezzo/utente, [0~14]；"
    "Parametri Predefiniti", "- ``joint_pos_p``: Posizioni dei giunti del punto di percorso, unità [°] Valore iniziale predefinito è [0.0,0.0,0.0,0.0,0.0,0.0], valore predefinito è il risultato della cinematica inversa;
    - ``joint_pos_t``: Posizioni dei giunti del punto target, unità [°] Valore iniziale predefinito è [0.0,0.0,0.0,0.0,0.0,0.0], valore predefinito è il risultato della cinematica inversa;
    - ``vel_p``: Percentuale di velocità del punto di percorso, [0~100] Predefinito 20.0;
    - ``acc_p``: Percentuale di accelerazione del punto di percorso, [0~100] Attualmente non disponibile, predefinito 0.0;
    - ``exaxis_pos_p``: Posizione asse esterno 1 del punto di percorso ~ Posizione asse esterno 4 Predefinito [0.0,0.0,0.0,0.0];
    - ``offset_flag_p``: Se il punto di percorso è scostato [0]-Nessuno scostamento, [1]-Scostamento nel sistema di coordinate pezzo/base, [2]-Scostamento nel sistema di coordinate utensile Predefinito 0;
    - ``vel_t``: Percentuale di velocità del punto target, [0~100] Predefinito 20.0;
    - ``acc_t``: Percentuale di accelerazione del punto target, [0~100] Attualmente non disponibile predefinito 0.0;
    - ``exaxis_pos_t``: Posizione asse esterno 1 del punto target ~ Posizione asse esterno 4 Predefinito [0.0,0.0,0.0,0.0];
    - ``offset_flag_t``: Se il punto target è scostato [0]-Nessuno scostamento, [1]-Scostamento nel sistema di coordinate pezzo/base, [2]-Scostamento nel sistema di coordinate utensile Predefinito 0;
    - ``offset_pos_t``: Valore di scostamento della posa del punto target, unità [mm][°] Predefinito [0.0,0.0,0.0,0.0,0.0,0.0];
    - ``ovl:``: Fattore di scala velocità, [0~100] Predefinito 100.0;
    - ``blendR``:[-1.0]-Blocca fino al completamento del movimento (bloccante), [0~1000]-Raggio di transizione (non bloccante), unità [mm] Predefinito -1.0;
    - ``oacc``: Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²) Predefinito 100;
    - ``config``: Configurazione spazio giunti per soluzione inversa, [-1]-Risolvi con riferimento alle posizioni correnti dei giunti, [0~7]-Risolvi secondo una specifica configurazione dello spazio giunti, predefinito -1;
    - ``velAccParamMode``: Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²) Predefinito 0"
    "Valore di Ritorno", "Codice di errore 0-Successo  Errore- errcode"

Movimento Circolare Completo nello Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``Circle(desc_pos_p, tool_p, user_p, desc_pos_t, tool_t, user_t, joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=0.0, exaxis_pos_p=[0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=0.0,exaxis_pos_t=[0.0, 0.0, 0.0, 0.0],ovl=100.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], oacc=100.0, blendR=-1,config=-1,velAccParamMode=0)``"
    "Descrizione", "Movimento Circolare Completo nello Spazio Cartesiano"
    "Parametri Obbligatori", "- ``desc_pos_p``: Posa cartesiana del punto di percorso, unità [mm][°]；
    - ``tool_p``: Numero utensile, [0~14]；
    - ``user_p``: Numero pezzo/utente, [0~14]；
    - ``desc_pos_t``: Posa cartesiana del punto target, unità [mm][°]；
    - ``tool_t``: Numero utensile, [0~14]；
    - ``user_t``: Numero pezzo/utente, [0~14]；"
    "Parametri Predefiniti", "- ``joint_pos_p``: Posizioni dei giunti del punto di percorso, unità [°] Valore iniziale predefinito è [0.0,0.0,0.0,0.0,0.0,0.0], valore predefinito è il risultato della cinematica inversa;
    - ``joint_pos_t``: Posizioni dei giunti del punto target, unità [°] Valore iniziale predefinito è [0.0,0.0,0.0,0.0,0.0,0.0], valore predefinito è il risultato della cinematica inversa;
    - ``vel_p``: Percentuale di velocità, [0~100] Predefinito 20.0;
    - ``acc_p``: Percentuale di accelerazione del punto di percorso, [0~100] Attualmente non disponibile predefinito 0.0;
    - ``exaxis_pos_p``: Posizione asse esterno 1 del punto di percorso ~ Posizione asse esterno 4 Predefinito [0.0,0.0,0.0,0.0];
    - ``vel_t``: Percentuale di velocità del punto target, [0~100] Predefinito 20.0;
    - ``acc_t``: Percentuale di accelerazione del punto target, [0~100] Attualmente non disponibile predefinito 0.0;
    - ``exaxis_pos_t``: Posizione asse esterno 1 del punto target ~ Posizione asse esterno 4 Predefinito [0.0,0.0,0.0,0.0]
    - ``ovl``: Fattore di scala velocità, [0~100] Predefinito 100.0;
    - ``offset_flag``: Se scostare [0]-Nessuno scostamento, [1]-Scostamento nel sistema di coordinate pezzo/base, [2]-Scostamento nel sistema di coordinate utensile Predefinito 0;
    - ``offset_pos``: Valore di scostamento della posa, unità [mm][°] Predefinito [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``oacc``: Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²), predefinito: 100；
    - ``blendR``:-1：Bloccante；0~1000：Raggio di transizione, predefinito: -1；
    - ``config``: Configurazione spazio giunti per soluzione inversa, [-1]-Risolvi con riferimento alle posizioni correnti dei giunti, [0~7]-Risolvi secondo una specifica configurazione dello spazio giunti, predefinito -1;
    - ``velAccParamMode``: Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²) Predefinito 0"
    "Valore di Ritorno", "Codice di errore 0-Successo  Errore- errcode"

Movimento punto a punto spazio cartesiano
++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveCart(desc_pos, tool, user, vel = 20.0, acc = 0.0, ovl = 100.0, blendT = -1.0, config = -1)``"
    "Descrizione", "Movimento punto a punto spazio cartesiano"
    "Parametri obbligatori", "- ``desc_pos``: posizione cartesiana target；
    - ``tool``: numero utensile，[0~14]；
    - ``user``: numero pezzo，[0~14]；"
    "Parametri predefiniti", "- ``vel``: velocità，range [0~100]，default 20.0;
    - ``acc``: accelerazione，range [0~100]，non aperto attualmente, default 0.0;
    - ``ovl``: fattore scala velocità，[0~100]，default 100.0;
    - ``blendT``:[-1.0]-movimento a posizione (bloccante)，[0~500]-tempo smooth (non bloccante)，unità [ms] default -1.0;
    - ``config``: configurazione giunti，[-1]-soluzione riferimento posizione giunti corrente，[0~7]-soluzione basata configurazione giunti default -1"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice comandi movimento base robot
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    j4 = [-31.154, -95.317, 94.276, -88.079, -89.740, 74.256]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    desc_pos4 = [-443.165, 147.881, 480.951, 179.511, -0.775, -15.409]
    offset_pos = [0.0] * 6
    epos = [0.0] * 4
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    oacc = 100.0
    blendT = 0.0
    blendR = 0.0
    flag = 0
    search = 0
    blendMode = 0
    velAccMode = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos,oacc=oacc, velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel,acc_t=acc, exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, oacc=oacc, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl,offset_flag=flag, offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    rtn = robot.MoveCart(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, acc=acc,ovl=ovl, blendT=blendT, config=-1)
    print(f"MoveCart errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.MoveL(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, blendR=blendR, blendMode=blendMode, exaxis_pos=epos, search=search, offset_flag=flag, offset_pos=offset_pos, config=-1,velAccParamMode=velAccMode)
    print(f"movel errcode:{rtn}")
    rtn = robot.MoveC(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, offset_flag_p=flag, offset_pos_p=offset_pos, desc_pos_t=desc_pos4, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc,exaxis_pos_t=epos, offset_flag_t=flag, offset_pos_t=offset_pos, ovl=ovl, blendR=blendR, config=-1, velAccParamMode=velAccMode)
    print(f"movec errcode:{rtn}")
    rtn = robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
    print(f"movej errcode:{rtn}")
    rtn = robot.Circle(desc_pos_p=desc_pos3, tool_p=tool, user_p=user, vel_p=vel, acc_p=acc, exaxis_pos_p=epos, desc_pos_t=desc_pos1, tool_t=tool, user_t=user, vel_t=vel, acc_t=acc, exaxis_pos_t=epos, ovl=ovl, offset_flag=flag,offset_pos=offset_pos, oacc=oacc, blendR=-1, velAccParamMode=velAccMode)
    print(f"circle errcode:{rtn}")
    robot.CloseRPC()
    return 0

Movimento spirale spazio cartesiano
++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSpiral(desc_pos, tool, user, param, joint_pos = [0.0,0.0,0.0,0.0,0.0,0.0], vel = 20.0, acc = 0.0, exaxis_pos = [0.0,0.0,0.0,0.0], ovl = 100.0, offset_flag = 0, offset_pos = [0.0,0.0,0.0,0.0,0.0,0.0], config = -1)``"
    "Descrizione", "Movimento spirale spazio cartesiano"
    "Parametri obbligatori", "- ``desc_pos``: posa cartesiana target，unità[mm][°];
    - ``tool``: numero utensile，[0~14];
    - ``user``: numero pezzo，[0~14];
    - ``param=[circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]``：circle_num: numero giri spirale;circle_angle: angolo inclinazione spirale;rad_init: raggio iniziale spirale;rad_add: incremento raggio;rotaxis_add: incremento direzione asse rotazione;rot_direction: direzione rotazione，0-orario，1-antiorario, velAccMode modalità parametri velocità accelerazione：0-velocità angolare costante，1-velocità lineare costante;"
    "Parametri predefiniti", "- ``joint_pos``: posizione giunti target，unità [°] default valore iniziale [0.0,0.0,0.0,0.0,0.0,0.0]，valore default chiamata cinematica inversa restituisce valore;
    - ``vel``: percentuale velocità，[0~100] default 20.0;
    - ``acc``: percentuale accelerazione，[0~100] default 100.0;
    - ``exaxis_pos``: asse esterno 1 posizione ~ asse esterno 4 posizione default [0.0,0.0,0.0,0.0];
    - ``ovl``: fattore scala velocità，[0~100] default 100.0;
    - ``offset_flag``:[0]-nessun offset，[1]-offset sistema pezzo/base，[2]-offset sistema utensile default 0;
    - ``offset_pos``: quantità offset posa，unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0]
    - ``config``: configurazione spazio giunti cinematica inversa，[-1]-calcolo riferimento posizione giunti corrente，[0~7]-soluzione basata specifica configurazione spazio giunti，default -1"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice
++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    j = [67.957, -81.482, 87.595, -95.691, -94.899, -9.727]
    desc_pos = [-123.142, -551.735, 430.549, 178.753, -4.757, 167.754]
    offset_pos1 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    offset_pos2 = [50.0, 0.0, 0.0, -30.0, 0.0, 0.0]
    epos = [0.0] * 4
    sp = [2, 30.0, 50.0, 10.0, 10.0, 0, 1]  # [circle_num, circle_angle, rad_init, rad_add, rotaxis_add, rot_direction, velAccMode]
    tool = 0
    user = 0
    vel = 30.0
    acc = 60.0
    ovl = 100.0
    blendT = -1.0
    flag = 2
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j, tool=tool, user=user, vel=vel, acc=acc, ovl=ovl, exaxis_pos=epos, blendT=blendT, offset_flag=flag, offset_pos=offset_pos1)
    print(f"movej errcode:{rtn}")
    rtn = robot.NewSpiral(desc_pos=desc_pos, tool=tool, user=user, vel=vel, acc=acc, exaxis_pos=epos, ovl=ovl, offset_flag=flag, offset_pos=offset_pos2, param=sp)
    print(f"newspiral errcode:{rtn}")
    robot.CloseRPC()
    return 0

Inizio movimento servo
++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMoveStart()``"
    "Descrizione", "Inizio movimento servo，utilizzato con comandi ServoJ、ServoCart"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Fine movimento servo
++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoMoveEnd()``"
    "Descrizione", "Fine movimento servo，utilizzato con comandi ServoJ、ServoCart"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Movimento modalità servo spazio giunti
++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJ(joint_pos, axisPos, acc = 0.0, vel = 0.0, cmdT = 0.008, filterT = 0.0, gain = 0.0, id=0)``"
    "Descrizione", "Movimento modalità servo spazio giunti"
    "Parametri obbligatori", "- ``joint_pos``: posizione giunti target，unità[°]；
    - ``axisPos``: posizione asse esterno, unitàmm；"
    "Parametri predefiniti", "- ``acc``: accelerazione，range [0~100]，non aperto attualmente，default 0.0;
    - ``vel``: velocità，range [0~100]，non aperto attualmente，default 0.0;
    - ``cmdT``: periodo invio comando，unitàs，range consigliato [0.001~0.0016], default 0.008;
    - ``filterT``: tempo filtro，unità [s]，non aperto attualmente， default 0.0;
    - ``gain``: amplificatore proporzionale posizione target，non aperto attualmente， default 0.0;
    - ``id``: ID comando servoJ, default 0;"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Esempio codice movimento modalità servo spazio giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, restituisce oggetto robot se connesso con successo
    robot = Robot.RPC('192.168.58.2')
    j = [0.0] * 6
    epos = [0.0] * 4
    vel = 0.0
    acc = 0.0
    cmdT = 0.008
    filterT = 0.0
    gain = 0.0
    flag = 0
    count = 500
    dt = 0.1
    cmdID = 0
    ret, j = robot.GetActualJointPosDegree(flag)
    if ret == 0:
        cmdID += 1
        robot.ServoMoveStart()
        while count:
            robot.ServoJ(joint_pos=j,axisPos= epos,acc= acc,vel= vel, cmdT=cmdT, filterT=filterT, gain=gain, id=cmdID)
            j[4] += dt
            count -= 1
            time.sleep(cmdT)
            rtn,pkg = robot.GetRobotRealTimeState()
            print(f"Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")

            if count < 50:
                robot.MotionQueueClear()
                print(f"After queue clear, Servoj Count {pkg.servoJCmdNum}; last pos is {pkg.lastServoTarget[0]},{pkg.lastServoTarget[1]},{pkg.lastServoTarget[2]},{pkg.lastServoTarget[3]},{pkg.lastServoTarget[4]},{pkg.lastServoTarget[5]}")
                break
        robot.ServoMoveEnd()
    else:
        print(f"GetActualJointPosDegree errcode:{ret}")
    robot.CloseRPC()

Inizio controllo coppia giunti
++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJTStart()``"
    "Descrizione", "Inizio controllo coppia giunti"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice errore Successo-0  Fallimento- errcode"

Controllo Coppia Giunti
+++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJT(torque, interval, checkFlag=0, jPowerLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],jVelLimit=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Descrizione", "Controllo coppia giunti"
    "Parametri Obbligatori", "- ``torque``:coppia giunti j1~j6, unità Nm
                - ``interval``:periodo istruzione, unità s, range [0.001~0.008]
                - ``checkFlag``:strategia rilevamento 0-nessun limite; 1-limite potenza; 2-limite velocità; 3-limite potenza e velocità simultaneo, default 0
                - ``jPowerLimit``:parametro predefinito jPowerLimit limite potenza massima giunti (W), default [0.0,0.0,0.0,0.0,0.0,0.0]
                - ``jVelLimit``:velocità massima giunti (°/s), default [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Controllo Coppia Giunti
+++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoJTEnd()``"
    "Descrizione", "Fine controllo coppia giunti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Controllo Coppia Giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    robot.DragTeachSwitch(1)
    # torques = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error,torques = robot.GetJointTorques(1)
    robot.ServoJTStart()
    count = 100
    while count > 0:
        error = robot.ServoJT(torques, 0.001)
        count -= 1
        time.sleep(0.001)
    error = robot.ServoJTEnd()
    robot.DragTeachSwitch(0)
    robot.CloseRPC()

Movimento Modalità Servo Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ServoCart(mode, desc_pos, pos_gain = [1.0, 1.0, 1.0, 1.0, 1.0, 1.0] , acc = 0.0, vel = 0.0, cmdT = 0.008, filterT = 0.0, gain = 0.0)``"
    "Descrizione", "Movimento modalità servo spazio cartesiano"
    "Parametri Obbligatori", "- ``mode``:[0]-movimento assoluto (sistema base), [1]-movimento incrementale (sistema base), [2]-movimento incrementale (sistema utensile);
    - ``desc_pos``:posizione target cartesiana/incremento posizione target cartesiana;"
    "Parametri Predefiniti", "- ``pos_gain``:fattore proporzionale incremento posa, efficace solo movimento incrementale, range [0~1], default [1.0, 1.0, 1.0, 1.0, 1.0, 1.0];
    - ``acc``:accelerazione, range [0~100], non ancora disponibile, default 0.0;
    - ``vel``:velocità, range [0~100], non ancora disponibile, default 0.0;
    - ``cmdT``:periodo invio istruzione, unità s, range consigliato [0.001~0.0016], default 0.008;
    - ``filterT``:tempo filtro, unità [s], non ancora disponibile, default 0.0;
    - ``gain``:amplificatore proporzionale posizione target, non ancora disponibile, default 0.0;"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Movimento Modalità Servo Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    desc_pos_dt = [0.0,0.0,0.0,0.0,0.0,0.0]  # [x, y, z, rx, ry, rz]
    desc_pos_dt[2] = -0.5 
    pos_gain = [0.0, 0.0, 1.0, 0.0, 0.0, 0.0]
    mode = 2
    vel = 0.0
    acc = 0.0
    cmdT = 0.008
    filterT = 0.0 
    gain = 0.0 
    flag = 0
    count = 100 
    robot.SetSpeed(20)
    while count > 0:
        robot.ServoCart(mode=mode, desc_pos=desc_pos_dt, pos_gain=pos_gain, acc=acc, vel=vel, cmdT=cmdT, filterT=filterT, gain=gain)
        count -= 1
        time.sleep(cmdT)
    robot.CloseRPC()

Inizio Movimento Spline
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplineStart()``"
    "Descrizione", "Inizio movimento spline"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Movimento Spline PTP
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplinePTP(joint_pos, tool, user, desc_pos = [0.0,0.0,0.0,0.0,0.0,0.0],  vel = 20.0,  acc = 100.0, ovl = 100.0)``"
    "Descrizione", "Movimento spline PTP"
    "Parametri Obbligatori", "- ``joint_pos``:posizione target giunti, unità[°];
    - ``tool``:numero utensile, [0~14];
    - ``user``:numero pezzo, [0~14];"
    "Parametri Predefiniti", "- ``desc_pos``:posa target cartesiana, unità [mm][°] default valore iniziale [0.0,0.0,0.0,0.0,0.0,0.0], default chiama risultato calcolo cinematica diretta;
    - ``vel``:velocità, range [0~100], default 20.0;
    - ``acc``:accelerazione, range [0~100], default 100.0;
    - ``ovl``:fattore scala velocità, [0~100], default 100.0"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Movimento Spline
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SplineEnd()``"
    "Descrizione", "Fine movimento spline"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"
    
Esempio Codice Movimento Spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    joint_points = [
        [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256],  # j1
        [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255],  # j2
        [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260],  # j3
        [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]  # j4
    ]
    cart_points = [
        [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833],  # desc_pos1
        [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869],  # desc_pos2
        [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207],  # desc_pos3
        [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]  # desc_pos4
    ]
    offset_pos = [0] * 6 
    epos = [0] * 4 
    tool = user = 0
    vel = acc = ovl = 100.0 
    blendT = -1.0  
    flag = 0 
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=joint_points[0],tool=tool, user=user,vel=vel)
    print(f"MoveJ errore: {err1}")
    robot.SplineStart()
    robot.SplinePTP(joint_pos=joint_points[0],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[1],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[2],tool=tool, user=user)
    robot.SplinePTP(joint_pos=joint_points[3],tool=tool, user=user)
    robot.SplineEnd()
    robot.CloseRPC()

Inizio Nuovo Movimento Spline
+++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSplineStart(type,averageTime=2000)``"
    "Descrizione", "Inizio nuovo movimento spline"
    "Parametri Obbligatori", "- ``type``:0-transizione arco, 1-punti percorso dati"
    "Parametri Predefiniti", "- ``averageTime``:tempo medio transizione globale (ms) default 2000"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Punto Istruzione Nuova Spline
+++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``NewSplinePoint(desc_pos,tool,user,lastFlag,joint_pos=[0.0,0.0,0.0,0.0,0.0,0.0], vel = 0.0, acc = 0.0, ovl = 100.0 ,blendR = 0.0 )``"
    "Descrizione", "Punto istruzione nuova spline"
    "Parametri Obbligatori", "- ``desc_pos``:posa target cartesiana, unità [mm][°];
    - ``tool``:numero utensile, [0~14];
    - ``user``:numero pezzo, [0~14];
    - ``lastFlag``:se ultimo punto, 0-no, 1-sì;"
    "Parametri Predefiniti", "- ``joint_pos``:posizione target giunti, unità [°] default valore iniziale [0.0,0.0,0.0,0.0,0.0,0.0], default chiama risultato calcolo cinematica inversa;
    - ``vel``:velocità, range [0~100], non ancora disponibile, default 0.0;;
    - ``acc``:accelerazione, range [0~100], non ancora disponibile, default 0.0;
    - ``ovl``:fattore scala velocità, [0~100] default 100.0;
    - ``blendR``: [0~1000]-raggio smoothing, unità [mm] default 0.0;"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Nuovo Movimento Spline
+++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``NewSplineEnd()``"
    "Descrizione", "Fine nuovo movimento spline"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Nuovo Movimento Spline
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    j3 = [-61.954, -84.409, 108.153, -116.316, -91.283, 74.260]
    j4 = [-89.575, -80.276, 102.713, -116.302, -91.284, 74.267]
    j5 = [-95.228, -54.621, 73.691, -112.245, -91.280, 74.267]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    desc_pos3 = [-327.622, 402.230, 320.402, -178.067, 2.127, -46.207]
    desc_pos4 = [-104.066, 544.321, 327.023, -177.715, 3.371, -73.818]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    err1 = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    print(f"movej errore:{err1}")
    robot.NewSplineStart(1, 2000)
    robot.NewSplinePoint(desc_pos=desc_pos1, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos2, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos3, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos4, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplinePoint(desc_pos=desc_pos5, tool=tool, user=user, vel=vel, lastFlag=-1, blendR=0)
    robot.NewSplineEnd()
    robot.CloseRPC()

Terminazione Movimento Robot
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``StopMotion()``"
    "Descrizione", "Termina movimento, usare con istruzioni movimento non bloccanti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Pausa Movimento Robot
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PauseMotion()``"
    "Descrizione", "Pausa movimento, usare con istruzioni movimento non bloccanti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Ripresa Movimento Robot
++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``ResumeMotion()``"
    "Descrizione", "Riprende movimento, usare con istruzioni movimento non bloccanti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Pausa, Ripresa, Stop Movimento
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    j1 =[-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j5 =[-95.228, -54.621, 73.691, -112.245, -91.280, 74.268]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos5 = [-33.421, 732.572, 275.103, -177.907, 2.709, -79.482]
    offset_pos = [0, 0, 0, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    rtn = robot.MoveJ(joint_pos=j1, tool=tool, user=user, vel=vel)
    rtn = robot.MoveJ(joint_pos=j5, tool=tool, user=user, vel=vel, blendT=1)
    time.sleep(1)
    robot.PauseMotion()
    time.sleep(1)
    robot.ResumeMotion()
    time.sleep(1)
    robot.StopMotion()
    time.sleep(1)
    robot.CloseRPC()

Inizio Offset Globale Punti
+++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PointsOffsetEnable(flag,offset_pos)``"
    "Descrizione", "Inizio offset globale punti"
    "Parametri Obbligatori", "- ``flag``:0-offset in sistema base o pezzo, 2-offset in sistema utensile;
    - ``offset_pos``:valore offset, unità [mm][°]."
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Offset Globale Punti
+++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PointsOffsetDisable()``"
    "Descrizione", "Fine offset globale punti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Offset Punti
+++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 100.0
    acc = 100.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    time.sleep(1)
    robot.PointsOffsetEnable(flag=0, offset_pos=offset_pos1)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.PointsOffsetDisable()
    robot.CloseRPC()

Inizio Movimento AO Box Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveAOStart(AONum,maxTCPSpeed=1000,maxAOPercent=100,zeroZoneCmp=20)``"
    "Descrizione", "Inizio movimento AO box controllo"
    "Parametri Obbligatori", "- ``AONum``:numero AO box controllo"
    "Parametri Predefiniti", "
    - ``maxTCPSpeed``:valore massimo velocità TCP [1-5000mm/s], default 1000;
    - ``maxAOPercent``:percentuale AO corrispondente valore massimo velocità TCP, default 100%;
    - ``zeroZoneCmp``:valore compensazione zona morta percentuale AO, intero, default 20%, range [0-100]."
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Movimento AO Box Controllo
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveAOStop()``"
    "Descrizione", "Fine movimento AO box controllo"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Inizio Movimento AO Terminale
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveToolAOStart(AONum,maxTCPSpeed=1000,maxAOPercent=100,zeroZoneCmp =20)``"
    "Descrizione", "Inizio movimento AO terminale"
    "Parametri Obbligatori", "- ``AONum``:numero AO terminale"
    "Parametri Predefiniti", "
    - ``maxTCPSpeed``:valore massimo velocità TCP [1-5000mm/s], default 1000;
    - ``maxAOPercent``:percentuale AO corrispondente valore massimo velocità TCP, default 100%;
    - ``zeroZoneCmp``:valore compensazione zona morta percentuale AO, intero, default 20%, range [0-100]."
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Movimento AO Terminale
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``MoveToolAOStop()``"
    "Descrizione", "Fine movimento AO terminale"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"
      
Esempio Codice AO Fly Shoot
+++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    j1 = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    j2 = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    desc_pos1 = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    desc_pos2 = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    offset_pos = [0, 0, 0, 0, 0, 0]
    offset_pos1 = [0, 0, 50, 0, 0, 0]
    epos = [0, 0, 0, 0]
    tool = 0
    user = 0
    vel = 20.0
    acc = 20.0
    ovl = 100.0
    blendT = -1.0
    flag = 0
    robot.SetSpeed(20)
    robot.MoveAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveAOStop()
    time.sleep(1)
    robot.MoveToolAOStart(0, 100, 100, 20)
    robot.MoveJ(joint_pos=j1,tool=tool, user=user, vel=vel)
    robot.MoveJ(joint_pos=j2, tool=tool, user=user, vel=vel)
    robot.MoveToolAOStop()
    robot.CloseRPC()

Inizio Filtro FIR Movimento Ptp
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PtpFIRPlanningStart(maxAcc, maxJek)``"
    "Descrizione", "Inizio filtro FIR movimento Ptp"
    "Parametri Obbligatori", "- ``maxAcc``:valore estremo accelerazione massima (deg/s2)
    - ``maxJek``:valore estremo jerk giunti unificato (deg/s3)"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Filtro FIR Movimento Ptp
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``PtpFIRPlanningEnd()``"
    "Descrizione", "Fine filtro FIR movimento Ptp"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Inizio Filtro FIR Movimento LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``LinArcFIRPlanningStart(maxAccLin,maxAccDeg,maxJerkLin,maxJerkDeg)``"
    "Descrizione", "Inizio filtro FIR movimento LIN, ARC"
    "Parametri Obbligatori", "- ``maxAccLin``:valore estremo accelerazione lineare (mm/s2)
    - ``maxAccDeg``:valore estremo accelerazione angolare (deg/s2)
    - ``maxJerkLin``:valore estremo jerk lineare (mm/s3)
    - ``maxJerkDeg``:valore estremo jerk angolare (deg/s3)"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Fine Filtro FIR Movimento LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30
    
    "Prototipo", "``LinArcFIRPlanningEnd()``"
    "Descrizione", "Fine filtro FIR movimento LIN, ARC"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"   

Esempio Codice Filtro FIR
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    midjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    endjointPos = [-29.777, -84.536, 109.275, -114.075, -86.655, 74.257]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    middescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    enddescPose = [-487.434, 154.362, 308.576, 176.600, 0.268, -14.061]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.PtpFIRPlanningStart(1000.0, 1000.0)
    print(f"PtpFIRPlanningStart rtn is {rtn}")
    error = robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,desc_pos=startdescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    error = robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,desc_pos=enddescPose,vel= 100,acc=100,ovl=100, blendT=-1.0, offset_flag=0)
    print(f"MoveJ rtn is {rtn}")
    robot.PtpFIRPlanningEnd()
    print(f"PtpFIRPlanningEnd rtn is {rtn}")
    rtn = robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000)
    print(f"LinArcFIRPlanningStart rtn is {rtn}")
    error = robot.MoveL(desc_pos=startdescPose,tool= 0,user= 0, joint_pos=startjointPos,vel= 100,overSpeedStrategy=1,speedPercent=1)
    print(f"MoveL rtn is {rtn}")
    error = robot.MoveC(desc_pos_p=middescPose,tool_p= 0,user_p= 0, joint_pos_p=midjointPos,vel_p= 100,desc_pos_t=enddescPose,tool_t= 0,user_t= 0,joint_pos_t=endjointPos,vel_t= 100)
    print(f"MoveC rtn is {rtn}")
    robot.LinArcFIRPlanningEnd()
    print(f"LinArcFIRPlanningEnd rtn is {rtn}")
    robot.CloseRPC()

Attivazione Smoothing Accelerazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AccSmoothStart(saveFlag_flag)``"
    "Descrizione", "Attiva smoothing accelerazione"
    "Parametri Obbligatori", "- ``saveFlag_flag``：salvataggio dopo spegnimento"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Disattivazione Smoothing Accelerazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AccSmoothEnd(saveFlag_flag)``"
    "Descrizione", "Disattiva smoothing accelerazione"
    "Parametri Obbligatori", "- ``saveFlag_flag``：salvataggio dopo spegnimento"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Smoothing Accelerazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AccSmoothStart(0)
    print(f"AccSmoothStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos,tool= 0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos,tool= 0,user= 0,vel= 100)
    rtn = robot.AccSmoothEnd(0)
    print(f"AccSmoothEnd rtn is {rtn}")

Attivazione Velocità Orientamento Specifica Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AngularSpeedStart(ratio)``"
    "Descrizione", "Attiva velocità orientamento specifica"
    "Parametri Obbligatori", "- ``ratio``:percentuale velocità orientamento [0-300]"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode "

Disattivazione Velocità Orientamento Specifica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AngularSpeedEnd()``"
    "Descrizione", "Disattiva velocità orientamento specifica"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode "

Esempio Codice Velocità Orientamento Specifica Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.AngularSpeedStart(50)
    print(f"AngularSpeedStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.AngularSpeedEnd()
    print(f"AngularSpeedEnd rtn is {rtn}")
    robot.CloseRPC()

Attivazione Protezione Posizioni Singolari
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SingularAvoidStart(protectMode, minShoulderPos=100, minElbowPos=50, minWristPos=10)``"
    "Descrizione", "Attiva protezione posizioni singolari"
    "Parametri Obbligatori", "
    - ``protectMode``：modalità protezione posizioni singolari: 0-modalità giunti; 1-modalità cartesiana
    "
    "Parametri Predefiniti", "- ``minShoulderPos``：intervallo regolazione singolarità spalla (mm), default 100.0
    - ``minElbowPos``：intervallo regolazione singolarità gomito (mm), default 50.0
    - ``minWristPos``：intervallo regolazione singolarità polso (°), default 10.0"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Disattivazione Protezione Posizioni Singolari
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SingularAvoidEnd()``"
    "Descrizione", "Disattiva protezione posizioni singolari"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Esempio Codice Protezione Posizioni Singolari Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    startjointPos = [-11.904, -99.669, 117.473, -108.616, -91.726, 74.256]
    endjointPos = [-45.615, -106.172, 124.296, -107.151, -91.282, 74.255]
    startdescPose = [-419.524, -13.000, 351.569, -178.118, 0.314, 3.833]
    enddescPose = [-321.222, 185.189, 335.520, -179.030, -1.284, -29.869]
    exaxisPos = [0.0, 0.0, 0.0, 0.0]
    offdese = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SingularAvoidStart(2, 10, 5, 5)
    print(f"SingularAvoidStart rtn is {rtn}")
    robot.MoveJ(joint_pos=startjointPos, tool=0,user= 0,vel= 100)
    robot.MoveJ(joint_pos=endjointPos, tool=0,user= 0,vel= 100)
    rtn = robot.SingularAvoidEnd()
    print(f"SingularAvoidEnd rtn is {rtn}")
    robot.CloseRPC()

Svuotamento Coda Istruzioni Movimento
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MotionQueueClear()``"
    "Descrizione", "Svuota coda istruzioni movimento"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Movimento a Inizio Linea Intersecante
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveToIntersectLineStart(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveType,mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],extAxisFlag=0,exaxisPos=[0.0,0.0,0.0,0.0],moveDirection=0,offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descrizione", "Movimento a inizio linea intersecante"
    "Parametri Obbligatori", "
    - ``mainPoint``：6 pose cartesiane punti insegnamento tubo principale
    - ``piecePoint``：6 pose cartesiane punti insegnamento tubo secondario
    - ``tool``：numero sistema coordinate utensile
    - ``wobj``：numero sistema coordinate pezzo
    - ``vel``：percentuale velocità
    - ``acc``：percentuale accelerazione
    - ``ovl``：fattore scala velocità
    - ``oacc``：fattore scala accelerazione
    - ``moveType``：tipo movimento; 0-PTP; 1-LIN
    - ``mainExaxisPos``：posizioni assi estesi 6 punti insegnamento tubo principale, default[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``pieceExaxisPos``：posizioni assi estesi 6 punti insegnamento tubo secondario, default[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``extAxisFlag``：abilita assi estesi; 0-disabilitato; 1-abilitato
    - ``exaxisPos``：posizione assi estesi punto iniziale [0.0,0.0,0.0,0.0]
    - ``moveDirection``：direzione movimento; 0-orario; 1-antiorario
    - ``offset``：valore offset
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Movimento Linea Intersecante
+++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveIntersectLine(mainPoint, piecePoint, tool, wobj, vel, acc, ovl, oacc, moveDirection,mainExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],pieceExaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],extAxisFlag=0,exaxisPos=[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]],offset=[0.0,0.0,0.0,0.0,0.0,0.0])``"
    "Descrizione", "Movimento linea intersecante"
    "Parametri Obbligatori", "
    - ``mainPoint``：6 pose cartesiane punti insegnamento tubo principale
    - ``piecePoint``：6 pose cartesiane punti insegnamento tubo secondario
    - ``tool``：numero sistema coordinate utensile
    - ``wobj``：numero sistema coordinate pezzo
    - ``vel``：percentuale velocità
    - ``acc``：percentuale accelerazione
    - ``ovl``：fattore scala velocità
    - ``oacc``：fattore scala accelerazione
    - ``moveDirection``：direzione movimento; 0-orario; 1-antiorario
    - ``mainExaxisPos``：posizioni assi estesi 6 punti insegnamento tubo principale, default[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``pieceExaxisPos``：posizioni assi estesi 6 punti insegnamento tubo secondario, default[[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0],[0.0,0.0,0.0,0.0]]
    - ``extAxisFlag``：abilita assi estesi; 0-disabilitato; 1-abilitato
    - ``exaxisPos``：posizione assi estesi punto iniziale [0.0,0.0,0.0,0.0]
    - ``offset``：valore offset
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode"

Esempio Codice Movimento Linea Intersecante Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    mainPoint = [[0.0] * 6 for _ in range(6)]
    piecePoint = [[0.0] * 6 for _ in range(6)]
    mainExaxisPos = [[0.0] * 4 for _ in range(6)]
    pieceExaxisPos = [[0.0] * 4 for _ in range(6)]
    extAxisFlag = 1
    exaxisPos = [[0.0] * 4 for _ in range(4)]
    offset = [0.0, 2.0, 30.0, -2.0, 0.0, 0.0]
    mainPoint[0] = [490.004, -383.194, 402.735, -9.332, -1.528, 69.594]
    mainPoint[1] = [444.950, -407.117, 389.011, -5.546, -2.196, 65.279]
    mainPoint[2] = [445.168, -463.605, 355.759, -1.544, -10.886, 57.104]
    mainPoint[3] = [507.529, -485.385, 343.013, -0.786, -4.834, 61.799]
    mainPoint[4] = [554.390, -442.647, 367.701, -4.761, -10.181, 64.925]
    mainPoint[5] = [532.552, -394.003, 396.467, -13.732, -13.592, 67.411]
    mainExaxisPos[0] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[1] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[2] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[3] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[4] = [-29.996, 0.000, 0.000, 0.000]
    mainExaxisPos[5] = [-29.996, 0.000, 0.000, 0.000]
    piecePoint[0] = [505.571, -192.408, 316.759, 38.098, 37.051, 139.447]
    piecePoint[1] = [533.837, -201.558, 332.340, 34.644, 42.339, 137.748]
    piecePoint[2] = [530.386, -225.085, 373.808, 35.431, 45.111, 137.560]
    piecePoint[3] = [485.646, -229.195, 383.778, 33.870, 45.173, 137.064]
    piecePoint[4] = [460.551, -212.161, 354.256, 28.856, 45.602, 135.930]
    piecePoint[5] = [474.217, -197.124, 324.611, 42.469, 41.133, 148.167]
    pieceExaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[1] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[2] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[3] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[4] = [-29.996, -0.000, 0.000, 0.000]
    pieceExaxisPos[5] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[0] = [-29.996, -0.000, 0.000, 0.000]
    exaxisPos[1] = [-44.994, 90.000, 0.000, 0.000]
    exaxisPos[2] = [-59.992, 0.002, 0.000, 0.000]
    exaxisPos[3] = [-44.994, -89.997, 0.000, 0.000]
    tool = 2
    wobj = 0
    vel = 100.0
    acc = 100.0
    ovl = 12.0
    oacc = 12.0
    moveType = 1
    moveDirection = 1
    rtn = robot.MoveToIntersectLineStart(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag,exaxisPos=exaxisPos[0], tool=tool, wobj=wobj, vel=vel, acc=acc, ovl=ovl, oacc=oacc, moveType=moveType, moveDirection=moveDirection, offset=offset)
    print(f"MoveToIntersectLineStart rtn is {rtn}")
    rtn = robot.MoveIntersectLine(mainPoint=mainPoint, mainExaxisPos=mainExaxisPos, piecePoint=piecePoint, pieceExaxisPos=pieceExaxisPos, extAxisFlag=extAxisFlag, exaxisPos=exaxisPos, tool=tool,wobj=wobj, vel=vel, acc=acc, ovl=5.0, oacc=5.0, moveDirection=moveDirection, offset=offset)
    print(f"MoveIntersectLine rtn is {rtn}")
    robot.CloseRPC()

Movimento Aereo Stazionario
+++++++++++++++++++++++++++++++++
    
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MoveStationary()``"
    "Descrizione", "Movimento Aereo Stazionario"
    "Parametri Richiesti", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore. Successo - 0, Fallimento - errcode"
 
Esempio Codice Movimento Aereo Stazionario
++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 0, 10, 100)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    rtn = robot.MoveStationary()
    print(f"MoveStationary rtn is {rtn}")
    rtn = robot.LaserSensorRecord1(0, 10)
    print(f"LaserSensorRecordandReplay rtn is {rtn}")
    robot.CloseRPC()
    return 0

