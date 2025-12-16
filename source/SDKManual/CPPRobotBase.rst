Fondamenti del Robot
=================================

.. toctree:: 
    :maxdepth: 5

Creare un'istanza del Robot (Istanziazione)
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Costruttore della classe interfaccia del robot
    */
    FRRobot();

Stabilire la comunicazione con il controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Stabilisce la comunicazione con il controller del robot
    * @param  [in] ip  Indirizzo IP del controller, predefinito di fabbrica: 192.168.58.2
    * @return Codice di errore
    */
    errno_t  RPC(const char *ip);

Chiudere la comunicazione con il controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief   Chiude la comunicazione con il controller del robot
     * @return Codice di errore
     */
    errno_t  CloseRPC();

Interrogare il numero di versione dell'SDK
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Interroga il numero di versione dell'SDK
    * @param  [out] version   Numero di versione dell'SDK
    * @return   Codice di errore
    */  
    errno_t  GetSDKVersion(char *version);

Ottenere l'IP del controller
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Ottiene l'IP del controller
    * @param  [out] ip  IP del controller
    * @return   Codice di errore
    */
    errno_t  GetControllerIP(char *ip);

Controllare l'ingresso o l'uscita del robot dalla modalità di insegnamento tramite trascinamento (drag & teach)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Controlla l'ingresso o l'uscita del robot dalla modalità di insegnamento tramite trascinamento
    * @param  [in] state 0-Esci dalla modalità insegnamento tramite trascinamento, 1-Entra nella modalità insegnamento tramite trascinamento
    * @return   Codice di errore
    */
    errno_t  DragTeachSwitch(uint8_t state);

Interrogare se il robot è in modalità trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Interroga se il robot è in modalità di insegnamento tramite trascinamento
    * @param  [out] state 0-Non in modalità insegnamento tramite trascinamento, 1-In modalità insegnamento tramite trascinamento
    * @return   Codice di errore
    */
    errno_t  IsInDragTeach(uint8_t *state);

Controllare l'abilitazione (enable) o la disabilitazione (disable) del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Controlla l'abilitazione o la disabilitazione del robot. Dopo l'accensione, il robot è automaticamente abilitato per impostazione predefinita.
    * @param  [in] state  0-Disabilita (disable), 1-Abilitata (enable)
    * @return   Codice di errore
    */
    errno_t  RobotEnable(uint8_t state);

Controllare la commutazione della modalità manuale/automatica del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Controlla la commutazione della modalità manuale/automatica del robot
    * @param [in] mode 0-Modalità automatica, 1-Modalità manuale
    * @return Codice di errore
    */
    errno_t  Mode(int mode);

Spegnere il sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Spegne il sistema operativo del robot
    * @return Codice di errore
    */
    errno_t ShutDownRobotOS();

Impostare i parametri di riconnessione per la comunicazione con il robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i parametri di riconnessione per la comunicazione con il robot
    * @param [in] enable Abilita la riconnessione in caso di guasto di rete true-Abilitata false-Disabilitata
    * @param [in] reconnectTime Tempo di riconnessione, unità ms
    * @param [in] period Periodo di riconnessione, unità ms
    * @return Codice di errore
    */
    errno_t SetReConnectParam(bool enable, int reconnectTime = 30000, int period = 50);

Spegnere il sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spegne il sistema operativo del robot
    * @return Codice di errore
    */
    int ShutDownRobotOS();

Inizializzare i parametri del registro (log)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inizializza i parametri del registro (log);
    * @param output_model：Modalità di output, 0-Output diretto；1-Output bufferizzato；2-Output asincrono;
    * @param file_path: Percorso+Nome del file di salvataggio, lunghezza massima 256, il nome deve essere nel formato xxx.log, ad esempio /home/fr/linux/fairino.log;
    * @param file_num：Numero di file per l'archiviazione a rotazione (rolling), da 1 a 20 file. Dimensione massima per singolo file 50M;
    * @return errno_t Codice di errore;
    */
	errno_t LoggerInit(int output_model = 0, std::string file_path = "", int file_num = 5);

Impostare il livello di filtro del registro (log)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il livello di filtro del registro (log);
    * @param lvl: Valore del livello di filtro, valori più bassi producono meno log in output, valore predefinito è 1. 1-error, 2-warning, 3-inform, 4-debug;
    */
    void SetLoggerLevel(int lvl = 1);

