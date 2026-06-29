Descrizione della Struttura Dati
================================

.. toctree:: 
    :maxdepth: 5

Tipo di Valore Restituito dalla Chiamata dell'Interfaccia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    typedef  int errno_t;

Tipo di Dati della Posizione Articolare
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo di dati della posizione articolare
    */
    typedef  struct
    {
        double jPos[6];   /* Posizioni delle sei articolazioni, unità deg */
    }JointPos;

Tipo di Dati della Posizione nello Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo di dati della posizione nello spazio cartesiano
    */
    typedef struct
    {
        double x;    /* Coordinata dell'asse x, unità mm  */
        double y;    /* Coordinata dell'asse y, unità mm  */
        double z;    /* Coordinata dell'asse z, unità mm  */
    } DescTran;

Tipo di Dati dell'Orientamento in Angoli di Eulero
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo di dati dell'orientamento in angoli di Eulero
    */
    typedef struct
    {
        double rx;   /* Angolo di rotazione attorno all'asse fisso X, unità: deg  */
        double ry;   /* Angolo di rotazione attorno all'asse fisso Y, unità: deg  */
        double rz;   /* Angolo di rotazione attorno all'asse fisso Z, unità: deg  */
    } Rpy;

Tipo di Dati della Posa nello Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    *@brief  Tipo di posa nello spazio cartesiano
    */
    typedef struct
    {
        DescTran tran;      /* Posizione nello spazio cartesiano  */
        Rpy rpy;            /* Orientamento nello spazio cartesiano  */
    } DescPose;

Tipo di Dati della Posizione dell'Asse Esteso
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo di dati della posizione dell'asse esteso
    */
    typedef  struct
    {
        double ePos[4];   /* Posizioni dei quattro assi estesi, unità mm */
    }ExaxisPos;

Tipo di Dati del Sensore di Coppia/Forza
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Componenti di forza e momento del sensore di forza
    */
    typedef struct
    {
        double fx;  /* Componente di forza lungo l'asse x, unità N  */
        double fy;  /* Componente di forza lungo l'asse y, unità N  */
        double fz;  /* Componente di forza lungo l'asse z, unità N  */
        double tx;  /* Componente di momento attorno all'asse x, unità Nm */
        double ty;  /* Componente di momento attorno all'asse y, unità Nm */
        double tz;  /* Componente di momento attorno all'asse z, unità Nm */
    } ForceTorque;

Tipo di Dati dei Parametri a Spirale
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Tipo di dati dei parametri a spirale
    */
    typedef  struct
    {
        int    circle_num;           /* Numero di giri della spirale  */
        float  circle_angle;         /* Angolo di inclinazione della spirale  */
        float  rad_init;             /* Raggio iniziale della spirale, unità mm  */
        float  rad_add;              /* Incremento del raggio  */
        float  rotaxis_add;          /* Incremento della direzione dell'asse di rotazione  */
        int rot_direction;   /* Direzione di rotazione, 0-orario, 1-antiorario  */
        int velAccMode;      /* Modalità parametri velocità/accelerazione: 0-velocità angolare costante; 1-velocità lineare costante */
    }SpiralParam;

