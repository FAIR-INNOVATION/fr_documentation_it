Descrizione Strutture Dati
==========================

.. toctree:: 
    :maxdepth: 5

Pacchetto Dati Feedback Stato Controller
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.7
    
.. csv-table:: 
    :header-rows: 1
    :name: Pacchetto Dati Feedback Stato Controller
    :widths: 20 30

    "Variabile","Significato"
    "program_state","Stato esecuzione programma，1-Fermo; 2-In esecuzione; 3-In pausa"
    "robot_state","Stato movimento robot，1-Fermo; 2-In esecuzione; 3-In pausa; 4-Trascinamento"
    "main_code","Codice errore principale"
    "sub_code",	"Codice errore secondario"
    "robot_mode","Modalità robot，0-Modalità automatica; 1-Modalità manuale"
    "jt_cur_pos[i]","Posizione corrente giunto, unità deg,i:0~5"
    "tl_cur_pos[i]","Posa corrente utensile, unità deg&mm,i:0~5"
    "flange_cur_pos[i]","Posa corrente flangia terminale, unità deg&mm,i:0~5"
    "actual_qd[i]","Velocità corrente giunti robot, unità deg/s^2,i:0~5"
    "actual_qdd[i]","Accelerazione corrente giunti robot, unità mm/s,i:0~5"
    "target_TCP_CmpSpeed[i]","Velocità sintetica comando TCP robot, unità mm/s&deg/s,i:0~1"
    "target_TCP_Speed[i]","Velocità comando TCP robot, unità mm/s&deg/s,i:0~5"
    "actual_TCP_CmpSpeed[i]","Velocità sintetica effettiva TCP robot, unità mm/s&deg/s,i:0~1"
    "actual_TCP_Speed[i]","Velocità effettiva TCP robot, unità mm/s&deg/s,i:0~5"
    "jt_cur_tor[i]","Coppia corrente, unità N·m ,i:0~5"
    "tool","Numero sistema coordinate utensile applicato"
    "user","Numero sistema coordinate pezzo applicato"
    "cl_dgt_output_h","Uscita IO digitale pannello controllo 15-8"
    "cl_dgt_output_l","Uscita IO digitale pannello controllo 7-0"
    "tl_dgt_output_l","Uscita IO digitale utensile 7-0，solo bit0-bit1 validi"
    "dgt_input_h","Ingresso IO digitale pannello controllo 15-8"
    "cl_dgt_input_l","Ingresso IO digitale pannello controllo 7-0"
    "tl_dgt_input_l","Ingresso IO digitale utensile 7-0，solo bit0-bit1 validi"
    "cl_analog_input[i]","Ingresso analogico pannello controllo,i:0~2"
    "tl_anglog_input","Ingresso analogico utensile"
    "ft_sensor_raw_data","Dati grezzi sensore forza/coppia, unità N&Nm,i:0~5"
    "ft_sensor_data","Dati sensore forza/coppia, unità N&Nm,i:0~5"
    "ft_sensor_active","Stato attivazione sensore forza/coppia，0-Ripristino，1-Attivato"
    "EmergencyStop","Segnale arresto emergenza,0-Arresto emergenza non premuto,1-Arresto emergenza premuto"
    "motion_done","Segnale movimento a posizione,1-A posizione，0-Non a posizione"
    "gripper_motiondone","Segnale completamento movimento pinza,1-Completato，0-Non completato "
    "mc_queue_len","Lunghezza coda comandi movimento"
    "collisionState","Rilevamento collisione,1-Collisione，0-Nessuna collisione "
    "trajectory_pnum","Numero punto traiettoria"
    "safety_stop0_state","Segnale arresto sicurezza SI0"
    "safety_stop1_state","Segnale arresto sicurezza SI1"
    "gripper_fault_id","Numero pinza errore"
    "gripper_fault","Guasto pinza"
    "gripper_active","Stato attivazione pinza，0-Non attivato，1-Attivato"
    "gripper_position","Posizione pinza (percentuale)"
    "gripper_speed","Velocità pinza (percentuale)"
    "gripper_current","Corrente pinza (percentuale)"
    "gripper_tmp","Temperatura pinza, unità ℃"
    "gripper_voltage","Tensione pinza, unità V"
    "auxState.servoId","Asse espansione 485, Numero ID driver servomotore,i:0~3"
    "auxState.servoErrCode","Asse espansione 485, Codice errore driver servomotore,i:0~3"
    "auxState.servoState","Asse espansione 485, Stato driver servomotore,i:0~3"
    "auxState.servoPos","Asse espansione 485, Posizione corrente servomotore,i:0~3"
    "auxState.servoVel","Asse espansione 485, Velocità corrente servomotore,i:0~3"
    "auxState.servoTorque","Asse espansione 485, Coppia corrente servomotore,i:0~3"
    "extAxisStatus[i].pos","Asse espansione UDP, Posizione,i:0~3"
    "extAxisStatus[i].vel","Asse espansione UDP, Velocità,i:0~3"
    "extAxisStatus[i].errorCode","Asse espansione UDP, Codice errore,i:0~3"
    "extAxisStatus[i].ready","Asse espansione UDP, Servomotore pronto,i:0~3"
    "extAxisStatus[i].inPos","Asse espansione UDP, Servomotore a posizione,i:0~3"
    "extAxisStatus[i].alarm","Asse espansione UDP, Allarme servomotore,i:0~3"
    "extAxisStatus[i].flerr","Asse espansione UDP, Errore inseguimento,i:0~3"
    "extAxisStatus[i].nlimit","Asse espansione UDP, A limite negativo,i:0~3"
    "extAxisStatus[i].pLimit","Asse espansione UDP, A limite positivo,i:0~3"
    "extAxisStatus[i].mdbsOffLine","Asse espansione UDP, Bus 485 driver disconnesso"
    "extAxisStatus[i].mdbsTimeout","Asse espansione UDP, Timeout comunicazione 485 scheda controllo-pannello controllo"
    "extAxisStatus[i].homingStatus","Asse espansione UDP, Stato home"
    "extDIState","Stato ingressi digitali espansione"
    "extDOState","Stato uscite digitali espansione"
    "extAIState","Stato ingressi analogici espansione"
    "extAOState","Stato uscite analogiche espansione"
    "rbtEnableState","Stato abilitazione robot"
    "jointDriverTorque","Coppia corrente driver giunti"
    "jointDriverTemperature","Temperatura corrente driver giunti"
    "year","Anno"
    "mouth","Mese"
    "day","Giorno"
    "hour","Ora"
    "minute","Minuto"
    "second","Secondo"
    "millisecond","Millisecondo"
    "softwareUpgradeState","Stato aggiornamento software robot"
    "endLuaErrCode","Stato esecuzione LUA terminale"
    "cl_analog_output[i]","Uscita analogica pannello controllo,i:0~1"
    "tl_analog_output","Uscita analogica utensile"
    "gripperRotNum","Numero rotazioni corrente pinza rotante"
    "gripperRotSpeed","Velocità rotazione percentuale corrente pinza rotante"
    "gripperRotTorque","Coppia rotazione percentuale corrente pinza rotante"
    "weldingBreakOffState","Stato interruzione saldatura"
    "jt_tgt_tor","Coppia comando giunti"
    "smartToolState","Stato pulsante manopola SmartTool"
    "wideVoltageCtrlBoxTemp","Temperatura pannello controllo a tensione ampia"
    "wideVoltageCtrlBoxFanCurrent","Corrente ventilatore pannello controllo a tensione ampia (ma)"
    "toolCoord[i]","Sistema coordinate utensile,i:0~5"
    "wobjCoord[i]","Sistema coordinate pezzo,i:0~5"
    "extoolCoord[i]","Sistema coordinate utensile esterno,i:0~5"
    "exAxisCoord[i]","Sistema coordinate asse espansione,i:0~5"
    "load","Massa carico"
    "loadCog[i]","Baricentro carico,i:0~2"
    "lastServoTarget[i]","Ultima posizione obiettivo ServoJ in coda,i:0~5"
    "servoJCmdNum","Conteggio comandi ServoJ"

