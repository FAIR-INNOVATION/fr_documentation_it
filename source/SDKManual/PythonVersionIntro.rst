Note Aggiornamento Versione
======================================

.. toctree:: 
    :maxdepth: 5

.. list-table::
   :widths: 10 10 30
   :header-rows: 0
   :align: center

   * - **Numero Versione**
     - **Data**
     - **Descrizione Aggiornamento**

   * - V3.9.9
     - 2026-09-01
     - | 1. Aggiornata l'interfaccia GetGripperMotionDone() per ottenere lo stato di movimento della pinza, aggiornata la definizione e l'ambito di utilizzo dei parametri di output dello stato della pinza;
       | 2. Modificata GetInverseKinExaxis(), l'interfaccia di soluzione cinematica inversa che include le posizioni degli assi estesi, aggiunti parametri di configurazione dei giunti con valore predefinito -1 che fa riferimento alla configurazione corrente dei giunti;
       | 3. Modificate le interfacce di controllo di forza FT_SpiralSearch(), FT_LinInsertion() e FT_FindSurface() per aggiungere parametri di strategia di gestione per quando non viene rilevata forza/coppia;
       | 4. Modificate SetDIConfig(), GetDIConfig(), SetDOConfig(), GetDOConfig() CIO del box di controllo del robot;
       | 5. Descrizioni dei parametri dell'interfaccia di configurazione delle funzioni aggiornate, aggiornati i nomi delle funzioni e i codici funzione appena aggiunti; aggiunta l'interfaccia GetSafetyParamsCheckSum() per ottenere il checksum dei parametri di configurazione di sicurezza;
       | 6. Modificati gli esempi di codice di controllo di base del robot, aggiunti esempi di codice per il passaggio alla modalità manuale ad alta velocità;
       | 7. Aggiunta l'interfaccia di verifica della password dell'operazione di sicurezza SafetyOPPasswordCheck();
       | 8. Aggiunta l'interfaccia GripperWaitMotionDone() per attendere lo stato di movimento della pinza, supporta impostazioni di timeout e strategia (applicabile solo al protocollo aperto dell'end-effector);
       | 9. Aggiunta l'interfaccia SetRobottime() per sincronizzare l'ora di sistema con il robot;
       | 10. Aggiunta l'interfaccia ServoJ() per il movimento in modalità servo nello spazio dei giunti, supporta l'inserimento di più punti in una volta;
       | 11. Aggiunti esempi di codice per la riproduzione della registrazione laser + tessitura regolare;
       | 12. Aggiunti esempi di codice per la riproduzione della registrazione laser + movimento asincrono degli assi estesi + tessitura a punti fissi;
       | 13. Aggiunta l'interfaccia di ricerca a spirale FT_SpiralSearch();
       | 14. Aggiunta l'interfaccia HiSpeedManualSwitch() per il passaggio alla modalità manuale ad alta velocità;
       | 15. Aggiunta l'interfaccia SetSafetyDIConfig() per la configurazione della funzione CI a doppio canale di sicurezza;
       | 16. Aggiunta l'interfaccia SetSafetyDOConfig() per la configurazione della funzione CO a doppio canale di sicurezza;
       | 17. Aggiunti esempi di verifica di impostazione-lettura-cancellazione della configurazione delle funzioni CI/CO a doppio canale di sicurezza.

   * - V3.9.8
     - 2026-07-27
     - | 1. Aggiornata la struttura di feedback dello stato del robot per includere lo stato di esecuzione del programma LUA corrente del robot: 0 - programma non in esecuzione; 1 - programma in esecuzione (incluso programma in pausa);
       | 2. Aggiornate le descrizioni dei parametri per le interfacce SetExToolCoord() e SetExToolList() per l'impostazione del sistema di coordinate dell'utensile esterno e dell'elenco dei sistemi di coordinate degli utensili. I numeri dei sistemi di coordinate degli utensili esterni sono stati aggiornati a 20-39. Aggiornati gli esempi di codice per le operazioni sui sistemi di coordinate degli utensili esterni.
       | 3. Aggiunta la possibilità di recuperare i parametri del tipo di utensile, della posizione di installazione, dell'ID utensile e del numero di carico all'interfaccia GetToolCoordWithID() per il recupero dei parametri del sistema di coordinate dell'utensile.
       | 4. Aggiunta la possibilità di recuperare i parametri del sistema di coordinate di riferimento all'interfaccia GetWObjCoordWithID() per il recupero dei parametri del sistema di coordinate del pezzo.
       | 5. Aggiunta la possibilità di recuperare i parametri della posa del sistema di coordinate del pezzo montato all'estremità del robot all'interfaccia GetExToolCoordWithID() per il recupero dei parametri del sistema di coordinate dell'utensile esterno.
       | 6. Aggiunta la possibilità di recuperare il numero dell'asse esteso e i parametri del flag di calibrazione all'interfaccia GetExAxisCoordWithID() per il recupero dei parametri del sistema di coordinate dell'asse esteso.
       | 7. Aggiunte le impostazioni dei parametri di velocità di sicurezza dei giunti del robot all'interfaccia SetVelReducePara() per l'impostazione della velocità di sicurezza del robot.
       | 8. Aggiunto un esempio di acquisizione della modalità di controllo della saldatrice all'esempio di codice di configurazione dei parametri di saldatura.
       | 9. Aggiunti esempi di codice per il recupero delle configurazioni delle funzioni DI estese e DO estese all'esempio di codice di configurazione dei segnali di saldatura IO estesi.
       | 10. Aggiunto un nuovo esempio di codice per l'impostazione della velocità di sicurezza dei giunti del robot;
       | 11. Aggiunta una nuova interfaccia WaitStationaryMotionDone() per attendere il completamento del movimento a vuoto in posizione;
       | 12. Aggiunta una nuova interfaccia SetStationaryTrackPara() per la configurazione dei parametri di tracciamento in posizione del nastro trasportatore, insieme a un esempio di codice per il tracciamento in posizione del nastro trasportatore;
       | 13. Aggiunte nuove interfacce WorkPieceTrsfStart() e WorkPieceTrsfEnd() per l'avvio e la fine della trasformazione del sistema di coordinate del pezzo, insieme a un esempio di codice per la trasformazione del sistema di coordinate del pezzo.
       | 14. Aggiunta l'interfaccia GetWeldMachineCtrlMode() per il recupero della modalità di controllo della saldatrice.
       | 15. Aggiunte le interfacce GetExtDIConfig() e GetExtDOConfig() per il recupero delle configurazioni delle funzioni DI estese e DO estese.

   * - V3.9.7
     - 2026-06-25
     - | 1. I parametri di PhotoelectricSensorTCPCalibration() ora possono adattarsi a nomi di file senza percorso;
       | 2. I parametri di LoadTrajectoryJ() ora possono adattarsi a nomi di file senza percorso;
       | 3. I parametri di LoadTrajectoryLA() ora possono adattarsi a nomi di file senza percorso;
       | 4. I parametri di LoadDefaultProgConfig() ora possono adattarsi a nomi di file senza percorso;
       | 5. I parametri di ProgramLoad() ora possono adattarsi a nomi di file senza percorso;
       | 6. Aggiunto parametro stato abilitazione mano destra all'interfaccia SetAxleLuaEnableDeviceType();
       | 7. Aggiunto parametro stato abilitazione mano destra all'interfaccia GetAxleLuaEnableDeviceType();
       | 8. Modificate le interfacce per ottenere i tipi di abilitazione dei dispositivi dell'end-effector attualmente configurati e il controllo azione pinza;
       | 9. Aggiunti abilitazione e codici funzione per la mano destra;
       | 10. Aggiunta interfaccia SetDexterousHandsMove() per il controllo del movimento della mano destra;
       | 11. Aggiunta interfaccia SetDexterousHandsAct() per il controllo del reset e attivazione della mano destra;
       | 12. Aggiunta interfaccia ClearDexterousHandsError() per la cancellazione degli errori della mano destra;
       | 13. Aggiunta interfaccia SetDexterousHandsFunc() per impostare le funzioni di controllo azione mano destra abilitate;
       | 14. Aggiunta interfaccia GetDexterousHandsFunc() per ottenere le funzioni di controllo azione mano destra abilitate;
       | 15. Aggiunte interfacce per impostare e ottenere i parametri del punto zero di ritorno al ciclo al termine della tessitura;
       | 16. Aggiunta interfaccia SetWeaveOffsetRT() per impostare l'offset in tempo reale della tessitura e interfaccia SetSpeedInstant() per impostazione velocità in tempo reale.

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
       | 5.Aggiunto tipo enumerato per la configurazione del feedback di stato del robot; aggiunta interfaccia SetRobotRealtimeStateConfig() per configurare il feedback di stato CNDE del robot;
       | 6.Aggiunta interfaccia AddRobotRealtimeState() per aggiungere uno stato del robot alla configurazione di stato CNDE;
       | 7.Aggiunta interfaccia DeleteRobotRealtimeState() per eliminare uno stato del robot dalla configurazione di stato CNDE;
       | 8.Aggiunta interfaccia SetRobotRealtimeStatePeriod() per impostare il periodo di feedback di stato CNDE;
       | 9.Aggiunta interfaccia GetRobotRealtimeStateConfig() per ottenere tutti gli insiemi di stati e il periodo dell'attuale feedback di stato CNDE.

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
       | 30.Aggiunge interfaccia SendUDPFrameUDP() per inviare frame di istruzioni;
       | 31.Aggiunge interfaccia SetUDPCmdRpyCallback() per impostare la funzione di callback per i risultati di esecuzione delle istruzioni inviate da SDK tramite UDP;
       | 32.Aggiunge interfaccia SetVelReducePara() per impostare i parametri di velocità di sicurezza;
       | 33.Aggiunge interfaccia OriginPointWeaveStart() per avviare l'oscillazione a punto fisso;
       | 34.Aggiunge interfaccia OriginPointWeaveEnd() per terminare l'oscillazione a punto fisso;
       | 35.Aggiunge interfaccia SetUserLEDColor() per impostare il colore LED personalizzato dell'end-effector del robot;
       | 36.Aggiunge interfaccia MoveToTPDStart() per spostarsi al punto di inizio della registrazione della traiettoria TPD;
       | 37.Aggiunge interfaccia OpenLuaDownload() per scaricare file Lua di protocollo aperto;
       | 38.Aggiunge interfaccia OpenLuaDelete() per eliminare file Lua di protocollo aperto;
       | 39.Aggiunge interfaccia AllOpenLuaDelete() per eliminare file Lua di protocollo aperto;   

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
     - | 1.Interfaccia JointSensitivityCalibration() aggiunge ritorno linearità giunti j1~j6
       | 2.Aggiunta interfaccia JointHysteresisError()
       | 3.Aggiunta interfaccia JointRepeatability()
       | 4.Aggiunta interfaccia SetAdmittanceParams()
       | 5.Aggiunta interfaccia MoveToIntersectLineStart()
       | 6.Aggiunta interfaccia MoveIntersectLine()

   * - V3.8.7
     - 2025-10-21
     - | 1.Interfaccia NewSpiral() aggiunge parametro velAccMode
       | 2.FT_Control() aggiunge interfacce parametri massa e smorzamento
       | 3.Aggiunta interfaccia JointSensitivityCalibration()
       | 4.Aggiunta interfaccia JointSensitivityCollect()
       | 5.Aggiunta interfaccia MotionQueueClear()
       | 6.Aggiunta interfaccia GetSlavePortErrCounter()
       | 7.Aggiunta interfaccia SlavePortErrCounterClear()
       | 8.Aggiunta interfaccia SetVelFeedForwardRatio()
       | 9.Aggiunta interfaccia GetVelFeedForwardRatio()
       | 10.Aggiunta interfaccia RobotMCULogCollect()
       | 11.Struttura stato aggiunge ultima posizione obiettivo ServoJ in coda, conteggio comandi ServoJ

   * - V3.8.6
     - 2025-09-19
     - | 1.Interfaccia SetLoadCoord() aggiunge parametro numero carico
       | 2.Aggiunta interfaccia LaserTrackingLaserOnOff()
       | 3.Aggiunta interfaccia LaserTrackingTrackOnOff()
       | 4.Aggiunta interfaccia LaserTrackingSearchStart_xyz()
       | 5.Aggiunta interfaccia LaserTrackingSearchStart_point()
       | 6.Aggiunta interfaccia LaserTrackingSearchStop()
       | 7.Aggiunta interfaccia LaserTrackingSensorConfig()
       | 8.Aggiunta interfaccia LaserTrackingSensorSamplePeriod()
       | 9.Aggiunta interfaccia LoadPosSensorDriver()
       | 10.Aggiunta interfaccia UnLoadPosSensorDriver()
       | 11.Aggiunta interfaccia LaserSensorRecord1()
       | 12.Aggiunta interfaccia LaserSensorReplay()
       | 13.Aggiunta interfaccia MoveLTR()
       | 14.Aggiunta interfaccia LaserSensorRecordandReplay()
       | 15.Aggiunta interfaccia MoveToLaserRecordStart()
       | 16.Aggiunta interfaccia MoveToLaserRecordEnd()
       | 17.Aggiunta interfaccia MoveToLaserSeamPos()
       | 18.Aggiunta interfaccia GetLaserSeamPos()
       | 19.Aggiunta interfaccia ImpedanceControlStartStop()
       | 20.Aggiunta interfaccia GetToolCoordWithID()
       | 21.Aggiunta interfaccia GetWObjCoordWithID()
       | 22.Aggiunta interfaccia GetExToolCoordWithID()
       | 23.Aggiunta interfaccia GetExAxisCoordWithID()
       | 24.Aggiunta interfaccia GetTargetPayloadWithID()
       | 25.Aggiunta interfaccia GetExAxisCoordWithID()
       | 26.Aggiunta interfaccia GetCurWObjCoord()
       | 27.Aggiunta interfaccia GetCurExToolCoord()
       | 28.Aggiunta interfaccia GetCurExToolCoord()
       | 29.Aggiunta interfaccia KernelUpgrade()
       | 30.Aggiunta interfaccia GetKernelUpgradeResult()
       | 31.Aggiunta interfaccia CustomWeaveSetPara()
       | 32.Aggiunta interfaccia CustomWeaveGetPara()
       | 33.Struttura stato aggiunge dati sistema coordinate utensile, pezzo, utensile esterno, asse estensione e dati massa, centro di massa carico

   * - V3.8.5
     - 2025-08-20
     - | 1.Interfaccia MoveL() aggiunge parametro cinematica inversa config, parametro velAccParamMode
       | 2.Interfaccia MoveC() aggiunge parametro cinematica inversa config, parametro velAccParamMode
       | 3.Interfaccia Circle() aggiunge parametro cinematica inversa config, parametro velAccParamMode
       | 4.Interfaccia NewSpiral() aggiunge parametro cinematica inversa config
       | 5.Interfaccia NewSplinePoint() aggiunge parametro cinematica inversa config
       | 6.Interfaccia ExtAxisSyncMoveJ() aggiunge parametro cinematica inversa config
       | 7.Interfaccia ExtAxisSyncMoveL() aggiunge parametro cinematica inversa config
       | 8.Interfaccia ExtAxisSyncMoveC() aggiunge parametro cinematica inversa config
       | 9.Nuova interfaccia LaserRecordPoint(coordID)
       | 10.Nuova interfaccia SetExAxisRobotPlan(strategy)
       | 11.Nuova interfaccia OpenLuaUpload(filePath)
       | 12.Nuova interfaccia GetFieldBusConfig()
       | 13.Nuova interfaccia FieldBusSlaveWriteDO(DOIndex,wirteNum,status)
       | 14.Nuova interfaccia FieldBusSlaveWriteAO(AOIndex,wirteNum,status)
       | 15.Nuova interfaccia FieldBusSlaveReadDI(DOIndex,readeNum)
       | 16.Nuova interfaccia FieldBusSlaveReadAI(AOIndex,readeNum)
       | 17.Nuova interfaccia FieldBusSlaveWaitDI(DIIndex,status,waitMs)
       | 18.Nuova interfaccia FieldBusSlaveWaitAI(AIIndex,waitType,value,waitMs)
       | 19.Nuova interfaccia SetSuckerCtrl(slaveID,len,ctrlValue)
       | 20.Nuova interfaccia GetSuckerState(slaveID)
       | 21.Nuova interfaccia WaitSuckerState(slaveID,state,ms)

   * - V3.8.4
     - 2025-07-17
     - | 1.Interfaccia ExtAxisMove() aggiunge parametro smooth blend
       | 2.Aggiunta interfaccia SetFocusCalibPoint(pointNum,point)
       | 3.Aggiunta interfaccia ComputeFocusCalib(pointNum)
       | 4.Aggiunta interfaccia FocusStart(kp,kpredic,aMax,vMax,type)
       | 5.Aggiunta interfaccia FocusEnd()
       | 6.Aggiunta interfaccia SetFocusPosition(pos)
       | 7.Aggiunta interfaccia SetEncoderUpgrade(path)
       | 8.Aggiunta interfaccia SetJointFirmwareUpgrade(type,path)
       | 9.Aggiunta interfaccia SetCtrlFirmwareUpgrade(type,path)
       | 10.Aggiunta interfaccia SetEndFirmwareUpgrade(type,path)
       | 11.Aggiunta interfaccia JointAllParamUpgrade(path)
       
   * - V3.8.3
     - 2025-06-24
     - | 1.Interfaccia Circle() aggiunge parametri percentuale accelerazione e raggio smooth
       | 2.Interfaccia EndForceDragControl() aggiunge parametro flag rilevamento collisione robot durante trascinamento assistito
       | 3.Interfaccia ServoJ() aggiunge parametro ID comando
       | 4.Aggiunta interfaccia SetSSHScpCmd()
       | 5.Aggiunta interfaccia SetWideBoxTempFanMonitorParam()
       | 6.Aggiunta interfaccia GetWideBoxTempFanMonitorParam()
       | 7.Struttura stato aggiunge dati stato temperatura pannello controllo e corrente ventilatore
              
   * - V3.8.2
     - 2025-06-13
     - | 1.Interfaccia WeaveSetPara() aggiunge parametro angolo rollio direzione oscillazione (rotazione attorno asse X oscillazione)
       | 2.Interfaccia WeaveChangeStart() aggiunge parametri numero oscillazione, velocità inizio saldatura, velocità fine saldatura
       | 3.Interfaccia ExtDevSetUDPComParam() aggiunge parametro connessione automatica dopo riavvio alimentazione
       | 4.SetCollisionDetectionMethod() aggiunge selezione metodo soglia livello collisione
       | 5.PtpFIRPlanningStart() aggiunge valore estremo jerk giunto unificato
       | 6.Aggiunta interfaccia WeldingSetVoltageGradualChangeStart()
       | 7.Aggiunta interfaccia WeldingSetVoltageGradualChangeEnd()
       | 8.Aggiunta interfaccia WeldingSetCurrentGradualChangeStart()
       | 9.Aggiunta interfaccia WeldingSetCurrentGradualChangeEnd()
       | 10.Aggiunta interfaccia ArcWeldTraceAIChannelCurrent()
       | 11.Aggiunta interfaccia ArcWeldTraceAIChannelVoltage()
       | 12.Aggiunta interfaccia ArcWeldTraceCurrentPara()
       | 13.Aggiunta interfaccia ArcWeldTraceVoltagePara()
       | 14.Aggiunta interfaccia GetSmarttoolBtnState()
       | 15.Aggiunta interfaccia ExtAxisGetCoord()
                     
   * - V3.8.1
     - 2025-04-24
     - | 1.Interfaccia ConveyorSetParam() aggiunge parametri tipo movimento tracciamento, distanza inizio tracciamento, distanza fine tracciamento
       | 2.Aggiunta interfaccia AccSmoothStart()
       | 3.Aggiunta interfaccia AccSmoothEnd()
       | 4.Aggiunta interfaccia RbLogDownload()
       | 5.Aggiunta interfaccia AllDataSourceDownload()
       | 6.Aggiunta interfaccia DataPackageDownload()
       | 7.Aggiunta interfaccia GetRobotSN()
       | 8.Aggiunta interfaccia ShutDownRobotOS()
       | 9.Aggiunta interfaccia ConveyorComDetect()
       | 10.Aggiunta interfaccia ConveyorComDetectTrigger()
                     
   * - V3.8.0
     - 2025-02-12
     - | 1.Interfaccia EndForceDragControl() aggiunge parametro evitamento punti singolari
       | 2.Interfaccia ArcWeldTraceControl() aggiunge parametro offset
       | 3.Aggiunta interfaccia WeaveChangeStart()
       | 4.Aggiunta interfaccia WeaveChangeEnd()
       | 5.Aggiunta interfaccia LoadTrajectoryLA()
       | 6.Aggiunta interfaccia MoveTrajectoryLA()
       | 7.Aggiunta interfaccia CustomCollisionDetectionStart()
       | 8.Aggiunta interfaccia CustomCollisionDetectionEnd()