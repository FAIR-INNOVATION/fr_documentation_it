Note sulle Aggiornamenti di Versione
=====================================

.. toctree::
   :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Numero Versione**
     - **Data**
     - **Descrizione Aggiornamento**

   * - V3.9.7
     - 2026-06-25
     - | 1. Aggiunto errore di allarme caduta pezzo dalla pinza, codice guasto principale 8, codice guasto secondario 3.
       | 2. Aggiornata la struttura di feedback dello stato del robot: aggiunto stato di rilevamento oggetto al segnale di completamento movimento pinza; aggiunti ai guasti pinza: 2-errore comando, 3-caduta pezzo, altri-codice guasto pinza +3;
       | 3. Aggiornati esempi di codice per il reset dell'output dopo stop/pausa del programma LUA; ottimizzata l'interfaccia di caricamento file lua che ora richiede solo il nome del file lua, non più il percorso.
       | 4. Aggiornati esempi di codice per la calibrazione TCP del sensore fotoelettrico; ottimizzata l'interfaccia di caricamento file che ora richiede solo il nome del file lua, non più il percorso.
       | 5. Aggiornati esempi di codice per l'impostazione della velocità durante l'esecuzione della traiettoria; ottimizzata l'interfaccia di caricamento file traiettoria J che ora richiede solo il nome del file traiettoria J, non più il percorso.
       | 6. Aggiornati esempi di codice per la riproduzione del file traiettoria J del robot; ottimizzata l'interfaccia di caricamento file traiettoria J che ora richiede solo il nome del file traiettoria J, non più il percorso.
       | 7. Aggiornati esempi di codice per la riproduzione traiettoria (look-ahead); ottimizzata l'interfaccia di caricamento file traiettoria J che ora richiede solo il nome del file traiettoria J, non più il percorso.
       | 8. Il parametro nome programma job nell'interfaccia LoadDefaultProgConfig() ora richiede solo il nome del file lua, non più il percorso.
       | 9. Il parametro nome programma job nell'interfaccia ProgramLoad() ora richiede solo il nome del file lua, non più il percorso.
       | 10. Il parametro nome programma job nell'interfaccia GetLoadedProgram() ora richiede solo il nome del file lua, non più il percorso.
       | 11. Aggiornati esempi di codice per le operazioni sui programmi LUA del robot; ottimizzata l'interfaccia di caricamento file che ora richiede solo il nome del file lua, non più il percorso.
       | 12. Aggiunto parametro stato abilitazione mano destra all'interfaccia SetAxleLuaEnableDeviceType();
       | 13. Aggiunto parametro stato abilitazione mano destra all'interfaccia GetAxleLuaEnableDeviceType();
       | 14. Aggiunto parametro stato numero dispositivo abilitato per mano destra all'interfaccia GetAxleLuaEnableDevice();
       | 15. Espanso l'array dei codici funzione pinza a 32 in SetAxleLuaGripperFunc(), aggiunto controllo pinza rotante, ecc.;
       | 16. Espanso l'array dei codici funzione pinza a 32 in GetAxleLuaGripperFunc(), aggiunto stato pinza rotante, ecc.;
       | 17. Corretto errore nel nome dell'interfaccia SetCoderCompenParams();
       | 18. Aggiunta interfaccia SetDexterousHandsMove() per il controllo del movimento della mano destra.
       | 19. Aggiunta interfaccia SetDexterousHandsAct() per il controllo del reset e attivazione della mano destra.
       | 20. Aggiunta interfaccia ClearDexterousHandsError() per la cancellazione degli errori della mano destra.
       | 21. Aggiunta interfaccia SetDexterousHandsFunc() per impostare le funzioni di controllo azione mano destra abilitate.
       | 22. Aggiunta interfaccia GetDexterousHandsFunc() per ottenere le funzioni di controllo azione mano destra abilitate.
       | 23. Aggiunta interfaccia FT_LinInsertion() per inserimento lineare ed esempi di codice per inserimento rotazionale con sensore di forza.
       | 24. Aggiunte interfacce FT_FindSurface(), FT_CalCenterStart(), FT_CalCenterEnd() per il posizionamento superficiale ed esempi di codice correlati.
       | 25. Aggiunte SetWeaveBackCenterConfig(), GetWeaveBackCenterConfig() per impostare e ottenere i parametri del punto zero di ritorno al ciclo al termine della tessitura.
       | 26. Aggiunta interfaccia SetWeaveOffsetRT() per impostare l'offset in tempo reale della tessitura;
       | 27. Aggiunta interfaccia SetSpeedInstant() per impostazione velocità in tempo reale;

   * - V3.9.6
     - 2026-05-26
     - | 1.Aggiornata la struttura di feedback dello stato del robot, aggiunto lo stato del numero del sistema di coordinate degli assi di estensione;
       | 2.Aggiornato il tipo enumerato di configurazione del feedback di stato del robot, aggiunta l'enumerazione di configurazione del numero del sistema di coordinate degli assi di estensione;
       | 3.Aggiunta interfaccia ExtAxisGetParamConfig() per ottenere la configurazione dei parametri degli assi di estensione UDP;
       | 4.Aggiunta interfaccia ServoJV() per il movimento in modalità servo a velocità nello spazio dei giunti del robot;
       | 5.Aggiunta interfaccia ServoMITStart() per l'avvio del controllo MIT dei giunti del robot;
       | 6.Aggiunta interfaccia ServoMITEnd() per la fine del controllo MIT dei giunti del robot;
       | 7.Aggiunta interfaccia ServoMIT() per il controllo MIT dei giunti del robot;
       | 8.Aggiunta interfaccia SetLaserWeldingParam() per la configurazione dei parametri di saldatura laser del robot;
       | 9.Aggiunta interfaccia SetLaserWeldingStartEnd() per impostare l'avvio/arresto della saldatura laser del robot;
       | 10.Aggiunta interfaccia SetLaserWeldingEnable() per abilitare/disabilitare la saldatrice laser;
       | 11.Aggiunta interfaccia ResetLaserWeldingErr() per il ripristino dei guasti della saldatrice laser;
       | 12.Aggiunta interfaccia GetLaserWeldingRunningState() per ottenere lo stato di funzionamento della saldatrice laser;
       | 13.Aggiunta interfaccia GetLaserWeldingErrState() per ottenere lo stato di guasto della saldatrice laser;
       | 14.Aggiunta interfaccia GetLaserWeldingParamTarget() per ottenere i parametri di configurazione della saldatura laser;
       | 15.Aggiunta interfaccia GetLaserWeldingParamActual() per ottenere i parametri di configurazione attualmente attivi della saldatrice laser;
       | 16.Aggiunta interfaccia SetLaserWeldingEnableExtDoNum() per configurare la porta DO di abilitazione IO esteso della saldatrice laser;
       | 17.Aggiunta interfaccia SetLaserWeldingStartExtDoNum() per configurare la porta DO di avvio IO esteso della saldatrice laser;
       | 18.Aggiunta interfaccia SetLaserWeldingErrResetExtDoNum() per configurare la porta DO di ripristino guasto IO esteso della saldatrice laser;
       | 19.Aggiunta interfaccia SetLaserWeldingRunningStateExtDiNum() per configurare la porta DI dello stato di funzionamento (stato laser acceso) IO esteso della saldatrice laser;
       | 20.Aggiunta interfaccia SetLaserWeldingErrStateExtDiNum() per configurare la porta DI dello stato di guasto IO esteso della saldatrice laser.

   * - V3.9.5
     - 2026-04-24
     - | 1.Interfaccia GetRobotRealTimeState() modifica il meccanismo interno per ottenere l'ultimo frame dei dati di stato in tempo reale del robot, senza modifiche alle caratteristiche esterne;
       | 2.Interfaccia SetTrajectoryJSpeed() aggiunge le modalità di riduzione della velocità e commutazione diretta;
       | 3.Interfaccia GetSystemClock() aggiunge feedback del codice di errore e descrizione della funzione;
       | 4.Interfaccia FieldBusSlaveWriteAO() modifica il tipo di valore scritto in double, dove AO0~AO15 sono di tipo intero e AO16~AO31 sono in virgola mobile;
       | 5.Tipo struttura di feedback di stato del robot aggiornato, ROBOT_STATE_PKG cambiato da struct a class;
       | 6.Aggiunto tipo enumerato per la configurazione del feedback di stato del robot;
       | 7.Aggiunto esempio di codice per impostare la velocità del robot durante l'esecuzione della traiettoria;
       | 8.Aggiunta interfaccia SetRobotRealtimeStateConfig() per configurare il feedback di stato CNDE del robot;
       | 9.Aggiunta interfaccia AddRobotRealtimeState() per aggiungere uno stato del robot alla configurazione di stato CNDE;
       | 10.Aggiunta interfaccia DeleteRobotRealtimeState() per eliminare uno stato del robot dalla configurazione di stato CNDE;
       | 11.Aggiunta interfaccia SetRobotRealtimeStatePeriod() per impostare il periodo di feedback di stato CNDE;
       | 12.Aggiunta interfaccia GetRobotRealtimeStateConfig() per ottenere tutti gli insiemi di stati e il periodo dell'attuale feedback di stato CNDE;
       | 13.Le seguenti interfacce aggiungono logica di blocco durante lo stato di disconnessione e riconnessione: GetSafetyCode, GetAI, GetToolAI, GetAxlePointRecordBtnState, GetToolDO, GetDO, GetActualJointPosDegree, GetActualJointSpeedsDegree, GetActualJointAccDegree, GetTargetTCPCompositeSpeed, GetActualTCPCompositeSpeed, GetTargetTCPSpeed, GetActualTCPSpeed, GetActualTCPPose, GetActualTCPNum, GetActualWObjNum, GetActualToolFlangePose, GetJointTorques, GetRobotMotionDone, GetRobotErrorCode, GetError, GetMotionQueueLength, GetProgramState, GetGripperActivateStatus, GetGripperCurPosition, GetGripperCurSpeed, GetGripperCurCurrent, GetGripperVoltage, GetGripperTemp, FT_GetForceTorqueRCS, FT_GetForceTorqueOrigin, FT_Control, GetRobotEmergencyStopState, GetSDKComState, GetSafetyStopState, LuaUpload, LuaDownLoad, ForceSensorAutoComputeLoad, AxleLuaUpload, GetGripperRotNum, GetGripperRotSpeed, GetGripperRotTorque.

   * - V3.9.4
     - 2026-03-25
     - | 1.Interfaccia ServoJTStart() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 2.Interfaccia ServoJTEnd() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 3.Interfaccia ServoJT() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 4.Interfaccia ServoMoveStart() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 5.Interfaccia ServoMoveEnd() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 6.Interfaccia ServoJ() aggiunge parametro di selezione del tipo di comunicazione, supporta comunicazione XMLRPC/UDP;
       | 7.Interfaccia SetWeldMachineCtrlMode() aggiunge parametro di selezione della modalità di controllo;
       | 8.Interfaccia ExtDevGetUDPComParam() aggiunge capacità di ottenere parametri di comunicazione UDP: se riconnettersi automaticamente dopo il riavvio del box di controllo;
       | 9.Aggiunge interfaccia SetAxleGenComEnable() per abilitare la funzione di trasmissione trasparente generale dell'end-effector;
       | 10.Aggiunge interfaccia SndRcvAxleGenComCmdData() per l'end-effector per inviare dati non periodici e attendere risposta;
       | 11.Aggiunge interfaccia SetRobotStopOnComDisc() per fermare il funzionamento del robot quando la comunicazione della porta è disconnessa;
       | 12.Aggiunge interfaccia GetRobotStopOnComDisc() per ottenere i parametri per fermare il funzionamento del robot quando la comunicazione della porta è disconnessa;
       | 13.Aggiunge interfaccia SetDIConfig() per impostare le funzioni delle porte CI configurabili del box di controllo;
       | 14.Aggiunge interfaccia GetDIConfig() per ottenere le funzioni delle porte CI configurabili del box di controllo;
       | 15.Aggiunge interfaccia SetDOConfig() per impostare le funzioni delle porte CO configurabili del box di controllo;
       | 16.Aggiunge interfaccia GetDOConfig() per ottenere le funzioni delle porte CO configurabili del box di controllo;
       | 17.Aggiunge interfaccia SetToolDIConfig() per impostare le funzioni delle porte End-CI configurabili dell'end-effector;
       | 18.Aggiunge interfaccia GetToolDIConfig() per ottenere le funzioni delle porte End-CI configurabili dell'end-effector;
       | 19.Aggiunge interfaccia SetDIConfigLevel() per impostare lo stato attivo delle porte CI configurabili del box di controllo;
       | 20.Aggiunge interfaccia GetDIConfigLevel() per ottenere lo stato attivo delle porte CI configurabili del box di controllo;
       | 21.Aggiunge interfaccia SetDOConfigLevel() per impostare lo stato attivo delle porte CO configurabili del box di controllo;
       | 22.Aggiunge interfaccia GetDOConfigLevel() per ottenere lo stato attivo delle porte CO configurabili del box di controllo;
       | 23.Aggiunge interfaccia SetToolDIConfigLevel() per impostare lo stato attivo delle porte CI configurabili dell'end-effector;
       | 24.Aggiunge interfaccia GetToolDIConfigLevel() per ottenere lo stato attivo delle porte CI configurabili dell'end-effector;
       | 25.Aggiunge interfaccia SetStandardDILevel() per impostare lo stato attivo delle porte DI standard del box di controllo;
       | 26.Aggiunge interfaccia GetStandardDILevel() per ottenere lo stato attivo delle porte DI standard del box di controllo;
       | 27.Aggiunge interfaccia SetStandardDOLevel() per impostare lo stato attivo delle porte DO standard del box di controllo;
       | 28.Aggiunge interfaccia GetStandardDOLevel() per ottenere lo stato attivo delle porte DO standard del box di controllo;
       | 29.Aggiunge interfaccia SetExAxisCmdDoneTimeUDP() per impostare il tempo di completamento del posizionamento degli assi di estensione;
       | 30.Aggiunge interfaccia OpenLuaDownload() per scaricare file Lua di protocollo aperto;
       | 31.Aggiunge interfaccia OpenLuaDelete() per eliminare file Lua di protocollo aperto;
       | 32.Aggiunge interfaccia AllOpenLuaDelete() per eliminare file Lua di protocollo aperto;
       | 33.Aggiunge interfaccia SendUDPFrameUDP() per inviare frame di istruzioni;
       | 34.Aggiunge interfaccia SetCmdRpyCallback() per impostare la funzione di callback per i risultati di esecuzione delle istruzioni inviate da SDK tramite UDP;
       | 35.Aggiunge interfaccia SetVelReducePara() per impostare i parametri di velocità di sicurezza;
       | 36.Aggiunge interfaccia OriginPointWeaveStart() per avviare l'oscillazione a punto fisso;
       | 37.Aggiunge interfaccia OriginPointWeaveEnd() per terminare l'oscillazione a punto fisso;
       | 38.Aggiunge interfaccia SetUserLEDColor() per impostare il colore LED personalizzato dell'end-effector del robot;
       | 39.Aggiunge interfaccia MoveToTPDStart() per spostarsi al punto di inizio della registrazione della traiettoria TPD;  

   * - V3.9.3
     - 2026-02-11
     - | 1.Interfaccia ServoCart() ha aggiunto parametri asse esteso
       | 2.Interfaccia SetOutputResetCtlBoxDO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 3.Interfaccia SetOutputResetCtlBoxAO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 4.Interfaccia SetOutputResetAxleDO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 5.Interfaccia SetOutputResetAxleAO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 6.Interfaccia SetOutputResetExtDO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 7.Interfaccia SetOutputResetExtAO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 8.Interfaccia SetOutputResetSmartToolDO() ha aggiunto parametro per ricaricare stato DO pre-reset dopo ripresa pausa
       | 9.Aggiunta interfaccia GetInverseKinExaxis() per soluzione cinematica inversa con posizione asse esteso

