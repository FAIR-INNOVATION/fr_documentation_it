Interrogazione Stato Robot
=======================================

.. toctree:: 
    :maxdepth: 5

Ottenere Posizione Corrente Giunti (Gradi)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene posizione corrente giunti (gradi)
    * @param  [out] jPos Sei posizioni giunti ottenute, unità deg
    * @return  Codice errore
    */
    int GetActualJointPosDegree(JointPos jPos); 

Ottenere Velocità Feedback Giunti - deg/s
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene velocità feedback giunti - deg/s
    * @param [out] speed Sei velocità giunti
    * @return Codice errore 
    */
    int GetActualJointSpeedsDegree(Object[] speed);

Ottenere Accelerazione Feedback Giunti
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene accelerazione feedback giunti - deg/s^2
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] acc Sei accelerazioni giunti
    * @return  Codice errore
    */
    public int GetActualJointAccDegree(int flag, Object[] acc)

Ottenere Velocità Sintetica Istruzione TCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene velocità istruzione TCP
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] tcp_speed Velocità lineare
    * @param  [out] ori_speed Velocità orientamento
    * @return  Codice errore
    */
    public int GetTargetTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Ottenere Velocità Sintetica Feedback TCP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene velocità sintetica feedback TCP
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] tcp_speed Velocità lineare
    * @param  [out] ori_speed Velocità orientamento
    * @return  Codice errore
    */
    public int GetActualTCPCompositeSpeed(int flag, double tcp_speed, double ori_speed)

Ottenere Velocità Istruzione TCP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene velocità istruzione TCP
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] speed Velocità [x,y,z,rx,ry,rz]
    * @return  Codice errore
    */
    public int GetTargetTCPSpeed(int flag, Object[] speed)

Ottenere Velocità Feedback TCP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene velocità feedback TCP
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] speed Velocità [x,y,z,rx,ry,rz]
    * @return  Codice errore
    */
    public int GetActualTCPSpeed(int flag, Object[] speed)

Ottenere Posa Corrente Utensile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene posa corrente utensile
    * @param  [out] desc_pos  Posa utensile
    * @return  Codice errore
    */
    int GetActualTCPPose(DescPose desc_pos); 

Ottenere Numero Sistema Coordinate Utensile Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene numero sistema coordinate utensile corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema coordinate utensile
    * @return  Codice errore
    */
    int GetActualTCPNum(int flag, int[] id)

Ottenere Numero Sistema Coordinate Pezzo Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene numero sistema coordinate pezzo corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema coordinate pezzo
    * @return  Codice errore
    */
    public int GetActualWObjNum(int flag, int[] id)

Ottenere Posa Corrente Flangia Terminale
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene posa corrente flangia terminale
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] desc_pos  Posa flangia
    * @return  Codice errore
    */
    public int GetActualToolFlangePose(int flag, DescPose desc_pos)

Ottenere Coppia Corrente Giunti
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene coppia corrente giunti
    * @param  [in]  flag 0-bloccante, 1-non bloccante
    * @param  [out]  torques Coppia giunti
    * @return  Codice errore
    */
    int GetJointTorques(int flag, Object[] torques);

Ottenere Orario Sistema
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene orario sistema
    * @return  List[0]:int Codice errore; List[1]:double t_ms unità ms
    */
    List<Number> GetSystemClock();

Interrogare Completamento Movimento Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Interroga completamento movimento robot
    * @param   [out] state  0-non completato, 1-completato
    * @return  Codice errore
    */
    public int GetRobotMotionDone(int[] state)

Interrogare Lunghezza Buffer Coda Movimento Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Interroga lunghezza buffer coda movimento robot
    * @param   [out] len  Lunghezza buffer
    * @return  Codice errore
    */
    public int GetMotionQueueLength(int[] len)

Ottenere Stato Arresto Emergenza Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene stato arresto emergenza robot
    * @param [out] state Stato arresto emergenza, 0-nessun arresto emergenza, 1-arresto emergenza
    * @return Codice errore
    */
    public int GetRobotEmergencyStopState(int[] state)

Ottenere Stato Comunicazione SDK-Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene stato comunicazione SDK-robot
    * @return state Stato comunicazione, 0-comunicazione normale, 1-comunicazione anomala
    */
    public int GetSDKComState()

Ottenere Segnali Arresto Sicurezza
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene segnali arresto sicurezza
    * @param  [out] si0_state Segnale arresto sicurezza SI0, 0-invalido, 1-valido
    * @param  [out] si1_state Segnale arresto sicurezza SI1, 0-invalido, 1-valido
    * @return Codice errore
    */
    public int GetSafetyStopState(int[] si0_state, int[] si1_state)

