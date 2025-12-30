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