Periferiche Robot
======================

.. toctree:: 
    :maxdepth: 5

Configurare Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configurare Pinza
    * @param  [in] company  Produttore pinza, da definire
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, default 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, default 0
    * @param  [in] bus Posizione bus estremità dove è collegato il dispositivo, attualmente non utilizzato, default 0
    * @return   Codice errore
    */
    int SetGripperConfig(int company, int device, int softvesion, int bus);

Ottenere Configurazione Pinza
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Configurazione Pinza
    * @param  [in] company  Produttore pinza, da definire
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, default 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, default 0
    * @param  [in] bus Posizione bus estremità dove è collegato il dispositivo, attualmente non utilizzato, default 0
    * @return   Codice errore
    */
    int GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Attivare Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Attivare Pinza
    * @param  [in] index  Numero identificativo pinza
    * @param  [in] act  0-reset, 1-attiva
    * @return   Codice errore
    */
    int ActGripper(int index, byte act); 

Controllare Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controllare Pinza
    * @param  [in] index  Numero identificativo pinza
    * @param  [in] pos  Percentuale posizione, range [0~100]
    * @param  [in] vel  Percentuale velocità, range [0~100]
    * @param  [in] force  Percentuale coppia, range [0~100]
    * @param  [in] max_time  Tempo di attesa massimo, range [0~30000], unità ms
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [in] type Tipo pinza, 0-pinza parallela; 1-pinza rotante
    * @param  [in] rotNum Numero di giri rotazione
    * @param  [in] rotVel Percentuale velocità rotazione [0-100]
    * @param  [in] rotTorque Percentuale coppia rotazione [0-100]
    * @return   Codice errore
    */
    int MoveGripper(int index, int pos, int vel, int force, int max_time, byte block, int type, double rotNum, int rotVel, int rotTorque);

Ottenere Stato Movimento Pinza
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Stato Movimento Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] staus  0-movimento non completato, 1-movimento completato
    * @return   Codice errore
    */
    int GetGripperMotionDone(ref int fault, ref int status); 

Ottenere Stato Attivazione Pinza
++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Stato Attivazione Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] status  bit0~bit15 corrispondono numeri pinza 0~15, bit=0 non attivato, bit=1 attivato
    * @return   Codice errore
    */
    int GetGripperActivateStatus(ref int fault, ref int status);

Ottenere Posizione Pinza
+++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Posizione Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] position  Percentuale posizione, range 0~100%
    * @return   Codice errore
    */
    int GetGripperCurPosition(ref int fault, ref int position);

Ottenere Velocità Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Velocità Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] speed  Percentuale velocità, range 0~100%
    * @return   Codice errore
    */
    int GetGripperCurSpeed(ref int fault, ref int speed);
     
Ottenere Corrente Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Corrente Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] current  Percentuale corrente, range 0~100%
    * @return   Codice errore
    */
    int GetGripperCurCurrent(ref int fault, ref int current);

Ottenere Tensione Pinza
++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Tensione Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] voltage  Tensione, unità 0.1V
    * @return   Codice errore
    */
    int GetGripperVoltage(ref int fault, ref int voltage);

Ottenere Temperatura Pinza
+++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Temperatura Pinza
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] temp  Temperatura, unità ℃
    * @return   Codice errore
    */
    int GetGripperTemp(ref int fault, ref int temp);

Calcolare Punto Pre-Presa - Visione
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolare Punto Pre-Presa - Visione 
    * @param [in] desc_pos Posa cartesiana punto di presa 
    * @param [in] zlength Offset asse z 
    * @param [in] zangle Offset rotazione attorno asse z
    * @param [out] pre_pos Punto pre-presa
    * @return Codice errore 
    */ 
    int ComputePrePick(DescPose desc_pos, double zlength, double zangle, ref DescPose pre_pos);

Calcolare Punto Post-Presa - Visione
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolare Punto Post-Presa - Visione 
    * @param [in] desc_pos Posa cartesiana punto post-presa 
    * @param [in] zlength Offset asse z 
    * @param [in] zangle Offset rotazione attorno asse z
    * @param [out] post_pos Punto post-presa
    * @return Codice errore 
    */ 
    int ComputePostPick(DescPose desc_pos, double zlength, double zangle, ref DescPose post_pos);

Esempio Codice Operazioni Pinza Robot
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button36_Click(object sender, EventArgs e)
    {
        int company = 4;
        int device = 0;
        int softversion = 0;
        int bus = 2;
        int index = 2;
        byte act = 0;
        int max_time = 30000;
        byte block = 0;
        int status=0;
        int fault=0;
        int active_status = 0;
        int current_pos = 0;
        int current = 0;
        int voltage = 0;
        int temp = 0;
        int speed = 0;

        robot.SetGripperConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.GetGripperConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine("gripper config:{0},{1},{2},{3}\n", company, device, softversion, bus);

        robot.ActGripper(index, act);
        Thread.Sleep(1000);
        act = 1;
        robot.ActGripper(index, act);
        Thread.Sleep(1000);

        robot.MoveGripper(index, 90, 50, 50, max_time, block, 0, 0, 0, 0);
        Thread.Sleep(1000);
        robot.MoveGripper(index, 30, 50, 0, max_time, block, 0, 0, 0, 0);

        robot.GetGripperMotionDone(ref fault, ref status);
        Console.WriteLine("motion status:{0},{1}\n", fault, status);

        robot.GetGripperActivateStatus(ref fault, ref active_status);
        Console.WriteLine("gripper active fault is: {0}, status is: {1}\n", fault, active_status);

        robot.GetGripperCurPosition(ref fault, ref current_pos);
        Console.WriteLine("fault is:{0}, current position is: {1}\n", fault, current_pos);

        robot.GetGripperCurCurrent(ref fault, ref current);
        Console.WriteLine("fault is:{0}, current current is: {1}\n", fault, current);

        robot.GetGripperVoltage(ref fault, ref voltage);
        Console.WriteLine("fault is:{0}, current voltage is: {1} \n", fault, voltage);

        robot.GetGripperTemp(ref fault, ref temp);
        Console.WriteLine("fault is:{0}, current temperature is: {1}\n", fault, temp);

        robot.GetGripperCurSpeed(ref fault, ref speed);
        Console.WriteLine("fault is:{0}, current speed is: {1}\n", fault, speed);

        int retval = 0;
        DescPose prepick_pose = new DescPose();
        DescPose postpick_pose = new DescPose();

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        retval = robot.ComputePrePick(p1Desc, 10, 0, ref prepick_pose);
        Console.WriteLine("ComputePrePick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z,
            prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);

        retval = robot.ComputePostPick( p2Desc, -10, 0, ref postpick_pose);
        Console.WriteLine("ComputePostPick retval is: {0}\n", retval);
        Console.WriteLine("xyz is: {0}, {1}, {2}; rpy is: {3}, {4}, {5}\n",
            postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z,
            postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);

    }

