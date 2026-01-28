Controllo di forza del robot
=======================================

.. toctree::
    :maxdepth: 5

Configurazione sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Configura sensore di forza
    * @param  [in] company  Produttore sensore di forza, 17-Kunwei Technology
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, default 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, default 0
    * @param  [in] bus  Posizione bus terminale dove è collegato il dispositivo, attualmente non utilizzato, default 0
    * @return  Codice di errore
    */
    int FT_SetConfig(int company, int device, int softvesion, int bus);

Ottieni la configurazione del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni la configurazione del sensore di forza
    * @param [out] deviceID Numero sensore di forza
    * @param [out] company Produttore sensore di forza, 17-Kunwei Technology, 19-CASC 11th Academy, 20-Sensore ATI, 21-Zhongke Midian, 22-Weihang Minxin
    * @param [out] device  Numero dispositivo, Kunwei(0-KWR75B), CASC 11th Academy(0-MCS6A-200-4), ATI (0-AXIA80 -M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A)
    * @param [out] softvesion Numero versione software, attualmente non utilizzato, default 0
    * @return Codice di errore
    */
    int FT_GetConfig(ref int deviceID, ref int company, ref int device, ref int softvesion);

Attivazione sensore di forza
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Attivazione sensore di forza
    * @param  [in] act  0-Ripristina, 1-Attiva
    * @return  Codice di errore
    */
    int FT_Activate(byte act);

Azzeramento sensore di forza
+++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Azzeramento sensore di forza
    * @param  [in] act  0-Rimuovi offset zero, 1-Correggi offset zero
    * @return  Codice di errore
    */
    int FT_SetZero(byte act);

Imposta il sistema di coordinate di riferimento del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta il sistema di coordinate di riferimento del sensore di forza
    * @param  [in] ref  0-Sistema di coordinate utensile, 1-Sistema di coordinate base
    * @return  Codice di errore
    */
    int FT_SetRCS(byte type);

Imposta il peso del carico sotto il sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta il peso del carico sotto il sensore di forza
    * @param  [in] weight Peso del carico kg
    * @return  Codice di errore
    */
    int SetForceSensorPayLoad(double weight);

Imposta il centro di massa del carico sotto il sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta il centro di massa del carico sotto il sensore di forza
    * @param  [in] x Centro di massa carico x mm
    * @param  [in] y Centro di massa carico y mm
    * @param  [in] z Centro di massa carico z mm
    * @return  Codice di errore
    */
    int SetForceSensorPayLoadCog(double x, double y, double z);

Ottieni il peso del carico sotto il sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni il peso del carico sotto il sensore di forza
    * @param  [in] weight Peso del carico kg
    * @return  Codice di errore
    */
    int GetForceSensorPayLoad(ref double weight);

Ottieni il centro di massa del carico sotto il sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni il centro di massa del carico sotto il sensore di forza
    * @param  [out] x Centro di massa carico x mm
    * @param  [out] y Centro di massa carico y mm
    * @param  [out] z Centro di massa carico z mm
    * @return  Codice di errore
    */
    int GetForceSensorPayLoadCog(ref double x, ref double y, ref double z);

Azzeramento automatico sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Azzeramento automatico sensore di forza
    * @param  [out] weight Massa sensore kg
    * @param  [out] pos Centro di massa sensore mm
    * @return  Codice di errore
    */
    int ForceSensorAutoComputeLoad(ref double weight, ref DescTran pos);

Ottieni i dati forza/coppia nel sistema di coordinate di riferimento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni i dati forza/coppia nel sistema di coordinate di riferimento
    * @param  [out] ft  Forza/Coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice di errore
    */
    int FT_GetForceTorqueRCS(byte flag, ref ForceTorque ft);

Ottieni i dati forza/coppia originali del sensore di forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni i dati forza/coppia originali del sensore di forza
    * @param  [out] ft  Forza/Coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice di errore
    */
    int FT_GetForceTorqueOrigin(byte flag, ref ForceTorque ft);

Esempio di codice per la configurazione e l'azzeramento automatico del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button54_Click(object sender, EventArgs e)
    {
        int company = 24;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        int index = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0, 0, 0, 0, 0, 0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin:{ft.fx},{ft.fy},{ft.fz},{ft.tx},{ft.ty},{ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose ftCoord = new DescPose(0, 0, 0, 0, 0, 0);
        robot.FT_SetRCS(0, ftCoord);

        robot.SetForceSensorPayLoad(0.824);
        robot.SetForceSensorPayLoadCog(0.778, 2.554, 48.765);
        double weight = 0;
        double x = 0, y = 0, z = 0;
        robot.GetForceSensorPayLoad(ref weight);
        robot.GetForceSensorPayLoadCog(ref x, ref y, ref z);
        Console.WriteLine($"the FT load is {weight}, {x} {y} {z}");

        robot.SetForceSensorPayLoad(0);
        robot.SetForceSensorPayLoadCog(0, 0, 0);

        double computeWeight = 0;
        DescTran tran = new DescTran(0, 0, 0);
        robot.ForceSensorAutoComputeLoad(ref weight, ref tran);
        Console.WriteLine($"the result is weight {weight} pos is {tran.x} {tran.y} {tran.z}");

    }

Registra identificazione peso carico
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Registra identificazione peso carico
    * @param  [in] id  Numero sistema di coordinate sensore, intervallo[1~14]
    * @return  Codice di errore
    */
    int FT_PdIdenRecord(int id);

Calcola identificazione peso carico
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcola identificazione peso carico
    * @param  [out] weight  Peso carico, unità kg
    * @return  Codice di errore
    */
    int FT_PdIdenCompute(ref double weight);

Registra identificazione centro di massa carico
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Registra identificazione centro di massa carico
    * @param  [in] id  Numero sistema di coordinate sensore, intervallo[1~14]
    * @param  [in] index Numero punto, intervallo[1~3]
    * @return  Codice di errore
    */
    int FT_PdCogIdenRecord(int id, int index);

Calcola identificazione centro di massa carico
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcola identificazione centro di massa carico
    * @param  [out] cog  Centro di massa carico, unità mm
    * @return  Codice di errore
    */
    int FT_PdCogIdenCompute(ref DescTran cog);

Esempio di codice per l'identificazione del carico del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTPdCog_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        ForceTorque ft = new ForceTorque(0,0,0,0,0,0);
        robot.FT_GetForceTorqueOrigin(0, ref ft);
        Console.WriteLine($"ft origin: {ft.fx}, {ft.fy}, {ft.fz}, {ft.tx}, {ft.ty}, {ft.tz}");
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        DescPose tcoord = new DescPose(0, 0, 35.0, 0, 0, 0);
        robot.SetToolCoord(10, tcoord, 1, 0, 0, 0);

        robot.FT_PdIdenRecord(10);
        Thread.Sleep(1000);

        double weight = 0.0f;
        robot.FT_PdIdenCompute(ref weight);
        Console.WriteLine($"payload weight: {weight}");

        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 2);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        Thread.Sleep(1000);
        robot.FT_PdCogIdenRecord(10, 3);

        DescTran cog = new DescTran(0,0,0);
        robot.FT_PdCogIdenCompute(ref cog);
        Console.WriteLine($"cog: {cog.x}, {cog.y}, {cog.z}");
    }

Guardia collisione
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Guardia collisione
    * @param  [in] flag 0-Disabilita guardia collisione, 1-Abilità guardia collisione
    * @param  [in] sensor_id Numero sensore di forza
    * @param  [in] select  Seleziona quali sei gradi di libertà controllare per collisione, 0-Non controllare, 1-Controlla
    * @param  [in] ft  Forza/coppia collisione, fx,fy,fz,tx,ty,tz
    * @param  [in] max_threshold Soglia massima
    * @param  [in] min_threshold Soglia minima
    * @note   Intervallo di rilevamento forza/coppia: (ft-min_threshold, ft+max_threshold)
    * @return  Codice di errore
    */
    int FT_Guard(int flag, int sensor_id, int[] select, ForceTorque ft, double[] max_threshold, double[] min_threshold);

Esempio di codice per la guardia collisione
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnFTGuard_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;

        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte sensor_id = 1;
        int[] select = { 1, 1, 1, 1, 1, 1 };
        double[] max_threshold = { 10.0f, 10.0f, 10.0f, 10.0f, 10.0f, 10.0f };
        double[] min_threshold = { 5.0f, 5.0f, 5.0f, 5.0f, 5.0f, 5.0f };

        ForceTorque ft = new ForceTorque();
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_p3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);

        robot.FT_Guard(1, sensor_id, select,  ft, max_threshold, min_threshold);
        robot.MoveCart( desc_p1, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p2, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);
        robot.MoveCart( desc_p3, 0, 0, 100.0f, 100.0f, 100.0f, -1.0f, -1);

        robot.FT_Guard(0, sensor_id, select, ft, max_threshold, min_threshold);
    }

Controllo forza costante
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: c#
    :linenos:

    /**
    * @brief  Controllo a Forza Costante
    * @param  [in] flag 0-Disabilita controllo forza costante, 1-Abilità controllo forza costante
    * @param  [in] sensor_id ID sensore di forza
    * @param  [in] select  Seleziona se rilevare collisione per i sei gradi di libertà, 0-Non rilevare, 1-Rileva
    * @param  [in] ft  Forza/coppia di collisione, fx,fy,fz,tx,ty,tz
    * @param  [in] ft_pid Parametri PID forza, parametri PID coppia
    * @param  [in] adj_sign Controllo avvio/arresto adattativo, 0-Disabilita, 1-Abilità
    * @param  [in] ILC_sign Controllo avvio/arresto ILC, 0-Arresto, 1-Addestramento, 2-Operativo
    * @param  [in] max_dis Massima distanza di regolazione, unità mm
    * @param  [in] max_ang Massimo angolo di regolazione, unità deg
    * @param  [in] M Parametri massa rx, ry [0.1-10], predefinito 2
    * @param  [in] B Parametri smorzamento rx, ry [0.1-50], predefinito 8
    * @param  [in] threshold Soglie di attivazione rx, ry [0-10], predefinito 0.2
    * @param  [in] adjustCoeff Coefficienti di regolazione coppia rx, ry [0-1], predefinito 1
    * @param  [in] polishRadio Raggio di lucidatura, unità mm
    * @param  [in] filter_Sign Flag abilitazione filtro 0-Spegni; 1-Accendi, predefinito spento
    * @param  [in] posAdapt_sign Flag abilitazione adattamento posa 0-Spegni; 1-Accendi, predefinito spento
    * @param  [in] isNoBlock Flag blocco, 0-Bloccante; 1-Non bloccante
    * @return  Codice errore
    */
    public int FT_Control(byte flag, int sensor_id, byte[] select, ForceTorque ft, float[] ft_pid,byte adj_sign, byte ILC_sign, float max_dis, float max_ang,double[] M, double[] B, double[] threshold, double[] adjustCoeff,double polishRadio, int filter_Sign, int posAdapt_sign, int isNoBlock)

Esempio di codice per il controllo forza costante con smorzamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7

.. code-block:: c#
    :linenos:

    public void TestFTControlWithAdjustCoeff()
    {
        int rtn;
        int sensor_id = 10;
        byte[] select = new byte[6] { 0, 0, 1, 0, 0, 0 };
        float[] ft_pid = new float[6] { 0.0008f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0;
        byte ILC_sign = 0;
        float max_dis = 1000.0f;
        float max_ang = 20.0f;
        ForceTorque ft = new ForceTorque();
        ft.fz = -10.0f;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        JointPos j1 = new JointPos(80.765f, -98.795f, 106.548f, -97.734f, -89.999f, 94.842f);
        JointPos j2 = new JointPos(43.067f, -84.429f, 92.620f, -98.175f, -90.011f, 57.144f);
        DescPose desc_p1 = new DescPose(5.009f, -547.463f, 262.053f, -179.999f, -0.019f, 75.923f);
        DescPose desc_p2 = new DescPose(-347.966f, -547.463f, 262.048f, -180.000f, -0.019f, 75.923f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        double[] M = new double[2] { 2.0, 2.0 };
        double[] B = new double[2] { 15.0, 15.0 };
        double[] threshold = new double[2] { 1.0, 1.0 };
        double[] adjustCoeff = new double[2] { 1.0, 0.8 };
        double polishRadio = 0.0;
        int filter_Sign = 0;
        int posAdapt_sign = 1;
        int isNoBlock = 0;
        while (true)
        {
            rtn = robot.FT_Control(1, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control start rtn is {rtn}");
            robot.MoveL(j1, desc_p1, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            robot.MoveL(j2, desc_p2, 1, 0, 100, 100, 100, -1, 0, epos, 0, 0, offset_pos, 0, 0, 10);
            rtn = robot.FT_Control(0, sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, threshold, adjustCoeff, 0, 0, 1, 0);
            Console.WriteLine($"FT_Control end rtn is {rtn}");
        }
    }

Inserzione Rotazionale
+++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Inserzione Rotazionale
    * @param [in] rcs Sistema di coordinate di riferimento, 0 - Sistema di coordinate utensile, 1 - Sistema di coordinate base
    * @param [in] angVelRot Velocità angolare di rotazione, unità deg/s
    * @param [in] ft Soglia Forza/Coppia, fx,fy,fz,tx,ty,tz, intervallo [0~100]
    * @param [in] max_angle Angolo di rotazione massimo, unità deg
    * @param [in] orn Direzione Forza/Coppia, 1 - Lungo l'asse Z, 2 - Attorno all'asse Z
    * @param [in] max_angAcc Accelerazione angolare massima, unità deg/s^2, attualmente non utilizzata, predefinita a 0
    * @param [in] rotorn Direzione di rotazione, 1 - Senso orario, 2 - Senso antiorario
    * @param [in] strategy Strategia di elaborazione per forza/coppia non rilevata, 0 - Errore; 1 - Avviso, continua movimento
    * @return Codice di errore
    */
    public int FT_RotInsertion(int rcs, double angVelRot, double ft, double max_angle, int orn, double max_angAcc, int rotorn, int strategy)

Esempio Codice Inserzione Rotazionale Sensore di Forza Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestMove()
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Avvia controllo compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Avvia controllo compliance
    * @param  [in] p Coefficiente di regolazione posizione o coefficiente compliance
    * @param  [in] force Soglia forza per attivare compliance, unità N
    * @return  Codice di errore
    */
    int FT_ComplianceStart(float p, float force);

Arresta controllo compliance
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Arresta controllo compliance
    * @return  Codice di errore
    */
    int FT_ComplianceStop();

Esempio di codice per il controllo compliance
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnComplience_Click(object sender, EventArgs e)
    {
        int company = 24, device = 0, softversion = 0, bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config: {company}, {device}, {softversion}, {bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);

        robot.FT_SetZero(0);
        Thread.Sleep(1000);

        byte flag = 1;
        int sensor_id = 1;
        int[] select = { 1, 1, 1, 0, 0, 0 };
        double[] ft_pid = { 0.0005f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        byte adj_sign = 0, ILC_sign = 0;
        float max_dis = 100.0f, max_ang = 0.0f;

        ForceTorque ft = new ForceTorque { fx = -10.0, fy = -10.0, fz = -10.0 };
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_p1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_p2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
        float p = 0.00005f;
        float force = 30.0f;
        int rtn = robot.FT_ComplianceStart(p, force);
        Console.WriteLine($"FT_ComplianceStart rtn is {rtn}");

        int count = 5;
        while (count-- > 0)
        {
        robot.MoveL(j1, desc_p1, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 1, offset_pos);
        robot.MoveL(j2, desc_p2, 0, 0, 100.0f, 180.0f, 100.0f, -1.0f, epos, 0, 0, offset_pos);
        }

        robot.FT_ComplianceStop();
        Console.WriteLine($"FT_ComplianceStop rtn is {rtn}");

        flag = 0;
        robot.FT_Control(flag, (byte)sensor_id, select, ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang);
    }

Inizializza identificazione carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inizializza identificazione carico
    * @return Codice di errore
    */
    int LoadIdentifyDynFilterInit();

Inizializza variabili identificazione carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Inizializza variabili identificazione carico
    * @return Codice di errore
    */
    int LoadIdentifyDynVarInit();

Programma principale identificazione carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Programma principale identificazione carico
    * @param [in] joint_torque Coppia giunto
    * @param [in] joint_pos Posizione giunto
    * @param [in] t Periodo campionamento
    * @return Codice di errore
    */
    int LoadIdentifyMain(double[] joint_torque, double[] joint_pos, double t);

Ottieni risultato identificazione carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni risultato identificazione carico
    * @param [in] gain  Coefficiente termine gravità double[6], coefficiente termine centrifugo double[6]
    * @param [out] weight Peso carico
    * @param [out] cog Centro di massa carico
    * @return Codice di errore
    */
    int LoadIdentifyGetResult(double[] gain, ref double weight, ref DescTran cog);

Esempio di codice per l'identificazione del carico del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button74_Click(object sender, EventArgs e)
    {
        int rtn;
        int retval = 0;

        retval = robot.LoadIdentifyDynFilterInit();
        Console.WriteLine("LoadIdentifyDynFilterInit retval is: " + retval);

        retval = robot.LoadIdentifyDynVarInit();
        Console.WriteLine("LoadIdentifyDynVarInit retval is: " + retval);

        JointPos posJ = new JointPos(0,0,0,0,0,0);
        DescPose posDec = new DescPose(0, 0, 0, 0, 0, 0);
        double[] joint_toq = new double[6] { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        robot.GetActualJointPosDegree(0, ref posJ);
        posJ.jPos[1] = posJ.jPos[1] + 10;
        robot.GetJointTorques(0, joint_toq);
        joint_toq[1] = joint_toq[1] + 2;

        double[] tmpTorque = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        for (int i = 0; i < 6; i++)
        {
            tmpTorque[i] = joint_toq[i];
        }

        retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
        Console.WriteLine("LoadIdentifyMain retval is: " + retval);

        double[] gain = new double[12] { 0, 0.05, 0, 0, 0, 0, 0, 0.02, 0, 0, 0, 0 };
        double weight = 0;
        DescTran load_pos = new DescTran(0, 0, 0);
        retval = robot.LoadIdentifyGetResult(gain, ref weight, ref load_pos);
        Console.WriteLine("LoadIdentifyGetResult retval is: {0}; weight is {1} cog is {2} {3} {4}", retval, weight, load_pos.x, load_pos.y, load_pos.z);
    }

Trascinamento assistito da sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: c#
    :linenos:

    /**
    * @brief  Trascinamento assistito da sensore di forza
    * @param  [in] status Stato controllo, 0-Disabilita; 1-Abilita
    * @param  [in] asaptiveFlag Flag abilitazione adattamento, 0-Disabilita; 1-Abilita
    * @param  [in] interfereDragFlag Flag trascinamento area di interferenza, 0-Disabilita; 1-Abilita
    * @param  [in] ingularityConstraintsFlag Strategia punto singolare, 0-Evita; 1-Attraversa
    * @param  [in] forceCollisionFlag Flag rilevamento collisione robot durante trascinamento assistito; 0-Disabilita; 1-Abilita
    * @param  [in] M Coefficiente inerzia
    * @param  [in] B Coefficiente smorzamento
    * @param  [in] K Coefficiente rigidità
    * @param  [in] F Soglia forza sei dimensioni per trascinamento
    * @param  [in] Fmax Limite massimo forza trascinamento Nm
    * @param  [in] Vmax Limite massimo velocità giunto °/s
    * @return  Codice di errore
    */
    int EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag,int ingularityConstraintsFlag,int forceCollisionFlag, double[] M, double[] B, double[] K, double[] F, double Fmax, double Vmax);

Ottieni lo stato dell'interruttore di trascinamento del sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni lo stato dell'interruttore di trascinamento del sensore di forza
    * @param  [out] dragState Stato controllo trascinamento assistito da sensore di forza, 0-Disabilita; 1-Abilita
    * @param  [out] sixDimensionalDragState Stato controllo trascinamento assistito a sei dimensioni, 0-Disabilita; 1-Abilita
    * @return  Codice di errore
    */
    int GetForceAndTorqueDragState(ref int dragState, ref int sixDimensionalDragState);

Attivazione automatica sensore di forza dopo cancellazione errore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Attivazione automatica sensore di forza dopo cancellazione errore
    * @param  [in] status Stato controllo, 0-Disabilita; 1-Abilita
    * @return  Codice di errore
    */
    int SetForceSensorDragAutoFlag(int status);

Esempio di codice per il trascinamento assistito da sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button61_Click(object sender, EventArgs e)
    {
        robot.SetForceSensorDragAutoFlag(1);
        double[] M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
        double[] B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
        double[] K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };

        robot.EndForceDragControl(1, 0, 0, 0, M, B, K, F, 50, 100);
        robot.WaitMs(5000);

        int dragState = 0;
        int sixDimensionalDragState = 0;
        robot.GetForceAndTorqueDragState(ref dragState, ref sixDimensionalDragState);
        Console.WriteLine($"the drag state is {dragState} {sixDimensionalDragState}");

        robot.EndForceDragControl(0, 0, 0, 0, M, B, K, F, 50, 100);
    }

Imposta interruttore e parametri per trascinamento ibrido a sei dimensioni e impedenza giunto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta interruttore e parametri per trascinamento ibrido a sei dimensioni e impedenza giunto
    * @param  [in] status Stato controllo, 0-Disabilita; 1-Abilita
    * @param  [in] impedanceFlag Flag abilitazione impedenza, 0-Disabilita; 1-Abilita
    * @param  [in] lamdeDain Guadagno trascinamento
    * @param  [in] KGain Guadagno rigidità
    * @param  [in] BGain Guadagno smorzamento
    * @param  [in] dragMaxTcpVel Limite massimo velocità lineare TCP durante trascinamento
    * @param  [in] dragMaxTcpOriVel Limite massimo velocità angolare TCP durante trascinamento
    * @return  Codice di errore
    */
    int ForceAndJointImpedanceStartStop(int status, int impedanceFlag, double[] lamdeDain, double[] KGain, double[] BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Esempio di codice per il trascinamento assistito da sensore di forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button62_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        double[] lambdaGain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
        double[] kGain = { 0, 0, 0, 0, 0, 0 };
        double[] bGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
        int rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
        Thread.Sleep(5000);
        robot.DragTeachSwitch(0);
        rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lambdaGain, kGain, bGain, 1000, 180);
        Console.WriteLine($"ForceAndJointImpedanceStartStop rtn is {rtn}");
    }

Controllo avvio/arresto impedenza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Controllo avvio/arresto impedenza
    * @param [in] status 0: Disabilita; 1-Abilità
    * @param [in] workSpace 0-Spazio giunto; 1-Spazio cartesiano
    * @param [in] forceThreshold Soglia forza di attivazione (N)
    * @param [in] m Parametro massa
    * @param [in] b Parametro smorzamento
    * @param [in] k Parametro rigidità
    * @param [in] maxV Massima velocità lineare (mm/s)
    * @param [in] maxVA Massima accelerazione lineare (mm/s2)
    * @param [in] maxW Massima velocità angolare (°/s)
    * @param [in] maxWA Massima accelerazione angolare (°/s2)
    * @return Codice di errore
    */
    public int ImpedanceControlStartStop(int status, int workSpace, double[] forceThreshold, double[] m, double[] b, double[] k, double maxV, double maxVA, double maxW, double maxWA)

Esempio di codice per il controllo avvio/arresto impedenza del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    public void TestImpedanceControl()
    {
        int[] ctrl = new int[20];
        int state;
        int pressValue;
        int error;
        int rtn;
        JointPos j1 = new JointPos(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
        JointPos j2 = new JointPos(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
        DescPose desc_pos1 = new DescPose(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
        DescPose desc_pos2 = new DescPose(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);

        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 200.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        float blendR = -1.0f;

        byte flag = 0;

        byte search = 0;
        robot.SetSpeed(20);
        int company = 17;
        int device = 0;
        int softversion = 0;
        int bus = 1;
        robot.FT_SetConfig(company, device, softversion, bus);
        Thread.Sleep(1000);
        robot.FT_GetConfig(ref company, ref device, ref softversion, ref bus);
        Console.WriteLine($"FT config:{company},{device},{softversion},{bus}");
        Thread.Sleep(1000);

        robot.FT_Activate(0);
        Thread.Sleep(1000);
        robot.FT_Activate(1);
        Thread.Sleep(1000);
        Thread.Sleep(1000);
        robot.FT_SetZero(0);
        Thread.Sleep(1000);
        robot.FT_SetZero(1);
        Thread.Sleep(1000);

        double[] forceThreshold = new double[] { 30, 30, 30, 5, 5, 5 };
        double[] m = new double[] { 0.1, 0.1, 0.1, 0.02, 0.02, 0.02 };
        double[] b = new double[] { 1, 1, 1, 0.08, 0.08, 0.08 };
        double[] k = new double[] { 0, 0, 0, 0, 0, 0 };
        rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
        Console.WriteLine($"ImpedanceControlStartStop errcode:{rtn}");
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos1, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0, epos, search, flag, offset_pos, -1, 0);
        Console.WriteLine($"movel errcode:{rtn}");
        robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
    }

Abilita funzione compensazione coppia e coefficiente di compensazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Abilita funzione compensazione coppia e coefficiente di compensazione
    * @param [in] status Interruttore, 0-Disabilita; 1-Abilità
    * @param [in] torqueCoeff Coefficiente compensazione coppia J1-J6 [0-1]
    * @return Codice errore
    */
    public int SerCoderCompenParams(int status, double[] torqueCoeff)