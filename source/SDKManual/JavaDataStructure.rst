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
    * @brief Tipo struttura feedback stato robot
    */
    public class ROBOT_STATE_PKG
    {
      public short frame_head = 0;            //Intestazione frame 0x5A5A
      public byte frame_cnt = 0;              //Contatore frame
      public short data_len = 0;              //Lunghezza dati  5
      public int program_state = 0;          //Stato esecuzione programma, 1-fermo; 2-in esecuzione; 3-in pausa
      public int robot_state = 0;            //Stato movimento robot, 1-fermo; 2-in esecuzione; 3-in pausa; 4-trattamento  7
      public int main_code = 0;               //Codice errore principale
      public int sub_code = 0;                //Codice errore secondario
      public int robot_mode = 0;             //Modalità robot, 0-modalità automatica; 1-modalità manuale 16
      public double[] jt_cur_pos  =new double[6];                  //Posizione corrente giunti
      public double[] tl_cur_pos = new double[6];                  //Posa corrente utensile
      public double[] flange_cur_pos = new double[6];              //Posa corrente flangia terminale
      public double[] actual_qd = new double[6];                   //Velocità corrente giunti robot
      public double[] actual_qdd = new double[6];                  //Accelerazione corrente giunti robot
      public double[] target_TCP_CmpSpeed = new double[2];         //Velocità istruzione sintetica TCP robot
      public double[] target_TCP_Speed = new double[6];            //Velocità istruzione TCP robot
      public double[] actual_TCP_CmpSpeed = new double[2];         //Velocità reale sintetica TCP robot
      public double[] actual_TCP_Speed = new double[6];            //Velocità reale TCP robot
      public double[] jt_cur_tor = new double[6];                             //Coppia corrente
      public int tool = 0;                        //Numero utensile
      public int user = 0;                        //Numero pezzo
      public int cl_dgt_output_h = 0;            //Uscite digitali 15-8
      public int cl_dgt_output_l = 0;            //Uscite digitali 7-0
      public int tl_dgt_output_l = 0;            //Uscite digitali utensile 7-0 (solo bit0-bit1 validi)
      public int cl_dgt_input_h = 0;             //Ingressi digitali 15-8
      public int cl_dgt_input_l = 0;             //Ingressi digitali 7-0
      public int tl_dgt_input_l = 0;             //Ingressi digitali utensile 7-0 (solo bit0-bit1 validi)
      public short[] cl_analog_input = new short[2];          //Ingressi analogici box controllo
      public short tl_anglog_input = 0;                       //Ingresso analogico utensile
      public double[] ft_sensor_raw_data = new double[6];     //Dati grezzi sensore forza/coppia
      public double[] ft_sensor_data = new double[6];         //Dati sensore forza/coppia in sistema di riferimento
      public int ft_sensor_active = 0;           //Stato attivazione sensore forza/coppia, 0-reset, 1-attivo
      public int EmergencyStop = 0;              //Segnale emergenza
      public int motion_done = 0;                 //Segnale in posizione
      public int gripper_motiondone = 0;         //Segnale completamento movimento pinza
      public int mc_queue_len = 0;                //Lunghezza coda movimento
      public int collisionState = 0;             //Rilevamento collisione, 1-collisione; 0-nessuna collisione
      public int trajectory_pnum = 0;             //Numero punto traiettoria
      public int safety_stop0_state = 0;  /* Segnale arresto sicurezza SI0 */
      public int safety_stop1_state = 0;  /* Segnale arresto sicurezza SI1 */
      public int gripper_fault_id = 0;    /* Numero pinza errore */               // + 19 = 567
      public short gripper_fault = 0;      /* Guasto pinza */
      public short gripper_active = 0;     /* Stato attivazione pinza */
      public int gripper_position = 0;    /* Posizione pinza */
      public int gripper_speed = 0;       /* Velocità pinza */
      public int gripper_current = 0;     /* Corrente pinza */
      public int gripper_tmp = 0;          /* Temperatura pinza */
      public int gripper_voltage = 0;      /* Tensione pinza */
      public ROBOT_AUX_STATE auxState = new ROBOT_AUX_STATE(); /* Stato assi estesi 485 */
      public EXT_AXIS_STATUS extAxisStatus0 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus1 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus2 = new EXT_AXIS_STATUS();
      public EXT_AXIS_STATUS extAxisStatus3 = new EXT_AXIS_STATUS();
      public short[] extDIState = new short[8];        //Ingressi digitali estesi
      public short[] extDOState = new short[8];        //Uscite digitali estese
      public short[] extAIState = new short[4];        //Ingressi analogici estesi
      public short[] extAOState = new short[4];        //Uscite analogiche estese
      public int rbtEnableState = 0;       //Stato abilitazione robot --robot enable s
      public double[] jointDriverTorque  =new double[6];       //Coppia corrente driver giunti
      public double[] jointDriverTemperature = new double[6];  //Temperatura corrente driver giunti
      public ROBOT_TIME robotTime = new ROBOT_TIME();
      public int softwareUpgradeState = 0;   //Stato aggiornamento software robot 0-inattivo o caricamento pacchetto; 1~100: percentuale completamento; -1: fallimento aggiornamento; -2: fallimento verifica; -3: fallimento verifica versione; -4: fallimento decompressione; -5: fallimento aggiornamento configurazione utente; -6: fallimento aggiornamento configurazione periferiche; -7: fallimento aggiornamento configurazione assi estesi; -8: fallimento aggiornamento configurazione robot; -9: fallimento aggiornamento parametri DH
      public int endLuaErrCode;              //Stato esecuzione LUA terminale

      public int[] cl_analog_output = new int[2];  //Uscite analogiche box controllo
      public int tl_analog_output;              //Uscita analogica utensile
      public float gripperRotNum;               //Numero giri corrente pinza rotante
      public int gripperRotSpeed;                //Velocità rotazione percentuale corrente pinza rotante
      public int gripperRotTorque;	            //Coppia rotazione percentuale corrente pinza rotante

      public  WELDING_BREAKOFF_STATE weldingBreakOffstate=new WELDING_BREAKOFF_STATE();//Stato interruzione saldatura

      public double[] jt_tgt_tor = new double[6];    //Coppia istruzione giunti
      public int smartToolState;         //Stato pulsanti manopola SmartTool

      public float wideVoltageCtrlBoxTemp;        //Temperatura box controllo tensione ampia
      public int wideVoltageCtrlBoxFanVel;   //Velocità ventilatore box controllo tensione ampia (mA)

      public double[] toolCoord=new double[6];           //Sistema di coordinate utensile
      public double[] wobjCoord=new double[6];		   //Sistema di coordinate pezzo
      public double[] extoolCoord=new double[6];		   //Sistema di coordinate utensile esterno
      public double[] exAxisCoord=new double[6];		   //Sistema di coordinate assi estesi
      public double load;                   //Massa carico
      public double[] loadCog=new double[3];             //Baricentro carico

      public double[] lastServoTarget=new double[6];      //Ultima posizione target servo in coda
      public int servoJCmdNum;                            //Conteggio istruzioni servo

      public short check_sum = 0;          /* Checksum */

      public ROBOT_STATE_PKG()
      {

      }
    }