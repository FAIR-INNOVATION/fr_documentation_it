Fondamenti del robot
===============================

.. toctree:: 
    :maxdepth: 5

Istanziazione del robot
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Costruttore della classe dell'interfaccia del robot
    */
    Robot(); 

Stabilire la comunicazione con il controller
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Stabilire la comunicazione con il controller del robot
    * @param  [in] ip  Indirizzo IP del controller, predefinito di fabbrica: 192.168.58.2
    * @return Codice di errore
    */
    int RPC(string ip);

Interrompere la comunicazione con il robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Interrompere la comunicazione con il controller del robot 
    * @return Codice di errore 
    */ 
    int CloseRPC(); 

Interrogare il numero di versione dell'SDK
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Interrogare il numero di versione dell'SDK 
    * @param [out] version Numero di versione dell'SDK 
    * @return Codice di errore 
    */  
    int GetSDKVersion(ref string version);

Ottenere l'IP del controller
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere l'IP del controller
    * @param  [out] ip  IP del controller
    * @return  Codice di errore
    */
    int GetControllerIP(ref string ip);

Controllare l'ingresso o l'uscita del robot dalla modalità di insegnamento a trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controllare l'ingresso o l'uscita del robot dalla modalità di insegnamento a trascinamento
    * @param  [in] state 0-Uscire dalla modalità di insegnamento a trascinamento, 1-Entrare nella modalità di insegnamento a trascinamento
    * @return  Codice di errore
    */
    int DragTeachSwitch(byte state);

Verificare se il robot è in modalità trascinamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Verificare se il robot è in modalità di insegnamento a trascinamento
    * @param  [out] state 0-Non in modalità di insegnamento a trascinamento, 1-In modalità di insegnamento a trascinamento
    * @return  Codice di errore
    */
    int IsInDragTeach(ref byte state); 

Controllare l'abilitazione o la disabilitazione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Controllare l'abilitazione o la disabilitazione del robot. Dopo l'accensione, il robot viene automaticamente abilitato per impostazione predefinita.
    * @param  [in] state  0-Disabilitazione, 1-Abilitazione
    * @return  Codice di errore
    */
    int RobotEnable(byte state); 

Controllare il cambio di modalità manuale/automatica del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Controllare il cambio di modalità manuale/automatica del robot
    * @param [in] mode 0-Modalità automatica, 1-Modalità manuale
    * @return Codice di errore
    */
    int Mode(int mode);

Spegnere il sistema operativo del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Spegnere il sistema operativo del robot
    * @return Codice di errore
    */
    int ShutDownRobotOS();

Esempio di codice
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgse)
    {   
        int rtn = robot.ShutDownRobotOS();
        Console.WriteLine($"ShutDownRobotOS rtn is {rtn}");
    }

Impostare i parametri di riconnessione per la comunicazione con il robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare i parametri di riconnessione per la comunicazione con il robot
    * @param [in] enable Se attivare true-Abilitato, false-Non abilitato
    * @param [in] times Numero di tentativi di riconnessione
    * @param [in] period Intervallo di tempo per la riconnessione (millisecondi)
    */
    void SetReconnectParam(bool enable, int times, int period);

Esempio di codice
+++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnStandard_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true, 100, 20000);// Parametri di riconnessione in caso di interruzione
        robot.RPC("192.168.58.2"); 

        string ip = "";
        string version = "";
        byte state = 0;

        robot.GetSDKVersion(ref version);
        Console.WriteLine($"SDK version : {version}");
        robot.GetControllerIP(ref ip);
        Console.WriteLine($"controller ip : {ip}");

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        int rtn = robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.DragTeachSwitch(0);
        Thread.Sleep(1000);
        robot.IsInDragTeach(ref state);
        Console.WriteLine($"drag state : {state}");
        Thread.Sleep(3000);
        robot.RobotEnable(0);
        Thread.Sleep(3000);
        robot.RobotEnable(1);

        robot.Mode(0);
        Thread.Sleep(1000);
        robot.Mode(1);
    }

Inizializzare i parametri del log
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inizializzare i parametri del log
    * @param [in] logType：Modalità di output，DIRECT-Output diretto；BUFFER-Output bufferizzato；ASYNC-Output asincrono
    * @param [in] logLevel：Livello di filtraggio del log，ERROR-Errore；WARNING-Avviso；INFO-Informazione；DEBUG-Debug
    * @param [in] filePath: Percorso di salvataggio del file，es. “D://Log/”
    * @param [in] saveFileNum：Numero di file da salvare，i file che superano sia il numero di file salvati che i giorni di salvataggio verranno eliminati
    * @param [in] saveDays: Giorni di salvataggio del file，i file che superano sia il numero di file salvati che i giorni di salvataggio verranno eliminati
    * @return Codice di errore
    */
    int LoggerInit(FrLogType logType = FrLogType.DIRECT, FrLogLevel logLevel = FrLogLevel.INFO, string filePath = "", int saveFileNum = 10, int saveDays = 10);

Impostare il livello di filtraggio del log
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostare il livello di filtraggio del log
    * @param [in] logLevel: Livello di filtraggio del log，ERROR-Errore；WARNING-Avviso；INFO-Informazione；DEBUG-Debug
    * @return Codice di errore
    */
    int SetLoggerLevel(FrLogLevel logLevel);

Ottenere la versione del software del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere le informazioni sulla versione del software del robot
    * @param [out] robotModel Modello del robot
    * @param [out] webVersion Versione web
    * @param [out] controllerVersion Versione del controller
    * @return Codice di errore 
    */ 
    int GetSoftwareVersion(ref string robotModel, ref string webVersion, ref string controllerVersion);
    
Ottenere la versione hardware del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere le informazioni sulla versione hardware del robot
    * @param [out] ctrlBoxBoardVersion Versione hardware della scheda del quadro di controllo
    * @param [out] driver1Version Versione hardware dell'azionamento 1
    * @param [out] driver1Version Versione hardware dell'azionamento 2
    * @param [out] driver1Version Versione hardware dell'azionamento 3
    * @param [out] driver1Version Versione hardware dell'azionamento 4
    * @param [out] driver1Version Versione hardware dell'azionamento 5
    * @param [out] driver1Version Versione hardware dell'azionamento 6
    * @param [out] endBoardVersion Versione hardware della scheda finale
    * @return Codice di errore 
    */ 
    int GetHardwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Ottenere la versione del firmware del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere le informazioni sulla versione del firmware del robot
    * @param [out] ctrlBoxBoardVersion Versione firmware della scheda del quadro di controllo
    * @param [out] driver1Version Versione firmware dell'azionamento 1
    * @param [out] driver1Version Versione firmware dell'azionamento 2
    * @param [out] driver1Version Versione firmware dell'azionamento 3
    * @param [out] driver1Version Versione firmware dell'azionamento 4
    * @param [out] driver1Version Versione firmware dell'azionamento 5
    * @param [out] driver1Version Versione firmware dell'azionamento 6
    * @param [out] endBoardVersion Versione firmware della scheda finale
    * @return Codice di errore 
    */ 
    int GetFirmwareVersion(ref string ctrlBoxBoardVersion, ref string driver1Version, ref string driver2Version, ref string driver3Version,ref string driver4Version, ref string driver5Version, ref string driver6Version, ref string endBoardVersion);

Esempio di codice
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnGetVersions_Click(object sender, EventArgs e)
    {
        string[] ver = new string[20];
        int rtn = 0;
        rtn = robot.GetSoftwareVersion(ref ver[0], ref ver[1], ref ver[2]);
        rtn = robot.GetHardwareVersion(ref ver[3], ref ver[4], ref ver[5], ref ver[6], ref ver[7], ref ver[8], ref ver[9], ref ver[10]);
        rtn = robot.GetFirmwareVersion(ref ver[11], ref ver[12], ref ver[13], ref ver[14], ref ver[15], ref ver[16], ref ver[17], ref ver[18]);
        Console.WriteLine($"robotmodel  is: {ver[0]}");
        Console.WriteLine($"webVersion  is: {ver[1]}");
        Console.WriteLine($"controllerVersion  is: {ver[2]}");
        Console.WriteLine($"Hard ctrlBox Version  is: {ver[3]}");
        Console.WriteLine($"Hard driver1 Version  is: {ver[4]}");
        Console.WriteLine($"Hard driver2 Version  is: {ver[5]}");
        Console.WriteLine($"Hard driver3 Version  is: {ver[6]}");
        Console.WriteLine($"Hard driver4 Version  is: {ver[7]}");
        Console.WriteLine($"Hard driver5 Version  is: {ver[8]}");
        Console.WriteLine($"Hard driver6 Version  is: {ver[9]}");
        Console.WriteLine($"Hard end Version  is: {ver[10]}");
        Console.WriteLine($"Firm ctrlBox Version  is: {ver[11]}");
        Console.WriteLine($"Firm driver1 Version  is: {ver[12]}");
        Console.WriteLine($"Firm driver2 Version  is: {ver[13]}");
        Console.WriteLine($"Firm driver3 Version  is: {ver[14]}");
        Console.WriteLine($"Firm driver4 Version  is: {ver[15]}");
        Console.WriteLine($"Firm driver5 Version  is: {ver[16]}");
        Console.WriteLine($"Firm driver6 Version  is: {ver[17]}");
        Console.WriteLine($"Firm end Version  is: {ver[18]}");
    }