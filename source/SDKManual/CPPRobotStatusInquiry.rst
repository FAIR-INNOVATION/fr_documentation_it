Interrogazione Stato Robot
==========================

.. toctree:: 
    :maxdepth: 5

Ottenere Posizione Articolare Corrente (Angoli)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene la posizione articolare corrente (angoli)
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] jPos Posizioni delle sei articolazioni, unità deg
    * @return  Codice errore
    */
    errno_t  GetActualJointPosDegree(uint8_t flag, JointPos *jPos);

Ottenere Velocità di Feedback Articolare
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene velocità di feedback articolare - deg/s
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] speed Velocità delle sei articolazioni
     * @return  Codice errore 
     */ 
    errno_t  GetActualJointSpeedsDegree(uint8_t flag, float speed[6]);

Ottenere Accelerazione di Feedback Articolare
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene accelerazione di feedback articolare - deg/s^2
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] acc Accelerazione delle sei articolazioni
     * @return  Codice errore 
     */ 
    errno_t  GetActualJointAccDegree(uint8_t flag, float acc[6]);   

Ottenere Velocità Risultante Istruzionale TCP
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene velocità risultante istruzionale TCP
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] tcp_speed Velocità lineare
     * @param  [out] ori_speed Velocità di orientamento
     * @return  Codice errore 
     */
    errno_t  GetTargetTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Ottenere Velocità Risultante di Feedback TCP
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene velocità risultante di feedback TCP
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] tcp_speed Velocità lineare
     * @param  [out] ori_speed Velocità di orientamento
     * @return  Codice errore 
     */ 
    errno_t  GetActualTCPCompositeSpeed(uint8_t flag, float *tcp_speed, float *ori_speed);

Ottenere Velocità Istruzionale TCP
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene velocità istruzionale TCP
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] speed Velocità [x,y,z,rx,ry,rz]
     * @return  Codice errore 
     */ 
    errno_t  GetTargetTCPSpeed(uint8_t flag, float speed[6]);

Ottenere Velocità di Feedback TCP
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene velocità di feedback TCP
     * @param  [in] flag 0-bloccante, 1-non bloccante
     * @param  [out] speed Velocità [x,y,z,rx,ry,rz]
     * @return  Codice errore 
     */ 
    errno_t  GetActualTCPSpeed(uint8_t flag, float speed[6]);

Ottenere Posa Corrente Utensile
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene la posa corrente dell'utensile
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] desc_pos  Posa utensile
    * @return  Codice errore
    */
    errno_t  GetActualTCPPose(uint8_t flag, DescPose *desc_pos);

Ottenere Numero Sistema di Coordinate Utensile Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene il numero del sistema di coordinate utensile corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema di coordinate utensile
    * @return  Codice errore
    */
    errno_t  GetActualTCPNum(uint8_t flag, int *id);

Ottenere Numero Sistema di Coordinate Pezzo Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene il numero del sistema di coordinate pezzo corrente
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] id  Numero sistema di coordinate pezzo
    * @return  Codice errore
    */
    errno_t  GetActualWObjNum(uint8_t flag, int *id);  

Ottenere Posa Corrente Flangia Terminale
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene la posa corrente della flangia terminale
    * @param  [in] flag  0-bloccante, 1-non bloccante
    * @param  [out] desc_pos  Posa flangia
    * @return  Codice errore
    */
    errno_t  GetActualToolFlangePose(uint8_t flag, DescPose *desc_pos);  

Ottenere Coppia Corrente Articolare
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la coppia corrente articolare
    * @param  [in] flag 0-bloccante, 1-non bloccante
    * @param  [out] torques Coppia articolare
    * @return  Codice errore
    */
    errno_t  GetJointTorques(uint8_t flag, float torques[6]);

Ottenere Ora di Sistema
+++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene l'ora di sistema
    * @param  [out] t_ms Unità ms
    * @return  Codice errore
    */
    errno_t  GetSystemClock(float *t_ms);

Interrogare Se il Movimento del Robot è Completato
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Interroga se il movimento del robot è completato
    * @param  [out]  state  0-non completato, 1-completato
    * @return  Codice errore
    */   
    errno_t  GetRobotMotionDone(uint8_t *state);

Interrogare Lunghezza Buffer Coda Movimento Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Interroga la lunghezza del buffer della coda di movimento del robot
     * @param  [out]  len  Lunghezza buffer
     * @return  Codice errore
     */ 
    errno_t  GetMotionQueueLength(int *len);

