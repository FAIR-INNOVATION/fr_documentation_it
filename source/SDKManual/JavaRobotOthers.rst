Altre Interfacce
================

.. toctree:: 
    :maxdepth: 5

Ottenere Chiave Pubblica SSH
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene chiave pubblica SSH
    * @param [out] keygen Chiave pubblica
    * @return Codice errore
    */
    int GetSSHKeygen(String[] keygen)

Inviare Comando SCP
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /** 
    * @brief Invia comando SCP
    * @param [in] mode 0-upload (PC -> controller), 1-download (controller -> PC)
    * @param [in] sshname Nome utente PC
    * @param [in] sship Indirizzo IP PC
    * @param [in] usr_file_url Percorso file PC
    * @param [in] robot_file_url Percorso file controller robot
    * @return Codice errore
    */
    int SetSSHScpCmd(int mode, String sshname, String sship, String usr_file_url, String robot_file_url)

Calcolare Valore MD5 File in Percorso Specificato
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calcola valore MD5 file in percorso specificato
    * @param [in] file_path Percorso file incluso nome file, percorso predefinito cartella Traj: "/fruser/traj/", es. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valore MD5 file
    * @return Codice errore
    */
    int ComputeFileMD5(String file_path, String[] md5)

Esempio Codice Comandi SSH, MD5 Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSSHMd5(Robot robot)
    {
        String file_path= "/fruser/airlab.lua";
        String[] md5 =new String[]{""};

        String[] ssh_keygen=new String[]{""};
        int retval = robot.GetSSHKeygen(ssh_keygen);
        System.out.println(ssh_keygen[0]);

        String ssh_name = "fr";
        String ssh_ip = "192.168.58.45";
        String ssh_route = "/home/fr";
        String ssh_robot_url = "/root/robot/dhpara.config";
        retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
        System.out.println("SetSSHScpCmd retval is:"+ retval);
        System.out.println("robot url is:"+ ssh_robot_url);

        robot.ComputeFileMD5(file_path, md5);
        System.out.println("md5 is:+"+ md5[0]);
        return 0;
    }

Impostare Periodo Feedback Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta periodo feedback porta 20004 robot
    * @param [in] period Periodo feedback porta 20004 robot (ms)
    * @return  Codice errore
    */
    public int SetRobotRealtimeStateSamplePeriod(int period)

Ottenere Periodo Feedback Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene periodo feedback porta 20004 robot
    * @return  List[0]:Codice errore; List[1]:Periodo feedback porta 20004 robot (ms)
    */
    public List<Integer> GetRobotRealtimeStateSamplePeriod()

Esempio Codice Configurazione Periodo Feedback Porta 20004 Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestRealtimePeriod(Robot robot)
    {
        robot.SetRobotRealtimeStateSamplePeriod(10);
        List<Integer> getPeriod = new ArrayList<>();
        getPeriod=robot.GetRobotRealtimeStateSamplePeriod();
        robot.Sleep(1000);

        return 0;
    }

Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Aggiornamento software robot
     * @param [in] filePath Percorso completo pacchetto aggiornamento software
     * @param [in] block Blocco fino a completamento aggiornamento true:bloccante; false:non bloccante
     * @return  Codice errore
     */
    public int SoftwareUpgrade(String filePath, boolean block)

Ottenere Stato Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene stato aggiornamento software robot
    * @return  List[0]:Codice errore; List[1]:Stato aggiornamento software robot 0-inattivo o caricamento pacchetto; 1~100: percentuale completamento; -1: fallimento aggiornamento software; -2: fallimento verifica; -3: fallimento verifica versione; -4: fallimento decompressione; -5: fallimento aggiornamento configurazione utente; -6: fallimento aggiornamento configurazione periferiche; -7: fallimento aggiornamento configurazione assi estesi; -8: fallimento aggiornamento configurazione robot; -9: fallimento aggiornamento parametri DH
    */
    public List<Integer> GetSoftwareUpgradeState()

Esempio Codice Aggiornamento Software Robot
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUpgrade(Robot robot)
    {
        robot.SoftwareUpgrade("D://zUP/QNX382/software.tar.gz", false);
        while (true)
        {
            List<Integer> inter=new ArrayList<>();
            inter=robot.GetSoftwareUpgradeState();
            System.out.println("upgrade state is:"+ inter.get(1));
            robot.Sleep(300);
        }
    }

Download Database Tabella Punti
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Download database tabella punti
    * @param [in] pointTableName Nome tabella punti da scaricare    pointTable1.db
    * @param [in] saveFilePath Percorso salvataggio tabella punti   C://test/
    * @return Codice errore 
    */
    int PointTableDownLoad(String pointTableName, String saveFilePath);

