Controllo di Forza del Robot
===================================

.. toctree:: 
    :maxdepth: 5

Configurare il sensore di forza
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Configurare il sensore di forza
    * @param  config company: produttore del sensore di forza, 17-Kunwei Technology, 19-Academy 11, 20-Sensore ATI, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xin Jingcheng (XJC), 26-NSR
    * @param  config device: numero dispositivo, Kunwei (0-KWR75B), Academy 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A), NBIT (0-XLH93003ACS), Xin Jingcheng XJC (0-XJC-6F-D82), NSR (0-NSR-FTSensorA)
    * @param  config softvesion: numero versione software, non utilizzato attualmente, default 0
    * @param  config bus: posizione bus terminale del dispositivo, non utilizzato attualmente, default 0
    * @return  Codice errore
    */
    int FT_SetConfig(DeviceConfig config); 

Ottenere la configurazione del sensore di forza 
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere la configurazione del sensore di forza 
    * @param [out] config company: produttore del sensore di forza, 17-Kunwei Technology, 19-Academy 11, 20-Sensore ATI, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] config device: numero dispositivo, Kunwei (0-KWR75B), Academy 11 (0-MCS6A-200-4), ATI (0-AXIA80-M8), Zhongke Midian (0-MST2010), Weihang Minxin (0-WHC6L-YB-10A)
    * @param [out] config softvesion: numero versione software, non utilizzato attualmente, default 0
    * @param [out] config bus: posizione bus terminale del dispositivo, non utilizzato attualmente, default 0
    * @return Codice errore 
    */ 
    int FT_GetConfig(DeviceConfig config); 

Attivare il sensore di forza
++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Attivare il sensore di forza
    * @param  [in] act  0-reset, 1-attiva
    * @return  Codice errore
    */
    int FT_Activate(int act); 

Calibrazione zero del sensore di forza
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calibrazione zero del sensore di forza
    * @param  [in] act  0-rimuovi zero, 1-calibrazione zero
    * @return  Codice errore
    */
    int FT_SetZero(int act); 

Impostare il sistema di riferimento del sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Impostare il sistema di riferimento del sensore di forza
    * @param  [in] type  0-sistema coordinato utensile, 1-sistema coordinato base, 2-sistema coordinato libero
    * @param  [in] coord  valore del sistema coordinato libero
    * @return  Codice errore
    */
    int FT_SetRCS(int type, DescPose coord);

Impostare il peso del carico sotto il sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostare il peso del carico sotto il sensore di forza
    * @param [in] weight peso del carico kg
    * @return Codice errore
    */
    int SetForceSensorPayLoad(double weight);

Impostare il centro di gravità del carico sotto il sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostare il centro di gravità del carico sotto il sensore di forza
    * @param [in] cog centro di gravità del carico mm
    * @return Codice errore
    */
    int SetForceSensorPayLoadCog(DescTran cog);

Ottenere il peso del carico sotto il sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere il peso del carico sotto il sensore di forza
    * @return List[0]: codice errore; List[1] : weight peso del carico kg
    */
    List<Number> GetForceSensorPayLoad();

Ottenere il centro di gravità del carico sotto il sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere il centro di gravità del carico sotto il sensore di forza
    * @param [out] cog centro di gravità del carico mm
    * @return Codice errore
    */
    int GetForceSensorPayLoadCog(DescTran cog);

Calibrazione zero automatica del sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione zero automatica del sensore di forza
    * @param [in] massCenter massa del sensore (kg) e centro di gravità (mm)
    * @return Codice errore
    */
    int ForceSensorAutoComputeLoad(MassCenter massCenter);

Ottenere dati forza/coppia nel sistema di riferimento
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere dati forza/coppia nel sistema di riferimento
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] ft  forza/coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice errore
    */   
    int FT_GetForceTorqueRCS(int flag, ForceTorque ft); 

Ottenere dati forza/coppia originali del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere dati forza/coppia originali del sensore di forza
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] ft  forza/coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice errore
    */   
    int FT_GetForceTorqueOrigin(int flag, ForceTorque ft); 

Esempio di codice per configurazione e calibrazione zero automatica sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTInit(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company,device,softversion,bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose ftCoord = new DescPose();
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayload(0.824);

        DescTran tr=new DescTran(0.778, 2.554, 48.765);
        robot.SetForceSensorPayloadCog(tr);
        List<Number> weight = new ArrayList<>();
        double x = 0, y = 0, z = 0;
        weight=robot.GetForceSensorPayload();
        robot.GetForceSensorPayloadCog(tr);
        tr.x=0;
        tr.y=0;
        tr.z=0;
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr);

        double computeWeight = 0;
        DescTran tran = new DescTran();
        MassCenter mass=new MassCenter();
        mass.weight=weight.get(1).doubleValue();
        mass.cog=tran;
        robot.ForceSensorAutoComputeLoad(mass);
        return 0;
    }

Registrazione identificazione peso carico
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrazione identificazione peso carico
    * @param  [in] id  numero sistema coordinato sensore, range [1~14]
    * @return  Codice errore
    */
    int FT_PdIdenRecord(int id);

Calcolo identificazione peso carico
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo identificazione peso carico
    * @return  List[0]: codice errore; List[1] : double weight  peso carico, unità kg
    */   
    List<Number> FT_PdIdenCompute();

Registrazione identificazione centro di gravità carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Registrazione identificazione centro di gravità carico
    * @param  [in] id  numero sistema coordinato sensore, range [1~14]
    * @param  [in] index numero punto, range [1~3]
    * @return  Codice errore
    */
    int FT_PdCogIdenRecord(int id, int index); 

Calcolo identificazione centro di gravità carico
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo identificazione centro di gravità carico
    * @param  [out] cog  centro di gravità carico, unità mm
    * @return  Codice errore
    */   
    int FT_PdCogIdenCompute(DescTran cog);

