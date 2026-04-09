Altre Interfacce
=================

.. toctree:: 
    :maxdepth: 5

Ottenere la chiave pubblica SSH
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la chiave pubblica SSH
    * @param [out] keygen Chiave pubblica
    * @return Codice di errore
    */
    errno_t GetSSHKeygen(char keygen[1024]);

Inviare comando SCP
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Invia comando SCP
    * @param [in] mode 0-Upload (computer->controller), 1-Download (controller->computer)
    * @param [in] sshname Nome utente computer
    * @param [in] sship Indirizzo IP computer
    * @param [in] usr_file_url Percorso file computer
    * @param [in] robot_file_url Percorso file controller robot
    * @return Codice di errore
    */
    errno_t SetSSHScpCmd(int mode, char sshname[32], char sship[32], char usr_file_url[128], char robot_file_url[128]);

Calcolare il valore MD5 del file nel percorso specificato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Calcola il valore MD5 del file nel percorso specificato
    * @param [in] file_path Percorso file incluso nome file, percorso cartella Traj predefinito: "/fruser/traj/", es. "/fruser/traj/trajHelix_aima_1.txt"
    * @param [out] md5 Valore MD5 file
    * @return Codice di errore
    */
    errno_t ComputeFileMD5(char file_path[256], char md5[256]);

Esempio di codice per comandi SSH e MD5 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSSHMd5(void)
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
      char file_path[256] = "/fruser/airlab.lua";
      char md5[256] = { 0 };
      uint8_t emerg_state = 0;
      uint8_t si0_state = 0;
      uint8_t si1_state = 0;
      int sdk_com_state = 0;
      char ssh_keygen[1024] = { 0 };
      int retval = robot.GetSSHKeygen(ssh_keygen);
      printf("GetSSHKeygen retval is: %d\n", retval);
      printf("ssh key is: %s \n", ssh_keygen);
      char ssh_name[32] = "fr";
      char ssh_ip[32] = "192.168.58.45";
      char ssh_route[128] = "/home/fr";
      char ssh_robot_url[128] = "/root/robot/dhpara.config";
      retval = robot.SetSSHScpCmd(1, ssh_name, ssh_ip, ssh_route, ssh_robot_url);
      printf("SetSSHScpCmd retval is: %d\n", retval);
      printf("robot url is: %s\n", ssh_robot_url);
      robot.ComputeFileMD5(file_path, md5);
      printf("md5 is: %s \n", md5);
      robot.CloseRPC();
      return 0;
    }

Impostare il periodo di feedback della porta 20004 del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il periodo di feedback della porta 20004 del robot
    * @param [in] period Periodo di feedback porta 20004 del robot (ms)
    * @return Codice di errore
    */
    errno_t SetRobotRealtimeStateSamplePeriod(int period);

Ottenere il periodo di feedback della porta 20004 del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il periodo di feedback della porta 20004 del robot
    * @param [out] period Periodo di feedback porta 20004 del robot (ms)
    * @return Codice di errore
    */
    errno_t GetRobotRealtimeStateSamplePeriod(int& period);

Esempio di codice per configurazione periodo feedback stato in tempo reale porta 20004 robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestRealtimePeriod(void)
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
      robot.SetRobotRealtimeStateSamplePeriod(10);
      int getPeriod = 0;
      robot.GetRobotRealtimeStateSamplePeriod(getPeriod);
      cout << "period is " << getPeriod << endl;
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Aggiornamento software del robot
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Aggiornamento software del robot
    * @param [in] filePath Percorso completo pacchetto aggiornamento software
    * @param [in] block Se bloccare fino al completamento aggiornamento true: bloccante; false: non bloccante
    * @return Codice di errore
    */
    errno_t SoftwareUpgrade(std::string filePath, bool block);

Ottenere lo stato dell'aggiornamento software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato dell'aggiornamento software del robot
    * @param [out] state Stato aggiornamento pacchetto software robot (0-Inattivo o caricamento pacchetto aggiornamento; 1~100: percentuale completamento aggiornamento; -1: aggiornamento software fallito; -2: verifica fallita; -3: verifica versione fallita; -4: decompressione fallita; -5: aggiornamento configurazione utente fallito; -6: aggiornamento configurazione periferiche fallito; -7: aggiornamento configurazione assi estesi fallito; -8: aggiornamento configurazione robot fallito; -9: aggiornamento parametri DH fallito)
    * @return Codice di errore
    */
    errno_t GetSoftwareUpgradeState(int &state);

Esempio di codice per aggiornamento software robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestUpgrade(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(3);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      robot.SoftwareUpgrade("D://zUP/QNX/software.tar.gz", false);
      while (true)
      {
        int curState = -1;
        robot.GetSoftwareUpgradeState(curState);
        printf("upgrade state is %d\n", curState);
        robot.Sleep(300);
      }
      robot.CloseRPC();
      return 0;
    }

Download database tabella punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Download database tabella punti
    * @param [in] pointTableName Nome tabella punti da scaricare    pointTable1.db
    * @param [in] saveFilePath Percorso di salvataggio tabella punti scaricata   C://test/
    * @return Codice di errore
    */
    errno_t PointTableDownLoad(const std::string &pointTableName, const std::string &saveFilePath);

Upload database tabella punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Upload database tabella punti
    * @param [in] pointTableFilePath Nome percorso completo tabella punti da caricare   C://test/pointTable1.db
    * @return Codice di errore
    */
    errno_t PointTableUpLoad(const std::string &pointTableFilePath);

Aggiornamento file Lua tabella punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Aggiornamento file Lua tabella punti
    * @param [in] pointTableName Nome tabella punti da attivare   "pointTable1.db", quando la tabella punti è vuota, cioè "", significa aggiornare il programma Lua al programma iniziale senza tabella punti applicata
    * @param [in] luaFileName Nome file Lua da aggiornare   "testPointTable.lua"
    * @param [out] errorStr Informazioni errore attivazione tabella punti
    * @return Codice di errore
    */
    errno_t PointTableUpdateLua(const std::string &pointTableName, const std::string &luaFileName);

Esempio di codice per operazioni tabella punti robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestPointTable(void)
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
      string save_path = "D://zDOWN/";
      string point_table_name = "point_table_FR5.db";
      rtn = robot.PointTableDownLoad(point_table_name, save_path);
      cout << "download : " << point_table_name << " fail: " << rtn << endl;
      string upload_path = "D://zUP/point_table_FR5.db";
      rtn = robot.PointTableUpLoad(upload_path);
      cout << "retval is: " << rtn << endl;
      string point_tablename = "point_table_FR5.db";
      string lua_name = "airlab.lua";
      rtn = robot.PointTableUpdateLua(point_tablename, lua_name);
      cout << "retval is: " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Download log controller
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Download log controller
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice di errore
    */
    errno_t RbLogDownload(std::string savePath);

Download tutte le sorgenti dati
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Download tutte le sorgenti dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice di errore
    */
    errno_t AllDataSourceDownload(std::string savePath);

Download pacchetto backup dati
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Download pacchetto backup dati
    * @param [in] savePath Percorso salvataggio file "D://zDown/"
    * @return Codice di errore
    */
    errno_t DataPackageDownload(std::string savePath);

Esempio di codice per download dati controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestDownLoadRobotData(void)
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
      rtn = robot.RbLogDownload("D://zDOWN/");
      cout << "RbLogDownload rtn is " << rtn << endl;
      rtn = robot.AllDataSourceDownload("D://zDOWN/");
      cout << "AllDataSourceDownload rtn is " << rtn << endl;
      rtn = robot.DataPackageDownload("D://zDOWN/");
      cout << "DataPackageDownload rtn is " << rtn << endl;
      robot.CloseRPC();
      return 0;
    }

Impostare aggiornamento firmware giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware giunti
    * @param [in] type Tipo file aggiornamento; 1-Aggiornamento firmware (prima dell'uso, far entrare il robot in modalità boot); 2-Aggiornamento file configurazione slave (prima dell'uso, disabilitare il robot)
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice di errore
    */
    errno_t SetJointFirmwareUpgrade(int type, std::string path);

Impostare aggiornamento firmware scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware scatola di controllo
    * @param [in] type Tipo file aggiornamento; 1-Aggiornamento firmware (prima dell'uso, far entrare il robot in modalità boot); 2-Aggiornamento file configurazione slave (prima dell'uso, disabilitare il robot)
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice di errore
    */
    errno_t SetCtrlFirmwareUpgrade(int type, std::string path);

