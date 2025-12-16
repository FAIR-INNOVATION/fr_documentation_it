Query Stato Robot
========================

.. toctree:: 
    :maxdepth: 5

Ottenere Posizione Articolare Corrente (Gradi)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Posizione Articolare Corrente (Gradi)
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] jPos Sei posizioni articolari, unità deg
    * @return   Codice errore
    */
    int GetActualJointPosDegree(byte flag, ref JointPos jPos); 

Ottenere Posizione Articolare Corrente (Radianti)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Posizione Articolare Corrente (Radianti)
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] jPos Sei posizioni articolari, unità rad
    * @return   Codice errore
    */   
    int GetActualJointPosRadian(byte flag, ref JointPos jPos);

Ottenere Velocità Feedback Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Velocità Feedback Articolare-deg/s 
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] speed Sei velocità articolari 
    * @return Codice errore 
    */
    int GetActualJointSpeedsDegree(byte flag, ref double[] speed);

Ottenere Accelerazione Feedback Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Accelerazione Feedback Articolare-deg/s^2 
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] acc Sei accelerazioni articolari 
    * @return Codice errore 
    */
    int GetActualJointAccDegree(byte flag, ref double[] acc); 

Ottenere Velocità Comando TCP - Velocità Totale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Velocità Comando TCP - Velocità Totale 
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] tcp_speed Velocità lineare 
    * @param [out] ori_speed Velocità orientamento 
    * @return Codice errore 
    */
    int GetTargetTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed); 

Ottenere Velocità Feedback TCP - Velocità Totale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Ottenere Velocità Feedback TCP - Velocità Totale
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] tcp_speed Velocità lineare 
    * @param [out] ori_speed Velocità orientamento 
    * @return Codice errore 
    */
    int GetActualTCPCompositeSpeed(byte flag, ref double tcp_speed, ref double ori_speed);

Ottenere Velocità Comando TCP - Velocità Componenti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Velocità Comando TCP - Velocità Componenti
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] speed [x,y,z,rx,ry,rz] velocità 
    * @return Codice errore 
    */
    int GetTargetTCPSpeed(byte flag, ref double[] speed);

Ottenere Velocità Feedback TCP - Velocità Componenti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Velocità Feedback TCP - Velocità Componenti
    * @param [in] flag 0-bloccante, 1-non bloccante 
    * @param [out] speed [x,y,z,rx,ry,rz] velocità 
    * @return Codice errore 
    */
    int GetActualTCPSpeed(byte flag, ref double[] speed);

Ottenere Posa Utensile Corrente
+++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Posa Utensile Corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] desc_pos  Posa utensile
    * @return   Codice errore
    */
    int GetActualTCPPose(byte flag, ref DescPose desc_pos); 

Ottenere Numero Sistema Coordinate Utensile Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Numero Sistema Coordinate Utensile Corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema coordinate utensile
    * @return   Codice errore
    */
    int GetActualTCPNum(byte flag, ref int id);  

Ottenere Numero Sistema Coordinate Pezzo Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Numero Sistema Coordinate Pezzo Corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema coordinate pezzo
    * @return   Codice errore
    */
    int GetActualWObjNum(byte flag, ref int id);

Ottenere Posa Flangia Estremità Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Posa Flangia Estremità Corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] desc_pos  Posa flangia
    * @return   Codice errore
    */
    int GetActualToolFlangePose(byte flag, ref DescPose desc_pos);   

Ottenere Coppia Articolare Corrente
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Coppia Articolare Corrente
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] torques Coppia articolare
    * @return   Codice errore
    */
    int GetJointTorques(byte flag, float[] torques); 

Ottenere Ora Sistema
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Ora Sistema
    * @param  [out] t_ms Unità ms
    * @return   Codice errore
    */
    int GetSystemClock(ref double t_ms);

Verificare Se Movimento Robot Completato
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Verificare Se Movimento Robot Completato
    * @param  [out]  state  0-non completato, 1-completato
    * @return   Codice errore
    */   
    int GetRobotMotionDone(ref byte state);

Verificare Lunghezza Coda Cache Movimento Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Verificare Lunghezza Coda Cache Movimento Robot 
    * @param [out] len   Lunghezza cache
    * @return Codice errore 
    */
    int GetMotionQueueLength(ref int len);

Ottenere Stato Arresto Emergenza Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Stato Arresto Emergenza Robot
    * @param [out] state Stato arresto emergenza, 0-non arresto emergenza, 1-arresto emergenza
    * @return Codice errore  
    */
    int GetRobotEmergencyStopState(ref byte state);

Ottenere Stato Comunicazione SDK con Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Stato Comunicazione SDK con Robot
    * @param [out]  state Stato comunicazione, 0-comunicazione normale, 1-comunicazione anomala
    */
    int GetSDKComState(ref int state);

Ottenere Segnale Arresto Sicurezza
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Segnale Arresto Sicurezza
    * @param [out]  si0_state Segnale arresto sicurezza SI0, 0-non valido, 1-valido
    * @param [out]  si1_state Segnale arresto sicurezza SI1, 0-non valido, 1-valido
    */
    int GetSafetyStopState(ref byte si0_state, ref byte si1_state);

Ottenere Temperatura Azionamento Articolare Robot (℃)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Temperatura Azionamento Articolare Robot (℃)
    * @return Codice errore
    */
    int GetJointDriverTemperature(double[] temperature);

Ottenere Coppia Azionamento Articolare Robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Coppia Azionamento Articolare Robot (Nm)
    * @return Codice errore
    */
    int GetJointDriverTorque(double torque[]);

Ottenere Struttura Stato Tempo Reale Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Struttura Stato Tempo Reale Robot
    * @param [out] pkg Struttura stato tempo reale robot 
    * @return Codice errore 
    */
    int GetRobotRealTimeState(ref ROBOT_STATE_PKG pkg);