Esempio di codice identificazione carico sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFTLoadCompute(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ft);
        robot.FT_SetZero(1);
        robot.Sleep(1000);

        DescPose tcoord = new DescPose();
        tcoord.tran.z = 35.0;
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        robot.Sleep(1000);

        List<Number> weight =new ArrayList<>();
        weight=robot.FT_PdIdenCompute();

        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart(desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart(desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart(desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
        robot.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);
        robot.Sleep(1000);
        DescTran cog=new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(cog);

        robot.CloseRPC();
        return 0;
    }

Protezione collisione
++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Protezione collisione
    * @param  [in] flag 0-disattiva protezione collisione, 1-attiva protezione collisione
    * @param  [in] sensor_id numero sensore di forza
    * @param  [in] select  selezione sei gradi di libertà per rilevamento collisione, 0-non rilevare, 1-rileva
    * @param  [in] ft  forza/coppia collisione, fx,fy,fz,tx,ty,tz
    * @param  [in] max_threshold soglia massima
    * @param  [in] min_threshold soglia minima
    * @note   Intervallo rilevamento forza/coppia: (ft-min_threshold, ft+max_threshold)
    * @return  Codice errore
    */   
    int FT_Guard(int flag, int sensor_id, Object[] select, ForceTorque ft, Object[] max_threshold, Object[] min_threshold); 

Esempio di codice protezione collisione
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//imposta tentativi riconnessione, intervallo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("connessione rpc successo");
        }
        else
        {
            System.out.println("connessione rpc fallita");
            return ;
        }
        byte flag = 1;
        byte sensor_id = 8;
        Object[] select = { 1, 0, 0, 0, 0, 0 };//abilita solo protezione collisione asse x
        Object[] max_threshold = { 5.0, 0.01, 0.01, 0.01, 0.01, 0.01 };
        Object[] min_threshold = { 3.0, 0.01, 0.01, 0.01, 0.01, 0.01 };

        ForceTorque ft = new ForceTorque(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        DescPose  desc_p1, desc_p2, desc_p3;
        desc_p1 = new DescPose(-14.404,-455.283,319.847,-172.935,25.141,-68.097);
        desc_p2 = new DescPose(-107.999,-599.174,285.939,153.472,12.686,-71.284);
        desc_p3 = new DescPose(6.586,-704.897,309.638,178.909,-27.759,-70.479);

        int rtn =  robot.FT_Guard(flag, sensor_id, select, ft, max_threshold, min_threshold);
        System.out.println("FT_Guard avvio rtn {rtn}");
        robot.MoveCart(desc_p1, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p2, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart(desc_p3, 0, 0, 20, 100.0f, 100.0f, -1.0f, -1);
    }

Controllo forza costante
+++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controllo forza costante
    * @param  flag 0-disattiva controllo forza costante, 1-attiva controllo forza costante
    * @param  sensor_id numero sensore di forza
    * @param  select  selezione sei gradi di libertà per rilevamento collisione, 0-non rilevare, 1-rileva
    * @param  ft  forza/coppia collisione, fx,fy,fz,tx,ty,tz
    * @param  ft_pid parametri pid forza, parametri pid coppia
    * @param  adj_sign controllo avvio/arresto adattativo, 0-disattiva, 1-attiva
    * @param  ILC_sign controllo avvio/arresto ILC, 0-arresta, 1-addestra, 2-operazione
    * @param  max_dis distanza regolazione massima, unità mm
    * @param  max_ang angolo regolazione massimo, unità deg
    * @param  M parametri massa
    * @param  B parametri smorzamento
    * @param  polishRadio raggio levigatura, unità mm
    * @param  filter_Sign flag attivazione filtro 0-off; 1-on, default off
    * @param  posAdapt_sign flag attivazione adattamento posa 0-off; 1-on, default off
    * @param  isNoBlock flag bloccante, 0-bloccante; 1-non bloccante
    * @return  Codice errore
    */
    public int FT_Control(int flag, int sensor_id, int[] select, ForceTorque ft, double[] ft_pid, int adj_sign, int ILC_sign, double max_dis, double max_ang,double[] M,double[] B, double polishRadio,int filter_Sign, int posAdapt_sign, int isNoBlock)

Esempio di codice controllo forza costante con smorzamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFTControlWithDamping(Robot robot)
    {
        int sensor_id = 10;
        int[] select = { 0,0,1,0,0,0 };
        double[] ft_pid = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 100.0;
        double max_ang = 20;
        ForceTorque ft =new ForceTorque(0,0,0,0,0,0);
        ft.fz = -10.0;
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        JointPos j1=new JointPos(-118.985, -86.882, -118.139, -65.019, 90.002, 54.951);
        JointPos j2=new JointPos(-77.055, -77.218, -126.219, -66.591, 90.028, 96.881);
        DescPose desc_p1=new DescPose(-300.856, -332.618, 309.240, 179.976, -0.031, 96.065);
        DescPose desc_p2=new DescPose(-16.399, -383.760, 309.312, 179.975, -0.031, 96.064);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = {2.0, 2.0};
        double[] B = {8.0, 8.0};
        double polishRadio;
        int filter_Sign;
        int posAdapt_sign;
        int isNoBlock;
        DescPose ftCoord =new DescPose();
        robot.FT_SetRCS(2, ftCoord);
        int rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, 0, 0, 1, 0);
        System.out.printf("FT_Control avvio rtn è %d\n", rtn);
        rtn = robot.MoveL(j1, desc_p1, 0, 0, 100.0, 100.0, 20.0, -1.0,0, epos, 0, 0, offset_pos,0,0,10);
        rtn = robot.MoveL(j2, desc_p2, 0, 0, 100.0, 100.0, 20.0, -1.0, 0,epos, 0, 0, offset_pos,0,0,10);
        rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, 0, 0, 1, 0);
        System.out.printf("FT_Control fine rtn è %d\n", rtn);
        robot.CloseRPC();
    }

Avvio controllo conformità
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Avvio controllo conformità
    * @param  [in] p coefficiente regolazione posizione o coefficiente conformità
    * @param  [in] force soglia forza attivazione conformità, unità N
    * @return  Codice errore
    */   
    int FT_ComplianceStart(double p, double force);

Arresto controllo conformità
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Arresto controllo conformità
    * @return  Codice errore
    */   
    int FT_ComplianceStop(); 