Esempio di codice per il controllo di base del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestRobotCtrl(void)
    {
            ROBOT_STATE_PKG pkg = {};
            FRRobot robot;
            robot.LoggerInit();
            robot.SetLoggerLevel(1);
            int rtn = robot.RPC("192.168.58.2");
            robot.SetReConnectParam(true, 30000, 500);
            char ip[64] = "";
            char version[64] = "";
            uint8_t state;
            robot.GetSDKVersion(version);
            printf("SDK version:%s\n", version);
            robot.GetControllerIP(ip);
            printf("controller ip:%s\n", ip);
            robot.Mode(1);
            robot.Sleep(1000);
            robot.DragTeachSwitch(1);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.DragTeachSwitch(0);
            robot.Sleep(1000);
            robot.IsInDragTeach(&state);
            printf("drag state :%u\n", state);
            robot.Sleep(3000);
            robot.RobotEnable(0);
            robot.Sleep(3000);
            robot.RobotEnable(1);
            robot.Mode(0);
            robot.Sleep(1000);
            robot.Mode(1);
            robot.Sleep(3000);
            robot.ShutDownRobotOS();
            robot.CloseRPC();
            return 0;
    }

Esempio di codice per ottenere la versione software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la versione software del robot
    * @param[out]	robotModel Modello del robot
    * @param[out]	webversion Versione web
    * @param[out]	controllerVersion Versione del controller
    * @return Codice di errore
    */
    errno_t GetSoftwareVersion(char robotModel[64], char webVersion[64], char controllerVersion[64]);

Ottenere la versione hardware del robot
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la versione hardware del robot
    * @param[out] ctrlBoxBoardversion Versione hardware della scheda principale del control box
    * @param[out] driver1version Versione hardware del driver 1
    * @param[out] driver2version Versione hardware del driver 2
    * @param[out] driver3version Versione hardware del driver 3
    * @param[out] driver4version Versione hardware del driver 4
    * @param[out] driver5version Versione hardware del driver 5
    * @param[out] driver6version Versione hardware del driver 6
    * @param[out] endBoardversion Versione hardware della scheda terminale (end board)
    */
    errno_t GetHardwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Ottenere la versione firmware del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene la versione firmware del robot
    * @param[out] ctrlBoxBoardversion Versione firmware della scheda principale del control box
    * @param[out] driver1version Versione firmware del driver 1
    * @param[out] driver2version Versione firmware del driver 2
    * @param[out] driver3version Versione firmware del driver 3
    * @param[out] driver4version Versione firmware del driver 4
    * @param[out] driver5version Versione firmware del driver 5
    * @param[out] driver6version Versione firmware del driver 6
    * @param[out] endBoardversion Versione firmware della scheda terminale (end board)
    */
    errno_t GetFirmwareVersion(char ctrlBoxBoardversion[128], char driver1version[128], char driver2version[128], char driver3version[128], char driver4version[128], char driver5version[128], char driver6version[128], char endBoardversion[128]);

Esempio di codice per ottenere le versioni software/firmware del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestGetVersions(void)
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
         char robotModel[64] = { 0 };
         char webversion[64] = { 0 };
         char controllerVersion[64] = { 0 };
         char ctrlBoxBoardversion[128] = { 0 };
         char driver1version[128] = { 0 };
         char driver2version[128] = { 0 };
         char driver3version[128] = { 0 };
         char driver4version[128] = { 0 };
         char driver5version[128] = { 0 };
         char driver6version[128] = { 0 };
         char endBoardversion[128] = { 0 };
         rtn = robot.GetSoftwareVersion(robotModel, webversion, controllerVersion);
         printf("Getsoftwareversion rtn is: %d\n", rtn);
         printf("robotmodel is: %s, webversion is: %s, controllerVersion is: %s \n\n", robotModel, webversion, controllerVersion);
         rtn = robot.GetHardwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetHardwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         rtn = robot.GetFirmwareVersion(ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         printf("GetFirmwareversion rtn is: %d\n", rtn);
         printf("GetHardwareversion get hardware versoin is: %s, %s, %s, %s, %s, %s, %s, %s\n\n", ctrlBoxBoardversion, driver1version, driver2version, driver3version, driver4version, driver5version, driver6version, endBoardversion);
         robot.CloseRPC();
         return 0;
     }