Esempio Codice Query Stato Robot
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button29_Click(object sender, EventArgs e)
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
        double yangle = 0, zangle = 0;
        robot.GetRobotInstallAngle(ref yangle, ref zangle);
        Console.WriteLine($"yangle:{yangle},zangle:{zangle}");

        JointPos j_deg = new JointPos(0,0,0,0,0,0);
        robot.GetActualJointPosDegree(0, ref j_deg);
        Console.WriteLine($"joint pos deg:{j_deg.jPos[0]},{j_deg.jPos[1]},{j_deg.jPos[2]},{j_deg.jPos[3]},{j_deg.jPos[4]},{j_deg.jPos[5]}");

        double[] jointSpeed = new double[6];
        robot.GetActualJointSpeedsDegree(0, ref jointSpeed);
        Console.WriteLine($"joint speeds deg:{jointSpeed[0]},{jointSpeed[1]},{jointSpeed[2]},{jointSpeed[3]},{jointSpeed[4]},{jointSpeed[5]}");

        double[] jointAcc = new double[6];
        robot.GetActualJointAccDegree(0, ref jointAcc);
        Console.WriteLine($"joint acc deg:{jointAcc[0]},{jointAcc[1]},{jointAcc[2]},{jointAcc[3]},{jointAcc[4]},{jointAcc[5]}");

        double tcp_speed = 0, ori_speed = 0;
        robot.GetTargetTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetTargetTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        robot.GetActualTCPCompositeSpeed(0, ref tcp_speed, ref ori_speed);
        Console.WriteLine($"GetActualTCPCompositeSpeed tcp {tcp_speed}; ori {ori_speed}");

        double[] targetSpeed = new double[6];
        robot.GetTargetTCPSpeed(0,ref targetSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {targetSpeed[0]},{targetSpeed[1]},{targetSpeed[2]},{targetSpeed[3]},{targetSpeed[4]},{targetSpeed[5]}");

        double[] actualSpeed = new double[6];
        robot.GetActualTCPSpeed(0, ref actualSpeed);
        Console.WriteLine($"GetTargetTCPSpeed {actualSpeed[0]},{actualSpeed[1]},{actualSpeed[2]},{actualSpeed[3]},{actualSpeed[4]},{actualSpeed[5]}");

        DescPose tcp = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualTCPPose(0, ref tcp);
        Console.WriteLine($"tcp pose:{tcp.tran.x},{tcp.tran.y},{tcp.tran.z},{tcp.rpy.rx},{tcp.rpy.ry},{tcp.rpy.rz}");

        DescPose flange = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetActualToolFlangePose(0, ref flange);
        Console.WriteLine($"flange pose:{flange.tran.x},{flange.tran.y},{flange.tran.z},{flange.rpy.rx},{flange.rpy.ry},{flange.rpy.rz}");

        int id = 0;
        robot.GetActualTCPNum(0, ref id);
        Console.WriteLine($"tcp num:{id}");

        robot.GetActualWObjNum(0, ref id);
        Console.WriteLine($"wobj num:{id}");

        double[] jtorque = new double[6];
        robot.GetJointTorques(0, jtorque);
        Console.WriteLine($"torques:{jtorque[0]},{jtorque[1]},{jtorque[2]},{jtorque[3]},{jtorque[4]},{jtorque[5]}");

        double t_ms = 0;
        robot.GetSystemClock(ref t_ms);
        Console.WriteLine($"system clock:{t_ms}");

        int config = 0;
        robot.GetRobotCurJointsConfig(ref config);
        Console.WriteLine($"joint config:{config}");

        byte motionDone = 0;
        robot.GetRobotMotionDone(ref motionDone);
        Console.WriteLine($"GetRobotMotionDone :{motionDone}");

        int len = 0;
        robot.GetMotionQueueLength(ref len);
        Console.WriteLine($"GetMotionQueueLength :{len}");

        byte emergState = 0;
        robot.GetRobotEmergencyStopState(ref emergState);
        Console.WriteLine($"GetRobotEmergencyStopState :{emergState}");

        int comstate = 0;
        robot.GetSDKComState(ref comstate);
        Console.WriteLine($"GetSDKComState :{comstate}");

        byte si0_state = 0, si1_state = 0;
        robot.GetSafetyStopState(ref si0_state, ref si1_state);
        Console.WriteLine($"GetSafetyStopState :{si0_state} {si1_state}");

        double[] temp = new double[6];
        robot.GetJointDriverTemperature(temp);
        Console.WriteLine($"Temperature:{temp[0]},{temp[1]},{temp[2]},{temp[3]},{temp[4]},{temp[5]}");

        double[] torque = new double[6];
        robot.GetJointDriverTorque(torque);
        Console.WriteLine($"torque:{torque[0]},{torque[1]},{torque[2]},{torque[3]},{torque[4]},{torque[5]}");

        robot.GetRobotRealTimeState(ref pkg);
    }

Calcolo Cinematica Inversa
+++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcolo Cinematica Inversa
    * @param  [in] type 0-posa assoluta (sistema base), 1-posa incrementale (sistema base), 2-posa incrementale (sistema utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] config Configurazione spazio articolare, [-1]-calcolo riferimento posizione articolare corrente, [0~7]-soluzione basata configurazione spazio articolare specifica
    * @param  [out] joint_pos Posizione articolare
    * @return   Codice errore
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, ref JointPos joint_pos);

Calcolo Cinematica Inversa (Riferimento Posizione)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcolo Cinematica Inversa, riferimento posizione articolare specificata per verificare se soluzione esiste
    * @param  [in] type 0-posa assoluta (sistema base), 1-posa incrementale (sistema base), 2-posa incrementale (sistema utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] joint_pos_ref Posizione articolare riferimento
    * @param  [out] result 0-nessuna soluzione, 1-soluzione esistente
    * @return   Codice errore
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref JointPos joint_pos); 