Ottenere Numero Giri Pinza Rotante
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Numero Giri Pinza Rotante
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] num  Numero giri rotazione
    * @return   Codice errore
    */
    int GetGripperRotNum(ref UInt16 fault, ref double num);

Ottenere Percentuale Velocità Rotazione Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Percentuale Velocità Rotazione Pinza Rotante
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] speed  Percentuale velocità rotazione
    * @return   Codice errore
    */
    int GetGripperRotSpeed(ref UInt16 fault, ref int speed);

Ottenere Percentuale Coppia Rotazione Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Percentuale Coppia Rotazione Pinza Rotante
    * @param  [out] fault  0-nessun errore, 1-errore presente
    * @param  [out] torque  Percentuale coppia rotazione
    * @return   Codice errore
    */
    int GetGripperRotTorque(ref UInt16 fault, ref int torque);

Esempio Codice Ottenimento Stato Pinza Rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    int MoveRotGripper(int pos, double rotPos)
    {
        robot.ResetAllError();
        robot.ActGripper(1, 1);
        Thread.Sleep(1000);
        int rtn = robot.MoveGripper(1, pos, 50, 50, 5000, 1, 1, rotPos, 50, 100);
        Console.WriteLine($"move gripper rtn is {rtn}" );
        UInt16 fault = 0;
        double rotNum = 0.0;
        int rotSpeed = 0;
        int rotTorque = 0;
        robot.GetGripperRotNum(ref fault, ref rotNum);
        robot.GetGripperRotSpeed(ref fault, ref rotSpeed);
        robot.GetGripperRotTorque(ref fault, ref rotTorque);
        Console.WriteLine($"gripper rot num :{ rotNum}, gripper rotSpeed :{rotSpeed}, gripper rotTorque : { rotTorque}");
        return 0;
    }

Avvio, Arresto Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Avvio, Arresto Nastro Trasportatore 
    * @param [in] status Stato, 1-avvio, 0-arresto
    * @return Codice errore 
    */ 
    int ConveyorStartEnd(byte status); 

Registrare Punto Rilevamento IO
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registrare Punto Rilevamento IO 
    * @return Codice errore 
    */ 
    int ConveyorPointIORecord(); 

Registrare Punto A
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registrare Punto A 
    * @return Codice errore 
    */ 
    int ConveyorPointARecord();

Registrare Punto Riferimento
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registrare Punto Riferimento 
    * @return Codice errore 
    */ 
    int ConveyorRefPointRecord(); 

Registrare Punto B
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Registrare Punto B 
    * @return Codice errore 
    */ 
    int ConveyorPointBRecord();

Rilevamento IO Pezzo Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Rilevamento IO Pezzo Nastro Trasportatore 
    * @param [in] max_t Tempo massimo rilevamento, unità ms
    * @return Codice errore 
    */ 
    int ConveyorIODetect(int max_t);

Ottenere Posizione Corrente Oggetto
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Posizione Corrente Oggetto 
    * @param [in] mode 1-tracciamento presa, 2-tracciamento movimento, 3-tracciamento TPD
    * @return Codice errore 
    */ 
    int ConveyorGetTrackData(int mode);

Inizio Tracciamento Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Inizio Tracciamento Nastro Trasportatore 
    * @param [in] status Stato, 1-avvio, 0-arresto
    * @return Codice errore 
    */
    int ConveyorTrackStart(byte status);

Fine Tracciamento Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Fine Tracciamento Nastro Trasportatore 
    * @return Codice errore 
    */
    int ConveyorTrackEnd();

Configurazione Parametri Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Configurazione Parametri Nastro Trasportatore
    * @param [in] para[0] Canale encoder 1~2
    * @param [in] para[1] Numero impulsi per giro encoder
    * @param [in] para[2] Distanza percorrenza nastro per giro encoder
    * @param [in] para[3] Numero sistema coordinate pezzo Per funzione tracciamento movimento selezionare numero sistema coordinate pezzo, per tracciamento presa, TPD impostare 0
    * @param [in] para[4] Se dotato di visione  0 no  1 sì
    * @param [in] para[5] Rapporto velocità  Opzione tracciamento presa nastro (1-100)  Altre opzioni default 1 
    * @param [in] followType Tipo movimento tracciamento, 0-tracciamento movimento; 1-movimento inseguimento ispezione
    * @param [in] startDis Necessario per presa inseguimento ispezione, distanza inizio tracciamento, -1: calcolo automatico (inseguimento ispezione automatico dopo arrivo pezzo sotto robot), unità mm, valore default 0
    * @param [in] endDis Necessario per presa inseguimento ispezione, distanza fine tracciamento, unità mm, valore default 100
    * @return Codice errore
    */
    int ConveyorSetParam(int encChannel, int resolution, double lead, int wpAxis, int vision, double speedRadio, int followType, int startDis=0, int endDis=100);

Impostare Compensazione Punto Presa Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Compensazione Punto Presa Nastro Trasportatore 
    * @param [in] cmp Posizione compensazione double[3]{x, y, z}
    * @return Codice errore 
    */
    int ConveyorCatchPointComp(double[] cmp);

Movimento Lineare Tracciamento Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Movimento Lineare Tracciamento Nastro Trasportatore 
    * @param [in] name Nome punto movimento
    * @param [in] tool Numero sistema coordinate utensile, range [0~14] 
    * @param [in] wobj Numero sistema coordinate pezzo, range [0~14] 
    * @param [in] vel Percentuale velocità, range [0~100] 
    * @param [in] acc Percentuale accelerazione, range [0~100], attualmente non disponibile 
    * @param [in] ovl Fattore di scala velocità, range [0~100] 
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm  
    * @return Codice errore 
    */
    int ConveyorTrackMoveL(string name, int tool, int wobj, float vel, float acc, float ovl, float blendR);

Rilevamento Input Comunicazione Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rilevamento Input Comunicazione Nastro Trasportatore
    * @param [in] timeout Tempo attesa timeout ms
    * @return Codice errore
    */
    int ConveyorComDetect(int timeout);

Trigger Rilevamento Input Comunicazione Nastro Trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Trigger Rilevamento Input Comunicazione Nastro Trasportatore
    * @return Codice errore
    */
    int ConveyorComDetectTrigger();

