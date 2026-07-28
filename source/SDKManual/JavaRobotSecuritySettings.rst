Impostazioni di Sicurezza del Robot
============================================

.. toctree:: 
    :maxdepth: 5

Impostazione Livello di Collisione
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il livello di collisione
    * @param  [in]  mode  0-Livello, 1-Percentuale
    * @param  [in]  level Soglia di collisione, intervallo per livello [1-10 corrispondente ai livelli 1-10, 100-disattiva], intervallo per percentuale [0~10 corrispondente a 0% - 100%]
    * @param  [in]  config 0-Non aggiorna il file di configurazione, 1-Aggiorna il file di configurazione
    * @return  Codice errore
    */
    int SetAnticollision(int mode, Object[] level, int config);

Impostazione Strategia Post-Collisione
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la strategia post-collisione
    * @param  [in] strategy  0-Segnala errore e ferma, 1-Continua esecuzione
    * @param  [in] safeTime  Tempo di arresto sicuro [1000 - 2000]ms
    * @param  [in] safeDistance  Distanza di arresto sicuro [1-150]mm
    * @param  [in] safetyMargin  Coefficiente di sicurezza j1-j6 [1-10]
    * @return  Codice errore  
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]);

Avvio Funzione di Rilevamento Collisione con Soglie Personalizzate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Avvia la funzione di rilevamento collisione con soglie personalizzate, imposta le soglie di rilevamento collisione per giunti e TCP
    * @param  [in] flag 1-Attiva solo rilevamento giunti; 2-Attiva solo rilevamento TCP; 3-Attiva contemporaneamente rilevamento giunti e TCP
    * @param  [in] jointDetectionThreshould Soglia di rilevamento collisione giunti j1-j6
    * @param  [in] tcpDetectionThreshould Soglia di rilevamento collisione TCP, xyzabc
    * @param  [in] block 0-Non bloccante; 1-Bloccante
    * @return  Codice errore
    */   
    public int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Fine Funzione di Rilevamento Collisione con Soglie Personalizzate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /**
    * @brief  Termina la funzione di rilevamento collisione con soglie personalizzate
    * @return  Codice errore
    */   
    public int CustomCollisionDetectionEnd();