* - V3.9.2
     - 2026-01-26
     - | 1. Aggiunto un parametro di strategia di elaborazione per forza/coppia non rilevata all'interfaccia FT_RotInsertion()
       | 2. Aggiunti parametri relativi al tracciamento a punto fisso del robot all'interfaccia LaserSensorRecordandReplay()
       | 3. Aggiunta l'interfaccia MoveStationary()
       | 4. Aggiunta l'interfaccia TCPComputeRPY()
       | 5. Aggiunta l'interfaccia TCPComputeXYZ()
       | 6. Aggiunta l'interfaccia TCPRecordFlangePosStart()
       | 7. Aggiunta l'interfaccia TCPRecordFlangePosEnd()
       | 8. Aggiunta l'interfaccia TCPGetRecordFlangePos()
       | 9. Aggiunta l'interfaccia PhotoelectricSensorTCPCalibration()

   * - V3.9.1
     - 2025-12-25
     - | 1. Aggiunto il parametro fattore di scala velocità oacc / parametro accelerazione fisica all'interfaccia MoveL();
       | 2. Aggiunto il parametro fattore di scala velocità oacc / parametro accelerazione fisica all'interfaccia MoveC();
       | 3. Ottimizzate le descrizioni dei parametri per velocità fisica e accelerazione fisica nell'interfaccia Circle();
       | 4. Aggiunta funzione sovraccaricata FT_Control() con parametri soglie di attivazione rx, ry e coefficienti di regolazione della coppia;
       | 5. Aggiunta interfaccia SerCoderCompenParams();

   * - V3.9.0
     - 2025-11-26
     - | 1. Interfaccia JointSensitivityCalibration() aggiunge restituzione linearità giunti j1~j6
       | 2. Aggiunta interfaccia JointHysteresisError()
       | 3. Aggiunta interfaccia JointRepeatability()
       | 4. Aggiunta interfaccia SetAdmittanceParams()
       | 5. Aggiunta interfaccia MoveToIntersectLineStart()
       | 6. Aggiunta interfaccia MoveIntersectLine()
       
   * - V3.8.7
     - 2025-10-21
     - | 1. FT_Control() aggiunge parametri massa e smorzamento
       | 2. Aggiunta interfaccia JointSensitivityCalibration()
       | 3. Aggiunta interfaccia JointSensitivityCollect()
       | 4. Aggiunta interfaccia MotionQueueClear()
       | 5. Aggiunta interfaccia GetSlavePortErrCounter()
       | 6. Aggiunta interfaccia SlavePortErrCounterClear()
       | 7. Aggiunta interfaccia SetVelFeedForwardRatio()
       | 8. Aggiunta interfaccia GetVelFeedForwardRatio()
       | 9. Aggiunta interfaccia RobotMCULogCollect()
       | 10. Struttura stato aggiunge conteggio comandi ServoJ e dati ultima posizione target comando
       | 11. Nuova struttura parametri spirale SpiralParam aggiunge modalità parametri velocità accelerazione

   * - V3.8.6
     - 2025-09-19
     - | 1. Interfaccia SetLoadCoord() aggiunge parametro numero carico
       | 2. Aggiunta interfaccia LaserTrackingLaserOnOff()
       | 3. Aggiunta interfaccia LaserTrackingTrackOnOff()
       | 4. Aggiunta interfaccia LaserTrackingSearchStart_xyz()
       | 5. Aggiunta interfaccia LaserTrackingSearchStart_point()
       | 6. Aggiunta interfaccia LaserTrackingSearchStop()
       | 7. Aggiunta interfaccia LaserTrackingSensorConfig()
       | 8. Aggiunta interfaccia LaserTrackingSensorSamplePeriod()
       | 9. Aggiunta interfaccia LoadPosSensorDriver()
       | 10. Aggiunta interfaccia UnLoadPosSensorDriver()
       | 11. Aggiunta interfaccia LaserSensorRecord1()
       | 12. Aggiunta interfaccia LaserSensorReplay()
       | 13. Aggiunta interfaccia MoveLTR()
       | 14. Aggiunta interfaccia LaserSensorRecordandReplay()
       | 15. Aggiunta interfaccia MoveToLaserRecordStart()
       | 16. Aggiunta interfaccia MoveToLaserRecordEnd()
       | 17. Aggiunta interfaccia MoveToLaserSeamPos()
       | 18. Aggiunta interfaccia GetLaserSeamPos()
       | 19. Aggiunta interfaccia ImpedanceControlStartStop()
       | 20. Aggiunta interfaccia GetToolCoordWithID()
       | 21. Aggiunta interfaccia GetWObjCoordWithID()
       | 22. Aggiunta interfaccia GetExToolCoordWithID()
       | 23. Aggiunta interfaccia GetExAxisCoordWithID()
       | 24. Aggiunta interfaccia GetTargetPayloadWithID()
       | 25. Aggiunta interfaccia GetExAxisCoordWithID()
       | 26. Aggiunta interfaccia GetCurWObjCoord()
       | 27. Aggiunta interfaccia GetCurExToolCoord()
       | 28. Aggiunta interfaccia GetCurExToolCoord()
       | 29. Aggiunta interfaccia KernelUpgrade()
       | 30. Aggiunta interfaccia GetKernelUpgradeResult()
       | 31. Aggiunta interfaccia CustomWeaveSetPara()
       | 32. Aggiunta interfaccia CustomWeaveGetPara()
       | 33. Struttura stato aggiunge dati sistema coordinate utensile, pezzo, utensile esterno, assi estesi e massa carico, centro di massa

   * - V3.8.5
     - 2025-08-20
     - | 1. Aggiunta interfaccia OpenLuaUpload()
       | 2. Aggiunta interfaccia GetFieldBusConfig()
       | 3. Aggiunta interfaccia FieldBusSlaveWriteDO()
       | 4. Aggiunta interfaccia FieldBusSlaveWriteAO()
       | 5. Aggiunta interfaccia FieldBusSlaveReadDI()
       | 6. Aggiunta interfaccia FieldBusSlaveReadAI()
       | 7. Aggiunta interfaccia FieldBusSlaveWaitDI()
       | 8. Aggiunta interfaccia FieldBusSlaveWaitAI()
       | 9. Aggiunta interfaccia SetSuckerCtrl()
       | 10. Aggiunta interfaccia GetSuckerState()
       | 11. Aggiunta interfaccia WaitSuckerState()
       | 12. Aggiunta modalità parametri velocità accelerazione velAccParamMode per interfaccia MoveL()
       | 13. Aggiunta overload funzione 1 per interfaccia MoveL()
       | 14. Aggiunta overload funzione 2 per interfaccia MoveL()
       | 15. Aggiunta modalità parametri velocità accelerazione velAccParamMode per interfaccia MoveC()
       | 16. Aggiunta overload funzione 1 per interfaccia MoveC()
       | 17. Aggiunta modalità parametri velocità accelerazione velAccParamMode per interfaccia Circle()
       | 18. Aggiunta overload funzione 1 per interfaccia Circle()
       | 19. Aggiunta interfaccia SetExAxisRobotPlan()

   * - V3.8.4
     - 2025-07-17
     - | 1. Interfaccia ExtAxisMove() aggiunge parametro levigatura blend
       | 2. Aggiunta interfaccia SetFocusCalibPoint()
       | 3. Aggiunta interfaccia ComputeFocusCalib()
       | 4. Aggiunta interfaccia SetFocusPosition()
       | 5. Aggiunta interfaccia FocusStart()
       | 6. Aggiunta interfaccia FocusEnd()
       | 7. Aggiunta interfaccia SetEncoderUpgrade()
       | 8. Aggiunta interfaccia SetJointFirmwareUpgrade()
       | 9. Aggiunta interfaccia SetCtrlFirmwareUpgrade()
       | 10. Aggiunta interfaccia SetEndFirmwareUpgrade()
       | 11. Aggiunta interfaccia JointAllParamUpgrade()
       
   * - V3.8.3
     - 2025-06-24
     - | 1. Interfaccia Circle() aggiunge parametri percentuale accelerazione e raggio levigatura
       | 2. Interfaccia EndForceDragControl() aggiunge parametro flag rilevamento collisione robot durante trascinamento assistito
       | 3. Interfaccia ServoJ() aggiunge parametro ID comando
       | 4. Aggiunta interfaccia SetSSHScpCmd()
       | 5. Aggiunta interfaccia SetWideBoxTempFanMonitorParam()
       | 6. Aggiunta interfaccia GetWideBoxTempFanMonitorParam()
       | 7. Struttura stato aggiunge dati stato temperatura centralina e corrente ventole
              
   * - V3.8.2
     - 2025-06-13
     - | 1. Interfaccia WeaveSetPara() aggiunge parametro angolo di rollio direzione oscillazione (rotazione attorno all'asse X oscillazione)
       | 2. Interfaccia WeaveChangeStart() aggiunge parametri numero oscillazione, velocità inizio saldatura, velocità fine saldatura
       | 3. Interfaccia ExtDevSetUDPComParam() aggiunge parametro connessione automatica dopo riavvio alimentazione
       | 4. Interfaccia SetCollisionDetectionMethod() aggiunge selezione metodo soglia livello collisione
       | 5. Interfaccia PtpFIRPlanningStart() aggiunge valore picco jerk giunto unificato
       | 6. Aggiunta interfaccia WeldingSetVoltageGradualChangeStart()
       | 7. Aggiunta interfaccia WeldingSetVoltageGradualChangeEnd()
       | 8. Aggiunta interfaccia WeldingSetCurrentGradualChangeStart()
       | 9. Aggiunta interfaccia WeldingSetCurrentGradualChangeEnd()
       | 10. Aggiunta interfaccia ArcWeldTraceAIChannelCurrent()
       | 11. Aggiunta interfaccia ArcWeldTraceAIChannelVoltage()
       | 12. Aggiunta interfaccia ArcWeldTraceCurrentPara()
       | 13. Aggiunta interfaccia ArcWeldTraceVoltagePara()
       | 14. Aggiunta interfaccia GetSmarttoolBtnState()
       | 15. Aggiunta interfaccia ExtAxisGetCoord()
                     
   * - V3.8.1
     - 2025-04-24
     - | 1. Interfaccia ConveyorSetParam() aggiunge parametri tipo movimento tracciamento, distanza inizio tracciamento, distanza fine tracciamento
       | 2. Aggiunta interfaccia AccSmoothStart()
       | 3. Aggiunta interfaccia AccSmoothEnd()
       | 4. Aggiunta interfaccia RbLogDownload()
       | 5. Aggiunta interfaccia AllDataSourceDownload()
       | 6. Aggiunta interfaccia DataPackageDownload()
       | 7. Aggiunta interfaccia GetRobotSN()
       | 8. Aggiunta interfaccia ShutDownRobotOS()
       | 9. Aggiunta interfaccia ConveyorComDetect()
       | 10. Aggiunta interfaccia ConveyorComDetectTrigger()
                     
   * - V3.8.0
     - 2025-02-12
     - | 1. Interfaccia EndForceDragControl() aggiunge parametro evitamento punti singolari
       | 2. Interfaccia ArcWeldTraceControl() aggiunge parametri offset
       | 3. Aggiunta interfaccia WeaveChangeStart()
       | 4. Aggiunta interfaccia WeaveChangeEnd()
       | 5. Aggiunta interfaccia LoadTrajectoryLA()
       | 6. Aggiunta interfaccia MoveTrajectoryLA()
       | 7. Aggiunta interfaccia CustomCollisionDetectionStart()
       | 8. Aggiunta interfaccia CustomCollisionDetectionEnd()