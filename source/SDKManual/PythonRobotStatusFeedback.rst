Descrizione Strutture Dati
==========================

.. toctree:: 
    :maxdepth: 5

Tipo Struttura di Feedback di Stato del Robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:
    
    class ROBOT_AUX_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("servoId", c_uint8),         # Numero ID driver servo
            ("servoErrCode", c_int),     # Codice guasto driver servo
            ("servoState", c_int),       # Stato driver servo
            ("servoPos", c_double),      # Posizione corrente servo
            ("servoVel", c_float),       # Velocità corrente servo
            ("servoTorque", c_float),    # Coppia corrente servo
        ]

    class EXT_AXIS_STATUS(Structure):
        _pack_ = 1
        _fields_ = [
            ("pos", c_double),        # Posizione asse di estensione
            ("vel", c_double),        # Velocità asse di estensione
            ("errorCode", c_int),     # Codice guasto asse di estensione
            ("ready", c_uint8),        # Servo pronto
            ("inPos", c_uint8),        # Servo in posizione
            ("alarm", c_uint8),        # Allarme servo
            ("flerr", c_uint8),        # Errore di inseguimento
            ("nlimit", c_uint8),       # Limite negativo raggiunto
            ("pLimit", c_uint8),       # Limite positivo raggiunto
            ("mdbsOffLine", c_uint8),  # Bus 485 driver offline
            ("mdbsTimeout", c_uint8),  # Timeout comunicazione 485 tra scheda di controllo e box di controllo
            ("homingStatus", c_uint8), # Stato homing asse di estensione
        ]

    class WELDING_BREAKOFF_STATE(Structure):
        _pack_ = 1
        _fields_ = [
            ("breakOffState", c_uint8),        # Stato interruzione saldatura
            ("weldArcState", c_uint8),        # Stato interruzione arco di saldatura
        ]

    # ==================== Struttura Completa dello Stato del Robot ====================
    class RobotStatePkg(Structure):
        """
        Pacchetto dati di feedback di stato del robot
        """
        _pack_ = 1
        _fields_ = [
            # Informazioni intestazione frame
            ("frame_head", c_uint16),           # Intestazione frame, concordata come 0x5A5A
            ("frame_cnt", c_uint8),             # Conteggio frame, conteggio ciclico 0-255
            ("data_len", c_uint16),             # Lunghezza del contenuto dei dati
            ("program_state", c_uint8),         # Stato di esecuzione del programma, 1-arrestato; 2-in esecuzione; 3-in pausa
            ("robot_state", c_uint8),             # Stato di movimento del robot, 1-arrestato; 2-in movimento; 3-in pausa; 4-trascinamento
            ("main_code", c_int),               # Codice guasto principale
            ("sub_code", c_int),                # Codice guasto secondario
            ("robot_mode", c_uint8),            # Modalità robot, 1-manuale; 0-automatica

            # Posizioni e velocità dei giunti
            ("jt_cur_pos", c_double * 6),       # Posizioni articolari correnti di 6 assi, unità deg
            ("tl_cur_pos", c_double * 6),       # Posizione corrente utensile [x,y,z,rx,ry,rz]
            ("flange_cur_pos", c_double * 6),   # Posizione corrente flangia terminale [x,y,z,rx,ry,rz]
            ("actual_qd", c_double * 6),        # Velocità correnti di 6 giunti, unità deg/s
            ("actual_qdd", c_double * 6),       # Accelerazioni correnti di 6 giunti, unità deg/s^2
            ("target_TCP_CmpSpeed", c_double * 2),  # Velocità di comando composita TCP [posizione mm/s, orientamento deg/s]
            ("target_TCP_Speed", c_double * 6), # Velocità di comando TCP [x,y,z,rx,ry,rz]
            ("actual_TCP_CmpSpeed", c_double * 2),  # Velocità effettiva composita TCP [posizione mm/s, orientamento deg/s]
            ("actual_TCP_Speed", c_double * 6), # Velocità effettiva TCP [x,y,z,rx,ry,rz]
            ("jt_cur_tor", c_double * 6),       # Coppie correnti di 6 assi, unità N·m

            # Sistemi di coordinate utensile e pezzo
            ("tool", c_int),                    # Numero del sistema di coordinate utensile applicato
            ("user", c_int),                    # Numero del sistema di coordinate pezzo applicato

            # I/O digitale
            ("cl_dgt_output_h", c_uint8),       # Uscita IO digitale del box di controllo 15-8
            ("cl_dgt_output_l", c_uint8),       # Uscita IO digitale del box di controllo 7-0
            ("tl_dgt_output_l", c_uint8),       # Uscita IO digitale dell'utensile 7-0, solo bit0-bit1 validi
            ("cl_dgt_input_h", c_uint8),        # Ingresso IO digitale del box di controllo 15-8
            ("cl_dgt_input_l", c_uint8),        # Ingresso IO digitale del box di controllo 7-0
            ("tl_dgt_input_l", c_uint8),        # Ingresso IO digitale dell'utensile 7-0, solo bit0-bit1 validi

            # I/O analogico
            ("cl_analog_input", c_uint16 * 2),  # Ingresso analogico del box di controllo [0],[1]
            ("tl_anglog_input", c_uint16),      # Ingresso analogico dell'utensile

            # Sensore di forza/coppia
            ("ft_sensor_raw_data", c_double * 6),   # Dati grezzi del sensore di forza/coppia
            ("ft_sensor_data", c_double * 6),      # Dati del sensore di forza/coppia
            ("ft_sensor_active", c_uint8),          # Stato di attivazione del sensore di forza/coppia

            # Segnali di stato
            ("EmergencyStop", c_uint8),         # Flag di arresto di emergenza, 0-non premuto, 1-premuto
            ("motion_done", c_int),             # Segnale di movimento completato, 1-completato, 0-non completato
            ("gripper_motiondone", c_uint8),    # Segnale di movimento della pinza completato, 1-completato, 0-non completato
            ("mc_queue_len", c_int),            # Lunghezza della coda dei comandi di movimento
            ("collisionState", c_uint8),        # Rilevamento collisione, 1-collisione, 0-nessuna collisione
            ("trajectory_pnum", c_int),         # Numero del punto di traiettoria
            ("safety_stop0_state", c_uint8),    # Segnale di arresto di sicurezza SI0
            ("safety_stop1_state", c_uint8),    # Segnale di arresto di sicurezza SI1

            # Informazioni pinza
            ("gripper_fault_id", c_uint8),      # Numero pinza guasta
            ("gripper_fault", c_uint16),        # Guasto pinza
            ("gripper_active", c_uint16),      # Stato di attivazione della pinza
            ("gripper_position", c_uint8),      # Posizione della pinza
            ("gripper_speed", c_int8),          # Velocità della pinza
            ("gripper_current", c_int8),        # Corrente della pinza
            ("gripper_temp", c_int),            # Temperatura della pinza
            ("gripper_voltage", c_int),         # Tensione della pinza

            # Stato assi di estensione
            ("aux_axis_state", ROBOT_AUX_STATE * 25),    # Stato assi di estensione 485 (25)
            ("extAxisStatus", EXT_AXIS_STATUS * 4), # Stato assi di estensione UDP (4)

            # Stato I/O esteso
            ("extDIState", c_uint16 * 8),       # Ingresso DI esteso
            ("extDOState", c_uint16 * 8),       # Uscita DO estesa
            ("extAIState", c_uint16 * 4),        # Ingresso AI esteso
            ("extAOState", c_uint16 * 4),        # Uscita AO estesa

            # Stato robot e giunti
            ("rbtEnableState", c_int),                  # Stato di abilitazione del robot
            ("jointDriverTorque", c_double * 6),        # Coppia del driver dei giunti del robot
            ("jointDriverTemperature", c_double * 6),   # Temperatura del driver dei giunti del robot

            # Tempo del robot
            #("robotTime", c_int * 7),             # Tempo del sistema robot [anno,mese,giorno,ora,minuto,secondo,millisecondo]
            ("year", ctypes.c_uint16),  # Anno
            ("mouth", ctypes.c_uint8),  # Mese
            ("day", ctypes.c_uint8),   # Giorno
            ("hour", ctypes.c_uint8),   # Ora
            ("minute", ctypes.c_uint8), # Minuto
            ("second", ctypes.c_uint8), # Secondo
            ("millisecond", ctypes.c_uint16), # Millisecondo

            ("softwareUpgradeState", c_int),      # Stato di aggiornamento del software del robot
            ("endLuaErrCode", c_uint16),          # Stato di esecuzione Lua dell'estremità

            # Uscita analogica
            ("cl_analog_output", c_uint16 * 2), # Uscita analogica del box di controllo [0],[1]
            ("tl_analog_output", c_uint16),       # Uscita analogica dell'utensile

            # Pinza rotante
            ("gripperRotNum", c_float),         # Numero di giri corrente della pinza rotante
            ("gripperRotSpeed", c_uint8),       # Percentuale di velocità di rotazione corrente della pinza rotante
            ("gripperRotTorque", c_uint8),      # Percentuale di coppia di rotazione corrente della pinza rotante

            # Stato interruzione saldatura - utilizzo struttura
            ("weldingBreakOffState", WELDING_BREAKOFF_STATE),  # Stato interruzione saldatura

            # Coppia articolare target
            ("jt_tgt_tor", c_double * 6),       # Coppia di comando del giunto

            ("smartToolState", c_int),          # Stato del pulsante della maniglia SmartTool
            ("wideVoltageCtrlBoxTemp", c_float),        # Temperatura del box di controllo wide voltage
            ("wideVoltageCtrlBoxFanCurrent", c_uint16), # Corrente ventola del box di controllo wide voltage (mA)

            # Valori del sistema di coordinate
            ("toolCoord", c_double * 6),        # Valori correnti del sistema di coordinate utensile; x,y,z,rx,ry,rz
            ("wobjCoord", c_double * 6),        # Valori correnti del sistema di coordinate pezzo; x,y,z,rx,ry,rz
            ("extoolCoord", c_double * 6),      # Valori correnti del sistema di coordinate utensile esterno; x,y,z,rx,ry,rz
            ("exAxisCoord", c_double * 6),      # Valori correnti del sistema di coordinate assi di estensione; x,y,z,rx,ry,rz

            # Carico
            ("load", c_double),                 # Massa del carico
            ("loadCog", c_double * 3),            # Centro di gravità del carico

            # Comandi servo
            ("lastServoTarget", c_double * 6),  # Ultima posizione target ServoJ nella coda
            ("servoJCmdNum", c_int),            # Conteggio comandi ServoJ

            # Dati giunto target
            ("targetJointPos", c_double * 6),   # Posizione di comando di 6 giunti, unità °
            ("targetJointVel", c_double * 6),   # Velocità di comando di 6 giunti, unità °/s
            ("targetJointAcc", c_double * 6),   # Accelerazione di comando di 6 giunti, unità °/s2
            ("targetJointCurrent", c_double * 6), # Corrente di comando di 6 giunti, unità A
            ("actualJointCurrent", c_double * 6), # Corrente corrente di 6 giunti, unità A
            ("actualTCPForce", c_double * 6),   # Coppia dell'end-effector del robot Nm; x,y,z,rx,ry,rz
            ("targetTCPPos", c_double * 6),     # Posizione di comando TCP del robot mm; x,y,z,rx,ry,rz

            ("collisionLevel", c_uint8 * 6),    # Livello di collisione del robot
            ("speedScaleManual", c_double),     # Percentuale di velocità globale in modalità manuale
            ("speedScaleAuto", c_double),       # Percentuale di velocità globale in modalità automatica
            ("luaLineNum", c_int),              # Numero di riga corrente del programma Lua in esecuzione
            ("abnomalStop", c_uint8),           # 0-nessuna anomalia; 1-anomalia presente
            ("currentLuaFileName", c_uint8 * 256),  # Nome del programma Lua attualmente in esecuzione
            ("programTotalLine", c_uint8),      # Numero totale di righe del programma Lua
            ("safetyBoxSingal", c_uint8 * 6),   # Stato dei pulsanti del box pulsanti del robot

            # Dati saldatura
            ("weldVoltage", c_double),          # Tensione di saldatura V
            ("weldCurrent", c_double),          # Corrente di saldatura
            ("weldTrackVel", c_double),         # Velocità di inseguimento del cordone di saldatura mm/s

            ("tpdException", c_uint8),            # Conteggio di caricamento traiettoria TPD superato, 0-non superato, 1-superato
            ("alarmRebootRobot", c_uint8),      # Avviso, 1-rilasciare il pulsante di arresto di emergenza e riavviare il box di controllo, 2-anomalia di comunicazione del giunto, riavviare il box di controllo
            ("modbusMasterConnect", c_uint8),   # bit0-7 corrispondono allo stato di connessione dei master ModbusTCP 0-7
            ("modbusSlaveConnect", c_uint8),    # Stato di connessione slave ModbusTCP
            ("btnBoxStopSignal", c_uint8),      # Segnale di arresto di emergenza del box pulsanti
            ("dragAlarm", c_uint8),             # Avviso di trascinamento
            ("safetyDoorAlarm", c_uint8),       # Avviso porta di sicurezza
            ("safetyPlaneAlarm", c_uint8),      # Avviso di ingresso nella parete di sicurezza
            ("motonAlarm", c_uint8),            # Avviso di movimento
            ("interfaceAlarm", c_uint8),        # Avviso di ingresso nell'area di interferenza
            ("udpCmdState", c_int),             # Stato di connessione di comunicazione UDP della porta 20007
            ("weldReadyState", c_uint8),        # Stato di prontezza della saldatrice
            ("alarmCheckEmergStopBtn", c_uint8),    # 0-normale; 1-anomalia di comunicazione, verificare se il pulsante di arresto di emergenza è rilasciato
            ("tsTmCmdComError", c_uint8),       # 0-normale; 1-guasto comunicazione comando coppia
            ("tsTmStateComError", c_uint8),     # 0-normale; 1-guasto comunicazione stato coppia
            ("ctrlBoxError", c_int),            # Errore del box di controllo
            ("safetyDataState", c_uint8),       # Flag di stato dei dati di sicurezza
            ("forceSensorErrState", c_uint8),   # Guasto timeout connessione sensore di forza
            ("ctrlOpenLuaErrCode", c_uint8 * 4),  # 4 codici di errore del protocollo aperto del controller periferico
            ("strangePosFlag", c_uint8),        # Flag di posa singolare attuale
            ("alarm", c_uint8),                 # Avviso
            ("driverAlarm", c_uint8),           # Numero asse allarme driver
            ("aliveSlaveNumError", c_uint8),    # Errore conteggio slave attivi
            ("slaveComError", c_uint8 * 8),     # Stato errore slave
            ("cmdPointError", c_uint8),         # Errore punto di comando
            ("IOError", c_uint8),               # Errore IO
            ("gripperError", c_uint8),          # Errore pinza
            ("fileError", c_uint8),             # Errore file
            ("paraError", c_uint8),             # Errore parametro
            ("exaxisOutLimitError", c_uint8),   # Errore superamento limite morbido asse esterno
            ("driverComError", c_uint8 * 6),    # Guasto comunicazione driver
            ("driverError", c_uint8),           # Numero asse con guasto comunicazione driver
            ("outSoftLimitError", c_uint8),     # Guasto superamento limite morbido
            ("axleGenComData", c_uint8 * 130),   # Dati di comunicazione generale assi non periodici
            ("socketConnTimeout", c_uint8),     # Timeout connessione socket
            ("socketReadTimeout", c_uint8),     # Timeout lettura socket
            ("tsWebStateComErr", c_uint8),      # Errore comunicazione stato TS_WEB
            ("exaxisCoordID", c_uint8),         # ID dell'asse esteso esterno
            ("check_sum", c_uint16)          # Checksum
        ]

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
    "actual_qd[i]","Velocità corrente giunti robot, unità deg/s,i:0~5"
    "actual_qdd[i]","Accelerazione corrente giunti robot, unità deg/s^2,i:0~5"
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