Ottenere Temperatura Driver Giunti Robot (°C)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene temperatura driver giunti robot (°C)
    * @param  [out] temperature Temperatura
    * @return Codice errore
    */
    public int GetJointDriverTemperature(double[] temperature)

Ottenere Coppia Driver Giunti Robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene coppia driver giunti robot (Nm)
    * @param  [out] torque Coppia
    * @return Codice errore
    */
    public int GetJointDriverTorque(double[] torque)

Ottenere Struttura Stato Tempo Reale Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene struttura stato tempo reale robot
    * @return Struttura stato tempo reale
    */
    public ROBOT_STATE_PKG GetRobotRealTimeState()

Esempio Codice Interrogazione Stato Robot
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetStatus(Robot robot)
    {
        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("yangle:"+angle.get(1)+",zangle:"+angle.get(2));

        JointPos j_deg =new JointPos(){};
        robot.GetActualJointPosDegree( j_deg);

        Object[] jointSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetActualJointSpeedsDegree(jointSpeed);

        Object[] jointAcc = new Object[]{0,0,0,0,0,0 };
        robot.GetActualJointAccDegree(0, jointAcc);

        double tcp_speed = 0.0;
        double ori_speed = 0.0;
        robot.GetTargetTCPCompositeSpeed(0, tcp_speed, ori_speed);

        robot.GetActualTCPCompositeSpeed(0, tcp_speed, ori_speed);

        Object[] targetSpeed =new Object[] { 0,0,0,0,0,0 };
        robot.GetTargetTCPSpeed(0, targetSpeed);

        Object[] actualSpeed =new Object[] {0,0,0,0,0,0 };
        robot.GetActualTCPSpeed(0, actualSpeed);

        DescPose tcp = new DescPose(){};
        robot.GetActualTCPPose(tcp);

        DescPose flange = new DescPose(){};
        robot.GetActualToolFlangePose(0, flange);

        int[] id = {};
        robot.GetActualTCPNum(0, id);

        robot.GetActualWObjNum(0, id);

        List<Number> jtorque=new ArrayList<>();
        jtorque=robot.GetJointTorques(0);

        List<Number> t_ms = new ArrayList<>();
        t_ms=robot.GetSystemClock();

        List<Integer> config = new ArrayList<>();
        config=robot.GetRobotCurJointsConfig();

        int motionDone = 0;
        robot.GetRobotMotionDone(motionDone);

        int[] len ={0 };
        robot.GetMotionQueueLength(len);

        int[] emergState = {0};
        robot.GetRobotEmergencyStopState(emergState);

        int comstate = 0;
        comstate=robot.GetSDKComState();

        int[] si0_state=new int[]{0}, si1_state=new int[]{0};
        robot.GetSafetyStopState(si0_state, si1_state);

        double[] temp =new double[] { 0,0,0,0,0,0 };
        robot.GetJointDriverTemperature(temp);

        double[] torque = new double[]{ 0,0,0,0,0,0 };
        robot.GetJointDriverTorque(torque);

        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        pkg=robot.GetRobotRealTimeState();

        return 0;
    }

Calcolo Cinematica Inversa
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa
    * @param  [in] type 0-posa assoluta (sistema base), 1-posa incrementale (sistema base), 2-posa incrementale (sistema utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] config Configurazione spazio giunti, [-1]-riferimento posizione giunti corrente, [0~7]-risoluzione basata specifica configurazione spazio giunti
    * @param  [out] joint_pos Posizione giunti
    * @return  Codice errore
    */ 
    int GetInverseKin(int type, DescPose desc_pos, int config, JointPos joint_pos);

Calcolo Cinematica Inversa (Posizione Riferimento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa, risoluzione riferita a posizione giunti specificata
    * @param  [in] posMode 0 posa assoluta, 1 posa relativa - sistema base, 2 posa relativa - sistema utensile
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] joint_pos_ref Posizione giunti riferimento
    * @param  [out] joint_pos Posizione giunti
    * @return  Codice errore
    */   
    int GetInverseKinRef(int posMode, DescPose desc_pos, JointPos joint_pos_ref, JointPos joint_pos); 

Soluzione Cinematica Inversa, Spazio Cartesiano Include Posizione Asse Esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Soluzione cinematica inversa, spazio cartesiano include posizione asse esteso
    * @param  type 0-Posa assoluta (sistema coordinate base), 1-Posa incrementale (sistema coordinate base), 2-Posa incrementale (sistema coordinate utensile)
    * @param  desc_pos Posa cartesiana
    * @param  exaxis Posizione asse esteso
    * @param  tool Numero utensile
    * @param  workPiece Numero pezzo
    * @param  joint_pos Posizione giunto
    * @return Codice errore
    */
    public int GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos joint_pos)
    
