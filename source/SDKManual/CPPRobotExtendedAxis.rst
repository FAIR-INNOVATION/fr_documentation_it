Assi Estesi
=============

.. toctree:: 
    :maxdepth: 5

Impostare i parametri dell'asse esteso RS485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i parametri dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] servoCompany Produttore driver servo, 1-Dynatek
    * @param [in] servoModel Modello driver servo, 1-FD100-750C
    * @param [in] servoSoftVersion Versione software driver servo, 1-V1.0
    * @param [in] servoResolution Risoluzione encoder
    * @param [in] axisMechTransRatio Rapporto di trasmissione meccanico
    * @return Codice di errore
    */
    errno_t AuxServoSetParam(int servoId, int servoCompany, int servoModel, int servoSoftVersion, int servoResolution, double axisMechTransRatio);

Ottenere i parametri di configurazione dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i parametri di configurazione dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [out] servoCompany Produttore driver servo, 1-Dynatek
    * @param [out] servoModel Modello driver servo, 1-FD100-750C
    * @param [out] servoSoftVersion Versione software driver servo, 1-V1.0
    * @param [out] servoResolution Risoluzione encoder
    * @param [out] axisMechTransRatio Rapporto di trasmissione meccanico
    * @return Codice di errore
    */
    errno_t AuxServoGetParam(int servoId, int* servoCompany, int* servoModel, int* servoSoftVersion, int* servoResolution, double* axisMechTransRatio);

Impostare l'abilitazione/disabilitazione dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta l'abilitazione/disabilitazione dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] status Stato abilitazione, 0-Disabilitato, 1-Abilitato
    * @return Codice di errore
    */
    errno_t AuxServoEnable(int servoId, int status);

Impostare la modalità di controllo dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la modalità di controllo dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] mode Modalità controllo, 0-Modalità posizione, 1-Modalità velocità
    * @return Codice di errore
    */
    errno_t AuxServoSetControlMode(int servoId, int mode);

Impostare la posizione target dell'asse esteso RS485 (Modalità posizione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la posizione target dell'asse esteso RS485 (Modalità posizione)
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] pos Posizione target, mm o °
    * @param [in] speed Velocità target, mm/s o °/s
    * @return Codice di errore
    */
    errno_t AuxServoSetTargetPos(int servoId, double pos, double speed);

Impostare la coppia target dell'asse esteso RS485 (Modalità coppia) - Non ancora disponibile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la coppia target dell'asse esteso RS485 (Modalità coppia)
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] torque Coppia target, Nm
    * @return Codice di errore
    */
    errno_t AuxServoSetTargetTorque(int servoId, double torque);

Impostare l'azzeramento (homing) dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta l'azzeramento (homing) dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] mode Modalità azzeramento, 0-Azzeramento alla posizione corrente; 1-Azzeramento al finecorsa
    * @param [in] searchVel Velocità ricerca azzeramento, mm/s o °/s
    * @param [in] latchVel Velocità aggancio, mm/s o °/s
    * @return Codice di errore
    */
    errno_t AuxServoHoming(int servoId, int mode, double searchVel, double latchVel);

Cancellare le informazioni di errore dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Cancella le informazioni di errore dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @return Codice di errore
    */
    errno_t AuxServoClearError(int servoId);

Ottenere lo stato del servo dell'asse esteso RS485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato del servo dell'asse esteso RS485
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [out] servoErrCode Codice errore driver servo
    * @param [out] servoState Stato driver servo [numero decimale convertito in binario, bit0-bit5: Servo abilitato-Servo in esecuzione-Finecorsa positivo attivato-Finecorsa negativo attivato-Posizionamento completato-Azzeramento completato]
    * @param [out] servoPos Posizione corrente servo mm o °
    * @param [out] servoSpeed Velocità corrente servo mm/s o °/s
    * @param [out] servoTorque Coppia corrente servo Nm
    * @return Codice di errore
    */
    errno_t AuxServoGetStatus(int servoId, int* servoErrCode, int* servoState, double* servoPos, double* servoSpeed, double* servoTorque);

Impostare la velocità target dell'asse esteso RS485 (Modalità velocità)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la velocità target dell'asse esteso RS485 (Modalità velocità)
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @param [in] speed Velocità target, mm/s o °/s
    * @return Codice di errore
    */
    errno_t AuxServoSetTargetSpeed(int servoId, double speed);

Impostare il numero dell'asse per i dati dell'asse esteso RS485 nel feedback di stato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il numero dell'asse per i dati dell'asse esteso RS485 nel feedback di stato
    * @param [in] servoId ID driver servo, intervallo [1-15], corrisponde all'ID slave
    * @return Codice di errore
    */
    errno_t AuxServosetStatusID(int servoId);

Impostare l'accelerazione/decelerazione del movimento dell'asse esteso RS485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta l'accelerazione/decelerazione del movimento dell'asse esteso RS485
    * @param [in] acc Accelerazione movimento asse esteso RS485
    * @param [in] dec Decelerazione movimento asse esteso RS485
    * @return Codice di errore
    */
    errno_t AuxServoSetAcc(double acc, double dec);

Impostare l'accelerazione/decelerazione di arresto di emergenza dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta l'accelerazione/decelerazione di arresto di emergenza dell'asse esteso RS485
    * @param [in] acc Accelerazione arresto emergenza asse esteso RS485
    * @param [in] dec Decelerazione arresto emergenza asse esteso RS485
    * @return Codice di errore
    */
    errno_t AuxServoSetEmergencyStopAcc(double acc, double dec);

Ottenere l'accelerazione/decelerazione del movimento dell'asse esteso RS485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene l'accelerazione/decelerazione del movimento dell'asse esteso RS485
    * @param [out] acc Accelerazione movimento asse esteso RS485
    * @param [out] dec Decelerazione movimento asse esteso RS485
    * @return Codice di errore
    */
    errno_t AuxServoGetAcc(double& acc, double& dec);

Ottenere l'accelerazione/decelerazione di arresto di emergenza dell'asse esteso RS485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene l'accelerazione/decelerazione di arresto di emergenza dell'asse esteso RS485
    * @param [out] acc Accelerazione arresto emergenza asse esteso RS485
    * @param [out] dec Decelerazione arresto emergenza asse esteso RS485
    * @return Codice di errore
    */
    errno_t AuxServoGetEmergencyStopAcc(double& acc, double& dec);

Esempio di codice per il controllo degli assi estesi
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
        
    int Test485Auxservo(void)
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
      int retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      int servoCompany;
      int servoModel;
      int servoSoftVersion;
      int servoResolution;
      double axisMechTransRatio;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      retval = robot.AuxServoGetParam(1, &servoCompany, &servoModel, &servoSoftVersion, &servoResolution, &axisMechTransRatio);
      std::cout << "servoCompany " << servoCompany << "\n"
        << "servoModel " << servoModel << "\n"
        << "servoSoftVersion " << servoSoftVersion << "\n"
        << "servoResolution " << servoResolution << "\n"
        << "axisMechTransRatio " << axisMechTransRatio << "\n"
        << std::endl;
      retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36);
      std::cout << "AuxServoSetParam is: " << retval << std::endl;
      robot.Sleep(3000);
      robot.AuxServoSetAcc(3000, 3000);
      robot.AuxServoSetEmergencyStopAcc(5000, 5000);
      robot.Sleep(1000);
      double emagacc = 0, acc = 0;
      double emagdec = 0, dec = 0;
      robot.AuxServoGetEmergencyStopAcc(emagacc, emagdec);
      printf("emergency acc is %f dec is %f \n", emagacc, emagdec);
      robot.AuxServoGetAcc(acc, dec);
      printf("acc is %f dec is %f \n", acc, dec);
      robot.AuxServoSetControlMode(1, 0);
      robot.Sleep(2000);
      retval = robot.AuxServoEnable(1, 0);
      std::cout << "AuxServoEnable disenable " << retval << std::endl;
      robot.Sleep(1000);
      int servoerrcode = 0;
      int servoErrCode;
      int servoState;
      double servoPos;
      double servoSpeed;
      double servoTorque;
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);;
      retval = robot.AuxServoEnable(1, 1);
      std::cout << "AuxServoEnable enable " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoState " << servoState << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoHoming(1, 1, 5, 1);
      std::cout << "AuxServoHoming " << retval << std::endl;
      robot.Sleep(3000);
      retval = robot.AuxServoSetTargetPos(1, 200, 30);
      std::cout << "AuxServoSetTargetPos " << retval << std::endl;
      robot.Sleep(1000);
      retval = robot.AuxServoGetStatus(1, &servoErrCode, &servoState, &servoPos, &servoSpeed, &servoTorque);
      std::cout << "AuxServoGetStatus servoSpeed " << servoSpeed << std::endl;
      robot.Sleep(8000);
      robot.AuxServoSetControlMode(1, 1);
      robot.Sleep(2000);
      robot.AuxServoEnable(1, 0);
      robot.Sleep(1000);
      robot.AuxServoEnable(1, 1);
      robot.Sleep(1000);
      robot.AuxServoSetTargetSpeed(1, 100, 80);
      robot.Sleep(5000);
      robot.AuxServoSetTargetSpeed(1, 0, 80);
      robot.CloseRPC();
      return 0;
    }

Configurazione dei parametri di comunicazione per l'asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Configurazione dei parametri di comunicazione per l'asse esteso UDP
    * @param [in] ip Indirizzo IP PLC
    * @param [in] port   Numero porta
    * @param [in] period    Periodo di comunicazione (ms, predefinito 2, non modificare questo parametro)
    * @param [in] lossPkgTime   Tempo rilevamento perdita pacchetti (ms)
    * @param [in] lossPkgNum    Numero perdite pacchetti
    * @param [in] disconnectTime    Tempo conferma disconnessione comunicazione
    * @param [in] reconnectEnable   Abilita riconnessione automatica in caso di interruzione comunicazione 0-Non abilitata 1-Abilitata
    * @param [in] reconnectPeriod   Intervallo periodo riconnessione (ms)
    * @param [in] reconnectNum  Numero tentativi riconnessione
    * @param [in] selfConnect Stabilire automaticamente la connessione dopo riavvio da spegnimento; 0-Non stabilire connessione; 1-Stabilire connessione
    * @return Codice di errore
    */
    errno_t ExtDevSetUDPComParam(std::string ip, int port, int period, int lossPkgTime, int lossPkgNum, int disconnectTime, int reconnectEnable, int reconnectPeriod, int reconnectNum, int selfConnect = 1);

