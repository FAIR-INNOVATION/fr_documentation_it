Robot di saldatura
==================

.. toctree::
   :maxdepth: 5

Impostare i parametri della curva del processo di saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Imposta i parametri della curva del processo di saldatura
    * @param  [in] id  Numero del processo di saldatura (1-99)
    * @param  [in] startCurrent  Corrente di accensione dell'arco (A)
    * @param  [in] startVoltage  Tensione di accensione dell'arco (V)
    * @param  [in] startTime  Tempo di accensione dell'arco (ms)
    * @param  [in] weldCurrent  Corrente di saldatura (A)
    * @param  [in] weldVoltage  Tensione di saldatura (V)
    * @param  [in] endCurrent  Corrente di spegnimento dell'arco (A)
    * @param  [in] endVoltage  Tensione di spegnimento dell'arco (V)
    * @param  [in] endTime  Tempo di spegnimento dell'arco (ms)
    * @return  Codice di errore
    */
   int WeldingSetProcessParam(int id, double startCurrent, double startVoltage, double startTime, double weldCurrent, double weldVoltage, double endCurrent, double endVoltage, double endTime);

Ottenere i parametri della curva del processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Ottieni i parametri della curva del processo di saldatura
    * @param  [in] id  Numero del processo di saldatura (1-99)
    * @param  [out] startCurrent  Corrente di accensione dell'arco (A)
    * @param  [out] startVoltage  Tensione di accensione dell'arco (V)
    * @param  [out] startTime  Tempo di accensione dell'arco (ms)
    * @param  [out] weldCurrent  Corrente di saldatura (A)
    * @param  [out] weldVoltage  Tensione di saldatura (V)
    * @param  [out] endCurrent  Corrente di spegnimento dell'arco (A)
    * @param  [out] endVoltage  Tensione di spegnimento dell'arco (V)
    * @param  [out] endTime  Tempo di spegnimento dell'arco (ms)
    * @return  Codice di errore
    */
   int WeldingGetProcessParam(int id, ref double startCurrent, ref double startVoltage, ref double startTime, ref double weldCurrent, ref double weldVoltage, ref double endCurrent, ref double endVoltage, ref double endTime);

Impostare la relazione tra corrente di saldatura e uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la relazione tra corrente di saldatura e uscita analogica
    * @param [in] currentMin  Valore corrente del punto sinistro della relazione lineare corrente-uscita analogica (A)
    * @param [in] currentMax  Valore corrente del punto destro della relazione lineare corrente-uscita analogica (A)
    * @param [in] outputVoltageMin  Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [in] outputVoltageMax  Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   int WeldingSetCurrentRelation(double currentMin, double currentMax, double outputVoltageMin, double outputVoltageMax);

Impostare la relazione tra tensione di saldatura e uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la relazione tra tensione di saldatura e uscita analogica
    * @param [in] weldVoltageMin  Valore di tensione di saldatura del punto sinistro della relazione lineare (V)
    * @param [in] weldVoltageMax  Valore di tensione di saldatura del punto destro della relazione lineare (V)
    * @param [in] outputVoltageMin  Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [in] outputVoltageMax  Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   int WeldingSetVoltageRelation(double weldVoltageMin, double weldVoltageMax, double outputVoltageMin, double outputVoltageMax);

Ottenere la relazione tra corrente di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Ottieni la relazione tra corrente di saldatura e uscita analogica
    * @param [out] currentMin  Valore corrente del punto sinistro della relazione lineare corrente-uscita analogica (A)
    * @param [out] currentMax  Valore corrente del punto destro della relazione lineare corrente-uscita analogica (A)
    * @param [out] outputVoltageMin  Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [out] outputVoltageMax  Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   int WeldingGetCurrentRelation(ref double currentMin, ref double currentMax, ref double outputVoltageMin, ref double outputVoltageMax);

Ottenere la relazione tra tensione di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Ottieni la relazione tra tensione di saldatura e uscita analogica
    * @param [out] weldVoltageMin  Valore di tensione di saldatura del punto sinistro della relazione lineare (V)
    * @param [out] weldVoltageMax  Valore di tensione di saldatura del punto destro della relazione lineare (V)
    * @param [out] outputVoltageMin  Valore di tensione di uscita analogica del punto sinistro della relazione lineare (V)
    * @param [out] outputVoltageMax  Valore di tensione di uscita analogica del punto destro della relazione lineare (V)
    * @return Codice di errore
    */
   int WeldingGetVoltageRelation(ref double weldVoltageMin, ref double weldVoltageMax, ref double outputVoltageMin, ref double outputVoltageMax);

Impostare la corrente di saldatura
++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la corrente di saldatura
    * @param [in] ioType  Tipo IO di controllo 0-IO della centralina; 1-IO esteso
    * @param [in] current  Valore della corrente di saldatura (A)
    * @param [in] AOIndex  Porta di uscita analogica della centralina per il controllo della corrente di saldatura (0-1)
    * @return Codice di errore
    */
   int WeldingSetCurrent(int ioType, double current, int AOIndex);

Impostare la tensione di saldatura
++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la tensione di saldatura
    * @param [in] ioType  Tipo IO di controllo 0-IO della centralina; 1-IO esteso
    * @param [in] voltage  Valore della tensione di saldatura (V)
    * @param [in] AOIndex  Porta di uscita analogica della centralina per il controllo della tensione di saldatura (0-1)
    * @return Codice di errore
    */
   int WeldingSetVoltage(int ioType, double voltage, int AOIndex);

Impostare i parametri di oscillazione
+++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione
    * @param [in] weaveNum  Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] weaveType  Tipo di oscillazione 0-Oscillazione a onda triangolare piana; 1-Oscillazione a onda triangolare L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione a onda sinusoidale piana; 5-Oscillazione a onda sinusoidale L verticale; 6-Oscillazione a onda triangolare verticale; 7-Oscillazione a onda sinusoidale verticale
    * @param [in] weaveFrequency  Frequenza di oscillazione (Hz)
    * @param [in] weaveIncStayTime  Modalità di attesa 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] weaveRange  Ampiezza di oscillazione (mm)
    * @param [in] weaveLeftRange  Lunghezza della corda sinistra per l'oscillazione triangolare verticale (mm)
    * @param [in] weaveRightRange  Lunghezza della corda destra per l'oscillazione triangolare verticale (mm)
    * @param [in] additionalStayTime  Tempo di permanenza nel punto del triangolo verticale (ms)
    * @param [in] weaveLeftStayTime  Tempo di permanenza a sinistra (ms)
    * @param [in] weaveRightStayTime  Tempo di permanenza a destra (ms)
    * @param [in] weaveCircleRadio  Rapporto di ritorno per l'oscillazione circolare (0-100%)
    * @param [in] weaveStationary  Attesa della posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione rimane ferma durante il tempo di attesa
    * @param [in] weaveYawAngle  Angolo di direzione dell'oscillazione (rotazione attorno all'asse Z dell'oscillazione), unità °
    * @return Codice di errore
    */
   int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle, double weaveRotAngle=0);

Esempio di codice per impostare i parametri di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V3.9.8
    
.. code-block:: c#
    :linenos:

    private void button42_Click(object sender, EventArgs e)
    {
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

        robot.WeldingGetProcessParam(1, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 1 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);
        robot.WeldingGetProcessParam(2, ref startCurrent, ref startVoltage, ref startTime, ref weldCurrent, ref weldVoltage, ref endCurrent, ref endVoltage, ref endTime);
        Console.WriteLine("the Num 2 process param is " + startCurrent + " " + startVoltage + " " + startTime + " " + weldCurrent + " " + weldVoltage + " " + endCurrent + " " + endVoltage + " " + endTime);

        int rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0);
        Console.WriteLine("WeldingSetCurrentRelation rtn is: " + rtn);

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1);
        Console.WriteLine("WeldingSetVoltageRelation rtn is: " + rtn);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        rtn = robot.WeldingGetCurrentRelation(ref current_min, ref current_max, ref output_vmin, ref output_vmax, ref curIndex);
        Console.WriteLine("WeldingGetCurrentRelation rtn is: " + rtn);
        Console.WriteLine("current min " + current_min + " current max " + current_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingGetVoltageRelation(ref vol_min, ref vol_max, ref output_vmin, ref output_vmax, ref volIndex);
        Console.WriteLine("WeldingGetVoltageRelation rtn is: " + rtn);
        Console.WriteLine("vol min " + vol_min + " vol max " + vol_max + " output vol min " + output_vmin + " output vol max " + output_vmax);

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0);
        Console.WriteLine("WeldingSetCurrent rtn is: " + rtn);

        System.Threading.Thread.Sleep(3000);

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0);
        Console.WriteLine("WeldingSetVoltage rtn is: " + rtn);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000);
        Console.WriteLine("rtn is: " + rtn);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        Console.WriteLine("WeldingSetCheckArcInterruptionParam    " + rtn);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        Console.WriteLine("WeldingSetReWeldAfterBreakOffParam    " + rtn);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        rtn = robot.WeldingGetCheckArcInterruptionParam(ref checkEnable, ref arcInterruptTimeLength);
        Console.WriteLine("WeldingGetCheckArcInterruptionParam  checkEnable  " + checkEnable + "   arcInterruptTimeLength  " + arcInterruptTimeLength);
        rtn = robot.WeldingGetReWeldAfterBreakOffParam(ref enable, ref length, ref velocity, ref moveType);
        Console.WriteLine("WeldingGetReWeldAfterBreakOffParam  enable = " + enable + ", length = " + length + ", velocity = " + velocity + ", moveType = " + moveType);

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            int getCtrlMode = -1;
            robot.SetWeldMachineCtrlMode(0);
            robot.GetWeldMachineCtrlMode(ref getCtrlMode);
            Console.WriteLine("GetWeldMachineCtrlMode {0}", getCtrlMode);
            Thread.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.GetWeldMachineCtrlMode(ref getCtrlMode);
            Console.WriteLine("GetWeldMachineCtrlMode {0}", getCtrlMode);
            Thread.Sleep(1000);
        }
    }

Impostare i parametri di oscillazione in tempo reale
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione in tempo reale
    * @param [in] weaveNum  Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] weaveType  Tipo di oscillazione 0-Oscillazione a onda triangolare piana; 1-Oscillazione a onda triangolare L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione a onda sinusoidale piana; 5-Oscillazione a onda sinusoidale L verticale; 6-Oscillazione a onda triangolare verticale; 7-Oscillazione a onda sinusoidale verticale
    * @param [in] weaveFrequency  Frequenza di oscillazione (Hz)
    * @param [in] weaveIncStayTime  Modalità di attesa 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] weaveRange  Ampiezza di oscillazione (mm)
    * @param [in] weaveLeftStayTime  Tempo di permanenza a sinistra (ms)
    * @param [in] weaveRightStayTime  Tempo di permanenza a destra (ms)
    * @param [in] weaveCircleRadio  Rapporto di ritorno per l'oscillazione circolare (0-100%)
    * @param [in] weaveStationary  Attesa della posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione rimane ferma durante il tempo di attesa
    * @return Codice di errore
    */
   int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Impostare i parametri di rilevamento dell'interruzione dell'arco di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
    * @param [in] checkEnable  Abilita il rilevamento; 0-Disabilitato; 1-Abilitato
    * @param [in] arcInterruptTimeLength  Durata di conferma dell'interruzione dell'arco (ms)
    * @return Codice di errore
    */
   int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength)

Ottenere i parametri di rilevamento dell'interruzione dell'arco di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Ottieni i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
    * @param [out] checkEnable  Abilita il rilevamento; 0-Disabilitato; 1-Abilitato
    * @param [out] arcInterruptTimeLength  Durata di conferma dell'interruzione dell'arco (ms)
    * @return Codice di errore
    */
   int WeldingGetCheckArcInterruptionParam(ref int checkEnable, ref int arcInterruptTimeLength)

Impostare i parametri di recupero dell'interruzione di saldatura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta i parametri di recupero dell'interruzione di saldatura del robot
    * @param[in] enable  Abilita il recupero dell'interruzione di saldatura
    * @param[in] length  Distanza di sovrapposizione della saldatura (mm)
    * @param[in] velocity  Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    * @param[in] moveType  Metodo di movimento del robot verso il punto di riaccensione; 0-LIN; 1-PTP
    * @return Codice di errore
    */
   int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType)

Ottenere i parametri di recupero dell'interruzione di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Ottieni i parametri di recupero dell'interruzione di saldatura del robot
    * @param [out] enable  Abilita il recupero dell'interruzione di saldatura
    * @param [out] length  Distanza di sovrapposizione della saldatura (mm)
    * @param [out] velocity  Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    * @param [out] moveType  Metodo di movimento del robot verso il punto di riaccensione; 0-LIN; 1-PTP
    * @return Codice di errore
    */
   int WeldingGetReWeldAfterBreakOffParam(ref int enable, ref double length, ref double velocity, ref int moveType)

Impostare la porta DO estesa per la modalità di controllo della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la porta DO estesa per la modalità di controllo della saldatrice
    * @param DONum  Porta DO per la modalità di controllo della saldatrice (0-127)
    * @return Codice di errore
    */
   int SetWeldMachineCtrlModeExtDoNum(int DONum);

Imposta Modalità di Controllo della Saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la modalità di controllo della saldatrice
    * @param [in] mode Modalità di controllo della saldatrice; 0-Modo unico DC; 1-Modo unico a impulsi; 2-Modalità JOB; 3-Modalità controllo locale; 4-Modalità separata; 5-Modalità CC/CV; 6-TIG; 7-CMT
    * @param [in] ioType Tipo di controllo; 0-IO del box di controllo; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    * @return Codice di errore
    */
    public int SetWeldMachineCtrlMode(int mode,int ioType = 1)

Ottieni Modalità di Controllo della Saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene la modalità di controllo della saldatrice
    * @param [out] mode Modalità di controllo della saldatrice; 0-modalità unica CC; 1-modalità unica a impulsi; 2-modalità JOB; 3-modalità controllo locale; 4-modalità separata; 5-modalità CC/CV; 6-TIG; 7-CMT
    * @return Codice errore
    */
    public int GetWeldMachineCtrlMode(ref int mode)

Inizio della saldatura
++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Inizia la saldatura
    * @param [in] ioType  Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] arcNum  Numero del file di configurazione della saldatrice
    * @param [in] timeout  Tempo di timeout per l'accensione dell'arco
    * @return Codice di errore
    */
   int ARCStart(int ioType, int arcNum, int timeout);

Fine della saldatura
++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Termina la saldatura
    * @param [in] ioType  Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] arcNum  Numero del file di configurazione della saldatrice
    * @param [in] timeout  Tempo di timeout per lo spegnimento dell'arco
    * @return Codice di errore
    */
   int ARCEnd(int ioType, int arcNum, int timeout);

Inizio dell'oscillazione
++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Inizia l'oscillazione
    * @param [in] weaveNum  Numero di configurazione dei parametri di saldatura oscillante
    * @return Codice di errore
    */
   int WeaveStart(int weaveNum);

Fine dell'oscillazione
++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Termina l'oscillazione
    * @param [in] weaveNum  Numero di configurazione dei parametri di saldatura oscillante
    * @return Codice di errore
    */
   int WeaveEnd(int weaveNum);

Alimentazione del filo in avanti
+++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Alimentazione del filo in avanti
    * @param [in] ioType  Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] wireFeed  Controllo alimentazione filo 0-Ferma alimentazione filo; 1-Alimenta filo
    * @return Codice di errore
    */
   int SetForwardWireFeed(int ioType, int wireFeed);

Alimentazione del filo all'indietro
++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Alimentazione del filo all'indietro
    * @param [in] ioType  Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] wireFeed  Controllo alimentazione filo 0-Ferma alimentazione filo; 1-Alimenta filo
    * @return Codice di errore
    */
   int SetReverseWireFeed(int ioType, int wireFeed);

Alimentazione del gas
+++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Alimentazione del gas
    * @param [in] ioType  Tipo IO 0-IO del controllore; 1-IO esteso
    * @param [in] airControl  Controllo alimentazione gas 0-Ferma alimentazione gas; 1-Alimenta gas
    * @return Codice di errore
    */
   int SetAspirated(int ioType, int airControl);

Impostare il recupero della saldatura dopo l'interruzione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta il recupero della saldatura dopo l'interruzione del robot
    * @return Codice di errore
    */
   int WeldingStartReWeldAfterBreakOff()

Impostare l'uscita dalla saldatura dopo l'interruzione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta l'uscita dalla saldatura dopo l'interruzione del robot
    * @return Codice di errore
    */
   int WeldingAbortWeldAfterBreakOff()

Esempio di codice
+++++++++++++++++

.. code-block:: c#
   :linenos:

   private void button7_Click(object sender, EventArgs e)
   {
       robot.WeldingSetCurrent(1, 230, 0, 0);
       robot.WeldingSetVoltage(1, 24, 0, 1);

       DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
       JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

       DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
       JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

       ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
       DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

       robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
       robot.ARCStart(1, 0, 10000);
       robot.WeaveStart(0);
       robot.MoveL (p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
       robot.ARCEnd(1, 0, 10000);
       robot.WeaveEnd(0);
   }

Inizio della saldatura a segmenti
+++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   /**
    * @brief Inizia la saldatura a segmenti
    * @param [in] startDesePos  Posizione cartesiana del punto di inizio
    * @param [in] endDesePos  Posa cartesiana del punto di fine
    * @param [in] startJPos  Posa articolare del punto di inizio
    * @param [in] endJPos  Posa articolare del punto di fine
    * @param [in] weldLength  Lunghezza del segmento di saldatura (mm)
    * @param [in] noWeldLength  Lunghezza del segmento non saldato (mm)
    * @param [in] weldIOType  Tipo IO di saldatura (0-IO della centralina; 1-IO esteso)
    * @param [in] arcNum  Numero del file di configurazione della saldatrice
    * @param [in] weldTimeout  Tempo di timeout per accensione/spegnimento dell'arco
    * @param [in] isWeave  Se oscillare
    * @param [in] weaveNum  Numero di configurazione dei parametri di saldatura oscillante
    * @param [in] tool  Numero dello strumento
    * @param [in] user  Numero del pezzo
    * @param [in] vel   Percentuale di velocità, range [0~100]
    * @param [in] acc   Percentuale di accelerazione, range [0~100], attualmente non disponibile
    * @param [in] ovl   Fattore di scala della velocità, range [0~100]
    * @param [in] blendR [-1.0]-Movimento fino a destinazione (bloccante), [0~1000.0]-Raggio di levigatura (non bloccante), unità mm
    * @param [in] epos   Posizione degli assi estesi, unità mm
    * @param [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/pezzo, 2-Offset nel sistema di coordinate utensile
    * @param [in] offset_pos   Quantità di offset della posa
    * @return Codice di errore
    */
   int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType, int arcNum, int weldTimeout,bool isWeave, int weaveNum, int tool, int user, float vel, float acc, float ovl, float blendR, ExaxisPos epos, byte search, byte offset_flag, DescPose offset_pos);

Esempio di codice per la saldatura a segmenti del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.4

.. code-block:: c#
   :linenos:

   private void btnWeldStart_Click(object sender, EventArgs e)
   {
       robot.WeldingSetCurrent(1, 230, 0, 0);
       robot.WeldingSetVoltage(1, 24, 0, 1);

       DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
       JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

       DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
       JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

       ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
       DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

       int rtn = robot.SegmentWeldStart( p1Desc,  p2Desc,  p1Joint,  p2Joint, 20, 20, 0, 0, 5000, false, 0, 0, 0, 100, 100, 100, -1,  exaxisPos, 0, 0,  offdese);
       Console.WriteLine("SegmentWeldStart rtn is {0}", rtn);
   }

Inizio della simulazione di oscillazione
++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Inizia la simulazione di oscillazione
    * @param  [in] weaveNum  Numero dei parametri di oscillazione
    * @return  Codice di errore
    */
   int WeaveStartSim(int weaveNum);

Fine della simulazione di oscillazione
++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Termina la simulazione di oscillazione
    * @param  [in] weaveNum  Numero dei parametri di oscillazione
    * @return  Codice di errore
    */
   int WeaveEndSim(int weaveNum);

Inizio del rilevamento di traiettoria di allarme (senza movimento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Inizia il rilevamento di traiettoria di allarme (senza movimento)
    * @param  [in] weaveNum   Numero dei parametri di oscillazione
    * @return  Codice di errore
    */
   int WeaveInspectStart(int weaveNum);

Fine del rilevamento di traiettoria di allarme (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Termina il rilevamento di traiettoria di allarme (senza movimento)
    * @param  [in] weaveNum   Numero dei parametri di oscillazione
    * @return  Codice di errore
    */
   int WeaveInspectEnd(int weaveNum);

Inizio della transizione graduale di oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief  Inizia la transizione graduale di oscillazione
    * @param [in] weaveChangeFlag 1-Cambia parametri di oscillazione; 2-Cambia parametri di oscillazione + velocità di saldatura
    * @param [in] weaveNum  Numero di oscillazione
    * @param [in] velStart  Velocità di inizio saldatura, (cm/min)
    * @param [in] velEnd  Velocità di fine saldatura, (cm/min)
    * @return  Codice di errore
    */
   int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd);

Fine della transizione graduale di oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Termina la transizione graduale di oscillazione
    * @return  Codice di errore
    */
   int WeaveChangeEnd()

Esempio di codice per la saldatura con transizione graduale di oscillazione del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   private void btnweld_Click(object sender, EventArgs e)
   {
       DescPose p1Desc = new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
       JointPos p1Joint = new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

       DescPose p2Desc = new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
       JointPos p2Joint = new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

       ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
       DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

       robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
       robot.WeaveStartSim(0);
       robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
       robot.WeaveEndSim(0);
       robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
       robot.WeaveInspectStart(0);
       robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese);
       robot.WeaveInspectEnd(0);

       robot.WeldingSetVoltage(1, 19, 0, 0);
       robot.WeldingSetCurrent(1, 190, 0, 0);
       robot.MoveL( p1Joint,  p1Desc, 1, 1, 100, 100, 50, -1,  exaxisPos, 0, 0,  offdese);
       robot.ARCStart(1, 0, 10000);
       robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
       robot.WeaveStart(0);
       robot.WeaveChangeStart(1, 0, 50, 30);
       robot.MoveL( p2Joint,  p2Desc, 1, 1, 100, 100, 1, -1,  exaxisPos, 0, 0,  offdese);
       robot.WeaveChangeEnd();
       robot.WeaveEnd(0);
       robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
       robot.ARCEnd(1, 0, 10000);
   }

IO esteso - Configurare il segnale di rilevamento del gas della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di rilevamento del gas della saldatrice
    * @param  [in] DONum  Numero DO esteso per il segnale di rilevamento del gas
    * @return  Codice di errore
    */
   int SetAirControlExtDoNum(int DONum);

IO esteso - Configurare il segnale di accensione dell'arco della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di accensione dell'arco della saldatrice
    * @param  [in] DONum  Numero DO esteso per il segnale di accensione dell'arco
    * @return  Codice di errore
    */
   int SetArcStartExtDoNum(int DONum);

IO esteso - Configurare il segnale di alimentazione all'indietro del filo della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di alimentazione all'indietro del filo della saldatrice
    * @param  [in] DONum  Numero DO esteso per il segnale di alimentazione all'indietro del filo
    * @return  Codice di errore
    */
   int SetWireReverseFeedExtDoNum(int DONum);

IO esteso - Configurare il segnale di alimentazione in avanti del filo della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di alimentazione in avanti del filo della saldatrice
    * @param  [in] DONum  Numero DO esteso per il segnale di alimentazione in avanti del filo
    * @return  Codice di errore
    */
   int SetWireForwardFeedExtDoNum(int DONum);

IO esteso - Configurare il segnale di successo dell'accensione dell'arco della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di successo dell'accensione dell'arco della saldatrice
    * @param  [in] DINum  Numero DI esteso per il segnale di successo dell'accensione dell'arco
    * @return  Codice di errore
    */
   int SetArcDoneExtDiNum(int DINum);

IO esteso - Configurare il segnale di pronto della saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura il segnale di pronto della saldatrice
    * @param  [in] DINum  Numero DI esteso per il segnale di pronto della saldatrice
    * @return  Codice di errore
    */
   int SetWeldReadyExtDiNum(int DINum);

IO esteso - Configurare i segnali di recupero dell'interruzione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief IO esteso - Configura i segnali di recupero dell'interruzione di saldatura
    * @param  [in] reWeldDINum  Numero DI esteso per il segnale di recupero della saldatura dopo interruzione
    * @param  [in] abortWeldDINum  Numero DI esteso per il segnale di uscita dalla saldatura dopo interruzione
    * @return  Codice di errore
    */
   int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Configurare e Ottenere Esempio di Codice IO Esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button51_Click(object sender, EventArgs e)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);

        int[] DIConfig = new int[16];
        int[] DOConfig = new int[16];
        int rtn = robot.GetExtDIConfig(ref DIConfig);
        Console.WriteLine("GetExtDIConfig rtn={0}, saldatrice pronta={1}, avvio arco riuscito={2}, ripresa interruzione={3}, uscita interruzione={4}, ricerca filo riuscita={5}, stato laser={6}, errore laser={7}",
            rtn, DIConfig[0], DIConfig[1], DIConfig[2], DIConfig[3], DIConfig[4], DIConfig[5], DIConfig[6]);
        rtn = robot.GetExtDOConfig(ref DOConfig);
        Console.WriteLine("GetExtDOConfig rtn={0}, avvio arco saldatrice={1}, rilevamento gas={2}, avanzamento filo={3}, retrocessione filo={4}, ricerca filo={5}, modalità saldatrice={6}, abilitazione laser={7}, avvio laser={8}, reset laser={9}",
            rtn, DOConfig[0], DOConfig[1], DOConfig[2], DOConfig[3], DOConfig[4], DOConfig[5], DOConfig[6], DOConfig[7], DOConfig[8]);
    }

Ottieni Configurazione Funzione DI Estesa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene la configurazione della funzione DI estesa
    * @param [out] DIConfig Configurazione input DI esteso; [0]-saldatrice pronta; [1]-avvio arco riuscito; [2]-ripresa interruzione saldatura; [3]-uscita interruzione saldatura; [4]-ricerca filo riuscita; [5]-stato funzionamento saldatrice laser; [6]-stato guasto saldatrice laser; [7-15]-riservati
    * @return  Codice errore
    */
    public int GetExtDIConfig(ref int[] DIConfig)

Ottieni Configurazione Funzione DO Estesa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene la configurazione della funzione DO estesa
    * @param [out] DOConfig Configurazione output DO esteso; [0]-avvio arco saldatrice; [1]-rilevamento gas; [2]-alimentazione filo in avanti; [3]-alimentazione filo all'indietro; [4]-ricerca filo; [5]-modalità controllo saldatrice; [6]-abilitazione saldatrice laser; [7]-avvio saldatrice laser; [8]-reset saldatrice laser; [9-15]-riservati
    * @return  Codice errore
    */
    public int GetExtDOConfig(ref int[] DOConfig)

Controllo del tracciamento dell'arco
++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Controllo del tracciamento dell'arco
    * @param  [in] flag  Interruttore, 0-Spegnere; 1-Accendere
    * @param  [in] dalayTime  Tempo di ritardo, unità ms
    * @param  [in] isLeftRight  Compensazione deviazione sinistra-destra
    * @param  [in] klr  Coefficiente di regolazione sinistra-destra (sensibilità)
    * @param  [in] tStartLr  Tempo di inizio compensazione sinistra-destra cyc
    * @param  [in] stepMaxLr  Compensazione massima per volta sinistra-destra mm
    * @param  [in] sumMaxLr  Compensazione totale massima sinistra-destra mm
    * @param  [in] isUpLow  Compensazione deviazione alto-basso
    * @param  [in] kud  Coefficiente di regolazione alto-basso (sensibilità)
    * @param  [in] tStartUd  Tempo di inizio compensazione alto-basso cyc
    * @param  [in] stepMaxUd  Compensazione massima per volta alto-basso mm
    * @param  [in] sumMaxUd  Compensazione totale massima alto-basso mm
    * @param  [in] axisSelect  Selezione sistema coordinate alto-basso, 0-Oscillazione; 1-Utensile; 2-Base
    * @param  [in] referenceType  Metodo impostazione corrente di riferimento alto-basso, 0-Retroazione; 1-Costante
    * @param  [in] referSampleStartUd  Conteggio inizio campionamento corrente di riferimento alto-basso (retroazione), cyc
    * @param  [in] referSampleCountUd  Conteggio ciclo campionamento corrente di riferimento alto-basso (retroazione), cyc
    * @param  [in] referenceCurrent  Corrente di riferimento alto-basso mA
    *  @param  [in] offsetType  Tipo di tracciamento offset, 0-Nessun offset; 1-Campionamento; 2-Percentuale  /version 3.7.9
    * @param  [in] offsetParameter  Parametro offset; Campionamento (tempo di inizio campionamento offset, per default campiona un ciclo); Percentuale (percentuale offset (-100 ~ 100)) /version 3.7.9
    * @return  Codice di errore
    */
   int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent, int offsetType, int offsetParameter);

Selezione banda passante AI per il tracciamento dell'arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Selezione banda passante AI per il tracciamento dell'arco
    * @param  [in] channel  Selezione banda passante AI per il tracciamento dell'arco, [0-3]
    * @return  Codice di errore
    */
   int ArcWeldTraceExtAIChannelConfig(int channel);

Attivazione tracciamento arco + compensazione multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Attiva tracciamento arco + compensazione multi-strato multi-passata
    * @return Codice di errore
    */
   int ArcWeldTraceReplayStart();

Disattivazione tracciamento arco + compensazione multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Disattiva tracciamento arco + compensazione multi-strato multi-passata
    * @return Codice di errore
    */
   int ArcWeldTraceReplayEnd();

Trasformazione delle coordinate di offset - Saldatura multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Trasformazione delle coordinate di offset - Saldatura multi-strato multi-passata
    * @param [in] pointO  Posa cartesiana del punto di riferimento
    * @param [in] pointX  Posa cartesiana del punto nella direzione dell'offset X rispetto al punto di riferimento
    * @param [in] pointZ  Posa cartesiana del punto nella direzione dell'offset Z rispetto al punto di riferimento
    * @param [in] dx  Quantità di offset in direzione X (mm)
    * @param [in] dy  Quantità di offset in direzione Y (mm)
    * @param [in] db  Quantità di offset attorno all'asse Y (°)
    * @param [out] offset  Quantità di offset calcolata
    * @return Codice di errore
    */
   int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dy, double db, ref DescPose offset);

Esempio di codice per il tracciamento dell'arco nella saldatura multi-strato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   private void button52_Click(object sender, EventArgs e)
   {
       JointPos mulitilineorigin1_joint = new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
       DescPose mulitilineorigin1_desc = new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

       DescTran mulitilineX1_desc = new DescTran();
       mulitilineX1_desc.x = -677.556;
       mulitilineX1_desc.y = 211.949;
       mulitilineX1_desc.z = -1.206;

       DescTran mulitilineZ1_desc = new DescTran();
       mulitilineZ1_desc.x = -677.564;
       mulitilineZ1_desc.y = 190.956;
       mulitilineZ1_desc.z = 19.817;

       JointPos mulitilinesafe_joint = new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
       DescPose mulitilinesafe_desc = new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
       JointPos mulitilineorigin2_joint = new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
       DescPose mulitilineorigin2_desc = new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

       DescTran mulitilineX2_desc = new DescTran();
       mulitilineX2_desc.x = -563.965;
       mulitilineX2_desc.y = 220.355;
       mulitilineX2_desc.z = -0.680;

       DescTran mulitilineZ2_desc = new DescTran();
       mulitilineZ2_desc.x = -563.968;
       mulitilineZ2_desc.y = 215.362;
       mulitilineZ2_desc.z = 4.331;

       ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
       DescPose offset = new DescPose(0, 0, 0, 0, 0, 0);

       Thread.Sleep(10);
       int error = robot.MoveJ( mulitilinesafe_joint,  mulitilinesafe_desc, 13, 0, 10, 100, 100,  epos, -1, 0,  offset);
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ARCStart(1, 0, 3000);
       Console.WriteLine("ARCStart return: {0}", error);

       error = robot.WeaveStart(0);
       Console.WriteLine("WeaveStart return: {0}", error);

       error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
       Console.WriteLine("ArcWeldTraceControl return: {0}", error);

       error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1,  epos, 0, 0,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10);
       Console.WriteLine("ArcWeldTraceControl return: {0}", error);

       error = robot.WeaveEnd(0);
       Console.WriteLine("WeaveEnd return: {0}", error);

       error = robot.ARCEnd(1, 0, 10000);
       Console.WriteLine("ARCEnd return: {0}", error);

       error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, ref offset);
       Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

       error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ARCStart(1, 0, 3000);
       Console.WriteLine("ARCStart return: {0}", error);

       error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, ref offset);
       Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

       error = robot.ArcWeldTraceReplayStart();
       Console.WriteLine("ArcWeldTraceReplayStart return: {0}", error);

       error = robot.MoveL( mulitilineorigin2_joint,  mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ArcWeldTraceReplayEnd();
       Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

       error = robot.ARCEnd(1, 0, 10000);
       Console.WriteLine("ARCEnd return: {0}", error);

       error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, ref offset);
       Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

       error = robot.MoveL( mulitilineorigin1_joint,  mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,  epos, 0, 1,  offset, 0, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ARCStart(1, 0, 3000);
       Console.WriteLine("ARCStart return: {0}", error);

       error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, ref offset);
       Console.WriteLine("MultilayerOffsetTrsfToBase return: {0}  offect is {1} {2} {3}", error, offset.tran.x, offset.tran.y, offset.tran.z);

       error = robot.ArcWeldTraceReplayStart();
       Console.WriteLine("MoveJ return: {0}", error);

       error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 1, 2, 100, 100, -1, epos, 1, 1, offset, 1, 100);
       Console.WriteLine("MoveL return: {0}", error);

       error = robot.ArcWeldTraceReplayEnd();
       Console.WriteLine("ArcWeldTraceReplayEnd return: {0}", error);

       error = robot.ARCEnd(1, 0, 3000);
       Console.WriteLine("ARCEnd return: {0}", error);

       error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);
       Console.WriteLine("MoveJ return: {0}", error);
   }

Selezione canale AI per la retroazione della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Selezione canale AI per la retroazione della corrente della saldatrice nel tracciamento dell'arco
    * @param [in]  channel  Canale; 0-AI esteso 0; 1-AI esteso 1; 2-AI esteso 2; 3-AI esteso 3; 4-AI centralina 0; 5-AI centralina 1
    * @return Codice di errore
    */
   int ArcWeldTraceAIChannelCurrent(int channel);

Selezione canale AI per la retroazione della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Selezione canale AI per la retroazione della tensione della saldatrice nel tracciamento dell'arco
    * @param [in]  channel  Canale; 0-AI esteso 0; 1-AI esteso 1; 2-AI esteso 2; 3-AI esteso 3; 4-AI centralina 0; 5-AI centralina 1
    * @return Codice di errore
    */
   int ArcWeldTraceAIChannelVoltage(int channel);

Parametri di conversione per la retroazione della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Parametri di conversione per la retroazione della corrente della saldatrice nel tracciamento dell'arco
    * @param [in] AILow  Limite inferiore canale AI, valore predefinito 0V, range [0-10V]
    * @param [in] AIHigh  Limite superiore canale AI, valore predefinito 10V, range [0-10V]
    * @param [in] currentLow  Valore di corrente della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, range [0-200V]
    * @param [in] currentHigh  Valore di corrente della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, range [0-200V]
    * @return Codice di errore
    */
   public int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Parametri di conversione per la retroazione della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Parametri di conversione per la retroazione della tensione della saldatrice nel tracciamento dell'arco
    * @param [in] AILow  Limite inferiore canale AI, valore predefinito 0V, range [0-10V]
    * @param [in] AIHigh  Limite superiore canale AI, valore predefinito 10V, range [0-10V]
    * @param [in] voltageLow  Valore di tensione della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, range [0-200V]
    * @param [in] voltageHigh  Valore di tensione della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, range [0-200V]
    * @return Codice di errore
    */
   public int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Esempio di codice per il tracciamento dell'arco
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   private void button8_Click(object sender, EventArgs e)
   {
      DescPose startdescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
      JointPos startjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

      DescPose enddescPose = new DescPose(441.901, 615.317, -51.979, -179.234, 0.718, -115.305);
      JointPos endjointPos = new JointPos(-133.22, -44.193, 74.934, -121.661, -90.509, 72.087);

      DescPose safetydescPose = new DescPose(441.901, 416.508, -51.979, -179.234, 0.718, -115.305);
      JointPos safetyjointPos = new JointPos(-146.22, -60.551, 104.859, -135.317, -90.289, 59.088);

      ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
      DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
      robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

      robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
      robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);
      robot.WeldingSetVoltage(0, 25, 1, 0); 
      robot.WeldingSetCurrent(0, 260, 0, 0); 

      int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
      Console.WriteLine("ArcWeldTraceAIChannelCurrent rtn is " + rtn);
      rtn = robot.ArcWeldTraceAIChannelVoltage(5);
      Console.WriteLine("ArcWeldTraceAIChannelVoltage rtn is " + rtn);
      rtn = robot.ArcWeldTraceCurrentPara((double)0, (double)5, (double)0, (double)500);
      Console.WriteLine("ArcWeldTraceCurrentPara rtn is " + rtn);
      rtn = robot.ArcWeldTraceVoltagePara((double)1.018, (double)10, (double)0, (double)50);
      Console.WriteLine("ArcWeldTraceVoltagePara rtn is " + rtn);

      robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
      robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot.ARCStart(0, 0, 10000);
      robot.WeaveStart(0);
         robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0,exaxisPos, 0, 0, offdese);
      robot.ARCEnd(0, 0, 10000);
      robot.WeaveEnd(0);
      robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
      robot.MoveJ(safetyjointPos, safetydescPose, 1, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);

   }

Impostare le porte IO estese per la ricerca del filo
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta le porte IO estese per la ricerca del filo
    * @param searchDoneDINum  Porta DO per il successo della ricerca del filo (0-127)
    * @param searchStartDONum  Porta DO per il controllo avvio/arresto della ricerca del filo (0-127)
    * @return Codice di errore
    */
   int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Inizio della ricerca del filo
+++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Inizia la ricerca del filo
    * @param  [in] refPos  1-Punto di riferimento 0-Punto di contatto
    * @param  [in] searchVel   Velocità di ricerca %
    * @param  [in] searchDis   Distanza di ricerca mm
    * @param  [in] autoBackFlag  Flag ritorno automatico, 0-Non automatico; -Automatico
    * @param  [in] autoBackVel   Velocità di ritorno automatico %
    * @param  [in] autoBackDis   Distanza di ritorno automatico mm
    * @param  [in] offectFlag   1-Ricerca con offset; 0-Ricerca al punto insegnato
    * @return  Codice di errore
    */
   int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Fine della ricerca del filo
+++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Termina la ricerca del filo
    * @param  [in] refPos  1-Punto di riferimento 2-Punto di contatto
    * @param  [in] searchVel   Velocità di ricerca %
    * @param  [in] searchDis   Distanza di ricerca mm
    * @param  [in] autoBackFlag  Flag ritorno automatico, 0-Non automatico; -Automatico
    * @param  [in] autoBackVel   Velocità di ritorno automatico %
    * @param  [in] autoBackDis   Distanza di ritorno automatico mm
    * @param  [in] offectFlag   1-Ricerca con offset; 2-Ricerca al punto insegnato
    * @return  Codice di errore
    */
   int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Calcolare l'offset della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Calcola l'offset della ricerca del filo
    * @param  [in] seamType   Tipo di giunzione
    * @param  [in] method    Metodo di calcolo
    * @param  [in] varNameRef  Punti di riferimento 1-6, "#" indica nessuna variabile punto
    * @param  [in] varNameRes  Punti di contatto 1-6, "#" indica nessuna variabile punto
    * @param  [out] offectFlag 0-L'offset viene aggiunto direttamente ai punti di comando; 1-L'offset richiede una trasformazione delle coordinate dei punti di comando
    * @param  [out] offect  Posa offset [x, y, z, a, b, c]
    * @return  Codice di errore
    */
   int GetWireSearchOffset(int seamType, int method, string[] varNameRef, string[] varNameRes, ref int offsetFlag, ref DescPose offset);

Attendere il completamento della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Attende il completamento della ricerca del filo
    * @return  Codice di errore
    */
   int WireSearchWait(string name);

Scrivere il punto di contatto della ricerca del filo nel database
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   /**
    * @brief  Scrive il punto di contatto della ricerca del filo nel database
    * @param  [in] varName   Nome del punto di contatto "RES0" ~ "RES99"
    * @param  [in] pos   Dati del punto di contatto [x, y, z, a, b, c]
    * @return  Codice di errore
    */
   int SetPointToDatabase(string varName, DescPose pos);

Esempio di codice per la ricerca del filo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
   :linenos:

   private void button53_Click(object sender, EventArgs e)
   {
       DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
       robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
       DescPose wobjCoord=new DescPose(0, 0, 0, 0, 0, 0);
       robot.SetWObjCoord(1, wobjCoord, 0);

       int rtn0, rtn1, rtn2 = 0;
       ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
       DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

       DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
       JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

       DescPose descEnd = new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
       JointPos jointEnd = new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302);

       robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
       robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);

       DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
       JointPos jointREF0A = new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

       DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
       JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

       DescPose descREF1A = new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
       JointPos jointREF1A = new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

       DescPose descREF1B = new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
       JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

       rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
       robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //Punto di partenza
       robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //Punto direzione
       rtn1 = robot.WireSearchWait("REF0");
       rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

       rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
       robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //Punto di partenza
       robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //Punto direzione
       rtn1 = robot.WireSearchWait("REF1");
       rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

       rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
       robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //Punto di partenza
       robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //Punto direzione
       rtn1 = robot.WireSearchWait("RES0");
       rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

       rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
       robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);  //Punto di partenza
       robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);  //Punto direzione
       rtn1 = robot.WireSearchWait("RES1");
       rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

       string[] varNameRef = { "REF0", "REF1", "#", "#", "#", "#" };
       string[] varNameRes = { "RES0", "RES1", "#", "#", "#", "#" };
       int offectFlag = 0;
       DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
       rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, ref offectFlag, ref offectPos);
       robot.PointsOffsetEnable(0, offectPos);
       robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1, exaxisPos, 0, 0, offdese);
       robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, exaxisPos, 1, 0, offdese);
       robot.PointsOffsetDisable();
   }

Impostare l'inizio della transizione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta l'inizio della transizione graduale della tensione di saldatura
    * @param [in] IOType  Tipo di controllo; 0-IO della centralina; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    * @param [in] voltageStart  Tensione di saldatura iniziale (V)
    * @param [in] voltageEnd  Tensione di saldatura finale (V)
    * @param [in] AOIndex  Numero porta AO della centralina (0-1)
    * @param [in] blend  Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend);

Impostare la fine della transizione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la fine della transizione graduale della tensione di saldatura
    * @return Codice di errore
    */
   int WeldingSetVoltageGradualChangeEnd();

Impostare l'inizio della transizione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta l'inizio della transizione graduale della corrente di saldatura
    * @param [in] IOType  Tipo di controllo; 0-IO della centralina; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    * @param [in] currentStart  Corrente di saldatura iniziale (A)
    * @param [in] currentEnd  Corrente di saldatura finale (A)
    * @param [in] AOIndex  Numero porta AO della centralina (0-1)
    * @param [in] blend  Se levigare 0-Non levigare; 1-Levigare
    * @return Codice di errore
    */
   int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend);

Impostare la fine della transizione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta la fine della transizione graduale della corrente di saldatura
    * @return Codice di errore
    */
   int WeldingSetCurrentGradualChangeEnd();

Esempio di codice per la transizione graduale di corrente e tensione di saldatura del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.3  Web-3.8.2

.. code-block:: c#
   :linenos:

   private void btnweld_Click(object sender, EventArgs e)
   {
       DescPose startdescPose = new DescPose(-319.303, -240.689, 116.379, -175.879, -0.337, 148.239);
       JointPos startjointPos = new JointPos(20.474, -103.554, 126.774, -116.682, -87.746, -37.709);

       DescPose enddescPose = new DescPose(-454.166, -327.159, 62.217, 177.199, -2.276, 154.955);
       JointPos endjointPos = new JointPos(27.176, -74.423, 104.557, -119.315, -93.514, -37.698);

       DescPose safedescPose = new DescPose(-375.533, -543.319, 19.798, 177.486, -2.489, 175.825);
       JointPos safejointPos = new JointPos(48.074, -59.714, 89.955, -119.777, -93.508, -37.683);

       ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
       DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

       robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0);
       robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1);

       robot.WeldingSetVoltage(0, 25, 1, 0);//
       robot.WeldingSetCurrent(0, 260, 0, 0);// 

       robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

       int rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
       Console.WriteLine($"WeldingSetCurrentGradualChangeStart rtn is {rtn}");
       rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
       Console.WriteLine($"WeldingSetVoltageGradualChangeStart rtn is {rtn}");

       rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
       Console.WriteLine($"ArcWeldTraceControl rtn is {rtn}");

       robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

       robot.ARCStart(0, 0, 10000);
       robot.WeaveStart(0);
       rtn = robot.WeaveChangeStart(2, 1, 24, 36);
       Console.WriteLine($"WeaveChangeStart rtn is {rtn}");
       //robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, exaxisPos, 0, 0, offdese);
       robot.ARCEnd(0, 0, 10000);
       robot.WeaveChangeEnd();
       robot.WeaveEnd(0);
       robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
       robot.WeldingSetCurrentGradualChangeEnd();
       robot.WeldingSetVoltageGradualChangeEnd();
   }

Impostare i parametri di oscillazione personalizzati
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
   :linenos:

   /**
    * @brief Imposta i parametri di oscillazione personalizzati
    * @param [in] id  Numero di oscillazione personalizzata: 0-2
    * @param [in] pointNum  Numero di punti di oscillazione 0-10
    * @param [in] points  Dati dei punti di estremità del movimento x,y,z
    * @param [in] stayTimes  Tempi di permanenza nell'oscillazione ms
    * @param [in] frequency  Frequenza di oscillazione Hz
    * @param [in] incStayType  Modalità di attesa: 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [in] stationary  Attesa della posizione di oscillazione: 0-Continua a muoversi durante il tempo di attesa; 1-Posizione ferma durante il tempo di attesa
    * @return  Codice di errore
    */
   public int CustomWeaveSetPara(int id, int pointNum, DescTran[] points, double[] stayTimes, double frequency, int incStayType, int stationary)

Ottenere i parametri di oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
   :linenos:

   /**
    * @brief Ottiene i parametri di oscillazione personalizzati
    * @param [in] id  Numero di oscillazione personalizzata: 0-2
    * @param [out] pointNum  Numero di punti di oscillazione 0-10
    * @param [out] points  Dati dei punti di estremità del movimento x,y,z
    * @param [out] stayTimes  Tempi di permanenza nell'oscillazione ms
    * @param [out] frequency  Frequenza di oscillazione Hz
    * @param [out] incStayType  Modalità di attesa: 0-Il ciclo non include il tempo di attesa; 1-Il ciclo include il tempo di attesa
    * @param [out] stationary  Attesa della posizione di oscillazione: 0-Continua a muoversi durante il tempo di attesa; 1-Posizione ferma durante il tempo di attesa
    * @return  Codice di errore
    */
   public int CustomWeaveGetPara(int id, ref int pointNum, ref DescTran[] points, ref double[] stayTimes, ref double frequency, ref int incStayType, ref int stationary)

Esempio di codice per i parametri di oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-V1.1.8  Web-3.8.6

.. code-block:: c#
   :linenos:

   public void TestCoordMain5()
   {  
       DescTran[] points = new DescTran[10];
       for (int i = 0; i < 10; i++)
       {
           points[i] = new DescTran();
       }
       points[0].x = -3;
       points[0].y = -3;
       points[0].z = 0;
       points[1].x = -6;
       points[1].y = 0;
       points[1].z = 0;
       points[2].x = -3;
       points[2].y = 3;
       points[2].z = 0;
       points[3].x = 0;
       points[3].y = 0;
       points[3].z = 0;
       double[] stayTimes = new double[10] { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
       int rtn = robot.CustomWeaveSetPara(2, 4, points, stayTimes, 1.000, 0, 0);
       Console.WriteLine($"CustomWeaveSetPara rtn is {rtn}");
       System.Threading.Thread.Sleep(1000);
       int pointNum = 0;
       double frequency = 0;
       int incStayType = 0;
       int stationary = 0;
       rtn = robot.CustomWeaveGetPara(2, ref pointNum, ref points, ref stayTimes, ref frequency, ref incStayType, ref stationary);
       Console.WriteLine($"pointNum is {pointNum}");
       for (int i = 0; i < pointNum; i++)
       {
           Console.WriteLine($"point {i}, point x y z {points[i].x:F6} {points[i].y:F6} {points[i].z:F6}");
       }
       Console.WriteLine($"fre is {frequency:F6}, stay is {incStayType} {stationary}");
       robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000);
       DescPose desc_p1 = new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001);
       DescPose desc_p2 = new DescPose(-431.714, 367.815, 288.415, 0.001, 0.001, 0.000);    
       DescPose desc_p3 = new DescPose(-348.666, 427.798, 288.404, -0.000, -0.000, 0.001);
       JointPos j1 = new JointPos(140.656,  -84.560,  -91.707, -93.734,  90.000,50.655 );
       JointPos j2 = new JointPos ( 149.873, -98.298, -77.599,  -94.103,  90.000,  59.873 );
       JointPos j3 = new JointPos (139.773,  -96.173, -80.014,  -93.814,  90.000,  49.772 );
       ExaxisPos epos = new ExaxisPos(0,0,0,0);
       DescPose offset_pos = new DescPose(0,0,0,0,0,0);
       robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
       robot.WeaveStart(0);
       robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos, 100, -1, 0);
       robot.WeaveEnd(0);
       robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
       robot.WeaveStart(0);
       robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1, 0);
       robot.WeaveEnd(0);
       robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
       robot.WeaveStart(0);
       robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1, epos, 0, 0, offset_pos, 0, 0, 10);
       robot.WeaveEnd(0);
   }

Configurazione dei Parametri della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Scrive i parametri di configurazione per uno dei 10 gruppi di processo della saldatrice laser e configura la saldatrice
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[in] num Numero del gruppo da impostare (1~10)
    * @param[in] scanSpeed Velocità di scansione
    * @param[in] scanWidth Larghezza di scansione
    * @param[in] peakPower Potenza di picco
    * @param[in] dutyCycle Ciclo di lavoro
    * @param[in] freq Frequenza
    * @return Codice di errore
    */
    public int SetLaserWeldingParam(int io_type, int num, int scanSpeed, int scanWidth, int peakPower, int dutyCycle, int freq)

Impostare Avvio/Arresto Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta accensione/spegnimento della saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[in] status Parola di controllo 0-laser spento 1-laser acceso
    * @param[in] max_waittime Tempo massimo di attesa
    * @return Codice di errore
    */
    public int SetLaserWeldingStartEnd(int io_type, int status, int max_waittime)

Abilitazione/Disabilitazione Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Abilita/disabilita la saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[in] status 0-disabilita 1-abilita
    * @return Codice di errore
    */
    public int SetLaserWeldingEnable(int io_type, int status)

Ripristino Guasto Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ripristina il guasto della saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[in] status Parola di controllo 0-invalido 1-ripristino guasto
    * @return Codice di errore
    */
    public int ResetLaserWeldingErr(int io_type, int status)

Ottenere lo Stato di Funzionamento della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato di funzionamento della saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[out] status Parola di controllo 0-fermo 1-in funzione
    * @return Codice di errore
    */
    public int GetLaserWeldingRunningState(int io_type, ref int status)

Ottenere lo Stato di Guasto della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato di guasto della saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[out] status 0-nessun guasto 1-guasto presente
    * @return Codice di errore
    */
    public int GetLaserWeldingErrState(int io_type, ref int status)

Ottenere i Parametri Configurati della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene i parametri di configurazione per uno dei 10 gruppi di processo della saldatrice laser
    * @param[in] num Numero del gruppo da impostare (1~10)
    * @param[out] scanSpeed Velocità di scansione
    * @param[out] scanWidth Larghezza di scansione
    * @param[out] peakPower Potenza di picco
    * @param[out] dutyCycle Ciclo di lavoro
    * @param[out] freq Frequenza
    * @return Codice di errore
    */
    public int GetLaserWeldingParamTarget(int num, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)

Ottenere i Parametri di Configurazione Attualmente Attivi della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene i parametri di configurazione attualmente attivi della saldatrice laser
    * @param[in] io_type Tipo di comunicazione 0-IO 1-UDP
    * @param[out] scanSpeed Velocità di scansione
    * @param[out] scanWidth Larghezza di scansione
    * @param[out] peakPower Potenza di picco
    * @param[out] dutyCycle Ciclo di lavoro
    * @param[out] freq Frequenza
    * @return Codice di errore
    */
    public int GetLaserWeldingParamActual(int io_type, ref int scanSpeed, ref int scanWidth, ref int peakPower, ref int dutyCycle, ref int freq)
    
Configurare la Porta DO di Abilitazione IO Esteso della Saldatrice Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta l'IO esteso della saldatrice laser, porta DO di abilitazione
    * @param[in] ctrlModeDONum Numero della porta DO estesa per l'abilitazione della saldatrice laser
    * @return Codice di errore
    */
    public int SetLaserWeldingEnableExtDoNum(int ctrlModeDONum)

Configurare la Porta DO di Avvio IO Esteso della Saldatrice Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta l'IO esteso della saldatrice laser, porta DO di avvio
    * @param[in] ctrlModeDONum Numero della porta DO estesa per l'avvio (laser acceso/spento) della saldatrice laser
    * @return Codice di errore
    */
    public int SetLaserWeldingStartExtDoNum(int ctrlModeDONum)

Configurare la Porta DO di Ripristino Guasto IO Esteso della Saldatrice Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta l'IO esteso della saldatrice laser, porta DO di ripristino guasto
    * @param[in] ctrlModeDONum Numero della porta DO estesa per il ripristino del guasto della saldatrice laser
    * @return Codice di errore
    */
    public int SetLaserWeldingErrResetExtDoNum(int ctrlModeDONum)

Configurare il DI Esteso per lo Stato di Funzionamento (Stato Laser Accesso) della Saldatrice Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configura il DI esteso per lo stato di funzionamento (stato laser acceso) della saldatrice laser
    * @param[in] diNum Porta DI estesa per lo stato di funzionamento (stato laser acceso) della saldatrice laser
    * @return Codice di errore
    */
    public int SetLaserWeldingRunningStateExtDiNum(int diNum)
    
Configurare la Porta DI di Stato Guasto IO Esteso della Saldatrice Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Configura il DI esteso per lo stato di guasto della saldatrice laser
    * @param[in] diNum Porta DI estesa per lo stato di guasto della saldatrice laser
    * @return Codice di errore
    */
    public int SetLaserWeldingErrStateExtDiNum(int diNum)
        
Esempio di Codice per Saldatura Laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    private void btnLaserWeld_Click(object sender, EventArgs e)
    {

        int rtn = -1;
        // Carica driver UDP
        rtn = robot.ExtDevLoadUDPDriver();
        if (rtn != 0)
        {
            Console.WriteLine("Failed to load UDP driver, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Imposta parametri saldatura laser: io_type=1, num=3, scanSpeed=2000, scanWidth=3, peakPower=1500, dutyCycle=100, freq=1000
        rtn = robot.SetLaserWeldingParam(1, 3, 2000, 3, 1500, 100, 1000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingParam failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("SetLaserWeldingParam success");
        }

        // Imposta il numero della porta DO di avvio
        rtn = robot.SetLaserWeldingStartExtDoNum(1);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartExtDoNum failed, error code: " + rtn);
        }

        // Imposta la modalità 0 (modalità insegnamento)
        rtn = robot.Mode(0);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 0 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);


        DescPose desc_pos1 = new DescPose(-303.721, -206.960, 297.105, 152.209, 19.857, 109.166);
        DescPose desc_pos2 = new DescPose(-301.575, -254.888, 284.786, 155.919, 26.946, 111.629);
        DescPose desc_safe = new DescPose(-344.386, -280.830, 435.073, 173.835, 15.333, 124.931);


        ExaxisPos exaxis = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offset = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        // Muovi al primo punto di saldatura
        int error = robot.MoveL(desc_pos1, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos1 return: " + error);

        // Avvia laser (laser acceso)
        rtn = robot.SetLaserWeldingStartEnd(1, 1, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (start) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser started");
        }

        // Muovi al secondo punto di saldatura (durante la saldatura)
        rtn = robot.MoveL(desc_pos2, 0, 0, 30, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to pos2 return: " + rtn);

        Thread.Sleep(500);
        // Ferma laser (laser spento)
        rtn = robot.SetLaserWeldingStartEnd(1, 0, 10000);
        if (rtn != 0)
        {
            Console.WriteLine("SetLaserWeldingStartEnd (stop) failed, error code: " + rtn);
        }
        else
        {
            Console.WriteLine("Laser stopped");
        }

        // Muovi al punto di sicurezza
        rtn = robot.MoveL(desc_safe, 0, 0, 100, 100, 100, -1, 0, exaxis, 0, 0, offset, -1, 0);
        Console.WriteLine("MoveL to safe_pos return: " + rtn);

        // Imposta la modalità 1 (modalità remota)
        rtn = robot.Mode(1);
        if (rtn != 0)
        {
            Console.WriteLine("Set mode 1 failed, error code: " + rtn);
        }
        Thread.Sleep(1000);

        // Chiudi connessione
        robot.CloseRPC();
        Thread.Sleep(1000);

        Console.WriteLine("Test completed");

        return ;
    }

Imposta il ritorno al punto zero del ciclo al termine della tessitura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta se tornare al punto zero del ciclo al termine della tessitura
    * @param [in] flag Se tornare al punto zero del ciclo al termine della tessitura; 0-non tornare; 1-tornare al punto zero del ciclo
    * @return  Codice errore
    */
    public int SetWeavebackCenterConfig(int flag) 
           
Ottiene i parametri del ritorno al punto zero del ciclo al termine della tessitura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottiene i parametri del ritorno al punto zero del ciclo al termine della tessitura
    * @param [out] flag Se tornare al punto zero del ciclo al termine della tessitura; 0-non tornare; 1-tornare al punto zero del ciclo
    * @return  Codice errore
    */
    public int GetWeavebackCenterConfig(ref int flag)
           
Esempio di codice per il ritorno al punto zero del ciclo al termine della tessitura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestSplineWeave()
    {
        int rtn;

        // Configurazione ritorno al centro della tessitura
        robot.SetWeavebackCenterConfig(1);
        int weaveBackConfig = 0;
        robot.GetWeavebackCenterConfig(ref weaveBackConfig);
        Console.WriteLine("GetWeavebackCenterConfig: {0}", weaveBackConfig);

        JointPos j1 = new JointPos(9.000, -66.067, 67.706, -103.217, -90.151, 100.669);
        JointPos j2 = new JointPos(-4.660, -107.973, 103.734, -76.214, -89.999, 90.886);
        JointPos j3 = new JointPos(-36.762, -77.380, 91.364, -127.159, -90.024, 54.833);
        JointPos j4 = new JointPos(-62.875, -89.460, 86.437, -77.030, -90.012, 31.539);
        DescPose desc_pos1 = new DescPose(-654.129, -235.344, 246.543, 6.010, -11.535, -176.787);
        DescPose desc_pos2 = new DescPose(-273.710, -100.871, 280.935, 5.692, 9.522, 179.512);
        DescPose desc_pos3 = new DescPose(-566.093, 311.278, 215.008, -10.453, -17.486, -174.209);
        DescPose desc_pos4 = new DescPose(-246.558, 328.240, 292.173, 13.912, 4.437, -179.067);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 2;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 20.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;

        robot.SetSpeed(1);

        // Movimento al punto iniziale j1
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, 100.0f, epos, blendT, flag, offset_pos);
        Console.WriteLine("MoveJ to j1 rtn: {0}", rtn);

        // Tessitura + movimento curva spline
        robot.WeaveStart(0);
        robot.NewSplineStart(0, 6000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1.0f, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1.0f, 1);
        robot.NewSplineEnd();

        Console.WriteLine("TestSplineWeave completed");
    }