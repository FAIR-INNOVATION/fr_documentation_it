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