Ottenere la configurazione dei parametri di comunicazione per l'asse esteso UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i parametri di comunicazione per l'asse esteso UDP
    * @param [out] ip Indirizzo IP PLC
    * @param [out] port Numero porta
    * @param [out] period Periodo di comunicazione (ms, predefinito 2, non modificare questo parametro)
    * @param [out] lossPkgTime Tempo rilevamento perdita pacchetti (ms)
    * @param [out] lossPkgNum Numero perdite pacchetti
    * @param [out] disconnectTime Tempo conferma disconnessione comunicazione
    * @param [out] reconnectEnable Abilita riconnessione automatica in caso di interruzione comunicazione 0-Non abilitata 1-Abilitata
    * @param [out] reconnectPeriod Intervallo periodo riconnessione (ms)
    * @param [out] reconnectNum Numero tentativi riconnessione
    * @return Codice di errore
    */
    errno_t ExtDevGetUDPComParam(std::string& ip, int& port, int& period, int& lossPkgTime, int& lossPkgNum, int& disconnectTime, int& reconnectEnable, int& reconnectPeriod, int& reconnectNum);

Caricare la comunicazione UDP
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Carica la comunicazione UDP
    * @return Codice di errore
    */
    errno_t ExtDevLoadUDPDriver();

Scaricare la comunicazione UDP
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Scarica la comunicazione UDP
    * @return Codice di errore
    */
    errno_t ExtDevUnloadUDPDriver();

Ripristinare la connessione dopo interruzione anomala della comunicazione per l'asse esteso UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ripristinare la connessione dopo interruzione anomala della comunicazione per l'asse esteso UDP
    * @return Codice di errore
    */
    errno_t ExtDevUDPClientComReset();

Chiudere la comunicazione dopo interruzione anomala della comunicazione per l'asse esteso UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Chiudere la comunicazione dopo interruzione anomala della comunicazione per l'asse esteso UDP
    * @return Codice di errore
    */
    errno_t ExtDevUDPClientComClose();

Configurazione dei parametri dell'asse esteso UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Configurazione dei parametri dell'asse esteso UDP
    * @param [in] axisID Numero asse
    * @param [in] axisType Tipo asse esteso 0-Traslazione; 1-Rotazione
    * @param [in] axisDirection Direzione asse esteso 0-Positiva; 1-Negativa
    * @param [in] axisMax Posizione massima asse esteso mm
    * @param [in] axisMin Posizione minima asse esteso mm
    * @param [in] axisVel Velocità mm/s
    * @param [in] axisAcc Accelerazione mm/s2
    * @param [in] axisLead Passo vite mm
    * @param [in] encResolution Risoluzione encoder
    * @param [in] axisOffect Spostamento asse esteso al punto di partenza della saldatura
    * @param [in] axisCompany Produttore driver 1-Hechuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Modello driver 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Tipo encoder 0-Incrementale; 1-Assoluto
    * @return Codice di errore
    */
    errno_t ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, long encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Impostare la posizione di installazione dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la posizione di installazione dell'asse esteso
    * @param [in] installType 0-Robot installato sull'asse esterno, 1-Robot installato esternamente all'asse
    * @return Codice di errore
    */
    errno_t SetRobotPosToAxis(int installType);

Impostare la configurazione dei parametri DH del sistema asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la configurazione dei parametri DH del sistema asse esteso
    * @param [in]  axisConfig Configurazione asse esterno, 0-Guida lineare a 1 grado di libertà, 1-Posizionatore a L a 2 gradi di libertà, 2-3 gradi di libertà, 3-4 gradi di libertà, 4-Posizionatore a 1 grado di libertà
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
    errno_t SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Abilitazione asse esteso UDP
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Abilitazione asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] status 0-Disabilita; 1-Abilitata
    * @return Codice di errore
    */
    errno_t ExtAxisServoOn(int axisID, int status);

Azzeramento (Homing) asse esteso UDP
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Azzeramento (Homing) asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] mode Modalità azzeramento 0-Azzeramento alla posizione corrente, 1-Azzeramento al finecorsa negativo, 2-Azzeramento al finecorsa positivo
    * @param [in] searchVel Velocità ricerca (mm/s)
    * @param [in] latchVel Velocità aggancio (mm/s)
    * @return Codice di errore
    */
    errno_t ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Inizio Jog asse esteso UDP
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio Jog asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @param [in] direction Direzione rotazione 0-Negativa; 1-Positiva
    * @param [in] vel Velocità (mm/s)
    * @param [in] acc Accelerazione (mm/s2)
    * @param [in] maxDistance Distanza massima Jog
    * @return Codice di errore
    */
    errno_t ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);

Stop Jog asse esteso UDP
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Stop Jog asse esteso UDP
    * @param [in] axisID Numero asse[1-4]
    * @return Codice di errore
    */
    errno_t ExtAxisStopJog(int axisID);

Esempio di codice per configurazione e Jog dell'asse esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxis(void)
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
      rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
      cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
      string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
      rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
      string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
      cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
      rtn = robot.ExtAxisServoOn(2, 1);
      cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
      robot.Sleep(4000);
      rtn = robot.SetRobotPosToAxis(1);
      cout << "SetRobotPosToAxis rtn is " << rtn << endl;
      rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
      cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
      rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
      cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
      rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
      cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
      robot.Sleep(1000 * 3);
      robot.ExtAxisStartJog(1, 0, 10, 10, 30);
      robot.Sleep(1000 * 1);
      robot.ExtAxisStopJog(1);
      robot.Sleep(1000 * 3);
      robot.ExtAxisServoOn(1, 0);
      robot.Sleep(1000 * 3);
      robot.ExtAxisStartJog(2, 0, 10, 10, 30);
      robot.Sleep(1000 * 1);
      robot.ExtAxisStopJog(2);
      robot.Sleep(1000 * 3);
      robot.ExtAxisServoOn(2, 0);
      robot.ExtDevUnloadUDPDriver();
      robot.CloseRPC();
      return 0;
    }

Impostare i punti di riferimento del sistema di coordinate dell'asse esteso - Metodo a 4 punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i punti di riferimento del sistema di coordinate dell'asse esteso - Metodo a 4 punti
    * @param [in]  pointNum Numero punto[1-4]
    * @return Codice di errore
    */
    errno_t ExtAxisSetRefPoint(int pointNum);

Calcolare il sistema di coordinate dell'asse esteso - Metodo a 4 punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Calcola il sistema di coordinate dell'asse esteso - Metodo a 4 punti
    * @param [out]  coord Valore sistema di coordinate
    * @return Codice di errore
    */
    errno_t ExtAxisComputeECoordSys(DescPose& coord);

Impostare i punti di riferimento del sistema di coordinate del posizionatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i punti di riferimento del sistema di coordinate del posizionatore
    * @param [in]  pointNum Numero punto[1-4]
    * @return Codice di errore
    */
    errno_t PositionorSetRefPoint(int pointNum);

Calcolare il sistema di coordinate del posizionatore - Metodo a 4 punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Calcola il sistema di coordinate del posizionatore - Metodo a 4 punti
    * @param [out] coord Valore sistema di coordinate
    * @return Codice di errore
    */
    errno_t PositionorComputeECoordSys(DescPose& coord);

Impostare la posa del punto di riferimento di calibrazione nel sistema di coordinate terminale del posizionatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta la posa del punto di riferimento di calibrazione nel sistema di coordinate terminale del posizionatore
    * @param [in] pos Valore posa
    * @return Codice di errore
    */
    errno_t SetRefPointInExAxisEnd(DescPose pos);

Applicare il sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Applicare il sistema di coordinate dell'asse esteso
    * @param [in]  applyAxisId Numero asse esteso bit0-bit3 corrisponde ai numeri asse esteso 1-4, ad es. se applicati assi estesi 1 e 3, allora è 0b 0000 0101; ovvero 5
    * @param [in]  axisCoordNum Numero sistema di coordinate asse esteso
    * @param [in]  coord Valore sistema di coordinate
    * @param [in]  calibFlag Flag calibrazione 0-No, 1-Sì
    * @return Codice di errore
    */
    errno_t ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Ottenere il sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene il sistema di coordinate dell'asse esteso
    * @param [out] coord Sistema di coordinate asse esteso
    * @return Codice di errore
    */
    errno_t ExtAxisGetCoord(DescPose& coord);

