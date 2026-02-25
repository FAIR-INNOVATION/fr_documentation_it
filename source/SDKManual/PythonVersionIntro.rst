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