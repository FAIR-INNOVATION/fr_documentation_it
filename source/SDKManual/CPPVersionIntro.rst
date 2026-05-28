Note di Aggiornamento Versione
==================================

.. toctree:: 
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Numero Versione**
     - **Data**
     - **Descrizione Aggiornamento**

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
     - | 1.Interfaccia SetTrajectoryJSpeed() aggiunge le modalità di riduzione della velocità e commutazione diretta;
       | 2.Interfaccia FieldBusSlaveWriteAO() modifica il tipo di valore scritto in double, dove AO0~AO15 sono di tipo intero e AO16~AO31 sono in virgola mobile;
       | 3.Interfaccia FieldBusSlaveReadAI() modifica il tipo di valore letto in double, dove AI0~AI15 sono di tipo intero e AI16~AI31 sono in virgola mobile;
       | 4.Tipo struttura di feedback di stato del robot aggiornato;
       | 5.Aggiunto tipo enumerato per la configurazione del feedback di stato del robot;
       | 6.Aggiunta interfaccia SetRobotRealtimeStateConfig() per configurare il feedback di stato CNDE del robot;
       | 7.Aggiunta interfaccia AddRobotRealtimeState() per aggiungere uno stato del robot alla configurazione di stato CNDE;
       | 8.Aggiunta interfaccia DeleteRobotRealtimeState() per eliminare uno stato del robot dalla configurazione di stato CNDE;
       | 9.Aggiunta interfaccia SetRobotRealtimeStatePeriod() per impostare il periodo di feedback di stato CNDE;
       | 10.Aggiunta interfaccia GetRobotRealtimeStateConfig() per ottenere tutti gli insiemi di stati e il periodo dell'attuale feedback di stato CNDE.

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
     - | 1. Interfaccia JointSensitivityCalibration() aggiunge ritorno linearità giunti j1~j6
       | 2. Aggiunta interfaccia JointHysteresisError()
       | 3. Aggiunta interfaccia JointRepeatability()
       | 4. Aggiunta interfaccia SetAdmittanceParams()
       | 5. Aggiunta interfaccia MoveToIntersectLineStart()
       | 6. Aggiunta interfaccia MoveIntersectLine()

   * - V3.8.7
     - 2025-10-21
     - | 1. FT_Control() aggiunge interfaccia parametri massa e smorzamento
       | 2. Aggiunta interfaccia JointSensitivityCalibration()
       | 3. Aggiunta interfaccia JointSensitivityCollect()
       | 4. Aggiunta interfaccia MotionQueueClear()
       | 5. Aggiunta interfaccia GetSlavePortErrCounter()
       | 6. Aggiunta interfaccia SlavePortErrCounterClear()
       | 7. Aggiunta interfaccia SetVelFeedForwardRatio()
       | 8. Aggiunta interfaccia GetVelFeedForwardRatio()
       | 9. Aggiunta interfaccia RobotMCULogCollect()
       | 10. Struttura stato aggiunge conteggio istruzioni ServoJ e dati posizione target ultima istruzione
       | 11. Nuova struttura parametri elica SpiralParam aggiunge modalità parametri velocità accelerazione

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
       | 33. Struttura stato aggiunge dati sistema coordinate utensile, pezzo, utensile esterno, asse esteso e massa carico, centro di massa

   * - V3.8.5
     - 2025-08-20
     - | 1. Istruzioni MoveL(), MoveC(), Circle() aggiungono parametro velAccParamMode
       | 2. Aggiunte interfacce calcolo cinematico diretto automatico per MoveJ(), SplinePTP(), ExtAxisSyncMoveJ()
       | 3. LoadTrajectoryLA() aggiunge parametro attivazione interruttore lookahead velocità costante
       | 4. Aggiunte interfacce calcolo cinematico inverso automatico per MoveL(), MoveC(), Circle(), NewSplinePoint(), NewSpiral(), ExtAxisSyncMoveL(), ExtAxisSyncMoveC()
       | 5. Aggiunte interfacce controllo ventosa SetSuckerCtrl(), GetSuckerState(), WaitSuckerState(), ecc., interfaccia strategia movimento sincrono SetExAxisRobotPlan()
       | 6. Aggiunte istruzioni controllo modalità slave robot OpenLuaUpload(), GetFieldBusConfig(), FieldBusSlaveWriteDO(), FieldBusSlaveWriteAO(), FieldBusSlaveReadDI(), FieldBusSlaveReadAI(), FieldBusSlaveWaitDI(), FieldBusSlaveWaitAI(), ecc.

   * - V3.8.4
     - 2025-07-17
     - | 1. Interfaccia ExtAxisMove() aggiunge parametro smoothing blend
       | 2. Aggiunta interfaccia SetFocusCalibPoint()
       | 3. Aggiunta interfaccia ComputeFocusCalib()
       | 4. Aggiunta interfaccia SetFocusPosition()
       | 5. Aggiunta interfaccia FocusStart()
       | 6. Aggiunta interfaccia FocusEnd()
       | 7. Aggiunta interfaccia SetJointFirmwareUpgrade()
       | 8. Aggiunta interfaccia SetCtrlFirmwareUpgrade()
       | 9. Aggiunta interfaccia SetEndFirmwareUpgrade()
       | 10. Aggiunta interfaccia JointAllParamUpgrade()

   * - V3.8.3
     - 2025-06-24
     - | 1. Interfaccia Circle() aggiunge parametri percentuale accelerazione e raggio smoothing
       | 2. Interfaccia EndForceDragControl() aggiunge parametro flag rilevamento collisione robot durante trascinamento assistito
       | 3. Interfaccia ServoJ() aggiunge parametro ID istruzione
       | 4. Aggiunta interfaccia SetWideBoxTempFanMonitorParam()
       | 5. Aggiunta interfaccia GetWideBoxTempFanMonitorParam()
       | 6. Struttura stato aggiunge dati stato temperatura control box e corrente ventola

   * - V3.8.2
     - 2025-06-13
     - | 1. Interfaccia WeaveSetPara() aggiunge parametro angolo rollio direzione oscillazione (deviazione attorno asse X oscillazione)
       | 2. Interfaccia WeaveChangeStart() aggiunge parametri numero oscillazione, velocità inizio saldatura, velocità fine saldatura
       | 3. Interfaccia ExtDevSetUDPComParam() aggiunge parametro stabilire automaticamente connessione dopo riavvio da spegnimento
       | 4. SetCollisionDetectionMethod() aggiunge selezione modalità soglia livello collisione
       | 5. PtpFIRPlanningStart() aggiunge valore estremo jerk giunti unificato
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
       | 2. Interfaccia ArcWeldTraceControl() aggiunge parametro offset
       | 3. Aggiunta interfaccia WeaveChangeStart()
       | 4. Aggiunta interfaccia WeaveChangeEnd()
       | 5. Aggiunta interfaccia LoadTrajectoryLA()
       | 6. Aggiunta interfaccia MoveTrajectoryLA()
       | 7. Aggiunta interfaccia CustomCollisionDetectionStart()
       | 8. Aggiunta interfaccia CustomCollisionDetectionEnd()