Esempio Codice Soluzione Cinematica Inversa con Posizione Asse Esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void  TestInverseKinExaxis(Robot robot)
    {
        DescPose desc=new DescPose(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis=new ExaxisPos(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos =new JointPos();
        DescPose offsetPos =new DescPose();
        ROBOT_STATE_PKG pkg=robot.GetRobotRealTimeState();
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        System.out.printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.J1, jointPos.J2, jointPos.J3, jointPos.J4, jointPos.J5, jointPos.J6);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(jointPos, desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, exaxis, -1, 0, offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }

Ottenere Esistenza Soluzione Cinematica Inversa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa, determinare esistenza soluzione riferita a posizione giunti specificata
    * @param  [in] posMode 0 posa assoluta, 1 posa relativa - sistema base, 2 posa relativa - sistema utensile
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] joint_pos_ref Posizione giunti riferimento
    * @return  Codice errore  List[0]:Codice errore; List[1]: int hasResult 0-nessuna soluzione, 1-soluzione esistente
    */   
    List<Integer> GetInverseKinHasSolution(int posMode, DescPose desc_pos, JointPos joint_pos_ref);  

Calcolo Cinematica Diretta
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Calcolo cinematica diretta
    * @param  [in] joint_pos Posizione giunti
    * @param  [out] desc_pos Posa cartesiana
    * @return  Codice errore
    */
    int GetForwardKin(JointPos joint_pos, DescPose desc_pos); 

Esempio Codice Calcolo Cinematica Diretta/Inversa Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestInverseKin(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        JointPos inverseRtn = new JointPos(){};

        robot.GetInverseKin(0, desc_pos1, -1, inverseRtn);
        robot.GetInverseKinRef(0, desc_pos1, j1, inverseRtn);

        List<Integer> hasResut = new ArrayList<>();
        hasResut=robot.GetInverseKinHasSolution(0, desc_pos1, j1);

        DescPose forwordResult = new DescPose(){};
        robot.GetForwardKin(j1, forwordResult);

        return 0;
    }

Interrogare Dati Punti Gestione Insegnamento Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Interroga dati punti gestione insegnamento robot
    * @param [in]  name  Nome punto
    * @return  List[0]:Codice errore; List[1] - List[20] : Dati punto double[20]{x,y,z,rx,ry,rz,j1,j2,j3,j4,j5,j6,tool,wobj,speed,acc,e1,e2,e3,e4} 
    */ 
    List<Number> GetRobotTeachingPoint(String name); 

Ottenere Valori Compensazione Parametri DH Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene valori compensazione parametri DH robot
    * @param dhCompensation Valori compensazione parametri DH robot (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Codice errore
    */
    public int GetDHCompensation(Object[] dhCompensation)

Ottenere Codice SN Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene codice SN box controllo
    * @param [out] SNCode Codice SN box controllo
    * @return Codice errore
    */
    int GetRobotSN(String[] SNCode);

Esempio Codice Interrogazione Dati Punti Insegnamento Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetTeachPoint(Robot robot)
    {
        String name = "P1";
        List<Number> data=new ArrayList<>();
        data = robot.GetRobotTeachingPoint(name);
        System.out.println(name+" name is: "+data.get(0));
        for (int i = 0; i < 20; i++)
        {
            System.out.println("data is: "+ data.get(i+1));
        }

        int[] que_len = {0};
        int rtn = robot.GetMotionQueueLength(que_len);
        System.out.println("GetMotionQueueLength rtn is:"+rtn+", queue length is:"+ que_len[0]);

        Object[] dh = new Object[]{ 0,0,0,0,0,0 };
        int retval = 0;
        retval = robot.GetDHCompensation(dh);
        System.out.println("retval is: "+retval);

        String[] SN = new String[]{""};
        robot.GetRobotSN(SN);
        System.out.println("robot SN is "+SN[0]);
        return 0;
    }

Ottieni il Sistema di Coordinate dell'Utensile per ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'utensile per ID
    * @param [in] id Numero del sistema di coordinate dell'utensile
    * @param [out] coord Valori del sistema di coordinate
    * @param [out] type Tipo di utensile: 0-utensile; 1-sensore
    * @param [out] install Posizione di installazione: 0-estremità del robot; 1-esterna al robot
    * @param [out] toolID ID dell'utensile
    * @param [out] loadNo Numero di carico
    * @return Codice errore
    */
    int GetToolCoordWithID(int id, DescPose coord, int[] type, int[] install, int[] toolID, int[] loadNo)

Ottieni il Sistema di Coordinate del Pezzo per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate del pezzo per ID
    * @param [in] id Numero del sistema di coordinate del pezzo
    * @param [out] coord Valori del sistema di coordinate
    * @param [out] refFrame Sistema di coordinate di riferimento
    * @return Codice errore
    */
    public int GetWObjCoordWithID(int id, DescPose coord, int[] refFrame)

Ottieni il Sistema di Coordinate dell'Utensile Esterno per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'utensile esterno per ID
    * @param [in] id Numero del sistema di coordinate dell'utensile esterno, 20-39 corrispondono ai sistemi di coordinate degli utensili esterni 0-19
    * @param [out] coord Posizione TCP dell'utensile esterno fisso sul robot
    * @param [out] tcoord Posizione del sistema di coordinate del pezzo montato sull'estremità del robot
    * @return Codice errore
    */
    public int GetExToolCoordWithID(int id, DescPose coord, DescPose tcoord)

Ottieni il Sistema di Coordinate dell'Asse Esteso per ID
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-V3.9.8

.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'asse esteso per ID
    * @param [in] id Numero del sistema di coordinate dell'utensile esterno
    * @param [out] coord Valori del sistema di coordinate
    * @param [out] axisCoordNum Numero dell'asse esteso; bit0-bit3 corrispondono agli assi estesi 1-4; ad esempio, un valore axisCoordNum pari a 3 corrisponde agli assi estesi [1, 2]
    * @param [out] calibFlag Flag di calibrazione; 0-non calibrato; 1-calibrato
    * @return Codice errore
    */
    public int GetExAxisCoordWithID (int id, DescPose coord, int[] axisCoordNum, int[] calibFlag)

Ottenere Sistema Coordinate Utensile Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene sistema coordinate utensile corrente
     * @param [out] coord Valori sistema coordinate
     * @return Codice errore
     */
    public int GetCurToolCoord(DescPose coord)

Ottenere Sistema Coordinate Pezzo Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene sistema coordinate pezzo corrente
     * @param [out] coord Valori sistema coordinate
     * @return Codice errore
     */
    public int GetCurWObjCoord(DescPose coord)

Ottenere Sistema Coordinate Utensile Esterno Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene sistema coordinate utensile esterno corrente
     * @param  [out] coord Valori sistema coordinate
     * @return Codice errore
     */
    public int GetCurExToolCoord(DescPose coord)

Ottenere Sistema Coordinate Assi Estesi Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene sistema coordinate assi estesi corrente
     * @param [out] coord Valori sistema coordinate
     * @return Codice errore
     */
    public int GetCurExAxisCoord(DescPose coord)

Esempio Codice Sistemi Coordinate e Carico Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestCoord(Robot robot)
    {
        int id = 1;
        DescPose toolCoord = new DescPose();
        DescPose extoolCoord = new DescPose();
        DescPose exworkpieceCoord = new DescPose();
        DescPose wobjCoord = new DescPose();
        DescPose exAxisCoord = new DescPose();
        int[] type = new int[1];
        int[] install = new int[1];
        int[] toolID = new int[1];
        int[] loadNo = new int[1];
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        System.out.printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type[0], install[0], toolID[0], loadNo[0]);
        int[] refFrame = new int[1];
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        System.out.printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame[0]);


        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        System.out.printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);

        int[] axisCoordNum = new int[1];
        int[] calibFlag = new int[1];
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        System.out.printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum[0], calibFlag[0]);

        double[] weight = new double[1];
        DescTran cog = new DescTran();
        robot.GetTargetPayloadWithID(id, weight, cog);
        System.out.println("GetTargetPayload is " + weightT.get(0) + " cogT is  " + cogT.x + "  " + cogT.y + "  " + cogT.z);
        robot.GetCurToolCoord(toolCoord);
        System.out.printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        System.out.printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        System.out.printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        System.out.printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        DescTran cogT = new DescTran();
        List<Number> weightT = robot.GetTargetPayload(0);
        robot.GetTargetPayloadCog(0, cogT);
        System.out.printf("GetTargetPayload %f %f %f %f\n", weightT.get(0),
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet = new DescPose(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, cog);
        DescPose etcp = new DescPose(0, 0, 100, 0, 0, 0);
        DescPose etool = new DescPose(0, 0, 50, 0, 0, 0);
        int rtn = robot.SetExToolCoord(21, etcp, etool);
        System.out.printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        return 0;
    }