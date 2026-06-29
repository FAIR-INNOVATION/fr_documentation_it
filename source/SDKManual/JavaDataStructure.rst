Spiegazione della Struttura Dati
===========================================

.. toctree:: 
    :maxdepth: 5

Tipo di Dati Posizione Giunti
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Tipo di dati posizione giunti
    */  
    public class JointPos
    {
      double J1;
      double J2;
      double J3;
      double J4;
      double J5;
      double J6;

      public JointPos(double j1, double j2, double j3, double j4, double j5, double j6)
      {
        J1 = j1;
        J2 = j2;
        J3 = j3;
        J4 = j4;
        J5 = j5;
        J6 = j6;
      }

      public JointPos()
      {

      }
    }

Tipo di Dati Posizione Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di dati posizione spazio cartesiano
    */
    public class DescTran
    {
      public double x = 0.0;    /* Coordinata asse x, unità mm  */
      public double y = 0.0;    /* Coordinata asse y, unità mm  */
      public double z = 0.0;    /* Coordinata asse z, unità mm  */
      public DescTran(double posX, double posY, double posZ)
      {
        x = posX;
        y = posY;
        z = posZ;
      }

      public DescTran()
      {

      }

    }

Tipo di Dati Orientamento Angoli di Eulero
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di dati orientamento angoli di Eulero
    */
    public class Rpy
    {
      public double rx = 0.0;   /* Angolo di rotazione attorno all'asse X fisso, unità: deg  */
      public double ry = 0.0;   /* Angolo di rotazione attorno all'asse Y fisso, unità: deg  */
      public double rz = 0.0;   /* Angolo di rotazione attorno all'asse Z fisso, unità: deg  */
      public Rpy(double rotateX, double rotateY, double rotateZ)
      {
        rx = rotateX;
        ry = rotateY;
        rz = rotateZ;
      }
    }

Tipo di Dati Posa Spazio Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo posa spazio cartesiano
    */
    public class DescPose
    {
      public DescTran tran = new DescTran(0.0, 0.0, 0.0);      /* Posizione spazio cartesiano  */
      public Rpy rpy = new Rpy(0.0, 0.0, 0.0);			       /* Orientamento spazio cartesiano  */

      public DescPose()
      {

      }

      public DescPose(DescTran descTran, Rpy rotateRpy)
      {
        tran = descTran;
        rpy = rotateRpy;
      }

      public DescPose(double tranX, double tranY, double tranZ, double rX, double ry, double rz)
      {
        tran.x = tranX;
        tran.y = tranY;
        tran.z = tranZ;
        rpy.rx = rX;
        rpy.ry = ry;
        rpy.rz = rz;
      }

      public String toString()
      {
        return String.valueOf(tran.x) + "," +  String.valueOf(tran.y) + "," +String.valueOf(tran.z) + "," +String.valueOf(rpy.rx) + "," +String.valueOf(rpy.ry) + "," +String.valueOf(rpy.rz);
      }
    }

Tipo di Dati Posizione Assi Estesi
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di dati posizione assi estesi
    */
    public class ExaxisPos
    {
      public double axis1 = 0.0;
      public double axis2 = 0.0;
      public double axis3 = 0.0;
      public double axis4 = 0.0;

      public ExaxisPos()
      {

      }
      public ExaxisPos(double[] exaxisPos)
      {
        axis1 = exaxisPos[0];
        axis2 = exaxisPos[1];
        axis3 = exaxisPos[2];
        axis4 = exaxisPos[3];
      }

      public ExaxisPos(double pos1, double pos2, double pos3, double pos4)
      {
        axis1 = pos1;
        axis2 = pos2;
        axis3 = pos3;
        axis4 = pos4;
      }
    }