Esempio Programma Trigger Rilevamento Input Comunicazione Nastro Trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button3_Click(object sender, EventArgs e)
    {

        // Disabilitare pulsante per evitare clic ripetuti
        button3.Enabled = false;

        // Eseguire operazione lunga in thread background
        Thread conveyorThread = new Thread(ConveyorTest);
        conveyorThread.IsBackground = true;
        conveyorThread.Start();
    }

    private void button4_Click(object sender, EventArgs e)
    {
        // Ottenere input utente
        string input = texBox.Text;
        Console.WriteLine($"please input a number to trigger:{input}");
    
        int rtn = robot.ConveyorComDetectTrigger();
        Console.WriteLine($"ConveyorComDetectTrigger valore restituito: {rtn}");
        
    }

    private void ConveyorTest()
    {
        // Usare Invoke per aggiornare controlli sul thread UI
        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("Inizio test nastro trasportatore...");
        });

        int retval = 0;
        int index = 1;
        int max_time = 30000;
        bool block = false;
        retval = 0;

        /* Processo presa nastro trasportatore */
        DescPose startdescPose = new DescPose(139.176f, 4.717f, 9.088f, -179.999f, -0.004f, -179.990f);
        JointPos startjointPos = new JointPos(-34.129f, -88.062f, 97.839f, -99.780f, -90.003f, -34.140f);

        DescPose homePose = new DescPose(139.177f, 4.717f, 69.084f, -180.000f, -0.004f, -179.989f);
        JointPos homejointPos = new JointPos(-34.129f, -88.618f, 84.039f, -85.423f, -90.003f, -34.140f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        // Spostarsi a posizione sicura
        retval = robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        Console.WriteLine($"MoveL a posizione sicura valore restituito: {retval}");

        // Rilevamento nastro trasportatore
        retval = robot.ConveryComDetect(1000 * 10);
        Console.WriteLine($"ConveyorComDetect valore restituito: {retval}");

        // Ottenere dati tracciamento
        retval = robot.ConveyorGetTrackData(2);
        Console.WriteLine($"ConveyorGetTrackData valore restituito: {retval}");

        // Inizio tracciamento
        retval = robot.ConveyorTrackStart(2);
        Console.WriteLine($"ConveyorTrackStart valore restituito: {retval}");

        // Spostarsi a posizione iniziale
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveL(startjointPos, startdescPose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        // Fine tracciamento
        retval = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd valore restituito: {retval}");

        // Ritorno a posizione sicura
        robot.MoveL(homejointPos, homePose, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 1, 1);

        this.Invoke((MethodInvoker)delegate {
            Console.WriteLine("Test nastro trasportatore completato!");
            button3.Enabled = true;
        });
    }

Esempio Programma Operazioni Nastro Trasportatore Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnConvert_Click(object sender, EventArgs e)
        {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");
        DescPose pos1 = new DescPose(0, 0, 0, 0 ,0 ,0);
        DescPose pos2 = new DescPose(0, 0, 0, 0, 0, 0);

        pos1.tran.x = -351.175;
        pos1.tran.y = 3.389;
        pos1.tran.z = 431.172;
        pos1.rpy.rx = -179.111;
        pos1.rpy.ry = -0.241;
        pos1.rpy.rz = 90.388;

        pos2.tran.x = -333.654;
        pos2.tran.y = -229.003;
        pos2.tran.z = 404.335;
        pos2.rpy.rx = -179.139;
        pos2.rpy.ry = -0.779;
        pos2.rpy.rz = 91.269;
        int rtn = -1;

        double[] cmp = new double[3] { 0, 9.99, 0};
        rtn = robot.ConveyorCatchPointComp(cmp);
        if(rtn != 0)
        {
            return;
        }
        Console.WriteLine($"ConveyorCatchPointComp: rtn  {rtn}");

        rtn = robot.MoveCart(pos1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, -1);
        Console.WriteLine($"MoveCart: rtn  {rtn}");

        rtn = robot.ConveyorIODetect(10000);
        Console.WriteLine($"ConveyorIODetect: rtn  {rtn}");

        robot.ConveyorGetTrackData(1);
        rtn = robot.ConveyorTrackStart(1);
        Console.WriteLine($"ConveyorTrackStart: rtn  {rtn}");

        rtn = robot.ConveyorTrackMoveL("cvrCatchPoint", 0, 0, 100.0f, 0.0f, 100.0f, -1.0f, 0, 0);
        Console.WriteLine($"ConveyorTrackMoveL: rtn  {rtn}");

        rtn = robot.MoveGripper(1, 59, 43, 21, 30000, 0);
        Console.WriteLine($"MoveGripper: rtn  {rtn}");

        rtn = robot.ConveyorTrackMoveL("cvrRaisePoint", 0, 0, 100.0f, 0.0f, 100.0f, -1.0f, 0, 0);
        Console.WriteLine($"ConveyorTrackMoveL: rtn  {rtn}");

        rtn = robot.ConveyorTrackEnd();
        Console.WriteLine($"ConveyorTrackEnd: rtn  {rtn}");

        rtn = robot.MoveCart(pos2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, -1);
        Console.WriteLine($"MoveCart: rtn  {rtn}");

        rtn = robot.MoveGripper(1, 100, 43, 21, 30000, 0);
        Console.WriteLine($"MoveGripper: rtn  {rtn}");
    }

Configurazione Sensore Estremità
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configurazione Sensore Estremità
    * @param  [in] idCompany Produttore, 18-JUNKONG；25-HUIDE
    * @param  [in] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @param  [in] idSoftware Versione software, 0-J1.0/HuiDe1.0(attualmente non disponibile)
    * @param  [in] idBus Posizione montaggio, 1-porta 1 estremità; 2-porta 2 estremità...8-porta 8 estremità(attualmente non disponibile)
    * @return   Codice errore
    */
    int AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Ottenere Configurazione Sensore Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Configurazione Sensore Estremità
    * @param  [out] idCompany Produttore, 18-JUNKONG；25-HUIDE
    * @param  [out] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @return   Codice errore
    */
    int AxleSensorConfigGet(ref int idCompany, ref int idDevice);

Attivazione Sensore Estremità
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Attivazione Sensore Estremità
    * @param  [in] actFlag 0-reset; 1-attiva
    * @return   Codice errore
    */
    int AxleSensorActivate(int actFlag);

Scrittura Registro Sensore Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Scrittura Registro Sensore Estremità
    * @param  [in] devAddr  Numero indirizzo dispositivo 0-255
    * @param  [in] regHAddr Indirizzo registro 8 bit alti
    * @param  [in] regLAddr Indirizzo registro 8 bit bassi
    * @param  [in] regNum  Numero registri 0-255
    * @param  [in] data1 Valore scrittura registro 1
    * @param  [in] data2 Valore scrittura registro 2
    * @param  [in] isNoBlock 0-bloccante; 1-non bloccante
    * @return   Codice errore
    */
     int AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Esempio Codice Sensore Estremità
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button2_Click_1(object sender, EventArgs e)
    {
        robot.AxleSensorConfig(18, 0, 0, 1);
        int company = -1;
        int type = -1;
        robot.AxleSensorConfigGet(ref company, ref type);
        Console.WriteLine("company is " + company + ", type is " + type);

        int rtn = robot.AxleSensorActivate(1);
        Console.WriteLine("AxleSensorActivate rtn is " + rtn);

        Thread.Sleep(1000);

        rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
        Console.WriteLine("AxleSensorRegWrite rtn is " + rtn);   
    }

Ottenere Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Protocollo Periferiche Robot
    * @param [out] protocol Numero protocollo periferiche robot 4096-scheda controllo asse esteso; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Codice errore 
    */
    int GetExDevProtocol(ref int protocol);

Impostare Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Protocollo Periferiche Robot
    * @param [in] protocol Numero protocollo periferiche robot 4096-scheda controllo asse esteso; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Codice errore 
    */
    int SetExDevProtocol(int protocol);

Esempio Programma Impostazione Protocollo Periferiche Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSetProto_Click(object sender, EventArgs e)
    {
      int protocol = 4096;
      int rtn = robot.SetExDevProtocol(protocol);
      Console.WriteLine("SetExDevProtocol rtn " + rtn);
      rtn = robot.GetExDevProtocol(ref protocol);
      Console.WriteLine("GetExDevProtocol rtn " + rtn + " protocol is: " + protocol);
    }

Ottenere Parametri Comunicazione Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Parametri Comunicazione Estremità
    * @param param Parametri comunicazione estremità
    * @return   Codice errore
    */
    int GetAxleCommunicationParam(ref AxleComParam getParam);

Impostare Parametri Comunicazione Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Parametri Comunicazione Estremità
    * @param param  Parametri comunicazione estremità
    * @return   Codice errore
    */
    int SetAxleCommunicationParam(AxleComParam param);

Impostare Tipo Trasmissione File Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Tipo Trasmissione File Estremità
    * @param type 1-file aggiornamento MCU; 2-file LUA
    * @return   Codice errore
    */
    int SetAxleFileType(int type);

Impostare Abilitazione Esecuzione LUA Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Abilitazione Esecuzione LUA Estremità
    * @param enable 0-non abilitato; 1-abilitato
    * @return   Codice errore
    */
    int SetAxleLuaEnable(int enable);

Recupero Errore Anomalo File LUA Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Recupero Errore Anomalo File LUA Estremità
    * @param status 0-non recuperare; 1-recupera
    * @return   Codice errore
    */
    int SetRecoverAxleLuaErr(int status);

Ottenere Stato Abilitazione Esecuzione LUA Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Stato Abilitazione Esecuzione LUA Estremità
    * @param [out] status 0-non abilitato; 1-abilitato
    * @return   Codice errore
    */
    int GetAxleLuaEnableStatus(ref int status);

Impostare Tipo Dispositivi Estremità Abilitati LUA Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Tipo Dispositivi Estremità Abilitati LUA Estremità
    * @param [in] forceSensorEnable Stato abilitazione sensore forza, 0-non abilitato; 1-abilitato
    * @param [in] gripperEnable Stato abilitazione pinza, 0-non abilitato; 1-abilitato
    * @param [in] IOEnable Stato abilitazione dispositivo IO, 0-non abilitato; 1-abilitato
    * @return   Codice errore
    */
    int SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable);

Ottenere Tipo Dispositivi Estremità Abilitati LUA Estremità
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Tipo Dispositivi Estremità Abilitati LUA Estremità
    * @param [out] forceSensorEnable Stato abilitazione sensore forza, 0-non abilitato; 1-abilitato
    * @param [out] gripperEnable Stato abilitazione pinza, 0-non abilitato; 1-abilitato
    * @param [out] IOEnable Stato abilitazione dispositivo IO, 0-non abilitato; 1-abilitato
    * @return   Codice errore
    */
    int GetAxleLuaEnableDeviceType(ref int forceSensorEnable, ref int gripperEnable, ref int IOEnable);

Ottenere Dispositivi Estremità Configurati Correntemente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Dispositivi Estremità Configurati Correntemente
    * @param [out] forceSensorEnable Numero dispositivo sensore forza abilitato 0-non abilitato; 1-abilitato
    * @param [out] gripperEnable Numero dispositivo pinza abilitato, 0-non abilitato; 1-abilitato
    * @param [out] IODeviceEnable Numero dispositivo IO abilitato, 0-non abilitato; 1-abilitato
    * @return   Codice errore
    */
    int GetAxleLuaEnableDevice(ref int[] forceSensorEnable, ref int[] gripperEnable, ref int[] IODeviceEnable);

Impostare Funzione Controllo Azione Pinza Abilitata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Funzione Controllo Azione Pinza Abilitata
    * @param [in] id Numero dispositivo pinza
    * @param [in] func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; 2-impostazione posizione; 3-impostazione velocità; 4-impostazione coppia; 6-lettura stato pinza; 7-lettura stato inizializzazione; 8-lettura codice errore; 9-lettura posizione; 10-lettura velocità; 11-lettura coppia
    * @return   Codice errore
    */
    int SetAxleLuaGripperFunc(int id, int[] func);

Ottenere Funzione Controllo Azione Pinza Abilitata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Funzione Controllo Azione Pinza Abilitata
    * @param [in] id Numero dispositivo pinza
    * @param [out] func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; 2-impostazione posizione; 3-impostazione velocità; 4-impostazione coppia; 6-lettura stato pinza; 7-lettura stato inizializzazione; 8-lettura codice errore; 9-lettura posizione; 10-lettura velocità; 11-lettura coppia
    * @return   Codice errore
    */
    int GetAxleLuaGripperFunc(int id, ref int[] func);

Scrittura File Slave Robot Ethercat
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Scrittura File Slave Robot Ethercat
    * @param [in] type Tipo file slave, 1-aggiornamento file slave; 2-aggiornamento file configurazione slave
    * @param [in] slaveID Numero slave
    * @param [in] fileName Nome file caricamento
    * @return   Codice errore
    */
    int SlaveFileWrite(int type, int slaveID, string fileName);

Caricamento File Protocollo Aperto LUA Estremità
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Caricamento File Protocollo Aperto LUA Estremità
    * @param filePath Nome percorso file lua locale ".../AXLE_LUA_End_DaHuan.lua"
    * @return Codice errore 
    */
    int AxleLuaUpload(string filePath);

Impostare Modalità Boot Slave Ethercat Robot
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Modalità Boot Slave Ethercat Robot
    * @return   Codice errore
    */
    int SetSysServoBootMode();