Esempio di codice per la calibrazione del sistema di coordinate dell'asse esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
       rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
       cout << "ExtDevSetUDPComParam rtn is " << rtn << endl;
       string ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
       rtn = robot.ExtDevGetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum);
       string patam = "\nip " + ip + "\nport " + to_string(port) + "\nperiod " + to_string(period) + "\nlossPkgTime " + to_string(lossPkgTime) + "\nlossPkgNum " + to_string(lossPkgNum) + "\ndisConntime " + to_string(disconnectTime) + "\nreconnecable " + to_string(reconnectEnable) + "\nreconnperiod " + to_string(reconnectPeriod) + "\nreconnnun " + to_string(reconnectNum);
       cout << "ExtDevGetUDPComParam rtn is " << rtn << patam << endl;
       robot.ExtDevLoadUDPDriver();
       rtn = robot.ExtAxisServoOn(1, 1);
       cout << "ExtAxisServoOn axis id 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisServoOn(2, 1);
       cout << "ExtAxisServoOn axis id 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.ExtAxisSetHoming(1, 0, 10, 2);
       robot.Sleep(2000);
       rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
       cout << "ExtAxisSetHoming rtnn is " << rtn << endl;
       robot.Sleep(4000);
       rtn = robot.SetRobotPosToAxis(1);
       cout << "SetRobotPosToAxis rtn is " << rtn << endl;
       rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0);
       cout << "SetAxisDHParaConfig rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);
       cout << "ExtAxisParamConfig axis 1 rtn is " << rtn << endl;
       DescPose toolCoord(0, 0, 210, 0, 0, 0);
       robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
       JointPos jSafe(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
       JointPos j1(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
       JointPos j2(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
       JointPos j3(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
       JointPos j4(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);
       DescPose descSafe = {};
       DescPose desc1 = {};
       DescPose desc2 = {};
       DescPose desc3 = {};
       DescPose desc4 = {};
       ExaxisPos exaxisPos = { 0, 0, 0, 0 };
       DescPose offdese = { 0, 0, 0, 0, 0, 0 };
       robot.GetForwardKin(&jSafe, &descSafe);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       robot.GetForwardKin(&j1, &desc1);
       robot.MoveJ(&j1, &desc1, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.Sleep(2000);
       DescPose actualTCPPos = {};
       robot.GetActualTCPPose(0, &actualTCPPos);
       robot.SetRefPointInExAxisEnd(actualTCPPos);
       rtn = robot.PositionorSetRefPoint(1);
       cout << "PositionorSetRefPoint 1 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j2, &desc2);
       rtn = robot.MoveJ(&j2, &desc2, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(2);
       cout << "PositionorSetRefPoint 2 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j3, &desc3);
       robot.MoveJ(&j3, &desc3, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(3);
       cout << "PositionorSetRefPoint 3 rtn is " << rtn << endl;
       robot.Sleep(2000);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.ExtAxisStartJog(1, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.ExtAxisStartJog(2, 0, 50, 50, 10);
       robot.Sleep(1000);
       robot.GetForwardKin(&j4, &desc4);
       robot.MoveJ(&j4, &desc4, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       rtn = robot.PositionorSetRefPoint(4);
       cout << "PositionorSetRefPoint 4 rtn is " << rtn << endl;
       robot.Sleep(2000);
       DescPose axisCoord = {};
       robot.PositionorComputeECoordSys(axisCoord);
       robot.MoveJ(&jSafe, &descSafe, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       printf("PositionorComputeECoordSys rtn is %f %f %f %f %f %f\n", axisCoord.tran.x, axisCoord.tran.y, axisCoord.tran.z, axisCoord.rpy.rx, axisCoord.rpy.ry, axisCoord.rpy.rz);
       rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);
       cout << "ExtAxisActiveECoordSys rtn is " << rtn << endl;
    DescPose getCoord(0, 0, 0, 0, 0, 0);
    rtn = robot.ExtAxisGetCoord(getCoord);
    printf("ExtAxisGetCoord rtn is %f %f %f %f %f %f\n", getCoord.tran.x, getCoord.tran.y, getCoord.tran.z, getCoord.rpy.rx, getCoord.rpy.ry, getCoord.rpy.rz);
    robot.CloseRPC();
    return 0;
    }

Movimento dell'asse esteso UDP
++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento dell'asse esteso UDP
    * @param [in] pos Posizione target
    * @param [in] ovl Percentuale velocità
    * @param [in] blend Parametro smoothing (mm o ms); -1: attendi completamento movimento
    * @return Codice di errore
    */
    errno_t ExtAxisMove(ExaxisPos pos, double ovl, double blend = -1);

Esempio di codice per il movimento dell'asse esteso UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestUDPAxisCalib(void)
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
      ExaxisPos axisPos;
      axisPos.ePos[0] = 20;
      axisPos.ePos[1] = 0;
      axisPos.ePos[2] = 0;
      axisPos.ePos[3] = 0;
      robot.ExtAxisMove(axisPos, 50);
      robot.CloseRPC();
      return 0;
    }

Movimento sincronizzato dell'asse esteso UDP con le giunti del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con le giunti del robot
    * @param [in] joint_pos Posizione giunti target, unità deg
    * @param [in] desc_pos Posa cartesiana target
    * @param [in] tool Numero coordinate utensile, intervallo [0~14]
    * @param [in] user Numero coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl Fattore scala velocità, intervallo [0~100]
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] blendT [-1.0]-movimento fino alla posizione (bloccante), [0~500.0]-tempo smoothing (non bloccante), unità ms
    * @param [in] offset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos  Quantità offset posa
    * @return  Codice di errore
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Movimento sincronizzato dell'asse esteso UDP con le giunti del robot (calcolo cinematico diretto automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con le giunti del robot (calcolo cinematico diretto automatico)
    * @param [in] joint_pos Posizione giunti target, unità deg
    * @param [in] tool Numero coordinate utensile, intervallo [0~14]
    * @param [in] user Numero coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl Fattore scala velocità, intervallo [0~100]
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] blendT [-1.0]-movimento fino alla posizione (bloccante), [0~500.0]-tempo smoothing (non bloccante), unità ms
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità offset posa
    * @return Codice di errore
    */
    errno_t ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, uint8_t offset_flag, DescPose offset_pos);

Esempio di codice per movimento sincronizzato dell'asse esteso UDP con le giunti del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveJ()
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
      //1. Calibrare e applicare il sistema di coordinate utensile del robot, è possibile utilizzare il metodo a 4 o 6 punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
      //  int SetToolPoint(int point_num); //Impostare punto di riferimento utensile - metodo a 6 punti
      //  int ComputeTool(ref DescPose tcp_pose); //Calcolare sistema di coordinate utensile
      //  int SetTcp4RefPoint(int point_num);  //Impostare punto di riferimento utensile - metodo a 4 punti
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcolare sistema di coordinate utensile - metodo a 4 punti
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Impostare e applicare sistema di coordinate utensile
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Impostare e applicare lista sistemi coordinate utensile
      //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Impostare parametri asse esteso, inclusi tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore ad asse singolo e parametri DH
      robot.SetRobotPosToAxis(1); //Posizione installazione asse esteso
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è per un posizionatore ad asse singolo, quindi è necessario impostare solo i parametri di un driver. Se si sceglie un tipo di asse esteso che include più assi, è necessario impostare i parametri del driver per ciascun asse
      //4. Impostare abilitazione e azzeramento per l'asse selezionato
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Eseguire calibrazione e applicazione del sistema di coordinate dell'asse esteso
      DescPose pos = {/* Inserire le coordinate del punto di calibrazione */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare l'asse esteso, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcolare risultato calibrazione asse esteso
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applicare risultato calibrazione al sistema di coordinate asse esteso
      //6. Calibrare il sistema di coordinate pezzo sull'asse esteso, è necessario utilizzare le seguenti interfacce
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Registrare il punto di partenza del movimento sincrono delle giunti
      DescPose startdescPose = {/*Inserire coordinate*/ };
      JointPos startjointPos = {/*Inserire coordinate*/ };
      ExaxisPos startexaxisPos = {/* Inserire coordinate punto di partenza asse esteso */ };
      //8. Registrare le coordinate del punto di arrivo del movimento sincrono delle giunti
      DescPose enddescPose = {/*Inserire coordinate*/ };
      JointPos endjointPos = {/*Inserire coordinate*/ };
      ExaxisPos endexaxisPos = {/* Inserire coordinate punto di arrivo asse esteso */ };
      //9. Scrivere programma movimento sincrono
      //Muoversi al punto di partenza, supponendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
      robot.CloseRPC();
    }

Movimento sincronizzato dell'asse esteso UDP con movimento lineare del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con movimento lineare del robot
    * @param [in] joint_pos   Posizione giunti target, unità deg
    * @param [in] desc_pos    Posa cartesiana target
    * @param [in] tool   Numero coordinate utensile, intervallo [0~14]
    * @param [in] user   Numero coordinate pezzo, intervallo [0~14]
    * @param [in] vel   Percentuale velocità, intervallo [0~100]
    * @param [in] acc   Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl   Fattore scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino alla posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param [in] epos   Posizione asse esteso, unità mm
    * @param [in] offset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos   Quantità offset posa
    * @return Codice di errore
    */
    errno_t ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Movimento sincronizzato dell'asse esteso UDP con movimento lineare del robot (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con movimento lineare del robot (calcolo cinematico inverso automatico)
    * @param [in] desc_pos   Posa cartesiana target
    * @param [in] tool Numero coordinate utensile, intervallo [0~14]
    * @param [in] user Numero coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl Fattore scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino alla posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità offset posa
    * @param [in] config Configurazione spazio giunti per soluzione inversa, [-1]-calcolo con riferimento alla posizione giunti corrente, [0~7]-soluzione basata su specifica configurazione spazio giunti
    * @return Codice di errore
    */
    errno_t ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, uint8_t offset_flag, DescPose offset_pos, int config = -1);

Esempio di codice per movimento sincronizzato dell'asse esteso UDP con movimento lineare del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveL()
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
      //1. Calibrare e applicare il sistema di coordinate utensile del robot, è possibile utilizzare il metodo a 4 o 6 punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
      //  int SetToolPoint(int point_num); //Impostare punto di riferimento utensile - metodo a 6 punti
      //  int ComputeTool(ref DescPose tcp_pose); //Calcolare sistema di coordinate utensile
      //  int SetTcp4RefPoint(int point_num);  //Impostare punto di riferimento utensile - metodo a 4 punti
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcolare sistema di coordinate utensile - metodo a 4 punti
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Impostare e applicare sistema di coordinate utensile
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Impostare e applicare lista sistemi coordinate utensile
      //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Impostare parametri asse esteso, inclusi tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore ad asse singolo e parametri DH
      robot.SetRobotPosToAxis(1); //Posizione installazione asse esteso
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è per un posizionatore ad asse singolo, quindi è necessario impostare solo i parametri di un driver. Se si sceglie un tipo di asse esteso che include più assi, è necessario impostare i parametri del driver per ciascun asse
      //4. Impostare abilitazione e azzeramento per l'asse selezionato
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Eseguire calibrazione e applicazione del sistema di coordinate dell'asse esteso
      DescPose pos = {/* Inserire le coordinate del punto di calibrazione */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare l'asse esteso, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcolare risultato calibrazione asse esteso
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applicare risultato calibrazione al sistema di coordinate asse esteso
      //6. Calibrare il sistema di coordinate pezzo sull'asse esteso, è necessario utilizzare le seguenti interfacce
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Registrare il punto di partenza del movimento sincrono lineare
      DescPose startdescPose = {/*Inserire coordinate*/ };
      JointPos startjointPos = {/*Inserire coordinate*/ };
      ExaxisPos startexaxisPos = {/* Inserire coordinate punto di partenza asse esteso */ };
      //8. Registrare le coordinate del punto di arrivo del movimento sincrono lineare
      DescPose enddescPose = {/*Inserire coordinate*/ };
      JointPos endjointPos = {/*Inserire coordinate*/ };
      ExaxisPos endexaxisPos = {/* Inserire coordinate punto di arrivo asse esteso */ };
      //9. Scrivere programma movimento sincrono
      //Muoversi al punto di partenza, supponendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
      
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
      robot.CloseRPC();
    }

Movimento sincronizzato dell'asse esteso UDP con movimento circolare del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con movimento circolare del robot
    * @param [in] joint_pos_p   Posizione giunti punto percorso, unità deg
    * @param [in] desc_pos_p    Posa cartesiana punto percorso
    * @param [in] ptool   Numero coordinate utensile, intervallo [0~14]
    * @param [in] puser   Numero coordinate pezzo, intervallo [0~14]
    * @param [in] pvel   Percentuale velocità, intervallo [0~100]
    * @param [in] pacc   Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_p   Posizione asse esteso punto intermedio, unità mm
    * @param [in] poffset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_p   Quantità offset posa
    * @param [in] joint_pos_t   Posizione giunti punto target, unità deg
    * @param [in] desc_pos_t    Posa cartesiana punto target
    * @param [in] ttool   Numero coordinate utensile, intervallo [0~14]
    * @param [in] tuser   Numero coordinate pezzo, intervallo [0~14]
    * @param [in] tvel   Percentuale velocità, intervallo [0~100]
    * @param [in] tacc   Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_t   Posizione asse esteso, unità mm
    * @param [in] toffset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_t   Quantità offset posa
    * @param [in] ovl   Fattore scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino alla posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @return Codice di errore
    */
    errno_t ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, float ovl, float blendR);

Movimento sincronizzato dell'asse esteso UDP con movimento circolare del robot (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento sincronizzato dell'asse esteso UDP con movimento circolare del robot (calcolo cinematico inverso automatico)
    * @param [in] desc_pos_p   Posa cartesiana punto percorso
    * @param [in] ptool Numero coordinate utensile, intervallo [0~14]
    * @param [in] puser Numero coordinate pezzo, intervallo [0~14]
    * @param [in] pvel Percentuale velocità, intervallo [0~100]
    * @param [in] pacc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_p Posizione asse esteso, unità mm
    * @param [in] poffset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_p Quantità offset posa
    * @param [in] desc_pos_t   Posa cartesiana punto target
    * @param [in] ttool Numero coordinate utensile, intervallo [0~14]
    * @param [in] tuser Numero coordinate pezzo, intervallo [0~14]
    * @param [in] tvel Percentuale velocità, intervallo [0~100]
    * @param [in] tacc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_t Posizione asse esteso, unità mm
    * @param [in] toffset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_t Quantità offset posa
    * @param [in] ovl Fattore scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino alla posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param [in] config Configurazione spazio giunti per soluzione inversa, [-1]-calcolo con riferimento alla posizione giunti corrente, [0~7]-soluzione basata su specifica configurazione spazio giunti
    * @return Codice di errore
    */
    errno_t ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos epos_p, uint8_t poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos epos_t, uint8_t toffset_flag, DescPose offset_pos_t, float ovl, float blendR, int config = -1);

Esempio di codice per movimento sincronizzato dell'asse esteso UDP con movimento circolare del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int testSyncMoveC()
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
      //1. Calibrare e applicare il sistema di coordinate utensile del robot, è possibile utilizzare il metodo a 4 o 6 punti per la calibrazione e applicazione del sistema di coordinate utensile, le interfacce coinvolte sono:
      //  int SetToolPoint(int point_num); //Impostare punto di riferimento utensile - metodo a 6 punti
      //  int ComputeTool(ref DescPose tcp_pose); //Calcolare sistema di coordinate utensile
      //  int SetTcp4RefPoint(int point_num);  //Impostare punto di riferimento utensile - metodo a 4 punti
      //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcolare sistema di coordinate utensile - metodo a 4 punti
      //  int SetToolCoord(int id, DescPose coord, int type, int install); //Impostare e applicare sistema di coordinate utensile
      //  int SetToolList(int id, DescPose coord, int type, int install);  //Impostare e applicare lista sistemi coordinate utensile
      //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
      robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10);
      robot.ExtDevLoadUDPDriver();
      //3. Impostare parametri asse esteso, inclusi tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
      robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore ad asse singolo e parametri DH
      robot.SetRobotPosToAxis(1); //Posizione installazione asse esteso
      robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è per un posizionatore ad asse singolo, quindi è necessario impostare solo i parametri di un driver. Se si sceglie un tipo di asse esteso che include più assi, è necessario impostare i parametri del driver per ciascun asse
      //4. Impostare abilitazione e azzeramento per l'asse selezionato
      robot.ExtAxisServoOn(1, 0);
      robot.ExtAxisSetHoming(1, 0, 20, 3);
      //5. Eseguire calibrazione e applicazione del sistema di coordinate dell'asse esteso
      DescPose pos = {/* Inserire le coordinate del punto di calibrazione */ };
      robot.SetRefPointInExAxisEnd(pos);
      robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare l'asse esteso, quindi è necessario chiamare questa interfaccia 4 volte per completare la calibrazione */
      DescPose coord = {};
      robot.PositionorComputeECoordSys(coord); //Calcolare risultato calibrazione asse esteso
      robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applicare risultato calibrazione al sistema di coordinate asse esteso
      //6. Calibrare il sistema di coordinate pezzo sull'asse esteso, è necessario utilizzare le seguenti interfacce
      //int SetWObjCoordPoint(int point_num);
      //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
      //int SetWObjCoord(int id, DescPose coord);
      //int SetWObjList(int id, DescPose coord);
      //7. Registrare il punto di partenza del movimento sincrono circolare
      DescPose startdescPose = {/*Inserire coordinate*/ };
      JointPos startjointPos = {/*Inserire coordinate*/ };
      ExaxisPos startexaxisPos = {/* Inserire coordinate punto di partenza asse esteso */ };
      //8. Registrare le coordinate del punto di arrivo del movimento sincrono circolare
      DescPose enddescPose = {/*Inserire coordinate*/ };
      JointPos endjointPos = {/*Inserire coordinate*/ };
      ExaxisPos endexaxisPos = {/* Inserire coordinate punto di arrivo asse esteso */ };
      //9. Registrare le coordinate del punto intermedio del movimento sincrono circolare
      DescPose middescPose = {/*Inserire coordinate*/ };
      JointPos midjointPos = {/*Inserire coordinate*/ };
      ExaxisPos midexaxisPos = {/* Inserire coordinate asse esteso al punto intermedio dell'arco del robot */ };
      //10. Scrivere programma movimento sincrono
      //Muoversi al punto di partenza, supponendo che i sistemi di coordinate utensile e pezzo applicati siano entrambi 1
      robot.ExtAxisMove(startexaxisPos, 20);
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      robot.MoveJ(&startjointPos, &startdescPose, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.MoveJ(&startjointPos, 1, 1, 100, 100, 100, &startexaxisPos, 0, 0, &offdese);
      //Iniziare movimento sincrono
      robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
      robot.CloseRPC();
    }