Impostare aggiornamento firmware terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta aggiornamento firmware terminale
    * @param [in] type Tipo file aggiornamento; 1-Aggiornamento firmware (prima dell'uso, far entrare il robot in modalità boot); 2-Aggiornamento file configurazione slave (prima dell'uso, disabilitare il robot)
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice di errore
    */
    errno_t SetEndFirmwareUpgrade(int type, std::string path);

Aggiornamento file configurazione parametri completi giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Aggiornamento file configurazione parametri completi giunti (prima dell'uso, disabilitare il robot)
    * @param [in] path Percorso completo pacchetto aggiornamento locale (D://zUP/XXXXX.bin)
    * @return Codice di errore
    */
    errno_t JointAllParamUpgrade(std::string path);

Esempio di codice per aggiornamento firmware slave robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestFirmWareUpgrade()
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
    robot.RobotEnable(0);
    robot.Sleep(200);
    rtn = robot.JointAllParamUpgrade("D://zUP/upgrade/jointallparameters.db");
    printf("robot JointAllParamUpgrade rtn is %d\n", rtn);
    rtn = robot.SetCtrlFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Cbd_Asix_V2.0.bin");
    printf("robot SetCtrlFirmwareUpgrade config param rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(2, "D://zUP/upgrade/FAIR_Cobot_Axle_Asix_V2.4.bin");
    printf("robot SetEndFirmwareUpgrade config param rtn is %d\n", rtn);
    robot.SetSysServoBootMode();
    rtn = robot.SetCtrlFirmwareUpgrade(1, "D://zUP/upgrade/FR_CTRL_PRIMCU_FV201212_MAIN_U4_T01_20250428(MT).bin");
    printf("robot SetCtrlFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetEndFirmwareUpgrade(1, "D://zUP/upgrade/FR_END_FV201009_MAIN_U1_T01_20250428.bin");
    printf("robot SetEndFirmwareUpgrade rtn is %d\n", rtn);
    rtn = robot.SetJointFirmwareUpgrade(1, "D://zUP/upgrade/FR_SERVO_FV504214_MAIN_U7_T07_20250519.bin");
    printf("robot SetJointFirmwareUpgrade rtn is %d\n", rtn);
    robot.CloseRPC();
    return 0;
    }

Aggiornamento sistema operativo robot (Scatola di controllo LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Aggiornamento sistema operativo robot (Scatola di controllo LA)
    * @param [in] filePath Percorso completo pacchetto aggiornamento sistema operativo
    * @return Codice di errore
    */
    errno_t KernelUpgrade(std::string filePath);

Ottenere risultato aggiornamento sistema operativo robot (Scatola di controllo LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene risultato aggiornamento sistema operativo robot (Scatola di controllo LA)
    * @param [out] result Risultato aggiornamento: 0: successo; -1: fallito
    * @return Codice di errore
    */
    errno_t GetKernelUpgradeResult(int& result);

Generazione log MCU robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Generazione log MCU robot
    * @return Codice di errore
    */
    errno_t RobotMCULogCollect();

Imposta l'arresto del robot quando la comunicazione della porta è disconnessa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta l'arresto del robot quando la comunicazione della porta è disconnessa
    * @param [in] portID Numero porta 0-8080; 1-8083; 2-20002; 3-20004
    * @param [in] enable 0-disabilitato; 1-abilitato
    * @param [in] confirmTime Durata conferma interruzione comunicazione (ms)[0-5000]
    * @return Codice di errore
    */
    errno_t SetRobotStopOnComDisc(int portID, bool enable, int confirmTime);
        
Ottieni i parametri di arresto del robot alla disconnessione della comunicazione della porta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i parametri di arresto del robot alla disconnessione della comunicazione della porta
    * @param [in] portID Numero porta 0-8080; 1-8083; 2-20002; 3-20004
    * @param [out] enable 0-disabilitato; 1-abilitato
    * @param [out] confirmTime Durata conferma interruzione comunicazione (ms)[0-5000]
    * @return Codice di errore
    */
    errno_t GetRobotStopOnComDisc(int portID, bool &enable, int &confirmTime);

Esempio di Codice per i Parametri di Arresto del Robot alla Disconnessione della Comunicazione della Porta
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestRobotStopOnComDisc()
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
        bool enable = false;
        int confirmTime = 0;
        rtn = robot.SetRobotStopOnComDisc(0, true, 330);
        rtn = robot.SetRobotStopOnComDisc(1, true, 550);
        rtn = robot.SetRobotStopOnComDisc(2, true, 110);
        rtn = robot.SetRobotStopOnComDisc(3, true, 220);
        printf("SetRobotStopOnComDisc %d\n", rtn);
        robot.GetRobotStopOnComDisc(0, enable, confirmTime);
        printf("GetRobotStopOnComDisc 8080 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(1, enable, confirmTime);
        printf("GetRobotStopOnComDisc 80803 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(2, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20002 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.GetRobotStopOnComDisc(3, enable, confirmTime);
        printf("GetRobotStopOnComDisc 20004 rtn %d; enable is %d; confirm time is %d\n", rtn, enable, confirmTime);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Invia Frame di Istruzione UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Invia frame di istruzione UDP
    * @param [in] frame Stringa del frame dati da inviare, es. /f/bIII20III303III7IIIMode(0)III/b/f
    * @return Codice di errore
    */
    errno_t SendUDPFrame(std::string frame);

Imposta la Funzione di Callback per i Risultati di Esecuzione delle Istruzioni Inviate da SDK tramite UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la funzione di callback per i risultati di esecuzione delle istruzioni inviate da SDK tramite UDP
    * @param [in] CallBack Funzione di callback; comType-tipo di risposta comunicazione risultato istruzione 0-TCP, 1-UDP; count-conteggio frame di risposta istruzione; cmdID-ID istruzione; contentLen-lunghezza dati; content-contenuto dati
    * @return Codice di errore
    */
    errno_t SetCmdRpyCallback(void (*CallBack)(int comType, int count, int cmdID, int contentLen, std::string content));

Esempio di Codice per Invio Istruzioni UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestSendUDPFrame()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.SetCmdRpyCallback(UDPFrameCallBack);
        printf("SetCmdRpyCallback rtn is %d\n", rtn);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        robot.SetReConnectParam(true, 30000, 500);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame Mode(0) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII21III303III7IIIMode(1)III/b/f");
        printf("SendUDPFrame Mode(1) rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII49III201III184IIIMoveJ(-15.625, -82.680, 101.654, -110.950, -88.290, 0.017, -383.012, -2.325, 242.655, -178.024, 1.710, 74.416, 0, 0, 100, 100, 100, 0.000, 0.000, 0.000, 0.000, -1, 0, 0, 0, 0, 0, 0, 0)III/b/f");
        printf("SendUDPFrame MoveJ(-15.625 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII48III203III199IIIMoveL(-75.622, -82.680, 101.654, -110.950, -88.290, 0.017, -193.537, 330.525, 242.657, -178.024, 1.710, 14.420, 0, 0, 100, 100, 100, -1, 0, 0.000, 0.000, 0.000, 0.000, 0, 0, 0, 0, 0, 0, 0, 0, 100, 0)III/b/f");
        printf("SendUDPFrame MoveL(-75.622 rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII4III905III20IIIGetSoftwareVersion()III/b/f");
        printf("SendUDPFrame GetSoftwareVersion() rtn is %d\n", rtn);
        robot.Sleep(1000);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("III20III303III7IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III7IIIMode(0)");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bIII20III303III6IIIMode(0)III/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/b|||20|||303|||7|||Mode(0)|||/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        rtn = robot.SendUDPFrame("/f/bII20II303II7IIMode(0)II/b/f");
        printf("SendUDPFrame rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }
    
Imposta il Colore LED Personalizzato dell'End-Effector del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il colore LED personalizzato dell'end-effector del robot
    * @param [in] r Controllo LED rosso dell'end-effector; 0-spento; 1-acceso
    * @param [in] g Controllo LED verde dell'end-effector; 0-spento; 1-acceso
    * @param [in] b Controllo LED blu dell'end-effector; 0-spento; 1-acceso
    * @return Codice di errore
    */
    errno_t SetUserLEDColor(bool r, bool g, bool b);
        
Esempio di Codice per Impostare il Colore LED Personalizzato dell'End-Effector del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestUserLedColor()
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
        robot.SetUserLEDColor(true, true, true);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(true, false, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, true, false);
        robot.Sleep(1000);
        robot.SetUserLEDColor(false, false, true);
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }