Impostazioni Sicurezza Robot
============================================

.. toctree:: 
    :maxdepth: 5

Impostare Livello Collisione
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Livello Collisione
    * @param  [in]  mode  0-livello, 1-percentuale
    * @param  [in]  level Soglia collisione, livello corrisponde range[], percentuale corrisponde range[0~1]
    * @param  [in]  config 0-non aggiornare file configurazione, 1-aggiornare file configurazione
    * @return   Codice errore
    */
    int SetAnticollision(int mode, double[] level, int config); 

Impostare Strategia Post-Collisione
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostare Strategia Post-Collisione
    * @param  [in] strategy  0-segnala errore e pausa; 1-continua esecuzione; 2-segnala errore e arresto; 3-modalità coppia gravità; 4-modalità risposta oscillazione; 5-modalità rimbalzo collisione
    * @param  [in] safeTime  Tempo arresto sicuro [1000 - 2000]ms
    * @param  [in] safeDistance  Distanza arresto sicuro [1-150]mm
    * @param  [in] safeVel  Velocità arresto sicuro TCP [50-250]mm/s
    * @param  [in] safetyMargin  Coefficiente sicurezza j1-j6 [1-10]
    * @return   Codice errore
    */
    int SetCollisionStrategy(int strategy, int safeTime, int safeDistance, int safeVel,int[] safetyMargin);

Inizio Funzione Soglia Rilevamento Collisione Personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inizio Funzione Soglia Rilevamento Collisione Personalizzata, impostare soglia rilevamento collisione lato articolare e TCP
    * @param  [in] flag 1-solo rilevamento articolare attivo; 2-solo rilevamento TCP attivo; 3-rilevamento articolare e TCP simultaneamente attivo
    * @param  [in] jointDetectionThreshould Soglia rilevamento collisione articolare j1-j6
    * @param  [in] tcpDetectionThreshould Soglia rilevamento collisione TCP, xyzabc
    * @param  [in] block 0-non bloccante; 1-bloccante
    * @return   Codice errore
    */
    int CustomCollisionDetectionStart(int flag, double[] jointDetectionThreshould, double[] tcpDetectionThreshould, int block);

Fine Funzione Soglia Rilevamento Collisione Personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fine Funzione Soglia Rilevamento Collisione Personalizzata
    * @return   Codice errore
    */
    int CustomCollisionDetectionEnd()

