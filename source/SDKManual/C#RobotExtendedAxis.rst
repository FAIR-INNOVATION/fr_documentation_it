Assi estesi
=================

.. toctree::
    :maxdepth: 5

Imposta i parametri dell'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta i parametri dell'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] servoCompany Produttore servazionatore, 1-Dinatek
    * @param [in] servoModel Modello servazionatore, 1-FD100-750C
    * @param [in] servoSoftVersion Versione software servazionatore, 1-V1.0
    * @param [in] servoResolution Risoluzione encoder
    * @param [in] axisMechTransRatio Rapporto di trasmissione meccanico
    * @return Codice di errore
    */
    int AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);
    
Ottieni i parametri di configurazione dell'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni i parametri di configurazione dell'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [out] servoCompany Produttore servazionatore, 1-Dinatek
    * @param [out] servoModel Modello servazionatore, 1-FD100-750C
    * @param [out] servoSoftVersion Versione software servazionatore, 1-V1.0
    * @param [out] servoResolution Risoluzione encoder
    * @param [out] axisMechTransRatio Rapporto di trasmissione meccanico
    * @return Codice di errore
    */
    int AuxServoGetParam(int servoId, ref int servoCompany, ref int servoModel, ref int servoSoftVersion, ref int servoResolution, ref double axisMechTransRatio);
    
Imposta abilita/disabilita per l'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta abilita/disabilita per l'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] status Stato abilitazione, 0-Disabilita, 1-Abilita
    * @return Codice di errore
    */
    int AuxServoEnable(int servoId, int status);
        
Imposta la modalità di controllo per l'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la modalità di controllo per l'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] mode Modalità di controllo, 0-Modalità posizione, 1-Modalità velocità
    * @return Codice di errore
    */
    int AuxServoSetControlMode(int servoId, int mode);

Imposta la posizione target per l'asse esteso 485 (modalità posizione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la posizione target per l'asse esteso 485 (modalità posizione)
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] pos Posizione target, mm o °
    * @param [in] speed Velocità target, mm/s o °/s
    * @return Codice di errore
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed);

Imposta la velocità target per l'asse esteso 485 (modalità velocità)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la velocità target per l'asse esteso 485 (modalità velocità)
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] speed Velocità target, mm/s o °/s
    * @return Codice di errore
    */
    int AuxServoSetTargetSpeed(int servoId, double speed);
    
Imposta la coppia target per l'asse esteso 485 (modalità coppia)--Non ancora disponibile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la coppia target per l'asse esteso 485 (modalità coppia)--Non ancora disponibile
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] torque Coppia target, Nm
    * @return Codice di errore
    */
    int AuxServoSetTargetTorque(int servoId, double torque);

Imposta l'homing per l'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta l'homing per l'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [in] mode Modalità homing, 1-Homing posizione corrente; 2-Homing finecorsa negativo; 3-Homing finecorsa positivo
    * @param [in] searchVel Velocità ricerca zero, mm/s o °/s
    * @param [in] latchVel Velocità aggancio zero, mm/s o °/s
    * @return Codice di errore
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);
        
Cancella le informazioni di errore dell'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Cancella le informazioni di errore dell'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @return Codice di errore
    */
    int AuxServoClearError(int servoId);

Ottieni lo stato del servomotore dell'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni lo stato del servomotore dell'asse esteso 485
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @param [out] servoErrCode Codice errore servazionatore
    * @param [out] servoState Stato servazionatore  bit0:0-Non abilitato; 1-Abilitato;  bit1:0-Non in movimento; 1-In movimento;  bit2 0-Finecorsa positivo non attivato; 1-Finecorsa positivo attivato; bit3 0-Finecorsa negativo non attivato; 1-Finecorsa negativo attivato; bit4 0-Posizionamento non completato; 1-Posizionamento completato;  bit5: 0-Homing non completato; 1-Homing completato
    * @param [out] servoPos Posizione corrente servomotore mm o °
    * @param [out] servoSpeed Velocità corrente servomotore mm/s o °/s
    * @param [out] servoTorque Coppia corrente servomotore Nm
    * @return Codice di errore
    */
    int AuxServoGetStatus(int servoId, ref int servoErrCode, ref int servoState, ref double servoPos, ref double servoSpeed, ref double servoTorque);
    
Imposta il numero dell'asse per i dati dell'asse esteso 485 nel feedback di stato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.6
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta il numero dell'asse per i dati dell'asse esteso 485 nel feedback di stato
    * @param [in] servoId ID servazionatore, intervallo [1-15], corrisponde all'ID slave
    * @return Codice di errore
    */
    int AuxServosetStatusID(int servoId);

Imposta le accelerazioni/decelerazioni di movimento per l'asse esteso 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta le accelerazioni/decelerazioni di movimento per l'asse esteso 485
    * @param [in] acc Accelerazione di movimento asse esteso 485
    * @param [in] dec Decelerazione di movimento asse esteso 485
    * @return  Codice di errore
    */
    int AuxServoSetAcc(double acc, double dec);

Imposta le accelerazioni/decelerazioni di arresto di emergenza per l'asse esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta le accelerazioni/decelerazioni di arresto di emergenza per l'asse esteso 485
    * @param [in] acc Accelerazione arresto emergenza asse esteso 485
    * @param [in] dec Decelerazione arresto emergenza asse esteso 485
    * @return  Codice di errore
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec);

Ottieni le accelerazioni/decelerazioni di movimento per l'asse esteso 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Ottieni le accelerazioni/decelerazioni di movimento per l'asse esteso 485
    * @param [out] acc Accelerazione di movimento asse esteso 485
    * @param [out] dec Decelerazione di movimento asse esteso 485
    * @return  Codice di errore
    */
    int AuxServoGetAcc(ref double acc, ref double dec);

Ottieni le accelerazioni/decelerazioni di arresto di emergenza per l'asse esteso 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: C#
    :linenos:

    /**
    * @brief Ottieni le accelerazioni/decelerazioni di arresto di emergenza per l'asse esteso 485
    * @param [out] acc Accelerazione arresto emergenza asse esteso 485
    * @param [out] dec Decelerazione arresto emergenza asse esteso 485
    * @return  Codice di errore
    */
    int AuxServoGetEmergencyStopAcc(ref double acc, ref double dec);

Esempio di codice per il controllo dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
    :linenos:

    private void button64_Click(object sender, EventArgs e)
    {
        int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        int servoCompany = 0;
        int servoModel = 0;
        int servoSoftVersion = 0;
        int servoResolution = 0;
        double axisMechTransRatio = 0;
        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
        Console.WriteLine($"AuxServoSetParam is: {retval}");

        retval = robot.AuxServoGetParam(1, ref servoCompany, ref servoModel, ref servoSoftVersion, ref servoResolution, ref axisMechTransRatio);
        Console.WriteLine($"servoCompany {servoCompany}\n" +
            $"servoModel {servoModel}\n" +
            $"servoSoftVersion {servoSoftVersion}\n" +
            $"servoResolution {servoResolution}\n" +
            $"axisMechTransRatio {axisMechTransRatio}\n");

        retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
        Console.WriteLine($"AuxServoSetParam is: {retval}");
        Thread.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        Thread.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;
        robot.AuxServoGetEmergencyStopAcc(ref emagacc, ref emagdec);
        Console.WriteLine($"emergency acc is {emagacc}  dec is {emagdec}");
        robot.AuxServoGetAcc(ref acc, ref dec);
        Console.WriteLine($"acc is {acc}  dec is {dec}");

        robot.AuxServoSetControlMode(1, 0);
        Thread.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        Console.WriteLine($"AuxServoEnable disenable {retval}");
        Thread.Sleep(1000);
        int servoerrcode = 0;
        int servoErrCode = 0;
        int servoState = 0;
        double servoPos = 0;
        double servoSpeed = 0;
        double servoTorque = 0;
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoEnable(1, 1);
        Console.WriteLine($"AuxServoEnable enable {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoState {servoState}");
        Thread.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1);
        Console.WriteLine($"AuxServoHoming {retval}");
        Thread.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30);
        Console.WriteLine($"AuxServoSetTargetPos {retval}");
        Thread.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, ref servoErrCode, ref servoState, ref servoPos, ref servoSpeed, ref servoTorque);
        Console.WriteLine($"AuxServoGetStatus servoSpeed {servoSpeed}");
        Thread.Sleep(8000);

        robot.AuxServoSetControlMode(1, 1);
        Thread.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        Thread.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        Thread.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        Thread.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);
    }

Configurazione parametri comunicazione UDP per asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Configurazione parametri comunicazione UDP per asse esteso
    * @param [in] ip Indirizzo IP PLC
    * @param [in] port	Numero porta
    * @param [in] period	Periodo comunicazione (ms, default 2, non modificare)
    * @param [in] lossPkgTime	Tempo rilevamento perdita pacchetti (ms)
    * @param [in] lossPkgNum	Numero pacchetti persi
    * @param [in] disconnectTime	Durata conferma disconnessione comunicazione
    * @param [in] reconnectEnable	Abilita riconnessione automatica in caso di disconnessione 0-Disabilita 1-Abilita
    * @param [in] reconnectPeriod	Intervallo periodo riconnessione (ms)
    * @param [in] reconnectNum	Numero tentativi riconnessione
    * @param [in] selfConnect Ricostruisci connessione automaticamente dopo riavvio da spegnimento; 0-Non costruire connessione; 1-Costruisci connessione
    * @return Codice di errore
    */
    int ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect);
         
Ottenere la Configurazione dei Parametri di Comunicazione UDP per Assi di Estensione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ottiene i parametri di comunicazione UDP per assi di estensione
    * @param [out] ip Indirizzo IP del PLC
    * @param [out] port	Numero di porta
    * @param [out] period	Periodo di comunicazione (ms, default è 2, non modificare questo parametro)
    * @param [out] lossPkgTime	Tempo di rilevamento perdita pacchetti (ms)
    * @param [out] lossPkgNum	Numero di perdite di pacchetti
    * @param [out] disconnectTime	Durata di conferma disconnessione comunicazione
    * @param [out] reconnectEnable	Abilitazione riconnessione automatica alla disconnessione della comunicazione 0-disabilitato 1-abilitato
    * @param [out] reconnectPeriod	Intervallo di riconnessione (ms)
    * @param [out] reconnectNum	Numero di tentativi di riconnessione
    * @param [out] selfConnect	Riconnessione automatica dopo riavvio del box di controllo; 0-nessuna riconnessione; 1-riconnessione
    * @return Codice di errore
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)
        
Carica comunicazione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Carica comunicazione UDP
    * @return Codice di errore
    */
    int ExtDevLoadUDPDriver();

Scarica comunicazione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Scarica comunicazione UDP
    * @return Codice di errore
    */
    int ExtDevUnloadUDPDriver();

Ripristina connessione dopo disconnessione anomala della comunicazione UDP per asse esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ripristina connessione dopo disconnessione anomala della comunicazione UDP per asse esteso
    * @return Codice di errore
    */
    int ExtDevUDPClientComReset();

Chiudi comunicazione dopo disconnessione anomala della comunicazione UDP per asse esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Chiudi comunicazione dopo disconnessione anomala della comunicazione UDP per asse esteso
    * @return Codice di errore
    */
    int ExtDevUDPClientComClose();

Configurazione parametri asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Configurazione parametri asse esteso UDP
    * @param [in] axisID Numero asse
    * @param [in] axisType Tipo asse esteso 0-Traslazionale; 1-Rotazionale
    * @param [in] axisDirection Direzione asse esteso 0-Positiva; 1-Negativa 
    * @param [in] axisMax Posizione massima asse esteso mm
    * @param [in] axisMin Posizione minima asse esteso mm
    * @param [in] axisVel Velocità mm/s
    * @param [in] axisAcc Accelerazione mm/s2
    * @param [in] axisLead Passo vite mm
    * @param [in] encResolution Risoluzione encoder
    * @param [in] axisOffect Offset asse esteso punto di inizio giunto
    * @param [in] axisCompany Produttore azionamento 1-Hichain; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Modello azionamento 1-Hichain-SV-XD3EA040L-E, 2-Hichain-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Tipo encoder  0-Incrementale; 1-Assoluto
    * @return Codice di errore
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Imposta la posizione di installazione dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta la posizione di installazione dell'asse esteso
    * @param [in] installType 0-Robot installato sull'asse esterno, 1-Robot installato all'esterno dell'asse esterno
    * @return Codice di errore
    */
    int SetRobotPosToAxis(int installType);

Imposta la configurazione dei parametri DH del sistema asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta la configurazione dei parametri DH del sistema asse esteso
    * @param [in]  axisConfig Configurazione asse esterno, 0-Corsia lineare a singolo grado di libertà, 1-Posizionatore a due gradi di libertà a L, 2-Tre gradi di libertà, 3-Quattro gradi di libertà, 4-Posizionatore a singolo grado di libertà
    * @param [in]  axisDHd1 Parametro DH asse esterno d1 mm
    * @param [in]  axisDHd2 Parametro DH asse esterno d2 mm
    * @param [in]  axisDHd3 Parametro DH asse esterno d3 mm
    * @param [in]  axisDHd4 Parametro DH asse esterno d4 mm
    * @param [in]  axisDHa1 Parametro DH asse esterno a1 mm
    * @param [in]  axisDHa2 Parametro DH asse esterno a2 mm
    * @param [in]  axisDHa3 Parametro DH asse esterno a3 mm
    * @param [in]  axisDHa4 Parametro DH asse esterno a4 mm
    * @return Codice di errore
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Abilita asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Abilita asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] status 0-Disabilita; 1-Abilita
    * @return Codice di errore
    */
    int ExtAxisServoOn(int axisID, int status);

Homing asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Homing asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] mode Modalità homing 0-Homing posizione corrente, 1-Homing finecorsa negativo, 2-Homing finecorsa positivo
    * @param [in] searchVel Velocità ricerca zero (mm/s)
    * @param [in] latchVel Velocità aggancio zero (mm/s)
    * @return Codice di errore
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Avvia jog asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Avvia jog asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] direction Direzione rotazione 0-Negativa; 1-Positiva
    * @param [in] vel Velocità (mm/s)
    * @param [in] acc Accelerazione (mm/s2)
    * @param [in] maxDistance Massima distanza jog
    * @return Codice di errore
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Arresta jog asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Arresta jog asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @return Codice di errore
    */
    int ExtAxisStopJog(int axisID);

Esempio di codice per la configurazione e il jog dell'asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnJog_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        rtn = robot.ExtAxisSetHoming(1, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 1 rtnn is  " + rtn);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming 2 rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 2 rtn is " + rtn);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(1);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(1, 0);

        Thread.Sleep(3000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        Thread.Sleep(1000);
        robot.ExtAxisStopJog(2);
        Thread.Sleep(3000);
        robot.ExtAxisServoOn(2, 0);
        Thread.Sleep(3000);
        robot.ExtDevUnloadUDPDriver();
    }

Imposta il punto di riferimento del sistema di coordinate dell'asse esteso - metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta il punto di riferimento del sistema di coordinate dell'asse esteso - metodo a quattro punti
    * @param [in]  pointNum Numero punto[1-4]
    * @return Codice di errore
    */
    int ExtAxisSetRefPoint(int pointNum);

Calcola il sistema di coordinate dell'asse esteso - metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Calcola il sistema di coordinate dell'asse esteso - metodo a quattro punti
    * @param [out]  coord Valore sistema di coordinate
    * @return Codice di errore
    */
    int ExtAxisComputeECoordSys(DescPose& coord);

Applica il sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Applica il sistema di coordinate dell'asse esteso
    * @param [in]  applyAxisId Numero asse esteso bit0-bit3 corrisponde a numero asse esteso 1-4, es. applicare assi estesi 1 e 3, allora è 0b 0000 0101; cioè 5
    * @param [in]  axisCoordNum Numero sistema di coordinate asse esteso
    * @param [in]  coord Valore sistema di coordinate
    * @param [in]  calibFlag Flag calibrazione 0-No, 1-Sì
    * @return Codice di errore
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Imposta la posa del punto di riferimento di calibrazione nel sistema di coordinate dell'estremità del posizionatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta la posa del punto di riferimento di calibrazione nel sistema di coordinate dell'estremità del posizionatore
    * @param [in] pos Valore di posa
    * @return Codice di errore
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Impostazione punto di riferimento del sistema di coordinate del posizionatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Impostazione punto di riferimento del sistema di coordinate del posizionatore
    * @param [in]  pointNum Numero punto[1-4]
    * @return Codice di errore
    */
    int PositionorSetRefPoint(int pointNum);

Calcolo sistema di coordinate del posizionatore - metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Calcolo sistema di coordinate del posizionatore - metodo a quattro punti
    * @param [out] coord Valore sistema di coordinate
    * @return Codice di errore
    */
    int PositionorComputeECoordSys(DescPose& coord);

Ottieni il sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni il sistema di coordinate dell'asse esteso
    * @param [out] coord Sistema di coordinate asse esteso
    * @return Codice di errore
    */
    int ExtAxisGetCoord(ref DescPose coord);

Esempio di codice per la calibrazione del sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        int rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5,1);
        Console.WriteLine("ExtDevSetUDPComParam rtn is " + rtn);
        string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        rtn = robot.ExtDevGetUDPComParam(ref ip, ref port, ref period, ref lossPkgTime, ref lossPkgNum, ref disconnectTime, ref reconnectEnable, ref reconnectPeriod, ref reconnectNum);
        string param = "\nip " + ip + "\nport " + port.ToString() + "\nperiod  " + period.ToString() + "\nlossPkgTime " + lossPkgTime.ToString() + "\nlossPkgNum  " + lossPkgNum.ToString() + "\ndisConntime  " + disconnectTime.ToString() + "\nreconnecable  " + reconnectEnable.ToString() + "\nreconnperiod  " + reconnectPeriod.ToString() + "\nreconnnun  " + reconnectNum.ToString();
        Console.WriteLine("ExtDevGetUDPComParam rtn is " + rtn + param);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Console.WriteLine("ExtAxisSetHoming rtnn is  " + rtn);

        Thread.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        Console.WriteLine("SetRobotPosToAxis rtn is " + rtn);
        rtn = robot.SetAxisDHParaConfig(1, 128.5f, 206.4f, 0, 0, 0, 0, 0, 0);
        Console.WriteLine("SetAxisDHParaConfig rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444f, 262144, 200, 1, 0, 0);
        Console.WriteLine("ExtAxisParamConfig axis 1 rtn is " + rtn);

        DescPose toolCoord = new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe = new JointPos(115.193f, -96.149f, 92.489f, -87.068f, -89.15f, -83.488f);
        JointPos j1 = new JointPos(117.559f, -92.624f, 100.329f, -96.909f, -94.057f, -83.488f);
        JointPos j2 = new JointPos(112.239f, -90.096f, 99.282f, -95.909f, -89.824f, -83.488f);
        JointPos j3 = new JointPos(110.839f, -83.473f, 93.166f, -89.22f, -90.499f, -83.487f);
        JointPos j4 = new JointPos(107.935f, -83.572f, 95.424f, -92.873f, -87.933f, -83.488f);

        DescPose descSafe = new DescPose();
        DescPose desc1 = new DescPose();
        DescPose desc2 = new DescPose();
        DescPose desc3 = new DescPose();
        DescPose desc4 = new DescPose();
        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin( jSafe,  ref descSafe);
        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        robot.GetForwardKin( j1, ref desc1);
        robot.MoveJ( j1,  desc1, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        Thread.Sleep(2000);

        DescPose actualTCPPos = new DescPose();
        robot.GetActualTCPPose(0, ref actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        Console.WriteLine("PositionorSetRefPoint 1 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j2, ref desc2);
        rtn = robot.MoveJ( j2,  desc2, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(2);
        Console.WriteLine("PositionorSetRefPoint 2 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin( j3, ref desc3);
        robot.MoveJ( j3,  desc3, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.PositionorSetRefPoint(3);
        Console.WriteLine("PositionorSetRefPoint 3 rtn is " + rtn);
        Thread.Sleep(2000);

        robot.MoveJ( jSafe,  descSafe, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        Thread.Sleep(1000);
        robot.GetForwardKin(j4, ref desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        Console.WriteLine("PositionorSetRefPoint 4 rtn is " + rtn);
        Thread.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(ref axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        Console.WriteLine("PositionorComputeECoordSys rtn is {0} {1} {2} {3} {4} {5}", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
        Console.WriteLine("ExtAxisActiveECoordSys rtn is " + rtn);
    }

Movimento asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4

.. code-block:: C#
    :linenos:

    /**
    * @brief Movimento asse esteso UDP
    * @param [in] pos Posizione target
    * @param [in] ovl Percentuale velocità
    * @param [in] blend Parametro smooth (mm o ms)
    * @return Codice di errore
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend=-1);

Esempio di codice per il movimento dell'asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void button66_Click(object sender, EventArgs e)
    {
        ExaxisPos axisPos;
        axisPos.ePos[0] = 20;
        axisPos.ePos[1] = 0;
        axisPos.ePos[2] = 0;
        axisPos.ePos[3] = 0;
        robot.ExtAxisMove(axisPos, 50);
    }

Movimento sincrono asse esteso UDP con giunti del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Movimento sincrono asse esteso UDP con giunti del robot
    * @param [in] joint_pos Posizione target giunti, unità deg
    * @param [in] desc_pos Posa cartesiana target
    * @param [in] tool Numero coordinata utensile, intervallo[0~14]
    * @param [in] user Numero coordinata pezzo, intervallo[0~14]
    * @param [in] vel Percentuale velocità, intervallo[0~100]
    * @param [in] acc Percentuale accelerazione, intervallo[0~100], non ancora disponibile
    * @param [in] ovl Fattore di scala velocità, intervallo[0~100]
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] blendT [-1.0]-Movimento fino a posizione (bloccante), [0~500.0]-Tempo smooth (non bloccante), unità ms
    * @param [in] offset_flag  0-Nessun offset, 1-Offset sistema base/pezzo, 2-Offset sistema utensile
    * @param [in] offset_pos  Quantità offset posa
    * @return  Codice di errore
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveJ_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

        //1. Calibra e applica il sistema di coordinate utensile del robot, puoi usare il metodo a quattro o sei punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
        //    int SetToolPoint(int point_num);  //Imposta punto riferimento utensile - metodo a sei punti
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile
        //    int SetTcp4RefPoint(int point_num);    //Imposta punto riferimento utensile - metodo a quattro punti
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcola sistema coordinate utensile - metodo a quattro punti
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Imposta e applica sistema coordinate utensile
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Imposta e applica lista sistemi coordinate utensile

        //2. Imposta i parametri di comunicazione UDP e carica la comunicazione UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Imposta i parametri dell'asse esteso, inclusi tipo asse esteso, parametri azionamento asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1);  //Posizione di installazione asse esteso
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri azionamento servomotore, questo esempio è per un posizionatore monoasse, quindi è necessario impostare solo i parametri di un azionamento. Se scegli un tipo di asse esteso con più assi, devi impostare i parametri dell'azionamento per ogni asse

        //4. Abilita e fai homing dell'asse selezionato
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Effettua calibrazione e applicazione del sistema di coordinate dell'asse esteso (Nota: le interfacce di calibrazione per posizionatore e corsia lineare sono diverse, di seguito sono le interfacce per il posizionatore)
        DescPose pos = new DescPose(/* Inserisci le coordinate del tuo punto di calibrazione */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* È necessario calibrare l'asse esteso utilizzando quattro punti in posizioni diverse, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
        DescPose coord = new DescPose( );
        robot.PositionorComputeECoordSys(ref coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Applica il risultato di calibrazione al sistema di coordinate dell'asse esteso

        //6. Calibra il sistema di coordinate del pezzo sull'asse esteso, avrai bisogno delle seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Registra il punto di partenza del tuo movimento articolare sincrono
        DescPose startdescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos startjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto di partenza dell'asse esteso */);

        //8. Registra le coordinate del punto finale del tuo movimento articolare sincrono
        DescPose enddescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos endjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto finale dell'asse esteso */);

        //9. Scrivi il programma di movimento sincrono
        //Muoviti al punto di partenza, assumendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Inizia movimento sincrono
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
    }

Movimento sincrono asse esteso UDP con movimento lineare del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Movimento sincrono asse esteso UDP con movimento lineare del robot
    * @param [in] joint_pos  Posizione target giunti, unità deg
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool  Numero coordinata utensile, intervallo[0~14]
    * @param [in] user  Numero coordinata pezzo, intervallo[0~14]
    * @param [in] vel  Percentuale velocità, intervallo[0~100]
    * @param [in] acc  Percentuale accelerazione, intervallo[0~100], non ancora disponibile
    * @param [in] ovl  Fattore di scala velocità, intervallo[0~100]
    * @param [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param [in] epos  Posizione asse esteso, unità mm
    * @param [in] offset_flag  0-Nessun offset, 1-Offset sistema base/pezzo, 2-Offset sistema utensile
    * @param [in] offset_pos  Quantità offset posa
    * @return Codice di errore
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveL_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Calibra e applica il sistema di coordinate utensile del robot, puoi usare il metodo a quattro o sei punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
        //    int SetToolPoint(int point_num);  //Imposta punto riferimento utensile - metodo a sei punti
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile
        //    int SetTcp4RefPoint(int point_num);    //Imposta punto riferimento utensile - metodo a quattro punti
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcola sistema coordinate utensile - metodo a quattro punti
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Imposta e applica sistema coordinate utensile
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Imposta e applica lista sistemi coordinate utensile

        //2. Imposta i parametri di comunicazione UDP e carica la comunicazione UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Imposta i parametri dell'asse esteso, inclusi tipo asse esteso, parametri azionamento asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1);  //Posizione di installazione asse esteso
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri azionamento servomotore, questo esempio è per un posizionatore monoasse, quindi è necessario impostare solo i parametri di un azionamento. Se scegli un tipo di asse esteso con più assi, devi impostare i parametri dell'azionamento per ogni asse

        //4. Abilita e fai homing dell'asse selezionato
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Effettua calibrazione e applicazione del sistema di coordinate dell'asse esteso (Nota: le interfacce di calibrazione per posizionatore e corsia lineare sono diverse, di seguito sono le interfacce per il posizionatore)
        DescPose pos = new DescPose(/* Inserisci le coordinate del tuo punto di calibrazione */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* È necessario calibrare l'asse esteso utilizzando quattro punti in posizioni diverse, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Applica il risultato di calibrazione al sistema di coordinate dell'asse esteso

        //6. Calibra il sistema di coordinate del pezzo sull'asse esteso, avrai bisogno delle seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Registra il punto di partenza del tuo movimento lineare sincrono
        DescPose startdescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos startjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto di partenza dell'asse esteso */);

        //8. Registra le coordinate del punto finale del tuo movimento lineare sincrono
        DescPose enddescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos endjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto finale dell'asse esteso */);

        //9. Scrivi il programma di movimento sincrono
        //Muoviti al punto di partenza, assumendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Inizia movimento sincrono
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
    }
    
Movimento sincrono asse esteso UDP con movimento circolare del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Movimento sincrono asse esteso UDP con movimento circolare del robot
    * @param [in] joint_pos_p  Posizione giunti punto percorso, unità deg
    * @param [in] desc_pos_p  Posa cartesiana punto percorso
    * @param [in] ptool  Numero coordinata utensile, intervallo[0~14]
    * @param [in] puser  Numero coordinata pezzo, intervallo[0~14]
    * @param [in] pvel  Percentuale velocità, intervallo[0~100]
    * @param [in] pacc  Percentuale accelerazione, intervallo[0~100], non ancora disponibile
    * @param [in] epos_p  Posizione asse esteso punto intermedio, unità mm
    * @param [in] poffset_flag  0-Nessun offset, 1-Offset sistema base/pezzo, 2-Offset sistema utensile
    * @param [in] offset_pos_p  Quantità offset posa
    * @param [in] joint_pos_t  Posizione giunti punto target, unità deg
    * @param [in] desc_pos_t  Posa cartesiana punto target
    * @param [in] ttool  Numero coordinata utensile, intervallo[0~14]
    * @param [in] tuser  Numero coordinata pezzo, intervallo[0~14]
    * @param [in] tvel  Percentuale velocità, intervallo[0~100]
    * @param [in] tacc  Percentuale accelerazione, intervallo[0~100], non ancora disponibile
    * @param [in] epos_t  Posizione asse esteso, unità mm
    * @param [in] toffset_flag  0-Nessun offset, 1-Offset sistema base/pezzo, 2-Offset sistema utensile
    * @param [in] offset_pos_t  Quantità offset posa	 
    * @param [in] ovl  Fattore di scala velocità, intervallo[0~100]
    * @param [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @return Codice di errore
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);
    
Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnSyncMoveC_Click(object sender, EventArgs e)
    {
        Robot robot = new Robot();
        robot.RPC("192.168.58.2");

    //1. Calibra e applica il sistema di coordinate utensile del robot, puoi usare il metodo a quattro o sei punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
        //    int SetToolPoint(int point_num);  //Imposta punto riferimento utensile - metodo a sei punti
        //    int ComputeTool(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile
        //    int SetTcp4RefPoint(int point_num);    //Imposta punto riferimento utensile - metodo a quattro punti
        //    int ComputeTcp4(ref DescPose tcp_pose);   //Calcola sistema coordinate utensile - metodo a quattro punti
        //    int SetToolCoord(int id, DescPose coord, int type, int install);  //Imposta e applica sistema coordinate utensile
        //    int SetToolList(int id, DescPose coord, int type, int install);   //Imposta e applica lista sistemi coordinate utensile

        //2. Imposta i parametri di comunicazione UDP e carica la comunicazione UDP
        robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
        robot.ExtDevLoadUDPDriver();

        //3. Imposta i parametri dell'asse esteso, inclusi tipo asse esteso, parametri azionamento asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1);  //Posizione di installazione asse esteso
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri azionamento servomotore, questo esempio è per un posizionatore monoasse, quindi è necessario impostare solo i parametri di un azionamento. Se scegli un tipo di asse esteso con più assi, devi impostare i parametri dell'azionamento per ogni asse

        //4. Abilita e fai homing dell'asse selezionato
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);

        //5. Effettua calibrazione e applicazione del sistema di coordinate dell'asse esteso (Nota: le interfacce di calibrazione per posizionatore e corsia lineare sono diverse, di seguito sono le interfacce per il posizionatore)
        DescPose pos = new DescPose(/* Inserisci le coordinate del tuo punto di calibrazione */);
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* È necessario calibrare l'asse esteso utilizzando quattro punti in posizioni diverse, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(ref coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1);  //Applica il risultato di calibrazione al sistema di coordinate dell'asse esteso

        //6. Calibra il sistema di coordinate del pezzo sull'asse esteso, avrai bisogno delle seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);

        //7. Registra il punto di partenza del tuo movimento circolare sincrono
        DescPose startdescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos startjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto di partenza dell'asse esteso */);

        //8. Registra le coordinate del punto finale del tuo movimento circolare sincrono
        DescPose enddescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos endjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos endexaxisPos = new ExaxisPos(/* Inserisci le coordinate del punto finale dell'asse esteso */);

        //8. Registra le coordinate del punto intermedio del tuo movimento circolare sincrono
        DescPose middescPose = new DescPose(/*Inserisci le tue coordinate*/);
        JointPos midjointPos = new JointPos(/*Inserisci le tue coordinate*/);
        ExaxisPos midexaxisPos = new ExaxisPos(/* Inserisci le coordinate dell'asse esteso al punto intermedio del movimento circolare del robot */);

        //9. Scrivi il programma di movimento sincrono
        //Muoviti al punto di partenza, assumendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);

        //Inizia movimento sincrono
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
    }

Imposta DO esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta DO esteso
    * @param [in] DONum Numero DO
    * @param [in] bOpen Interruttore true-Aperto; false-Chiuso
    * @param [in] smooth Se smooth
    * @param [in] block Se bloccante
    * @return Codice di errore
    */
    int SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);
        
Imposta AO esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta AO esteso
    * @param [in] AONum Numero AO
    * @param [in] value Valore analogico[0-4095]
    * @param [in] block Se bloccante
    * @return Codice di errore
    */
    int SetAuxAO(int AONum, double value, bool block);
            
Imposta tempo filtro ingresso DI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta tempo filtro ingresso DI esteso
    * @param [in] filterTime Tempo filtro (ms)
    * @return Codice di errore
    */
    int SetAuxDIFilterTime(int filterTime);

Imposta tempo filtro ingresso AI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Imposta tempo filtro ingresso AI esteso
    * @param [in] filterTime Tempo filtro (ms)
    * @return Codice di errore
    */
    int SetAuxAIFilterTime(int filterTime);

Attendi ingresso DI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Attendi ingresso DI esteso
    * @param [in] DINum Numero DI
    * @param [in] bOpen Interruttore 0-Chiuso; 1-Aperto
    * @param [in] time Tempo di attesa massimo (ms)
    * @param [in] errorAlarm Se continuare il movimento
    * @return Codice di errore
    */
    int WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);
    
Attendi ingresso AI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Attendi ingresso AI esteso
    * @param [in] AINum Numero AI
    * @param [in] sign 0-Maggiore di; 1-Minore di
    * @param [in] value Valore AI
    * @param [in] time Tempo di attesa massimo (ms)
    * @param [in] errorAlarm Se continuare il movimento
    * @return Codice di errore
    */
    int WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);
        
Ottieni valore DI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ottieni valore DI esteso
    * @param [in] DINum Numero DI
    * @param [in] isNoBlock Se non bloccante
    * @param [out] isOpen 0-Chiuso; 1-Aperto
    * @return Codice di errore
    */
    int GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);
            
Ottieni valore AI esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: C#
    :linenos:

    /**
    * @brief Ottieni valore AI esteso
    * @param [in] AINum Numero AI
    * @param [in] isNoBlock Se non bloccante
    * @param [in] value Valore di ingresso
    * @return Codice di errore
    */
    int GetAuxAI(int AINum, bool isNoBlock, int& value);

Esempio di codice per I/O estesi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: C#
    :linenos:

    private void btnAODO_Click(object sender, EventArgs e)
    {
        int rtn;
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            Thread.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            Thread.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            Thread.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);

        for (int i = 0; i < 20; i++)
        {
            bool curValue = false;
            rtn = robot.GetAuxDI(i, false, ref curValue);
            Console.WriteLine("DI" + i + "   " + curValue);
        }
        int curValueAI = -1;
        for (int i = 0; i < 4; i++)
        {
            rtn = robot.GetAuxAI(i, true, ref curValueAI);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);
    }

Abilita dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Abilita dispositivo mobile
    * @param enable false-Disabilita; true-Abilita
    * @return Codice di errore
    */
    int TractorEnable(bool enable);

Arresta movimento dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Arresta movimento dispositivo mobile
    * @return Codice di errore
    */
    int TractorStop();

Homing dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Homing dispositivo mobile
    * @return Codice di errore
    */
    int  TractorHoming();

Movimento lineare dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento lineare dispositivo mobile
    * @param distance Distanza movimento lineare (mm)
    * @param vel Percentuale velocità movimento lineare (0-100)
    * @return Codice di errore
    */
    int TractorMoveL(double distance, double vel);

Movimento circolare dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento circolare dispositivo mobile
    * @param radio Raggio movimento circolare (mm)
    * @param angle Angolo movimento circolare (°)
    * @param vel Percentuale velocità movimento lineare (0-100)
    * @return Codice di errore
    */
    int TractorMoveC(double radio, double angle, double vel);

Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    private void button6_Click(object sender, EventArgs e)
    {
        int rtn;
        robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10,1);
        robot.ExtDevLoadUDPDriver();
        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        Thread.Sleep(2000);
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        Thread.Sleep(2000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
        Thread.Sleep(4000);
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280f, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
        robot.TractorEnable(false);
        Thread.Sleep(2000);
        robot.TractorEnable(true);
        Thread.Sleep(2000);
        robot.TractorHoming();
        Thread.Sleep(2000);
        robot.TractorMoveL(100, 2);
        Thread.Sleep(5000);
        robot.TractorStop();
        robot.TractorMoveL(-100, 20);
        Thread.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        Thread.Sleep(10000);
        robot.TractorMoveC(300, -90, 20);
        Thread.Sleep(1000);
        robot.TractorStop();    
    }

Imposta la strategia di movimento sincrono tra asse esteso e robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    /**
    * @brief Imposta la strategia di movimento sincrono tra asse esteso e robot
    * @param strategy Strategia; 0-Con robot come principale; 1-Asse esteso e robot sincronizzati
    * @return Codice di errore
    */
    int SetExAxisRobotPlan(int strategy)

Esempio di codice per impostare la strategia di movimento sincrono tra asse esteso e robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:


    private void button94_Click(object sender, EventArgs e)
    {
        JointPos joint_pos1 = new JointPos(-22.016, -49.217, 124.714, -161.100, -85.108, -0.333);
        JointPos joint_pos2 = new JointPos(-21.083, -46.613, 110.079, -147.796, -80.757, -0.330);
        JointPos joint_pos3 = new JointPos(-25.572, -60.090, 135.397, -163.889, -82.489, -0.345);
        DescPose desc_pos1 = new DescPose(2.637, -0.001, 30.673, 178.786, -4.134, 68.326);
        DescPose desc_pos2 = new DescPose(213.812, -1.440, 47.311, 177.410, 0.166, 68.946);
        DescPose desc_pos3 = new DescPose(444.342, -12.723, 82.470, -177.701, -1.325, 65.151);   
        ExaxisPos epos1 = new ExaxisPos(0.001, 0.000, 0.000, 0.000);
        ExaxisPos epos2 = new ExaxisPos(299.977, 0.000, 0.000, 0.000);
        ExaxisPos epos3 = new ExaxisPos(399.969, 0.000, 0.000, 0.000);      
        DescPose offset_pos = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.SetExAxisRobotPlan(0);
        Console.WriteLine($"SetExAxisRobotPlan rtn is {rtn}");
        Thread.Sleep(1000);
        rtn = robot.ExtAxisSyncMoveL(joint_pos1, desc_pos1, 1, 0, 100, 100, 100, -1, epos1, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 1 rtn is {rtn}");

        rtn = robot.ExtAxisSyncMoveL(joint_pos2, desc_pos2, 1, 0, 100, 100, 100, -1, epos2, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 2 rtn is {rtn}");
        rtn = robot.ExtAxisSyncMoveL(joint_pos3, desc_pos3, 1, 0, 100, 100, 100, -1, epos3, 0, offset_pos);
        Console.WriteLine($"ExtAxisSyncMoveL 3 rtn is {rtn}");
        Thread.Sleep(8000);
    }

Impostazione del Tempo di Completamento del Posizionamento per Assi di Estensione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta il tempo di completamento del posizionamento per assi di estensione UDP
    * @param [in] time Tempo di completamento del posizionamento [ms]
    * @return Codice di errore
    */
    public int SetExAxisCmdDoneTime(double time)