Configurazione Sicurezza Robot
==============================

.. toctree:: 
    :maxdepth: 5

Impostare Livello Rilevamento Collisioni
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il livello di rilevamento collisioni
    * @param  [in]  mode  0-livello, 1-percentuale
    * @param  [in]  level Soglia di collisione, intervallo per livello [], intervallo per percentuale [0~1]
    * @param  [in]  config 0-non aggiornare file di configurazione, 1-aggiorna file di configurazione
    * @return  Codice errore
    */
    errno_t  SetAnticollision(int mode, float level[6], int config);

Impostare Strategia dopo Collisione
++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
	 * @brief  Imposta la strategia dopo una collisione
	 * @param  [in] strategy  0-segnala errore e pausa; 1-continua esecuzione; 2-segnala errore e ferma; 3-modalità coppia gravità; 4-modalità risposta oscillazioni; 5-modalità rimbalzo da collisione 
	 * @param  [in] safeTime  Tempo di arresto sicuro [1000 - 2000] ms
	 * @param  [in] safeDistance  Distanza di arresto sicuro [1-150] mm
	 * @param  [in] safetyMargin  Fattori di sicurezza j1-j6 [1-10]
	 * @return  Codice errore
	 */
	errno_t SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safetyMargin[]);

Inizio Funzione Soglia Rilevamento Collisioni Personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

	 /**
	 * @brief  Inizia funzione soglia rilevamento collisioni personalizzata, imposta le soglie di rilevamento collisioni per lato articolare e TCP
	 * @param  [in] flag 1-attiva solo rilevamento articolare; 2-attiva solo rilevamento TCP; 3-attiva sia rilevamento articolare che TCP
	 * @param  [in] jointDetectionThreshould Soglia rilevamento collisioni articolari j1-j6
	 * @param  [in] tcpDetectionThreshould Soglia rilevamento collisioni TCP, xyzabc
	 * @param  [in] block 0-non bloccante; 1-bloccante
	 * @return  Codice errore
	 */
	errno_t CustomCollisionDetectionStart(int flag, double jointDetectionThreshould[6], double tcpDetectionThreshould[6], int block);

Fine Funzione Soglia Rilevamento Collisioni Personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
    :linenos:

	/**
	 * @brief  Disattiva funzione soglia rilevamento collisioni personalizzata
	 * @return  Codice errore
	 */
	errno_t CustomCollisionDetectionEnd();

Esempio di Codice Impostazione Livello Collisioni Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestCollision(void)
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
         int mode = 0;
         int config = 1;
         float level1[6] = { 1.0,2.0,3.0,4.0,5.0,6.0 };
         float level2[6] = { 50.0,20.0,30.0,40.0,50.0,60.0 };
         rtn = robot.SetAnticollision(mode, level1, config);
         printf("SetAnticollision mode 0 rtn is %d\n", rtn);
         mode = 1;
         rtn = robot.SetAnticollision(mode, level2, config);
         printf("SetAnticollision mode 1 rtn is %d\n", rtn);
         JointPos p1Joint(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos p2Joint(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0.0, 0.0, 0.0, 0.0);
         DescPose offdese(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, 2, &exaxisPos, 0, 0, &offdese);
         robot.ResetAllError();
         int safety[6] = { 5,5,5,5,5,5 };
         rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
         printf("SetCollisionStrategy rtn is %d\n", rtn);
         double jointDetectionThreshould[6] = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
         double tcpDetectionThreshould[6] = { 60,60,60,60,60,60 };
         rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
         cout << "CustomCollisionDetectionStart rtn is " << rtn << endl;
         robot.MoveL(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         robot.MoveL(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
         rtn = robot.CustomCollisionDetectionEnd();
         cout << "CustomCollisionDetectionEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Impostare Limiti Positivi (Soft Limit)
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta i limiti positivi (soft limit)
    * @param  [in] limit Posizioni delle sei articolazioni, unità deg
    * @return  Codice errore
    */
    errno_t  SetLimitPositive(float limit[6]);

Impostare Limiti Negativi (Soft Limit)
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta i limiti negativi (soft limit)
    * @param  [in] limit Posizioni delle sei articolazioni, unità deg
    * @return  Codice errore
    */
    errno_t  SetLimitNegative(float limit[6]);   

Ottenere Angoli Limiti Articolari Soft
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene gli angoli dei limiti articolari soft
    * @param  [in] flag 0-bloccante, 1-non bloccante    
    * @param  [out] negative  Angoli limite negativi, unità deg
    * @param  [out] positive  Angoli limite positivi, unità deg
    * @return  Codice errore
    */
    errno_t  GetJointSoftLimitDeg(uint8_t flag, float negative[6], float positive[6]);
    
Esempio di Codice Impostazione Limiti Robot
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLimit(void)
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
      float plimit[6] = { 170.0,80.0,150.0,80.0,170.0,160.0 };
      robot.SetLimitPositive(plimit);
      float nlimit[6] = { -170.0,-260.0,-150.0,-260.0,-170.0,-160.0 };
      robot.SetLimitNegative(nlimit);
      float neg_deg[6] = { 0.0 }, pos_deg[6] = { 0.0 };
      robot.GetJointSoftLimitDeg(0, neg_deg, pos_deg);
      printf("neg limit deg:%f,%f,%f,%f,%f,%f\n", neg_deg[0], neg_deg[1], neg_deg[2], neg_deg[3], neg_deg[4], neg_deg[5]);
      printf("pos limit deg:%f,%f,%f,%f,%f,%f\n", pos_deg[0], pos_deg[1], pos_deg[2], pos_deg[3], pos_deg[4], pos_deg[5]);
      robot.CloseRPC();
      return 0;
    }

Impostare Metodo Rilevamento Collisioni Robot
+++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il metodo di rilevamento collisioni del robot
    * @param [in] method Metodo di rilevamento collisioni: 0-modalità corrente; 1-doppio encoder; 2-attiva sia corrente che doppio encoder
    * @param [in] thresholdMode Modalità soglia livello collisioni; 0-modalità soglia fissa per livello collisioni; 1-soglia di rilevamento collisioni personalizzata
    * @return  Codice errore
    */
    errno_t SetCollisionDetectionMethod(int method, int thresholdMode = 0);

Impostare Attivazione/Disattivazione Rilevamento Collisioni in Stato Statico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Imposta attivazione/disattivazione rilevamento collisioni in stato statico
     * @param [in] status 0-disattiva; 1-attiva
     * @return Codice errore
     */
    errno_t SetStaticCollisionOnOff(int status);

Esempio di Codice Impostazione Metodo Rilevamento Collisioni Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestCollisionMethod(void)
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
      rtn = robot.SetCollisionDetectionMethod(0, 0);
      printf("SetCollisionDetectionMethod rtn is %d\n", rtn);
      rtn = robot.SetStaticCollisionOnOff(1);
      printf("SetStaticCollisionOnOff On rtn is %d\n", rtn);
      rtn = robot.Sleep(5000);
      rtn = robot.SetStaticCollisionOnOff(0);
      printf("SetStaticCollisionOnOff Off rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Rilevamento Potenza Coppia Articolare
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Rilevamento potenza coppia articolare
     * @param [in] status 0-disattiva; 1-attiva
     * @param [in] power Imposta potenza massima (W);
     * @return Codice errore
     */
    errno_t SetPowerLimit(int status, double power);

Esempio di Codice Rilevamento Potenza Coppia Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestPowerLimit(void)
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
       robot.DragTeachSwitch(1);
       robot.SetPowerLimit(1, 200);
       float torques[] = { 0, 0, 0, 0, 0, 0 };
       robot.GetJointTorques(1, torques);
       int count = 100;
       robot.ServoJTStart(); 
       int error = 0;
       while (count > 0)
       {
          error = robot.ServoJT(torques, 0.001);
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
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i parametri di velocità di sicurezza
    * @param [in] enable 0-disabilitato; 1-abilitato in modalità manuale; 2-abilitato in tutte le modalità
    * @param [in] maxTCPVel Limite massimo di velocità TCP; [0-1000] mm/s
    * @param [in] strategy Strategia post-superamento velocità; 0-stop e allarme; 1-limitazione automatica della velocità; 2-stop e allarme con disabilitazione
    * @param [in] maxJointVel Velocità massima per 6 giunti (°/s), default 45°/s
    * @return Codice errore
    */
    errno_t SetVelReducePara(int enable, double maxTCPVel, int strategy, std::vector<double> maxJointVel = {45.0, 45.0, 45.0, 45.0, 45.0, 45.0});
        
Esempio di Codice SDK per Impostare i Parametri di Velocità di Sicurezza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSetVelReducePara()
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
        JointPos j1(0, -90, 90, 0, 0, 0);
        JointPos j2(90, -90, 90, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(80);
        rtn = robot.SetVelReducePara(2, 30, 1);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        rtn = robot.SetVelReducePara(0, 30, 1);
        printf("SetVelReducePara disable reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(1, 30, 1);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        rtn = robot.SetVelReducePara(2, 30, 2);
        printf("SetVelReducePara disable robot rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.ResetAllError();
        robot.RobotEnable(1);
        robot.Sleep(1000);
        rtn = robot.SetVelReducePara(2, 30, 0);
        printf("SetVelReducePara report error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Esempio di Codice per l'Impostazione della Velocità di Sicurezza dei Giunti del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:    

    int TestSetJointVelReducePara()
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
        JointPos j1(10.220, -11.121, -118.086, -46.739, 82.036, 131.503);
        JointPos j2(89.782, -11.122, -118.086, -46.740, 82.036, 131.504);
        ExaxisPos epos(0, 0, 0, 0);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        robot.SetSpeed(20);

        std::vector<double> maxJointVelA = {100.0, 100.0, 100.0, 100.0, 100.0, 100.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelA);
        printf("SetVelReducePara param error rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        std::vector<double> maxJointVelB = { 20.0, 20.0, 20.0, 20.0, 20.0, 20.0 };
        rtn = robot.SetVelReducePara(2, 200, 0, maxJointVelB);
        printf("SetVelReducePara reduce vel rtn is %d\n", rtn);
        robot.MoveJ(&j1, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.MoveJ(&j2, 1, 2, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(2000);
        robot.CloseRPC();
        return 0;
    }    