Tipo di Dati Sensore di Coppia/Forza
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Componenti forza e coppia del sensore di forza
    */
    public class ForceTorque
    {
      public double fx;  /* Componente forza lungo l'asse x, unità N  */
      public double fy;  /* Componente forza lungo l'asse y, unità N  */
      public double fz;  /* Componente forza lungo l'asse z, unità N  */
      public double tx;  /* Componente coppia attorno all'asse x, unità Nm */
      public double ty;  /* Componente coppia attorno all'asse y, unità Nm */
      public double tz;  /* Componente coppia attorno all'asse z, unità Nm */
      public ForceTorque(double fX, double fY, double fZ, double tX, double tY, double tZ)
      {
        fx = fX;
        fy = fY;
        fz = fZ;
        tx = tX;
        ty = tY;
        tz = tZ;
      }
    }

Tipo di Dati Parametri Spirale
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di dati parametri spirale
    */
    public class SpiralParam
    {
        public int circle_num;           /* Numero di giri della spirale  */
        public double circle_angle;         /* Angolo di inclinazione della spirale  */
        public double rad_init;             /* Raggio iniziale della spirale, unità mm  */
        public double rad_add;              /* Incremento del raggio  */
        public double rotaxis_add;          /* Incremento direzione asse di rotazione  */
        public int rot_direction;  /* Direzione di rotazione, 0-orario, 1-antiorario  */
        public int velAccMode;     /* Modalità parametri velocità/accelerazione: 0-velocità angolare costante; 1-velocità lineare costante */
        public SpiralParam(int circleNum, double circleAngle, double radInit, double radAdd, double rotaxisAdd, int rotDirection,int vel_AccMode)
        {
            circle_num = circleNum;
            circle_angle = circleAngle;
            rad_init = radInit;
            rad_add = radAdd;
            rotaxis_add = rotaxisAdd;
            rot_direction = rotDirection;
            velAccMode=vel_AccMode;
        }
    }

Tipo di Stato Assi Estesi
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di stato assi estesi
    */
    public class EXT_AXIS_STATUS
    {
     public double pos = 0;        //Posizione asse esteso
     public double vel = 0;        //Velocità asse esteso
     public int errorCode = 0;     //Codice errore asse esteso
     public int ready = 0;        //Servo pronto
     public int inPos = 0;        //Servo in posizione
     public int alarm = 0;        //Allarme servo
     public int flerr = 0;        //Errore di inseguimento
     public int nlimit = 0;       //Al limite negativo
     public int pLimit = 0;       //Al limite positivo
     public int mdbsOffLine = 0;  //Driver bus 485 offline
     public int mdbsTimeout = 0;  //Timeout comunicazione 485 scheda controllo/box controllo
     public int homingStatus = 0; //Stato homing asse esteso
    }

Tipo di Sensore
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Tipo di sensore
    */
    public class DeviceConfig
    {
      int company = 0;          // Produttore
      int device = 0;           // Tipo/Numero dispositivo
      int softwareVersion = 0;  // Versione software
      int bus = 0;              // Posizione montaggio

      public DeviceConfig()
      {

      }

      public DeviceConfig(int company, int device, int softwareVersion, int bus)
      {
        this.company = company;
        this.device = device;
        this.softwareVersion = softwareVersion;
        this.bus = bus;
      }
    }

Configurazione Assi Estesi 485
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configurazione assi estesi 485
    */
    public class Axis485Param
    {
      int servoCompany;           // Produttore driver servo, 1-DynaTech
      int servoModel;             // Modello driver servo, 1-FD100-750C
      int servoSoftVersion;       // Versione software driver servo, 1-V1.0
      int servoResolution;        // Risoluzione encoder
      double axisMechTransRatio;  // Rapporto trasmissione meccanico

      public Axis485Param(int company, int model, int softVersion, int resolution, double mechTransRatio)
      {
        servoCompany = company;
        servoModel = model;
        servoSoftVersion = softVersion;
        servoResolution = resolution;
        axisMechTransRatio = mechTransRatio;
      }

      public Axis485Param()
      {

      }
    }

