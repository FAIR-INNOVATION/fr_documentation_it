Saldatura Robot
===============

.. toctree:: 
    :maxdepth: 5


Impostazione parametri curva processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta i parametri della curva del processo di saldatura
    * @param [in] id Numero processo di saldatura (1-99)
    * @param [in] param Parametri del processo di saldatura
    * @return Codice di errore 
    */
    int WeldingSetProcessParam(int id, WeldingProcessParam param);

Ottenimento parametri curva processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene i parametri della curva del processo di saldatura
    * @param [in] id Numero processo di saldatura (1-99)
    * @param [out] param Parametri del processo di saldatura
    * @return Codice di errore 
    */
    int WeldingGetProcessParam(int id, WeldingProcessParam param);

Impostazione relazione corrente saldatura - uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta la relazione corrente saldatura - uscita analogica
    * @param [in] relation Valore della relazione
    * @return Codice di errore
    */
    int WeldingSetCurrentRelation(WeldCurrentAORelation relation);

Impostazione relazione tensione saldatura - uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta la relazione tensione saldatura - uscita analogica
    * @param [in] relation Valore della relazione tensione-uscita analogica
    * @return Codice di errore
    */
    int WeldingSetVoltageRelation(WeldVoltageAORelation relation);

Ottenimento relazione corrente saldatura - uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene la relazione corrente saldatura - uscita analogica
    * @param [out] relation Valore della relazione
    * @return Codice di errore
    */
    int WeldingGetCurrentRelation(WeldCurrentAORelation relation);

Ottenimento relazione tensione saldatura - uscita analogica
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene la relazione tensione saldatura - uscita analogica
    * @param [out] relation Valore della relazione tensione-uscita analogica
    * @return Codice di errore
    */
    int WeldingGetVoltageRelation(WeldVoltageAORelation relation);

Impostazione corrente saldatura
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta la corrente di saldatura
    * @param [in] ioType Tipo IO controllo 0-IO quadro controllo; 1-IO esteso
    * @param [in] current Valore corrente saldatura (A)
    * @param [in] AOIndex Porta uscita analogica quadro controllo corrente (0-1)
    * @param [in] blend Smoothing 0-Nessuno; 1-Sì
    * @return Codice di errore
    */
    int WeldingSetCurrent(int ioType, double current, int AOIndex, int blend);

Impostazione tensione saldatura
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta la tensione di saldatura
    * @param [in] ioType Tipo IO controllo 0-IO quadro controllo; 1-IO esteso
    * @param [in] voltage Valore tensione saldatura (A)
    * @param [in] AOIndex Porta uscita analogica quadro controllo tensione (0-1)
    * @param [in] blend Smoothing 0-Nessuno; 1-Sì
    * @return Codice di errore
    */
    int WeldingSetVoltage(int ioType, double voltage, int AOIndex, int blend);

Impostazione parametri oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i parametri di oscillazione
    * @param [in] weaveNum Numero configurazione parametri oscillazione
    * @param [in] weaveType Tipo oscillazione 0-Onda triangolare piano; 1-Onda triangolare L verticale; 2-Onda circolare oraria; 3-Onda circolare antioraria; 4-Onda sinusoidale piano; 5-Onda sinusoidale L verticale; 6-Onda triangolare verticale; 7-Onda sinusoidale verticale
    * @param [in] weaveFrequency Frequenza oscillazione (Hz)
    * @param [in] weaveIncStayTime Modalità attesa 0-Ciclo non include tempo attesa; 1-Ciclo include tempo attesa
    * @param [in] weaveRange Ampiezza oscillazione (mm)
    * @param [in] weaveLeftRange Lunghezza corda sinistra oscillazione triangolare verticale (mm)
    * @param [in] weaveRightRange Lunghezza corda destra oscillazione triangolare verticale (mm)
    * @param [in] additionalStayTime Tempo permanenza punto triangolo verticale oscillazione triangolare (ms)
    * @param [in] weaveLeftStayTime Tempo permanenza sinistra (ms)
    * @param [in] weaveRightStayTime Tempo permanenza destra (ms)
    * @param [in] weaveCircleRadio Rapporto callback oscillazione circolare (0-100%)
    * @param [in] weaveStationary Attesa posizione oscillazione, 0-Posizione continua durante attesa; 1-Posizione stazionaria durante attesa
    * @param [in] weaveYawAngle Angolo azimut direzione oscillazione (rotazione asse Z oscillazione), unità °
    * @param [in] weaveRotAngle Angolo rotazione direzione oscillazione (rotazione asse X oscillazione), unità °
    * @return Codice di errore
    */
    int WeaveSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, double weaveLeftRange, double weaveRightRange, int additionalStayTime, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary, double weaveYawAngle,double weaveRotAngle)

Esempio codice impostazione parametri saldatura
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSetWeldParam(Robot robot)
    {
        WeldingProcessParam para1=new WeldingProcessParam(177, 27, 1000, 178, 28, 176, 26, 1000);
        WeldingProcessParam para2=new WeldingProcessParam(188, 28, 555, 199, 29, 133, 23, 333);

        robot.WeldingSetProcessParam(1, para1);
        robot.WeldingSetProcessParam(2, para2);

        double startCurrent = 0;
        double startVoltage = 0;
        int startTime = 0;
        double weldCurrent = 0;
        double weldVoltage = 0;
        double endCurrent = 0;
        double endVoltage = 0;
        int endTime = 0;

        WeldingProcessParam param=new WeldingProcessParam( startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime);
        robot.WeldingGetProcessParam(1,param);
        robot.WeldingGetProcessParam(2,param);

        WeldCurrentAORelation rela1=new WeldCurrentAORelation(0,400,0,10,0);
        int rtn = robot.WeldingSetCurrentRelation(rela1);

        WeldVoltageAORelation rela2=new WeldVoltageAORelation(0, 40, 0, 10, 1);
        rtn = robot.WeldingSetVoltageRelation(rela2);

        double current_min = 0;
        double current_max = 0;
        double vol_min = 0;
        double vol_max = 0;
        double output_vmin = 0;
        double output_vmax = 0;
        int curIndex = 0;
        int volIndex = 0;
        WeldCurrentAORelation rela3=new WeldCurrentAORelation(current_min, current_max, output_vmin, output_vmax, curIndex);
        rtn = robot.WeldingGetCurrentRelation(rela3);

        WeldVoltageAORelation rela4=new WeldVoltageAORelation(0,0,0,0,0);
        rtn = robot.WeldingGetVoltageRelation(rela4);

        rtn = robot.WeldingSetCurrent(0, 100, 0, 0);

        robot.Sleep(3000);

        rtn = robot.WeldingSetVoltage(0, 10, 0, 0);

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0, 60.000000,0);

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0);

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200);
        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0);
        int enable = 0;
        double length = 0;
        double velocity = 0;
        int moveType = 0;
        int checkEnable = 0;
        int arcInterruptTimeLength = 0;
        List<Integer> inter=new ArrayList<>();
        List<Number> num=new ArrayList<>();

        inter = robot.WeldingGetCheckArcInterruptionParam();
        num = robot.WeldingGetReWeldAfterBreakOffParam();

        robot.SetWeldMachineCtrlModeExtDoNum(17);
        for (int i = 0; i < 5; i++)
        {
            robot.SetWeldMachineCtrlMode(0);
            robot.Sleep(1000);
            robot.SetWeldMachineCtrlMode(1);
            robot.Sleep(1000);
        }
        return 0;
    }