Esempio Codice Impostazione Livello Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button24_Click(object sender, EventArgs e)
    {
        int mode = 0;
        int config = 1;
        double[] level1 = { 1.0f, 2.0f, 3.0f, 4.0f, 5.0f, 6.0f };
        double[] level2 = { 50.0f, 20.0f, 30.0f, 40.0f, 50.0f, 60.0f };

        int rtn = robot.SetAnticollision(mode, level1, config);
        Console.WriteLine($"SetAnticollision mode 0 rtn is {rtn}");
        mode = 1;
        rtn = robot.SetAnticollision(mode, level2, config);
        Console.WriteLine($"SetAnticollision mode 1 rtn is {rtn}");

        JointPos p1Joint = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos p2Joint = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose p1Desc = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose p2Desc = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0.0f, 0.0f, 0.0f, 0.0f);
        DescPose offdese = new DescPose(0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, 2,  exaxisPos, 0, 0,  offdese);
        robot.ResetAllError();
        int[] safety = { 5, 5, 5, 5, 5, 5 };
        rtn = robot.SetCollisionStrategy(3, 1000, 150, 250, safety);
        Console.WriteLine($"SetCollisionStrategy rtn is {rtn}");

        double[] jointDetectionThreshould = { 0.1, 0.1, 0.1, 0.1, 0.1, 0.1 };
        double[] tcpDetectionThreshould = { 60, 60, 60, 60, 60, 60 };
        rtn = robot.CustomCollisionDetectionStart(3, jointDetectionThreshould, tcpDetectionThreshould, 0);
        Console.WriteLine($"CustomCollisionDetectionStart rtn is {rtn}");

        robot.MoveL( p1Joint,  p1Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        robot.MoveL( p2Joint,  p2Desc, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
        rtn = robot.CustomCollisionDetectionEnd();
        Console.WriteLine($"CustomCollisionDetectionEnd rtn is {rtn}");
    }

Impostare Limite Positivo
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostare Limite Positivo
    * @param  [in] limit Sei posizioni articolari, unità deg
    * @return   Codice errore
    */
    int SetLimitPositive(double[] limit); 

Impostare Limite Negativo
++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostare Limite Negativo
    * @param  [in] limit Sei posizioni articolari, unità deg
    * @return   Codice errore
    */
    int SetLimitNegative(double[] limit); 

Ottenere Angoli Limiti Software Articolari
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Angoli Limiti Software Articolari
    * @param  [in] flag 0-bloccante, 1-non bloccante	 
    * @param  [out] negative  Angoli limite negativo, unità deg
    * @param  [out] positive  Angoli limite positivo, unità deg
    * @return   Codice errore
    */
    int GetJointSoftLimitDeg(byte flag, ref double[] negative, ref double[] positive);

Esempio Codice Impostazione Limiti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] plimit = { 170.0f, 80.0f, 150.0f, 80.0f, 170.0f, 160.0f };
        robot.SetLimitPositive(plimit);
        double[] nlimit = { -170.0f, -260.0f, -150.0f, -260.0f, -170.0f, -160.0f };
        robot.SetLimitNegative(nlimit);

        double[] neg_deg = new double[6] {0,0,0,0,0,0 };
        double[] pos_deg = new double[6] { 0, 0, 0, 0, 0, 0 };
        robot.GetJointSoftLimitDeg(0, ref neg_deg,ref pos_deg);
        Console.WriteLine($"neg limit deg:{neg_deg[0]},{neg_deg[1]},{neg_deg[2]},{neg_deg[3]},{neg_deg[4]},{neg_deg[5]}");
        Console.WriteLine($"pos limit deg:{pos_deg[0]},{pos_deg[1]},{pos_deg[2]},{pos_deg[3]},{pos_deg[4]},{pos_deg[5]}");
    }

Impostare Metodo Rilevamento Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Metodo Rilevamento Collisione Robot
    * @param  [in] method Metodo rilevamento collisione: 0-modalità corrente; 1-doppio encoder; 2-corrente e doppio encoder simultaneamente attivi
    * @param [in] thresholdMode Modalità soglia livello collisione; 0-modalità soglia fissa livello collisione; 1-soglia rilevamento collisione personalizzata
    * @return   Codice errore
    */
    int SetCollisionDetectionMethod(int method,int thresholdMode=0);


Impostare Inizio/Arresto Rilevamento Collisione Statica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Inizio/Arresto Rilevamento Collisione Statica
    * @param  [in] status 0-arresto; 1-inizio
    * @return   Codice errore
    */
    int SetStaticCollisionOnOff(int status);

Esempio Codice Impostazione Metodo Rilevamento Collisione Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        int rtn = robot.SetCollisionDetectionMethod(0, 0);

        rtn = robot.SetStaticCollisionOnOff(1);
        Console.WriteLine($"SetStaticCollisionOnOff On rtn is {rtn}");
        Thread.Sleep(5000);
        rtn = robot.SetStaticCollisionOnOff(0);
        Console.WriteLine($"SetStaticCollisionOnOff Off rtn is {rtn}");
    }

Rilevamento Potenza Coppia Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Rilevamento Potenza Coppia Articolare
    * @param  [in] status 0-arresto; 1-inizio
    * @param  [in] power Impostare potenza massima(W)
    * @return   Codice errore
    */
    int SetPowerLimit(int status, double power);

Esempio Codice Rilevamento Potenza Coppia Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button26_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }