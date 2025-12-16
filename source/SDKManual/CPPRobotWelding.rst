Robot di Saldatura
==================

.. toctree::
   :maxdepth: 5

Impostare i parametri della curva del processo di saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri della curva del processo di saldatura
    * @param [in] id Numero del processo di saldatura (1-99)
    * @param [in] startCurrent Corrente di accensione dell'arco (A)
    * @param [in] startVoltage Tensione di accensione dell'arco (V)
    * @param [in] startTime Tempo di accensione dell'arco (ms)
    * @param [in] weldCurrent Corrente di saldatura (A)
    * @param [in] weldVoltage Tensione di saldatura (V)
    * @param [in] endCurrent Corrente di spegnimento dell'arco (A)
    * @param [in] endVoltage Tensione di spegnimento dell'arco (V)
    * @param [in] endTime Tempo di spegnimento dell'arco (ms)
    * @return Codice di errore
    */
   errno_t WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Ottenere i parametri della curva del processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene i parametri della curva del processo di saldatura
    * @param [in] id Numero del processo di saldatura (1-99)
    * @param [out] startCurrent Corrente di accensione dell'arco (A)
    * @param [out] startVoltage Tensione di accensione dell'arco (V)
    * @param [out] startTime Tempo di accensione dell'arco (ms)
    * @param [out] weldCurrent Corrente di saldatura (A)
    * @param [out] weldVoltage Tensione di saldatura (V)
    * @param [out] endCurrent Corrente di spegnimento dell'arco (A)
    * @param [out] endVoltage Tensione di spegnimento dell'arco (V)
    * @param [out] endTime Tempo di spegnimento dell'arco (ms)
    * @return Codice di errore
    */
   errno_t WeldingGetProcessParam(int id, double& startCurrent, double& startVoltage, double& startTime, double& weldCurrent, double& weldVoltage, double& endCurrent, double& endVoltage, double& endTime);

Impostare la relazione tra corrente di saldatura e uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la relazione tra corrente di saldatura e uscita analogica
    * @param [in] currentMin Valore corrente del punto sinistro della relazione lineare corrente-uscita analogica (A)
    * @param [in] currentMax Valore corrente del punto destro della relazione lineare corrente-uscita analogica (A)
    * @param [in] outputVoltageMin Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [in] outputVoltageMax Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   errno_t WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Impostare la relazione tra tensione di saldatura e uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la relazione tra tensione di saldatura e uscita analogica
    * @param [in] weldVoltageMin Valore di tensione di saldatura del punto sinistro della relazione lineare (V)
    * @param [in] weldVoltageMax Valore di tensione di saldatura del punto destro della relazione lineare (V)
    * @param [in] outputVoltageMin Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [in] outputVoltageMax Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   errno_t WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Ottenere la relazione tra corrente di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene la relazione tra corrente di saldatura e uscita analogica
    * @param [out] currentMin Valore corrente del punto sinistro della relazione lineare corrente-uscita analogica (A)
    * @param [out] currentMax Valore corrente del punto destro della relazione lineare corrente-uscita analogica (A)
    * @param [out] outputVoltageMin Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [out] outputVoltageMax Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   errno_t WeldingGetCurrentRelation(double *currentMin, double *currentMax, double *outputVoltageMin, double *outputVoltageMax);

Ottenere la relazione tra tensione di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene la relazione tra tensione di saldatura e uscita analogica
    * @param [out] weldVoltageMin Valore di tensione di saldatura del punto sinistro della relazione lineare (V)
    * @param [out] weldVoltageMax Valore di tensione di saldatura del punto destro della relazione lineare (V)
    * @param [out] outputVoltageMin Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [out] outputVoltageMax Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   errno_t WeldingGetVoltageRelation(double *weldVoltageMin, double *weldVoltageMax, double *outputVoltageMin, double *outputVoltageMax);

Impostare la corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la corrente di saldatura
    * @param [in] ioType Tipo IO di controllo 0-IO della centralina; 1-IO esteso
    * @param [in] current Valore della corrente di saldatura (A)
    * @param [in] AOIndex Porta di uscita analogica della centralina per il controllo della corrente di saldatura (0-1)
    * @param [in] blend Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   errno_t WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Impostare la tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la tensione di saldatura
    * @param [in] ioType Tipo IO di controllo 0-IO della centralina; 1-IO esteso
    * @param [in] voltage Valore della tensione di saldatura (V)
    * @param [in] AOIndex Porta di uscita analogica della centralina per il controllo della tensione di saldatura (0-1)
    * @param [in] blend Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   errno_t WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Impostare i parametri di oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione
    * @param [in] weaveNum Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] weaveType Tipo di oscillazione 0-Oscillazione a onda triangolare piana; 1-Oscillazione a onda triangolare L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione a onda sinusoidale piana; 5-Oscillazione a onda sinusoidale L verticale; 6-Oscillazione a onda triangolare verticale; 7-Oscillazione a onda sinusoidale verticale
    * @param [in] weaveFrequency Frequenza di oscillazione (Hz)
    * @param [in] weaveIncStayTime Modalità di attesa 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] weaveRange Ampiezza di oscillazione (mm)
    * @param [in] weaveLeftRange Lunghezza della corda sinistra per l'oscillazione triangolare verticale (mm)
    * @param [in] weaveRightRange Lunghezza della corda destra per l'oscillazione triangolare verticale (mm)
    * @param [in] additionalStayTime Tempo di permanenza nel punto del triangolo verticale (ms)
    * @param [in] weaveLeftStayTime Tempo di permanenza a sinistra (ms)
    * @param [in] weaveRightStayTime Tempo di permanenza a destra (ms)
    * @param [in] weaveCircleRadio Rapporto di ritorno per l'oscillazione circolare (0-100%)
    * @param [in] weaveStationary Attesa della posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione rimane ferma durante il tempo di attesa
    * @param [in] weaveYawAngle Angolo di direzione dell'oscillazione (rotazione attorno all'asse Z dell'oscillazione), unità °
    * @param [in] weaveRotAngle Angolo di rollio direzione oscillazione (rotazione attorno all'asse X oscillazione), unità °
    * @return Codice di errore
    */
   errno_t WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle = 0);

Esempio di codice per impostare i parametri di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestSetWeldParam(void)
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
      robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000);
      robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333);
      double startCurrent = 0;
      double startVoltage = 0;
      double startTime = 0;
      double weldCurrent = 0;
      double weldVoltage = 0;
      double endCurrent = 0;
      double endVoltage = 0;
      double endTime = 0;
      robot.WeldingGetProcessParam(1, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 1 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      robot.WeldingGetProcessParam(2, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
      cout << "the Num 2 process param is " << startCurrent << " " << startVoltage << " " << startTime << " " << weldCurrent << " " << weldVoltage << " " << endCurrent << " " << endVoltage << " " << endTime << endl;
      rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
      cout << "WeldingSetCurrentRelation rtn is: " << rtn << endl;
      rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
      cout << "WeldingSetVoltageRelation rtn is: " << rtn << endl;
      double current_min = 0;
      double current_max = 0;
      double vol_min = 0;
      double vol_max = 0;
      double output_vmin = 0;
      double output_vmax = 0;
      int curIndex = 0;
      int volIndex = 0;
      rtn = robot.WeldingGetCurrentRelation(&current_min, &current_max, &output_vmin, &output_vmax, &curIndex);
      cout << "WeldingGetCurrentRelation rtn is: " << rtn << endl;
      cout << "current min " << current_min << " current max " << current_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingGetVoltageRelation(&vol_min, &vol_max, &output_vmin, &output_vmax, &volIndex);
      cout << "WeldingGetVoltageRelation rtn is: " << rtn << endl;
      cout << "vol min " << vol_min << " vol max " << vol_max << " output vol min " << output_vmin << " output vol max " << output_vmax << endl;
      rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
      cout << "WeldingSetCurrent rtn is: " << rtn << endl;
      this_thread::sleep_for(chrono::seconds(3));
      rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
      cout << "WeldingSetVoltage rtn is: " << rtn << endl;
      rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
      cout << "rtn is: " << rtn << endl;
      robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);
      rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
      printf("WeldingSetCheckArcInterruptionParam  %d\n", rtn);
      rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
      printf("WeldingSetReWeldAfterBreakOffParam  %d\n", rtn);
      int enable = 0;
      double length = 0;
      double velocity = 0;
      int moveType = 0;
      int checkEnable = 0;
      int arcInterruptTimeLength = 0;
      rtn = robot.WeldingGetCheckArcInterruptionParam(&checkEnable, &arcInterruptTimeLength);
      printf("WeldingGetCheckArcInterruptionParam checkEnable %d  arcInterruptTimeLength %d\n", checkEnable, arcInterruptTimeLength);
      rtn = robot.WeldingGetReWeldAfterBreakOffParam(&enable, &length, &velocity, &moveType);
      printf("WeldingGetReWeldAfterBreakOffParam enable = %d, length = %lf, velocity = %lf, moveType = %d\n", enable, length, velocity, moveType);
      robot.SetWeldMachineCtrlModeExtDoNum(17);
      for (int i = 0; i < 5; i++)
      {
        robot.SetWeldMachineCtrlMode(0);
        robot.Sleep(1000);
        robot.SetWeldMachineCtrlMode(1);
        robot.Sleep(1000);
      }
      robot.CloseRPC();
      return 0;
    }

Impostare i parametri di oscillazione in tempo reale
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione in tempo reale
    * @param [in] weaveNum Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] weaveType Tipo di oscillazione 0-Oscillazione a onda triangolare piana; 1-Oscillazione a onda triangolare L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione a onda sinusoidale piana; 5-Oscillazione a onda sinusoidale L verticale; 6-Oscillazione a onda triangolare verticale; 7-Oscillazione a onda sinusoidale verticale
    * @param [in] weaveFrequency Frequenza di oscillazione (Hz)
    * @param [in] weaveIncStayTime Modalità di attesa 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] weaveRange Ampiezza di oscillazione (mm)
    * @param [in] weaveLeftStayTime Tempo di permanenza a sinistra (ms)
    * @param [in] weaveRightStayTime Tempo di permanenza a destra (ms)
    * @param [in] weaveCircleRadio Rapporto di ritorno per l'oscillazione circolare (0-100%)
    * @param [in] weaveStationary Attesa della posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione rimane ferma durante il tempo di attesa
    * @return Codice di errore
    */
   errno_t WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Impostare i parametri di rilevamento dell'interruzione dell'arco di saldatura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
    * @param [in] checkEnable Abilita il rilevamento; 0-Disabilitato; 1-Abilitato
    * @param [in] arcInterruptTimeLength Durata di conferma dell'interruzione dell'arco (ms)
    * @return Codice di errore
    */
   errno_t WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Ottenere i parametri di rilevamento dell'interruzione dell'arco di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
    * @param [out] checkEnable Abilita il rilevamento; 0-Disabilitato; 1-Abilitato
    * @param [out] arcInterruptTimeLength Durata di conferma dell'interruzione dell'arco (ms)
    * @return Codice di errore
    */
   errno_t WeldingGetCheckArcInterruptionParam(int* checkEnable, int* arcInterruptTimeLength);

Impostare i parametri di recupero dell'interruzione di saldatura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri di recupero dell'interruzione di saldatura del robot
    * @param [in] enable Abilita il recupero dell'interruzione di saldatura
    * @param [in] length Distanza di sovrapposizione della saldatura (mm)
    * @param [in] velocity Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    * @param [in] moveType Metodo di movimento del robot verso il punto di riaccensione; 0-LIN; 1-PTP
    * @return Codice di errore
    */
   errno_t WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Ottenere i parametri di recupero dell'interruzione di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene i parametri di recupero dell'interruzione di saldatura del robot
    * @param [out] enable Abilita il recupero dell'interruzione di saldatura
    * @param [out] length Distanza di sovrapposizione della saldatura (mm)
    * @param [out] velocity Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    * @param [out] moveType Metodo di movimento del robot verso il punto di riaccensione; 0-LIN; 1-PTP
    * @return Codice di errore
    */
   errno_t WeldingGetReWeldAfterBreakOffParam(int* enable, double* length, double* velocity, int* moveType);

Impostare la porta DO estesa per la modalità di controllo della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la porta DO estesa per la modalità di controllo della saldatrice
    * @param DONum Porta DO per la modalità di controllo della saldatrice (0-127)
    * @return Codice di errore
    */
   errno_t SetWeldMachineCtrlModeExtDoNum(int DONum);

Impostare la modalità di controllo della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la modalità di controllo della saldatrice
    * @param mode Modalità di controllo della saldatrice; 0-Unitaria
    * @return Codice di errore
    */
   errno_t SetWeldMachineCtrlMode(int mode);

Inizio della saldatura
++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia la saldatura
    * @param [in] ioType Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] arcNum Numero del file di configurazione della saldatrice
    * @param [in] timeout Tempo di timeout per l'accensione dell'arco
    * @return Codice di errore
    */
   errno_t ARCStart(int ioType, int arcNum, int timeout);

Fine della saldatura
++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina la saldatura
    * @param [in] ioType Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] arcNum Numero del file di configurazione della saldatrice
    * @param [in] timeout Tempo di timeout per lo spegnimento dell'arco
    * @return Codice di errore
    */
   errno_t ARCEnd(int ioType, int arcNum, int timeout);

Inizio dell'oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia l'oscillazione
    * @param [in] weaveNum Numero di configurazione dei parametri di saldatura oscillante
    * @return Codice di errore
    */
   errno_t WeaveStart(int weaveNum);

Fine dell'oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina l'oscillazione
    * @param [in] weaveNum Numero di configurazione dei parametri di saldatura oscillante
    * @return Codice di errore
    */
   errno_t WeaveEnd(int weaveNum);

Alimentazione del filo in avanti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Alimentazione del filo in avanti
    * @param [in] ioType Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] wireFeed Controllo alimentazione filo 0-Ferma alimentazione filo; 1-Alimenta filo
    * @return Codice di errore
    */
   errno_t SetForwardWireFeed(int ioType, int wireFeed);

Alimentazione del filo all'indietro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Alimentazione del filo all'indietro
    * @param [in] ioType Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] wireFeed Controllo alimentazione filo 0-Ferma alimentazione filo; 1-Alimenta filo
    * @return Codice di errore
    */
   errno_t SetReverseWireFeed(int ioType, int wireFeed);

Alimentazione del gas
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Alimentazione del gas
    * @param [in] ioType Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] airControl Controllo alimentazione gas 0-Ferma alimentazione gas; 1-Alimenta gas
    * @return Codice di errore
    */
   errno_t SetAspirated(int ioType, int airControl);

Impostare il recupero della saldatura dopo l'interruzione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta il recupero della saldatura dopo l'interruzione del robot
    * @return Codice di errore
    */
   errno_t WeldingStartReWeldAfterBreakOff();

Impostare l'uscita dalla saldatura dopo l'interruzione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta l'uscita dalla saldatura dopo l'interruzione del robot
    * @return Codice di errore
    */
   errno_t WeldingAbortWeldAfterBreakOff();

Esempio di codice per controllo saldatura robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestWelding(void)
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
      robot.SetForwardWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetForwardWireFeed(0, 0);
      robot.SetReverseWireFeed(0, 1);
      robot.Sleep(1000);
      robot.SetReverseWireFeed(0, 0);
      robot.SetAspirated(0, 1);
      robot.Sleep(1000);
      robot.SetAspirated(0, 0);
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.WeaveStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.ARCEnd(1, 0, 10000);
      robot.WeaveEnd(0);
      robot.WeldingStartReWeldAfterBreakOff();
      robot.WeldingAbortWeldAfterBreakOff();
      robot.CloseRPC();
      return 0;
    }

Inizio della saldatura a segmenti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.1.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia la saldatura a segmenti
    * @param [in] startDesePos Posizione cartesiana del punto di inizio
    * @param [in] endDesePos Posa cartesiana del punto di fine
    * @param [in] startJPos Posa articolare del punto di inizio
    * @param [in] endJPos Posa articolare del punto di fine
    * @param [in] weldLength Lunghezza del segmento di saldatura (mm)
    * @param [in] noWeldLength Lunghezza del segmento non saldato (mm)
    * @param [in] weldIOType Tipo IO di saldatura (0-IO della centralina; 1-IO esteso)
    * @param [in] arcNum Numero del file di configurazione della saldatrice
    * @param [in] weldTimeout Tempo di timeout per accensione/spegnimento dell'arco
    * @param [in] isWeave Se oscillare
    * @param [in] weaveNum Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] tool Numero sistema coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale di velocità, range [0~100]
    * @param [in] acc Percentuale di accelerazione, range [0~100], attualmente non disponibile
    * @param [in] ovl Fattore di scala della velocità, range [0~100]
    * @param [in] blendR [-1.0]-Movimento fino a destinazione (bloccante), [0~1000.0]-Raggio di levigatura (non bloccante), unità mm
    * @param [in] epos Posizione degli assi estesi, unità mm
    * @param [in] search 0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param [in] offset_flag 0-Nessun offset, 1-Offset nel sistema di coordinate base/pezzo, 2-Offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità di offset della posa
    * @return Codice di errore
    */
   errno_t SegmentWeldStart(DescPose *startDesePos, DescPose *endDesePos, JointPos *startJPos, JointPos *endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout, bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos);