Impostazione istantanea parametri oscillazione
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Impostazione istantanea parametri oscillazione
    * @param [in] weaveNum Numero configurazione parametri oscillazione
    * @param [in]weaveType Tipo oscillazione 0-Onda triangolare piano; 1-Onda triangolare L verticale; 2-Onda circolare oraria; 3-Onda circolare antioraria; 4-Onda sinusoidale piano; 5-Onda sinusoidale L verticale; 6-Onda triangolare verticale; 7-Onda sinusoidale verticale
    * @param [in]weaveFrequency Frequenza oscillazione (Hz)
    * @param [in]weaveIncStayTime Modalità attesa 0-Ciclo non include tempo attesa; 1-Ciclo include tempo attesa
    * @param [in]weaveRange Ampiezza oscillazione (mm)
    * @param [in]weaveLeftStayTime Tempo permanenza sinistra (ms)
    * @param [in]weaveRightStayTime Tempo permanenza destra (ms)
    * @param [in]weaveCircleRadio Rapporto callback oscillazione circolare (0-100%)
    * @param [in]weaveStationary Attesa posizione oscillazione, 0-Posizione continua durante attesa; 1-Posizione stazionaria durante attesa
    * @return Codice di errore
    */
    int WeaveOnlineSetPara(int weaveNum, int weaveType, double weaveFrequency, int weaveIncStayTime, double weaveRange, int weaveLeftStayTime, int weaveRightStayTime, int weaveCircleRadio, int weaveStationary);

Impostazione parametri rilevamento interruzione arco saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta i parametri di rilevamento interruzione arco saldatura
    * @param [in] checkEnable Abilita rilevamento; 0-Disabilita; 1-Abilita
    * @param [in] arcInterruptTimeLength Durata conferma interruzione arco (ms)
    * @return Codice di errore 
    */
    int WeldingSetCheckArcInterruptionParam(int checkEnable, int arcInterruptTimeLength);

Ottenimento parametri rilevamento interruzione arco saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene i parametri di rilevamento interruzione arco saldatura
    * @return List[0]:Codice errore; List[1]:double Abilita rilevamento; 0-Disabilita; 1-Abilita; List[2]:Durata conferma interruzione arco (ms) 
    */
    List<Integer> WeldingGetCheckArcInterruptionParam();

Impostazione parametri recupero interruzione saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta i parametri di recupero interruzione saldatura
    * @param [in] enable Abilita recupero interruzione saldatura
    * @param [in] length Distanza sovrapposizione cordone (mm)
    * @param [in] velocity Percentuale velocità robot ritorno punto riaccensione (0-100)
    * @param [in] moveType Modalità movimento robot punto riaccensione; 0-LIN; 1-PTP
    * @return Codice di errore 
    */
    int WeldingSetReWeldAfterBreakOffParam(int enable, double length, double velocity, int moveType);

Ottenimento parametri recupero interruzione saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene i parametri di recupero interruzione saldatura
    * @return List[0]:Codice errore; List[1]:int Abilita recupero interruzione saldatura; List[2]:double Distanza sovrapposizione cordone (mm);
    * @return List[3]:double Percentuale velocità robot ritorno punto riaccensione (0-100);List[4]:int Modalità movimento robot punto riaccensione; 0-LIN; 1-PTP 
    */
    List<Number> WeldingGetReWeldAfterBreakOffParam();

Impostazione porta DO estesa modalità controllo saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta la porta DO estesa modalità controllo saldatrice
    * @param [in] DONum Porta DO modalità controllo saldatrice (0-127)
    * @return Codice di errore 
    */
    int SetWeldMachineCtrlModeExtDoNum(int DONum);

Impostazione modalità controllo saldatrice
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta la modalità di controllo della saldatrice
    * @param [in] mode Modalità controllo saldatrice; 0-Unificata
    * @return Codice di errore 
    */
    int SetWeldMachineCtrlMode(int mode);

Inizio saldatura
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio saldatura
    * @param [in] ioType Tipo io 0-IO controllore; 1-IO esteso
    * @param [in] arcNum Numero file configurazione saldatrice
    * @param [in] timeout Timeout accensione arco
    * @return Codice di errore
    */
    int ARCStart(int ioType, int arcNum, int timeout);

Fine saldatura
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine saldatura
    * @param [in] ioType Tipo io 0-IO controllore; 1-IO esteso
    * @param [in] arcNum Numero file configurazione saldatrice
    * @param [in] timeout Timeout spegnimento arco
    * @return Codice di errore
    */
    int ARCEnd(int ioType, int arcNum, int timeout);

Inizio oscillazione
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio oscillazione
    * @param [in] weaveNum Numero configurazione parametri oscillazione
    * @return Codice di errore
    */
    int WeaveStart(int weaveNum);

Fine oscillazione
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine oscillazione
    * @param [in] weaveNum Numero configurazione parametri oscillazione
    * @return Codice di errore
    */
    int WeaveEnd(int weaveNum);

Alimentazione filo in avanti
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Alimentazione filo in avanti
    * @param [in] ioType Tipo io  0-IO controllore; 1-IO esteso
    * @param [in] wireFeed Controllo alimentazione filo  0-Arresta alimentazione; 1-Alimenta
    * @return Codice di errore
    */
    int SetForwardWireFeed(int ioType, int wireFeed); 	

Alimentazione filo inversa
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Alimentazione filo inversa
    * @param [in] ioType Tipo io  0-IO controllore; 1-IO esteso
    * @param [in] wireFeed Controllo alimentazione filo  0-Arresta alimentazione; 1-Alimenta
    * @return Codice di errore
    */
    int SetReverseWireFeed(int ioType, int wireFeed);

Alimentazione gas
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Alimentazione gas
    * @param [in] ioType Tipo io  0-IO controllore; 1-IO esteso
    * @param [in] airControl Controllo alimentazione gas  0-Arresta gas; 1-Alimenta gas
    * @return Codice di errore
    */
    int SetAspirated(int ioType, int airControl);

Impostazione riavvio saldatura dopo interruzione
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il riavvio della saldatura dopo interruzione
    * @return Codice di errore 
    */
    int WeldingStartReWeldAfterBreakOff();

Impostazione uscita saldatura dopo interruzione
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta l'uscita dalla saldatura dopo interruzione
    * @return Codice di errore 
    */
    int WeldingAbortWeldAfterBreakOff();

Esempio codice controllo saldatura robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWelding(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ARCStart(1, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.ARCEnd(1, 0, 10000);
        robot.WeaveEnd(0);
        return 0;
    }

Inizio saldatura segmentata
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inizio saldatura segmentata
    * @param [in] startDesePos Posizione cartesiana punto iniziale
    * @param [in] endDesePos Posa cartesiana punto finale
    * @param [in] startJPos Posa giunti punto iniziale
    * @param [in] endJPos Posa giunti punto finale
    * @param [in] weldLength Lunghezza segmento saldatura (mm)
    * @param [in] noWeldLength Lunghezza segmento non saldatura (mm)
    * @param [in] weldIOType Tipo IO saldatura (0-IO quadro controllo; 1-IO esteso)
    * @param [in] arcNum Numero file configurazione saldatrice
    * @param [in] weldTimeout Timeout accensione/spegnimento arco
    * @param [in] isWeave Se oscillazione
    * @param [in] weaveNum Numero configurazione parametri oscillazione
    * @param [in] tool Numero utensile
    * @param [in] user Numero pezzo
    * @param [in] vel  Percentuale velocità, intervallo [0~100]
    * @param [in] acc  Percentuale accelerazione, intervallo [0~100], attualmente non disponibile
    * @param [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smoothing (non bloccante), unità mm
    * @param [in] epos  Posizione assi estesi, unità mm
    * @param [in] search  0-Nessuna ricerca filo, 1-Ricerca filo
    * @param [in] offset_flag  0-Nessun offset, 1-Offset sistema base/pezzo, 2-Offset sistema utensile
    * @param [in] offset_pos  Quantità offset posa
    * @return Codice di errore 
    */
    int SegmentWeldStart(DescPose startDesePos, DescPose endDesePos, JointPos startJPos, JointPos endJPos, double weldLength, double noWeldLength, int weldIOType,int arcNum, int weldTimeout, boolean isWeave, int weaveNum, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos);

Esempio codice saldatura segmentata robot
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSegWeld(Robot robot)
    {
        robot.WeldingSetCurrent(0, 230, 0, 0);
        robot.WeldingSetVoltage(0, 24, 0, 1);

        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);

        int rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, true,0, 1, 0, 30, 100, 100, -1, exaxisPos, 0, 0, offdese);
        return 0;
    }

Inizio oscillazione simulazione
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inizio oscillazione simulazione
    * @param [in] weaveNum  Numero parametri oscillazione
    * @return Codice di errore 
    */
    int WeaveStartSim(int weaveNum);

Fine oscillazione simulazione
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Fine oscillazione simulazione
    * @param [in] weaveNum  Numero parametri oscillazione
    * @return Codice di errore 
    */
    int WeaveEndSim(int weaveNum);

Inizio rilevamento preallarme traiettoria (senza movimento)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inizio rilevamento preallarme traiettoria (senza movimento)
    * @param [in] weaveNum   Numero parametri oscillazione
    * @return Codice di errore 
    */
    int WeaveInspectStart(int weaveNum);

Fine rilevamento preallarme traiettoria (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Fine rilevamento preallarme traiettoria (senza movimento)
    * @param [in] weaveNum   Numero parametri oscillazione
    * @return Codice di errore 
    */
    int WeaveInspectEnd(int weaveNum);

Inizio variazione graduale oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief  Inizio variazione graduale oscillazione
    * @param  [in] weaveChangeFlag 1-Varia parametri oscillazione; 2-Varia parametri oscillazione + velocità saldatura
    * @param  [in] weaveNum Numero oscillazione
    * @param  [in] velStart Velocità inizio saldatura, (cm/min)
    * @param  [in] velEnd Velocità fine saldatura, (cm/min)
    * @return Codice di errore
    */
    int WeaveChangeStart(int weaveChangeFlag, int weaveNum, double velStart, double velEnd)

Esempio codice saldatura con variazione graduale oscillazione robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWeave(Robot robot)
    {
        DescPose p1Desc=new DescPose(228.879, -503.594, 453.984, -175.580, 8.293, 171.267);
        JointPos p1Joint=new JointPos(102.700, -85.333, 90.518, -102.365, -83.932, 22.134);

        DescPose p2Desc=new DescPose(-333.302, -435.580, 449.866, -174.997, 2.017, 109.815);
        JointPos p2Joint=new JointPos(41.862, -85.333, 90.526, -100.587, -90.014, 22.135);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveStartSim(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveEndSim(0);
        robot.MoveJ(p1Joint, p1Desc, 13, 0, 20, 100, 100, exaxisPos, -1, 0, offdese);
        robot.WeaveInspectStart(0);
        robot.MoveL(p2Joint, p2Desc, 13, 0, 20, 100, 100, -1, 0, exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveInspectEnd(0);

        robot.WeldingSetVoltage(1, 19, 0, 0);
        robot.WeldingSetCurrent(1, 190, 0, 0);
        robot.MoveL(p1Joint, p1Desc, 1, 1, 100, 100, 50, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.ARCStart(1, 0, 10000);
        robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(1, 0, 50, 30);
        robot.MoveL(p2Joint, p2Desc, 1, 1, 100, 100, 1, -1, 0,exaxisPos, 0, 0, offdese,0,10);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0);
        robot.ARCEnd(1, 0, 10000);
        return 0;
    }

Fine variazione graduale oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.2-3.7.9

.. code-block:: Java
    :linenos:

    /**
    * @brief Fine variazione graduale oscillazione
    * @return Codice di errore
    */
    int WeaveChangeEnd(); 

IO estesi - Configurazione segnale rilevamento gas saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale rilevamento gas saldatrice
    * @param [in] DONum  Numero DO esteso segnale rilevamento gas
    * @return Codice di errore 
    */
    int SetAirControlExtDoNum(int DONum);

IO estesi - Configurazione segnale accensione arco saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale accensione arco saldatrice
    * @param [in] DONum  Numero DO esteso segnale accensione arco
    * @return Codice di errore 
    */
    int SetArcStartExtDoNum(int DONum);

IO estesi - Configurazione segnale alimentazione filo inversa saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale alimentazione filo inversa saldatrice
    * @param [in] DONum  Numero DO esteso segnale alimentazione filo inversa
    * @return Codice di errore 
    */
    int SetWireReverseFeedExtDoNum(int DONum);

IO estesi - Configurazione segnale alimentazione filo in avanti saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale alimentazione filo in avanti saldatrice
    * @param [in] DONum  Numero DO esteso segnale alimentazione filo in avanti
    * @return Codice di errore 
    */
    int SetWireForwardFeedExtDoNum(int DONum);

IO estesi - Configurazione segnale successo accensione arco saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale successo accensione arco saldatrice
    * @param [in] DINum  Numero DI esteso segnale successo accensione arco
    * @return Codice di errore 
    */
    int SetArcDoneExtDiNum(int DINum);

IO estesi - Configurazione segnale pronto saldatrice
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnale pronto saldatrice
    * @param [in] DINum  Numero DI esteso segnale pronto saldatrice
    * @return Codice di errore 
    */
    int SetWeldReadyExtDiNum(int DINum);

IO estesi - Configurazione segnali recupero interruzione saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief IO estesi - Configurazione segnali recupero interruzione saldatura
    * @param [in] reWeldDINum  Numero DI esteso segnale riavvio saldatura dopo interruzione
    * @param [in] abortWeldDINum  Numero DI esteso segnale uscita saldatura dopo interruzione
    * @return Codice di errore 
    */
    int SetExtDIWeldBreakOffRecover(int reWeldDINum, int abortWeldDINum);

Esempio codice impostazione segnali IO estesi saldatura
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExtDIConfig(Robot robot)
    {
        robot.SetArcStartExtDoNum(10);
        robot.SetAirControlExtDoNum(20);
        robot.SetWireForwardFeedExtDoNum(30);
        robot.SetWireReverseFeedExtDoNum(40);

        robot.SetWeldReadyExtDiNum(50);
        robot.SetArcDoneExtDiNum(60);
        robot.SetExtDIWeldBreakOffRecover(70, 80);
        robot.SetWireSearchExtDIONum(0, 1);

        return 0;
    }

Controllo tracciamento arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.2-3.7.9

.. code-block:: Java
    :linenos:

    /** 
    * @brief Controllo tracciamento arco
    * @param [in] flag Interruttore, 0-Spegnimento; 1-Accensione
    * @param [in] delaytime Tempo ritardo, unità ms
    * @param [in] isLeftRight Compensazione deviazione sinistra-destra
    * @param [in] klr Coefficiente regolazione sinistra-destra (sensibilità)
    * @param [in] tStartLr Tempo inizio compensazione sinistra-destra cyc
    * @param [in] stepMaxLr Compensazione massima per ciclo sinistra-destra mm
    * @param [in] sumMaxLr Compensazione totale massima sinistra-destra mm
    * @param [in] isUpLow Compensazione deviazione alto-basso
    * @param [in] kud Coefficiente regolazione alto-basso (sensibilità)
    * @param [in] tStartUd Tempo inizio compensazione alto-basso cyc
    * @param [in] stepMaxUd Compensazione massima per ciclo alto-basso mm
    * @param [in] sumMaxUd Compensazione totale massima alto-basso
    * @param [in] axisSelect Selezione sistema coordinate alto-basso, 0-Oscillazione; 1-Utensile; 2-Base
    * @param [in] referenceType Modalità impostazione corrente riferimento alto-basso, 0-Retroazione; 1-Costante
    * @param [in] referSampleStartUd Conteggio inizio campionamento corrente riferimento alto-basso (retroazione), cyc
    * @param [in] referSampleCountUd Conteggio cicli campionamento corrente riferimento alto-basso (retroazione), cyc
    * @param [in] referenceCurrent Corrente riferimento alto-basso mA
    * @param [in] offsetType Tipo tracciamento offset, 0-Nessun offset; 1-Campionamento; 2-Percentuale
    * @param [in] offsetParameter Parametro offset; Campionamento (tempo inizio campionamento offset, default un ciclo); Percentuale (percentuale offset (-100 ~ 100))
    * @return Codice di errore 
    */
    int ArcWeldTraceControl(int flag, double delaytime, int isLeftRight, double klr, double tStartLr, double stepMaxLr, double sumMaxLr, int isUpLow, double kud, double tStartUd, double stepMaxUd, double sumMaxUd, int axisSelect, int referenceType, double referSampleStartUd, double referSampleCountUd, double referenceCurrent,int offsetType, int offsetParameter);

Selezione banda passante AI tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Selezione banda passante AI tracciamento arco
    * @param  channel Selezione banda passante AI tracciamento arco,[0-3]
    * @return  Codice di errore
    */
    public int ArcWeldTraceExtAIChannelConfig(int channel)

Attivazione tracciamento arco + compensazione multistrato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attivazione tracciamento arco + compensazione multistrato multi-passata
    * @return Codice di errore
    */
    public int ArcWeldTraceReplayStart()

Disattivazione tracciamento arco + compensazione multistrato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Disattivazione tracciamento arco + compensazione multistrato multi-passata
    * @return Codice di errore
    */
    public int ArcWeldTraceReplayEnd()

Trasformazione coordinate offset - Saldatura multistrato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Trasformazione coordinate offset - Saldatura multistrato multi-passata
    * @param pointO Posa cartesiana punto riferimento
    * @param pointX Posa cartesiana punto direzione offset X
    * @param pointZ Posa cartesiana punto direzione offset Z
    * @param dx Offset direzione x (mm)
    * @param dz Offset direzione z (mm)
    * @param dry Offset rotazione asse y (°)
    * @param offset Risultato calcolo offset
    * @return Codice di errore
    */
    public int MultilayerOffsetTrsfToBase(DescTran pointO, DescTran pointX, DescTran pointZ, double dx, double dz, double dry, DescPose offset)

Esempio codice tracciamento arco saldatura multistrato multi-passata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestArcWeldTrace(Robot robot)
    {
        JointPos mulitilineorigin1_joint=new JointPos(-24.090, -63.501, 84.288, -111.940, -93.426, 57.669);
        DescPose mulitilineorigin1_desc=new DescPose(-677.559, 190.951, -1.205, 1.144, -41.482, -82.577);

        DescTran mulitilineX1_desc=new DescTran(0,0,0);
        mulitilineX1_desc.x = -677.556;
        mulitilineX1_desc.y = 211.949;
        mulitilineX1_desc.z = -1.206;

        DescTran mulitilineZ1_desc=new DescTran(0,0,0);
        mulitilineZ1_desc.x = -677.564;
        mulitilineZ1_desc.y = 190.956;
        mulitilineZ1_desc.z = 19.817;

        JointPos mulitilinesafe_joint=new JointPos(-25.734, -63.778, 81.502, -108.975, -93.392, 56.021);
        DescPose mulitilinesafe_desc=new DescPose(-677.561, 211.950, 19.812, 1.144, -41.482, -82.577);
        JointPos mulitilineorigin2_joint=new JointPos(-29.743, -75.623, 101.241, -116.354, -94.928, 55.735);
        DescPose mulitilineorigin2_desc=new DescPose(-563.961, 215.359, -0.681, 2.845, -40.476, -87.443);

        DescTran mulitilineX2_desc=new DescTran(0,0,0);
        mulitilineX2_desc.x = -563.965;
        mulitilineX2_desc.y = 220.355;
        mulitilineX2_desc.z = -0.680;

        DescTran mulitilineZ2_desc=new DescTran(0,0,0);
        mulitilineZ2_desc.x = -563.968;
        mulitilineZ2_desc.y = 215.362;
        mulitilineZ2_desc.z = 4.331;

        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        DescPose offset=new DescPose(0, 0, 0, 0, 0, 0);

        robot.Sleep(10);
        int error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 0, offset, 0, 100);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 0, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.WeaveStart(0);

        error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 1, 100, 100, -1, 0,epos, 0, 0,offset, 0, 100);

        error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0);

        error = robot.WeaveEnd(0);

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1, 0,epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0, offset);

        error = robot.ArcWeldTraceReplayStart();

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1, 0,epos, 0, 1, offset, 0, 100);

        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 10000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc.tran, mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0, offset);

        error = robot.MoveL(mulitilineorigin1_joint, mulitilineorigin1_desc, 13, 0, 10, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ARCStart(1, 0, 3000);

        error = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc.tran, mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0, offset);

        error = robot.ArcWeldTraceReplayStart();

        error = robot.MoveL(mulitilineorigin2_joint, mulitilineorigin2_desc, 13, 0, 2, 100, 100, -1,0, epos, 0, 1, offset, 0, 100);

        error = robot.ArcWeldTraceReplayEnd();

        error = robot.ARCEnd(1, 0, 3000);

        error = robot.MoveJ(mulitilinesafe_joint, mulitilinesafe_desc, 13, 0, 10, 100, 100, epos, -1, 0, offset);

        robot.CloseRPC();
        return 0;
    }

