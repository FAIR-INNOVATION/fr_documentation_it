Altre Interfacce
================

.. toctree:: 
    :maxdepth: 5

Ottenere Chiave Pubblica SSH
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Chiave Pubblica SSH 
    * @param [out] keygen Chiave pubblica
    * @return Codice errore 
    */
    int GetSSHKeygen(ref string keygen);

Inviare Comando SCP
+++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Inviare Comando SCP
    * @param [in] mode 0-Caricamento (PC supervisore -> controller), 1-Scaricamento (controller -> PC supervisore)
    * @param [in] sshname Nome utente PC supervisore
    * @param [in] sship Indirizzo IP PC supervisore
    * @param [in] usr_file_url Percorso file PC supervisore
    * @param [in] robot_file_url Percorso file controller robot
    * @return Codice errore
    */
    int SetSSHScpCmd(int mode, string sshname, string sship, string usr_file_url, string robot_file_url);

Calcolare Valore MD5 File Percorso Specificato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolare Valore MD5 File Percorso Specificato 
    * @param [in] file_path Percorso file incluso nome file, percorso cartella Traj predefinito:"/fruser/traj/", es. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valore MD5 file
    * @return Codice errore 
    */
    int ComputeFileMD5(string file_path, ref string md5);

Esempio Codice Istruzioni SSH, MD5 Robot
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        string file_path = "/fruser/airlab.lua";
        string md5 = "";
        byte emerg_state = 0;
        byte si0_state = 0;
        byte si1_state = 0;
        int sdk_com_state = 0;

        string ssh_keygen = "";
        int retval = robot.GetSSHKeygen(ref ssh_keygen);
        Console.WriteLine("GetSSHKeygen retval is: {0}", retval);
        Console.WriteLine("ssh key is: {0}", ssh_keygen);

        string ssh_name = "fr";
        string ssh_ip = "192.168.58.45";
        string ssh_route = "/home/fr";
        string ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        Console.WriteLine("SetSSHScpCmd retval is: {0}", retval);
        Console.WriteLine("robot url is: {0}", ssh_robot_url);

        robot.ComputeFileMD5(file_path, ref md5);
        Console.WriteLine("md5 is: {0}", md5);
    }

Impostare Periodo Feedback Porta 20004 Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Periodo Feedback Porta 20004 Robot
    * @param [in] period Periodo feedback porta 20004 robot(ms)
    * @return Codice errore
    */
    int SetRobotRealtimeStateSamplePeriod(int period);

Ottenere Periodo Feedback Porta 20004 Robot
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottenere Periodo Feedback Porta 20004 Robot
    * @param [out] period Periodo feedback porta 20004 robot(ms)
    * @return Codice errore
    */
    int GetRobotRealtimeStateSamplePeriod(ref int period);

Esempio Codice Configurazione Periodo Feedback Stato Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button47_Click(object sender, EventArgs e)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        int getPeriod = 0;
        robot.GetRobotRealtimeStateSamplePeriod(ref getPeriod);
        Console.WriteLine("period is {0}", getPeriod);
        Thread.Sleep(1000);
    }

Aggiornamento Software Robot
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aggiornamento Software Robot
    * @param [in] filePath Percorso completo pacchetto aggiornamento software
    * @param [in] block Se bloccare fino al completamento aggiornamento true:bloccante; false:non bloccante
    * @return   Codice errore
    */
    int SoftwareUpgrade(string filePath, bool block);

Ottenere Stato Aggiornamento Software Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Stato Aggiornamento Software Robot
    * @param [out] state Stato aggiornamento pacchetto software robot  0-inattivo o caricamento pacchetto aggiornamento in corso; 1~100: percentuale completamento aggiornamento; -1:fallimento aggiornamento software; -2: fallimento verifica; -3: fallimento verifica versione; -4: fallimento estrazione; -5: fallimento aggiornamento configurazione utente; -6: fallimento aggiornamento configurazione periferiche; -7: fallimento aggiornamento configurazione assi estesi; -8: fallimento aggiornamento configurazione robot; -9: fallimento aggiornamento parametri DH
    * @return   Codice errore
    */
    int GetSoftwareUpgradeState(ref int state);

Esempio Codice Aggiornamento Software Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button48_Click(object sender, EventArgs e)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            int curState = -1;
            robot.GetSoftwareUpgradeState(ref curState);
            Console.WriteLine("upgrade state is {0}", curState);
            Thread.Sleep(300);
        }
    }

Scaricamento Tabella Punti
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Scaricamento Tabella Punti da Controller Robot a Computer Locale 
    * @param [in] pointTableName Nome tabella punti nel controller: pointTable1.db
    * @param [in] saveFilePath Percorso scaricamento tabella punti sul computer C://test/
    * @return Codice errore 
    */
    int PointTableDownLoad(string pointTableName, string saveFilePath);