Esempio Codice Operazioni File LUA Estremità Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button41_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_JunDuo_Xinjingcheng.lua");

        AxleComParam param = new AxleComParam(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);

        AxleComParam getParam = new AxleComParam();
        robot.GetAxleCommunicationParam(ref getParam);
        Console.WriteLine("GetAxleCommunicationParam param is {0} {1} {2} {3} {4} {5} {6}",
            getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify,
            getParam.timeout, getParam.timeoutTimes, getParam.period);

        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(ref luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0);

        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        robot.GetAxleLuaEnableDeviceType(ref forceEnable, ref gripperEnable, ref ioEnable);
        Console.WriteLine("GetAxleLuaEnableDeviceType param is {0} {1} {2}", forceEnable, gripperEnable, ioEnable);

        int[] func = { 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1 };
        robot.SetAxleLuaGripperFunc(1, func);
        int[] getFunc = new int[16];
        robot.GetAxleLuaGripperFunc(1, ref getFunc);
        int[] getforceEnable = new int[16];
        int[] getgripperEnable = new int[16];
        int[] getioEnable = new int[16];
        robot.GetAxleLuaEnableDevice(ref getforceEnable, ref getgripperEnable, ref getioEnable);
        Console.WriteLine("\ngetforceEnable status : ");
        foreach (int i in getforceEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetgripperEnable status : ");
        foreach (int i in getgripperEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine("\ngetioEnable status : ");
        foreach (int i in getioEnable)
        {
            Console.Write(i + ",");
        }
        Console.WriteLine();
        robot.ActGripper(1, 0);
        Thread.Sleep(2000);
        robot.ActGripper(1, 1);
        Thread.Sleep(2000);
        robot.MoveGripper(1, 90, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine("gripper pos is " + pkg.gripper_position);
            Thread.Sleep(100);
        }
    }

Ottenere Stato Pulsante SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Stato Pulsante SmartTool
    * @param [out] state Stato pulsanti manopola SmartTool;(bit0:0-comunicazione normale; 1-perdita comunicazione; bit1-annulla operazione; bit2-svuota programma;
        bit3-pulsante A; bit4-pulsante B; bit5-pulsante C; bit6-pulsante D; bit7-pulsante E; bit8-pulsante IO; bit9-manuale/automatico; bit10-inizia)
    * @return Codice errore
    */
    int GetSmarttoolBtnState(ref int state);

Esempio Codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button11_Click(object sender, EventArgs e)
    {

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        int state = 0;
        while (true)
        {
            int rtn = robot.GetSmarttoolBtnState(ref state);
            string binaryString = Convert.ToString(state, 2).PadLeft(32, '0');
            Console.WriteLine($"GetSmarttoolBtnState rtn (binario): {binaryString}");
            Thread.Sleep(100);
        }

    }

Caricamento File Lua Protocollo Aperto
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Caricamento File Lua Protocollo Aperto
    * @param  filePath Nome percorso file lua protocollo aperto locale
    * @return Codice errore
    */
    public int OpenLuaUpload(string filePath)


Ottenere Parametri Scheda Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Parametri Scheda Slave
    * @param  type  0-Ethercat，1-CClink, 3-Ethercat, 4-EIP
    * @param  version  Versione protocollo
    * @param  connState  0-non connesso 1-connesso
    * @return   Codice errore
    */
    public int GetFieldBusConfig(int[] type, int[] version, int[] connState)

Scrittura DO Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Scrittura DO Slave
    * @param   DOIndex  Numero DO
    * @param   wirteNum  Quantità scrittura
    * @param   status Valori scrittura, massimo 8
    * @return   Codice errore
    */
    public int FieldBusSlaveWriteDO(int DOIndex, int wirteNum, int[] status)

Scrittura AO Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Scrittura AO Slave
    * @param  AOIndex  Numero AO
    * @param  wirteNum  Quantità scrittura
    * @param  status Valori scrittura, massimo 8
    * @return   Codice errore
    */
    public int FieldBusSlaveWriteAO(int AOIndex, int wirteNum, int[] status)

Lettura DI Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Lettura DI Slave
    * @param  DOIndex  Numero DI
    * @param  readNum  Quantità lettura
    * @param  status Valori letti, massimo 8
    * @return   Codice errore
    */
    public int FieldBusSlaveReadDI(int DOIndex, int readNum, int[] status)

Lettura AI Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Lettura AI Slave
    * @param  AIIndex  Numero AI
    * @param  readNum  Quantità lettura
    * @param  status Valori letti, massimo 8
    * @return   Codice errore
    */
    public int FieldBusSlaveReadAI(int AIIndex, int readNum, double[] status)

Attesa Input DI Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Attesa Input DI Esteso
    * @param  DIIndex Numero DI
    * @param  status 0-livello basso; 1-livello alto
    * @param  waitMs Tempo massimo attesa(ms)
    * @return Codice errore
    */
    public int FieldBusSlaveWaitDI(int DIIndex, int status, int waitMs)

Attesa Input AI Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Attesa Input AI Esteso
    * @param  AIIndex Numero AI
    * @param  waitType 0-maggiore; 1-minore
    * @param  value Valore AI
    * @param  waitMs Tempo massimo attesa(ms)
    * @return Codice errore
    */
    public int FieldBusSlaveWaitAI(int AIIndex, int waitType, double value, int waitMs)

Esempio Codice Istruzioni Interfacce Relative Modalità Slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button101_Click(object sender, EventArgs e)
    {
        int rtn = 0;
    
        int type = 0, version = 0, connState = 0;
        int[] ctrl = new int[8];
        int[] ctrlAO = new int[8];
        int[] DI = new int[8];
        double[] AI = new double[8];
        if (rtn != 0)
        {
            return;
        }
        // Caricare e caricare file protocollo aperto
        robot.OpenLuaUpload("E://zup/CtrlDev_field.lua");
        Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        Thread.Sleep(8000);
    
        // Ottenere tipo protocollo, versione software, stato connessione con PLC
        robot.GetFieldBusConfig(ref type, ref version, ref connState);
        Console.WriteLine($"type is {type}, version is {version}, connState is {connState}");
    
        // Scrivere DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 1;
        ctrl[1] = 0;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);
    
        // Scrivere AO2 = 0x1000
        ctrlAO[0] = 0x1000;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, ref DI);
            Console.WriteLine($"DI0 is {DI[0]}, DI1 is {DI[1]}, DI2 is {DI[2]}, DI3 is {DI[3]}");
            robot.FieldBusSlaveReadAI(0, 3, ref AI);
            Console.WriteLine($"AI0 is {AI[0]}, AI1 is {AI[1]}, AI2 is {AI[2]}");
            Thread.Sleep(10);
        }
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        Console.WriteLine($"FieldBusSlaveWaitDI result is {ret}");

        ret = robot.FieldBusSlaveWaitAI(0, 0, 400.00f, 100);
        Console.WriteLine($"FieldBusSlaveWaitAI result is {ret}"); 
    }

Controllo Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Controllo Ventosa a Matrice
    * @param  slaveID Numero slave
    * @param  len Lunghezza
    * @param  ctrlValue Valore controllo 1-aspirazione massima pressione vuoto 2-aspirazione pressione vuoto impostata 3-fermare aspirazione
    * @return Codice errore
    */
    public int SetSuckerCtrl(int slaveID, int len, int[] ctrlValue)

Ottenere Stato Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Stato Ventosa a Matrice
    * @param  slaveID Numero slave
    * @param  state Stato aspirazione 0-rilascio oggetto 1-rilevato presa oggetto riuscita 2-nessun oggetto aspirato 3-oggetto staccato
    * @param  pressValue Pressione vuoto corrente unità kpa
    * @param  error Codice errore corrente ventosa
    * @return Codice errore
    */
    public int GetSuckerState(int slaveID, int[] state, int[] pressValue, int[] error)

