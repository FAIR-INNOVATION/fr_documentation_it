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
    public struct ROBOT_STATE_PKG
    {
        public UInt16 frame_head;           // Intestazione del frame 0x5A5A
        public byte frame_cnt;              // Contatore frame
        public UInt16 data_len;             // Lunghezza dati  5
        public byte program_state;          // Stato di esecuzione del programma, 1-arrestato; 2-in esecuzione; 3-in pausa
        public byte robot_state;            // Stato di movimento del robot, 1-arrestato; 2-in esecuzione; 3-in pausa; 4-in trascinamento  7
        public int main_code;               // Codice guasto principale
        public int sub_code;                // Codice guasto secondario
        public byte robot_mode;             // Modalità robot, 0-modalità automatica; 1-modalità manuale 16

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_pos;                             // Posizione corrente dei giunti
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] tl_cur_pos;                             // Posa corrente dell'utensile
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] flange_cur_pos;                         // Posa corrente della flangia finale
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qd;                              // Velocità corrente dei giunti del robot
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_qdd;                             // Accelerazione corrente dei giunti del robot  16 + 8 * 6 * 5 = 256
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] target_TCP_CmpSpeed;                    // Velocità di comando sintetica TCP del robot                        
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] target_TCP_Speed;                       // Velocità di comando TCP del robot                        
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public double[] actual_TCP_CmpSpeed;                    // Velocità effettiva sintetica TCP del robot                     
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] actual_TCP_Speed;                       // Velocità effettiva TCP del robot                     
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_cur_tor;                             // Coppia corrente       
        public int tool;                        // Numero utensile
        public int user;                        // Numero pezzo
        public byte cl_dgt_output_h;            // Uscita digitale 15-8
        public byte cl_dgt_output_l;            // Uscita digitale 7-0
        public byte tl_dgt_output_l;            // Uscita digitale utensile 7-0 (solo bit0-bit1 validi)
        public byte cl_dgt_input_h;             // Ingresso digitale 15-8
        public byte cl_dgt_input_l;             // Ingresso digitale 7-0
        public byte tl_dgt_input_l;             // Ingresso digitale utensile 7-0 (solo bit0-bit1 validi)                  
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public UInt16[] cl_analog_input;        // Ingresso analogico del quadro di controllo
        public UInt16 tl_anglog_input;          // Ingresso analogico dell'utensile                            
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_raw_data;     // Dati grezzi del sensore di forza/coppia
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] ft_sensor_data;         // Dati del sensore di forza/coppia                          
        public byte ft_sensor_active;           // Stato di attivazione del sensore di forza/coppia, 0-ripristinato, 1-attivato
        public byte EmergencyStop;              // Segnale arresto di emergenza
        public int motion_done;                 // Segnale di posizione raggiunta
        public byte gripper_motiondone;         // Segnale di completamento movimento pinza
        public int mc_queue_len;                // Lunghezza coda movimento
        public byte collisionState;             // Rilevamento collisione, 1-collisione; 0-nessuna collisione
        public int trajectory_pnum;             // Numero punto traiettoria
        public byte safety_stop0_state;  /* Segnale arresto sicurezza SI0 */
        public byte safety_stop1_state;  /* Segnale arresto sicurezza SI1 */
        public byte gripper_fault_id;    /* Numero pinza in errore */             
        public UInt16 gripper_fault;     /* Guasto pinza */
        public UInt16 gripper_active;    /* Stato di attivazione pinza */
        public byte gripper_position;    /* Posizione pinza */
        public byte gripper_speed;       /* Velocità pinza */
        public byte gripper_current;     /* Corrente pinza */
        public int gripper_tmp;          /* Temperatura pinza */
        public int gripper_voltage;      /* Tensione pinza */                 
        public ROBOT_AUX_STATE auxState; /* Stato asse esteso 485 */          
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public EXT_AXIS_STATUS[] extAxisStatus;  /* Stato asse esteso UDP */
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDIState;        // Ingresso DI esteso
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
        public UInt16[] extDOState;        // Uscita DO estesa
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAIState;        // Ingresso AI esteso
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
        public UInt16[] extAOState;        // Uscita AO estesa
        public int rbtEnableState;       // Stato di abilitazione del robot -- robot enable state
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTorque;               // Coppia del driver del giunto
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jointDriverTemperature;          // Temperatura del driver del giunto
        public ROBOT_TIME robotTime;     // Ora di sistema del robot
        public int softwareUpgradeState; // Stato aggiornamento software  0-inattivo o caricamento pacchetto aggiornamento in corso; 1~100: percentuale completamento aggiornamento; -1: aggiornamento software fallito; -2: verifica fallita; -3: verifica versione fallita; -4: decompressione fallita; -5: aggiornamento configurazione utente fallito; -6: aggiornamento configurazione periferiche fallito; -7: aggiornamento configurazione asse esteso fallito; -8: aggiornamento configurazione robot fallito; -9: aggiornamento parametri DH fallito
        public UInt16 endLuaErrCode;    // Stato di esecuzione LUA finale 
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 2)]
        public  UInt16[] cl_analog_output;  // Uscita analogica del quadro di controllo				  Control box analog output
        public UInt16 tl_analog_output;     // Uscita analogica dell'utensile				  Tool analog output
        public float gripperRotNum;           // Numero di giri corrente della pinza rotante			  The current number of turns of the rotating clamp
        public byte gripperRotSpeed;       // Percentuale velocità di rotazione corrente della pinza rotante	  Percentage of the current rotation speed of the rotary clamp
        public byte gripperRotTorque;	   // Percentuale coppia di rotazione corrente della pinza rotante	  Percentage of the current rotating torque of the rotating clamp
        public WELDING_BREAKOFF_STATE weldingBreakOffState;// Stato di interruzione della saldatura

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] jt_tgt_tor;// Coppia di comando dei giunti
        public int smartToolState; // Stato pulsanti della maniglia SmartTool
        public float wideVoltageCtrlBoxTemp;        // Temperatura del quadro di controllo a tensione ampia
        public UInt16 wideVoltageCtrlBoxFanVel;   // Corrente ventola del quadro di controllo a tensione ampia (mA)

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] toolCoord;         // Sistema di coordinate dell'utensile
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] wobjCoord;         // Sistema di coordinate del pezzo
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] extoolCoord;        // Sistema di coordinate dell'utensile esterno
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] exAxisCoord;          // Sistema di coordinate dell'asse esteso
        public double load;                   // Massa del carico

        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 3)]
        public double[] loadCog;           // Centro di gravità del carico
        [MarshalAs(UnmanagedType.ByValArray, SizeConst = 6)]
        public double[] lastServoTarget;// Posizione target servoJ ultima nella coda

        public int servoJCmdNum;// Conteggio comandi servoJ
        public UInt16 check_sum;         /* Checksum di somma */                     
    }