Selezione canale AI retroazione corrente saldatrice tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Selezione canale AI retroazione corrente saldatrice tracciamento arco
    * @param  [in] channel Canale; 0-AI esteso0; 1-AI esteso1; 2-AI esteso2; 3-AI esteso3; 4-AI quadro controllo0; 5-AI quadro controllo1
    * @return Codice di errore
    */
    int ArcWeldTraceAIChannelCurrent(int channel)

Selezione canale AI retroazione tensione saldatrice tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Selezione canale AI retroazione tensione saldatrice tracciamento arco
    * @param  [in] channel Canale; 0-AI esteso0; 1-AI esteso1; 2-AI esteso2; 3-AI esteso3; 4-AI quadro controllo0; 5-AI quadro controllo1
    * @return Codice di errore
    */
    int ArcWeldTraceAIChannelVoltage(int channel)

Parametri conversione retroazione corrente saldatrice tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Parametri conversione retroazione corrente saldatrice tracciamento arco
    * @param [in] AILow Limite inferiore canale AI, valore default 0V, intervallo [0-10V]
    * @param [in] AIHigh Limite superiore canale AI, valore default 10V, intervallo [0-10V]
    * @param [in] currentLow Valore corrente saldatrice corrispondente limite inferiore AI, valore default 0V, intervallo [0-200V]
    * @param [in] currentHigh Valore corrente saldatrice corrispondente limite superiore AI, valore default 100V, intervallo [0-200V]
    * @return Codice di errore
    */
    int ArcWeldTraceCurrentPara(double AILow, double AIHigh, double currentLow, double currentHigh)

Parametri conversione retroazione tensione saldatrice tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Parametri conversione retroazione tensione saldatrice tracciamento arco
    * @param [in] AILow Limite inferiore canale AI, valore default 0V, intervallo [0-10V]
    * @param [in] AIHigh Limite superiore canale AI, valore default 10V, intervallo [0-10V]
    * @param [in] voltageLow Valore tensione saldatrice corrispondente limite inferiore AI, valore default 0V, intervallo [0-200V]
    * @param [in] voltageHigh Valore tensione saldatrice corrispondente limite superiore AI, valore default 100V, intervallo [0-200V]
    * @return Codice di errore
    */
    int ArcWeldTraceVoltagePara(double AILow, double AIHigh, double voltageLow, double voltageHigh)

Esempio codice tracciamento arco
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void WeldTraceControlWithCtrlBoxAI(Robot robot)
    {
        DescPose startdescPose = new DescPose(-473.86, 257.879, -20.849, -37.317, -42.021, 2.543);
        JointPos startjointPos = new JointPos(-43.487, -76.526, 95.568, -104.445, -89.356, 3.72);

        DescPose safedescPose = new DescPose(-504.043, 275.181, 40.908, -28.002, -42.025, -14.044);
        JointPos safejointPos = new JointPos(-39.078, -76.732, 87.227, -99.47, -94.301, 18.714);

        DescPose enddescPose = new DescPose(-499.844, 141.225, 7.72, -34.856, -40.17, 13.13);
        JointPos endjointPos = new JointPos(-31.305, -82.998, 99.401, -104.426, -89.35, 3.696);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        //Movimento iniziale a punto sicuro
        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 20, 100, exaxisPos, -1, 0, offdese);

        WeldCurrentAORelation current = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation voltage = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(current);//Relazione corrente-uscita analogica
        robot.WeldingSetVoltageRelation(voltage);//Relazione tensione-uscita analogica
        robot.WeldingSetVoltage(0, 25, 1, 0);//Imposta tensione
        robot.WeldingSetCurrent(0, 260, 0, 0);//Imposta corrente

        int rtn = robot.ArcWeldTraceAIChannelCurrent(4);
        System.out.println("ArcWeldTraceAIChannelCurrent rtn is " + rtn);

        rtn = robot.ArcWeldTraceAIChannelVoltage(5);
        System.out.println("ArcWeldTraceAIChannelVoltage rtn is " + rtn);

        rtn = robot.ArcWeldTraceCurrentPara(0.0, 5, 0, 500);
        System.out.println("ArcWeldTraceCurrentPara rtn is " + rtn);

        rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50);
        System.out.println("ArcWeldTraceVoltagePara rtn is " + rtn);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
        robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 20, 20, 100, exaxisPos, -1, 0, offdese);
    }

Impostazione porte IO estesi ricerca filo
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostazione porte IO estesi ricerca filo
    * @param [in] searchDoneDINum Porta DO successo ricerca filo (0-127)
    * @param [in] searchStartDONum Porta DO controllo avvio/arresto ricerca filo (0-127)
    * @return Codice di errore
    */
    int SetWireSearchExtDIONum(int searchDoneDINum, int searchStartDONum);

Programma di esempio
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    private static void TestUDPWireSearch(Robot robot)
    {
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);//Comunicazione UDP assi estesi

        robot.SetWireSearchExtDIONum(0, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos(0.0, 0.0, 0.0, 0.0);
        DescPose offdese = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);

        DescPose descStart = new DescPose(-158.767, -510.596, 271.709, -179.427, -0.745, -137.349);
        JointPos jointStart = new JointPos(61.667, -79.848, 108.639, -119.682, -89.700, -70.985);

        DescPose descEnd = new DescPose(0.332, -516.427, 270.688, 178.165, 0.017, -119.989);
        JointPos jointEnd = new JointPos(79.021, -81.839, 110.752, -118.298, -91.729, -70.981);

        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);

        DescPose descREF0A = new DescPose(-66.106, -560.746, 270.381, 176.479, -0.126, -126.745);
        JointPos jointREF0A = new JointPos(73.531, -75.588, 102.941, -116.250, -93.347, -69.689);

        DescPose descREF0B = new DescPose(-66.109, -528.440, 270.407, 176.479, -0.129, -126.744);
        JointPos jointREF0B = new JointPos(72.534, -79.625, 108.046, -117.379, -93.366, -70.687);

        DescPose descREF1A = new DescPose(72.975, -473.242, 270.399, 176.479, -0.129, -126.744);
        JointPos jointREF1A = new JointPos(87.169, -86.509, 115.710, -117.341, -92.993, -56.034);

        DescPose descREF1B = new DescPose(31.355, -473.238, 270.405, 176.480, -0.130, -126.745);
        JointPos jointREF1B = new JointPos(82.117, -87.146, 116.470, -117.737, -93.145, -61.090);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //Punto iniziale
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //Punto direzione
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //Punto iniziale
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //Punto direzione
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //Punto iniziale
        robot.MoveL(jointREF0B, descREF0B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //Punto direzione
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);  //Punto iniziale
        robot.MoveL(jointREF1B, descREF1B, 1, 0, 10, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);  //Punto direzione
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef = {"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = {"RES0", "RES1", "#", "#", "#", "#"};
        int offectFlag = 0;
        //DescPose offectPos = new DescPose(0, 0, 0, 0, 0, 0);
        DescOffset offset = new DescOffset();
        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offset);
        robot.PointsOffsetEnable(0, offset.offset);
        robot.MoveL(jointStart, descStart, 1, 0, 100, 100, 100, -1, exaxisPos, 0, 0, offdese, 0, 100);
        robot.MoveL(jointEnd, descEnd, 1, 0, 100, 100, 100, -1, exaxisPos, 1, 0, offdese, 0, 100);
        robot.PointsOffsetDisable();
    }