Pacchetto di feedback dello stato del controller
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pacchetto di feedback dello stato del controller
     */
    typedef struct _ROBOT_STATE_PKG
    {
      uint16_t frame_head;   // Intestazione del frame, convenuto come 0x5A5A
      uint8_t frame_cnt;     // Conteggio del frame, conteggio ciclico 0-255
      uint16_t data_len;     // Lunghezza del contenuto dei dati
      uint8_t program_state;   // Stato di esecuzione del programma, 1-stop; 2-esecuzione; 3-pausa;
      uint8_t robot_state;    // Stato di movimento del robot, 1-stop; 2-esecuzione; 3-pausa; 4-transcina
      int   main_code;     // Codice guasto principale
      int   sub_code;      // Codice guasto secondario
      uint8_t robot_mode;    // Modalità robot, 1-modalità manuale; 0-modalità automatica;
      double  jt_cur_pos[6];   // Posizione attuale dei giunti per 6 assi, unità deg
      double  tl_cur_pos[6];   // Posizione attuale dell'utensile (TCP)
            // tl_cur_pos[0], posizione lungo l'asse x, unità mm,
            // tl_cur_pos[1], posizione lungo l'asse y, unità mm,
            // tl_cur_pos[2], posizione lungo l'asse z, unità mm,
            // tl_cur_pos[3], angolo di rotazione attorno all'asse X fisso, unità deg
            // tl_cur_pos[4], angolo di rotazione attorno all'asse Y fisso, unità deg
            // tl_cur_pos[5], angolo di rotazione attorno all'asse Z fisso, unità deg
      double  flange_cur_pos[6]; // Posizione attuale della flangia finale
            // flange_cur_pos[0], posizione lungo l'asse x, unità mm,
            // flange_cur_pos[1], posizione lungo l'asse y, unità mm,
            // flange_cur_pos[2], posizione lungo l'asse z, unità mm,
            // flange_cur_pos[3], angolo di rotazione attorno all'asse X fisso, unità deg
            // flange_cur_pos[4], angolo di rotazione attorno all'asse Y fisso, unità deg
            // flange_cur_pos[5], angolo di rotazione attorno all'asse Z fisso, unità deg
      double  actual_qd[6];    // Velocità attuale dei 6 giunti, unità deg/s
      double  actual_qdd[6];    // Accelerazione attuale dei 6 giunti, unità deg/s^2
      double  target_TCP_CmpSpeed[2];
            // target_TCP_CmpSpeed[0], Velocità di istruzione composita TCP (posizione), unità mm/s
            // target_TCP_CmpSpeed[1], Velocità di istruzione composita TCP (assetto), unità deg/s */
      double  target_TCP_Speed[6];  // Velocità di istruzione TCP
              // target_TCP_Speed[0], velocità lungo l'asse x, unità mm/s,
              // target_TCP_Speed[1], velocità lungo l'asse y, unità mm/s,
              // target_TCP_Speed[2], velocità lungo l'asse z, unità mm/s,
              // target_TCP_Speed[3], velocità angolare attorno all'asse X fisso, unità deg/s
              // target_TCP_Speed[4], velocità angolare attorno all'asse Y fisso, unità deg/s
              // target_TCP_Speed[5], velocità angolare attorno all'asse Z fisso, unità deg/s */
      double  actual_TCP_CmpSpeed[2];
              // actual_TCP_CmpSpeed[0], Velocità effettiva composita TCP (posizione), unità mm/s
              // actual_TCP_CmpSpeed[1], Velocità effettiva composita TCP (assetto), unità deg/s */
      double  actual_TCP_Speed[6];  // Velocità effettiva TCP
              // actual_TCP_Speed[0], velocità lungo l'asse x, unità mm/s,
              // actual_TCP_Speed[1], velocità lungo l'asse y, unità mm/s,
              // actual_TCP_Speed[2], velocità lungo l'asse z, unità mm/s,
              // actual_TCP_Speed[3], velocità angolare attorno all'asse X fisso, unità deg/s
              // actual_TCP_Speed[4], velocità angolare attorno all'asse Y fisso, unità deg/s
              // actual_TCP_Speed[5], velocità angolare attorno all'asse Z fisso, unità deg/s
      double  jt_cur_tor[6];    // Coppia attuale dei 6 giunti, unità N·m
      int   tool;         // Numero del sistema di coordinate utensile applicato
      int   user;         // Numero del sistema di coordinate pezzo applicato
      uint8_t cl_dgt_output_h;   // Uscita IO digitale della scatola di controllo 15-8
      uint8_t cl_dgt_output_l;   // Uscita IO digitale della scatola di controllo 7-0
      uint8_t tl_dgt_output_l;   // Uscita IO digitale dell'utensile 7-0, solo bit0-bit1 validi
      uint8_t cl_dgt_input_h;    // Ingresso IO digitale della scatola di controllo 15-8
      uint8_t cl_dgt_input_l;    // Ingresso IO digitale della scatola di controllo 7-0
      uint8_t tl_dgt_input_l;    // Ingresso IO digitale dell'utensile 7-0, solo bit0-bit1 validi
      uint16_t cl_analog_input[2]; // cl_analog_input[0], Ingresso analogico della scatola di controllo 0
                    // cl_analog_input[1], Ingresso analogico della scatola di controllo 1
      uint16_t tl_anglog_input;   // Ingresso analogico dell'utensile
      double  ft_sensor_raw_data[6]; // Dati grezzi del sensore di forza
              // ft_sensor_raw_data[0], forza lungo l'asse x, unità N
              // ft_sensor_raw_data[1], forza lungo l'asse y, unità N
              // ft_sensor_raw_data[2], forza lungo l'asse z, unità N
              // ft_sensor_raw_data[3], coppia attorno all'asse x, unità Nm
              // ft_sensor_raw_data[4], coppia attorno all'asse y, unità Nm
              // ft_sensor_raw_data[5], coppia attorno all'asse z, unità Nm
      double  ft_sensor_data[6];    // Dati del sensore di forza
              // ft_sensor_data[0], forza lungo l'asse x, unità N
              // ft_sensor_data[1], forza lungo l'asse y, unità N
              // ft_sensor_data[2], forza lungo l'asse z, unità N
              // ft_sensor_data[3], coppia attorno all'asse x, unità Nm
              // ft_sensor_data[4], coppia attorno all'asse y, unità Nm
              // ft_sensor_data[5], coppia attorno all'asse z, unità Nm
      uint8_t ft_sensor_active;   // Stato di attivazione del sensore di forza, 0-reset, 1-attivo
      uint8_t EmergencyStop;    // Flag di arresto di emergenza, 0-arresto di emergenza non premuto, 1-arresto di emergenza premuto
      int   motion_done;     // Segnale di movimento completato, 1-completato, 0-non completato
      uint8_t gripper_motiondone; // Segnale di completamento movimento pinza, 0-non completato, 1-completato (nessun oggetto rilevato), 2-movimento completato (oggetto rilevato)
      int   mc_queue_len;     // Lunghezza della coda delle istruzioni di movimento
      uint8_t collisionState;    // Rilevamento collisione, 1-collisione, 0-nessuna collisione
      int   trajectory_pnum;   // Numero del punto di traiettoria
      uint8_t safety_stop0_state; // Segnale di stop di sicurezza SI0
      uint8_t safety_stop1_state; // Segnale di stop di sicurezza SI1
      uint8_t gripper_fault_id;   // ID pinza errata
      uint16_t gripper_fault;    // Guasto pinza 0-nessun guasto 1-timeout 485 2-errore comando 3-caduta pezzo Altro-codice guasto pinza
      uint16_t gripper_active;    // Stato di attivazione pinza
      uint8_t gripper_position;   // Posizione pinza
      int8_t  gripper_speed;    // Velocità pinza
      int8_t  gripper_current;   // Corrente pinza
      int   gripper_temp;     // Temperatura pinza
      int   gripper_voltage;   // Tensione pinza
      robot_aux_state aux_state;   // Stato asse estensione 485
      EXT_AXIS_STATUS extAxisStatus[4]; // Stato asse estensione UDP
      uint16_t extDIState[8];     // Ingresso DI esteso
      uint16_t extDOState[8];     // Uscita DO estesa
      uint16_t extAIState[4];     // Ingresso AI esteso
      uint16_t extAOState[4];     // Uscita AO estesa
      int rbtEnableState;       // Stato abilitazione robot
      double  jointDriverTorque[6];    // Coppia driver giunto robot
      double  jointDriverTemperature[6];  // Temperatura driver giunto robot
      RobotTime robotTime;       // Tempo del sistema robot
      int softwareUpgradeState;    // Stato aggiornamento software robot
      uint16_t endLuaErrCode;     // Stato esecuzione LUA finale
      uint16_t cl_analog_output[2]; // Uscita analogica scatola di controllo
      uint16_t tl_analog_output;    // Uscita analogica utensile
      float gripperRotNum;       // Numero di giri corrente pinza rotante
      uint8_t gripperRotSpeed;     // Percentuale velocità corrente pinza rotante
      uint8_t gripperRotTorque;    // Percentuale coppia corrente pinza rotante
      WELDING_BREAKOFF_STATE weldingBreakOffState; // Stato interruzione saldatura
      double jt_tgt_tor[6];         // Coppia istruzione giunto
      int smartToolState;          // Stato pulsante手柄 SmartTool
      float wideVoltageCtrlBoxTemp;     // Temperatura scatola di controllo wide voltage
      uint16_t wideVoltageCtrlBoxFanCurrent;// Corrente ventola scatola di controllo wide voltage (mA)
      double toolCoord[6];    // Valori correnti sistema coordinate utensile; x,y,z,rx,ry,rz
      double wobjCoord[6];    // Valori correnti sistema coordinate pezzo; x,y,z,rx,ry,rz
      double extoolCoord[6];   // Valori correnti sistema coordinate utensile esterno; x,y,z,rx,ry,rz
      double exAxisCoord[6];   // Valori correnti sistema coordinate asse estensione; x,y,z,rx,ry,rz
      double load;        // Massa carico
      double loadCog[3];     // Baricentro carico
      double lastServoTarget[6]; // Posizione target ultimo ServoJ in coda
      int servoJCmdNum;      // Conteggio istruzioni servoJ
      double targetJointPos[6];  // Posizione istruzione 6 giunti, unità °
      double targetJointVel[6];  // Velocità istruzione 6 giunti, unità °/s
      double targetJointAcc[6];  // Accelerazione istruzione 6 giunti, unità °/s2
      double targetJointCurrent[6]; // Corrente istruzione 6 giunti, unità A
      double actualJointCurrent[6]; // Corrente attuale 6 giunti, unità A
      double actualTCPForce[6];  // Coppia finale robot Nm; x,y,z,rx,ry,rz
      double targetTCPPos[6];    // Posizione istruzione TCP robot mm; x,y,z,rx,ry,rz
      uint8_t collisionLevel[6]; // Livello collisione robot
      double speedScaleManual;   // Percentuale velocità globale modalità manuale
      double speedScaleAuto;    // Percentuale velocità globale modalità automatica
      int luaLineNum;       // Numero riga programma lua corrente in esecuzione
      uint8_t abnomalStop;     // 0-nessuna anomalia; 1-anomalia presente
      char currentLuaFileName[256]; // Nome programma lua corrente in esecuzione
      uint8_t programTotalLine;   // Numero totale righe programma lua
      uint8_t safetyBoxSingal[6]; // Stato pulsanti box sicurezza robot
      double weldVoltage;     // Tensione saldatura V
      double weldCurrent;     // Corrente saldatura
      double weldTrackVel;    // Velocità tracciamento saldatura mm/s
      uint8_t tpdException;    // Superamento limite caricamento traiettoria TPD, 0-non superato, 1-superato
      uint8_t alarmRebootRobot;  // Avviso, 1-rilasciare pulsante arresto emergenza e riavviare scatola di controllo, 2-anomalia comunicazione giunto riavviare scatola di controllo
      uint8_t modbusMasterConnect; // bit0-bit7 corrispondono a stato connessione master 0-7 ModbusTCP 0-non connesso 1-connesso
      uint8_t modbusSlaveConnect;  // Stato connessione slave ModbusTCP 0-non connesso; 1-connesso
      uint8_t btnBoxStopSignal;    // Segnale arresto emergenza pulsantiera, 0-arresto emergenza rilasciato; 1-arresto emergenza premuto
      uint8_t dragAlarm;      // Avviso trascinamento, attualmente in modalità automatica, 0-nessun avviso, 1-avviso, 2-anomalia feedback posizione nessuna commutazione
      uint8_t safetyDoorAlarm;    // Avviso porta di sicurezza; 0-porta sicurezza chiusa; 1-porta sicurezza aperta
      uint8_t safetyPlaneAlarm;    // Avviso ingresso safety wall; 0-nessun ingresso safety wall; 1-ingresso safety wall
      uint8_t motonAlarm;      // Avviso movimento
      uint8_t interfaceAlarm;    // Avviso ingresso area interferenza
      int udpCmdState;       // Stato connessione comunicazione UDP porta 20007
      uint8_t weldReadyState;    // Stato preparazione saldatrice completato
      uint8_t alarmCheckEmergStopBtn; // 0-normale; 1-anomalia comunicazione, verificare se pulsante arresto emergenza rilasciato
      uint8_t tsTmCmdComError;    // 0-normale; 1-guasto comunicazione istruzione coppia
      uint8_t tsTmStateComError;   // 0-normale; 1-guasto comunicazione stato coppia
      int ctrlBoxError;       // Errore scatola di controllo
      uint8_t safetyDataState;    // Flag stato dati sicurezza, 0-normale, 1-anomalo
      uint8_t forceSensorErrState; // Guasto timeout connessione sensore forza; bit0-bit1 corrispondono a ID sensore forza ID1-ID2
      uint8_t ctrlOpenLuaErrCode[4]; // Codici errore protocollo periferiche controller 4 (codice errore 500)
      uint8_t strangePosFlag; // Flag posizione singolare attuale; 0-normale; 1-posizione singolare
      uint8_t alarm;      // Avviso
      uint8_t driverAlarm;    // Numero asse allarme driver
      uint8_t aliveSlaveNumError; // Errore numero slave attivi, 0: normale; 1: errore numero
      uint8_t slaveComError[8];   // Errore slave, 0: normale; 1: slave offline; 2: stato slave incoerente con valore impostato; 3: slave non configurato; 4: errore configurazione slave; 5: errore inizializzazione slave; 6: errore inizializzazione comunicazione mailbox slave
      uint8_t cmdPointError;    // Errore punto istruzione
      uint8_t IOError;      // Errore IO
      uint8_t gripperError;    // Errore pinza
      uint8_t fileError;     // Errore file
      uint8_t paraError;     // Errore parametro
      uint8_t exaxisOutLimitError;  // Errore superamento limite soft asse esterno
      uint8_t driverComError[6];    // Guasto comunicazione con driver
      uint8_t driverError;      // Numero asse guasto comunicazione driver
      uint8_t outSoftLimitError;   // Guasto superamento limite soft
      char axleGenComData[130];    // Dati feedback trasmissione trasparente finale robot
      uint8_t socketConnTimeout;   // Timeout connessione socket, bit0-bit4: socketID 1-4
      uint8_t socketReadTimeout;   // Timeout lettura socket, bit0-bit4: socketID 1-4
      uint8_t tsWebStateComErr;   // Guasto comunicazione web-coppia; 0-normale; 1-guasto
      uint8_t exaxisCoordID;     //ID del sistema di coordinate dell'asse esteso
      uint16_t check_sum;     // Checksum
    }ROBOT_STATE_PKG;

Tipo Enumerato per la Configurazione del Feedback di Stato del Robott
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    enum class RobotState
    {
        ProgramState = 3,           // Stato di esecuzione del programma, 1-arrestato; 2-in esecuzione; 3-in pausa
        RobotState = 4,             // Stato di movimento del robot, 1-arrestato; 2-in movimento; 3-in pausa; 4-trascinamento
        MainCode = 5,               // Codice guasto principale
        SubCode = 6,                // Codice guasto secondario
        RobotMode = 7,              // Modalità robot, 1-manuale; 0-automatica
        JointCurPos = 8,            // Posizioni articolari correnti di 6 assi, unità deg
        ToolCurPos = 9,             // Posizione corrente dell'utensile: [0] lungo x (mm), [1] lungo y (mm), [2] lungo z (mm), [3] rotazione attorno X fisso (deg), [4] attorno Y fisso (deg), [5] attorno Z fisso (deg)
        FlangeCurPos = 10,          // Posizione corrente della flangia terminale: [0] lungo x (mm), [1] lungo y (mm), [2] lungo z (mm), [3] rotazione attorno X fisso (deg), [4] attorno Y fisso (deg), [5] attorno Z fisso (deg)
        ActualJointVel = 11,        // Velocità correnti di 6 giunti, unità deg/s
        ActualJointAcc = 12,        // Accelerazioni correnti di 6 giunti, unità deg/s^2
        TargetTCPCmpSpeed = 13,     // Velocità di comando composita TCP: [0] posizione (mm/s), [1] orientamento (deg/s)
        TargetTCPSpeed = 14,        // Velocità di comando TCP: [0] lungo x (mm/s), [1] lungo y (mm/s), [2] lungo z (mm/s), [3] velocità angolare attorno X (deg/s), [4] attorno Y (deg/s), [5] attorno Z (deg/s)
        ActualTCPCmpSpeed = 15,     // Velocità effettiva composita TCP: [0] posizione (mm/s), [1] orientamento (deg/s)
        ActualTCPSpeed = 16,        // Velocità effettiva TCP: [0] lungo x (mm/s), [1] lungo y (mm/s), [2] lungo z (mm/s), [3] velocità angolare attorno X (deg/s), [4] attorno Y (deg/s), [5] attorno Z (deg/s)
        ActualJointTorque = 17,     // Coppie correnti di 6 assi, unità N·m
        Tool = 18,                  // Numero del sistema di coordinate utensile applicato
        User = 19,                  // Numero del sistema di coordinate pezzo applicato
        ClDgtOutputH = 20,          // Uscita IO digitale della scatola di controllo 15-8
        ClDgtOutputL = 21,          // Uscita IO digitale della scatola di controllo 7-0
        TlDgtOutputL = 22,          // Uscita IO digitale dell'utensile 7-0, solo bit0-bit1 validi
        ClDgtInputH = 23,           // Ingresso IO digitale della scatola di controllo 15-8
        ClDgtInputL = 24,           // Ingresso IO digitale della scatola di controllo 7-0
        TlDgtInputL = 25,           // Ingresso IO digitale dell'utensile 7-0, solo bit0-bit1 validi
        ClAnalogInput = 26,         // Ingresso analogico della scatola di controllo: [0] canale 0, [1] canale 1
        TlAnalogInput = 27,         // Ingresso analogico dell'utensile
        FtSensorRawData = 28,       // Dati grezzi del sensore di forza/coppia: [0] forza lungo x (N), [1] lungo y (N), [2] lungo z (N), [3] coppia attorno x (Nm), [4] attorno y (Nm), [5] attorno z (Nm)
        FtSensorData = 29,          // Dati del sensore di forza/coppia (elaborati): [0] forza lungo x (N), [1] lungo y (N), [2] lungo z (N), [3] coppia attorno x (Nm), [4] attorno y (Nm), [5] attorno z (Nm)
        FtSensorActive = 30,        // Stato di attivazione del sensore di forza/coppia, 0-reset, 1-attivato
        EmergencyStop = 31,         // Flag di arresto di emergenza, 0-non premuto, 1-premuto
        MotionDone = 32,            // Segnale di movimento completato, 1-completato, 0-non completato
        GripperMotiondone = 33,     // Segnale di movimento della pinza completato, 1-completato, 0-non completato
        McQueueLen = 34,            // Lunghezza della coda dei comandi di movimento
        CollisionState = 35,        // Rilevamento collisione, 1-collisione, 0-nessuna collisione
        TrajectoryPnum = 36,        // Numero del punto di traiettoria
        SafetyStop0State = 37,      // Segnale di arresto di sicurezza SI0
        SafetyStop1State = 38,      // Segnale di arresto di sicurezza SI1
        GripperFaultId = 39,        // Numero pinza guasta
        GripperFault = 40,          // Guasto pinza
        GripperActive = 41,         // Stato di attivazione della pinza
        GripperPosition = 42,       // Posizione della pinza
        GripperSpeed = 43,          // Velocità della pinza
        GripperCurrent = 44,        // Corrente della pinza
        GripperTemp = 45,           // Temperatura della pinza
        GripperVoltage = 46,        // Tensione della pinza
        AuxState = 47,              // Stato assi di estensione 485
        ExtAxisStatus = 48,         // Stato assi di estensione UDP (4 assi)
        ExtDIState = 49,            // Ingresso DI esteso (8)
        ExtDOState = 50,            // Uscita DO estesa (8)
        ExtAIState = 51,            // Ingresso AI esteso (4)
        ExtAOState = 52,            // Uscita AO estesa (4)
        RbtEnableState = 53,        // Stato di abilitazione del robot
        JointDriverTorque = 54,     // Coppia del driver dei giunti del robot (6 giunti)
        JointDriverTemperature = 55,// Temperatura del driver dei giunti del robot (6 giunti)
        RobotTime = 56,             // Tempo del sistema robot
        SoftwareUpgradeState = 57,  // Stato di aggiornamento del software del robot
        EndLuaErrCode = 58,         // Stato di esecuzione Lua dell'estremità
        ClAnalogOutput = 59,        // Uscita analogica della scatola di controllo (2)
        TlAnalogOutput = 60,        // Uscita analogica dell'utensile
        GripperRotNum = 61,         // Numero di giri corrente della pinza rotante
        GripperRotSpeed = 62,       // Percentuale di velocità di rotazione corrente della pinza rotante
        GripperRotTorque = 63,      // Percentuale di coppia di rotazione corrente della pinza rotante
        WeldingBreakOffState = 64,  // Stato di interruzione saldatura
        TargetJointTorque = 65,     // Coppia di comando del giunto (6 giunti)
        SmartToolState = 66,        // Stato del pulsante della maniglia SmartTool
        WideVoltageCtrlBoxTemp = 67,// Temperatura della scatola di controllo a vasta tensione
        WideVoltageCtrlBoxFanCurrent = 68, // Corrente della ventola della scatola di controllo a vasta tensione (mA)
        ToolCoord = 69,             // Valori correnti del sistema di coordinate utensile: x,y,z,rx,ry,rz
        WobjCoord = 70,             // Valori correnti del sistema di coordinate pezzo: x,y,z,rx,ry,rz
        ExtoolCoord = 71,           // Valori correnti del sistema di coordinate utensile esterno: x,y,z,rx,ry,rz
        ExAxisCoord = 72,           // Valori correnti del sistema di coordinate assi di estensione: x,y,z,rx,ry,rz
        Load = 73,                  // Massa del carico
        LoadCog = 74,               // Centro di gravità del carico: x,y,z
        LastServoTarget = 75,       // Ultima posizione target ServoJ nella coda (6 giunti)
        ServoJCmdNum = 76,          // Conteggio comandi ServoJ
        TargetJointPos = 77,        // Posizione di comando di 6 giunti, unità °
        TargetJointVel = 78,        // Velocità di comando di 6 giunti, unità °/s
        TargetJointAcc = 79,        // Accelerazione di comando di 6 giunti, unità °/s²
        TargetJointCurrent = 80,    // Corrente di comando di 6 giunti, unità A
        ActualJointCurrent = 81,    // Corrente corrente di 6 giunti, unità A
        ActualTCPForce = 82,        // Coppia dell'end-effector del robot: x,y,z,rx,ry,rz, unità Nm
        TargetTCPPos = 83,          // Posizione di comando TCP del robot: x,y,z,rx,ry,rz, unità mm
        CollisionLevel = 84,        // Livello di collisione del robot (6)
        SpeedScaleManual = 85,      // Percentuale di velocità globale in modalità manuale
        SpeedScaleAuto = 86,        // Percentuale di velocità globale in modalità automatica
        LuaLineNum = 87,            // Numero di riga corrente del programma Lua in esecuzione
        AbnomalStop = 88,           // 0-nessuna anomalia; 1-anomalia presente
        CurrentLuaFileName = 89,    // Nome del programma Lua attualmente in esecuzione
        ProgramTotalLine = 90,      // Numero totale di righe del programma Lua
        SafetyBoxSingal = 91,       // Stato dei pulsanti della scatola pulsanti del robot (6)
        WeldVoltage = 92,           // Tensione di saldatura V
        WeldCurrent = 93,           // Corrente di saldatura
        WeldTrackVel = 94,          // Velocità di inseguimento del cordone di saldatura mm/s
        TpdException = 95,          // Conteggio di caricamento traiettoria TPD superato, 0-non superato, 1-superato
        AlarmRebootRobot = 96,      // Avviso: 1-rilasciare l'arresto di emergenza e riavviare, 2-anomalia comunicazione giunto, riavviare
        ModbusMasterConnect = 97,   // bit0-7 corrispondono allo stato di connessione dei master ModbusTCP 0-7, 0-non connesso, 1-connesso
        ModbusSlaveConnect = 98,    // Stato di connessione slave ModbusTCP, 0-non connesso, 1-connesso
        BtnBoxStopSignal = 99,      // Segnale di arresto di emergenza della scatola pulsanti, 0-rilasciato, 1-premuto
        DragAlarm = 100,            // Avviso di trascinamento: 0-nessun avviso, 1-avviso, 2-anomalia feedback posizione, nessuna commutazione
        SafetyDoorAlarm = 101,      // Avviso porta di sicurezza: 0-chiusa, 1-aperta
        SafetyPlaneAlarm = 102,     // Avviso parete di sicurezza: 0-non entrata, 1-entrata
        MotonAlarm = 103,           // Avviso di movimento
        InterfaceAlarm = 104,       // Avviso di ingresso nell'area di interferenza
        UdpCmdState = 105,          // Stato di connessione di comunicazione UDP della porta 20007
        WeldReadyState = 106,       // Stato di prontezza della saldatrice
        AlarmCheckEmergStopBtn = 107, // 0-normale; 1-anomalia di comunicazione, verificare pulsante arresto emergenza
        TsTmCmdComError = 108,      // 0-normale; 1-guasto comunicazione comando coppia
        TsTmStateComError = 109,    // 0-normale; 1-guasto comunicazione stato coppia
        CtrlBoxError = 110,         // Errore della scatola di controllo
        SafetyDataState = 111,      // Stato dei dati di sicurezza, 0-normale, 1-anomalo
        ForceSensorErrState = 112,  // Timeout connessione sensore di forza, bit0-bit1 corrispondono a ID1-ID2
        CtrlOpenLuaErrCode = 113,   // Codici di errore del protocollo aperto del controller periferico (4 errori codice 500)
        StrangePosFlag = 114,       // Flag di posa singolare: 0-normale, 1-posa singolare
        Alarm = 115,                // Avviso
        DriverAlarm = 116,          // Numero asse allarme driver
        AliveSlaveNumError = 117,   // Errore conteggio slave attivi: 0-normale, 1-errore conteggio
        SlaveComError = 118,        // Errore slave: 0-normale, 1-offline, 2-stato incoerente, 3-non configurato, 4-errore configurazione, 5-errore inizializzazione, 6-errore inizializzazione comunicazione mailbox
        CmdPointError = 119,        // Errore punto di comando
        IOError = 120,              // Errore IO
        GripperError = 121,         // Errore pinza
        FileError = 122,            // Errore file
        ParaError = 123,            // Errore parametro
        ExaxisOutLimitError = 124,  // Errore superamento limite morbido asse esterno
        DriverComError = 125,       // Guasto comunicazione driver (6 assi)
        DriverError = 126,          // Numero asse con guasto comunicazione driver
        OutSoftLimitError = 127,    // Guasto superamento limite morbido
        AxleGenComData = 128,       // Dati di feedback di trasmissione trasparente dell'end-effector del robot
        SocketConnTimeout = 129,    // Timeout connessione socket, bit0-bit4 corrispondono a socketID 1-4
        SocketReadTimeout = 130,    // Timeout lettura socket, bit0-bit4 corrispondono a socketID 1-4
        TsWebStateComErr = 131,      // Guasto comunicazione web-coppia: 0-normale, 1-guasto
        ExaxisCoordID = 132          //ID del sistema di coordinate dell'asse esteso
    };