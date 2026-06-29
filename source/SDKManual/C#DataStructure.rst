Descrizione delle strutture dati
=============================================

.. toctree:: 
    :maxdepth: 5

Tipo di dati della posizione dei giunti
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Tipo di dati della posizione dei giunti 
    */  
    struct JointPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jPos;   /* Posizioni dei sei giunti, unità deg */
    }

Tipo di dati della posizione nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo di dati della posizione nello spazio cartesiano
    */
    struct DescTran
    {
        public double x;    /* Coordinata dell'asse x, unità mm  */
        public double y;    /* Coordinata dell'asse y, unità mm  */
        public double z;    /* Coordinata dell'asse z, unità mm  */
    }

Tipo di dati dell'orientamento degli angoli di Eulero
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo di dati dell'orientamento degli angoli di Eulero
    */
    struct Rpy
    {
    public double rx;   /* Angolo di rotazione attorno all'asse fisso X, unità: deg  */
    public double ry;   /* Angolo di rotazione attorno all'asse fisso Y, unità: deg  */
    public double rz;   /* Angolo di rotazione attorno all'asse fisso Z, unità: deg  */
    }

Tipo di dati della posa nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    *@brief Tipo di dati della posa nello spazio cartesiano
    */
    struct DescPose
    {
        public DescTran tran;     /* Posizione nello spazio cartesiano  */
        public Rpy rpy;			/* Orientamento nello spazio cartesiano  */
    }

Tipo di dati della posizione dell'asse esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Tipo di dati della posizione dell'asse esteso
    */
    struct ExaxisPos
    {
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public double[] ePos;   /* Posizioni dei quattro assi estesi, unità mm */
    }

Tipo di dati del sensore di coppia
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Componenti di forza e coppia del sensore di forza
    */
    struct ForceTorque
    {
        public double fx;  /* Componente di forza lungo l'asse x, unità N  */
        public double fy;  /* Componente di forza lungo l'asse y, unità N  */
        public double fz;  /* Componente di forza lungo l'asse z, unità N  */
        public double tx;  /* Componente di coppia attorno all'asse x, unità Nm */
        public double ty;  /* Componente di coppia attorno all'asse y, unità Nm */
        public double tz;  /* Componente di coppia attorno all'asse z, unità Nm */
    }

Tipo di dati dei parametri a spirale
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public struct SpiralParam
    {
        public int circle_num;           /* Numero di spire  */
        public float circle_angle;         /* Angolo di inclinazione della spirale  */
        public float rad_init;             /* Raggio iniziale della spirale, unità mm  */
        public float rad_add;              /* Incremento del raggio  */
        public float rotaxis_add;          /* Incremento della direzione dell'asse di rotazione  */
        public uint rot_direction;  /* Direzione di rotazione, 0-senso orario, 1-senso antiorario  */
        public int velAccMode;      // Modalità parametri velocità/accelerazione: 0-velocità angolare costante; 1-velocità lineare costante
        public SpiralParam(int num, float angle, float initRad, float addRad, float axisAdd, uint direction, int mode)
        {
            circle_num = num;
            circle_angle = angle;
            rad_init = initRad;
            rad_add = addRad;
            rotaxis_add = axisAdd;
            rot_direction = direction;
            velAccMode = mode;
        }
    }

Tipo di stato dell'asse esteso
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief  Tipo di stato dell'asse esteso
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct ROBOT_AUX_STATE
    {
        public byte servoId;           // ID driver servo
        public int servoErrCode;       // Codice errore driver servo
        public int servoState;         // Stato driver servo
        public double servoPos;        // Posizione corrente servo
        public float servoVel;         // Velocità corrente servo
        public float servoTorque;      // Coppia corrente servo
    }

Stato di interruzione della saldatura
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public struct WELDING_BREAKOFF_STATE
    {
        public byte breakOffState;  // Stato di interruzione della saldatura
        public byte weldArcState;   // Stato di interruzione dell'arco di saldatura
    }

Tipo di struttura di feedback dello stato del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: c#
    :linenos:

    /**
    * @brief  Tipo di struttura di feedback dello stato del robot
    */
    [StructLayout(LayoutKind.Sequential, Pack = 1)]
    public class ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           // Intestazione frame 0x5A5A
        public byte frame_cnt;              // Conteggio frame
        public UInt16 data_len;             // Lunghezza dati 5
        public byte program_state;          // Stato esecuzione programma, 1-fermo; 2-in esecuzione; 3-in pausa;
        public byte robot_state;            // Stato movimento robot, 1-fermo; 2-in esecuzione; 3-in pausa; 4-transcina
        public int main_code;               // Codice guasto principale
        public int sub_code;                // Codice guasto secondario
        public byte robot_mode;             // Modalità robot, 1-modalità manuale; 0-modalità automatica;

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;         // Posizione attuale giunti per 6 assi, unità deg
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;         // Posizione attuale utensile (TCP)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;     // Posizione attuale flangia finale
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;          // Velocità attuale 6 giunti, unità deg/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;         // Accelerazione attuale 6 giunti, unità deg/s^2
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;// Velocità istruzione composita TCP (posizione, orientamento)
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;   // Velocità istruzione TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;// Velocità effettiva composita TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;   // Velocità effettiva TCP
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;         // Coppia attuale 6 assi, unità N·m

        public int tool;                    // Numero sistema coordinate utensile applicato
        public int user;                    // Numero sistema coordinate pezzo applicato
        public byte cl_dgt_output_h;        // Uscita IO digitale scatola di controllo 15-8
        public byte cl_dgt_output_l;        // Uscita IO digitale scatola di controllo 7-0
        public byte tl_dgt_output_l;        // Uscita IO digitale utensile 7-0, solo bit0-bit1 validi
        public byte cl_dgt_input_h;         // Ingresso IO digitale scatola di controllo 15-8
        public byte cl_dgt_input_l;         // Ingresso IO digitale scatola di controllo 7-0
        public byte tl_dgt_input_l;         // Ingresso IO digitale utensile 7-0, solo bit0-bit1 validi

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        // Ingressi analogici scatola di controllo
        public UInt16 tl_anglog_input;          // Ingresso analogico utensile

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data; // Dati grezzi sensore di coppia
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;     // Dati sensore di coppia
        public byte ft_sensor_active;       // Stato attivazione sensore di coppia, 0-reset, 1-attivo

        public byte EmergencyStop;          // Flag arresto emergenza, 0-non premuto, 1-premuto
        public int motion_done;             // Segnale movimento completato, 1-completato, 0-non completato
        public byte gripper_motiondone;     // Segnale di completamento movimento pinza, 0-non completato, 1-completato (nessun oggetto rilevato), 2-movimento completato (oggetto rilevato)
        public int mc_queue_len;            // Lunghezza coda comandi movimento
        public byte collisionState;         // Rilevamento collisione, 1-collisione, 0-nessuna collisione
        public int trajectory_pnum;         // Numero punto traiettoria
        public byte safety_stop0_state;     // Segnale stop sicurezza SI0
        public byte safety_stop1_state;     // Segnale stop sicurezza SI1
        public byte gripper_fault_id;       // ID pinza errata
        public UInt16 gripper_fault;     /* Guasto pinza 0-nessun guasto 1-timeout 485 2-errore comando 3-caduta pezzo Altro-codice guasto pinza */
        public UInt16 gripper_active;    /* Stato attivazione pinza */
        public byte gripper_position;       // Posizione pinza
        public byte gripper_speed;       /* Velocità pinza */
        public byte gripper_current;     /* Corrente pinza */
        public int gripper_temp;            // Temperatura pinza
        public int gripper_voltage;         // Tensione pinza

        public ROBOT_AUX_STATE auxState;   // Stato assi estensione 485

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus; // Stato assi estensione UDP

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;        // Ingressi DI estesi
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;        // Uscite DO estese
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;        // Ingressi AI estesi
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;        // Uscite AO estese

        public int rbtEnableState;          // Stato abilitazione robot

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;      // Coppie driver giunto robot
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature; // Temperature driver giunto robot

        public ROBOT_TIME robotTime;        // Tempo sistema robot
        public int softwareUpgradeState;    // Stato aggiornamento software robot
        public UInt16 endLuaErrCode;    // Stato esecuzione LUA fine

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public  UInt16[] cl_analog_output;  // Uscite analogiche scatola di controllo
        public UInt16 tl_analog_output;     // Uscita analogica utensile

        public float gripperRotNum;         // Numero giri corrente pinza rotante
        public byte gripperRotSpeed;        // Percentuale velocità corrente pinza rotante
        public byte gripperRotTorque;       // Percentuale coppia corrente pinza rotante

        public WELDING_BREAKOFF_STATE weldingBreakOffState; // Stato interruzione saldatura

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;         // Coppie istruzione giunto
        public int smartToolState;          // Stato pulsante impugnatura SmartTool
        public float wideVoltageCtrlBoxTemp; // Temperatura scatola di controllo wide voltage
        public UInt16 wideVoltageCtrlBoxFanVel;   // Corrente ventola scatola di controllo wide voltage (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;          // Valori correnti coordinate utensile; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;          // Valori correnti coordinate pezzo; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;        // Valori correnti coordinate utensile esterno; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;        // Valori correnti coordinate assi estensione; x,y,z,rx,ry,rz

        public double load;                 // Massa carico
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;            // Baricentro carico
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;    // Ultima posizione target ServoJ in coda
        public int servoJCmdNum;            // Conteggio comandi servoJ

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointPos;     // Posizione istruzione 6 giunti, unità °
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointVel;     // Velocità istruzione 6 giunti, unità °/s
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointAcc;     // Accelerazione istruzione 6 giunti, unità °/s²
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetJointCurrent; // Corrente istruzione 6 giunti, unità A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualJointCurrent; // Corrente attuale 6 giunti, unità A
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actualTCPForce;     // Coppia fine robot Nm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] targetTCPPos;       // Posizione istruzione TCP robot mm; x,y,z,rx,ry,rz
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] collisionLevel;       // Livelli collisione robot

        public double speedScaleManual;     // Percentuale velocità globale modalità manuale
        public double speedScaleAuto;       // Percentuale velocità globale modalità automatica
        public int luaLineNum;              // Numero riga programma lua corrente in esecuzione
        public byte abnomalStop;            // 0-nessuna anomalia; 1-anomalia presente

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 256)]
        public byte[] currentLuaFileName;   // Nome programma lua corrente in esecuzione
        public byte programTotalLine;       // Righe totali programma lua
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] safetyBoxSingal;      // Stato pulsanti box pulsanti robot

        public double weldVoltage;          // Tensione saldatura V
        public double weldCurrent;          // Corrente saldatura
        public double weldTrackVel;         // Velocità inseguimento cordone saldatura mm/s

        public byte tpdException;           // Superamento limite caricamento traiettorie TPD, 0-non superato, 1-superato
        public byte alarmRebootRobot;       // Avviso, 1-rilasciare pulsante arresto emergenza e riavviare scatola di controllo, 2-anomalia comunicazione giunto riavviare scatola di controllo
        public byte modbusMasterConnect;    // bit0-bit7 corrispondono a stato connessione master 0-7 ModbusTCP 0-non connesso 1-connesso
        public byte modbusSlaveConnect;     // Stato connessione slave ModbusTCP 0-non connesso; 1-connesso
        public byte btnBoxStopSignal;       // Segnale arresto emergenza pulsantiera, 0-arresto emergenza rilasciato; 1-arresto emergenza premuto
        public byte dragAlarm;              // Avviso trascinamento, attualmente in modalità automatica, 0-nessun avviso, 1-avviso, 2-anomalia feedback posizione nessuna commutazione
        public byte safetyDoorAlarm;        // Avviso porta sicurezza; 0-porta sicurezza chiusa; 1-porta sicurezza aperta
        public byte safetyPlaneAlarm;       // Avviso ingresso safety wall; 0-nessun ingresso safety wall; 1-ingresso safety wall
        public byte motonAlarm;             // Avviso movimento
        public byte interfaceAlarm;         // Avviso ingresso area interferenza
        public int udpCmdState;             // Stato connessione comunicazione UDP porta 20007
        public byte weldReadyState;         // Stato preparazione saldatrice completato
        public byte alarmCheckEmergStopBtn; // 0-normale; 1-anomalia comunicazione, verificare se pulsante arresto emergenza rilasciato
        public byte tsTmCmdComError;        // 0-normale; 1-guasto comunicazione comando coppia
        public byte tsTmStateComError;      // 0-normale; 1-guasto comunicazione stato coppia
        public int ctrlBoxError;            // Errore scatola di controllo
        public byte safetyDataState;        // Flag stato dati sicurezza, 0-normale, 1-anomalo
        public byte forceSensorErrState;    // Guasto timeout connessione sensore forza; bit0-bit1 corrispondono a ID sensore forza ID1-ID2

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public byte[] ctrlOpenLuaErrCode;   // 4 codici errore protocollo periferiche controller (codice errore 500)

        public byte strangePosFlag;         // Flag posizione singolare attuale; 0-normale; 1-posizione singolare
        public byte alarm;                  // Avviso
        public byte driverAlarm;            // Numero asse allarme driver
        public byte aliveSlaveNumError;     // Errore numero slave attivi, 0: normale; 1: errore numero

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public byte[] slaveComError;        // Errore slave, 0: normale; 1: slave offline; 2: stato slave non corrisponde a valore impostato; 3: slave non configurato; 4: errore configurazione slave; 5: errore inizializzazione slave; 6: errore inizializzazione comunicazione mailbox slave

        public byte cmdPointError;          // Errore punto comando
        public byte IOError;                // Errore IO
        public byte gripperError;           // Errore pinza
        public byte fileError;              // Errore file
        public byte paraError;              // Errore parametro
        public byte exaxisOutLimitError;    // Errore superamento limite soft asse esterno

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public byte[] driverComError;       // Guasto comunicazione con driver
        public byte driverError;            // Numero asse guasto comunicazione driver
        public byte outSoftLimitError;      // Guasto superamento limite soft

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 130)]
        public byte[] axleGenComData;       // Dati feedback trasmissione trasparente fine robot

        public byte socketConnTimeout;     // Flag timeout connessione socket
        public byte socketReadTimeout;     // Flag timeout lettura socket
        public byte tsWebStateComErr;      // ts_web_state_com_err
        public byte exaxisCoordID;         // Numero del sistema di coordinate degli assi di estensione
        public UInt16 check_sum;         /* Checksum */

        // Costruttore: inizializza tutti i campi array
        public ROBOT_STATE_PKG()
        {
            jt_cur_pos = new double[6];
            tl_cur_pos = new double[6];
            flange_cur_pos = new double[6];
            actual_qd = new double[6];
            actual_qdd = new double[6];
            target_TCP_CmpSpeed = new double[2];
            target_TCP_Speed = new double[6];
            actual_TCP_CmpSpeed = new double[2];
            actual_TCP_Speed = new double[6];
            jt_cur_tor = new double[6];
            cl_analog_input = new ushort[2];
            ft_sensor_raw_data = new double[6];
            ft_sensor_data = new double[6];
            extAxisStatus = new EXT_AXIS_STATUS[4];
            extDIState = new ushort[8];
            extDOState = new ushort[8];
            extAIState = new ushort[4];
            extAOState = new ushort[4];
            jointDriverTorque = new double[6];
            jointDriverTemperature = new double[6];
            cl_analog_output = new ushort[2];
            jt_tgt_tor = new double[6];
            toolCoord = new double[6];
            wobjCoord = new double[6];
            extoolCoord = new double[6];
            exAxisCoord = new double[6];
            loadCog = new double[3];
            lastServoTarget = new double[6];
            targetJointPos = new double[6];
            targetJointVel = new double[6];
            targetJointAcc = new double[6];
            targetJointCurrent = new double[6];
            actualJointCurrent = new double[6];
            actualTCPForce = new double[6];
            targetTCPPos = new double[6];
            collisionLevel = new byte[6];
            currentLuaFileName = new byte[256];
            safetyBoxSingal = new byte[6];
            ctrlOpenLuaErrCode = new byte[4];
            slaveComError = new byte[8];
            driverComError = new byte[6];
            axleGenComData = new byte[130];
        }
    }