Upload Database Tabella Punti
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Upload database tabella punti
    * @param [in] pointTableFilePath Percorso completo tabella punti da caricare   C://test/pointTable1.db
    * @return Codice errore 
    */
    int PointTableUpLoad(String pointTableFilePath);

Aggiornamento File Lua Tabella Punti
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Aggiornamento file Lua tabella punti
    * @param [in] pointTableName Nome tabella punti da cambiare   "pointTable1.db", quando tabella punti è vuota, cioè "", significa aggiornare programma Lua a programma iniziale senza tabella punti applicata
    * @param [in] luaFileName Nome file Lua da aggiornare   "testPointTable.lua"
    * @param [out] errorStr Informazioni errore cambio tabella punti
    * @return Codice errore 
    */
    int PointTableUpdateLua(String pointTableName, String luaFileName, String errorStr);

Esempio Codice Operazioni Tabella Punti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPointTable(Robot robot)
    {
        String save_path = "D://zDOWN/";
        String point_table_name = "point_table_FR5.db";
        int rtn = robot.PointTableDownLoad(point_table_name, save_path);

        String upload_path = "D://zUP/point_table_FR5.db";
        rtn = robot.PointTableUpLoad(upload_path);

        String point_tablename = "point_table_FR5.db";
        String lua_name = "airlab.lua";
        String err="";
        rtn = robot.PointTableUpdateLua(point_tablename, lua_name,err);

        robot.CloseRPC();
        return 0;
    }

Download Log Controller
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Download log controller
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice errore
    */
    int RbLogDownload(String savePath);

Download Tutte Fonti Dati
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Download tutte fonti dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice errore
    */
    int AllDataSourceDownload(String savePath);

Download Pacchetto Backup Dati
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /** 
    * @brief Download pacchetto backup dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice errore
    */
    int DataPackageDownload(String savePath);

Esempio Codice Download Dati Controller
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestDownLoadRobotData(Robot robot)
    {
        int rtn = robot.RbLogDownload("D://zDOWN/");

        rtn = robot.AllDataSourceDownload("D://zDOWN/");

        rtn = robot.DataPackageDownload("D://zDOWN/");
        return 0;
    }

Impostare Aggiornamento Encoder
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta aggiornamento encoder
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    int SetEncoderUpgrade(String path)

Impostare Aggiornamento Firmware Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware giunti
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    public int SetJointFirmwareUpgrade(int type, String path)

Impostare Aggiornamento Firmware Box Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware box controllo
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    public int SetCtrlFirmwareUpgrade(int type, String path)

Impostare Aggiornamento Firmware Terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware terminale
    * @param [in] type Tipo file aggiornamento; 1-aggiornamento firmware; 2-aggiornamento file configurazione slave
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    public int SetEndFirmwareUpgrade(int type, String path)

Aggiornamento File Configurazione Parametri Completi Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Aggiornamento file configurazione parametri completi giunti
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice errore
    */
    public int JointAllParamUpgrade(String path)

Esempio Codice Aggiornamento Firmware Slave Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFirmWareUpgrade(Robot robot)
    {
        robot.RobotEnable(0);
        robot.Sleep(200);
        int rtn = robot.JointAllParamUpgrade("D://zUP/standardQX/jointallparametersFR56.0.db");
        System.out.println("robot JointAllParamUpgrade rtn is:"+ rtn);

        rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade config param rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
        System.out.println("robot SetEndFirmwareUpgrade config param rtn is:"+ rtn);

        robot.SetSysServoBootMode();
        rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/standardQX/FR_CTRL_PRIMCU_FV201010_MAIN_U4_T01_20240529.bin");
        System.out.println("robot SetCtrlFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/standardQX/FR_END_FV201010_MAIN_U01_T01_20250522.bin");
        System.out.println("robot SetEndFirmwareUpgrade rtn is:"+ rtn);

        rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/standardQX/FR_SERVO_FV502211_MAIN_U7_T07_20250217.bin");
        System.out.println("robot SetJointFirmwareUpgrade rtn is:"+ rtn);

        robot.CloseRPC();
    }

Aggiornamento Sistema Operativo Robot (Box Controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Aggiornamento sistema operativo robot (box controllo LA)
     * @param [in] filePath Percorso completo pacchetto aggiornamento sistema operativo
     * @return  Codice errore
     */
    public int KernelUpgrade(String filePath)

Ottenere Risultato Aggiornamento Sistema Operativo Robot (Box Controllo LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene risultato aggiornamento sistema operativo robot (box controllo LA)
     * @param [out] result Risultato aggiornamento: 0:successo; -1:fallimento
     * @return  Codice errore
     */
    public int GetKernelUpgradeResult(int[] result)

Generazione Log MCU Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Generazione log MCU robot
    * @return Codice errore
    */
    public int RobotMCULogCollect()