Stato Controller Servo
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Stato controller servo
    */
    public class ROBOT_AUX_STATE
    {
      public int servoId = 0;           //ID driver servo
      public int servoErrCode = 0;       //Codice errore driver servo
      public int servoState = 0;         //Stato driver servo
      public double servoPos = 0;        //Posizione corrente servo
      public float servoVel = 0;         //Velocità corrente servo
      public float servoTorque = 0;      //Coppia corrente servo    25
    }

Stato Interruzione Saldatura
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Stato interruzione saldatura
    */
    public class WELDING_BREAKOFF_STATE
    {
      public int breakOffState = 0;  //Stato interruzione saldatura
      public int weldArcState = 0;   //Stato interruzione arco saldatura
    }

Parametri Comunicazione Assi Estesi UDP
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Parametri comunicazione assi estesi UDP
    */
    public class UDP_EXT_AXIS_PARAM
    {
      public String ip = "192.168.58.88";//Indirizzo IP
      public int port = 2021;            //Porta
      public int period = 2;             //Periodo comunicazione (ms, default 2, non modificare)
      public int lossPkgTime = 50;       //Tempo rilevamento perdita pacchetti (ms)
      public int lossPkgNum = 2;         //Numero perdite pacchetti
      public int disconnectTime = 100;   //Durata conferma disconnessione comunicazione
      public int reconnectEnable = 0;    //Abilita riconnessione automatica 0-disabilitato 1-abilitato
      public int reconnectPeriod = 100;  //Intervallo periodo riconnessione (ms)
      public int reconnectNum = 3;       //Numero tentativi riconnessione
      public int selfConnect =0;         //Connessione automatica dopo riavvio alimentazione; 0-non connettere; 1-connetti
    }

Tipo Struttura Feedback Stato Robot
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Tipo struttura di feedback dello stato del robot
    */
    public class ROBOT_STATE_PKG {
        public int frame_head;                      // Intestazione del frame
        public int frame_cnt;                       // Conteggio frame
        public int data_len;                        // Lunghezza dati
        public int program_state;                   // Stato programma - 1-arrestato; 2-in esecuzione; 3-in pausa
        public int robot_state;                     // Stato movimento robot - 1-arrestato; 2-in movimento; 3-in pausa; 4-trascinamento
        public int main_code;                       // Codice guasto principale
        public int sub_code;                        // Codice guasto secondario
        public int robot_mode;                      // Modalità robot - 1-manuale; 0-automatica
        public double[] jt_cur_pos = new double[6]; // Posizioni articolari correnti di 6 assi, unità deg
        public double[] tl_cur_pos = new double[6]; // Posizione corrente utensile - [x,y,z,rx,ry,rz]
        public double[] flange_cur_pos = new double[6]; // Posizione corrente flangia terminale - [x,y,z,rx,ry,rz]
        public double[] actual_qd = new double[6];  // Velocità correnti di 6 giunti, unità deg/s
        public double[] actual_qdd = new double[6]; // Accelerazioni correnti di 6 giunti, unità deg/s^2
        public double[] target_TCP_CmpSpeed = new double[2]; // Velocità di comando composita TCP - [posizione mm/s, orientamento deg/s]
        public double[] target_TCP_Speed = new double[6]; // Velocità di comando TCP - [vx,vy,vz,wx,wy,wz]
        public double[] actual_TCP_CmpSpeed = new double[2]; // Velocità effettiva composita TCP - [posizione mm/s, orientamento deg/s]
        public double[] actual_TCP_Speed = new double[6]; // Velocità effettiva TCP - [vx,vy,vz,wx,wy,wz]
        public double[] jt_cur_tor = new double[6]; // Coppia articolare corrente
        public int tool;                            // ID utensile
        public int user;                            // ID pezzo
        public int cl_dgt_output_h;                 // Byte alto uscita digitale armadio di controllo
        public int cl_dgt_output_l;                 // Byte basso uscita digitale armadio di controllo
        public int tl_dgt_output_l;                 // Byte basso uscita digitale utensile
        public int cl_dgt_input_h;                  // Byte alto ingresso digitale armadio di controllo
        public int cl_dgt_input_l;                  // Byte basso ingresso digitale armadio di controllo
        public int tl_dgt_input_l;                  // Byte basso ingresso digitale utensile
        public int[] cl_analog_input = new int[2];  // Ingresso analogico armadio di controllo
        public int tl_anglog_input;                 // Ingresso analogico utensile
        public double[] ft_sensor_raw_data = new double[6]; // Dati grezzi sensore di forza
        public double[] ft_sensor_data = new double[6]; // Dati sensore di forza
        public int ft_sensor_active;                // Stato attivazione sensore di forza
        public int EmergencyStop;                   // Stato arresto di emergenza
        public int motion_done;                     // Movimento completato
        public int gripper_motiondone;              // Segnale di completamento movimento pinza, 0-non completato, 1-completato (nessun oggetto rilevato), 2-movimento completato (oggetto rilevato)
        public int mc_queue_len;                    // Lunghezza coda movimenti
        public int collisionState;                  // Stato collisione
        public int trajectory_pnum;                 // Numero sequenza punto traiettoria
        public int safety_stop0_state;              // Stato arresto di sicurezza 0
        public int safety_stop1_state;              // Stato arresto di sicurezza 1
        public int gripper_fault_id;                // ID guasto pinza
        public int gripper_fault;                   // Guasto pinza 0-nessun guasto 1-timeout 485 2-errore comando 3-caduta pezzo Altro-codice guasto pinza
        public int gripper_active;                  // Attivazione pinza
        public int gripper_position;                // Posizione pinza
        public int gripper_speed;                   // Velocità pinza
        public int gripper_current;                 // Corrente pinza
        public int gripper_temp;                    // Temperatura pinza
        public int gripper_voltage;                 // Tensione pinza
        public AuxState aux_state = new AuxState(); // Stato assi ausiliari interni
        public EXT_AXIS_STATUS[] extAxisStatus = new EXT_AXIS_STATUS[4]; // Array stato assi di estensione
        public short[] extDIState = new short[8];   // I/O estesi
        public short[] extDOState = new short[8];   // I/O estesi
        public short[] extAIState = new short[4];   // I/O estesi
        public short[] extAOState = new short[4];   // I/O estesi
        public int rbtEnableState;                  // Stato abilitazione robot
        public double[] jointDriverTorque = new double[6]; // Coppia driver giunti
        public double[] jointDriverTemperature = new double[6]; // Temperatura driver giunti
        public ROBOT_TIME robotTime = new ROBOT_TIME(); // Oggetto tempo robot
        public int softwareUpgradeState;            // Stato aggiornamento software
        public int endLuaErrCode;                   // Codice errore Lua terminale
        public int[] cl_analog_output = new int[2]; // Uscita analogica armadio di controllo
        public int tl_analog_output;                // Uscita analogica utensile
        public float gripperRotNum;                 // Numero di giri pinza rotante
        public int gripperRotSpeed;                 // Velocità pinza rotante
        public int gripperRotTorque;                // Coppia pinza rotante
        public WELDING_BREAKOFF_STATE weldingBreakOffState = new WELDING_BREAKOFF_STATE(); // Stato interruzione saldatura
        public double[] jt_tgt_tor = new double[6]; // Coppia articolare target
        public int smartToolState;                  // Stato utensile intelligente
        public float wideVoltageCtrlBoxTemp;        // Temperatura armadio di controllo wide voltage
        public int wideVoltageCtrlBoxFanCurrent;    // Corrente ventola armadio di controllo wide voltage
        public double[] toolCoord = new double[6];  // Sistema di coordinate utensile
        public double[] wobjCoord = new double[6];  // Sistema di coordinate pezzo
        public double[] extoolCoord = new double[6]; // Sistema di coordinate utensile esterno
        public double[] exAxisCoord = new double[6]; // Sistema di coordinate assi di estensione
        public double load;                         // Carico
        public double[] loadCog = new double[3];    // Centro di gravità del carico
        public double[] lastServoTarget = new double[6]; // Ultima posizione target servo J
        public int servoJCmdNum;                    // Numero comandi servo J
        public double[] targetJointPos = new double[6]; // Posizione articolare target
        public double[] targetJointVel = new double[6]; // Velocità articolare target
        public double[] targetJointAcc = new double[6]; // Accelerazione articolare target
        public double[] targetJointCurrent = new double[6]; // Corrente articolare target
        public double[] actualJointCurrent = new double[6]; // Corrente articolare effettiva
        public double[] actualTCPForce = new double[6]; // Forza TCP effettiva
        public double[] targetTCPPos = new double[6]; // Posizione TCP target
        public int[] collisionLevel = new int[6];   // Livello collisione
        public double speedScaleManual;              // Scala velocità manuale
        public double speedScaleAuto;                // Scala velocità automatica
        public int luaLineNum;                       // Numero riga Lua
        public int abnomalStop;                      // Arresto anomalo
        public String currentLuaFileName;            // Nome file Lua corrente
        public int programTotalLine;                 // Righe totali programma
        public int[] safetyBoxSingal = new int[6];   // Segnale scatola di sicurezza
        public double weldVoltage;                   // Tensione saldatura
        public double weldCurrent;                   // Corrente saldatura
        public double weldTrackVel;                  // Velocità tracciamento saldatura
        public int tpdException;                     // Eccezione TPD
        public int alarmRebootRobot;                 // Riavvio robot allarme
        public int modbusMasterConnect;              // Connessione master Modbus
        public int modbusSlaveConnect;               // Connessione slave Modbus
        public int btnBoxStopSignal;                 // Segnale stop scatola pulsanti
        public int dragAlarm;                        // Allarme trascinamento
        public int safetyDoorAlarm;                  // Allarme porta sicurezza
        public int safetyPlaneAlarm;                 // Allarme piano sicurezza
        public int motonAlarm;                       // Allarme movimento
        public int interfaceAlarm;                   // Allarme interferenza
        public int udpCmdState;                      // Stato comando UDP
        public int weldReadyState;                   // Stato pronto saldatura
        public int alarmCheckEmergStopBtn;           // Pulsante arresto emergenza controllo allarme
        public int tsTmCmdComError;                  // Errore comunicazione comando
        public int tsTmStateComError;                // Errore comunicazione stato
        public int ctrlBoxError;                     // Errore armadio di controllo
        public int safetyDataState;                  // Stato dati sicurezza
        public int forceSensorErrState;              // Stato errore sensore di forza
        public int[] ctrlOpenLuaErrCode = new int[4]; // Codice errore Lua open controllo
        public int strangePosFlag;                   // Flag posizione singolare
        public int alarm;                            // Allarme
        public int driverAlarm;                      // Allarme driver
        public int aliveSlaveNumError;               // Errore numero slave attivi
        public int[] slaveComError = new int[8];     // Errore comunicazione slave
        public int cmdPointError;                    // Errore punto comando
        public int IOError;                          // Errore IO
        public int gripperError;                     // Errore pinza
        public int fileError;                        // Errore file
        public int paraError;                        // Errore parametro
        public int exaxisOutLimitError;              // Errore superamento limite morbido asse estensione
        public int[] driverComError = new int[6];    // Errore comunicazione driver
        public int driverError;                      // Errore driver
        public int outSoftLimitError;                // Errore superamento limite morbido
        public byte[] axleGenComData = new byte[130]; // Dati comunicazione assi generali
        public int check_sum;                        // Checksum
        public int socketConnTimeout;                // Timeout connessione socket
        public int socketReadTimeout;                // Timeout lettura socket
        public int tsWebStateComErr;                 // Errore comunicazione stato TS Web
        public int exaxisCoordID;                  // ID sistema coordinate asse esteso
    }

