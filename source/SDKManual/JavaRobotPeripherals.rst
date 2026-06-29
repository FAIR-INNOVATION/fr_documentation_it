Periferiche del Robot
=====================

.. toctree:: 
    :maxdepth: 5

Configurare la pinza
++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configurare la pinza
    * @param  [in] config .company  produttore della pinza, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [in] config .device  numero dispositivo, Robotiq(0-serie 2F-85), Huiling(0-serie NK,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [in] config .softvesion  numero versione software, non utilizzato attualmente, default 0
    * @param  [in] config .bus posizione bus terminale del dispositivo, non utilizzato attualmente, default 0
    * @return  Codice errore
    */
    int SetGripperConfig(DeviceConfig config);

Ottenere la configurazione della pinza
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la configurazione della pinza
    * @param  [out] config .company  produttore della pinza, 1-Robotiq, 2-Huiling, 3-Tianji, 4-Dahuan, 5-Zhixing
    * @param  [out] config .device  numero dispositivo, Robotiq(0-serie 2F-85), Huiling(0-serie NK,1-Z-EFG-100), Tianji(0-TEG-110), Dahuan(0-PGI-140), Zhixing(0-CTPM2F20)
    * @param  [out] config .softvesion  numero versione software, non utilizzato attualmente, default 0
    * @param  [out] config .bus posizione bus terminale del dispositivo, non utilizzato attualmente, default 0
    * @return  Codice errore
    */
    int GetGripperConfig(DeviceConfig config);

Attivare la pinza
+++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Attivare la pinza
    * @param  [in] index  numero pinza
    * @param  [in] act  0-reset, 1-attiva
    * @return  Codice errore
    */
    int ActGripper(int index, int act); 

Controllare la pinza
++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controllare la pinza
    * @param  [in] index  numero pinza
    * @param  [in] pos  percentuale posizione, range [0~100]
    * @param  [in] vel  percentuale velocità, range [0~100]
    * @param  [in] force  percentuale coppia, range [0~100]
    * @param  [in] max_time  tempo attesa massimo, range [0~30000], unità ms
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [in] type tipo pinza, 0-pinza parallela; 1-pinza rotante
    * @param  [in] rotNum numero giri rotazione
    * @param  [in] rotVel percentuale velocità rotazione [0-100]
    * @param  [in] rotTorque percentuale coppia rotazione [0-100]
    * @return Codice errore
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, int block, int type, double rotNum, int rotVel, int rotTorque); 

Ottenere lo stato di movimento della pinza
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere lo stato di movimento della pinza
    * @return List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]: staus  0-movimento non completato, 1-movimento completato
    */
    List<Integer> GetGripperMotionDone(); 

Ottenere lo stato di attivazione della pinza
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere lo stato di attivazione della pinza
    * @return  List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]: status  bit0~bit15 corrispondono numeri pinza 0~15, bit=0 non attivato, bit=1 attivato
    */
    List<Number> GetGripperActivateStatus()

Ottenere la posizione della pinza
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la posizione della pinza
    * @return  List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]: position  percentuale posizione, range 0~100%
    */
    List<Number> GetGripperCurPosition()

Ottenere la velocità della pinza
+++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la velocità della pinza
    * @return  List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]: speed  percentuale velocità, range 0~100%
    */
    List<Number> GetGripperCurSpeed()

Ottenere la corrente della pinza
+++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la corrente della pinza
    * @return  List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]: current  percentuale corrente, range 0~100%
    */
    List<Number> GetGripperCurCurrent()

Ottenere la tensione della pinza
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la tensione della pinza
    * @return List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]:voltage  tensione, unità 0.1V
    */
    List<Number> GetGripperVoltage()

Ottenere la temperatura della pinza
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere la temperatura della pinza
    * @return List[0]: codice errore; List[1] : fault  0-nessun errore, 1-errore presente; List[2]:temp  temperatura, unità ℃
    */
    List<Number> GetGripperTemp()

Calcolare punto di pre-presa - visione
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcolare punto di pre-presa - visione 
    * @param [in] desc_pos  posa cartesiana punto presa
    * @param [in] zlength   offset asse z
    * @param [in] zangle    offset rotazione asse z
    * @param [out] pre_pos  punto ottenuto
    * @return Codice errore 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, DescPose pre_pos);

Calcolare punto di ritiro - visione
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcolare punto di ritiro - visione 
    * @param [in] desc_pos  posa cartesiana punto presa
    * @param [in] zlength   offset asse z 
    * @param [in] zangle    offset rotazione asse z
    * @param [out] post_poss punto ritiro
    * @return Codice errore 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, DescPose post_pos);

Esempio di codice operazione pinza robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGripper(Robot robot)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        int act = 0;
        int max_time = 30000;
        int block = 0;

        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        DeviceConfig cnn=new DeviceConfig(company,device,softversion,bus);
        robot.SetGripperConfig(cnn);
        robot.GetGripperConfig(cnn);

        robot.ActGripper(index, act);
        robot.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        robot.Sleep(1000);

        robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
        robot.Sleep(1000);
        robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);

        List<Integer> stat=new ArrayList<>();
        stat=robot.GetGripperMotionDone();

        List<Number> list=new ArrayList<>();
        list=robot.GetGripperActivateStatus();

        list=robot.GetGripperCurPosition();

        list=robot.GetGripperCurCurrent();

        list=robot.GetGripperVoltage();

        list=robot.GetGripperTemp();

        list=robot.GetGripperCurSpeed();

        int retval = 0;
        DescPose prepick_pose = new DescPose(){};
        DescPose postpick_pose = new DescPose(){};

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        retval = robot.ComputePrePick(p1Desc, 10, 0, prepick_pose);

        retval = robot.ComputePostPick(p2Desc, -10, 0, postpick_pose);
        return 0;
    }

Ottenere numero giri pinza rotante
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere numero giri pinza rotante
    * @return List[0]: codice errore List[1]: 0-nessun errore, 1-errore presente List[2]: numero giri rotazione
    */
    List<Number> GetGripperRotNum(); 

Ottenere percentuale velocità rotazione pinza rotante
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere percentuale velocità rotazione pinza rotante
    * @return List[0]: codice errore List[1]: 0-nessun errore, 1-errore presente List[2]: percentuale velocità rotazione
    */
    List<Number> GetGripperRotSpeed(); 

Ottenere percentuale coppia rotazione pinza rotante
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere percentuale coppia rotazione pinza rotante
    * @return List[0]: codice errore List[1]: 0-nessun errore, 1-errore presente List[2]: percentuale coppia rotazione
    */
    List<Number> GetGripperRotTorque(); 

Esempio di codice stato pinza rotante
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRotGripperState(Robot robot)
    {
        int fault = 0;
        List<Number> rotNum=new ArrayList<>();
        List<Number> rotSpeed=new ArrayList<>();
        List<Number> rotTorque=new ArrayList<>();

        rotNum=robot.GetGripperRotNum();
        rotSpeed=robot.GetGripperRotSpeed();
        rotTorque=robot.GetGripperRotTorque();
        System.out.println("gripper rot num :"+rotNum.get(2)+ ", gripper rotSpeed :"+rotSpeed.get(2)+",gripper rotTorque : "+rotTorque.get(2));

        return 0;
    }

Avvio, arresto nastro trasportatore
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Avvio, arresto nastro trasportatore
    * @param  [in] status stato, 1-avvia, 0-arresta
    * @return  Codice errore
    */
    int ConveyorStartEnd(int status);

Registrare punto rilevamento IO
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrare punto rilevamento IO
    * @return  Codice errore
    */
    int ConveyorPointIORecord();

Registrare punto A
++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrare punto A
    * @return  Codice errore
    */
    int ConveyorPointARecord(); 

Registrare punto di riferimento
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrare punto di riferimento
    * @return  Codice errore
    */
    int ConveyorRefPointRecord();

Registrare punto B
++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrare punto B
    * @return Codice errore
    */
    int ConveyorPointBRecord(); 

Rilevamento IO pezzo nastro trasportatore
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Rilevamento IO pezzo nastro trasportatore
    * @param [in] max_t tempo rilevamento massimo, unità ms
    * @return Codice errore 
    */ 
    int ConveyorIODetect(int max_t);

Ottenere posizione attuale oggetto
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere posizione attuale oggetto
    * @param [in] mode 1-tracciamento presa, 2-tracciamento movimento, 3-tracciamento TPD
    * @return Codice errore 
    */ 
    int ConveyorGetTrackData(int mode);

Avvio tracciamento nastro trasportatore
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Avvio tracciamento nastro trasportatore
    * @param [in] status stato, 1-avvia, 0-arresta
    * @return Codice errore 
    */ 
    int ConveyorTrackStart(int status);

Arresto tracciamento nastro trasportatore
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Arresto tracciamento nastro trasportatore
    * @return Codice errore 
    */ 
    int ConveyorTrackEnd();

Configurazione parametri nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief  Configurazione parametri nastro trasportatore
    * @param [in] encChannel canale encoder 1~2
    * @param [in] resolution impulsi per giro encoder
    * @param [in] lead distanza percorrenza nastro per giro encoder
    * @param [in] wpAxis numero sistema coordinato pezzo per funzione tracciamento movimento, tracciamento presa/TPD impostare 0
    * @param [in] vision se dotato visione 0 no 1 si
    * @param [in] speedRadio rapporto velocità per opzione tracciamento presa (1-100) altre opzioni default 1
    * @param [in] followType tipo movimento tracciamento, 0-tracciamento movimento; 1-movimento inseguimento ispezione
    * @param [in] startDis necessario per presa inseguimento ispezione, distanza inizio tracciamento, -1: calcolo automatico (inseguimento automatico dopo arrivo pezzo sotto robot), unità mm, default 0
    * @param [in] endDis necessario per presa inseguimento ispezione, distanza fine tracciamento, unità mm, default 100
    * @return Codice errore
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis, int endDis); 

Impostare compensazione punto presa nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare compensazione punto presa nastro trasportatore
    * @param [in] cmp posizione compensazione double[3]{x, y, z}
    * @return Codice errore 
    */ 
    int ConveyorCatchPointComp(Object[] cmp);

Movimento lineare nastro trasportatore
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimento lineare
    * @param [in] name descrizione punto movimento
    * @param [in] tool numero coordinata utensile, range [0~14]
    * @param [in] wobj numero coordinata pezzo, range [0~14]
    * @param [in] vel percentuale velocità, range [0~100]
    * @param [in] acc percentuale accelerazione, range [0~100], non aperto attualmente
    * @param [in] ovl fattore scala velocità, range [0~100]
    * @param [in] blendR [-1.0]-movimento a posizione (bloccante), [0~1000.0]-raggio smooth (non bloccante), unità mm
    * @return Codice errore 
    */ 
    int ConveyorTrackMoveL(String name, int tool, int wobj, double vel, double acc, double ovl, double blendR);   

Rilevamento input comunicazione nastro trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Rilevamento input comunicazione nastro trasportatore
    * @param [in] timeout tempo attesa timeout ms
    * @return Codice errore
    */
    int ConveyorComDetect(int timeout);

Trigger rilevamento input comunicazione nastro trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Trigger rilevamento input comunicazione nastro trasportatore
    * @param [in] timeout tempo attesa timeout ms
    * @return Codice errore
    */
    int ConveyorComDetectTrigger();

Esempio programma operazione nastro trasportatore robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestConveyor(Robot robot)
    {
        int retval = 0;

        retval = robot.ConveyorStartEnd(1);

        retval = robot.ConveyorPointIORecord();

        retval = robot.ConveyorPointARecord();

        retval = robot.ConveyorRefPointRecord();

        retval = robot.ConveyorPointBRecord();

        retval = robot.ConveyorStartEnd(0);

        retval = 0;

        retval = robot.ConveyorSetParam(1,10000,200,0,0,20,0,0,100);

        Object[] cmp = new Object[]{ 0.0, 0.0, 0.0 };
        retval = robot.ConveyorCatchPointComp(cmp);

        int index = 1;
        int max_time = 30000;
        int block = 0;
        retval = 0;

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);


        retval = robot.MoveCart(p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.WaitMs(1);

        retval = robot.ConveyorTrackStart(1);

        retval = robot.ConveyorTrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);

        retval = robot.ConveyorTrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0);

        retval = robot.ConveyorTrackEnd();

        robot.MoveCart(p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);

        retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);

        return 0;
    }

Configurazione sensore terminale
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Configurazione sensore terminale
    * @param [in] config idCompany produttore, 18-JUNKONG; 25-HUIDE
    * @param [in] config idDevice tipo, 0-JUNKONG/RYR6T.V1.0
    * @param [in] config idSoftware versione software, 0-J1.0/HuiDe1.0 (non aperto attualmente)
    * @param [in] config idBus posizione montaggio, 1-porta terminale 1; 2-porta terminale 2...8-porta terminale 8 (non aperto attualmente)
    * @return Codice errore
    */
    int AxleSensorConfig(DeviceConfig config);

Ottenere configurazione sensore terminale
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere configurazione sensore terminale
    * @param [out] config idCompany produttore, 18-JUNKONG; 25-HUIDE
    * @param [out] config idDevice tipo, 0-JUNKONG/RYR6T.V1.0
    * @return Codice errore
    */
    int AxleSensorConfigGet(DeviceConfig config);

Attivazione sensore terminale
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Attivazione sensore terminale
    * @param [in] actFlag 0-reset; 1-attiva
    * @return Codice errore
    */
    int AxleSensorActivate(int actFlag);

Scrittura registro sensore terminale
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Scrittura registro sensore terminale
    * @param [in] devAddr  numero indirizzo dispositivo 0-255
    * @param [in] regHAddr indirizzo registro 8 bit alti
    * @param [in] regLAddr indirizzo registro 8 bit bassi
    * @param [in] regNum  numero registri 0-255
    * @param [in] data1 valore registro scritto 1
    * @param [in] data2 valore registro scritto 2
    * @param [in] isNoBlock 0-bloccante; 1-non bloccante
    * @return Codice errore
    */
    int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Esempio di codice sensore terminale
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAxleSensor(Robot robot)
    {
        DeviceConfig con=new DeviceConfig(18,0,0,1);
        robot.AxleSensorConfig(con);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(con);

        int rtn = robot.AxleSensorActivate(1);

        robot.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        return 0;
    }

Ottenere protocollo periferiche robot
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere protocollo periferiche robot
    * @return List[0]: codice errore; List[1] : int protocol numero protocollo periferiche robot 4096-scheda controllo asse estensione; 4097-ModbusSlave; 4098-ModbusMaster 
    */
    List<Integer> GetExDevProtocol();

Impostare protocollo periferiche robot
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare protocollo periferiche robot
    * @param [in] protocol numero protocollo periferiche robot 4096-scheda controllo asse estensione; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Codice errore 
    */
    int SetExDevProtocol(int protocol);

Esempio programma impostazione protocollo periferiche robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExDevProtocol(Robot robot)
    {
        int protocol = 4096;
        int rtn = robot.SetExDevProtocol(protocol);
        List<Integer> integer=new ArrayList<>();
        integer = robot.GetExDevProtocol();

        return 0;
    }

Ottenere parametri comunicazione terminale
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere parametri comunicazione terminale
    * @param [out] param parametri comunicazione terminale
    * @return Codice errore 
    */
    int GetAxleCommunicationParam(AxleComParam param)

Impostare parametri comunicazione terminale
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare parametri comunicazione terminale
    * @param [in] param parametri comunicazione terminale
    * @return Codice errore 
    */
    int SetAxleCommunicationParam(AxleComParam param)

Impostare tipo trasferimento file terminale
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostare tipo trasferimento file terminale
    * @param [in] type 1-file aggiornamento MCU; 2-file LUA
    * @return  Codice errore
    */
    public int SetAxleFileType(int type)

Impostare abilitazione esecuzione LUA terminale
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostare abilitazione esecuzione LUA terminale
    * @param [in] enable 0-non abilitare; 1-abilitare
    * @return  Codice errore
    */
    public int SetAxleLuaEnable(int enable)

Ripristino errore anomalo file LUA terminale
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ripristino errore anomalo file LUA terminale
    * @param [in] status 0-non ripristinare; 1-ripristinare
    * @return  Codice errore
    */
    public int SetRecoverAxleLuaErr(int status)

Ottenere stato abilitazione esecuzione LUA terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere stato abilitazione esecuzione LUA terminale
    * @param [out] status[0]: 0-non abilitato; 1-abilitato
    * @return  Codice errore
    */
    int GetAxleLuaEnableStatus(int[] status)

Imposta i tipi di dispositivo abilitati per l'end-effector LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i tipi di dispositivo abilitati per l'end-effector LUA
    * @param forceSensorEnable Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    * @param gripperEnable Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    * @param IOEnable Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    * @param dexhandEnable Stato abilitazione mano destra, 0-disabilitato; 1-abilitato
    * @return  Codice errore
    */
    public int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable)

Ottiene i tipi di dispositivo abilitati per l'end-effector LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene i tipi di dispositivo abilitati per l'end-effector LUA
     * @param enable enable[0]:forceSensorEnable Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
     * @param enable enable[1]:gripperEnable Stato abilitazione pinza, 0-disabilitato; 1-abilitato
     * @param enable enable[2]:IOEnable Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
     * @param enable enable[3]:dexhandEnable Stato abilitazione mano destra, 0-disabilitato; 1-abilitato
     * @return  Codice errore
     */
    public int GetAxleLuaEnableDeviceType(int[] enable)

Ottiene i dispositivi dell'end-effector attualmente configurati
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene i dispositivi dell'end-effector attualmente configurati
     * @param forceSensorEnable Numero dispositivo sensore di forza abilitato, 0-disabilitato; 1-abilitato
     * @param gripperEnable Numero dispositivo pinza abilitato, 0-disabilitato; 1-abilitato
     * @param IODeviceEnable Numero dispositivo IO abilitato, 0-disabilitato; 1-abilitato
     * @param dexhandEnable Stato abilitazione mano destra, 0-disabilitato; 1-abilitato
     * @return  Codice errore
     */
    public int GetAxleLuaEnableDevice(int[] forceSensorEnable, int[] gripperEnable, int[] IODeviceEnable, int[] dexhandEnable)


Imposta le funzioni di controllo azione pinza abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Imposta le funzioni di controllo azione pinza abilitate
     * @param id Numero dispositivo pinza
     * @param func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; func[2]-impostazione posizione; func[3]-impostazione velocità; func[4]-impostazione coppia; func[6]-lettura stato pinza;
        func[7]-lettura stato inizializzazione; func[8]-lettura codice guasto; func[9]-lettura posizione; func[10]-lettura velocità; func[11]-lettura coppia; func[12]-impostazione giri per pinza rotante;
        func[13]-impostazione velocità rotazione pinza rotante; func[14]-impostazione coppia rotazione pinza rotante; func[15]-lettura stato pinza rotante; func[16]-lettura stato inizializzazione pinza rotante;
        func[17]-lettura giri pinza rotante; func[18]-lettura velocità pinza rotante; func[19]-lettura coppia pinza rotante; func[20]-impostazione movimento sincrono multiasse; func[21]-comando clear guasti;
        func[22]-stato funzionamento singolo asse; func[23]-stato funzionamento tutti gli assi;
     * @return  Codice errore
     */
    public int SetAxleLuaGripperFunc(int id, int[] func)

Ottiene le funzioni di controllo azione pinza abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene le funzioni di controllo azione pinza abilitate
     * @param id Numero dispositivo pinza
     * @param func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; func[2]-impostazione posizione; func[3]-impostazione velocità; func[4]-impostazione coppia; func[6]-lettura stato pinza;
        func[7]-lettura stato inizializzazione; func[8]-lettura codice guasto; func[9]-lettura posizione; func[10]-lettura velocità; func[11]-lettura coppia; func[12]-impostazione giri per pinza rotante;
        func[13]-impostazione velocità rotazione pinza rotante; func[14]-impostazione coppia rotazione pinza rotante; func[15]-lettura stato pinza rotante; func[16]-lettura stato inizializzazione pinza rotante;
        func[17]-lettura giri pinza rotante; func[18]-lettura velocità pinza rotante; func[19]-lettura coppia pinza rotante; func[20]-impostazione movimento sincrono multiasse; func[21]-comando clear guasti;
        func[22]-stato funzionamento singolo asse; func[23]-stato funzionamento tutti gli assi;
     * @return  Codice errore
     */
    public int GetAxleLuaGripperFunc(int id, int[] func)

Scrittura file slave Ethercat robot
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Scrittura file slave Ethercat robot
     * @param type tipo file slave, 1-file aggiornamento slave; 2-file configurazione slave
     * @param slaveID numero slave
     * @param fileName nome file upload
     * @return  Codice errore
     */
    public int SlaveFileWrite(int type, int slaveID, String fileName)

Upload file protocollo aperto LUA terminale
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Upload file protocollo aperto LUA terminale
     * @param filePath percorso file lua locale ".../AXLE_LUA_End_DaHuan.lua"
     * @return Codice errore
     */
    public int AxleLuaUpload(String filePath)

Ingresso modalità boot slave Ethercat robot
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ingresso modalità boot slave Ethercat robot
     * @return  Codice errore
     */
    public int SetSysServoBootMode()

Esempio codice operazione file LUA terminale robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAxleLua(Robot robot)
    {
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");

        AxleComParam param=new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        robot.GetAxleCommunicationParam(param);

        robot.SetAxleLuaEnable(1);
        int[] luaEnableStatus = new int[]{0};
        robot.GetAxleLuaEnableStatus(luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int [] enable=new int[]{0,0,0};
        robot.GetAxleLuaEnableDeviceType(enable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = { 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0};
        robot.GetAxleLuaGripperFunc(1, getFunc);
        int[] getforceEnable = { 0,0,0,0,0,0,0,0};
        int[] getgripperEnable = { 0,0,0,0,0,0,0,0};
        int[] getioEnable = { 0,0,0,0,0,0,0,0};
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable);
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getforceEnable[i]);
        }
        System.out.println("getgripperEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getgripperEnable[i]);
        }
        System.out.println("getioEnable status : ");
        for (int i = 0; i < 8; i++)
        {
            System.out.println(getioEnable[i]);
        }
        robot.ActGripper(1, 0);
        robot.Sleep(2000);
        robot.ActGripper(1, 1);
        robot.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
            pkg=robot.GetRobotRealTimeState();
            System.out.println("gripper pos is:"+pkg.gripper_position);
            robot.Sleep(100);
        }

    }

Ottenere stato pulsante SmartTool
+++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere stato pulsante SmartTool
    * @param [out] state stato pulsante manopola SmartTool;(bit0:0-comunicazione normale; 1-comunicazione persa; bit1-annulla operazione; bit2-cancella programma; bit3-tasto A; bit4-tasto B; bit5-tasto C; bit6-tasto D; bit7-tasto E; bit8-tasto IO; bit9-manuale/automatico; bit10-inizia)
    * @return Codice errore
    */
    int GetSmarttoolBtnState(int[] state)

Esempio codice pulsante SmartTool
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args) 
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 500);//imposta tentativi riconnessione, intervallo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn == 0) {
            System.out.println("connessione rpc successo");
        } else {
            System.out.println("connessione rpc fallita");
            return;
        }

        int[] state = {0};
        while (true)
        {
            robot.GetSmarttoolBtnState(state);

            String binaryString = String.format("%32s", Integer.toBinaryString(state[0])).replace(' ', '0');
            System.out.println("GetSmarttoolBtnState:"+binaryString);
            robot.Sleep(100);
        }
    }

Upload file LUA protocollo aperto
++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Upload file LUA protocollo aperto
    * @param  filePath percorso file lua protocollo aperto locale
    * @return Codice errore
    */
    public int OpenLuaUpload(String filePath)

Ottenere parametri scheda slave
++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere parametri scheda slave
    * @param  type  0-Ethercat, 1-CClink, 3-Ethercat, 4-EIP
    * @param  version  versione protocollo
    * @param  connState  0-non connesso 1-connesso
    * @return  Codice errore
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Scrivere DO slave
+++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Scrivere DO slave
    * @param   DOIndex  numero DO
    * @param   wirteNum  quantità scritta
    * @param   status valore scritto, massimo 8
    * @return  Codice errore
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int wirteNum, int[] status)

Scrivere AO slave
+++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /*
    * @brief  Scrivere AO slave
    * @param  AOIndex Numero AO
    * @param  writeNum Numero di valori da scrivere
    * @param  status Array di valori da scrivere (massimo 8), AO0~AO15 sono di tipo intero, AO16~AO31 sono in virgola mobile
    * @return  Codice di errore
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int writeNum, double[] status)

Leggere DI slave
++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Leggere DI slave
    * @param  DOIndex  numero DI
    * @param  readNum  quantità letta
    * @param  status valore letto, massimo 8
    * @return  Codice errore
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status)

Leggere AI slave
++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Leggere AI slave
    * @param  AIIndex  numero AI
    * @param  readNum  quantità letta
    * @param  status valore letto, massimo 8
    * @return  Codice errore
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status)

Attendere input DI estensione
+++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Attendere input DI estensione
    * @param  DIIndex numero DI
    * @param  status 0-basso; 1-alto
    * @param  waitMs tempo attesa massimo (ms)
    * @return Codice errore
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Attendere input AI estensione
+++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Attendere input AI estensione
    * @param  AIIndex numero AI
    * @param  waitType 0-maggiore; 1-minore
    * @param  valore AI
    * @param  waitMs tempo attesa massimo (ms)
    * @return Codice errore
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Esempio codice comandi interfaccia modalità slave
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testFieldBusBoard(Robot robot)
    {
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("D://zUP/1111/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);
        int[] type=new int[1];
        int[] version=new int[1];
        int[] connState=new int[1];
        //Ottenere tipo protocollo, versione software, stato connessione PLC scheda slave
        robot.GetFieldBusConfig(type, version, connState);
        System.out.println("type is: "+type[0]+", version is : "+version[0]+", connState is : "+connState[0]);
        //Scrivere DO0 = 1, DO1 = 0, DO2 = 1
        int[] ctrl =new int[8];
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
        //Scrivere AO2 = 0x1000
        int[] ctrlAO =new int[8];
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);
        int[] DI=new int[4];
        double[] AI=new double[3];
        //Monitoraggio ciclico DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            System.out.println("DI0 is: "+DI[0]+", DI1 is: "+DI[1]+",DI2 is: "+DI[2]+",DI3 is: "+DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            System.out.println("AI0 is: "+AI[0]+ ",AI1 is: "+AI[1]+",AI2 is: "+AI[2]);
            robot.Sleep(10);
        }
        //Attendere se DI0 è 1, tempo attesa 100ms, e stampare risultato
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        System.out.println("FieldBusSlaveWaitDI result is: "+ ret);
        //Attendere se AI0 è maggiore di 400, tempo attesa 100ms, e stampare risultato
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        System.out.println("FieldBusSlaveWaitAI result is: "+ ret);
        robot.CloseRPC();
    }

Controllare ventosa a matrice
++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Controllare ventosa a matrice
    * @param  slaveID numero slave
    * @param  len lunghezza
    * @param  ctrlValue valore controllo 1-aspirazione massima aspirazione 2-aspirazione soglia impostata 3-arresto aspirazione
    * @return Codice errore
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Ottenere stato ventosa a matrice
+++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere stato ventosa a matrice
    * @param  slaveID numero slave
    * @param  state stato aspirazione 0-rilascio oggetto 1-rilevato pezzo aspirazione riuscita 2-nessun oggetto aspirato 3-oggetto staccato
    * @param  pressValue vuoto corrente unità kpa
    * @param  error codice errore corrente ventosa
    * @return Codice errore
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Attendere stato ventosa
+++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Attendere stato ventosa
    * @param  slaveID numero slave
    * @param  state stato aspirazione 0-rilascio oggetto 1-rilevato pezzo aspirazione riuscita 2-nessun oggetto aspirato 3-oggetto staccato
    * @param  ms tempo attesa massimo
    * @return Codice errore
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Esempio codice comandi controllo ventosa a matrice
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testSucker(Robot robot)
    {
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("C：//项目/外设SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);
        //Controllo ventosa modalità broadcast, aspirazione massima capacità
        int[] ctrl = {1};
        robot.SetSuckerCtrl(0, 1, ctrl);
        int[] state=new int[1];
        int[] pressVlaue=new int[1];
        int[] error=new int[1];
        //Monitoraggio ciclico stato ventosa 1 e ventosa 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, state,pressVlaue, error);
            System.out.println("sucker1 state is:"+state[0]+",pressVlaue is:"+pressVlaue[0]+",error num is"+error[0]);
            robot.GetSuckerState(12, state, pressVlaue, error);
            System.out.println("sucker12 state is :"+state[0]+", pressVlaue is:"+pressVlaue[0]+",error num is:"+error[0]);
            robot.Sleep(100);
        }
        //Attendere se ventosa 1 è in stato oggetto aspirato, tempo attesa 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        System.out.println("WaitSuckerState result is:"+ ret);
        //Modalità unicast spegnimento ventosa 1 e 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
        robot.CloseRPC();
    }

Funzione accensione/spegnimento periferica laser
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Funzione accensione/spegnimento periferica laser
     * @param [in] OnOff 0-spegni 1-accendi
     * @param [in] weldId ID cordone saldatura default 0
     * @return Codice errore
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)

Funzione inizio/fine tracciamento laser
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:
    
    /**
     * @brief Funzione inizio/fine tracciamento laser
     * @param [in] OnOff 0-fine 1-inizio
     * @param [in] coordId numero sistema coordinato utensile periferica laser
     * @return Codice errore
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Ricerca posizione laser - direzione fissa inversa
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ricerca posizione laser - direzione fissa inversa
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel velocità unità %
     * @param [in] distance distanza ricerca massima unità mm
     * @param [in] timeout timeout ricerca unità ms
     * @param [in] posSensorNum numero coordinata utensile calibrata laser
     * @return Codice errore
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)

Ricerca posizione laser - direzione arbitraria
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ricerca posizione laser - direzione arbitraria
     * @param [in] directionPoint coordinate xyz punto input ricerca
     * @param [in] vel velocità unità %
     * @param [in] distance distanza ricerca massima unità mm
     * @param [in] timeout timeout ricerca unità ms
     * @param [in] posSensorNum numero coordinata utensile calibrata laser
     * @return Codice errore
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)

Fine ricerca posizione laser
+++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

   /**
    * @brief  Fine ricerca posizione laser
    * @return Codice errore
    */
    public int LaserTrackingSearchStop()

Configurazione IP laser
+++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
   :linenos:

    /**
     * @brief Configurazione IP laser
     * @param [in] ip indirizzo IP periferica laser
     * @param [in] porta numero porta periferica laser
     * @return Codice errore
     */
    public int LaserTrackingSensorConfig(String ip, int port)

Configurazione periodo campionamento periferica laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Configurazione periodo campionamento periferica laser
     * @param [in] period periodo campionamento periferica laser unità ms
     * @return Codice errore
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Caricamento driver periferica laser
++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Caricamento driver periferica laser
     * @param [in] type tipo protocollo driver periferica laser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Codice errore
     */
    public int LoadPosSensorDriver(int type)

Scaricamento driver periferica laser
+++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Scaricamento driver periferica laser
     * @return Codice errore
     */
    public int UnLoadPosSensorDriver()

Registrazione traiettoria cordone saldatura laser
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Registrazione traiettoria cordone saldatura laser
     * @param [in] status 0-arresta registrazione 1-tracciamento tempo reale 2-inizia registrazione
     * @param [in] delayTime tempo ritardo unità ms
     * @return Codice errore
     */
    public int LaserSensorRecord1(int status, int delayTime)

Riproduzione traiettoria cordone saldatura laser
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Riproduzione traiettoria cordone saldatura laser
     * @param [in] delayTime tempo ritardo unità ms
     * @param [in] speed velocità unità %
     * @return Codice errore
     */
    public int LaserSensorReplay(int delayTime, double speed)

Riproduzione tracciamento laser
++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Riproduzione tracciamento laser
     * @return Codice errore
     */
    public int MoveLTR()

Riproduzione traiettoria cordone saldatura laser
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
    * @brief Riproduzione Traiettoria Cordone di Saldatura Laser
    * @param delayMode Modalità 0-Tempo Ritardo 1-Distanza Ritardo
    * @param delayTime Tempo di ritardo in millisecondi (ms)
    * @param delayDisExAxisNum Numero Asse Esteso
    * @param delayDis Distanza di ritardo in millimetri (mm)
    * @param sensitivePara Coefficiente di Sensibilità della Compensazione
    * @param trackMode Tipo Tracciamento a Punto Fisso. 0-Movimento Asincrono Asse Esteso; 1-Robot
    * @param triggerMode Metodo di Attivazione Tracciamento a Punto Fisso. 0-Durata Tracciamento; 1-IO
    * @param runTime Durata Tracciamento a Punto Fisso del Robot in secondi (s)
    * @param speed Velocità in percentuale (%)
    * @return Codice Errore
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed)

Movimento punto inizio registrazione cordone laser
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Movimento punto inizio registrazione cordone laser
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl velocità unità %
     * @return Codice errore
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Movimento punto fine registrazione cordone laser
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Movimento punto fine registrazione cordone laser
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl velocità unità %
     * @return Codice errore
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Movimento punto ricerca sensore laser
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Movimento punto ricerca sensore laser
     * @param [in] moveFlag tipo movimento: 0-PTP; 1-LIN
     * @param [in] ovl fattore scala velocità, 0-100
     * @param [in] dataFlag selezione dati cache cordone: 0-esegui dati pianificazione; 1-esegui dati registrazione
     * @param [in] plateType tipo lamiera: 0-lamiera ondulata; 1-cartone ondulato; 2-pannello recinzione; 3-fusto olio; 4-acciaio ondulato
     * @param [in] trackOffectType tipo offset sensore laser: 0-nessun offset; 1-offset sistema base; 2-offset sistema utensile; 3-offset dati originali sensore laser
     * @param [in] offset valore offset
     * @return Codice errore
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)

Ottenere informazioni coordinate punto ricerca sensore laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottenere informazioni coordinate punto ricerca sensore laser
     * @param [in] trackOffectType tipo offset sensore laser: 0-nessun offset; 1-offset sistema base; 2-offset sistema utensile; 3-offset dati originali sensore laser
     * @param [in] offset valore offset
     * @param [out] jPos posizione giunti [°]
     * @param [out] descPos posizione cartesiana [mm]
     * @param [out] tool sistema coordinato utensile
     * @param [out] user sistema coordinato pezzo
     * @param [out] exaxis posizione asse estensione [mm]
     * @return Codice errore
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos jPos, DescPose descPos, int[] tool, int[] user, ExaxisPos exaxis)

Esempio codice configurazione parametri sensore periferica laser e debug
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLaserConfig(Robot robot)
    {
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);

        robot.LaserTrackingSensorSamplePeriod(20);

        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0,0);

        robot.Sleep(3000);

        robot.LaserTrackingLaserOnOff(1, 0);

        robot.CloseRPC();
    }

Esempio codice scansione traiettoria laser e riproduzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLaserRecordAndReplay(Robot robot)
    {
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);

        for (int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos=new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose=new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserSensorRecord1(0, 10);

            robot.MoveToLaserRecordStart(1, 30);

            robot.LaserSensorReplay(10, 100);

            robot.MoveLTR();

            robot.LaserSensorRecord1(0, 10);
        }

        robot.CloseRPC();
    }

Esempio codice ricerca posizione laser e tracciamento tempo reale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLasertrack(Robot robot)
    {
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        for(int i=0;i<10;++i){
            JointPos startjointPos=new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose=new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
            DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint=new DescTran();
            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();

            //robot.GetRobotTeachingPoint(name, data);
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
            //printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", data[0], data[1], data[2], data[3], data[4], data[5], data[6], data[7], data[8], data[9], data[10], data[11]);

            robot.LaserTrackingTrackOnOff(1, 3);
            //robot.LaserTrackingTrackOn(3);
            JointPos endjointPos=new JointPos(68.809,-87.100,121.120,-127.233,-95.038,-109.555);
            DescPose enddescPose=new DescPose(-103.555,-464.234,13.076,174.179,-1.344,-91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 0,1, 1);

            robot.LaserTrackingTrackOnOff(0, 3);
            System.out.println("Attualmente è la "+(i+1)+"° volta");
        }
        robot.CloseRPC();
    }

Esempio codice tracciamento laser sincronizzato asse estensione e robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testLasertrackandExitAxis(Robot robot)
    {
        ExaxisPos startexaxisPos =new ExaxisPos( 0,0,0,0 );
        ExaxisPos seamexaxisPos = new ExaxisPos(-10,0,0,0 );
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0 );
        JointPos seamjointPos=new JointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose=new DescPose(0, 0, 0, 0, 0, 0);

        for(int i =0;i<10;++i) {
            //Movimento punto inizio ricerca
            JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            System.out.println("11111");
            //Inizio ricerca lungo direzione -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            System.out.println("2222");
            int[] tool = new int[1];
            int[] user = new int[1];
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            System.out.println(seamjointPos.J1 + ", " + seamjointPos.J2 + ", " +
                    seamjointPos.J3 + ", " + seamjointPos.J4 + ", " +
                    seamjointPos.J5 + ", " + seamjointPos.J6 + ", " +
                    seamdescPose.tran.x + ", " + seamdescPose.tran.y + ", " +
                    seamdescPose.tran.z + ", " + seamdescPose.rpy.rx + ", " +
                    seamdescPose.rpy.ry + ", " + seamdescPose.rpy.rz);
            //Se ricerca riuscita
            if (ret == 0) {
                //Movimento sincronizzato robot e asse estensione punto ricerca
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                //Inizio tracciamento laser punto ricerca con movimento sincronizzato asse estensione
                System.out.println("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                ;
                //Arresto tracciamento
                robot.LaserTrackingTrackOnOff(0, 2);
                System.out.println("44444");
            }
            System.out.println("Numero esecuzioni corrente:"+i);
        }
        robot.CloseRPC();
    }

Abilita/Disabilita Funzione di Trasmissione Trasparente dell'End-Effector SDK Interface
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Abilita la funzione di trasmissione trasparente generale dell'end-effector
    * @param abilitazione, 0-disabilita, 1-abilita
    * @return Codice di errore
    */
    public int SetAxleGenComEnable(int mode)

Trasmissione e Ricezione Dati Non Periodici della Funzione di Trasmissione Trasparente dell'End-Effector SDK Interface
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief L'end-effector invia dati non periodici e attende risposta
    * @param lenSnd Lunghezza dei dati da inviare
    * @param sndBuff Dati da inviare
    * @param lenRcv Lunghezza dei dati da ricevere
    * @param [out] rcvData Dati di risposta
    * @return Codice di errore
    */
    public int SndRcvAxleGenComCmdData(int lenSnd, int[] sndBuff, int lenRcv, int[] rcvData)
    
Esempio di Codice per Comunicazione Dati Non Periodici del DIO Health Care Moxibustion Head basato sulla Funzione di Trasmissione Trasparente dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testAxleGenCom(Robot robot) {
    int[] led_on = {0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79};
    int[] led_off = {0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78};
    int[] version = {0xAB, 0xBA, 0x11, 0x00, 0x76};
    int[] state = {0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B};

    int[] rcvdata = new int[16];
    int ret = 0;
    int cnt = 1;

    JointPos p1Joint = new JointPos(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
    DescPose p1Desc = new DescPose(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);

    JointPos p2Joint = new JointPos(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
    DescPose p2Desc = new DescPose(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);

    ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
    DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

    // Abilita la funzione di trasmissione trasparente dell'end-effector
    robot.SetAxleGenComEnable(1);
    robot.SetAxleLuaEnable(1);

    while (cnt <= 10000) {
        // Legge il numero di versione
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        if (ret == 0) {
            System.out.printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n",
                    rcvdata[4], rcvdata[5], rcvdata[6], rcvdata[7], rcvdata[8]);
        } else {
            System.out.println("SndRcvAxleGenComCmdData version fail: " + ret);
            break;
        }
        robot.Sleep(1000);

        // Legge lo stato di presenza della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        if (ret == 0) {
            System.out.printf(" state : %d \n", rcvdata[4]);
        }
        robot.Sleep(1000);

        // Accende il laser della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led on rcv data is: %d, %d, %d, %d, %d, %d\n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(4000);

        // Spegne il laser della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        if (ret == 0) {
            System.out.printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n",
                    rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        }
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100.0, 100.0, 100.0, exaxisPos, -1.0, 0, offdese);
        robot.Sleep(1000);

        System.out.println("***********************complete No. " + cnt + " SDK test*****************************");
        cnt++;
    }
    }  
    
Scarica File Lua di Protocollo Aperto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Scarica file Lua di protocollo aperto
    * @param fileName Nome del file di protocollo aperto "CtrlDev_XXX.lua"
    * @param savePath Percorso di salvataggio del file di protocollo aperto
    * @return Codice di errore
    */
    public int OpenLuaDownload(string fileName, string savePath)

Elimina File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Elimina file Lua di protocollo aperto
    * @param [in] fileName Nome del file Lua di protocollo aperto da eliminare "CtrlDev_XXX.lua"
    * @return Codice di errore
    */
    public int OpenLuaDelete(string fileName)
        
Elimina Tutti i File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Elimina tutti i file Lua di protocollo aperto
    * @return Codice di errore
    */
    public int AllOpenLuaDelete()

Esempio di Codice per Caricamento, Download ed Eliminazione di Protocollo Aperto per Periferiche del Controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestCtrlOpenLuaOperate(Robot robot) {
        int rtn;
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        System.out.println("OpenLuaUpload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        System.out.println("OpenLuaDownload rtn is " + rtn);

        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        System.out.println("SetCtrlOpenLUAName rtn is " + rtn);

        String[] names = new String[4];
        rtn = robot.GetCtrlOpenLUAName(names);
        System.out.println("GetCtrlOpenLUAName rtn is " + rtn + ", names: " +
                names[0] + ", " + names[1] + ", " + names[2] + ", " + names[3]);

        rtn = robot.LoadCtrlOpenLUA(1);
        System.out.println("LoadCtrlOpenLUA rtn is " + rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        System.out.println("UnloadCtrlOpenLUA rtn is " + rtn);

        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        System.out.println("OpenLuaDelete rtn is " + rtn);
        rtn = robot.AllOpenLuaDelete();
        System.out.println("AllOpenLuaDelete rtn is " + rtn);

        robot.Sleep(1000);
        return 0;
    }

Controllo del Movimento della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Controllo del movimento della mano destra
    * @param idstart Numero stazione slave iniziale
    * @param slaveNum Numero di slave
    * @param pos Array di posizioni, lunghezza 16, intervallo (-360~360)
    * @param speed Array di percentuali di velocità, lunghezza 16, intervallo [0~100]
    * @param force Array di percentuali di coppia, lunghezza 16, intervallo [0~100]
    * @param max_time Tempo massimo di attesa, intervallo [0~30000], unità ms
    * @return Codice errore
    */
    public int SetDexterousHandsMove(int idstart, int slaveNum, double[] pos, int[] speed, int[] force, int max_time) 
        
Controllo del Reset e Attivazione della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Controllo del reset e attivazione della mano destra
    * @param id Numero stazione slave
    * @param act 0-reset 1-attivazione
    * @return Codice errore
    */
    public int SetDexterousHandsAct(int id, int act)
            
Cancellazione dell'Errore della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Cancellazione dell'errore della mano destra
    * @return Codice errore
    */
    public int ClearDexterousHandsError()
                
Impostazione delle Funzioni di Controllo Azione Mano Destra Abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta le funzioni di controllo azione mano destra abilitate
    * @param id Numero stazione slave della mano destra
    * @param func Array di funzioni, lunghezza 32, Bit0-attivazione presa, Bit1-inizializzazione pinza, Bit2-impostazione posizione, Bit3-impostazione velocità, Bit4-impostazione coppia, Bit6-lettura stato pinza, Bit7-lettura stato inizializzazione, Bit8-lettura codice guasto, Bit9-lettura posizione, Bit10-lettura velocità, Bit11-lettura coppia, Bit12-impostazione giri rotazione, Bit13-impostazione velocità rotazione, Bit14-impostazione coppia rotazione, Bit15-lettura stato pinza rotante, Bit16-lettura stato inizializzazione rotazione, Bit17-lettura giri rotazione, Bit18-lettura velocità rotazione, Bit19-lettura coppia rotazione, Bit20-impostazione movimento sincrono multiasse, Bit21-comando clear guasti, Bit22-stato funzionamento singolo asse, Bit23-stato funzionamento tutti gli assi
    * @return Codice errore
    */
    public int SetDexterousHandsFunc(int id, int[] func)
                    
Ottenimento delle Funzioni di Controllo Azione Mano Destra Abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene le funzioni di controllo azione mano destra abilitate
    * @param id Numero dispositivo mano destra
    * @param func Array di parametri di output, lunghezza 32, Bit0-attivazione presa, Bit1-inizializzazione pinza, Bit2-impostazione posizione, Bit3-impostazione velocità, Bit4-impostazione coppia, Bit6-lettura stato pinza, Bit7-lettura stato inizializzazione, Bit8-lettura codice guasto, Bit9-lettura posizione, Bit10-lettura velocità, Bit11-lettura coppia, Bit12-impostazione giri rotazione, Bit13-impostazione velocità rotazione, Bit14-impostazione coppia rotazione, Bit15-lettura stato pinza rotante, Bit16-lettura stato inizializzazione rotazione, Bit17-lettura giri rotazione, Bit18-lettura velocità rotazione, Bit19-lettura coppia rotazione, Bit20-impostazione movimento sincrono multiasse, Bit21-comando clear guasti, Bit22-stato funzionamento singolo asse, Bit23-stato funzionamento tutti gli assi
    * @return Codice errore
    */
    public int GetDexterousHandsFunc(int id, int[] func)
                    
Esempio di Codice per Configurazione e Movimento della Mano Destra sull'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestDexterousHands(Robot robot) {
        int id = 1;
        int slaveNum = 4;
        int max_time = 8000;
        int[] speed = new int[16]; 
        int[] force = new int[16]; 

        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        for (int i = 0; i < 16; i++) {
            force[i] = (i < 4) ? 50 : 0;
        }

        final double[] pos = new double[16];

        JointPos j1 = new JointPos(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
        JointPos j2 = new JointPos(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        int ret = robot.ClearDexterousHandsError();
        System.out.println("ClearDexterousHandsError -> " + ret);

        int[] setFunc = new int[32];
        setFunc[2] = 1;
        setFunc[4] = 1;
        setFunc[9] = 1;
        setFunc[10] = 1;
        setFunc[11] = 1;
        setFunc[22] = 1;

        ret = robot.SetDexterousHandsFunc(id, setFunc);

        int[] getFunc = new int[32];
        ret = robot.GetDexterousHandsFunc(id, getFunc);
        System.out.println("GetDexterousHandsFunc -> " + ret);
        if (ret == 0) {
            for (int i = 0; i < getFunc.length; i++) {
                System.out.print("  [" + i + "]=" + getFunc[i]);
                if ((i + 1) % 8 == 0) {
                    System.out.println();
                } else if (i < getFunc.length - 1) {
                    System.out.print(", ");
                }
            }
            if (getFunc.length % 8 != 0) {
                System.out.println();
            }
        }

        ret = robot.SetDexterousHandsAct(id, 1);
        if (ret != 0) {
            return ret;
        }

        setPositions(pos, 20, 20, 20, 20);
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        robot.Sleep(5000);
        
        for (int iteration = 1; iteration <= 10; iteration++) {
            robot.MoveJ(j1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            setPositions(pos, 10, 10, 10, 10);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            robot.Sleep(1000);

            robot.MoveJ(j2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            setPositions(pos, 50, 50, 50, 50);
            ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
            robot.Sleep(1000);
        }
        return 0;
    }    