Impostare DO esteso
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta DO esteso
    * @param [in] DONum Numero DO
    * @param [in] bOpen Interruttore true-Aperto; false-Chiuso
    * @param [in] smooth Smoothing
    * @param [in] block Bloccante
    * @return Codice di errore
    */
    errno_t SetAuxDO(int DONum, bool bOpen, bool smooth, bool block);

Impostare AO esteso
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta AO esteso
    * @param [in] AONum Numero AO
    * @param [in] value Valore analogico [0-4095]
    * @param [in] block Bloccante
    * @return Codice di errore
    */
    errno_t SetAuxAO(int AONum, double value, bool block);

Impostare il tempo di filtraggio input DI esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il tempo di filtraggio input DI esteso
    * @param [in] filterTime Tempo filtraggio (ms)
    * @return Codice di errore
    */
    errno_t SetAuxDIFilterTime(int filterTime);

Impostare il tempo di filtraggio input AI esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta il tempo di filtraggio input AI esteso
    * @param [in] filterTime Tempo filtraggio (ms)
    * @return Codice di errore
    */
    errno_t SetAuxAIFilterTime(int filterTime);

Attendere input DI esteso
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Attende input DI esteso
    * @param [in] DINum Numero DI
    * @param [in] bOpen Interruttore 0-Chiuso; 1-Aperto
    * @param [in] time Tempo massimo attesa (ms)
    * @param [in] errorAlarm Continuare movimento
    * @return Codice di errore
    */
    errno_t WaitAuxDI(int DINum, bool bOpen, int time, bool errorAlarm);

