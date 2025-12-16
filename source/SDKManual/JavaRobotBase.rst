Fondamenti del Robot
====================

.. toctree:: 
    :maxdepth: 5

Istanziazione del Robot
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Costruttore della classe interfaccia robot
    */
    Robot robot = new Robot(); 

Stabilire Comunicazione con il Controllore
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Stabilisce comunicazione con il controllore del robot
    * @param  [in] ip  Indirizzo IP del controllore, di fabbrica default 192.168.58.2
    * @return Codice errore
    */
    int RPC(String ip);

Chiudere Comunicazione con il Robot
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Chiude la comunicazione con il robot
    * @return Codice errore 
    */ 
    int CloseRPC(); 

Interrogare Numero Versione SDK
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Interroga il numero di versione SDK 
    * @return Numero versione 
    */  
    String GetSDKVersion();

Ottenere IP Controllore
+++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene l'IP del controllore
    * @param  [out] ip  IP controllore
    * @return  Codice errore
    */
    int GetControllerIP(String[] ip);

Controllare Ingresso/Uscita Robot dalla Modalità Insegnamento Trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controlla l'ingresso o l'uscita del robot dalla modalità di insegnamento trascinamento
    * @param  [in] state 0-esci dalla modalità insegnamento trascinamento, 1-entra nella modalità insegnamento trascinamento
    * @return  Codice errore
    */
    int DragTeachSwitch(int state);

Interrogare Se il Robot è in Modalità Insegnamento Trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Interroga se il robot è in modalità insegnamento trascinamento
    * @param  [in] state 0-non in modalità insegnamento trascinamento, 1-in modalità insegnamento trascinamento
    * @return  Codice errore
    */
    int IsInDragTeach(List<Number> state);

Controllare Abilitazione/Disabilitazione del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Controlla l'abilitazione o la disabilitazione del robot, dopo l'accensione il robot è abilitato automaticamente di default
    * @param  [in] state  0-disabilita, 1-abilita
    * @return  Codice errore
    */
    int RobotEnable(int state); 

Controllare Passaggio Modalità Manuale/Automatica del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Controlla il passaggio tra modalità manuale e automatica del robot
    * @param [in] mode 0-modalità automatica, 1-modalità manuale
    * @return Codice errore
    */
    int Mode(int mode);

Spegnere Sistema Operativo Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1

.. code-block:: Java
    :linenos:

    /**
    * @brief Spegne il sistema operativo del robot
    * @return Codice errore
    */
    int ShutDownRobotOS();

Impostare Parametri Reconnessione Comunicazione con il Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i parametri di riconnessione per la comunicazione con il robot
    * @param [in] enable Se abilitare, true: abilita, false: non abilitare
    * @param [in] times Numero tentativi di riconnessione
    * @param [in] period Intervallo di tempo tra riconnessioni
    * @return Codice errore
    */
    int SetReconnectParam(boolean enable, int times, int period);

Inizializzare Parametri Log
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizializza i parametri del log
    * @param [in] logType Modalità di output, DIRECT-output diretto; BUFFER-output bufferizzato; ASYNC-output asincrono
    * @param [in] logLevel Livello di filtro log, ERROR-errore; WARNING-avviso; INFO-informazione; DEBUG-debug
    * @param [in] filePath Percorso salvataggio file, es. "D://Log/"
    * @param [in] saveFileNum Numero file da salvare, i file che superano sia il numero di file salvati che i giorni di salvataggio saranno eliminati
    * @param [in] saveDays Giorni di salvataggio file, i file che superano sia il numero di file salvati che i giorni di salvataggio saranno eliminati
    * @return Codice errore
    */
    int LoggerInit(FrLogType logType, FrLogLevel logLevel, String filePath, int saveFileNum, int saveDays)