Ottenere Stato Arresto di Emergenza Robot
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato di arresto di emergenza del robot
    * @param [out] state Stato arresto di emergenza, 0-nessun arresto di emergenza, 1-arresto di emergenza
    * @return Codice errore 
    */
    errno_t GetRobotEmergencyStopState(uint8_t *state);

Ottenere Stato Comunicazione tra SDK e Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato di comunicazione tra SDK e robot
    * @param [out] state Stato comunicazione, 0-comunicazione normale, 1-comunicazione anomala
    */
    errno_t GetSDKComState(int *state);

Ottenere Segnale Arresto di Sicurezza
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il segnale di arresto di sicurezza
    * @param [out] si0_state Segnale arresto sicurezza SI0, 0-non attivo, 1-attivo
    * @param [out] si1_state Segnale arresto sicurezza SI1, 0-non attivo, 1-attivo
    */
    errno_t GetSafetyStopState(uint8_t *si0_state, uint8_t *si1_state);

Ottenere Temperatura Azionamenti Articolari Robot (°C)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la temperatura degli azionamenti articolari del robot (°C)
    * @return Codice errore
    */
    errno_t GetJointDriverTemperature(double temperature[]);

Ottenere Coppia Azionamenti Articolari Robot (Nm)
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la coppia degli azionamenti articolari del robot (Nm)
    * @return Codice errore
    */
    errno_t GetJointDriverTorque(double torque[]);
        
Ottenere Struttura Stato in Tempo Reale Robot
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la struttura dello stato in tempo reale del robot
    * @param [out] pkg Struttura stato in tempo reale robot
    * @return Codice errore
    */
    errno_t GetRobotRealTimeState(ROBOT_STATE_PKG *pkg);