Tipo di Enumerazione della Configurazione del Feedback di Stato del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Enumerazione degli stati configurabili del robot, intervallo 0~132
    */
    public enum RobotState
    {
        FrameHead = 0,
        FrameCnt = 1,
        DataLen = 2,
        ProgramState = 3,
        RobotState = 4,
        MainCode = 5,
        SubCode = 6,
        RobotMode = 7,
        JointCurPos = 8,
        ToolCurPos = 9,
        FlangeCurPos = 10,
        ActualJointVel = 11,
        ActualJointAcc = 12,
        TargetTCPCmpSpeed = 13,
        TargetTCPSpeed = 14,
        ActualTCPCmpSpeed = 15,
        ActualTCPSpeed = 16,
        ActualJointTorque = 17,
        Tool = 18,
        User = 19,
        ClDgtOutputH = 20,
        ClDgtOutputL = 21,
        TlDgtOutputL = 22,
        ClDgtInputH = 23,
        ClDgtInputL = 24,
        TlDgtInputL = 25,
        ClAnalogInput = 26,
        TlAnglogInput = 27,
        FtSensorRawData = 28,
        FtSensorData = 29,
        FtSensorActive = 30,
        EmergencyStop = 31,
        MotionDone = 32,
        GripperMotiondone = 33,
        McQueueLen = 34,
        CollisionState = 35,
        TrajectoryPnum = 36,
        SafetyStop0State = 37,
        SafetyStop1State = 38,
        GripperFaultId = 39,
        GripperFault = 40,
        GripperActive = 41,
        GripperPosition = 42,
        GripperSpeed = 43,
        GripperCurrent = 44,
        GripperTemp = 45,
        GripperVoltage = 46,
        AuxState = 47,
        ExtAxisStatus = 48,
        ExtDIState = 49,
        ExtDOState = 50,
        ExtAIState = 51,
        ExtAOState = 52,
        RbtEnableState = 53,
        JointDriverTorque = 54,
        JointDriverTemperature = 55,
        RobotTime = 56,
        SoftwareUpgradeState = 57,
        EndLuaErrCode = 58,
        ClAnalogOutput = 59,
        TlAnalogOutput = 60,
        GripperRotNum = 61,
        GripperRotSpeed = 62,
        GripperRotTorque = 63,
        WeldingBreakOffState = 64,
        TargetJointTorque = 65,
        SmartToolState = 66,
        WideVoltageCtrlBoxTemp = 67,
        WideVoltageCtrlBoxFanCurrent = 68,
        ToolCoord = 69,
        WobjCoord = 70,
        ExtoolCoord = 71,
        ExAxisCoord = 72,
        Load = 73,
        LoadCog = 74,
        LastServoTarget = 75,
        ServoJCmdNum = 76,
        TargetJointPos = 77,
        TargetJointVel = 78,
        TargetJointAcc = 79,
        TargetJointCurrent = 80,
        ActualJointCurrent = 81,
        ActualTCPForce = 82,
        TargetTCPPos = 83,
        CollisionLevel = 84,
        SpeedScaleManual = 85,
        SpeedScaleAuto = 86,
        LuaLineNum = 87,
        AbnomalStop = 88,
        CurrentLuaFileName = 89,
        ProgramTotalLine = 90,
        SafetyBoxSingal = 91,
        WeldVoltage = 92,
        WeldCurrent = 93,
        WeldTrackVel = 94,
        TpdException = 95,
        AlarmRebootRobot = 96,
        ModbusMasterConnect = 97,
        ModbusSlaveConnect = 98,
        BtnBoxStopSignal = 99,
        DragAlarm = 100,
        SafetyDoorAlarm = 101,
        SafetyPlaneAlarm = 102,
        MotonAlarm = 103,
        InterfaceAlarm = 104,
        UdpCmdState = 105,
        WeldReadyState = 106,
        AlarmCheckEmergStopBtn = 107,
        TsTmCmdComError = 108,
        TsTmStateComError = 109,
        CtrlBoxError = 110,
        SafetyDataState = 111,
        ForceSensorErrState = 112,
        CtrlOpenLuaErrCode = 113,
        StrangePosFlag = 114,
        Alarm = 115,
        DriverAlarm = 116,
        AliveSlaveNumError = 117,
        SlaveComError = 118,
        CmdPointError = 119,
        IOError = 120,
        GripperError = 121,
        FileError = 122,
        ParaError = 123,
        ExaxisOutLimitError = 124,
        DriverComError = 125,
        DriverError = 126,
        OutSoftLimitError = 127,
        AxleGenComData = 128,
        SocketConnTimeout = 129,     // Timeout connessione socket, bit0-bit4: socketID 1-4
        SocketReadTimeout = 130,     // Timeout lettura socket, bit0-bit4: socketID 1-4
        TsWebStateComErr = 131,     // Guasto comunicazione web-coppia; 0-normale; 1-guasto
        ExaxisCoordID = 132          // Numero del sistema di coordinate degli assi di estensione
    }