Esempio di codice controllo conformità
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCompliance(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);

        robot.Sleep(1000);

        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);

        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);

        int flag = 1;
        int sensor_id = 1;
        Object[] select =new Object[] { 1,1,1,0,0,0 };
        Object[] ft_pid =new Object[] { 0.0005,0.0,0.0,0.0,0.0,0.0 };
        int adj_sign = 0;
        int ILC_sign = 0;
        double max_dis = 100.0;
        double max_ang = 0.0;

        ForceTorque ft=new ForceTorque(0,0,0,0,0,0);
        DescPose  offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ft.fx = -10.0;
        ft.fy = -10.0;
        ft.fz = -10.0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
        double p = 0.00005;
        double force = 30.0;
        int rtn = robot.FT_ComplianceStart(p, force);

        int count = 15;
        while (count>0)
        {
            robot.MoveL(j1, desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 1, offset_pos,0,10);
            robot.MoveL(j2, desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0,0, epos, 0, 0, offset_pos,0,10);
            count -= 1;
        }
        robot.FT_ComplianceStop();
        flag = 0;
        robot.FT_Control(flag, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);

        robot.CloseRPC();
        return 0;
    }

Inizializzazione identificazione carico
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizializzazione identificazione carico
    * @return Codice errore
    */
    int LoadIdentifyDynFilterInit();

Inizializzazione variabili identificazione carico
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizializzazione variabili identificazione carico
    * @return Codice errore
    */
    int LoadIdentifyDynVarInit();

Programma principale identificazione carico
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Programma principale identificazione carico
    * @param [in] joint_torque coppia giunti
    * @param [in] joint_pos posizione giunti
    * @param [in] t periodo campionamento
    * @return Codice errore
    */
    int LoadIdentifyMain(Object[] joint_torque, Object[] joint_pos, double t);

Ottenere risultati identificazione carico
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere risultati identificazione carico
    * @param [in] gain
    * @return List[0]: codice errore; List[1] : double weight peso carico; List[2]: x centro di gravità carico X mm; List[3] : y centro di gravità carico Y mm; List[2]: z centro di gravità carico Z mm
    */
    List<Number> LoadIdentifyGetResult(Object[] gain);

Esempio di codice identificazione carico robot
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestIdentify(Robot robot)
    {
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();

        retval = robot.LoadIdentifyDynVarInit();

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0,0,0,0,0,0);
        List<Number> joint_toq=new ArrayList<>();
        robot.GetActualJointPosDegree( posJ);
        posJ.J2 = posJ.J2 + 10;
        joint_toq=robot.GetJointTorques(0);

        Object[] gain =new Object[] { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
        double weight = 0;
        DescTran load_pos=new DescTran(0,0,0);
        List<Number> num=new ArrayList<>();
        num = robot.LoadIdentifyGetResult(gain);

        robot.CloseRPC();
        return 0;

    }

Trascinamento assistito da sensore di forza
++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Trascinamento assistito da sensore di forza
    * @param [in] status stato controllo, 0-disattiva; 1-attiva
    * @param [in] asaptiveFlag flag attivazione adattativo, 0-disattiva; 1-attiva
    * @param [in] interfereDragFlag flag trascinamento zona interferenza, 0-disattiva; 1-attiva
    * @param [in] ingularityConstraintsFlag strategia punti singolari, 0-evitare; 1-attraversare
    * @param [in] forceCollisionFlag flag rilevamento collisione robot durante trascinamento assistito; 0-disattiva; 1-attiva
    * @param [in] M coefficiente inerzia
    * @param [in] B coefficiente smorzamento
    * @param [in] K coefficiente rigidezza
    * @param [in] F soglia forza sei dimensioni trascinamento
    * @param [in] Fmax limite forza trascinamento massima Nm
    * @param [in] Vmax limite velocità giunti massima °/s
    * @return Codice errore
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag, int forceCollisionFlag, Object[] M, Object[] B, Object[] K, Object[] F, double Fmax, double Vmax)

Ottenere stato interruttore trascinamento sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottenere stato interruttore trascinamento sensore di forza
    * @return List[0]: codice errore; List[1] : dragState stato controllo trascinamento assistito da sensore di forza, 0-disattiva; 1-attiva; List[1] : sixDimensionalDragState stato controllo trascinamento assistito sei dimensioni, 0-disattiva; 1-attiva
    */
    List<Integer> GetForceAndTorqueDragState();