Esempio di Codice per Impostazione Livello Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollision(Robot robot)
    {
        int mode = 0;
        int config = 1;
        Object[] level1 = new Object[]{ 1.0,2.0,3.0,4.0,5.0,6.0 };
        Object[] level2 = new Object[]{ 50.0,20.0,30.0,40.0,50.0,60.0 };

        int rtn = robot.SetAnticollision(mode, level1, config);
        System.out.println("SetAnticollision mode 0 rtn is: "+ rtn);
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        System.out.println("SetAnticollision mode 1 rtn is :"+ rtn);

        JointPos p1Joint=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos p2Joint=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose p1Desc=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose p2Desc=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese=new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, 2,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ResetAllError();
        int[] safety = new int[]{ 5,5,5,5,5,5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        System.out.println("SetCollisionStrategy rtn is:"+ rtn);

        double[] jointDetectionThreshould = new double[]{ 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould =new double[] { 60,60,60,60,60,60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        System.out.println("CustomCollisionDetectionStart rtn is :"+ rtn);

        robot.MoveL(p1Joint, p1Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(p2Joint, p2Desc, 0, 0, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        rtn = robot.CustomCollisionDetectionEnd();
        System.out.println("CustomCollisionDetectionEnd rtn is: "+ rtn);
        return 0;
    }

Impostazione Limiti Positivi
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta i limiti positivi
    * @param  [in] limit Posizioni dei sei giunti, unità deg
    * @return  Codice errore
    */
    int SetLimitPositive(Object[] limit);

Impostazione Limiti Negativi
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta i limiti negativi
    * @param  [in] limit Posizioni dei sei giunti, unità deg
    * @return  Codice errore
    */
    int SetLimitNegative(Object[] limit);

Ottenimento Angoli Limiti Software dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene gli angoli dei limiti software dei giunti
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] negative  Angoli limite negativi, unità deg
    * @param  [out] positive  Angoli limite positivi, unità deg
    * @return  Codice errore
    */
    int GetJointSoftLimitDeg(int flag, Object[] negative, Object[] positive);

Esempio di Codice per Impostazione Limiti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLimit(Robot robot)
    {
        Object[] plimit =new Object[] { 170.0,80.0,150.0,80.0,170.0,160.0 };
        robot.SetLimitPositive(plimit);
        Object[] nlimit =new Object[] { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
        robot.SetLimitNegative(nlimit);

        Object[] neg_deg =new Object[] {0, 0 , 0, 0, 0, 0}, pos_deg = new Object[]{0, 0 , 0, 0, 0, 0};
        robot.GetJointSoftLimitDeg(1,  neg_deg,  pos_deg);
        System.out.println("neg limit deg:"+ neg_deg[0]+","+ neg_deg[1]+","+ neg_deg[2]+","+ neg_deg[3]+","+ neg_deg[4]+","+ neg_deg[5]);
        System.out.println("pos limit deg:"+pos_deg[0]+","+ pos_deg[1]+","+ pos_deg[2]+","+ pos_deg[3]+","+ pos_deg[4]+","+pos_deg[5]);
        return 0;
    }

Impostazione Metodo di Rilevamento Collisione Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il metodo di rilevamento collisione del robot
    * @param [in] method Metodo di rilevamento collisione: 0-Modalità corrente; 1-Doppio encoder; 2-Corrente e doppio encoder attivi contemporaneamente
    * @param [in] thresholdMode Modalità soglia livello collisione; 0-Modalità soglia fissa livello collisione; 1-Soglie di rilevamento collisione personalizzate
    * @return Codice errore
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode);

Attivazione/Disattivazione Rilevamento Collisione in Stato Statico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta l'attivazione/disattivazione del rilevamento collisione in stato statico
    * @param  [in] status 0-Disattiva; 1-Attiva
    * @return  Codice errore
    */
    public int SetStaticCollisionOnOff(int status);

Esempio di Codice per Impostazione Metodo Rilevamento Collisione Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCollisionMethod(Robot robot)
    {
        int rtn = robot.SetCollisionDetectionMethod(0);

        rtn = robot.SetStaticCollisionOnOff(1);
        System.out.println("SetStaticCollisionOnOff On rtn is:"+ rtn);
        robot.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        System.out.println("SetStaticCollisionOnOff Off rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Rilevamento Coppia/Potenza Giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Rilevamento coppia/potenza giunti
    * @param  [in] status 0-Disattiva; 1-Attiva
    * @param  [in] power Imposta potenza massima (W)
    * @return  Codice errore
    */
    public int SetPowerLimit(int status, double power);

Esempio di Codice per Rilevamento Potenza Giunti
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPowerLimit(Robot robot)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #servoJT inizia
        int error = 0;
        while (count > 0)
        {
            count = count - 1;
            robot.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);

        robot.CloseRPC();
        return 0;
    }

Imposta i Parametri di Velocità di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i parametri di velocità di sicurezza
    * @param enable 0-disabilitato; 1-abilitato in modalità manuale; 2-abilitato in tutte le modalità (limitazione automatica della velocità non supportata)
    * @param maxTCPVel Limite massimo velocità TCP; [0-1000] mm/s
    * @param strategy Strategia dopo superamento velocità; 0-ferma con allarme; 1-limitazione automatica della velocità; 2-ferma con allarme e disabilita
    * @param maxJointVel Velocità massima per 6 giunti (°/s), default 45°/s
    * @return Codice di errore
    */
    public int SetVelReducePara(int enable, double maxTCPVel, int strategy, double[] maxJointVel)
        
Esempio di Codice SDK per Impostare i Parametri di Velocità di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetVelReducePara(Robot robot) {
        int rtn = 0;

        JointPos j1 = new JointPos(0, -90, 90, 0, 0, 0);
        JointPos j2 = new JointPos(90, -90, 90, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);

        rtn = robot.SetVelReducePara(0, 30, 1);
        System.out.printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(1, 30, 1);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        rtn = robot.SetVelReducePara(2, 30, 2);
        System.out.printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);

        rtn = robot.SetVelReducePara(2, 30, 0);
        System.out.printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(j1, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);
        robot.MoveJ(j2, 0, 0, 100, 100, 100.0, epos, -1.0, 0, offset_pos);

        robot.Sleep(1000);
        return 0;
    }

Esempio di Codice per l'Impostazione della Velocità di Sicurezza dei Giunti del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetJointVelReducePara(Robot robot) {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        JointPos j1 = new JointPos(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2 = new JointPos(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        double[] maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0};
        int rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        System.out.printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        double[] maxJointVelB = {20.0, 20.0, 20.0, 20.0, 20.0, 20.0};
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        System.out.printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(j1, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.MoveJ(j2, 1, 2, 100, 100, 100, epos, -1, 0, offset_pos);

        robot.Sleep(2000);
        return 0;
    }    