Classe Risultato Configurazione Feedback Stato Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Classe risultato configurazione feedback stato robot, contiene lista stati e periodo
    */
    public static class StateConfigResult {
      public final List<RobotState> stateList;
      public final int period;
    }

Tipo Enumerato Configurazione Feedback Stato Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * Tipo enumerato stato robot
    * Utilizzato per la configurazione del feedback di stato in tempo reale
    */
    enum class RobotState
    {
        ProgramState,           // Stato esecuzione programma, 1-arrestato; 2-in esecuzione; 3-in pausa
        RobotState,             // Stato movimento robot, 1-arrestato; 2-in movimento; 3-in pausa; 4-traino
        MainCode,               // Codice guasto principale
        SubCode,                // Codice guasto secondario
        RobotMode,              // Modalità robot, 1-modalità manuale; 0-modalità automatica
        JointCurPos,            // Posizioni attuali giunti di 6 assi, unità deg
        ToolCurPos,             // Posizione attuale utensile: [0]posizione lungo x(mm), [1]lungo y(mm), [2]lungo z(mm), [3]rotazione attorno X fisso(deg), [4]attorno Y fisso(deg), [5]attorno Z fisso(deg)
        FlangeCurPos,           // Posizione attuale flangia terminale: [0]lungo x(mm), [1]lungo y(mm), [2]lungo z(mm), [3]rotazione attorno X fisso(deg), [4]attorno Y fisso(deg), [5]attorno Z fisso(deg)
        ActualJointVel,         // Velocità attuali 6 giunti, unità deg/s
        ActualJointAcc,         // Accelerazioni attuali 6 giunti, unità deg/s²
        TargetTCPCmpSpeed,      // Velocità composita comando TCP: [0]posizione(mm/s), [1]orientamento(deg/s)
        TargetTCPSpeed,         // Velocità comando TCP: [0]lungo x(mm/s), [1]lungo y(mm/s), [2]lungo z(mm/s), [3]velocità angolare attorno X(deg/s), [4]attorno Y(deg/s), [5]attorno Z(deg/s)
        ActualTCPCmpSpeed,      // Velocità composita effettiva TCP: [0]posizione(mm/s), [1]orientamento(deg/s)
        ActualTCPSpeed,         // Velocità effettiva TCP: [0]lungo x(mm/s), [1]lungo y(mm/s), [2]lungo z(mm/s), [3]velocità angolare attorno X(deg/s), [4]attorno Y(deg/s), [5]attorno Z(deg/s)
        ActualJointTorque,      // Coppie attuali 6 giunti, unità N·m
        Tool,                   // Numero sistema coordinate utensile applicato
        User,                   // Numero sistema coordinate pezzo applicato
        ClDgtOutputH,           // Uscita IO digitale scatola di controllo 15-8
        ClDgtOutputL,           // Uscita IO digitale scatola di controllo 7-0
        TlDgtOutputL,           // Uscita IO digitale utensile 7-0, solo bit0-bit1 validi
        ClDgtInputH,            // Ingresso IO digitale scatola di controllo 15-8
        ClDgtInputL,            // Ingresso IO digitale scatola di controllo 7-0
        TlDgtInputL,            // Ingresso IO digitale utensile 7-0, solo bit0-bit1 validi
        ClAnalogInput,          // Ingresso analogico scatola di controllo: [0]canale 0, [1]canale 1
        TlAnalogInput,          // Ingresso analogico utensile
        FtSensorRawData,        // Dati grezzi sensore coppia-forza: [0]forza lungo x(N), [1]lungo y(N), [2]lungo z(N), [3]coppia attorno x(Nm), [4]attorno y(Nm), [5]attorno z(Nm)
        FtSensorData,           // Dati sensore coppia-forza (elaborati): [0]forza lungo x(N), [1]lungo y(N), [2]lungo z(N), [3]coppia attorno x(Nm), [4]attorno y(Nm), [5]attorno z(Nm)
        FtSensorActive,         // Stato attivazione sensore coppia-forza, 0-reset, 1-attivo
        EmergencyStop,          // Flag arresto emergenza, 0-arresto emergenza non premuto, 1-arresto emergenza premuto
        MotionDone,             // Segnale movimento completato, 1-completato, 0-non completato
        GripperMotiondone,      // Segnale completamento movimento pinza, 1-completato, 0-non completato
        McQueueLen,             // Lunghezza coda comandi movimento
        CollisionState,         // Rilevamento collisione, 1-collisione, 0-nessuna collisione
        TrajectoryPnum,         // Numero punto traiettoria
        SafetyStop0State,       // Segnale arresto sicurezza SI0
        SafetyStop1State,       // Segnale arresto sicurezza SI1
        GripperFaultId,         // Numero pinza guasta
        GripperFault,           // Guasto pinza
        GripperActive,          // Stato attivazione pinza
        GripperPosition,        // Posizione pinza
        GripperSpeed,           // Velocità pinza
        GripperCurrent,         // Corrente pinza
        GripperTemp,            // Temperatura pinza
        GripperVoltage,         // Tensione pinza
        AuxState,               // Stato asse esteso 485
        ExtAxisStatus,          // Stato asse esteso UDP (4 assi)
        ExtDIState,             // Ingresso DI esteso (8)
        ExtDOState,             // Uscita DO esteso (8)
        ExtAIState,             // Ingresso AI esteso (4)
        ExtAOState,             // Uscita AO esteso (4)
        RbtEnableState,         // Stato abilitazione robot
        JointDriverTorque,      // Coppia driver giunti robot (6 giunti)
        JointDriverTemperature, // Temperatura driver giunti robot (6 giunti)
        RobotTime,              // Tempo sistema robot
        SoftwareUpgradeState,   // Stato aggiornamento software robot
        EndLuaErrCode,          // Stato esecuzione LUA terminale
        ClAnalogOutput,         // Uscita analogica scatola di controllo (2)
        TlAnalogOutput,         // Uscita analogica utensile
        GripperRotNum,          // Giri correnti pinza rotante
        GripperRotSpeed,        // Percentuale velocità corrente pinza rotante
        GripperRotTorque,       // Percentuale coppia corrente pinza rotante
        WeldingBreakOffState,   // Stato interruzione saldatura
        TargetJointTorque,      // Coppia comando giunti (6 giunti)
        SmartToolState,         // Stato pulsanti maniglia SmartTool
        WideVoltageCtrlBoxTemp, // Temperatura scatola di controllo ampia tensione
        WideVoltageCtrlBoxFanCurrent, // Corrente ventola scatola di controllo ampia tensione (mA)
        ToolCoord,              // Valori coordinate utensile correnti: x,y,z,rx,ry,rz
        WobjCoord,              // Valori coordinate pezzo correnti: x,y,z,rx,ry,rz
        ExtoolCoord,            // Valori coordinate utensile esterno correnti: x,y,z,rx,ry,rz
        ExAxisCoord,            // Valori coordinate asse esteso correnti: x,y,z,rx,ry,rz
        Load,                   // Massa carico
        LoadCog,                // Baricentro carico: x,y,z
        LastServoTarget,        // Ultima posizione target ServoJ in coda (6 giunti)
        ServoJCmdNum,           // Conteggio comandi servoJ
        TargetJointPos,         // Posizioni comando 6 giunti, unità °
        TargetJointVel,         // Velocità comando 6 giunti, unità °/s
        TargetJointAcc,         // Accelerazioni comando 6 giunti, unità °/s²
        TargetJointCurrent,     // Correnti comando 6 giunti, unità A
        ActualJointCurrent,     // Correnti attuali 6 giunti, unità A
        ActualTCPForce,         // Coppia terminale robot: x,y,z,rx,ry,rz, unità Nm
        TargetTCPPos,           // Posizione comando TCP robot: x,y,z,rx,ry,rz, unità mm
        CollisionLevel,         // Livello collisione robot (6)
        SpeedScaleManual,       // Percentuale velocità globale modalità manuale
        SpeedScaleAuto,         // Percentuale velocità globale modalità automatica
        LuaLineNum,             // Numero riga programma lua in esecuzione
        AbnomalStop,            // 0-nessuna anomalia; 1-anomalia presente
        CurrentLuaFileName,     // Nome programma lua in esecuzione
        ProgramTotalLine,       // Righe totali programma lua
        SafetyBoxSingal,        // Stato pulsanti scatola pulsanti robot (6)
        WeldVoltage,            // Tensione saldatura V
        WeldCurrent,            // Corrente saldatura
        WeldTrackVel,           // Velocità inseguimento cordone mm/s
        TpdException,           // Superamento limite caricamento traiettorie TPD, 0-non superato, 1-superato
        AlarmRebootRobot,       // Avviso: 1-ciclo di alimentazione necessario dopo rilascio arresto emergenza, 2-anomalia comunicazione giunto richiede ciclo alimentazione
        ModbusMasterConnect,    // bit0-7 corrispondono stato connessione master ModbusTCP 0-7, 0-non connesso, 1-connesso
        ModbusSlaveConnect,     // Stato connessione slave ModbusTCP, 0-non connesso, 1-connesso
        BtnBoxStopSignal,       // Segnale arresto emergenza scatola pulsanti, 0-arresto emergenza rilasciato, 1-arresto emergenza premuto
        DragAlarm,              // Avviso traino: 0-nessun allarme, 1-allarme, 2-anomalia feedback posizione nessun cambio
        SafetyDoorAlarm,        // Avviso porta sicurezza: 0-chiusa, 1-aperta
        SafetyPlaneAlarm,       // Avviso muro sicurezza: 0-non entrato, 1-entrato
        MotonAlarm,             // Avviso movimento
        InterfaceAlarm,         // Avviso ingresso zona interferenza
        UdpCmdState,            // Stato connessione comunicazione UDP porta 20007
        WeldReadyState,         // Stato pronto saldatrice
        AlarmCheckEmergStopBtn, // 0-normale; 1-anomalia comunicazione, controllare pulsante arresto emergenza
        TsTmCmdComError,        // 0-normale; 1-guasto comunicazione comando coppia
        TsTmStateComError,      // 0-normale; 1-guasto comunicazione stato coppia
        CtrlBoxError,           // Errore scatola di controllo
        SafetyDataState,        // Stato dati sicurezza, 0-normale, 1-anomalo
        ForceSensorErrState,    // Timeout connessione sensore di forza, bit0-bit1 corrispondono ID1-ID2
        CtrlOpenLuaErrCode,     // Codici errore protocollo periferiche 4 controller (codice errore 500)
        StrangePosFlag,         // Flag posizione singolare: 0-normale, 1-posizione singolare
        Alarm,                  // Allarme
        DriverAlarm,            // Numero asse allarme driver
        AliveSlaveNumError,     // Errore conteggio slave attivi: 0-normale, 1-errore conteggio
        SlaveComError,          // Errore slave: 0-normale, 1-offline, 2-incoerenza stato, 3-non configurato, 4-errore configurazione, 5-errore inizializzazione, 6-errore inizializzazione comunicazione mailbox
        CmdPointError,          // Errore punto comando
        IOError,                // Errore IO
        GripperError,           // Errore pinza
        FileError,              // Errore file
        ParaError,              // Errore parametro
        ExaxisOutLimitError,    // Errore superamento limite soft asse esterno
        DriverComError,         // Guasto comunicazione driver (6 assi)
        DriverError,            // Numero asse guasto comunicazione driver
        OutSoftLimitError,      // Guasto superamento limite soft
        AxleGenComData,         // Dati feedback trasmissione trasparente terminale robot
        SocketConnTimeout,      // Timeout connessione socket, bit0-bit4 corrispondono socketID 1-4
        SocketReadTimeout,      // Timeout lettura socket, bit0-bit4 corrispondono socketID 1-4
        TsWebStateComErr,       // Guasto comunicazione web-coppia: 0-normale, 1-guasto
        ExaxisCoordID           // ID sistema coordinate asse esteso
    };