Attendere input AI esteso
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Attende input AI esteso
    * @param [in] AINum Numero AI
    * @param [in] sign 0-Maggiore di; 1-Minore di
    * @param [in] value Valore AI
    * @param [in] time Tempo massimo attesa (ms)
    * @param [in] errorAlarm Continuare movimento
    * @return Codice di errore
    */
    errno_t WaitAuxAI(int AINum, int sign, int value, int time, bool errorAlarm);

Ottenere valore DI esteso
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene valore DI esteso
    * @param [in] DINum Numero DI
    * @param [in] isNoBlock Bloccante
    * @param [out] isOpen 0-Chiuso; 1-Aperto
    * @return Codice di errore
    */
    errno_t GetAuxDI(int DINum, bool isNoBlock, bool& isOpen);

Ottenere valore AI esteso
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene valore AI esteso
    * @param [in] AINum Numero AI
    * @param [in] isNoBlock Bloccante
    * @param [in] value Valore input
    * @return Codice di errore
    */
    errno_t GetAuxAI(int AINum, bool isNoBlock, int& value);

Esempio di codice per I/O esteso
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAuxDOAO(void)
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
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, true, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 128; i++)
      {
        robot.SetAuxDO(i, false, false, true);
        Sleep(100);
      }
      for (int i = 0; i < 409; i++)
      {
        robot.SetAuxAO(0, i * 10, true);
        robot.SetAuxAO(1, 4095 - i * 10, true);
        robot.SetAuxAO(2, i * 10, true);
        robot.SetAuxAO(3, 4095 - i * 10, true);
        Sleep(10);
      }
      robot.SetAuxDIFilterTime(10);
      robot.SetAuxAIFilterTime(0, 10);
      for (int i = 0; i < 20; i++)
      {
        bool curValue = false;
        int rtn = robot.GetAuxDI(i, false, curValue);
        cout << "DI" << i << "  " << curValue << endl;
      }
      int curValue = -1;
      for (int i = 0; i < 4; i++)
      {
        rtn = robot.GetAuxAI(i, true, curValue);
      }
      robot.WaitAuxDI(1, false, 1000, false);
      robot.WaitAuxAI(1, 1, 132, 1000, false);
      robot.CloseRPC();
      return 0;
    }