Impostare Livello di Filtro Log
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il livello di filtro del log
    * @param [in] logLevel Livello di filtro log, ERROR-errore; WARNING-avviso; INFO-informazione; DEBUG-debug
    * @return Codice errore
    */
    int SetLoggerLevel(FrLogLevel logLevel)

Esempio di Codice Controllo Base Robot
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("Connessione Rpc success");
        }
        else
        {
            System.out.println("Connessione Rpc fail");
            return ;
        }
        String[] ip={""};
        String version = "";
        version=robot.GetSDKVersion();
        System.out.println("SDK version : " + version);
        int rtn = robot.GetControllerIP(ip);
        System.out.println("controller ip : " +  ip[0] + "  " + rtn);
        robot.Mode(1);//1-modalità manuale  0-modalità automatica
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);//entra in modalità trascinamento
        robot.Sleep(1000);
        ROBOT_STATE_PKG pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        robot.Sleep(1000);
        robot.DragTeachSwitch(0);//esce dalla modalità trascinamento
        robot.Sleep(1000);
        pkg = robot.GetRobotRealTimeState();
        System.out.println("drag state : " + pkg.robot_state);
        
        if (pkg.robot_state ==4){
           System.out.println("modalità trascinamento");
        }else {
           System.out.println("non in modalità trascinamento");
        }
    }

Ottenere Versione Software Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene la versione software del robot
    * @param [out] robotModel Modello robot
    * @param [out] webVersion Versione web
    * @param [out] controllerVersion Versione controllore
    * @return Codice errore 
    */
    int GetSoftwareVersion(String robotModel, String webVersion, String controllerVersion);

Ottenere Versione Hardware Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene la versione hardware del robot
    * @param [out] ctrlBoxBoardVersion Versione hardware scheda principale del cabinet di controllo
    * @param [out] driver1Version Versione hardware azionamento 1
    * @param [out] driver2Version Versione hardware azionamento 2
    * @param [out] driver3Version Versione hardware azionamento 3
    * @param [out] driver4Version Versione hardware azionamento 4
    * @param [out] driver5Version Versione hardware azionamento 5
    * @param [out] driver6Version Versione hardware azionamento 6
    * @param [out] endBoardVersion Versione hardware scheda terminale
    * @return Codice errore 
    */
    int GetHardwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Ottenere Versione Firmware Robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene la versione firmware del robot
    * @param [out] ctrlBoxBoardVersion Versione firmware scheda principale del cabinet di controllo
    * @param [out] driver1Version Versione firmware azionamento 1
    * @param [out] driver2Version Versione firmware azionamento 2
    * @param [out] driver3Version Versione firmware azionamento 3
    * @param [out] driver4Version Versione firmware azionamento 4
    * @param [out] driver5Version Versione firmware azionamento 5
    * @param [out] driver6Version Versione firmware azionamento 6
    * @param [out] endBoardVersion Versione firmware scheda terminale
    * @return Codice errore 
    */
    int GetFirmwareVersion(String ctrlBoxBoardVersion, String driver1Version, String driver2Version, String driver3Version,
                                          String driver4Version, String driver5Version, String driver6Version, String endBoardVersion);

Esempio di Codice Ottenimento Versioni Software/Firmware Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//imposta numero tentativi di riconnessione, intervallo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("Connessione Rpc success");
        }
        else
        {
            System.out.println("Connessione Rpc fail");
            return ;
        }
        String ctrlBoxBoardVersion = "";
        String driver1Version = "";
        String driver2Version = "";
        String driver3Version = "";
        String driver4Version = "";
        String driver5Version = "";
        String driver6Version = "";
        String endBoardVersion = "";
        robot.GetHardwareVersion(ctrlBoxBoardVersion ,driver1Version,  driver2Version,  driver3Version,
                 driver4Version,  driver5Version,  driver6Version,  endBoardVersion);

        robot.GetFirmwareVersion(ctrlBoxBoardVersion, driver1Version, driver2Version, driver3Version,
                driver4Version, driver5Version, driver6Version, endBoardVersion);
    }