Verificare Se Esiste Soluzione Cinematica Inversa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolo Cinematica Inversa, verificare se esiste soluzione per posizione articolare riferimento specificata
    * @param [in] posMode 0 posa assoluta, 1 posa relativa-sistema base, 2 posa relativa-sistema utensile 
    * @param [in] desc_pos Posa cartesiana 
    * @param [in] joint_pos_ref Posizione articolare riferimento 
    * @param [out] hasResult 0-nessuna soluzione, 1-soluzione esistente 
    * @return Codice errore 
    */ 
    int GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref, ref bool hasResult);  

Calcolo Cinematica Diretta
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcolo Cinematica Diretta
    * @param  [in] joint_pos Posizione articolare
    * @param  [out] desc_pos Posa cartesiana
    * @return   Codice errore
    */
    int GetForwardKin(JointPos joint_pos, ref DescPose desc_pos); 

Esempio Codice Calcolo Cinematica Diretta/Inversa Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button30_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);

        JointPos inverseRtn = new JointPos(0, 0, 0, 0, 0, 0);

        robot.GetInverseKin(0, desc_pos1, -1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKin rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");
        robot.GetInverseKinRef(0,  desc_pos1, j1, ref inverseRtn);
        Console.WriteLine($"dcs1 GetInverseKinRef rtn is {inverseRtn.jPos[0]} {inverseRtn.jPos[1]} {inverseRtn.jPos[2]} {inverseRtn.jPos[3]} {inverseRtn.jPos[4]} {inverseRtn.jPos[5]}");

        bool hasResut = false;
        robot.GetInverseKinHasSolution(0,  desc_pos1,  j1, ref hasResut);
        Console.WriteLine($"dcs1 GetInverseKinRef result {hasResut}");

        DescPose forwordResult = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetForwardKin(j1, ref forwordResult);
        Console.WriteLine($"jpos1 forwordResult rtn is {forwordResult.tran.x} {forwordResult.tran.y} {forwordResult.tran.z} {forwordResult.rpy.rx} {forwordResult.rpy.ry} {forwordResult.rpy.rz}");
    }

Verificare Dati Punti Gestione Insegnamento Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Verificare Dati Punti Gestione Insegnamento Robot 
    * @param [in] name    Nome punto
    * @param [out] data   Dati punto double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool, wobj,speed,acc,e1,e2,e3,e4}
    * @return Codice errore 
    */ 
    int GetRobotTeachingPoint(string name, ref double[] data); 

Ottenere Valori Compensazione Parametri DH Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Valori Compensazione Parametri DH Robot 
    * @param [out] dhCompensation Valori compensazione parametri DH robot(mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Codice errore 
    */
    int GetDHCompensation(ref double[] dhCompensation);


Ottenere Codice SN Quadro Controllo
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Codice SN Quadro Controllo
    * @param [out] SNCode Codice SN quadro controllo
    * @return Codice errore
    */
    int GetRobotSN(ref string SNCode);

Esempio Codice Verifica Dati Punti Gestione Insegnamento Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button31_Click(object sender, EventArgs e)
    {
        string name = "A0";
        double[] data = new double[20];
        int rtn = robot.GetRobotTeachingPoint(name, ref data);
        Console.WriteLine(" {0} name is: {1} \n", rtn, name);
        for (int i = 0; i < 20; i++)
        {
            Console.WriteLine("data is: {0} \n", data[i]);
        }

        int que_len = 0;
        rtn = robot.GetMotionQueueLength(ref que_len);
        Console.WriteLine("GetMotionQueueLength rtn is: {0}, queue length is: {1} \n", rtn, que_len);

        double[] dh = { 0, 0, 0, 0, 0, 0 };
        int retval = 0;
        retval = robot.GetDHCompensation(ref dh);
        Console.WriteLine($"retval is  {retval}");
        Console.WriteLine($"dh is {dh[0]}, {dh[1]}, {dh[2]}, {dh[3]}, {dh[4]}, {dh[5]}");
        string SN = "";
        robot.GetRobotSN(ref SN);
        Console.WriteLine($"robot SN is  {SN}");
    }

Ottenere Sistema Coordinate Utensile in Base al Numero
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Sistema Coordinate Utensile in Base al Numero
    * @param [in] id Numero sistema coordinate utensile
    * @param [out] coord Valori coefficienti coordinate
    * @return Codice errore
    */
    int GetToolCoordWithID(int id,ref DescPose coord)

Ottenere Sistema Coordinate Pezzo in Base al Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Sistema Coordinate Pezzo in Base al Numero
    * @param [in]  id Numero sistema coordinate pezzo
    * @param [out] coord Valori coefficienti coordinate
    * @return Codice errore
    */
    public int GetWObjCoordWithID(int id, ref DescPose coord)

Ottenere Sistema Coordinate Utensile Esterno in Base al Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Sistema Coordinate Utensile Esterno in Base al Numero
    * @param [in]  id Numero sistema coordinate utensile esterno
    * @param [out] coord Valori coefficienti coordinate
    * @return Codice errore
    */
    public int GetExToolCoordWithID(int id, ref DescPose coord)

Ottenere Sistema Coordinate Asse Esteso in Base al Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Sistema Coordinate Asse Esteso in Base al Numero
    * @param [in]  id Numero sistema coordinate utensile esterno
    * @param [out] coord Valori coefficienti coordinate
    * @return Codice errore
    */
    public int GetExAxisCoordWithID(int id, ref DescPose coord)

Ottenere Sistema Coordinate Utensile Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ottenere Sistema Coordinate Utensile Corrente
     * @param [out] coord Valori coefficienti coordinate
     * @return Codice errore
     */
    public int GetCurToolCoord(ref DescPose coord)

Ottenere Sistema Coordinate Pezzo Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ottenere Sistema Coordinate Pezzo Corrente
     * @param [out] coord Valori coefficienti coordinate
     * @return Codice errore
     */
    public int GetCurWObjCoord(ref DescPose coord)

Ottenere Sistema Coordinate Utensile Esterno Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ottenere Sistema Coordinate Utensile Esterno Corrente
     * @param  [out] coord Valori coefficienti coordinate
     * @return Codice errore
     */
    public int GetCurExToolCoord(ref DescPose coord)

Ottenere Sistema Coordinate Asse Esteso Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ottenere Sistema Coordinate Asse Esteso Corrente
     * @param [out] coord Valori coefficienti coordinate
     * @return Codice errore
     */
    public int GetCurExAxisCoord(ref DescPose coord)

Esempio Codice Ottenimento Sistemi Coordinate e Carico Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestCoordMain()
    {  
        DescPose t_coord = new DescPose(0, 0, 0, 0, 0, 0);
        t_coord.tran.x = 1.0;
        t_coord.tran.y = 2.0;
        t_coord.tran.z = 300.0;
        t_coord.rpy.rx = 4.0;
        t_coord.rpy.ry = 5.0;
        t_coord.rpy.rz = 6.0;
        int id = 1;
        DescPose toolCoord = new DescPose();
        robot.GetToolCoordWithID(id, ref toolCoord);
        Console.WriteLine($"GetToolCoordWithID {id}, {toolCoord.tran.x} {toolCoord.tran.y} {toolCoord.tran.z} {toolCoord.rpy.rx} {toolCoord.rpy.ry} {toolCoord.rpy.rz}");
        DescPose wobjCoord = new DescPose();
        robot.GetWObjCoordWithID(id, ref wobjCoord);
        Console.WriteLine($"GetWObjCoordWithID {id}, {wobjCoord.tran.x} {wobjCoord.tran.y} {wobjCoord.tran.z} {wobjCoord.rpy.rx} {wobjCoord.rpy.ry} {wobjCoord.rpy.rz}");
        DescPose extoolCoord = new DescPose();
        robot.GetExToolCoordWithID(id, ref extoolCoord);
        Console.WriteLine($"GetExToolCoordWithID {id}, {extoolCoord.tran.x} {extoolCoord.tran.y} {extoolCoord.tran.z} {extoolCoord.rpy.rx} {extoolCoord.rpy.ry} {extoolCoord.rpy.rz}");
        DescPose exAxisCoord = new DescPose();
        robot.GetExAxisCoordWithID(id, ref exAxisCoord);
        Console.WriteLine($"GetExAxisCoordWithID {id}, {exAxisCoord.tran.x} {exAxisCoord.tran.y} {exAxisCoord.tran.z} {exAxisCoord.rpy.rx} {exAxisCoord.rpy.ry} {exAxisCoord.rpy.rz}");
        double weight = 0.0;
        DescTran cog = new DescTran();
        robot.GetTargetPayloadWithID(id, ref weight, ref cog);
        Console.WriteLine($"GetTargetPayloadWithID {id}, {weight} {cog.x} {cog.y} {cog.z}");
        robot.GetCurToolCoord(ref toolCoord);
        Console.WriteLine($"GetCurToolCoord {toolCoord.tran.x} {toolCoord.tran.y} {toolCoord.tran.z} {toolCoord.rpy.rx} {toolCoord.rpy.ry} {toolCoord.rpy.rz}");

        robot.GetCurWObjCoord(ref wobjCoord);
        Console.WriteLine($"GetCurWObjCoord {wobjCoord.tran.x} {wobjCoord.tran.y} {wobjCoord.tran.z} {wobjCoord.rpy.rx} {wobjCoord.rpy.ry} {wobjCoord.rpy.rz}");
        robot.GetCurExToolCoord(ref extoolCoord);
        Console.WriteLine($"GetExToolCoordWithID {extoolCoord.tran.x} {extoolCoord.tran.y} {extoolCoord.tran.z} {extoolCoord.rpy.rx} {extoolCoord.rpy.ry} {extoolCoord.rpy.rz}");
        robot.GetCurExAxisCoord(ref exAxisCoord);
        Console.WriteLine($"GetCurExAxisCoord {exAxisCoord.tran.x} {exAxisCoord.tran.y} {exAxisCoord.tran.z} {exAxisCoord.rpy.rx} {exAxisCoord.rpy.ry} {exAxisCoord.rpy.rz}");
        double weightT = 0.0f;
        DescTran cogT = new DescTran();
        robot.GetTargetPayload(0, ref weightT);
        robot.GetTargetPayloadCog(0, ref cogT);
        Console.WriteLine($"GetTargetPayload {weightT} {cogT.x} {cogT.y} {cogT.z}");
        DescPose coordSet = new DescPose(0, 10, 2, 3, 4, 5);
        robot.SetToolCoord(2, coordSet, 0, 0, 1, 0);
        DescPose Coordset0 = new DescPose(0, 0, 0, 0, 0, 0);
        DescPose Coordset = new DescPose(1, 2, 3, 4, 5, 6);
        DescPose etcp = new DescPose(10, 20, 30, 40, 50, 60);
        DescPose etctool = new DescPose(0.1, 0.2, 0.3, 0.4, 0.5, 0.6);
        robot.SetToolCoord(id, Coordset, 0, 0, 1, 0);
        Thread.Sleep(100);
        robot.SetWObjCoord(id, Coordset, 0);
        Thread.Sleep(100);
        robot.ExtAxisActiveECoordSys(id, 1, Coordset, 0);
        Thread.Sleep(100);
        robot.SetExToolCoord(id, etcp, etctool);
        Thread.Sleep(100);
        robot.SetLoadWeight(id, (float)1.5);
        //Thread.Sleep(500);
        robot.SetLoadCoord(id, cog);
        Thread.Sleep(100);
    }