Stato Controller Servo
~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stato Controller Servo
    :widths: 20 30

    "Variabile","Significato"
    "servoId","Numero ID driver servomotore"
    "servoErrCode","Codice errore driver servomotore"
    "servoState","Stato driver servomotore"
    "servoPos","Posizione corrente servomotore"
    "servoVel","Velocità corrente servomotore"
    "servoTorque","Coppia corrente servomotore"

Stato Asse di Espansione
~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stato Asse di Espansione
    :widths: 20 30

    "Variabile","Significato"
    "pos","Posizione asse di espansione"
    "vel","Velocità asse di espansione"
    "errorCode","Codice errore asse di espansione"
    "ready","Servomotore pronto"
    "inPos","Servomotore a posizione"
    "alarm","Allarme servomotore"
    "flerr","Errore inseguimento"
    "nlimit","A limite negativo"
    "pLimit","A limite positivo"
    "mdbsOffLine","Bus 485 driver disconnesso"
    "mdbsTimeout","Timeout comunicazione 485 scheda controllo-pannello controllo"
    "homingStatus","Stato home asse di espansione"

Stato Interruzione Saldatura
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. versionadded:: python SDK-v2.1.3
    
.. csv-table:: 
    :header-rows: 1
    :name: Stato Interruzione Saldatura
    :widths: 20 30

    "Variabile","Significato"
    "breakOffState","Stato interruzione saldatura"
    "weldArcState","Stato interruzione arco saldatura"

