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

Pacchetto Dati di Feedback sullo Stato del Controllore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Pacchetto dati di feedback sullo stato del controllore
     */
    typedef struct _ROBOT_STATE_PKG
    {
        uint16_t frame_head;      // Intestazione frame, convenzionalmente 0x5A5A 
        uint8_t  frame_cnt;       // Contatore frame, conteggio ciclico 0-255 
        uint16_t data_len;        // Lunghezza del contenuto dei dati 
        uint8_t  program_state;   // Stato di esecuzione del programma, 1-fermo; 2-in esecuzione; 3-in pausa;
        uint8_t  robot_state;     // Stato di movimento del robot, 1-fermo; 2-in esecuzione; 3-in pausa; 4-trainabile 
        int      main_code;       // Codice guasto principale 
        int      sub_code;        // Codice guasto secondario 
        uint8_t  robot_mode;      // Modalità robot, 1-modalità manuale; 0-modalità automatica; 
        double   jt_cur_pos[6];   // Posizioni articolari correnti dei 6 assi, unità deg 
        double   tl_cur_pos[6];   // Posizione corrente dell'utensile
                                  // tl_cur_pos[0], posizione lungo l'asse x, unità mm,
                                  // tl_cur_pos[1], posizione lungo l'asse y, unità mm,
                                  // tl_cur_pos[2], posizione lungo l'asse z, unità mm,
                                  // tl_cur_pos[3], angolo di rotazione attorno all'asse fisso X, unità deg
                                  // tl_cur_pos[4], angolo di rotazione attorno all'asse fisso y, unità deg
                                  // tl_cur_pos[5], angolo di rotazione attorno all'asse fisso z, unità deg 
        double   flange_cur_pos[6]; // Posizione corrente della flangia terminale
                                    // flange_cur_pos[0], posizione lungo l'asse x, unità mm,
                                    // flange_cur_pos[1], posizione lungo l'asse y, unità mm,
                                    // flange_cur_pos[2], posizione lungo l'asse z, unità mm,
                                  // flange_cur_pos[3], angolo di rotazione attorno all'asse fisso X, unità deg
                                  // flange_cur_pos[4], angolo di rotazione attorno all'asse fisso y, unità deg
                                  // flange_cur_pos[5], angolo di rotazione attorno all'asse fisso z, unità deg
        double   actual_qd[6];      // Velocità correnti delle 6 articolazioni, unità deg/s 
        double   actual_qdd[6];     // Accelerazioni correnti delle 6 articolazioni, unità deg/s^2 
        double   target_TCP_CmpSpeed[2]; 
    // target_TCP_CmpSpeed[0], velocità istruzionale sintetica TCP (posizione), unità mm/s
                     // target_TCP_CmpSpeed[1], velocità istruzionale sintetica TCP (orientamento), unità deg/s  */
        double   target_TCP_Speed[6];    // Velocità istruzionale TCP
                         // target_TCP_Speed[0], velocità lungo l'asse x, unità mm/s,
                         // target_TCP_Speed[1], velocità lungo l'asse y, unità mm/s,
                         // target_TCP_Speed[2], velocità lungo l'asse z, unità mm/s,
                         // target_TCP_Speed[3], velocità angolare di rotazione attorno all'asse fisso X, unità deg/s
                         // target_TCP_Speed[4], velocità angolare di rotazione attorno all'asse fisso y, unità deg/s
                         // target_TCP_Speed[5], velocità angolare di rotazione attorno all'asse fisso z, unità deg/s */
        double   actual_TCP_CmpSpeed[2]; 
    // actual_TCP_CmpSpeed[0], velocità reale sintetica TCP (posizione), unità mm/s
                  // actual_TCP_CmpSpeed[1], velocità reale sintetica TCP (orientamento), unità deg/s 
        double   actual_TCP_Speed[6];    // Velocità reale TCP
                        // actual_TCP_Speed[0], velocità lungo l'asse x, unità mm/s,
                        // actual_TCP_Speed[1], velocità lungo l'asse y, unità mm/s,
                        // actual_TCP_Speed[2], velocità lungo l'asse z, unità mm/s,
                        // actual_TCP_Speed[3], velocità angolare di rotazione attorno all'asse fisso X, unità deg/s
                        // actual_TCP_Speed[4], velocità angolare di rotazione attorno all'asse fisso y, unità deg/s
                        // actual_TCP_Speed[5], velocità angolare di rotazione attorno all'asse fisso z, unità deg/s 
        double   jt_cur_tor[6];      // Coppia corrente dei 6 assi, unità N·m 
        int      tool;               // Numero del sistema di coordinate utensile applicato 
        int      user;               // Numero del sistema di coordinate pezzo applicato 
        uint8_t  cl_dgt_output_h;    // Uscite digitali IO del cabinet di controllo 15-8 
        uint8_t  cl_dgt_output_l;    // Uscite digitali IO del cabinet di controllo 7-0 
        uint8_t  tl_dgt_output_l;    // Uscite digitali IO dell'utensile 7-0, solo bit0-bit1 validi 
        uint8_t  cl_dgt_input_h;     // Ingressi digitali IO del cabinet di controllo 15-8 
        uint8_t  cl_dgt_input_l;     // Ingressi digitali IO del cabinet di controllo 7-0 
        uint8_t  tl_dgt_input_l;     // Ingressi digitali IO dell'utensile 7-0, solo bit0-bit1 validi 
        uint16_t cl_analog_input[2]; // cl_analog_input[0], ingresso analogico 0 del cabinet di controllo
                                     //cl_analog_input[1], ingresso analogico 1 del cabinet di controllo 
        uint16_t tl_anglog_input;    // Ingresso analogico dell'utensile 
        double   ft_sensor_raw_data[6]; // Dati grezzi del sensore di forza/coppia
                                      // ft_sensor_raw_data[0], forza lungo l'asse x, unità N
                                      // ft_sensor_raw_data[1], forza lungo l'asse y, unità N
                                      // ft_sensor_raw_data[2], forza lungo l'asse z, unità N
                                      // ft_sensor_raw_data[3], momento lungo l'asse x, unità Nm
                                      // ft_sensor_raw_data[4], momento lungo l'asse y, unità Nm
                                      // ft_sensor_raw_data[5], momento lungo l'asse z, unità Nm 
        double   ft_sensor_data[6];     // Dati del sensore di forza/coppia,
                                        // ft_sensor_data[0], forza lungo l'asse x, unità N
                                        // ft_sensor_data[1], forza lungo l'asse y, unità N
                                        // ft_sensor_data[2], forza lungo l'asse z, unità N
                                        // ft_sensor_data[3], momento lungo l'asse x, unità Nm
                                        // ft_sensor_data[4], momento lungo l'asse y, unità Nm
                                        // ft_sensor_data[5], momento lungo l'asse z, unità Nm 
        uint8_t  ft_sensor_active;   // Stato di attivazione del sensore di forza/coppia, 0-reset, 1-attivo 
        uint8_t  EmergencyStop;      // Indicatore di arresto di emergenza, 0-non premuto, 1-premuto 
        int      motion_done;        // Segnale di raggiungimento movimento, 1-raggiunto, 0-non raggiunto 
        uint8_t  gripper_motiondone; // Segnale di completamento movimento della pinza, 1-completato, 0-non completato 
        int      mc_queue_len;       // Lunghezza della coda dei comandi di movimento 
        uint8_t  collisionState;     // Rilevamento collisione, 1-collisione, 0-nessuna collisione 
        int      trajectory_pnum;    // Numero del punto di traiettoria 
        uint8_t  safety_stop0_state; // Segnale di arresto di sicurezza SI0 
        uint8_t  safety_stop1_state; // Segnale di arresto di sicurezza SI1 
        uint8_t  gripper_fault_id;   // Numero pinza in errore 
        uint16_t gripper_fault;      // Guasto pinza 
        uint16_t gripper_active;     // Stato di attivazione della pinza 
        uint8_t  gripper_position;   // Posizione della pinza 
        int8_t   gripper_speed;      // Velocità della pinza 
        int8_t   gripper_current;    // Corrente della pinza 
        int      gripper_temp;       // Temperatura della pinza 
        int      gripper_voltage;    // Tensione della pinza 
        robot_aux_state aux_state;   // Stato assi estesi 485
        EXT_AXIS_STATUS extAxisStatus[4];  // Stato assi estesi UDP 
        uint16_t extDIState[8];        // Ingressi DI estesi
        uint16_t extDOState[8];        // Uscite DO estese
        uint16_t extAIState[4];        // Ingressi AI estesi
        uint16_t extAOState[4];        // Uscite AO estese
        int rbtEnableState;            // Stato di abilitazione del robot
        double   jointDriverTorque[6];        // Coppia degli azionamenti articolari del robot
        double   jointDriverTemperature[6];   // Temperatura degli azionamenti articolari del robot
        RobotTime robotTime;           // Tempo di sistema del robot
        int softwareUpgradeState;      // Stato aggiornamento software del robot
        uint16_t endLuaErrCode;        // Stato esecuzione LUA terminale
        uint16_t cl_analog_output[2];  // Uscite analogiche del cabinet di controllo
        uint16_t tl_analog_output;     // Uscita analogica dell'utensile
        float gripperRotNum;           // Numero corrente di giri della pinza rotante
        uint8_t gripperRotSpeed;       // Velocità corrente di rotazione della pinza rotante (percentuale)
        uint8_t gripperRotTorque;      // Coppia corrente di rotazione della pinza rotante (percentuale)
        WELDING_BREAKOFF_STATE weldingBreakOffState;  // Stato interruzione saldatura
        double jt_tgt_tor[6];                 // Coppia istruzionale articolare
        int smartToolState;                   // Stato pulsanti del joystick SmartTool
        float wideVoltageCtrlBoxTemp;         // Temperatura del cabinet di controllo a tensione ampia
        uint16_t wideVoltageCtrlBoxFanCurrent;// Corrente della ventola del cabinet di controllo a tensione ampia (mA)
        double toolCoord[6];        // Sistema di coordinate utensile
        double wobjCoord[6];        // Sistema di coordinate pezzo
        double extoolCoord[6];      // Sistema di coordinate utensile esterno
        double exAxisCoord[6];      // Sistema di coordinate assi estesi
        double load;                // Massa del carico
        double loadCog[3];          // Centro di gravità del carico
        double lastServoTarget[6];  // Posizione target dell'ultimo ServoJ nella coda
        int servoJCmdNum;           // Conteggio comandi servoJ
        uint16_t check_sum;         // Checksum
    }ROBOT_STATE_PKG;