Esempio di codice per saldatura a segmenti del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
   :linenos:

    int TestSegWeld(void)
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
      robot.WeldingSetCurrent(1, 230, 0, 0);
      robot.WeldingSetVoltage(1, 24, 0, 1);
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      rtn = robot.SegmentWeldStart(&p1Desc, &p2Desc, &p1Joint, &p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      printf("SegmentWeldStart rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Inizio della simulazione di oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia la simulazione di oscillazione
    * @param [in] weaveNum Numero dei parametri di oscillazione
    * @return Codice di errore
    */
   errno_t WeaveStartSim(int weaveNum);

Fine della simulazione di oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina la simulazione di oscillazione
    * @param [in] weaveNum Numero dei parametri di oscillazione
    * @return Codice di errore
    */
   errno_t WeaveEndSim(int weaveNum);

Inizio del rilevamento di traiettoria di allarme (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia il rilevamento di traiettoria di allarme (senza movimento)
    * @param [in] weaveNum Numero dei parametri di oscillazione
    * @return Codice di errore
    */
   errno_t WeaveInspectStart(int weaveNum);

Fine del rilevamento di traiettoria di allarme (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina il rilevamento di traiettoria di allarme (senza movimento)
    * @param [in] weaveNum Numero dei parametri di oscillazione
    * @return Codice di errore
    */
   errno_t WeaveInspectEnd(int weaveNum);

Inizio della transizione graduale di oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia la transizione graduale di oscillazione
    * @param [in] weaveChangeFlag 1-Cambia parametri di oscillazione; 2-Cambia parametri di oscillazione + velocità di saldatura
    * @param [in] weaveNum Numero di oscillazione
    * @param [in] velStart Velocità di inizio saldatura, (cm/min)
    * @param [in] velEnd Velocità di fine saldatura, (cm/min)
    * @return Codice di errore
    */
   errno_t WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Esempio di codice per saldatura con transizione graduale di oscillazione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestWeave(void)
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
      DescPose p1Desc(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
      JointPos p1Joint(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);
      DescPose p2Desc(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
      JointPos p2Joint(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveStartSim(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveEndSim(0);
      robot.MoveJ(&p1Joint, &p1Desc, 13, 0, 20, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.WeaveInspectStart(0);
      robot.MoveL(&p2Joint, &p2Desc, 13, 0, 20, 100, 100, -1, 0, &exaxisPos, 0, 0, &offdese);
      robot.WeaveInspectEnd(0);
      robot.WeldingSetVoltage(1, 19, 0, 0);
      robot.WeldingSetCurrent(1, 190, 0, 0);
      robot.MoveL(&p1Joint, &p1Desc, 1, 1, 100, 100, 50, -1, &exaxisPos, 0, 0, &offdese);
      robot.ARCStart(1, 0, 10000);
      robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.WeaveStart(0);
      robot.WeaveChangeStart(1, 0, 50, 30);
      robot.MoveL(&p2Joint, &p2Desc, 1, 1, 100, 100, 1, -1, &exaxisPos, 0, 0, &offdese);
      robot.WeaveChangeEnd();
      robot.WeaveEnd(0);
      robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
      robot.ARCEnd(1, 0, 10000);
      robot.CloseRPC();
      return 0;
    }

Fine della transizione graduale di oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.2.0-3.8.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina la transizione graduale di oscillazione
    * @return Codice di errore
    */
   errno_t WeaveChangeEnd();

IO esteso - Configurare il segnale di rilevamento del gas della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di rilevamento del gas della saldatrice
    * @param [in] DONum Numero DO esteso per il segnale di rilevamento del gas
    * @return Codice di errore
    */
   errno_t SetAirControlExtDoNum(int DONum);

IO esteso - Configurare il segnale di accensione dell'arco della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di accensione dell'arco della saldatrice
    * @param [in] DONum Numero DO esteso per il segnale di accensione dell'arco
    * @return Codice di errore
    */
   errno_t SetArcStartExtDoNum(int DONum);

IO esteso - Configurare il segnale di alimentazione all'indietro del filo della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di alimentazione all'indietro del filo della saldatrice
    * @param [in] DONum Numero DO esteso per il segnale di alimentazione all'indietro del filo
    * @return Codice di errore
    */
   errno_t SetWireReverseFeedExtDoNum(int DONum);

IO esteso - Configurare il segnale di alimentazione in avanti del filo della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di alimentazione in avanti del filo della saldatrice
    * @param [in] DONum Numero DO esteso per il segnale di alimentazione in avanti del filo
    * @return Codice di errore
    */
   errno_t SetWireForwardFeedExtDoNum(int DONum);

IO esteso - Configurare il segnale di successo dell'accensione dell'arco della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di successo dell'accensione dell'arco della saldatrice
    * @param [in] DINum Numero DI esteso per il segnale di successo dell'accensione dell'arco
    * @return Codice di errore
    */
   errno_t SetArcDoneExtDiNum(int DINum);

IO esteso - Configurare il segnale di pronto della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di pronto della saldatrice
    * @param [in] DINum Numero DI esteso per il segnale di pronto della saldatrice
    * @return Codice di errore
    */
   errno_t SetWeldReadyExtDiNum(int DINum);

IO esteso - Configurare i segnali di recupero dell'interruzione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief IO esteso - Configura i segnali di recupero dell'interruzione di saldatura
    * @param [in] reWeldDINum Numero DI esteso per il segnale di recupero della saldatura dopo interruzione
    * @param [in] abortWeldDINum Numero DI esteso per il segnale di uscita dalla saldatura dopo interruzione
    * @return Codice di errore
    */
   errno_t SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Esempio di codice per impostare i segnali di saldatura IO estesi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestExtDIConfig(void)
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
      robot.SetArcStartExtDoNum(10);
      robot.SetAirControlExtDoNum(20);
      robot.SetWireForwardFeedExtDoNum(30);
      robot.SetWireReverseFeedExtDoNum(40);
      robot.SetWeldReadyExtDiNum(50);
      robot.SetArcDoneExtDiNum(60);
      robot.SetExtDIWeldBreakOffRecover(70, 80);
      robot.SetWireSearchExtDIONum(0, 1);
      robot.CloseRPC();
      return 0;
    }

Controllo del tracciamento dell'arco
++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Controllo del tracciamento dell'arco
    * @param [in] flag Interruttore, 0-Spegnere; 1-Accendere
    * @param [in] dalayTime Tempo di ritardo, unità ms
    * @param [in] isLeftRight Compensazione deviazione sinistra-destra
    * @param [in] klr Coefficiente di regolazione sinistra-destra (sensibilità)
    * @param [in] tStartLr Tempo di inizio compensazione sinistra-destra cyc
    * @param [in] stepMaxLr Compensazione massima per volta sinistra-destra mm
    * @param [in] sumMaxLr Compensazione totale massima sinistra-destra mm
    * @param [in] isUpLow Compensazione deviazione alto-basso
    * @param [in] kud Coefficiente di regolazione alto-basso (sensibilità)
    * @param [in] tStartUd Tempo di inizio compensazione alto-basso cyc
    * @param [in] stepMaxUd Compensazione massima per volta alto-basso mm
    * @param [in] sumMaxUd Compensazione totale massima alto-basso mm
    * @param [in] axisSelect Selezione sistema coordinate alto-basso, 0-Oscillazione; 1-Utensile; 2-Base
    * @param [in] referenceType Metodo impostazione corrente di riferimento alto-basso, 0-Retroazione; 1-Costante
    * @param [in] referSampleStartUd Conteggio inizio campionamento corrente di riferimento alto-basso (retroazione), cyc
    * @param [in] referSampleCountUd Conteggio ciclo campionamento corrente di riferimento alto-basso (retroazione), cyc
    * @param [in] referenceCurrent Corrente di riferimento alto-basso mA
    * @param [in] offsetType Tipo di tracciamento offset, 0-Nessun offset; 1-Campionamento; 2-Percentuale
    * @param [in] offsetParameter Parametro offset; Campionamento (tempo di inizio campionamento offset, per default campiona un ciclo); Percentuale (percentuale offset (-100 ~ 100))
    * @return Codice di errore
    */
   errno_t ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType = 0, int offsetParameter = 0);

Impostare la porta di ingresso del segnale per il tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la porta di ingresso del segnale per il tracciamento dell'arco
    * @param [in] channel Selezione banda passante AI per il tracciamento dell'arco, [0-3]
    * @return Codice di errore
    */
   errno_t ArcWeldTraceExtAIChannelConfig(int channel);

Attivazione tracciamento arco + compensazione multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Attiva tracciamento arco + compensazione multi-strato multi-passata
    * @return Codice di errore
    */
   errno_t ArcWeldTraceReplayStart();

Disattivazione tracciamento arco + compensazione multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Disattiva tracciamento arco + compensazione multi-strato multi-passata
    * @return Codice di errore
    */
   errno_t ArcWeldTraceReplayEnd();

Trasformazione delle coordinate di offset - Saldatura multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Trasformazione delle coordinate di offset - Saldatura multi-strato multi-passata
    * @return Codice di errore
    */
   errno_t MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, DescPose& offset);

Esempio di codice per il tracciamento dell'arco nella saldatura multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestArcWeldTrace(void)
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
      JointPos mulitilineorigin1_joint(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
      DescPose mulitilineorigin1_desc(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);
      DescTran mulitilineX1_desc;
      mulitilineX1_desc.x = -677.556;
      mulitilineX1_desc.y = 211.949;
      mulitilineX1_desc.z = -1.206;
      DescTran mulitilineZ1_desc;
      mulitilineZ1_desc.x = -677.564;
      mulitilineZ1_desc.y = 190.956;
      mulitilineZ1_desc.z = 19.817;
      JointPos mulitilinesafe_joint(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
      DescPose mulitilinesafe_desc(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
      JointPos mulitilineorigin2_joint(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
      DescPose mulitilineorigin2_desc(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);
      DescTran mulitilineX2_desc;
      mulitilineX2_desc.x = -563.965;
      mulitilineX2_desc.y = 220.355;
      mulitilineX2_desc.z = -0.680;
      DescTran mulitilineZ2_desc;
      mulitilineZ2_desc.x = -563.968;
      mulitilineZ2_desc.y = 215.362;
      mulitilineZ2_desc.z = 4.331;
      ExaxisPos epos(0, 0, 0, 0);
      DescPose offset(0, 0, 0, 0, 0, 0);
      robot.Sleep(10);
      int error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.WeaveStart(0);
      printf("WeaveStart return: %d\n", error);
      error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, &epos, 0, 0, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
      printf("ArcWeldTraceControl return: %d\n", error);
      error = robot.WeaveEnd(0);
      printf("WeaveEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("ArcWeldTraceReplayStart return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 10000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.MoveL(&mulitilineorigin1_joint, &mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ARCStart(1, 0, 3000);
      printf("ARCStart return: %d\n", error);
      error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);
      printf("MultilayerOffsetTrsfToBase return: %d offect is %f %f %f \n", error, offset.tran.x, offset.tran.y, offset.tran.z);
      error = robot.ArcWeldTraceReplayStart();
      printf("MoveJ return: %d\n", error);
      error = robot.MoveL(&mulitilineorigin2_joint, &mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, &epos, 0, 1, &offset, 0, 100);
      printf("MoveL return: %d\n", error);
      error = robot.ArcWeldTraceReplayEnd();
      printf("ArcWeldTraceReplayEnd return: %d\n", error);
      error = robot.ARCEnd(1, 0, 3000);
      printf("ARCEnd return: %d\n", error);
      error = robot.MoveJ(&mulitilinesafe_joint, &mulitilinesafe_desc, 13, 0, 10, 100, 100, &epos, -1, 0, &offset);
      printf("MoveJ return: %d\n", error);
      robot.CloseRPC();
      return 0;
    }

Selezione canale AI per la retroazione della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Selezione canale AI per la retroazione della corrente della saldatrice nel tracciamento dell'arco
    * @param [in] channel Canale; 0-AI esteso 0; 1-AI esteso 1; 2-AI esteso 2; 3-AI esteso 3; 4-AI centralina 0; 5-AI centralina 1
    * @return Codice di errore
    */
   errno_t ArcWeldTraceAIChannelCurrent(int channel);

Selezione canale AI per la retroazione della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Selezione canale AI per la retroazione della tensione della saldatrice nel tracciamento dell'arco
    * @param [in] channel Canale; 0-AI esteso 0; 1-AI esteso 1; 2-AI esteso 2; 3-AI esteso 3; 4-AI centralina 0; 5-AI centralina 1
    * @return Codice di errore
    */
   errno_t ArcWeldTraceAIChannelVoltage(int channel);

Parametri di conversione per la retroazione della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Parametri di conversione per la retroazione della corrente della saldatrice nel tracciamento dell'arco
    * @param [in] AILow Limite inferiore canale AI, valore predefinito 0V, range [0-10V]
    * @param [in] AIHigh Limite superiore canale AI, valore predefinito 10V, range [0-10V]
    * @param [in] currentLow Valore di corrente della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, range [0-200V]
    * @param [in] currentHigh Valore di corrente della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, range [0-200V]
    * @return Codice di errore
    */
   errno_t ArcWeldTraceCurrentPara(float AILow, float AIHigh, float currentLow, float currentHigh);

Parametri di conversione per la retroazione della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Parametri di conversione per la retroazione della tensione della saldatrice nel tracciamento dell'arco
    * @param [in] AILow Limite inferiore canale AI, valore predefinito 0V, range [0-10V]
    * @param [in] AIHigh Limite superiore canale AI, valore predefinito 10V, range [0-10V]
    * @param [in] voltageLow Valore di tensione della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, range [0-200V]
    * @param [in] voltageHigh Valore di tensione della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, range [0-200V]
    * @return Codice di errore
    */
   errno_t ArcWeldTraceVoltagePara(float AILow, float AIHigh, float voltageLow, float voltageHigh);

Esempio di codice per il tracciamento dell'arco
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int WeldTraceControlWithCtrlBoxAI(FRRobot* robot)
    {
      DescPose startdescPose = { -473.86, 257.879, -20.849, -37.317, -42.021, 2.543 };
      JointPos startjointPos = { -43.487, -76.526, 95.568, -104.445, -89.356, 3.72 };

      DescPose enddescPose = { -499.844, 141.225, 7.72, -34.856, -40.17, 13.13 };
      JointPos endjointPos = { -31.305, -82.998, 99.401, -104.426, -89.35, 3.696 };

      DescPose safedescPose = { -504.043, 275.181, 40.908, -28.002, -42.025, -14.044 };
      JointPos safejointPos = { -39.078, -76.732, 87.227, -99.47, -94.301, 18.714 };

      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);

      robot->WeldingSetVoltage(0, 25, 1, 0);// ----Imposta tensione
      robot->WeldingSetCurrent(0, 260, 0, 0);// ----Imposta corrente

      int rtn = robot->ArcWeldTraceAIChannelCurrent(4);
      cout << "ArcWeldTraceAIChannelCurrent rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceAIChannelVoltage(5);
      cout << "ArcWeldTraceAIChannelVoltage rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceCurrentPara(0, 5, 0, 500);
      cout << "ArcWeldTraceCurrentPara rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
      cout << "ArcWeldTraceVoltagePara rtn is " << rtn << endl;
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      return 0;
    }

Impostare le porte IO estese per la ricerca del filo
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta le porte IO estese per la ricerca del filo
    * @param searchDoneDINum Porta DO per il successo della ricerca del filo (0-127)
    * @param searchStartDONum Porta DO per il controllo avvio/arresto della ricerca del filo (0-127)
    * @return Codice di errore
    */
   errno_t SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Programma di esempio
++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

    void TestUDPWireSearch(FRRobot* robot)
    {
    robot->ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10);
    robot->ExtDevLoadUDPDriver();

    robot->SetWireSearchExtDIONum(0, 0);

    int rtn0, rtn1, rtn2 = 0;
    ExaxisPos exaxisPos = { 0.0, 0.0, 0.0, 0.0 };
    DescPose offdese = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };

    DescPose descStart = { -158.767, -510.596, 271.709, -179.427, -0.745, -137.349 };
    JointPos jointStart = { 61.667, -79.848, 108.639, -119.682, -89.700, -70.985 };

    DescPose descEnd = { 0.332, -516.427, 270.688, 178.165, 0.017, -119.989 };
    JointPos jointEnd = { 79.021, -81.839, 110.752, -118.298, -91.729, -70.981 };

    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);

    DescPose descREF0A = { -66.106, -560.746, 270.381, 176.479, -0.126, -126.745 };
    JointPos jointREF0A = { 73.531, -75.588, 102.941, -116.250, -93.347, -69.689 };

    DescPose descREF0B = { -66.109, -528.440, 270.407, 176.479, -0.129, -126.744 };
    JointPos jointREF0B = { 72.534, -79.625, 108.046, -117.379, -93.366, -70.687 };

    DescPose descREF1A = { 72.975, -473.242, 270.399, 176.479, -0.129, -126.744 };
    JointPos jointREF1A = { 87.169, -86.509, 115.710, -117.341, -92.993, -56.034 };

    DescPose descREF1B = { 31.355, -473.238, 270.405, 176.480, -0.130, -126.745 };
    JointPos jointREF1B = { 82.117, -87.146, 116.470, -117.737, -93.145, -61.090 };

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
    rtn1 = robot->WireSearchWait("REF0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
    rtn1 = robot->WireSearchWait("REF1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF0A, &descREF0A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
    robot->MoveL(&jointREF0B, &descREF0B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
    rtn1 = robot->WireSearchWait("RES0");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    rtn0 = robot->WireSearchStart(0, 10, 100, 0, 10, 100, 0);
    robot->MoveL(&jointREF1A, &descREF1A, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
    robot->MoveL(&jointREF1B, &descREF1B, 1, 0, 10, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
    rtn1 = robot->WireSearchWait("RES1");
    rtn2 = robot->WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

    vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
    vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
    int offectFlag = 0;
    DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
    rtn0 = robot->GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
    robot->PointsOffsetEnable(0, &offectPos);
    robot->MoveL(&jointStart, &descStart, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->MoveL(&jointEnd, &descEnd, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
    robot->PointsOffsetDisable();
    }

Inizio della ricerca del filo
+++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Inizia la ricerca del filo
    * @param [in] refPos 1-Punto di riferimento 0-Punto di contatto
    * @param [in] searchVel Velocità di ricerca %
    * @param [in] searchDis Distanza di ricerca mm
    * @param [in] autoBackFlag Flag ritorno automatico, 0-Non automatico; -Automatico
    * @param [in] autoBackVel Velocità di ritorno automatico %
    * @param [in] autoBackDis Distanza di ritorno automatico mm
    * @param [in] offectFlag 1-Ricerca con offset; 0-Ricerca al punto insegnato
    * @return Codice di errore
    */
   errno_t WireSearchStart(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Fine della ricerca del filo
+++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Termina la ricerca del filo
    * @param [in] refPos 1-Punto di riferimento 2-Punto di contatto
    * @param [in] searchVel Velocità di ricerca %
    * @param [in] searchDis Distanza di ricerca mm
    * @param [in] autoBackFlag Flag ritorno automatico, 0-Non automatico; -Automatico
    * @param [in] autoBackVel Velocità di ritorno automatico %
    * @param [in] autoBackDis Distanza di ritorno automatico mm
    * @param [in] offectFlag 1-Ricerca con offset; 2-Ricerca al punto insegnato
    * @return Codice di errore
    */
   errno_t WireSearchEnd(int refPos, float searchVel, int searchDis, int autoBackFlag, float autoBackVel, int autoBackDis, int offectFlag);

Calcolare l'offset della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Calcola l'offset della ricerca del filo
    * @param [in] seamType Tipo di giunzione
    * @param [in] method Metodo di calcolo
    * @param [in] varNameRef Punti di riferimento 1-6, "#" indica nessuna variabile punto
    * @param [in] varNameRes Punti di contatto 1-6, "#" indica nessuna variabile punto
    * @param [out] offectFlag 0-L'offset viene aggiunto direttamente ai punti di comando; 1-L'offset richiede una trasformazione delle coordinate dei punti di comando
    * @param [out] offect Posa offset [x, y, z, a, b, c]
    * @return Codice di errore
    */
   errno_t GetWireSearchOffset(int seamType, int method, std::vector<std::string> varNameRef, std::vector<std::string> varNameRes, int& offectFlag, DescPose& offect);

Attendere il completamento della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Attende il completamento della ricerca del filo
    * @return Codice di errore
    */
   errno_t WireSearchWait(std::string varName);

Scrivere il punto di contatto della ricerca del filo nel database
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief Scrive il punto di contatto della ricerca del filo nel database
    * @param [in] varName Nome del punto di contatto "RES0" ~ "RES99"
    * @param [in] pos Dati del punto di contatto [x, y, z, a, b, c]
    * @return Codice di errore
    */
   errno_t SetPointToDatabase(std::string varName, DescPose pos);

Esempio di codice per la ricerca del filo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

    int TestWireSearch(void)
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
      DescPose toolCoord(0, 0, 200, 0, 0, 0);
      robot.SetToolCoord(1, &toolCoord, 0, 0, 1, 0);
      DescPose wobjCoord(0, 0, 0, 0, 0, 0);
      robot.SetWObjCoord(1, &wobjCoord, 0);
      int rtn0, rtn1, rtn2 = 0;
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };
      DescPose descStart = { 216.543, 445.175, 93.465, 179.683, 1.757, -112.641 };
      JointPos jointStart = { -128.345, -86.660, 114.679, -119.625, -89.219, 74.303 };
      DescPose descEnd = { 111.143, 523.384, 87.659, 179.703, 1.835, -97.750 };
      JointPos jointEnd = { -113.454, -81.060, 109.328, -119.954, -89.218, 74.302 };
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      DescPose descREF0A = { 142.135, 367.604, 86.523, 179.728, 1.922, -111.089 };
      JointPos jointREF0A = { -126.794, -100.834, 128.922, -119.864, -89.218, 74.302 };
      DescPose descREF0B = { 254.633, 463.125, 72.604, 179.845, 2.341, -114.704 };
      JointPos jointREF0B = { -130.413, -81.093, 112.044, -123.163, -89.217, 74.303 };
      DescPose descREF1A = { 92.556, 485.259, 47.476, -179.932, 3.130, -97.512 };
      JointPos jointREF1A = { -113.231, -83.815, 119.877, -129.092, -89.217, 74.303 };
      DescPose descREF1B = { 203.103, 583.836, 63.909, 179.991, 2.854, -103.372 };
      JointPos jointREF1B = { -119.088, -69.676, 98.692, -121.761, -89.219, 74.303 };
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
      rtn1 = robot.WireSearchWait("REF0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
      rtn1 = robot.WireSearchWait("REF1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF0A, &descREF0A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
      robot.MoveL(&jointREF0B, &descREF0B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
      rtn1 = robot.WireSearchWait("RES0");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
      robot.MoveL(&jointREF1A, &descREF1A, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese); //Punto di partenza
      robot.MoveL(&jointREF1B, &descREF1B, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese); //Punto direzione
      rtn1 = robot.WireSearchWait("RES1");
      rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);
      vector <string> varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
      vector <string> varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
      int offectFlag = 0;
      DescPose offectPos = { 0, 0, 0, 0, 0, 0 };
      rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectFlag, offectPos);
      robot.PointsOffsetEnable(0, &offectPos);
      robot.MoveL(&jointStart, &descStart, 1, 1, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese);
      robot.MoveL(&jointEnd, &descEnd, 1, 1, 100, 100, 100, -1, &exaxisPos, 1, 0, &offdese);
      robot.PointsOffsetDisable();
      robot.CloseRPC();
      return 0;
    }

Impostare l'inizio della transizione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta l'inizio della transizione graduale della tensione di saldatura
    * @param [in] IOType Tipo di controllo; 0-IO della centralina; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    * @param [in] voltageStart Tensione di saldatura iniziale (V)
    * @param [in] voltageEnd Tensione di saldatura finale (V)
    * @param [in] AOIndex Numero porta AO della centralina (0-1)
    * @param [in] blend Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   errno_t WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Impostare la fine della transizione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la fine della transizione graduale della tensione di saldatura
    * @return Codice di errore
    */
   errno_t WeldingSetVoltageGradualChangeEnd();

Impostare l'inizio della transizione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta l'inizio della transizione graduale della corrente di saldatura
    * @param [in] IOType Tipo di controllo; 0-IO della centralina; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    * @param [in] currentStart Corrente di saldatura iniziale (A)
    * @param [in] currentEnd Corrente di saldatura finale (A)
    * @param [in] AOIndex Numero porta AO della centralina (0-1)
    * @param [in] blend Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   errno_t WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Impostare la fine della transizione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta la fine della transizione graduale della corrente di saldatura
    * @return Codice di errore
    */
   errno_t WeldingSetCurrentGradualChangeEnd();

Esempio di codice per la transizione graduale di corrente e tensione di saldatura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int WeldparamChange(FRRobot* robot)
    {
      DescPose startdescPose = { -484.707, 276.996, -14.013, -37.657, -40.508, -1.548 };
      JointPos startjointPos = { -45.421, -75.673, 93.627, -104.302, -87.938, 6.005 };

      DescPose enddescPose = { -508.767, 137.109, -13.966, -37.639, -40.508, -1.559 };
      JointPos endjointPos = { -32.768, -80.947, 100.254, -106.201, -87.201, 18.648 };

      DescPose safedescPose = { -484.709, 294.436, 13.621, -37.660, -40.508, -1.545 };
      JointPos safejointPos = { -46.604, -75.410, 89.109, -100.003, -88.012, 4.823 };
      ExaxisPos exaxisPos = { 0, 0, 0, 0 };
      DescPose offdese = { 0, 0, 0, 0, 0, 0 };

      robot->WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot->WeldingSetVoltageRelation(10, 45, 1, 10, 1);
      robot->MoveJ(&safejointPos, &safedescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);
      int rtn = robot->WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
      cout << "WeldingSetCurrentGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
      cout << "WeldingSetVoltageGradualChangeStart rtn is " << rtn << endl;
      rtn = robot->ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      cout << "ArcWeldTraceControl rtn is " << rtn << endl;
      robot->MoveJ(&startjointPos, &startdescPose, 1, 0, 5, 100, 100, &exaxisPos, -1, 0, &offdese);

      robot->ARCStart(0, 0, 10000);
      robot->WeaveStart(0);
      robot->WeaveChangeStart(2, 1, 24, 36);
      robot->MoveL(&endjointPos, &enddescPose, 1, 0, 100, 100, 2, -1, &exaxisPos, 0, 0, &offdese);
      robot->ARCEnd(0, 0, 10000);
      robot->WeaveChangeEnd();
      robot->WeaveEnd(0);
      robot->ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot->WeldingSetCurrentGradualChangeEnd();
      robot->WeldingSetVoltageGradualChangeEnd();
      return 0;
    }

Impostare i parametri di oscillazione personalizzati
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione personalizzati
    * @param [in] id Numero di oscillazione personalizzata: 0-2
    * @param [in] pointNum Numero di punti di oscillazione 0-10
    * @param [in] point Dati dei punti di estremità del movimento x,y,z
    * @param [in] stayTime Tempi di permanenza nell'oscillazione ms
    * @param [in] frequency Frequenza di oscillazione Hz
    * @param [in] incStayType Modalità di attesa: 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] stationary Attesa della posizione di oscillazione: 0-Continua a muoversi durante il tempo di attesa; 1-Posizione ferma durante il tempo di attesa
    * @return Codice di errore
    */
   errno_t CustomWeaveSetPara(int id, int pointNum, DescTran point[10], double stayTime[10], double frequency, int incStayType, int stationary);

Ottenere i parametri di oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene i parametri di oscillazione personalizzati
    * @param [in] id Numero di oscillazione personalizzata: 0-2
    * @param [out] pointNum Numero di punti di oscillazione 0-10
    * @param [out] point Dati dei punti di estremità del movimento x,y,z
    * @param [out] stayTime Tempi di permanenza nell'oscillazione ms
    * @param [out] frequency Frequenza di oscillazione Hz
    * @param [out] incStayType Modalità di attesa: 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [out] stationary Attesa della posizione di oscillazione: 0-Continua a muoversi durante il tempo di attesa; 1-Posizione ferma durante il tempo di attesa
    * @return Codice di errore
    */
   errno_t CustomWeaveGetPara(int id, int& pointNum, DescTran point[10], double stayTime[10], double& frequency, int& incStayType, int& stationary);

Esempio di codice per parametri di oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
   :linenos:

    int TestCustomWeaveSetPara()
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
      DescTran point[10] = {};
      point[0].x = -3;
      point[0].y = -3;
      point[0].z = 0;
      point[1].x = -6;
      point[1].y = 0;
      point[1].z = 0;
      point[2].x = -3;
      point[2].y = 3;
      point[2].z = 0;
      point[3].x = 0;
      point[3].y = 0;
      point[3].z = 0;
      double stayTime[10] = { 0,0,0,0,0,0,0,0,0,0 };
      rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
      printf("CustomWeaveSetPara rtn is %d\n", rtn);
      robot.Sleep(1000);
      int pointNum = 0;
      double frequency;
      int incStayType;
      int stationary;
      robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
      printf("pointNum is %d\n", pointNum);
      for (int i = 0; i < pointNum; i++)
      {
        printf("point %d, point x y z %f %f %f\n", i, point[i].x, point[i].y, point[i].z);
      }
      printf("fre is %f, stay is %d %d \n", frequency, incStayType, stationary);
      robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
      DescPose desc_p1 = { -288.650, 367.807, 288.404, 0.000, -0.001, 0.001 };
      DescPose desc_p2 = { -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 };
      DescPose desc_p3 = { -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 };
      JointPos j1 = { 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 };
      JointPos j2 = { 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 };
      JointPos j3 = { 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 };
      ExaxisPos epos = {};
      DescPose offset_pos = {};
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.Circle(&j3, &desc_p3, 3, 0, 100, 100, &epos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 10, -1, &offset_pos);
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveC(&j3, &desc_p3, 3, 0, 100, 100, &epos, 0, &offset_pos, &j2, &desc_p2, 3, 0, 100, 100, &epos, 0, &offset_pos, 10, -1); 
      robot.WeaveEnd(0);
      robot.MoveJ(&j1, &desc_p1, 3, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
      robot.WeaveStart(0);
      robot.MoveL(&j2, &desc_p2, 3, 0, 100, 100, 10, -1, &epos, 0, 0, &offset_pos, 0, 100);
      robot.WeaveEnd(0);
      robot.CloseRPC();
    }