Caricamento Tabella Punti
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Caricamento Tabella Punti da Computer Locale a Controller Robot 
    * @param [in] pointTableFilePath Percorso assoluto tabella punti su computer locale C://test/pointTabl e1.db
    * @return Codice errore 
    */
    int PointTableUpLoad(string pointTableFilePath);

Aggiornamento Programma Lua con Tabella Punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Aggiornamento punti nel programma Lua usando la tabella punti fornita
    * @param [in] pointTableName Nome tabella punti nel controller: "pointTable1.db", quando tabella punti vuota, cioè "", indica aggiornamento programma Lua al programma iniziale senza tabella punti applicata
    * @param [in] luaFileName Nome file Lua da aggiornare   "test.lua"
    * @param [out] errorStr Informazioni errore aggiornamento Lua tabella punti  
    * @return Codice errore 
    */
    int PointTableUpdateLua(string pointTableName, string luaFileName, ref string errorStr);

Cambio Tabella Punti e Applicazione
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Cambio Tabella Punti e Applicazione
    * @param [in] pointTableName Nome tabella punti da cambiare   "pointTable1.db"
    * @param [out] errorStr Informazioni errore cambio tabella punti   
    * @return Codice errore 
    */
    int PointTableSwitch(string pointTableName, ref string errorStr);

Esempio Codice Operazioni Tabella Punti Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnUpload_Click(object sender, EventArgs e)
    {
        string save_path = "D://zDOWN/";
        string point_table_name = "test_point_A.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);
        Console.WriteLine("download : {0} fail: {1}", point_table_name, rtn);

        string upload_path = "D://zUP/test_point_A.db";
        rtn = robot.PointTableUpLoad(upload_path);
        Console.WriteLine("retval is: {0}", rtn);

        string point_tablename = "test_point_A.db";
        string lua_name = "Text1.lua";

        string errorStr = "";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name, ref errorStr);
        Console.WriteLine("retval is: {0}", rtn);
    }

Scaricamento Log Controller
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Scaricamento Log Controller
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return   Codice errore
    */
    int RbLogDownload(string savePath);

Scaricamento Tutte Sorgenti Dati
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Scaricamento Tutte Sorgenti Dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return   Codice errore
    */
    int AllDataSourceDownload(string savePath);

Scaricamento Pacchetto Backup Dati
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Scaricamento Pacchetto Backup Dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return   Codice errore
    */
    int DataPackageDownload(string savePath);

Esempio Codice Scaricamento Dati Controller
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button50_Click(object sender, EventArgs e)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");
        Console.WriteLine("RbLogDownload rtn is {0}", rtn);

        rtn = robot.AllDataSourceDownload("D://zDOWN/");
        Console.WriteLine("AllDataSourceDownload rtn is {0}", rtn);

        rtn = robot.DataPackageDownload("D://zDOWN/");
        Console.WriteLine("DataPackageDownload rtn is {0}", rtn);
    }

Aggiornamento Sistema Operativo Robot (Quadro Controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Aggiornamento Sistema Operativo Robot (Quadro Controllo LA)
     * @param [in] filePath Percorso completo pacchetto aggiornamento sistema operativo
     * @return   Codice errore
     */
    public int KernelUpgrade(string filePath)

Ottenere Risultato Aggiornamento Sistema Operativo Robot (Quadro Controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
    :linenos:

    /**
     * @brief Ottenere Risultato Aggiornamento Sistema Operativo Robot (Quadro Controllo LA)
     * @param [out] result Risultato aggiornamento: 0:successo; -1:fallimento
     * @return   Codice errore
     */
    public int GetKernelUpgradeResult(ref int[] result)

Impostare Aggiornamento Encoder
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Aggiornamento Encoder
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int SetEncoderUpgrade(string path);

Impostare Aggiornamento Firmware Giunto
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Aggiornamento Firmware Giunto
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int SetJointFirmwareUpgrade(int type, string path);

Impostare Aggiornamento Firmware Quadro Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Aggiornamento Firmware Quadro Controllo
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int SetCtrlFirmwareUpgrade(int type, string path);

Impostare Aggiornamento Firmware Estremità
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare Aggiornamento Firmware Estremità
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int SetEndFirmwareUpgrade(int type, string path);

Aggiornamento File Configurazione Parametri Completi Giunto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Aggiornamento File Configurazione Parametri Completi Giunto
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int JointAllParamUpgrade(string path);

Esempio Codice Aggiornamento Firmware Slave Robot
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button83_Click(object sender, EventArgs e)
    {
        robot.RobotEnable(0);
        Thread.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
        Console.WriteLine($"robot JointAllParamUpgrade rtn is{rtn}");
        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
        Console.WriteLine($"robot SetCtrlFirmwareUpgrade rtn is{rtn}");
        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
        Console.WriteLine($"robot SetEndFirmwareUpgrade rtn is {rtn}");
        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
        Console.WriteLine($"robot SetJointFirmwareUpgrade rtn is{rtn}");
    }

Generazione Log MCU Robot
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Generazione Log MCU Robot
    * @return Codice errore
    */
    public int RobotMCULogCollect();