Attesa Stato Ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Attesa Stato Ventosa
    * @param  slaveID Numero slave
    * @param  state Stato aspirazione 0-rilascio oggetto 1-rilevato presa oggetto riuscita 2-nessun oggetto aspirato 3-oggetto staccato
    * @param  ms Tempo massimo attesa
    * @return Codice errore
    */
    public int WaitSuckerState(int slaveID, int state, int ms)

Esempio Codice Istruzioni Controllo Ventosa a Matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void TestSucker(Robot robot)
    {
    
        int[] ctrl = new int[20];
        int state=0;
        int pressValue=0;
        int error=0;
        int rtn;
    
    
        // Caricare e caricare file protocollo aperto
        robot.OpenLuaUpload(@"C:\SDK\CtrlDev_sucker.lua");
        Thread.Sleep(2000);
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        Thread.Sleep(1000);
    
        // Controllare ventosa in modalità broadcast con capacità aspirazione massima
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);
    
        // Monitorare stati ventosa 1 e ventosa 12 in ciclo
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker1 state is {state}, pressValue is {pressValue}, error num is {error}");
            robot.GetSuckerState(12, ref state, ref pressValue, ref error);
            Console.WriteLine($"sucker12 state is {state}, pressValue is {pressValue}, error num is {error}");
            Thread.Sleep(100);
        }
        // Attendere ventosa 1 raggiunga stato aspirato, timeout 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        Console.WriteLine($"WaitSuckerState result is {ret}");
    
        // Modalità unicast spegnere ventosa 1 e 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);
    
        robot.CloseRPC();
    }

Funzione Accensione/Spegnimento Periferica Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Funzione Accensione/Spegnimento Periferica Laser
     * @param [in] OnOff 0-spegnere 1-accendere
     * @param [in] weldId ID saldatura default 0
     * @return Codice errore
     */
    public int LaserTrackingLaserOnOff(int OnOff, int weldId)
    
Funzione Inizio/Fine Tracciamento Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    
    /**
     * @brief Funzione Inizio/Fine Tracciamento Laser
     * @param [in] OnOff 0-fine 1-inizio
     * @param [in] coordId Numero sistema coordinate utensile periferica laser
     * @return Codice errore
     */
    public int LaserTrackingTrackOnOff(int OnOff, int coordId)

Ricerca Posizione Laser - Direzione Fissa Inversa
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Ricerca Posizione Laser - Direzione Fissa Inversa
     * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
     * @param [in] vel Velocità unità%
     * @param [in] distance Distanza massima ricerca unità mm
     * @param [in] timeout Timeout ricerca unità ms
     * @param [in] posSensorNum Numero sistema coordinate utensile calibrato laser
     * @return Codice errore
     */
    public int LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum)
    
Ricerca Posizione Laser - Direzione Arbitraria
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Ricerca Posizione Laser - Direzione Arbitraria
     * @param [in] directionPoint Coordinate xyz punto input ricerca
     * @param [in] vel Velocità unità%
     * @param [in] distance Distanza massima ricerca unità mm
     * @param [in] timeout Timeout ricerca unità ms
     * @param [in] posSensorNum Numero sistema coordinate utensile calibrato laser
     * @return Codice errore
     */
    public int LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum)
   
Fine Ricerca Posizione Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
    * @brief  Fine Ricerca Posizione Laser
    * @return Codice errore
    */
    public int LaserTrackingSearchStop()

Configurazione IP Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Configurazione IP Laser
     * @param [in] ip Indirizzo IP periferica laser
     * @param [in] port Numero porta periferica laser
     * @return Codice errore
     */
    public int LaserTrackingSensorConfig(string ip, int port)

Configurazione Periodo Campionamento Periferica Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Configurazione Periodo Campionamento Periferica Laser
     * @param [in] period Periodo campionamento periferica laser unità ms
     * @return Codice errore
     */
    public int LaserTrackingSensorSamplePeriod(int period)

Caricamento Driver Periferica Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Caricamento Driver Periferica Laser
     * @param [in] type Tipo protocollo driver periferica laser 101-Ruiniao 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Codice errore
     */
    public int LoadPosSensorDriver(int type)

Scaricamento Driver Periferica Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Scaricamento Driver Periferica Laser
     * @return Codice errore
     */
    public int UnLoadPosSensorDriver()

Registrazione Traiettoria Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Registrazione Traiettoria Saldatura Laser
     * @param [in] status 0-fermare registrazione 1-tracciamento tempo reale  2-iniziare registrazione
     * @param [in] delayTime Tempo ritardo unità ms
     * @return Codice errore
     */
    public int LaserSensorRecord1(int status, int delayTime)

Riproduzione Traiettoria Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Riproduzione Traiettoria Saldatura Laser
     * @param [in] delayTime Tempo ritardo unità ms
     * @param [in] speed Velocità unità%
     * @return Codice errore
     */
    public int LaserSensorReplay(int delayTime, double speed)

Riproduzione Tracciamento Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Riproduzione Tracciamento Laser
     * @return Codice errore
     */
    public int MoveLTR()

Riproduzione Traiettoria Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Riproduzione Traiettoria Saldatura Laser
    * @param [in] delayMode Modalità 0-Tempo Ritardo 1-Distanza Ritardo
    * @param [in] delayTime Tempo di ritardo in millisecondi (ms)
    * @param [in] delayDisExAxisNum Numero Asse Esteso
    * @param [in] delayDis Distanza di ritardo in millimetri (mm)
    * @param [in] sensitivePara Coefficiente di Sensibilità della Compensazione
    * @param [in] trackMode Tipo Tracciamento a Punto Fisso. 0-Movimento Asincrono Asse Esteso; 1-Robot
    * @param [in] triggerMode Metodo di Attivazione Tracciamento a Punto Fisso. 0-Durata Tracciamento; 1-IO
    * @param [in] runTime Durata Tracciamento a Punto Fisso del Robot in secondi (s)
    * @param [in] speed Velocità in percentuale (%)
    * @return Codice Errore
    */
    public int LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum,double delayDis, double sensitivePara, int trackMode, int triggerMode,double runTime, double speed)
    