Esempio di Codice Interrogazione Stato Robot
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos: 

    int TestGetStatus(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      float yangle, zangle;
      robot.GetRobotInstallAngle(&yangle, &zangle);
      printf("yangle:%f,zangle:%f\n", yangle, zangle);
      JointPos j_deg = {};
      robot.GetActualJointPosDegree(0, &j_deg);
      printf("joint pos deg:%f,%f,%f,%f,%f,%f\n", j_deg.jPos[0], j_deg.jPos[1], j_deg.jPos[2], j_deg.jPos[3], j_deg.jPos[4], j_deg.jPos[5]);
      float jointSpeed[6] = { 0.0 };
      robot.GetActualJointSpeedsDegree(0, jointSpeed);
      printf("joint speeds deg:%f,%f,%f,%f,%f,%f\n", jointSpeed[0], jointSpeed[1], jointSpeed[2], jointSpeed[3], jointSpeed[4], jointSpeed[5]);
      float jointAcc[6] = { 0.0 };
      robot.GetActualJointAccDegree(0, jointAcc);
      printf("joint acc deg:%f,%f,%f,%f,%f,%f\n", jointAcc[0], jointAcc[1], jointAcc[2], jointAcc[3], jointAcc[4], jointAcc[5]);
      float tcp_speed = 0.0;
      float ori_speed = 0.0;
      robot.GetTargetTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetTargetTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      robot.GetActualTCPCompositeSpeed(0, &tcp_speed, &ori_speed);
      printf("GetActualTCPCompositeSpeed tcp %f; ori %f\n", tcp_speed, ori_speed);
      float targetSpeed[6] = { 0.0 };
      robot.GetTargetTCPSpeed(0, targetSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", targetSpeed[0], targetSpeed[1], targetSpeed[2], targetSpeed[3], targetSpeed[4], targetSpeed[5]);
      float actualSpeed[6] = { 0.0 };
      robot.GetActualTCPSpeed(0, actualSpeed);
      printf("GetTargetTCPSpeed %f,%f,%f,%f,%f,%f\n", actualSpeed[0], actualSpeed[1], actualSpeed[2], actualSpeed[3], actualSpeed[4], actualSpeed[5]);
      DescPose tcp = {};
      robot.GetActualTCPPose(0, &tcp);
      printf("tcp pose:%f,%f,%f,%f,%f,%f\n", tcp.tran.x, tcp.tran.y, tcp.tran.z, tcp.rpy.rx, tcp.rpy.ry, tcp.rpy.rz);
      DescPose flange = {};
      robot.GetActualToolFlangePose(0, &flange);
      printf("flange pose:%f,%f,%f,%f,%f,%f\n", flange.tran.x, flange.tran.y, flange.tran.z, flange.rpy.rx, flange.rpy.ry, flange.rpy.rz);
      int id = 0;
      robot.GetActualTCPNum(0, &id);
      printf("tcp num:%d\n", id);
      robot.GetActualWObjNum(0, &id);
      printf("wobj num:%d\n", id);
      float jtorque[6] = { 0.0 };
      robot.GetJointTorques(0, jtorque);
      printf("torques:%f,%f,%f,%f,%f,%f\n", jtorque[0], jtorque[1], jtorque[2], jtorque[3], jtorque[4], jtorque[5]);
      float t_ms = 0.0;
      robot.GetSystemClock(&t_ms);
      printf("system clock:%f\n", t_ms);
      int config = 0;
      robot.GetRobotCurJointsConfig(&config);
      printf("joint config:%d\n", config);
      uint8_t motionDone = 0;
      robot.GetRobotMotionDone(&motionDone);
      printf("GetRobotMotionDone :%d\n", motionDone);
      int len = 0;
      robot.GetMotionQueueLength(&len);
      printf("GetMotionQueueLength :%d\n", len);
      uint8_t emergState = 0;
      robot.GetRobotEmergencyStopState(&emergState);
      printf("GetRobotEmergencyStopState :%d\n", emergState);
      int comstate = 0;
      robot.GetSDKComState(&comstate);
      printf("GetSDKComState :%d\n", comstate);
      uint8_t si0_state, si1_state;
      robot.GetSafetyStopState(&si0_state, &si1_state);
      printf("GetSafetyStopState :%d %d\n", si0_state, si1_state);
      double temp[6] = { 0.0 };
      robot.GetJointDriverTemperature(temp);
      printf("Temperature:%f,%f,%f,%f,%f,%f\n", temp[0], temp[1], temp[2], temp[3], temp[4], temp[5]);
      double torque[6] = { 0.0 };
      robot.GetJointDriverTorque(torque);
      printf("torque:%f,%f,%f,%f,%f,%f\n", torque[0], torque[1], torque[2], torque[3], torque[4], torque[5]);
      robot.GetRobotRealTimeState(&pkg);
      robot.CloseRPC();
      return 0;
    }

Calcolo Cinematica Inversa
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa (Inverse Kinematics)
    * @param  [in] type 0-posa assoluta (sistema di coordinate base), 1-posa incrementale (sistema di coordinate base), 2-posa incrementale (sistema di coordinate utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] config Configurazione spazio articolare, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @param  [out] joint_pos Posizione articolare
    * @return  Codice errore
    */
    errno_t  GetInverseKin(int type, DescPose *desc_pos, int config, JointPos *joint_pos);

Calcolo Cinematica Inversa (Posizione di Riferimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa, risolve riferendosi a una specifica posizione articolare
    * @param  [in] type 0-posa assoluta (sistema di coordinate base), 1-posa incrementale (sistema di coordinate base), 2-posa incrementale (sistema di coordinate utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] joint_pos_ref Posizione articolare di riferimento
    * @param  [out] joint_pos Posizione articolare
    * @return  Codice errore
    */   
    errno_t  GetInverseKinRef(int type, DescPose *desc_pos, JointPos *joint_pos_ref, JointPos *joint_pos);

Soluzione di Cinematica Inversa, Spazio Cartesiano Inclusa Posizione dell'Asse Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Soluzione di cinematica inversa, spazio cartesiano inclusa posizione dell'asse esteso
    * @param [in] type 0-posa assoluta (sistema coordinate base), 1-posa incrementale (sistema coordinate base), 2-posa incrementale (sistema coordinate utensile)
    * @param [in] desc_pos Posa cartesiana
    * @param [in] exaxis Posizione asse esteso
    * @param [in] tool Numero utensile
    * @param [in] workPiece Numero pezzo
    * @param [out] joint_pos Posizione giunti
    * @param [in] config Configurazione dello spazio dei giunti, [-1] - risoluzione basata sulla posizione corrente dei giunti come riferimento, [0~7] - risoluzione in base a una configurazione specifica dello spazio dei giunti
    * @return Codice di errore
    */
    errno_t GetInverseKinExaxis(int type, DescPose desc_pos, ExaxisPos exaxis, int tool, int workPiece, JointPos& joint_pos, int config = -1);

Esempio di Codice per Soluzione di Cinematica Inversa Inclusa Posizione dell'Asse Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKinExaxis()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose desc(99.957, -0.002, 29.994, -176.569, -6.757, -167.462);
        ExaxisPos exaxis(100.0, 0.0, 0.0, 0.0);
        JointPos jointPos = {};
        DescPose offsetPos = {};
        robot.GetRobotRealTimeState(&pkg);
        int toolnum = pkg.tool;
        int workPcsNum = pkg.user;
        robot.GetInverseKinExaxis(0, desc, exaxis, toolnum, workPcsNum, jointPos);
        printf("GetInverseKinExaxis joint is %f, %f, %f, %f, %f, %f\n", jointPos.jPos[0], jointPos.jPos[1], jointPos.jPos[2], jointPos.jPos[3], jointPos.jPos[4], jointPos.jPos[5]);
        robot.ExtAxisMove(exaxis, 100, -1);
        robot.MoveJ(&jointPos, &desc, toolnum, workPcsNum, 100.0, 100.0, 100.0, &exaxis, -1, 0, &offsetPos);
        robot.CloseRPC();
        robot.Sleep(9999999);
        return 0;
    }

Verificare Se Esiste Soluzione per Cinematica Inversa
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcolo cinematica inversa, verifica se esiste soluzione riferendosi a una specifica posizione articolare
    * @param  [in] type 0-posa assoluta (sistema di coordinate base), 1-posa incrementale (sistema di coordinate base), 2-posa incrementale (sistema di coordinate utensile)
    * @param  [in] desc_pos Posa cartesiana
    * @param  [in] joint_pos_ref Posizione articolare di riferimento
    * @param  [out] result 0-nessuna soluzione, 1-esiste soluzione
    * @return  Codice errore
    */   
    errno_t  GetInverseKinHasSolution(int type, DescPose *desc_pos, JointPos *joint_pos_ref, uint8_t *result);

Calcolo Cinematica Diretta
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcolo cinematica diretta (Forward Kinematics)
    * @param  [in] joint_pos Posizione articolare
    * @param  [out] desc_pos Posa cartesiana
    * @return  Codice errore
    */
    errno_t  GetForwardKin(JointPos *joint_pos, DescPose *desc_pos);

Esempio di Codice Calcolo Cinematica Diretta e Inversa Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestInverseKin(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      JointPos inverseRtn = {};
      robot.GetInverseKin(0, &desc_pos1, -1, &inverseRtn);
      printf("dcs1 GetInverseKin rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      robot.GetInverseKinRef(0, &desc_pos1, &j1, &inverseRtn);
      printf("dcs1 GetInverseKinRef rtn is %f %f %f %f %f %f \n", inverseRtn.jPos[0], inverseRtn.jPos[1], inverseRtn.jPos[2], inverseRtn.jPos[3], inverseRtn.jPos[4], inverseRtn.jPos[5]);
      uint8_t hasResut = 0;
      robot.GetInverseKinHasSolution(0, &desc_pos1, &j1, &hasResut);
      printf("dcs1 GetInverseKinRef result %d\n", hasResut);
      DescPose forwordResult = {};
      robot.GetForwardKin(&j1, &forwordResult);
      printf("jpos1 forwordResult rtn is %f %f %f %f %f %f \n", forwordResult.tran.x, forwordResult.tran.y, forwordResult.tran.z, forwordResult.rpy.rx, forwordResult.rpy.ry, forwordResult.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Interrogare Dati Punti Gestione Insegnamento Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Interroga i dati dei punti della gestione insegnamento del robot
     * @param  [in]  name  Nome punto
     * @param  [out]  data  Dati punto
     * @return  Codice errore
     */ 
    errno_t  GetRobotTeachingPoint(char name[64], float data[20]);

Ottenere Valori di Compensazione Parametri DH Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i valori di compensazione dei parametri DH del robot
    * @param [out] dhCompensation Valori di compensazione parametri DH robot (mm) [cmpstD1,cmpstA2,cmpstA3,cmpstD4,cmpstD5,cmpstD6]
    * @return Codice errore
    */
    errno_t GetDHCompensation(double dhCompensation[6]);

Ottenere Codice SN Controllore
+++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il codice SN del controllore
    * @param [out] SNCode Codice SN controllore
    * @return Codice errore
    */
    errno_t GetRobotSN(std::string& SNCode);

Esempio di Codice Interrogazione Dati Punti Gestione Insegnamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestGetTeachPoint(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      char name[64] = "P1";
      float data[20] = { 0 };
      rtn = robot.GetRobotTeachingPoint(name, data);
      printf(" %d name is: %s \n", rtn, name);
      for (int i = 0; i < 20; i++)
      {
        printf("data is: %f \n", data[i]);
      }
      int que_len = 0;
      rtn = robot.GetMotionQueueLength(&que_len);
      printf("GetMotionQueueLength rtn is: %d, queue length is: %d \n", rtn, que_len);
      double dh[6] = { 0 };
      int retval = 0;
      retval = robot.GetDHCompensation(dh);
      cout << "retval is: " << retval << endl;
      cout << "dh is: " << dh[0] << " " << dh[1] << " " << dh[2] << " " << dh[3] << " " << dh[4] << " " << dh[5] << endl;
      string SN = "";
      robot.GetRobotSN(SN);
      cout << "robot SN is " << SN << endl;
      robot.CloseRPC();
      return 0;
    }

Ottieni il Sistema di Coordinate dell'Utensile per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
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
    errno_t GetToolCoordWithID(int id, DescPose& coord, int& type, int& install, int& toolID, int& loadNo);

Ottieni il Sistema di Coordinate del Pezzo per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate del pezzo per ID
    * @param [in] id Numero del sistema di coordinate del pezzo
    * @param [out] coord Valori del sistema di coordinate
    * @param [out] refFrame Sistema di coordinate di riferimento
    * @return Codice errore
    */
    errno_t GetWObjCoordWithID(int id, DescPose& coord, int& refFrame);
    
Ottieni il Sistema di Coordinate dell'Utensile Esterno per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'utensile esterno per ID
    * @param [in] id Numero del sistema di coordinate dell'utensile esterno, 20-39 corrispondono ai sistemi di coordinate degli utensili esterni 0-19
    * @param [out] coord Posizione TCP dell'utensile esterno fisso sul robot
    * @param [out] tcoord Posizione del sistema di coordinate del pezzo montato sull'estremità del robot
    * @return Codice errore
    */
    errno_t GetExToolCoordWithID(int id, DescPose& coord, DescPose& tcoord);
    
Ottieni il Sistema di Coordinate dell'Asse Esteso per ID
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v3.9.8
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'asse esteso per ID
    * @param [in] id Numero del sistema di coordinate dell'utensile esterno
    * @param [out] coord Valori del sistema di coordinate
    * @param [out] axisCoordNum Numero dell'asse esteso; bit0-bit3 corrispondono agli assi estesi 1-4; ad esempio, un valore axisCoordNum pari a 3 corrisponde agli assi estesi [1, 2]
    * @param [out] calibFlag Flag di calibrazione; 0-non calibrato; 1-calibrato
    * @return Codice errore
    */
    errno_t GetExAxisCoordWithID(int id, DescPose& coord, int& axisCoordNum, int& calibFlag);

Ottenere Massa e Centro di Gravità del Carico in Base al Numero
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene massa e centro di gravità del carico in base al numero
    * @param [in] id Numero carico
    * @param [out] weight Massa del carico
    * @param [out] cog Centro di gravità del carico
    * @return Codice errore
    */
    errno_t GetTargetPayloadWithID(int id, double& weight, DescTran& cog);
    
Ottenere Sistema di Coordinate Utensile Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Ottiene il sistema di coordinate utensile corrente
    * @param [out] coord Valori del sistema di coordinate
    * @return Codice errore
    */
    errno_t GetCurToolCoord(DescPose& coord);
        
Ottenere Sistema di Coordinate Pezzo Corrente
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate pezzo corrente
    * @param [out] coord Valori del sistema di coordinate
    * @return Codice errore
    */
    errno_t GetCurWObjCoord(DescPose& coord);
            
Ottenere Sistema di Coordinate Utensile Esterno Corrente
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate utensile esterno corrente
    * @param [out] coord Valori del sistema di coordinate
    * @return Codice errore
    */
    errno_t GetCurExToolCoord(DescPose& coord);
                
Ottenere Sistema di Coordinate Assi Estesi Corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate assi estesi corrente
    * @param [out] coord Valori del sistema di coordinate
    * @return Codice errore
    */
    errno_t GetCurExAxisCoord(DescPose& coord);

Esempio di Codice Ottenimento Sistemi di Coordinate e Carico Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestCoord()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        robot.Sleep(2000);
        int id = 1;
        DescPose toolCoord = {};
        DescPose extoolCoord = {};
        DescPose exworkpieceCoord = {};
        DescPose wobjCoord = {};
        DescPose exAxisCoord = {};
        int type = 0, install = 0, toolID = 0, loadNo = 0;
        robot.GetToolCoordWithID(id, toolCoord, type, install, toolID, loadNo);
        printf("GetToolCoordWithID %d, %f %f %f %f %f %f,  type = %d, install = %d, toolID = %d, loadNo = %d\n", id,
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz, type, install, toolID, loadNo);
        int refFrame = 0;
        robot.GetWObjCoordWithID(id, wobjCoord, refFrame);
        printf("GetWObjCoordWithID %d, %f %f %f %f %f %f, refFrame = %d\n", id,
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz, refFrame);
        robot.GetExToolCoordWithID(21, extoolCoord, exworkpieceCoord);
        printf("GetExToolCoordWithID %d, %f %f %f %f %f %f\n", id,
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz,
            exworkpieceCoord.tran.x, exworkpieceCoord.tran.y, exworkpieceCoord.tran.z,
            exworkpieceCoord.rpy.rx, exworkpieceCoord.rpy.ry, exworkpieceCoord.rpy.rz);
        int axisCoordNum = 0, calibFlag = 0;
        robot.GetExAxisCoordWithID(id, exAxisCoord, axisCoordNum, calibFlag);
        printf("GetExAxisCoordWithID %d, %f %f %f %f %f %f, axisCoordNum = %d, calibFlag = %d\n", id,
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz, axisCoordNum, calibFlag);
        double weight = 0.0;
        DescTran cog = {};
        robot.GetTargetPayloadWithID(id, weight, cog);
        printf("GetTargetPayloadWithID %d, %f %f %f %f\n", id, weight,
            cog.x, cog.y, cog.z);
        robot.GetCurToolCoord(toolCoord);
        printf("GetCurToolCoord %f %f %f %f %f %f\n",
            toolCoord.tran.x, toolCoord.tran.y, toolCoord.tran.z,
            toolCoord.rpy.rx, toolCoord.rpy.ry, toolCoord.rpy.rz);
        robot.GetCurWObjCoord(wobjCoord);
        printf("GetCurWObjCoord %f %f %f %f %f %f\n",
            wobjCoord.tran.x, wobjCoord.tran.y, wobjCoord.tran.z,
            wobjCoord.rpy.rx, wobjCoord.rpy.ry, wobjCoord.rpy.rz);
        robot.GetCurExToolCoord(extoolCoord);
        printf("GetExToolCoordWithID %f %f %f %f %f %f\n",
            extoolCoord.tran.x, extoolCoord.tran.y, extoolCoord.tran.z,
            extoolCoord.rpy.rx, extoolCoord.rpy.ry, extoolCoord.rpy.rz);
        robot.GetCurExAxisCoord(exAxisCoord);
        printf("GetCurExAxisCoord %f %f %f %f %f %f\n",
            exAxisCoord.tran.x, exAxisCoord.tran.y, exAxisCoord.tran.z,
            exAxisCoord.rpy.rx, exAxisCoord.rpy.ry, exAxisCoord.rpy.rz);
        float weightT = 0.0;
        DescTran cogT = {};
        robot.GetTargetPayload(0, &weightT);
        robot.GetTargetPayloadCog(0, &cogT);
        printf("GetTargetPayload %f %f %f %f\n", weightT,
            cogT.x, cogT.y, cogT.z);
        DescPose coordSet(0, 1, 2, 3, 4, 5);
        robot.SetToolCoord(1, &coordSet, 0, 0, 1, 0);
        robot.SetWObjCoord(1, &coordSet, 0);
        robot.SetLoadWeight(1, 1.3);
        //DescTran cog = {};
        cog.x = 10;
        cog.y = 20;
        cog.z = 30;
        robot.SetLoadCoord(1, &cog);
        DescPose etcp(0, 0, 100, 0, 0, 0);
        DescPose etool(0, 0, 50, 0, 0, 0);
        rtn = robot.SetExToolCoord(21, &etcp, &etool);
        printf("SetExToolCoord rtn is %d\n", rtn);
        robot.ExtAxisActiveECoordSys(1, 1, coordSet, 1);
        robot.CloseRPC();
        return 0;
    }