Tipo di Enumerazione dell'Elenco di Configurazione del Feedback di Stato del Robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    # ==================== Enumerazione Elenco di Configurazione RobotState ====================
    class RobotState(enum.Enum):
        """Enumerazione del tipo di stato CNDE"""
        FrameHead = 0
        FrameCnt = 1
        DataLen = 2
        ProgramState = 3
        RobotState = 4
        MainCode = 5
        SubCode = 6
        RobotMode = 7
        JointCurPos = 8
        ToolCurPos = 9
        FlangeCurPos = 10
        ActualJointVel = 11
        ActualJointAcc = 12
        TargetTCPCmpSpeed = 13
        TargetTCPSpeed = 14
        ActualTCPCmpSpeed = 15
        ActualTCPSpeed = 16
        ActualJointTorque = 17
        Tool = 18
        User = 19
        ClDgtOutputH = 20
        ClDgtOutputL = 21
        TlDgtOutputL = 22
        ClDgtInputH = 23
        ClDgtInputL = 24
        TlDgtInputL = 25
        ClAnalogInput = 26
        TlAnglogInput = 27
        FtSensorRawData = 28
        FtSensorData = 29
        FtSensorActive = 30
        EmergencyStop = 31
        MotionDone = 32
        GripperMotiondone = 33
        McQueueLen = 34
        CollisionState = 35
        TrajectoryPnum = 36
        SafetyStop0State = 37
        SafetyStop1State = 38
        GripperFaultId = 39
        GripperFault = 40
        GripperActive = 41
        GripperPosition = 42
        GripperSpeed = 43
        GripperCurrent = 44
        GripperTemp = 45
        GripperVoltage = 46
        AuxState = 47
        ExtAxisStatus = 48
        ExtDIState = 49
        ExtDOState = 50
        ExtAIState = 51
        ExtAOState = 52
        RbtEnableState = 53
        JointDriverTorque = 54
        JointDriverTemperature = 55
        RobotTime = 56
        SoftwareUpgradeState = 57
        EndLuaErrCode = 58
        ClAnalogOutput = 59
        TlAnalogOutput = 60
        GripperRotNum = 61
        GripperRotSpeed = 62
        GripperRotTorque = 63
        WeldingBreakOffState = 64
        TargetJointTorque = 65
        SmartToolState = 66
        WideVoltageCtrlBoxTemp = 67
        WideVoltageCtrlBoxFanCurrent = 68
        ToolCoord = 69
        WobjCoord = 70
        ExtoolCoord = 71
        ExAxisCoord = 72
        Load = 73
        LoadCog = 74
        LastServoTarget = 75
        ServoJCmdNum = 76
        TargetJointPos = 77
        TargetJointVel = 78
        TargetJointAcc = 79
        TargetJointCurrent = 80
        ActualJointCurrent = 81
        ActualTCPForce = 82
        TargetTCPPos = 83
        CollisionLevel = 84
        SpeedScaleManual = 85
        SpeedScaleAuto = 86
        LuaLineNum = 87
        AbnomalStop = 88
        CurrentLuaFileName = 89
        ProgramTotalLine = 90
        SafetyBoxSingal = 91
        WeldVoltage = 92
        WeldCurrent = 93
        WeldTrackVel = 94
        TpdException = 95
        AlarmRebootRobot = 96
        ModbusMasterConnect = 97
        ModbusSlaveConnect = 98
        BtnBoxStopSignal = 99
        DragAlarm = 100
        SafetyDoorAlarm = 101
        SafetyPlaneAlarm = 102
        MotonAlarm = 103
        InterfaceAlarm = 104
        UdpCmdState = 105
        WeldReadyState = 106
        AlarmCheckEmergStopBtn = 107
        TsTmCmdComError = 108
        TsTmStateComError = 109
        CtrlBoxError = 110
        SafetyDataState = 111
        ForceSensorErrState = 112
        CtrlOpenLuaErrCode = 113
        StrangePosFlag = 114
        Alarm = 115
        DriverAlarm = 116
        AliveSlaveNumError = 117
        SlaveComError = 118
        CmdPointError = 119
        IOError = 120
        GripperError = 121
        FileError = 122
        ParaError = 123
        ExaxisOutLimitError = 124
        DriverComError = 125
        DriverError = 126
        OutSoftLimitError = 127
        AxleGenComData = 128
        SocketConnTimeout = 129
        SocketReadTimeout = 130
        TsWebStateComErr = 131
        exaxisCoordID = 132
        CheckSum = 133