Attivazione automatica sensore di forza dopo cancellazione errore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attivazione automatica sensore di forza dopo cancellazione errore
    * @param [in] status stato controllo, 0-disattiva; 1-attiva
    * @return Codice errore
    */
    int SetForceSensorDragAutoFlag(int status)

Esempio di codice trascinamento assistito da sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestEndForceDragCtrl(Robot robot)
    {
        DescTran tr1=new DescTran(0,0,0);
        robot.SetForceSensorPayload(0);
        robot.SetForceSensorPayloadCog(tr1);

        robot.SetForceSensorDragAutoFlag(1);

        Object[] M =new Object[] { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        Object[] B =new Object[] { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        Object[] K =new Object[] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        Object[] F =new Object[] { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);

        robot.Sleep(10000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        List<Integer> state=new ArrayList<>();
        state=robot.GetForceAndTorqueDragState();

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
        return 0;
    }

Impostare interruttore e parametri trascinamento misto sei dimensioni e impedenza giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostare interruttore e parametri trascinamento misto sei dimensioni e impedenza giunti
    * @param [in] status stato controllo, 0-disattiva; 1-attiva
    * @param [in] impedanceFlag flag attivazione impedenza, 0-disattiva; 1-attiva
    * @param [in] lamdeGain guadagno trascinamento
    * @param [in] KGain guadagno rigidezza
    * @param [in] BGain guadagno smorzamento
    * @param [in] dragMaxTcpVel limite velocità lineare massima terminale trascinamento
    * @param [in] dragMaxTcpOriVel limite velocità angolare massima terminale trascinamento
    * @return Codice errore
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, Object[] lamdeGain, Object[] KGain, Object[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Esempio di codice trascinamento misto sei dimensioni e impedenza giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestForceAndJointImpedance(Robot robot)
    {
        robot.DragTeachSwitch(1);
        Object[] lamdeDain =new Object[] { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        Object[] KGain = new Object[]{ 0, 0, 0, 0, 0, 0 };
        Object[] BGain =new Object[] { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.Sleep(10000);

        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000.0, 180.0);

        robot.CloseRPC();
        return 0;
    }

Controllo avvio/arresto impedenza
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Controllo avvio/arresto impedenza
    * @param [in] status 0: disattiva; 1-attiva
    * @param [in] workSpace 0-spazio giunti; 1-spazio cartesiano
    * @param [in] forceThreshold soglia forza attivazione (N)
    * @param [in] m parametri massa
    * @param [in] b parametri smorzamento
    * @param [in] k parametri rigidezza
    * @param [in] maxV velocità lineare massima (mm/s)
    * @param [in] maxVA accelerazione lineare massima (mm/s2)
    * @param [in] maxW velocità angolare massima (°/s)
    * @param [in] maxWA accelerazione angolare massima (°/s2)
    * @return Codice errore
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Esempio di codice controllo avvio/arresto impedenza robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestImpedanceControl(Robot robot)
    {
        JointPos j1=new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2=new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1=new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2=new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 200.0;
        double ovl = 100.0;
        double blendT = -1.0;
        double blendR = -1.0;
        int flag = 0;
        int search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        DeviceConfig con=new DeviceConfig(company, device, softversion, bus);
        robot.FT_SetConfig(con);
        robot.Sleep(1000);
        robot.FT_GetConfig(con);
        System.out.println("FT config:"+con.company+","+con.device+","+con.softwareVersion+"con"+ con.bus);
        robot.Sleep(1000);
        robot.FT_Activate(0);
        robot.Sleep(1000);
        robot.FT_Activate(1);
        robot.Sleep(1000);
        robot.Sleep(1000);
        robot.FT_SetZero(0);
        robot.Sleep(1000);
        robot.FT_SetZero(1);
        robot.Sleep(1000);
        double[] forceThreshold = { 30,30,30,5,5,5 };
        double[] m= { 0.1,0.1,0.1,0.02,0.02,0.02 };
        double[] b = { 1,1,1,0.08,0.08,0.08 };
        double[] k = { 0,0,0,0,0,0 };
        int rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        System.out.println("ImpedanceControlStartStop codice errore:"+ rtn);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1,0,-1, 1);
        System.out.println("movel codice errore:"+ rtn);
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        robot.CloseRPC();
        return 0;
    }