Inizio ricerca filo
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Inizio ricerca filo
    * @param [in] refPos  1-Punto riferimento 0-Punto contatto
    * @param [in] searchVel   Velocità ricerca %
    * @param [in] searchDis  Distanza ricerca mm
    * @param [in] autoBackFlag Flag ritorno automatico, 0-Nessuno; -Automatico
    * @param [in] autoBackVel  Velocità ritorno automatico %
    * @param [in] autoBackDis  Distanza ritorno automatico mm
    * @param [in] offectFlag  1-Ricerca con offset; 0-Ricerca punto insegnato
    * @return Codice di errore 
    */
    int WireSearchStart(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Fine ricerca filo
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Fine ricerca filo
    * @param [in] refPos  1-Punto riferimento 2-Punto contatto
    * @param [in] searchVel   Velocità ricerca %
    * @param [in] searchDis  Distanza ricerca mm
    * @param [in] autoBackFlag Flag ritorno automatico, 0-Nessuno; -Automatico
    * @param [in] autoBackVel  Velocità ritorno automatico %
    * @param [in] autoBackDis  Distanza ritorno automatico mm
    * @param [in] offectFlag  1-Ricerca con offset; 2-Ricerca punto insegnato
    * @return Codice di errore 
    */
    int WireSearchEnd(int refPos, double searchVel, int searchDis, int autoBackFlag, double autoBackVel, int autoBackDis, int offectFlag);

Calcolo offset ricerca filo
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcolo offset ricerca filo
    * @param [in] seamType  Tipo cordone
    * @param [in] method   Metodo calcolo
    * @param [in] varNameRef Punti riferimento 1-6, "#" indica variabile senza punto
    * @param [in] varNameRes Punti contatto 1-6, "#" indica variabile senza punto
    * @param [out] offset Posa offset [x, y, z, a, b, c] e modalità offset
    * @return Codice di errore 
    */
    int GetWireSearchOffset(int seamType, int method, String[] varNameRef, String[] varNameRes, DescOffset offset);

Attesa completamento ricerca filo
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Attesa completamento ricerca filo
    * @return Codice di errore 
    */
    int WireSearchWait(String name);

Scrittura punto contatto ricerca filo database
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Scrittura punto contatto ricerca filo database
    * @param [in] varName  Nome punto contatto "RES0" ~ "RES99"
    * @param [in] pos  Dati punto contatto [x, y, x, a, b, c]
    * @return Codice di errore 
    */
    int SetPointToDatabase(String varName, DescPose pos);

Esempio codice ricerca filo robot
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWireSearch(Robot robot)
    {
        DescPose toolCoord=new DescPose(0, 0, 200, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);
        DescPose wobjCoord=new DescPose(0, 0, 0, 0, 0, 0);
        robot.SetWObjCoord(1, wobjCoord, 0);

        int rtn0, rtn1, rtn2 = 0;
        ExaxisPos exaxisPos = new ExaxisPos( 0, 0, 0, 0 );
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);


        DescPose descStart = new DescPose(216.543, 445.175, 93.465, 179.683, 1.757, -112.641);
        JointPos jointStart = new JointPos(-128.345, -86.660, 114.679, -119.625, -89.219, 74.303);

        DescPose descEnd =new DescPose(111.143, 523.384, 87.659, 179.703, 1.835, -97.750);
        JointPos jointEnd =new JointPos(-113.454, -81.060, 109.328, -119.954, -89.218, 74.302 );

        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,100);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,100);

        DescPose descREF0A = new DescPose(142.135, 367.604, 86.523, 179.728, 1.922, -111.089);
        JointPos jointREF0A =new JointPos(-126.794, -100.834, 128.922, -119.864, -89.218, 74.302);

        DescPose descREF0B = new DescPose(254.633, 463.125, 72.604, 179.845, 2.341, -114.704);
        JointPos jointREF0B = new JointPos(-130.413, -81.093, 112.044, -123.163, -89.217, 74.303);

        DescPose descREF1A =new DescPose(92.556, 485.259, 47.476, -179.932, 3.130, -97.512);
        JointPos jointREF1A =new JointPos(-113.231, -83.815, 119.877, -129.092, -89.217, 74.303);

        DescPose descREF1B =new DescPose(203.103, 583.836, 63.909, 179.991, 2.854, -103.372);
        JointPos jointREF1B = new JointPos(-119.088, -69.676, 98.692, -121.761, -89.219, 74.303);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //Punto iniziale
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //Punto direzione
        rtn1 = robot.WireSearchWait("REF0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //Punto iniziale
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //Punto direzione
        rtn1 = robot.WireSearchWait("REF1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF0A, descREF0A, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);  //Punto iniziale
        robot.MoveL(jointREF0B, descREF0B, 1, 1, 100, 100, 100, -1,0, exaxisPos, 1, 0, offdese,0,10);  //Punto direzione
        rtn1 = robot.WireSearchWait("RES0");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        rtn0 = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0);
        robot.MoveL(jointREF1A, descREF1A, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese,0,10);  //Punto iniziale
        robot.MoveL(jointREF1B, descREF1B, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);  //Punto direzione
        rtn1 = robot.WireSearchWait("RES1");
        rtn2 = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0);

        String[] varNameRef =new String[]{"REF0", "REF1", "#", "#", "#", "#"};
        String[] varNameRes = new String[]{ "RES0", "RES1", "#", "#", "#", "#" };
        int offectFlag = 0;

        DescPose pos = new DescPose(0,0,0,0,0,0);
        DescOffset offectPos=new DescOffset();
        offectPos.offset=pos;
        offectPos.offsetFlag=0;

        rtn0 = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes, offectPos);
        robot.PointsOffsetEnable(0, pos);
        robot.MoveL(jointStart, descStart, 1, 1, 100, 100, 100, -1,0, exaxisPos, 0, 0, offdese,0,10);
        robot.MoveL(jointEnd, descEnd, 1, 1, 100, 100, 100, -1, 0,exaxisPos, 1, 0, offdese,0,10);
        robot.PointsOffsetDisable();

        robot.CloseRPC();
        return 0;
    }

Inizio variazione graduale tensione saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio variazione graduale tensione saldatura
    * @param [in] IOType Tipo controllo; 0-IO quadro controllo; 1-Protocollo comunicazione digitale (UDP);2-Protocollo comunicazione digitale (ModbusTCP)
    * @param [in] voltageStart Tensione saldatura iniziale (V)
    * @param [in] voltageEnd Tensione saldatura finale (V)
    * @param [in] AOIndex Numero porta AO quadro controllo (0-1)
    * @param [in] blend Smoothing 0-Nessuno; 1-Sì
    * @return Codice di errore
    */
    int WeldingSetVoltageGradualChangeStart(int IOType, double voltageStart, double voltageEnd, int AOIndex, int blend)

Fine variazione graduale tensione saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Fine variazione graduale tensione saldatura
    * @return Codice di errore
    */
    int WeldingSetVoltageGradualChangeEnd()

Inizio variazione graduale corrente saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio variazione graduale corrente saldatura
    * @param [in] IOType Tipo controllo; 0-IO quadro controllo; 1-Protocollo comunicazione digitale (UDP);2-Protocollo comunicazione digitale (ModbusTCP)
    * @param [in] currentStart Corrente saldatura iniziale (A)
    * @param [in] currentEnd Corrente saldatura finale (A)
    * @param [in] AOIndex Numero porta AO quadro controllo (0-1)
    * @param [in] blend Smoothing 0-Nessuno; 1-Sì
    * @return Codice di errore
    */
    int WeldingSetCurrentGradualChangeStart(int IOType, double currentStart, double currentEnd, int AOIndex, int blend)

Fine variazione graduale corrente saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Fine variazione graduale corrente saldatura
    * @return Codice di errore
    */
    int WeldingSetCurrentGradualChangeEnd()

Esempio codice variazione graduale corrente/tensione saldatura robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void WeldparamChange(Robot robot) 
    {
        DescPose startdescPose = new DescPose(-484.707, 276.996, -14.013, -37.657, -40.508, -1.548);
        JointPos startjointPos = new JointPos(-45.421, -75.673, 93.627, -104.302, -87.938, 6.005);

        DescPose enddescPose = new DescPose(-508.767, 137.109, -13.966, -37.639, -40.508, -1.559);
        JointPos endjointPos = new JointPos(-32.768, -80.947, 100.254, -106.201, -87.201, 18.648);

        DescPose safedescPose = new DescPose(-484.709, 294.436, 13.621, -37.660, -40.508, -1.545);
        JointPos safejointPos = new JointPos(-46.604, -75.410, 89.109, -100.003, -88.012, 4.823);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        WeldCurrentAORelation cur = new WeldCurrentAORelation(0, 495, 1, 10, 0);
        WeldVoltageAORelation vol = new WeldVoltageAORelation(10, 45, 1, 10, 1);
        robot.WeldingSetCurrentRelation(cur);
        robot.WeldingSetVoltageRelation(vol);

        robot.WeldingSetVoltage(0, 25, 1, 0);// ----Imposta tensione
        robot.WeldingSetCurrent(0, 260, 0, 0);// ----Imposta corrente

        robot.MoveJ(safejointPos, safedescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);

        robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0);
        robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0);
        int rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);

        robot.MoveJ(startjointPos, startdescPose, 1, 0, 5, 100, 100, exaxisPos, -1, 0, offdese);
        System.out.println("ArcWeldTraceControl rtn is " + rtn);

        robot.ARCStart(0, 0, 10000);
        robot.WeaveStart(0);
        robot.WeaveChangeStart(2, 1, 24, 36);
        robot.MoveL(endjointPos, enddescPose, 1, 0, 100, 100, 2, -1, 0, exaxisPos, 0, 0, offdese, 0, 10);
        robot.ARCEnd(0, 0, 10000);
        robot.WeaveChangeEnd();
        robot.WeaveEnd(0);
        robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0);
        robot.WeldingSetCurrentGradualChangeEnd();
        robot.WeldingSetVoltageGradualChangeEnd();
    }

Impostazione parametri oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Imposta i parametri di oscillazione personalizzati
     * @param [in] id Numero oscillazione personalizzata: 0-2
     * @param [in] pointNum Numero punti oscillazione 0-10
     * @param [in] point Dati punti estremi movimento x,y,z
     * @param [in] stayTime Tempo permanenza oscillazione ms
     * @param [in] frequency Frequenza oscillazione Hz
     * @param [in] incStayType Modalità attesa: 0-Ciclo non include tempo attesa; 1-Ciclo include tempo attesa
     * @param [in] stationary Attesa posizione oscillazione: 0-Movimento continuo durante attesa; 1-Posizione stazionaria durante attesa
     * @return  Codice di errore
     */
    public int CustomWeaveSetPara(int id, int pointNum, DescTran[] point, double[] stayTime, double frequency, int incStayType, int stationary)

Ottenimento parametri oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.9-3.8.6

.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene i parametri di oscillazione personalizzati
     * @param [in] id Numero oscillazione personalizzata: 0-2
     * @param [out] pointNum Numero punti oscillazione 0-10
     * @param [out] point Dati punti estremi movimento x,y,z
     * @param [out] stayTime Tempo permanenza oscillazione ms
     * @param [out] frequency Frequenza oscillazione Hz
     * @param [out] incStayType Modalità attesa: 0-Ciclo non include tempo attesa; 1-Ciclo include tempo attesa
     * @param [out] stationary Attesa posizione oscillazione: 0-Movimento continuo durante attesa; 1-Posizione stazionaria durante attesa
     * @return  Codice di errore
     */
    public int CustomWeaveGetPara(int id, int[] pointNum, DescTran[] point, double[] stayTime, double[] frequency, int[] incStayType, int[] stationary)

Esempio codice parametri oscillazione personalizzati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestCustomWeaveSetPara(Robot robot)
    {
        DescTran[] point = new DescTran[10];
        point[0]=new DescTran();
        point[0].x = -3;
        point[0].y = -3;
        point[0].z = 0;

        point[1]=new DescTran();
        point[1].x = -6;
        point[1].y = 0;
        point[1].z = 0;

        point[2]=new DescTran();
        point[2].x = -3;
        point[2].y = 3;
        point[2].z = 0;

        point[3]=new DescTran();
        point[3].x = 0;
        point[3].y = 0;
        point[3].z = 0;
        point[4]=new DescTran(0,0,0);
        point[5]=new DescTran(0,0,0);
        point[6]=new DescTran(0,0,0);
        point[7]=new DescTran(0,0,0);
        point[8]=new DescTran(0,0,0);
        point[9]=new DescTran(0,0,0);

        double[] stayTime =new double[] { 0,0,0,0,0,0,0,0,0,0 };
        int rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0);
        System.out.println("CustomWeaveSetPara rtn is :"+ rtn);
        robot.Sleep(1000);

        int[] pointNum = new int[1];
        double[] frequency=new double[1];
        int[] incStayType=new int[1];
        int[] stationary=new int[1];
        robot.CustomWeaveGetPara(2, pointNum, point, stayTime, frequency, incStayType, stationary);
        System.out.println("pointNum is :"+ pointNum[0]);
        for (int i = 0; i < pointNum[0]; i++)
        {
            System.out.println("point:"+i+", "+ point[i].x+", "+ point[i].y+", "+ point[i].z);
        }
        System.out.println("fre is :"+ frequency[0]+", stay is:"+ incStayType[0]+", "+ stationary[0]);

        robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000,
                6.000000, 5.000000, 50, 100, 100,
                0, 1, 0.000000, 0.000000);

        DescPose desc_p1 =new DescPose(-288.650, 367.807, 288.404, 0.000, -0.001, 0.001 );
        DescPose desc_p2 = new DescPose( -431.714, 367.815, 288.415, 0.001, 0.001, 0.000 );
        DescPose desc_p3 = new DescPose( -348.666, 427.798, 288.404, -0.000, -0.000, 0.001 );
        JointPos j1 = new JointPos( 140.656, -84.560, -91.707, -93.734, 90.000, 50.655 );
        JointPos j2 = new JointPos( 149.873, -98.298, -77.599, -94.103, 90.000, 59.873 );
        JointPos j3 = new JointPos( 139.773, -96.173, -80.014, -93.814, 90.000, 49.772 );

        ExaxisPos epos = new ExaxisPos();
        DescPose offset_pos = new DescPose();

        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100,100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.Circle(j3, desc_p3, 3, 0, 100, 100, epos, j2, desc_p2, 3, 0, 100, 100, epos, 10, -1, offset_pos,0,-1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveC(j3, desc_p3, 3, 0, 100, 100, epos, 0, offset_pos, j2, desc_p2, 3, 0, 100, 100, epos, 0, offset_pos, 10, -1,0);
        robot.WeaveEnd(0);
        robot.MoveJ(j1, desc_p1, 3, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.WeaveStart(0);
        robot.MoveL(j2, desc_p2, 3, 0, 100, 100, 10, -1,epos, 0, 0, offset_pos, 0,0, 100);
        robot.WeaveEnd(0);

        robot.CloseRPC();
    }