Abilitazione dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abilitazione dispositivo mobile
    * @param enable false-Disabilita; true-Abilitata
    * @return Codice di errore
    */
    errno_t TractorEnable(bool enable);

Azzeramento (Homing) dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Azzeramento (Homing) dispositivo mobile
    * @return Codice di errore
    */
    errno_t TractorHoming();

Movimento lineare dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Movimento lineare dispositivo mobile
    * @param distance Distanza movimento lineare (mm)
    * @param vel Percentuale velocità movimento lineare (0-100)
    * @return Codice di errore
    */
    errno_t TractorMoveL(double distance, double vel);

Movimento circolare dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento circolare dispositivo mobile
    * @param radio Raggio movimento circolare (mm)
    * @param angle Angolo movimento circolare (°)
    * @param vel Percentuale velocità movimento lineare (0-100)
    * @return Codice di errore
    */
    errno_t TractorMoveC(double radio, double angle, double vel);

Stop movimento dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Stop movimento dispositivo mobile
    * @return Codice di errore
    */
    errno_t TractorStop();

Esempio di codice per dispositivo mobile
+++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestTractor(void)
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
      robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1);
      robot.ExtDevLoadUDPDriver();
      rtn = robot.ExtAxisServoOn(1, 1);
      rtn = robot.ExtAxisServoOn(2, 1);
      robot.Sleep(2000);
      robot.ExtAxisSetHoming(1, 0, 10, 2);
      robot.Sleep(2000);
      rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);
      robot.Sleep(4000);
      robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
      robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);
      robot.TractorEnable(false);
      robot.Sleep(2000);
      robot.TractorEnable(true);
      robot.Sleep(2000);
      robot.TractorHoming();
      robot.Sleep(2000);
      robot.TractorMoveL(100, 2);
      robot.Sleep(5000);
      robot.TractorStop();
      robot.TractorMoveL(-100, 20);
      robot.Sleep(5000);
      robot.TractorMoveC(300, 90, 20);
      robot.Sleep(10000);
      robot.TractorMoveC(300, -90, 20);
      robot.Sleep(1);
      robot.CloseRPC();
      return 0;
    }