Movimento a Punto Inizio Registrazione Saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Movimento a Punto Inizio Registrazione Saldatura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocità unità%
     * @return Codice errore
     */
    public int MoveToLaserRecordStart(int moveType, double ovl)

Movimento a Punto Fine Registrazione Saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Movimento a Punto Fine Registrazione Saldatura
     * @param [in] moveType 0-PTP 1-LIN
     * @param [in] ovl Velocità unità%
     * @return Codice errore
     */
    public int MoveToLaserRecordEnd(int moveType, double ovl)

Movimento a Punto Ricerca Sensore Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Movimento a Punto Ricerca Sensore Laser
     * @param [in] moveFlag Tipo movimento: 0-PTP; 1-LIN
     * @param [in] ovl Fattore di scala velocità, 0-100
     * @param [in] dataFlag Selezione dati cache saldatura: 0-eseguire dati pianificati; 1-eseguire dati registrati
     * @param [in] plateType Tipo piastra: 0-piastra ondulata; 1-piastra a nido d'ape; 2-piastra recinzione; 3-fusto olio; 4-acciaio corazza ondulata
     * @param [in] trackOffectType Tipo offset sensore laser: 0-nessun offset; 1-offset sistema base; 2-offset sistema utensile; 3-offset dati originali sensore laser
     * @param [in] offset Quantità offset
     * @return Codice errore
     */
    public int MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset)
    
Ottenere Informazioni Coordinate Punto Ricerca Sensore Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    /**
     * @brief Ottenere Informazioni Coordinate Punto Ricerca Sensore Laser
     * @param [in] trackOffectType Tipo offset sensore laser: 0-nessun offset; 1-offset sistema base; 2-offset sistema utensile; 3-offset dati originali sensore laser
     * @param [in] offset Quantità offset
     * @param [out] jPos Posizione articolare[°]
     * @param [out] descPos Posizione cartesiana[mm]
     * @param [out] tool Sistema coordinate utensile
     * @param [out] user Sistema coordinate pezzo
     * @param [out] exaxis Posizione asse esteso[mm]
     * @return Codice errore
     */
    public int GetLaserSeamPos(int trackOffectType, DescPose offset, ref JointPos jPos, ref DescPose descPos, ref int tool, ref int user, ref ExaxisPos exaxis)

Esempio Codice Configurazione Parametri Sensore Periferica Laser e Debug
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserConfig()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);
        robot.LaserTrackingLaserOnOff(0, 0);
        System.Threading.Thread.Sleep(3000);
        robot.LaserTrackingLaserOnOff(1, 0);
    }

Esempio Codice Scansione Traiettoria Laser e Riproduzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    void testLaserRecordAndReplay()
    { 
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i=0;i<10;++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserSensorRecord1(2, 10);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 50, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);

            robot.LaserSensorRecord1(0, 10);
            robot.MoveToLaserRecordStart(1, 30);
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            robot.LaserSensorRecord1(0, 10);
            Console.WriteLine($"Numero completamenti : {i+1} ");
        }
                
    }

Esempio Codice Ricerca Posizione Laser e Tracciamento Tempo Reale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public static void testLasertrack()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        robot.OpenLuaUpload("D://zUP/CtrlDev_laser_ruiniu-0117.lua");
        System.Threading.Thread.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        System.Threading.Thread.Sleep(8000);
        for (int i = 0; i < 10; ++i)
        {
            JointPos startjointPos = new JointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose = new DescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
            DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
            DescTran directionPoint = new DescTran();

            robot.MoveL(startjointPos, startdescPose, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 3);
            robot.LaserTrackingSearchStop();
            robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);

            robot.LaserTrackingTrackOnOff(1, 3);

            JointPos endjointPos = new JointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose = new DescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, exaxisPos, 0, 0, offdese, 0);
            robot.LaserTrackingTrackOnOff(0, 3);
            Console.WriteLine($"Numero completamenti : {i + 1} ");
        }
    }

Esempio Codice Tracciamento Laser con Asse Esteso e Robot Sincronizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:


    public void TestLaserTrackAndExitAxis()
    {   
        ExaxisPos startexaxisPos = new ExaxisPos(0, 0, 0, 0);
        ExaxisPos seamexaxisPos = new ExaxisPos(-10, 0, 0, 0);
        ExaxisPos endexaxisPos = new ExaxisPos(-30, 0, 0, 0);      
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);     
        JointPos startjointPos = new JointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
        DescPose startdescPose = new DescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
        for (int i=0;i<10;++i)
        {
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);
            Console.WriteLine("11111");
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            Console.WriteLine("2222");
            int tool = 0;
            int user = 0;
            JointPos seamjointPos = new JointPos();
            DescPose seamdescPose = new DescPose();
            robot.GetLaserSeamPos(0, offdese, ref seamjointPos, ref seamdescPose, ref tool, ref user, ref startexaxisPos);
            Console.WriteLine($"{seamjointPos.jPos[0]}, {seamjointPos.jPos[1]}, {seamjointPos.jPos[2]}, " +
                            $"{seamjointPos.jPos[3]}, {seamjointPos.jPos[4]}, {seamjointPos.jPos[5]}, " +
                            $"{seamdescPose.tran.x}, {seamdescPose.tran.y}, {seamdescPose.tran.z}, " +
                            $"{seamdescPose.rpy.rx}, {seamdescPose.rpy.ry}, {seamdescPose.rpy.rz}");
            if (ret == 0)
            {
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);
                Console.WriteLine("3333");
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos = new JointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose = new DescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            Console.WriteLine($"Numero completamenti : {i + 1} ");
        }     
    }