Esempio di Codice
~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    print("program_state:", robot.robot_state_pkg.program_state)
    print("robot_state:", robot.robot_state_pkg.robot_state)
    print("main_code:", robot.robot_state_pkg.main_code)
    print("sub_code:", robot.robot_state_pkg.sub_code)
    print("robot_mode:", robot.robot_state_pkg.robot_mode)
    print("jt_cur_pos0:", robot.robot_state_pkg.jt_cur_pos[0])
    print("jt_cur_pos1:", robot.robot_state_pkg.jt_cur_pos[1])
    print("jt_cur_pos2:", robot.robot_state_pkg.jt_cur_pos[2])
    print("jt_cur_pos3:", robot.robot_state_pkg.jt_cur_pos[3])
    print("jt_cur_pos4:", robot.robot_state_pkg.jt_cur_pos[4])
    print("jt_cur_pos5:", robot.robot_state_pkg.jt_cur_pos[5])
    print("tl_cur_pos0:", robot.robot_state_pkg.tl_cur_pos[0])
    print("tl_cur_pos1:", robot.robot_state_pkg.tl_cur_pos[1])
    print("tl_cur_pos2:", robot.robot_state_pkg.tl_cur_pos[2])
    print("tl_cur_pos3:", robot.robot_state_pkg.tl_cur_pos[3])
    print("tl_cur_pos4:", robot.robot_state_pkg.tl_cur_pos[4])
    print("tl_cur_pos5:", robot.robot_state_pkg.tl_cur_pos[5])
    print("flange_cur_pos0:", robot.robot_state_pkg.flange_cur_pos[0])
    print("flange_cur_pos1:", robot.robot_state_pkg.flange_cur_pos[1])
    print("flange_cur_pos2:", robot.robot_state_pkg.flange_cur_pos[2])
    print("flange_cur_pos3:", robot.robot_state_pkg.flange_cur_pos[3])
    print("flange_cur_pos4:", robot.robot_state_pkg.flange_cur_pos[4])
    print("flange_cur_pos5:", robot.robot_state_pkg.flange_cur_pos[5])
    print("actual_qd0:", robot.robot_state_pkg.actual_qd[0])
    print("actual_qd1:", robot.robot_state_pkg.actual_qd[1])
    print("actual_qd2:", robot.robot_state_pkg.actual_qd[2])
    print("actual_qd3:", robot.robot_state_pkg.actual_qd[3])
    print("actual_qd4:", robot.robot_state_pkg.actual_qd[4])
    print("actual_qd5:", robot.robot_state_pkg.actual_qd[5])
    print("actual_qdd0:", robot.robot_state_pkg.actual_qdd[0])
    print("actual_qdd1:", robot.robot_state_pkg.actual_qdd[1])
    print("actual_qdd2:", robot.robot_state_pkg.actual_qdd[2])
    print("actual_qdd3:", robot.robot_state_pkg.actual_qdd[3])
    print("actual_qdd4:", robot.robot_state_pkg.actual_qdd[4])
    print("actual_qdd5:", robot.robot_state_pkg.actual_qdd[5])
    print("target_TCP_CmpSpeed0:", robot.robot_state_pkg.target_TCP_CmpSpeed[0])
    print("target_TCP_CmpSpeed1:", robot.robot_state_pkg.target_TCP_CmpSpeed[1])
    print("target_TCP_Speed0:", robot.robot_state_pkg.target_TCP_Speed[0])
    print("target_TCP_Speed1:", robot.robot_state_pkg.target_TCP_Speed[1])
    print("target_TCP_Speed2:", robot.robot_state_pkg.target_TCP_Speed[2])
    print("target_TCP_Speed3:", robot.robot_state_pkg.target_TCP_Speed[3])
    print("target_TCP_Speed4:", robot.robot_state_pkg.target_TCP_Speed[4])
    print("target_TCP_Speed5:", robot.robot_state_pkg.target_TCP_Speed[5])
    print("actual_TCP_CmpSpeed0:", robot.robot_state_pkg.actual_TCP_CmpSpeed[0])
    print("actual_TCP_CmpSpeed1:", robot.robot_state_pkg.actual_TCP_CmpSpeed[1])
    print("actual_TCP_Speed0:", robot.robot_state_pkg.actual_TCP_Speed[0])
    print("actual_TCP_Speed1:", robot.robot_state_pkg.actual_TCP_Speed[1])
    print("actual_TCP_Speed2:", robot.robot_state_pkg.actual_TCP_Speed[2])
    print("actual_TCP_Speed3:", robot.robot_state_pkg.actual_TCP_Speed[3])
    print("actual_TCP_Speed4:", robot.robot_state_pkg.actual_TCP_Speed[4])
    print("actual_TCP_Speed5:", robot.robot_state_pkg.actual_TCP_Speed[5])
    print("jt_cur_tor0:", robot.robot_state_pkg.jt_cur_tor[0])
    print("jt_cur_tor1:", robot.robot_state_pkg.jt_cur_tor[1])
    print("jt_cur_tor2:", robot.robot_state_pkg.jt_cur_tor[2])
    print("jt_cur_tor3:", robot.robot_state_pkg.jt_cur_tor[3])
    print("jt_cur_tor4:", robot.robot_state_pkg.jt_cur_tor[4])
    print("jt_cur_tor5:", robot.robot_state_pkg.jt_cur_tor[5])
    print("tool:", robot.robot_state_pkg.tool)
    print("user:", robot.robot_state_pkg.user)
    print("cl_dgt_output_h:", robot.robot_state_pkg.cl_dgt_output_h)
    print("cl_dgt_output_l:", robot.robot_state_pkg.cl_dgt_output_l)
    print("tl_dgt_output_l:", robot.robot_state_pkg.tl_dgt_output_l)
    print("cl_dgt_input_h:", robot.robot_state_pkg.cl_dgt_input_h)
    print("cl_dgt_input_l:", robot.robot_state_pkg.cl_dgt_input_l)
    print("tl_dgt_input_l:", robot.robot_state_pkg.tl_dgt_input_l)
    print("cl_analog_input0:", robot.robot_state_pkg.cl_analog_input[0])
    print("cl_analog_input1:", robot.robot_state_pkg.cl_analog_input[1])
    print("tl_anglog_input:", robot.robot_state_pkg.tl_anglog_input)
    print("ft_sensor_raw_data0:", robot.robot_state_pkg.ft_sensor_raw_data[0])
    print("ft_sensor_raw_data1:", robot.robot_state_pkg.ft_sensor_raw_data[1])
    print("ft_sensor_raw_data2:", robot.robot_state_pkg.ft_sensor_raw_data[2])
    print("ft_sensor_raw_data3:", robot.robot_state_pkg.ft_sensor_raw_data[3])
    print("ft_sensor_raw_data4:", robot.robot_state_pkg.ft_sensor_raw_data[4])
    print("ft_sensor_raw_data5:", robot.robot_state_pkg.ft_sensor_raw_data[5])
    print("ft_sensor_data0:", robot.robot_state_pkg.ft_sensor_data[0])
    print("ft_sensor_data1:", robot.robot_state_pkg.ft_sensor_data[1])
    print("ft_sensor_data2:", robot.robot_state_pkg.ft_sensor_data[2])
    print("ft_sensor_data3:", robot.robot_state_pkg.ft_sensor_data[3])
    print("ft_sensor_data4:", robot.robot_state_pkg.ft_sensor_data[4])
    print("ft_sensor_data5:", robot.robot_state_pkg.ft_sensor_data[5])
    print("ft_sensor_active:", robot.robot_state_pkg.ft_sensor_active)
    print("EmergencyStop:", robot.robot_state_pkg.EmergencyStop)
    print("motion_done:", robot.robot_state_pkg.motion_done)
    print("gripper_motiondone:", robot.robot_state_pkg.gripper_motiondone)
    print("mc_queue_len:", robot.robot_state_pkg.mc_queue_len)
    print("collisionState:", robot.robot_state_pkg.collisionState)
    print("trajectory_pnum:", robot.robot_state_pkg.trajectory_pnum)
    print("safety_stop0_state:", robot.robot_state_pkg.safety_stop0_state)
    print("safety_stop1_state:", robot.robot_state_pkg.safety_stop1_state)
    print("gripper_fault_id:", robot.robot_state_pkg.gripper_fault_id)
    print("gripper_fault:", robot.robot_state_pkg.gripper_fault)
    print("gripper_active:", robot.robot_state_pkg.gripper_active)
    print("gripper_position:", robot.robot_state_pkg.gripper_position)
    print("gripper_speed:", robot.robot_state_pkg.gripper_speed)
    print("gripper_current:", robot.robot_state_pkg.gripper_current)
    print("gripper_tmp:", robot.robot_state_pkg.gripper_tmp)
    print("gripper_voltage:", robot.robot_state_pkg.gripper_voltage)
    print("auxState.servoId:", robot.robot_state_pkg.auxState.servoId)
    print("auxState.servoErrCode:", robot.robot_state_pkg.auxState.servoErrCode)
    print("auxState.servoState:", robot.robot_state_pkg.auxState.servoState)
    print("auxState.servoPos:", robot.robot_state_pkg.auxState.servoPos)
    print("auxState.servoVel:", robot.robot_state_pkg.auxState.servoVel)
    print("auxState.servoTorque:", robot.robot_state_pkg.auxState.servoTorque)
    for i in range(4):
        print("extAxisStatus.pos:", i,robot.robot_state_pkg.extAxisStatus[i].pos)
        print("extAxisStatus.vel:", i,robot.robot_state_pkg.extAxisStatus[i].vel)
        print("extAxisStatus.errorCode:", i,robot.robot_state_pkg.extAxisStatus[i].errorCode)
        print("extAxisStatus.ready:", i,robot.robot_state_pkg.extAxisStatus[i].ready)
        print("extAxisStatus.inPos:", i,robot.robot_state_pkg.extAxisStatus[i].inPos)
        print("extAxisStatus.alarm:", i,robot.robot_state_pkg.extAxisStatus[i].alarm)
        print("extAxisStatus.flerr:", i,robot.robot_state_pkg.extAxisStatus[i].flerr)
        print("extAxisStatus.nlimit:", i,robot.robot_state_pkg.extAxisStatus[i].nlimit)
        print("extAxisStatus.pLimit:", i,robot.robot_state_pkg.extAxisStatus[i].pLimit)
        print("extAxisStatus.mdbsOffLine:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsOffLine)
        print("extAxisStatus.mdbsTimeout:", i,robot.robot_state_pkg.extAxisStatus[i].mdbsTimeout)
        print("extAxisStatus.homingStatus:", i,robot.robot_state_pkg.extAxisStatus[i].homingStatus)
    for i in range(8):
        print("extDIState:",i, robot.robot_state_pkg.extDIState[i])
        print("extDOState:", i,robot.robot_state_pkg.extDOState[i])
    for i in range(4):
        print("extAIState:", i,robot.robot_state_pkg.extAIState[i])
        print("extAOState:", robot.robot_state_pkg.extAOState[i])
    print("rbtEnableState:", robot.robot_state_pkg.rbtEnableState)
    print("jointDriverTorque0:", robot.robot_state_pkg.jointDriverTorque[0])
    print("jointDriverTorque1:", robot.robot_state_pkg.jointDriverTorque[1])
    print("jointDriverTorque2:", robot.robot_state_pkg.jointDriverTorque[2])
    print("jointDriverTorque3:", robot.robot_state_pkg.jointDriverTorque[3])
    print("jointDriverTorque4:", robot.robot_state_pkg.jointDriverTorque[4])
    print("jointDriverTorque5:", robot.robot_state_pkg.jointDriverTorque[5])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[0])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[1])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[2])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[3])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[4])
    print("jointDriverTemperature:", robot.robot_state_pkg.jointDriverTemperature[5])
    print("year:", robot.robot_state_pkg.year)
    print("mouth:", robot.robot_state_pkg.mouth)
    print("day:", robot.robot_state_pkg.day)
    print("hour:", robot.robot_state_pkg.hour)
    print("minute:", robot.robot_state_pkg.minute)
    print("second:", robot.robot_state_pkg.second)
    print("millisecond:", robot.robot_state_pkg.millisecond)
    print("softwareUpgradeState:", robot.robot_state_pkg.softwareUpgradeState)
    print("endLuaErrCode:", robot.robot_state_pkg.endLuaErrCode)
    print("cl_analog_output[0]:", robot.robot_state_pkg.cl_analog_output[0])
    print("cl_analog_output[1]:", robot.robot_state_pkg.cl_analog_output[1])
    print("tl_analog_output:", robot.robot_state_pkg.tl_analog_output)
    print("gripperRotNum:", robot.robot_state_pkg.gripperRotNum)
    print("gripperRotSpeed:", robot.robot_state_pkg.gripperRotSpeed)
    print("gripperRotTorque:", robot.robot_state_pkg.gripperRotTorque)
    print("jt_tgt_tor:", robot.robot_state_pkg.jt_tgt_tor)
    print("smartToolState:", robot.robot_state_pkg.smartToolState)
    print("wideVoltageCtrlBoxTemp:", robot.robot_state_pkg.wideVoltageCtrlBoxTemp)
    print("wideVoltageCtrlBoxFanCurrent:", robot.robot_state_pkg.wideVoltageCtrlBoxFanCurrent)
    print("toolCoord0:", robot.robot_state_pkg.toolCoord[0])
    print("toolCoord1:", robot.robot_state_pkg.toolCoord[1])
    print("toolCoord2:", robot.robot_state_pkg.toolCoord[2])
    print("toolCoord3:", robot.robot_state_pkg.toolCoord[3])
    print("toolCoord4:", robot.robot_state_pkg.toolCoord[4])
    print("toolCoord5:", robot.robot_state_pkg.toolCoord[5])
    print("wobjCoord0:", robot.robot_state_pkg.wobjCoord[0])
    print("wobjCoord1:", robot.robot_state_pkg.wobjCoord[1])
    print("wobjCoord2:", robot.robot_state_pkg.wobjCoord[2])
    print("wobjCoord3:", robot.robot_state_pkg.wobjCoord[3])
    print("wobjCoord4:", robot.robot_state_pkg.wobjCoord[4])
    print("wobjCoord5:", robot.robot_state_pkg.wobjCoord[5])
    print("extoolCoord0:", robot.robot_state_pkg.extoolCoord[0])
    print("extoolCoord1:", robot.robot_state_pkg.extoolCoord[1])
    print("extoolCoord2:", robot.robot_state_pkg.extoolCoord[2])
    print("extoolCoord3:", robot.robot_state_pkg.extoolCoord[3])
    print("extoolCoord4:", robot.robot_state_pkg.extoolCoord[4])
    print("extoolCoord5:", robot.robot_state_pkg.extoolCoord[5])
    print("exAxisCoord0:", robot.robot_state_pkg.exAxisCoord[0])
    print("exAxisCoord1:", robot.robot_state_pkg.exAxisCoord[1])
    print("exAxisCoord2:", robot.robot_state_pkg.exAxisCoord[2])
    print("exAxisCoord3:", robot.robot_state_pkg.exAxisCoord[3])
    print("exAxisCoord4:", robot.robot_state_pkg.exAxisCoord[4])
    print("exAxisCoord5:", robot.robot_state_pkg.exAxisCoord[5])
    print("load:", robot.robot_state_pkg.load)
    print("loadCog0:", robot.robot_state_pkg.loadCog[0])
    print("loadCog1:", robot.robot_state_pkg.loadCog[1])
    print("loadCog2:", robot.robot_state_pkg.loadCog[2])
    print("lastServoTarget0:", robot.robot_state_pkg.lastServoTarget[0])
    print("lastServoTarget1:", robot.robot_state_pkg.lastServoTarget[1])
    print("lastServoTarget2:", robot.robot_state_pkg.lastServoTarget[2])
    print("lastServoTarget3:", robot.robot_state_pkg.lastServoTarget[3])
    print("lastServoTarget4:", robot.robot_state_pkg.lastServoTarget[4])
    print("lastServoTarget5:", robot.robot_state_pkg.lastServoTarget[5])
    print("servoJCmdNum:", robot.robot_state_pkg.servoJCcmdNum)