Periferiche del Robot
============================

.. toctree:: 
    :maxdepth: 5

Configurare la pinza
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Configura la pinza
    * @param  [in] company  Produttore pinza, da definire
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, predefinito 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, predefinito 0
    * @param  [in] bus  Posizione bus terminale su cui è montato il dispositivo, attualmente non utilizzato, predefinito 0
    * @return  Codice di errore
    */
    errno_t  SetGripperConfig(int company, int device, int softvesion, int bus);

Ottenere la configurazione della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene la configurazione della pinza
    * @param  [in] company  Produttore pinza, da definire
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, predefinito 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, predefinito 0
    * @param  [in] bus  Posizione bus terminale su cui è montato il dispositivo, attualmente non utilizzato, predefinito 0
    * @return  Codice di errore
    */
    errno_t  GetGripperConfig(int *company, int *device, int *softvesion, int *bus);

Attivare la pinza
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Attiva la pinza
    * @param  [in] index  Numero pinza
    * @param  [in] act  0-Ripristina, 1-Attiva
    * @return  Codice di errore
    */
    errno_t  ActGripper(int index, uint8_t act);

Controllare la pinza
++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
     * @brief  Controlla la pinza
     * @param  [in] index  Numero pinza
     * @param  [in] pos  Percentuale posizione, intervallo [0~100]
     * @param  [in] vel  Percentuale velocità, intervallo [0~100]
     * @param  [in] force  Percentuale coppia, intervallo [0~100]
     * @param  [in] max_time  Tempo massimo attesa, intervallo [0~30000], unità ms
     * @param  [in] block  0-Blocco, 1-Non bloccante
     * @param  [in] type Tipo pinza, 0-Pinza parallela; 1-Pinza rotante
     * @param  [in] rotNum Numero rotazioni
     * @param  [in] rotVel Percentuale velocità rotazione [0-100]
     * @param  [in] rotTorque Percentuale coppia rotazione [0-100]
     * @return  Codice di errore
     */
    errno_t MoveGripper(int index, int pos, int vel, int force, int max_time, uint8_t block, int type, double rotNum, int rotVel, int rotTorque);

Ottenere lo stato di movimento della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene lo stato di movimento della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] staus  0-Movimento non completato, 1-Movimento completato
     * @return  Codice di errore
     */
    errno_t  GetGripperMotionDone(uint16_t *fault, uint8_t *status);

Ottenere lo stato di attivazione della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene lo stato di attivazione della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] status  bit0~bit15 corrisponde ai numeri pinza 0~15, bit=0 non attivata, bit=1 attivata
     * @return  Codice di errore
     */
    errno_t  GetGripperActivateStatus(uint16_t *fault, uint16_t *status);

Ottenere la posizione della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la posizione della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] position  Percentuale posizione, intervallo 0~100%
     * @return  Codice di errore
     */
    errno_t  GetGripperCurPosition(uint16_t *fault, uint8_t *position);

Ottenere la velocità della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la velocità della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] speed  Percentuale velocità, intervallo 0~100%
     * @return  Codice di errore
     */
    errno_t  GetGripperCurSpeed(uint16_t *fault, int8_t *speed);

Ottenere la corrente della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la corrente della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] current  Percentuale corrente, intervallo 0~100%
     * @return  Codice di errore
     */
    errno_t  GetGripperCurCurrent(uint16_t *fault, int8_t *current);

Ottenere la tensione della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la tensione della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] voltage  Tensione, unità 0.1V
     * @return  Codice di errore
     */
    errno_t  GetGripperVoltage(uint16_t *fault, int *voltage);

Ottenere la temperatura della pinza
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la temperatura della pinza
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] temp  Temperatura, unità ℃
     * @return  Codice di errore
     */
    errno_t  GetGripperTemp(uint16_t *fault, int *temp);

Calcolare punto pre-presa - visione
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcola punto pre-presa - visione
     * @param  [in] desc_pos  Posa cartesiana punto presa
     * @param  [in] zlength   Spostamento asse z
     * @param  [in] zangle    Spostamento rotazione asse z
     * @return  Codice di errore 
     */
    errno_t  ComputePrePick(DescPose *desc_pos, double zlength, double zangle, DescPose *pre_pos);

Calcolare punto ritiro - visione
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Calcola punto ritiro - visione
     * @param  [in] desc_pos  Posa cartesiana punto presa
     * @param  [in] zlength   Spostamento asse z
     * @param  [in] zangle    Spostamento rotazione asse z
     * @return  Codice di errore 
     */
    errno_t  ComputePostPick(DescPose *desc_pos, double zlength, double zangle, DescPose *post_pos);

Esempio di codice per operazioni pinza robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestGripper(void)
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
      int company = 4;
      int device = 0;
      int softversion = 0;
      int bus = 2;
      int index = 2;
      int act = 0;
      int max_time = 30000;
      uint8_t block = 0;
      uint8_t status;
      uint16_t fault;
      uint16_t active_status = 0;
      uint8_t current_pos = 0;
      int8_t current = 0;
      int voltage = 0;
      int temp = 0;
      int8_t speed = 0;
      robot.SetGripperConfig(company, device, softversion, bus);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.GetGripperConfig(&company, &device, &softversion, &bus);
      printf("gripper config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      act = 1;
      robot.ActGripper(index, act);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 100, 50, 50, max_time, block, 0, 0, 0, 0);
      std::this_thread::sleep_for(std::chrono::milliseconds(1000));
      robot.MoveGripper(index, 0, 50, 0, max_time, block, 0, 0, 0, 0);
      robot.GetGripperMotionDone(&fault, &status);
      printf("motion status:%u,%u\n", fault, status);
      robot.GetGripperActivateStatus(&fault, &active_status);
      printf("gripper active fault is: %u, status is: %u\n", fault, active_status);
      robot.GetGripperCurPosition(&fault, &current_pos);
      printf("fault is:%u, current position is: %u\n", fault, current_pos);
      robot.GetGripperCurCurrent(&fault, &current);
      printf("fault is:%u, current current is: %d\n", fault, current);
      robot.GetGripperVoltage(&fault, &voltage);
      printf("fault is:%u, current voltage is: %d \n", fault, voltage);
      robot.GetGripperTemp(&fault, &temp);
      printf("fault is:%u, current temperature is: %d\n", fault, temp);
      robot.GetGripperCurSpeed(&fault, &speed);
      printf("fault is:%u, current speed is: %d\n", fault, speed);
      int retval = 0;
      DescPose prepick_pose = {};
      DescPose postpick_pose = {};
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.ComputePrePick(&p1Desc, 10, 0, &prepick_pose);
      printf("ComputePrePick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", prepick_pose.tran.x, prepick_pose.tran.y, prepick_pose.tran.z, prepick_pose.rpy.rx, prepick_pose.rpy.ry, prepick_pose.rpy.rz);
      retval = robot.ComputePostPick(&p2Desc, -10, 0, &postpick_pose);
      printf("ComputePostPick retval is: %d\n", retval);
      printf("xyz is: %f, %f, %f; rpy is: %f, %f, %f\n", postpick_pose.tran.x, postpick_pose.tran.y, postpick_pose.tran.z, postpick_pose.rpy.rx, postpick_pose.rpy.ry, postpick_pose.rpy.rz);
      robot.CloseRPC();
      return 0;
    }

Ottenere il numero di rotazioni della pinza rotante
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 3.7.6版本加入

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene il numero di rotazioni della pinza rotante
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] num  Numero rotazioni
     * @return  Codice di errore
     */
    errno_t GetGripperRotNum(uint16_t* fault, double* num);

Ottenere la velocità di rotazione della pinza rotante
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la velocità di rotazione della pinza rotante
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] speed  Percentuale velocità rotazione
     * @return  Codice di errore
     */
    errno_t GetGripperRotSpeed(uint16_t* fault, int* speed);

Ottenere la coppia di rotazione della pinza rotante
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: V3.7.6

.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la coppia di rotazione della pinza rotante
     * @param  [out] fault  0-Nessun errore, 1-Errore presente
     * @param  [out] torque  Percentuale coppia rotazione
     * @return  Codice di errore
     */
    errno_t GetGripperRotTorque(uint16_t* fault, int* torque);

Esempio di codice per ottenere lo stato della pinza rotante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestRotGripperState(void)
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
      uint16_t fault = 0;
      double rotNum = 0.0;
      int rotSpeed = 0;
      int rotTorque = 0;
      robot.GetGripperRotNum(&fault, &rotNum);
      robot.GetGripperRotSpeed(&fault, &rotSpeed);
      robot.GetGripperRotTorque(&fault, &rotTorque);
      printf("gripper rot num : %lf, gripper rotSpeed : %d, gripper rotTorque : %d\n", rotNum, rotSpeed, rotTorque);
      robot.CloseRPC();
      return 0;
    }

Avvio/arresto nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Avvio/arresto nastro trasportatore
    * @param [in] status Stato, 1-Avvia, 0-Arresta 
    * @return Codice di errore
    */
    errno_t ConveyorStartEnd(uint8_t status);

Registrare punto rilevamento IO
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registra punto rilevamento IO
    * @return Codice di errore
    */
    errno_t ConveyorPointIORecord();

Registrare punto A
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registra punto A
    * @return Codice di errore
    */
    errno_t ConveyorPointARecord();

Registrare punto di riferimento
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registra punto di riferimento
    * @return Codice di errore
    */
    errno_t ConveyorRefPointRecord();

Registrare punto B
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Registra punto B
    * @return Codice di errore
    */
    errno_t ConveyorPointBRecord();

Rilevamento IO pezzo nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Rilevamento IO pezzo nastro trasportatore
    * @param [in] max_t Tempo massimo rilevamento, unità ms
    * @return Codice di errore
    */
    errno_t ConveyorIODetect(int max_t);

Ottenere posizione corrente oggetto
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene posizione corrente oggetto
    * @param [in] mode 
    * @return Codice di errore
    */
    errno_t ConveyorGetTrackData(int mode);

Inizio tracciamento nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio tracciamento nastro trasportatore
    * @param [in] status Stato, 1-Avvia, 0-Arresta 
    * @return Codice di errore
    */
    errno_t ConveyorTrackStart(uint8_t status);

Fine tracciamento nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fine tracciamento nastro trasportatore
    * @return Codice di errore
    */
    errno_t ConveyorTrackEnd();

Configurazione parametri nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Configurazione parametri nastro trasportatore
    * @param [in] para[0] Canale encoder 1~2
    * @param [in] para[1] Impulsi per giro encoder
    * @param [in] para[2] Distanza percorrenza nastro per giro encoder
    * @param [in] para[3] Numero sistema coordinate pezzo Per funzione tracciamento movimento seleziona numero sistema coordinate pezzo, per tracciamento presa, tracciamento TPD imposta 0
    * @param [in] para[4] Configura visione 0 non configurato 1 configurato
    * @param [in] para[5] Rapporto velocità Per opzione tracciamento presa nastro trasportatore (1-100) Altre opzioni predefinite 1 
    * @param [in] followType Tipo movimento tracciamento, 0-Movimento tracciamento; 1-Movimento inseguimento verifica
    * @param [in] startDis Necessario per presa inseguimento verifica, distanza inizio tracciamento, -1: calcolo automatico (avvio automatico inseguimento verifica quando pezzo raggiunge sotto robot), unità mm, valore predefinito 0
    * @param [in] endDis Necessario per presa inseguimento verifica, distanza fine tracciamento, unità mm, valore predefinito 100
    * @return Codice di errore
    */
    errno_t ConveyorSetParam(float para[6], int followType = 0, int startDis = 0, int endDis = 100);

Compensazione punto presa nastro trasportatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
     * @brief Compensazione punto presa nastro trasportatore
     * @param [in] cmp Posizione compensazione double[3]{x, y, z}
     * @return Codice di errore
     */
    errno_t ConveyorCatchPointComp(double cmp[3]);

Movimento lineare nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento lineare nastro trasportatore
    * @param [in] status Stato, 1-Avvia, 0-Arresta 
    * @return Codice di errore
    */
    errno_t TrackMoveL(char name[32], int tool, int wobj, float vel, float acc, float ovl, float blendR, uint8_t flag, uint8_t type);

Rilevamento input comunicazione nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Rilevamento input comunicazione nastro trasportatore
    * @param [in] timeout Tempo attesa timeout ms
    * @return Codice di errore
    */
    errno_t ConveyorComDetect(int timeout);

Trigger rilevamento input comunicazione nastro trasportatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Trigger rilevamento input comunicazione nastro trasportatore
    * @return Codice di errore
    */
    errno_t ConveyorComDetectTrigger();

Esempio programma operazioni nastro trasportatore robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestConveyor(void)
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
      int retval = 0;
      retval = robot.ConveyorStartEnd(1);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = robot.ConveyorPointIORecord();
      printf("ConveyorPointIORecord retval is: %d\n", retval);
      retval = robot.ConveyorPointARecord();
      printf("ConveyorPointARecord retval is: %d\n", retval);
      retval = robot.ConveyorRefPointRecord();
      printf("ConveyorRefPointRecord retval is: %d\n", retval);
      retval = robot.ConveyorPointBRecord();
      printf("ConveyorPointBRecord retval is: %d\n", retval);
      retval = robot.ConveyorStartEnd(0);
      printf("ConveyorStartEnd retval is: %d\n", retval);
      retval = 0;
      float param[6] = { 1,10000,200,0,0,20 };
      retval = robot.ConveyorSetParam(param);
      printf("ConveyorSetParam retval is: %d\n", retval);
      double cmp[3] = { 0.0, 0.0, 0.0 };
      retval = robot.ConveyorCatchPointComp(cmp);
      printf("ConveyorCatchPointComp retval is: %d\n", retval);
      int index = 1;
      int max_time = 30000;
      uint8_t block = 0;
      retval = 0;
      DescPose p1Desc(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose p2Desc(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      retval = robot.MoveCart(&p1Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      printf("MoveCart retval is: %d\n", retval);
      retval = robot.WaitMs(1);
      printf("WaitMs retval is: %d\n", retval);
      retval = robot.ConveyorIODetect(10000);
      printf("ConveyorIODetect retval is: %d\n", retval);
      retval = robot.ConveyorGetTrackData(1);
      printf("ConveyorGetTrackData retval is: %d\n", retval);
      retval = robot.ConveyorTrackStart(1);
      printf("ConveyorTrackStart retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrCatchPoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.MoveGripper(index, 51, 40, 30, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      retval = robot.TrackMoveL("cvrRaisePoint", 1, 0, 100, 100, 100, -1.0, 0, 0);
      printf("TrackMoveL retval is: %d\n", retval);
      retval = robot.ConveyorTrackEnd();
      printf("ConveyorTrackEnd retval is: %d\n", retval);
      robot.MoveCart(&p2Desc, 1, 0, 100.0, 100.0, 100.0, -1.0, -1);
      retval = robot.MoveGripper(index, 100, 40, 10, max_time, block, 0, 0, 0, 0);
      printf("MoveGripper retval is: %d\n", retval);
      rtn = robot->ConveyorComDetect(1000 * 10);
      printf("ConveyorComDetect rtn is: %d\n", rtn);
      robot.Sleep(2000);
      rtn = robot->ConveyorComDetectTrigger();
      printf("ConveyorComDetectTrigger rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Configurazione sensore terminale
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurazione sensore terminale
    * @param [in] idCompany Produttore, 18-JUNKONG; 25-HUIDE
    * @param [in] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
    * @param [in] idSoftware Versione software, 0-J1.0/HuiDe1.0 (non ancora disponibile)
    * @param [in] idBus Posizione montaggio, 1-Porta terminale 1; 2-Porta terminale 2...8-Porta terminale 8 (non ancora disponibile)
    * @return Codice di errore
    */
    errno_t AxleSensorConfig(int idCompany, int idDevice, int idSoftware, int idBus);

Ottenere configurazione sensore terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene configurazione sensore terminale
     * @param [out] idCompany Produttore, 18-JUNKONG; 25-HUIDE
     * @param [out] idDevice Tipo, 0-JUNKONG/RYR6T.V1.0
     * @return Codice di errore
     */
    errno_t AxleSensorConfigGet(int& idCompany, int& idDevice);

Attivazione sensore terminale
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Attivazione sensore terminale
     * @param [in] actFlag 0-Ripristino; 1-Attivazione
     * @return Codice di errore
     */
    errno_t AxleSensorActivate(int actFlag);

Scrittura registro sensore terminale
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Scrittura registro sensore terminale
     * @param [in] devAddr Numero indirizzo dispositivo 0-255
     * @param [in] regHAddr Indirizzo registro alto 8 bit
     * @param [in] regLAddr Indirizzo registro basso 8 bit
     * @param [in] regNum Numero registri 0-255
     * @param [in] data1 Valore registro scritto 1
     * @param [in] data2 Valore registro scritto 2
     * @param [in] isNoBlock 0-Blocco; 1-Non bloccante
     * @return Codice di errore
     */
    errno_t AxleSensorRegWrite(int devAddr, int regHAddr, int regLAddr, int regNum, int data1, int data2, int isNoBlock);

Esempio di codice sensore terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestAxleSensor(void)
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
      robot.AxleSensorConfig(18, 0, 0, 1);
      int company = -1;
      int type = -1;
      robot.AxleSensorConfigGet(company, type);
      printf("company is %d, type is %d\n", company, type);
      rtn = robot.AxleSensorActivate(1);
      printf("AxleSensorActivate rtn is %d\n", rtn);
      robot.Sleep(1000);
      rtn = robot.AxleSensorRegWrite(1, 4, 6, 1, 0, 0, 0);
      printf("AxleSensorRegWrite rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Ottenere protocollo periferiche robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene protocollo periferiche robot
    * @param [out] protocol Numero protocollo periferiche robot 4096-Scheda controllo assi estesi; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Codice di errore
    */
    errno_t GetExDevProtocol(int *protocol);

Impostare protocollo periferiche robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta protocollo periferiche robot
    * @param [in] protocol Numero protocollo periferiche robot 4096-Scheda controllo assi estesi; 4097-ModbusSlave; 4098-ModbusMaster
    * @return Codice di errore
    */
    errno_t SetExDevProtocol(int protocol);

Esempio programma impostazione protocollo periferiche robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:
    
    int TestExDevProtocol(void)
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
      int protocol = 4096;
      rtn = robot.SetExDevProtocol(protocol);
      std::cout << "SetExDevProtocol rtn " << rtn << std::endl;
      rtn = robot.GetExDevProtocol(&protocol);
      std::cout << "GetExDevProtocol rtn " << rtn << " protocol is: " << protocol << std::endl;
      robot.CloseRPC();
      return 0;
    }

Ottenere parametri comunicazione terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene parametri comunicazione terminale
    * @param param Parametri comunicazione terminale
    * @return  Codice di errore
    */
    errno_t GetAxleCommunicationParam(AxleComParam* param);

Impostare parametri comunicazione terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta parametri comunicazione terminale
    * @param param  Parametri comunicazione terminale
    * @return  Codice di errore
    */
    errno_t SetAxleCommunicationParam(AxleComParam param);

Impostare tipo trasferimento file terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta tipo trasferimento file terminale
    * @param type 1-File aggiornamento MCU; 2-File LUA
    * @return  Codice di errore
    */
    errno_t SetAxleFileType(int type);

Impostare abilitazione esecuzione LUA terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta abilitazione esecuzione LUA terminale
    * @param enable 0-Non abilitare; 1-Abilitare
    * @return  Codice di errore
    */
    errno_t SetAxleLuaEnable(int enable);

Ripristino errori anomali file LUA terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ripristino errori anomali file LUA terminale
    * @param status 0-Non ripristinare; 1-Ripristinare
    * @return  Codice di errore
    */
    errno_t SetRecoverAxleLuaErr(int status);

Ripristino errori anomali file LUA terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene stato abilitazione esecuzione LUA terminale
    * @param status status[0]: 0-Non abilitato; 1-Abilitato
    * @return  Codice di errore
    */
    errno_t GetAxleLuaEnableStatus(int status[]);

Imposta i tipi di dispositivo abilitati per l'end-effector LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta i tipi di dispositivo abilitati per l'end-effector LUA
    * @param forceSensorEnable Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    * @param gripperEnable Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    * @param IOEnable Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    * @param dexhandEnable Stato abilitazione mano destra, 0-disabilitato; 1-abilitato
    * @return  Codice errore
    */
    errno_t SetAxleLuaEnableDeviceType(int forceSensorEnable, int gripperEnable, int IOEnable, int dexhandEnable);

Ottiene i tipi di dispositivo abilitati per l'end-effector LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:
        
    /**
    * @brief Ottiene i tipi di dispositivo abilitati per l'end-effector LUA
    * @param enable enable[0]:forceSensorEnable Stato abilitazione sensore di forza, 0-disabilitato; 1-abilitato
    * @param enable enable[1]:gripperEnable Stato abilitazione pinza, 0-disabilitato; 1-abilitato
    * @param enable enable[2]:IOEnable Stato abilitazione dispositivo IO, 0-disabilitato; 1-abilitato
    * @param enable enable[3]:dexhandEnable Stato abilitazione mano destra, 0-disabilitato; 1-abilitato
    * @return Codice errore
    */
    errno_t GetAxleLuaEnableDeviceType(int* forceSensorEnable, int* gripperEnable, int* IOEnable, int* dexhandEnable);

Ottiene i dispositivi dell'end-effector attualmente configurati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i dispositivi dell'end-effector attualmente configurati
    * @param [out] forceSensorEnable Numero dispositivo sensore di forza abilitato, 0-disabilitato; 1-abilitato
    * @param [out] gripperEnable Numero dispositivo pinza abilitato, 0-disabilitato; 1-abilitato
    * @param [out] IODeviceEnable Numero dispositivo IO abilitato, 0-disabilitato; 1-abilitato
    * @param [out] decHandEnable Numero dispositivo mano destra abilitato, 0-disabilitato; 1-abilitato
    * @return Codice errore
    */
    errno_t GetAxleLuaEnableDevice(int forceSensorEnable[], int gripperEnable[], int IODeviceEnable[], int decHandEnable[]);

Imposta le funzioni di controllo azione pinza abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta le funzioni di controllo azione pinza abilitate
    * @param id Numero dispositivo pinza
    * @param func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; func[2]-impostazione posizione; func[3]-impostazione velocità; func[4]-impostazione coppia; func[6]-lettura stato pinza;
        func[7]-lettura stato inizializzazione; func[8]-lettura codice guasto; func[9]-lettura posizione; func[10]-lettura velocità; func[11]-lettura coppia; func[12]-impostazione giri per pinza rotante;
        func[13]-impostazione velocità rotazione pinza rotante; func[14]-impostazione coppia rotazione pinza rotante; func[15]-lettura stato pinza rotante; func[16]-lettura stato inizializzazione pinza rotante;
        func[17]-lettura giri pinza rotante; func[18]-lettura velocità pinza rotante; func[19]-lettura coppia pinza rotante; func[20]-impostazione movimento sincrono multiasse; func[21]-comando clear guasti;
        func[22]-stato funzionamento singolo asse; func[23]-stato funzionamento tutti gli assi;
    * @return  Codice errore
    */
    errno_t SetAxleLuaGripperFunc(int id, int func[32]);

Ottiene le funzioni di controllo azione pinza abilitate
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene le funzioni di controllo azione pinza abilitate
    * @param id Numero dispositivo pinza
    * @param func func[0]-abilitazione pinza; func[1]-inizializzazione pinza; func[2]-impostazione posizione; func[3]-impostazione velocità; func[4]-impostazione coppia; func[6]-lettura stato pinza;
        func[7]-lettura stato inizializzazione; func[8]-lettura codice guasto; func[9]-lettura posizione; func[10]-lettura velocità; func[11]-lettura coppia; func[12]-impostazione giri per pinza rotante;
        func[13]-impostazione velocità rotazione pinza rotante; func[14]-impostazione coppia rotazione pinza rotante; func[15]-lettura stato pinza rotante; func[16]-lettura stato inizializzazione pinza rotante;
        func[17]-lettura giri pinza rotante; func[18]-lettura velocità pinza rotante; func[19]-lettura coppia pinza rotante; func[20]-impostazione movimento sincrono multiasse; func[21]-comando clear guasti;
        func[22]-stato funzionamento singolo asse; func[23]-stato funzionamento tutti gli assi;
    * @return  Codice errore
    */
    errno_t GetAxleLuaGripperFunc(int id, int func[32]);

Scrittura file slave Ethercat robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Scrittura file slave Ethercat robot
    * @param type Tipo file slave, 1-Aggiornamento file slave; 2-Aggiornamento file configurazione slave
    * @param slaveID Numero slave
    * @param fileName Nome file upload
    * @return  Codice di errore
    */
    errno_t SlaveFileWrite(int type, int slaveID, std::string fileName);

Upload file protocollo aperto Lua terminale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Upload file protocollo aperto Lua terminale
    * @param filePath Percorso nome file lua locale ".../AXLE_LUA_End_DaHuan.lua"
    * @return Codice di errore
    */
    errno_t AxleLuaUpload(std::string filePath);

Modalità boot slave Ethercat robot
++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Modalità boot slave Ethercat robot
    * @return  Codice di errore
    */
    errno_t SetSysServoBootMode();

Esempio codice operazioni file LUA terminale robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAxleLua(void)
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
        robot.AxleLuaUpload("D://zUP/AXLE_LUA_End_DaHuan.lua");
        AxleComParam param(7, 8, 1, 0, 5, 3, 1);
        robot.SetAxleCommunicationParam(param);
        AxleComParam getParam;
        robot.GetAxleCommunicationParam(&getParam);
        printf("GetAxleCommunicationParam param is %d %d %d %d %d %d %d\n", getParam.baudRate, getParam.dataBit, getParam.stopBit, getParam.verify, getParam.timeout, getParam.timeoutTimes, getParam.period);
        robot.SetAxleLuaEnable(1);
        int luaEnableStatus = 0;
        robot.GetAxleLuaEnableStatus(&luaEnableStatus);
        robot.SetAxleLuaEnableDeviceType(0, 1, 0, 0);
        int forceEnable = 0;
        int gripperEnable = 0;
        int ioEnable = 0;
        int dexhandEnable = 0;
        robot.GetAxleLuaEnableDeviceType(&forceEnable, &gripperEnable, &ioEnable, &dexhandEnable);
        printf("GetAxleLuaEnableDeviceType param is %d %d %d %d\n", forceEnable, gripperEnable, ioEnable, dexhandEnable);
        int func[32] = { 0,1,1,1,1,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0 };
        rtn = robot.SetAxleLuaGripperFunc(2, func);
        printf("SetAxleLuaGripperFunc rtn is %d\n", rtn);
        int getFunc[32] = { 0 };
        rtn = robot.GetAxleLuaGripperFunc(2, getFunc);
        printf("GetAxleLuaGripperFunc rtn is %d\n", rtn);
        int getforceEnable[16] = { 0 };
        int getgripperEnable[16] = { 0 };
        int getioEnable[16] = { 0 };
        int dexhandEnable1[16] = { 0 };
        robot.GetAxleLuaEnableDevice(getforceEnable, getgripperEnable, getioEnable, dexhandEnable1);
        printf("\ngetforceEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getforceEnable[i]);
        }
        printf("\ngetgripperEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getgripperEnable[i]);
        }
        printf("\ngetioEnable status : ");
        for (int i = 0; i < 16; i++)
        {
            printf("%d,", getioEnable[i]);
        }
        printf("\n");
        robot.ActGripper(2, 0);
        robot.Sleep(2000);
        robot.ActGripper(2, 1);
        robot.Sleep(2000);
        robot.MoveGripper(2, 1, 10, 100, 50000, 0, 0, 0, 0, 0);
        int pos = 0;
        while (true)
        {
            robot.GetRobotRealTimeState(&pkg);
            printf("gripper pos is %u\n", pkg.gripper_position);
            robot.Sleep(100);
        }
        robot.CloseRPC();
        return 0;
    }

Ottenere stato pulsanti SmartTool
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene stato pulsanti SmartTool
    * @param [out] state Stato pulsanti manopola SmartTool; (bit0:0-Comunicazione normale; 1-Comunicazione interrotta; bit1-Annulla operazione; bit2-Svuota programma;
    bit3-Pulsante A; bit4-Pulsante B; bit5-Pulsante C; bit6-Pulsante D; bit7-Pulsante E; bit8-Pulsante IO; bit9-Manuale/automatico; bit10-Avvio)
    * @return Codice di errore
    */
    errno_t GetSmarttoolBtnState(int& state);

Esempio codice pulsanti SmartTool
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int main(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;

      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      robot.SetReConnectParam(true, 30000, 500);

      while (true)
      {
        int btn = 0;
        robot.GetSmarttoolBtnState(btn);
        cout << "smarttool " << std::bitset<sizeof(btn) * 8>(btn) << endl;

        Sleep(100);
      }
    }

Controllare ventose a matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Controlla ventose a matrice
    * @param [in] slaveID Numero slave
    * @param [in] len Lunghezza
    * @param [in] ctrlValue Valore controllo
    * @return Codice di errore
    */
    errno_t FRRobot::SetSuckerCtrl(uint8_t slaveID, uint8_t len, uint8_t ctrlValue[20]);

Ottenere stato ventose a matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene stato ventose a matrice
    * @param [in] slaveID Numero slave
    * @param [out] state Stato aspirazione 0-Rilascio oggetto 1-Rilevato pezzo aspirazione riuscita 2-Nessun oggetto aspirato 3-Oggetto distaccato
    * @param [out] pressValue Vuoto corrente unità kpa 
    * @param [out] error Codice errore corrente ventosa
    * @return Codice di errore
    */
    errno_t FRRobot::GetSuckerState(uint8_t slaveID, uint8_t* state, int* pressValue, int* error);

Attendere stato ventosa
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Attende stato ventosa
    * @param [in] slaveID Numero slave
    * @param [in] state Stato aspirazione 0-Rilascio oggetto 1-Rilevato pezzo aspirazione riuscita 2-Nessun oggetto aspirato 3-Oggetto distaccato
    * @param [in] ms Tempo massimo attesa
    * @return Codice di errore
    */
    errno_t FRRobot::WaitSuckerState(uint8_t slaveID, uint8_t state, int ms);

Esempio codice comandi controllo ventose a matrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testSucker()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("E://项目/外设SDK/CtrlDev_sucker.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(1, "CtrlDev_sucker.lua");
        robot.UnloadCtrlOpenLUA(1);
        robot.LoadCtrlOpenLUA(1);
        robot.Sleep(1000);

        //Controllo ventosa modalità broadcast, aspirazione massima capacità
        ctrl[0] = 1;
        robot.SetSuckerCtrl(0, 1, ctrl);

        //Monitoraggio ciclo stato ventosa 1 e ventosa 12
        for (int i = 0; i < 100; i++)
        {
            robot.GetSuckerState(1, &state, &pressVlaue, &error);
            printf("sucker1 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.GetSuckerState(12, &state, &pressVlaue, &error);
            printf("sucker12 state is %d, pressVlaue is %d, error num is %d\n", state, pressVlaue, error);
            robot.Sleep(100);
        }

        //Attesa ventosa 1 se in stato oggetto aspirato, tempo attesa 100ms
        int ret = robot.WaitSuckerState(1, 1, 100);
        printf("WaitSuckerState result is  %d\n", ret);

        //Modalità unicast spegnimento ventosa 1 e 12
        ctrl[0] = 3;
        robot.SetSuckerCtrl(1, 1, ctrl);
        robot.SetSuckerCtrl(12, 1, ctrl);

        robot.CloseRPC();
    }

Upload file LUA protocollo aperto periferiche
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Upload file Lua
     * @param [in] filePath Percorso nome file lua locale
     * @return Codice di errore
     */
    errno_t OpenLuaUpload(std::string filePath);

Ottenere parametri scheda slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene parametri scheda slave
    * @param  [out] type  0-Ethercat，1-CClink, 3-Ethercat, 4-EIP
    * @param  [out] version  Versione protocollo
    * @param  [out] connState  0-Non connesso 1-Connesso
    * @return  Codice di errore
    */
    errno_t GetFieldBusConfig(uint8_t* type, uint8_t* version, uint8_t* connState);

Scrivere DO slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Scrive DO slave
    * @param  [in] DOIndex  Numero DO
    * @param  [in] wirteNum  Quantità scritta
    * @param  [in] status[8] Valori scritti, massimo 8
    * @return  Codice di errore
    */
    errno_t FieldBusSlaveWriteDO(uint8_t DOIndex, uint8_t wirteNum, uint8_t status[8]);

Scrivere AO slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Scrive AO slave
    * @param  [in] AOIndex  Numero AO
    * @param  [in] wirteNum  Quantità scritta
    * @param  [in] status[8] Valori scritti, massimo 8
    * @return  Codice di errore
    */
    errno_t FieldBusSlaveWriteAO(uint8_t AOIndex, uint8_t wirteNum, double status[8]);

Leggere DI slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Legge DI slave
    * @param  [in] DOIndex  Numero DI
    * @param  [in] readeNum  Quantità letta
    * @param  [out] status[8] Valori letti, massimo 8
    * @return  Codice di errore
    */
    errno_t FieldBusSlaveReadDI(uint8_t DOIndex, uint8_t readNum, uint8_t status[8]);

Leggere AI slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Legge AI slave
    * @param  [in] AOIndex  Numero AI
    * @param  [in] readeNum  Quantità letta
    * @param  [out] status[8] Valori letti, massimo 8
    * @return  Codice di errore
    */
    errno_t FieldBusSlaveReadAI(uint8_t AIIndex, uint8_t readNum, double status[8]);

Attendere input DI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Attende input DI esteso
    * @param [in] DIIndex Numero DI
    * @param [in] status 0-Livello basso; 1-Livello alto
    * @param [in] waitMs Tempo massimo attesa (ms)
    * @return Codice di errore
    */
    errno_t FRRobot::FieldBusSlaveWaitDI(uint8_t DIIndex, bool status, int waitMs);

Attendere input AI esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief Attende input AI esteso
    * @param [in] AIIndex Numero AI
    * @param [in] waitType 0-Maggiore di; 1-Minore di
    * @param [in] value Valore AI
    * @param [in] waitMs Tempo massimo attesa (ms)
    * @return Codice di errore
    */
    errno_t FRRobot::FieldBusSlaveWaitAI(uint8_t AIIndex, uint8_t waitType, double value, int waitMs);

Esempio codice interfacce modalità slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    void testFieldBusBoard()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t type = 0, version = 0, connState = 0;
        uint8_t ctrl[8];
        double ctrlAO[8];
        static uint8_t DI[8];
        static double AI[8];

        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("E://项目/外设SDK/CtrlDev_field.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(3, "CtrlDev_field.lua");
        robot.UnloadCtrlOpenLUA(3);
        robot.LoadCtrlOpenLUA(3);
        robot.Sleep(8000);

        //Ottenere tipo protocollo, versione software, stato connessione PLC scheda slave
        robot.GetFieldBusConfig(&type, &version, &connState);
        printf("type is %d, version is %d,connState is %d\n", type, version, connState);

        //Scrittura DO0 = 1, DO1 = 0, DO2 = 1
        ctrl[0] = 0;
        ctrl[1] = 1;
        ctrl[2] = 1;
        robot.FieldBusSlaveWriteDO(0, 3, ctrl);

        //Scrittura AO2 = 0x1000
        ctrlAO[0] = 0x1005;
        robot.FieldBusSlaveWriteAO(2, 1, ctrlAO);

        //Monitoraggio ciclo DI0~DI3 AI0~AI2
        for (int i = 0; i < 100; i++)
        {
            robot.FieldBusSlaveReadDI(0, 4, DI);
            printf("DI0 is %d, DI1 is %d,DI2 is %d,DI3 is %d\n", DI[0], DI[1], DI[2], DI[3]);
            robot.FieldBusSlaveReadAI(0, 3, AI);
            printf("AI0 is %d, AI1 is %d,AI2 is %d\n", AI[0], AI[1], AI[2]);
            robot.Sleep(10);
        }

        //Attesa DI0 se è 1, tempo attesa 100ms, stampa risultato
        int ret = robot.FieldBusSlaveWaitDI(0, 1, 100);
        printf("FieldBusSlaveWaitDI result is  %d\n", ret);

        //Attesa AI0 se maggiore di 400, tempo attesa 100ms, stampa risultato
        ret = robot.FieldBusSlaveWaitAI(0,0,400.00,100);
        printf("FieldBusSlaveWaitAI result is  %d\n", ret);

        robot.CloseRPC();
    }

Accensione/spegnimento periferica laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Funzione accensione/spegnimento periferica laser
     * @param [in] OnOff 0-Spegni 1-Accendi
     * @param [in] weldId ID saldatura predefinito 0
     * @return Codice di errore
     */
    errno_t LaserTrackingLaserOnOff(int OnOff,int weldId);

Inizio/fine tracciamento laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Funzione inizio/fine tracciamento laser
     * @param [in] OnOff 0-Fine 1-Inizio
     * @param [in] coordId Numero sistema coordinate utensile periferica laser
     * @return Codice di errore
     */
    errno_t LaserTrackingTrackOnOff(int OnOff, int coordId); 

Inizio posizionamento laser - direzione fissa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Posizionamento laser - direzione fissa
    * @param [in] direction 0-x+ 1-x- 2-y+ 3-y- 4-z+ 5-z-
    * @param [in] vel Velocità unità %
    * @param [in] distance Distanza massima posizionamento unità mm
    * @param [in] distance Tempo timeout posizionamento unità ms
    * @param [in] posSensorNum Numero coordinate utensile calibrate laser
    * @return Codice di errore
    */
    errno_t LaserTrackingSearchStart_xyz(int direction, int vel, int distance, int timeout, int posSensorNum);

Inizio posizionamento laser - direzione punto arbitrario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Posizionamento laser - direzione arbitraria
     * @param [in] directionPoint Coordinate xyz punto input posizionamento
     * @param [in] vel Velocità unità %
     * @param [in] distance Distanza massima posizionamento unità mm
     * @param [in] distance Tempo timeout posizionamento unità ms
     * @param [in] posSensorNum Numero coordinate utensile calibrate laser
     * @return Codice di errore
     */
    errno_t LaserTrackingSearchStart_point(DescTran directionPoint, int vel, int distance, int timeout, int posSensorNum);

Fine posizionamento laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Fine posizionamento laser
     * @return Codice di errore
     */
    errno_t LaserTrackingSearchStop();

Configurazione parametri rete laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Configurazione parametri rete laser
     * @param [in] ip Indirizzo IP periferica laser
     * @param [in] port Numero porta periferica laser
     * @return Codice di errore
     */
    errno_t LaserTrackingSensorConfig(std::string ip, int port);

Configurazione periodo campionamento periferica laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurazione periodo campionamento periferica laser
    * @param [in] period Periodo campionamento periferica laser unità ms
    * @return Codice di errore
    */
    errno_t LaserTrackingSensorSamplePeriod(int period);

Caricamento driver periferica laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Caricamento driver periferica laser
     * @param [in] type Tipo protocollo driver periferica laser 101-Ruiniu 102-Chuangxiang 103-Quanshi 104-Tongzhou 105-Aotai
     * @return Codice di errore
     */
    errno_t LoadPosSensorDriver(int type);

Scaricamento driver periferica laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Scaricamento driver periferica laser
     * @return Codice di errore
     */
    errno_t UnLoadPosSensorDriver();

Registrazione traiettoria saldatura laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Registrazione traiettoria saldatura laser
    * @param [in] status 0-Ferma registrazione 1-Tracciamento tempo reale  2-Inizia registrazione
    * @param [in] delayTime Tempo ritardo unità ms
    * @return Codice di errore
    */
    errno_t LaserSensorRecord1(int status, int delayTime); 

Riproduzione traiettoria saldatura laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Riproduzione traiettoria saldatura laser
     * @param [in] delayTime Tempo ritardo unità ms
     * @param [in] speed Velocità unità %
     * @return Codice di errore
     */
    errno_t LaserSensorReplay(int delayTime, double speed);

Riproduzione tracciamento laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Riproduzione tracciamento laser
     * @return Codice di errore
     */
    errno_t MoveLTR();

Registrazione e riproduzione traiettoria saldatura laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Registrazione e riproduzione traiettoria saldatura laser
    * @param [in] delayMode Modalità 0-Tempo Ritardo 1-Distanza Ritardo
    * @param [in] delayTime Tempo di ritardo in millisecondi (ms)
    * @param [in] delayDisExAxisNum Numero Asse Esteso
    * @param [in] delayDis Distanza di ritardo in millimetri (mm)
    * @param [in] sensitivePara Coefficiente di Sensibilità della Compensazione
    * @param [in] trackMode Tipo Tracciamento a Punto Fisso. 0-Movimento Asincrono Asse Esteso; 1-Robot
    * @param [in] triggerMode Metodo di Attivazione Tracciamento a Punto Fisso. 0-Durata Tracciamento; 1-IO
    * @param [in] runTime Durata Tracciamento a Punto Fisso del Robot in secondi (s)
    * @param [in] speed Velocità in percentuale (%)
    * @return Codice Errore
    */
    errno_t LaserSensorRecordandReplay(int delayMode, int delayTime, int delayDisExAxisNum, double delayDis, double sensitivePara, int trackMode, int triggerMode, double runTime, double speed);

Movimento al punto iniziale saldatura registrata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento al punto iniziale saldatura registrata
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Velocità unità %
    * @return Codice di errore
    */
    errno_t MoveToLaserRecordStart(int moveType, double ovl);

Movimento al punto finale saldatura registrata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento al punto finale saldatura registrata
    * @param [in] moveType 0-moveJ 1-moveL
    * @param [in] ovl Velocità unità %
    * @return Codice di errore
    */
    errno_t MoveToLaserRecordEnd(int moveType, double ovl);

Movimento al punto posizionamento sensore laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento al punto posizionamento sensore laser
    * @param [in] moveFlag Tipo movimento: 0-PTP; 1-LIN
    * @param [in] ovl Fattore scala velocità, 0-100
    * @param [in] dataFlag Selezione dati cache saldatura: 0-Esegui dati pianificati; 1-Esegui dati registrati
    * @param [in] plateType Tipo lamiera: 0-Lastra ondulata; 1-Lastra ondulata a doppia onda; 2-Lastra recinzione; 3-Fusto; 4-Acciaio corazzato ondulato
    * @param [in] trackOffectType Tipo offset sensore laser: 0-Nessun offset; 1-Offset sistema coordinate base; 2-Offset sistema coordinate utensile; 3-Offset dati originali sensore laser
    * @param [in] offset Quantità offset
    * @return Codice di errore
    */
    errno_t MoveToLaserSeamPos(int moveFlag, double ovl, int dataFlag, int plateType, int trackOffectType, DescPose offset);

Ottenere coordinate punto posizionamento sensore laser
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene informazioni coordinate punto posizionamento sensore laser
    * @param [in] trackOffectType Tipo offset sensore laser: 0-Nessun offset; 1-Offset sistema coordinate base; 2-Offset sistema coordinate utensile; 3-Offset dati originali sensore laser
    * @param [in] offset Quantità offset
    * @param [out] jPos Posizione giunti [°]
    * @param [out] descPos Posizione cartesiana [mm]
    * @param [out] tool Sistema coordinate utensile
    * @param [out] user Sistema coordinate pezzo
    * @param [out] exaxis Posizione asse esteso [mm]
    * @return Codice di errore
    */
    errno_t GetLaserSeamPos(int trackOffectType, DescPose offset, JointPos& jPos, DescPose& descPos, int& tool, int& user, ExaxisPos& exaxis); 

Esempio codice configurazione e debug parametri sensore periferica laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLaserConfig()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);
        //Impostare indirizzo IP e numero porta
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        //Impostare periodo campionamento
        robot.LaserTrackingSensorSamplePeriod(20);
        //Caricare driver
        robot.LoadPosSensorDriver(101);
        //Spegnere periferica laser
        robot.LaserTrackingLaserOnOff(0,0);
        robot.Sleep(3000);
        //Accendere periferica laser
        robot.LaserTrackingLaserOnOff(1, 0);
        robot.CloseRPC();
    }

Esempio codice scansione traiettoria laser e riproduzione traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLaserRecordAndReplay()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while(cnt<31)
        { 
            //Movimento al punto iniziale scansione
            JointPos startjointPos(56.205, -117.951, 141.872, -118.149, -94.217, -122.176);
            DescPose startdescPose(-97.552, -282.855, 26.675, 174.182, -1.338, -91.707);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            //Inizio registrazione traiettoria
            robot.LaserSensorRecord1(2, 10);
            //Movimento al punto finale da registrare
            JointPos endjointPos(68.809, -87.100, 121.120, -127.233, -95.038, -109.555);
            DescPose enddescPose(-103.555, -464.234, 13.076, 174.179, -1.344, -91.709);
            robot.MoveL(&endjointPos, &enddescPose, 1, 0, 30, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
            //Ferma registrazione
            robot.LaserSensorRecord1(0, 10);
            //Movimento al punto iniziale saldatura registrata
            robot.MoveToLaserRecordStart(1, 30);
            //Inizio riproduzione traiettoria
            robot.LaserSensorReplay(10, 100);
            robot.MoveLTR();
            //Ferma riproduzione traiettoria
            robot.LaserSensorRecord1(0, 10);
            printf("Test stabilità scansione laser + riproduzione traiettoria %d次\n", cnt);
            cnt++;
        }
        robot.CloseRPC();
    }

Esempio codice posizionamento laser e tracciamento tempo reale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLasertrack()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");

        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        //Upload e caricamento file protocollo aperto
        robot.OpenLuaUpload("E://openlua/CtrlDev_laser_ruiniu-0117.lua");
        robot.Sleep(2000);
        robot.SetCtrlOpenLUAName(0, "CtrlDev_laser_ruiniu-0117.lua");
        robot.UnloadCtrlOpenLUA(0);
        robot.LoadCtrlOpenLUA(0);
        robot.Sleep(8000);
        int cnt = 1;
        while (cnt < 2)
        {
            //Movimento al punto iniziale posizionamento
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            ExaxisPos exaxisPos(0, 0, 0, 0);
            DescPose offdese(0, 0, 0, 0, 0, 0);
            DescTran directionPoint;
            robot.MoveL(&startjointPos, &startdescPose, 1, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);

            //Inizio posizionamento direzione -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            //Se posizionamento riuscito
            if (ret == 0)
            {
                //Movimento al punto posizionamento
                robot.MoveToLaserSeamPos(1, 30, 0, 0, 0, offdese);
                //Inizio tracciamento laser lungo punto posizionamento
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.MoveL(&endjointPos, &enddescPose, 1, 0, 20, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
                //Ferma tracciamento
                robot.LaserTrackingTrackOnOff(0, 2);

            }
            cnt++;
        }
        robot.CloseRPC();
    }

Esempio codice tracciamento laser sincronizzato con assi estesi e robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    void testLasertrackandExitAxis()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        uint8_t ctrl[20];
        uint8_t state;
        int pressVlaue;
        int error;
        robot.CloseRPC();
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        int rtn = robot.RPC("192.168.58.2");

        if (rtn != 0)
        {
            return;
        }
        robot.SetReConnectParam(true, 30000, 500);

        ExaxisPos startexaxisPos = { 0,0,0,0 };
        ExaxisPos seamexaxisPos = { -10,0,0,0 };
        ExaxisPos endexaxisPos = { -30, 0, 0, 0 };
        DescPose offdese = { 0, 0, 0, 0, 0, 0 };
        JointPos seamjointPos(0, 0, 0, 0, 0, 0);
        DescPose seamdescPose(0, 0, 0, 0, 0, 0);
        
        int cnt = 1;
        while (cnt < 31)
        {
            //Movimento al punto iniziale posizionamento
            JointPos startjointPos(58.337, -119.628, 146.037, -116.358, -92.224, -117.654);
            DescPose startdescPose(-53.375, -255.363, 0.919, 178.054, 1.077, -94.026);
            robot.ExtAxisSyncMoveJ(startjointPos, startdescPose, 1, 0, 100, 100, 100, startexaxisPos, -1, 0, offdese);

            //Inizio posizionamento direzione -y
            int ret = robot.LaserTrackingSearchStart_xyz(3, 100, 300, 1000, 2);
            robot.LaserTrackingSearchStop();
            int tool = 0;
            int user = 0;
            robot.GetLaserSeamPos(0, offdese, seamjointPos, seamdescPose, tool, user, startexaxisPos);
            printf("%f, %f, %f,%f, %f, %f,%f, %f, %f,%f, %f, %f\n", seamjointPos.jPos[0], seamjointPos.jPos[1], seamjointPos.jPos[2], seamjointPos.jPos[3], seamjointPos.jPos[4], seamjointPos.jPos[5], seamdescPose.tran.x, seamdescPose.tran.y, seamdescPose.tran.z, seamdescPose.rpy.rx, seamdescPose.rpy.ry, seamdescPose.rpy.rz);

            //Se posizionamento riuscito
            if (ret == 0)
            {
                //Movimento sincrono robot e assi estesi al punto posizionamento
                robot.ExtAxisSyncMoveJ(seamjointPos, seamdescPose, 1, 0, 100, 100, 100, seamexaxisPos, -1, 0, offdese);

                //Inizio tracciamento laser lungo punto posizionamento e movimento sincrono con assi estesi
                robot.LaserTrackingTrackOnOff(1, 2);
                JointPos endjointPos(70.580, -90.918, 126.593, -125.154, -92.162, -105.403);
                DescPose enddescPose(-53.375, -419.020, 0.920, 178.054, 1.076, -94.026);
                robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 0, 20, 100, 100, -1, endexaxisPos, 0, offdese);;
                //Ferma tracciamento
                robot.LaserTrackingTrackOnOff(0, 2);
            }
            cnt++;
            printf("Tracciamento laser sincronizzato con assi estesi e robot  第%d次\n", cnt);
        }
        robot.CloseRPC();
    }

Abilita/Disabilita Funzione di Trasmissione Trasparente dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Abilita/disabilita la funzione di trasmissione trasparente dell'end-effector
    * @param [in] abilitazione, 0-disabilita, 1-abilita
    * @return Codice di errore
    */
    errno_t SetAxleGenComEnable(int mode);
                                                            
Trasmissione e Ricezione Dati Non Periodici della Funzione di Trasmissione Trasparente dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Trasmissione e ricezione dati non periodici della funzione di trasmissione trasparente dell'end-effector
    * @param [in] len_snd Lunghezza dei dati da inviare
    * @param [in] sndBuff Dati da inviare
    * @param [in] len_rcv Lunghezza dei dati da ricevere
    * @param [out] rcvBuff Dati di risposta
    * @return Codice di errore
    */
    errno_t SndRcvAxleGenComCmdData(int lenSnd, int sndBuff[130], int lenRcv, int rcvData[130]);
                                                                
Esempio di Codice per Comunicazione Dati Non Periodici del DIO Health Care Moxibustion Head basato sulla Funzione di Trasmissione Trasparente dell'End-Effector
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int testAxleGenCom()
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
      int led_on[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x01, 0x79 };
      int led_off[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int version[5] = { 0xAB, 0xBA, 0x11, 0x00, 0x76 };
      int state[6] = { 0xAB, 0xBA, 0x1B, 0x01, 0xAA, 0x2B };
      int cycleState[6] = { 0xAB, 0xBA, 0x12, 0x01, 0x00, 0x78 };
      int rcvdata[16] = {0};
      int ret = 0;
      int cnt = 1;
      JointPos p1Joint(88.708, -86.178, 140.989, -141.825, -89.162, -49.879);
      DescPose p1Desc(188.007, -377.850, 260.207, 178.715, 2.823, -131.466);
      JointPos p2Joint(112.131, -75.554, 126.989, -139.027, -88.044, -26.477);
      DescPose p2Desc(368.003, -377.848, 260.211, 178.715, 2.823, -131.465);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 0, 0, 0, 0);
      //Abilita la funzione di trasmissione trasparente dell'end-effector
      robot.SetAxleGenComEnable(1);
      robot.SetAxleLuaEnable(1);
      while (cnt <= 10000)
      {
        //Legge il numero di versione
        ret = robot.SndRcvAxleGenComCmdData(5, version, 10, rcvdata);
        printf(" hard version : %d,hard code:%d, soft version:%d %d, soft code:%d \n", rcvdata[4], rcvdata[5], rcvdata[6] ,rcvdata[7], rcvdata[8]);
        if (ret != 0)
        {
          break;
        }
        robot.Sleep(1000);
        //Legge lo stato di presenza della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, state, 6, rcvdata);
        printf(" state : %d \n", rcvdata[4]);
        robot.Sleep(1000);
        //Accende il laser della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, led_on, 6, rcvdata);
        printf("led on rcv data is: %d, %d, %d, %d, %d, %d  \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(4000);
        //Spegne il laser della testa di moxibustione
        ret = robot.SndRcvAxleGenComCmdData(6, led_off, 6, rcvdata);
        printf("led off rcv data is: %d, %d, %d, %d, %d, %d \n", rcvdata[0], rcvdata[1], rcvdata[2], rcvdata[3], rcvdata[4], rcvdata[5]);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.Sleep(1000);
        printf("***********************complate No. %d SDK test*****************************\n", cnt);
        cnt++;
      }
      robot.CloseRPC();
    }

Scarica File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Scarica file Lua di protocollo aperto
    * @param [in] fileName Nome del file di protocollo aperto "CtrlDev_XXX.lua"
    * @param [in] savePath Percorso di salvataggio del file di protocollo aperto
    * @return Codice di errore
    */
    errno_t OpenLuaDownload(std::string fileName, std::string savePath);
    
Elimina File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Elimina file Lua di protocollo aperto
    * @param [in] fileName Nome del file Lua di protocollo aperto da eliminare "CtrlDev_XXX.lua"
    * @return Codice di errore
    */
    errno_t OpenLuaDelete(std::string fileName);
        
Elimina Tutti i File Lua di Protocollo Aperto
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Elimina tutti i file Lua di protocollo aperto
    * @return Codice di errore
    */
    errno_t AllOpenLuaDelete();

Esempio di Codice per Caricamento, Download ed Eliminazione di Protocollo Aperto per Periferiche del Controller
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestCtrlOpenLuaOperate()
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
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_WELDING_A.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaUpload("D://zUP/openlua/CtrlDev_SWDPOLISH.lua");
        printf("OpenLuaUpload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_WELDING_A.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.OpenLuaDownload("CtrlDev_SWDPOLISH.lua", "D://zDOWN/");
        printf("OpenLuaDownload rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(0, "CtrlDev_WELDING_A.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        rtn = robot.SetCtrlOpenLUAName(1, "CtrlDev_SWDPOLISH.lua");
        printf("SetCtrlOpenLUAName rtn is %d\n", rtn);
        std::string name[4] = {};
        rtn = robot.GetCtrlOpenLUAName(name);
        printf("ctrl open lua names : %s, %s, %s, %s\n", name[0].c_str(), name[1].c_str(), name[2].c_str(), name[3].c_str());
        rtn = robot.LoadCtrlOpenLUA(1);
        printf("LoadCtrlOpenLUA rtn is %d\n", rtn);
        robot.Sleep(2000);
        rtn = robot.UnloadCtrlOpenLUA(1);
        printf("UnloadCtrlOpenLUA rtn is %d\n", rtn);
        rtn = robot.OpenLuaDelete("CtrlDev_WELDING_A.lua");
        printf("OpenLuaDelete rtn is %d\n", rtn);
        rtn = robot.AllOpenLuaDelete();
        printf("AllOpenLuaDelete rtn is %d\n", rtn);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }

Controllo del Movimento della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controllo del movimento della mano destra
    * @param [in] idstart Numero stazione slave iniziale
    * @param [in] slaveNum Numero di slave
    * @param [in] pos Array di posizioni, lunghezza 16, intervallo (-360~360)
    * @param [in] speed Array di percentuali di velocità, lunghezza 16, intervallo [0~100]
    * @param [in] force Array di percentuali di coppia, lunghezza 16, intervallo [0~100]
    * @param [in] max_time Tempo massimo di attesa, intervallo [0~30000], unità ms
    * @return Codice errore, 0 in caso di successo
    */
    errno_t SetDexterousHandsMove(int idstart, int slaveNum, double pos[16], int speed[16], int force[16], int max_time);
        
Controllo del Reset e Attivazione della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controllo del reset e attivazione della mano destra
    * @param [in] id Numero stazione slave
    * @param [in] act 0-reset 1-attivazione
    * @return Codice errore, 0 in caso di successo
    */
    errno_t SetDexterousHandsAct(int id, int act);
            
Cancellazione dell'Errore della Mano Destra
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Cancellazione dell'errore della mano destra
    * @return Codice errore, 0 in caso di successo
    */
    errno_t ClearDexterousHandsError();
                
Impostazione delle Funzioni di Controllo Azione Mano Destra Abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta le funzioni di controllo azione mano destra abilitate
    * @param [in] id Numero dispositivo mano destra
    * @param [in] func 0-attivazione presa, 1-inizializzazione pinza, 2-impostazione posizione, 3-impostazione velocità, 4-impostazione coppia, 6-lettura stato pinza, 7-lettura stato inizializzazione, 8-lettura codice guasto, 9-lettura posizione, 10-lettura velocità, 11-lettura coppia, 12-impostazione giri rotazione, 13-impostazione velocità rotazione, 14-impostazione coppia rotazione, 15-lettura stato pinza rotante, 16-lettura stato inizializzazione rotazione, 17-lettura giri rotazione, 18-lettura velocità rotazione, 19-lettura coppia rotazione, 20-impostazione movimento sincrono multiasse, 21-comando clear guasti, 22-stato funzionamento singolo asse, 23-stato funzionamento tutti gli assi
    * @return Codice errore
    */
    errno_t SetDexterousHandsFunc(int id, int func[32]);
                    
Ottenimento delle Funzioni di Controllo Azione Mano Destra Abilitate
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene le funzioni di controllo azione mano destra abilitate
    * @param [in] id Numero dispositivo mano destra
    * @param [out] func 0-attivazione presa, 1-inizializzazione pinza, 2-impostazione posizione, 3-impostazione velocità, 4-impostazione coppia, 6-lettura stato pinza, 7-lettura stato inizializzazione, 8-lettura codice guasto, 9-lettura posizione, 10-lettura velocità, 11-lettura coppia, 12-impostazione giri rotazione, 13-impostazione velocità rotazione, 14-impostazione coppia rotazione, 15-lettura stato pinza rotante, 16-lettura stato inizializzazione rotazione, 17-lettura giri rotazione, 18-lettura velocità rotazione, 19-lettura coppia rotazione, 20-impostazione movimento sincrono multiasse, 21-comando clear guasti, 22-stato funzionamento singolo asse, 23-stato funzionamento tutti gli assi
    * @return Codice errore
    */
    errno_t GetDexterousHandsFunc(int id, int func[32]);
                        
Esempio di Codice per Configurazione e Movimento della Mano Destra sull'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestDexterousHands()
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
    int id = 1;        // Numero stazione slave
    int slaveNum = 4;     // Controlla 4 dita
    int max_time = 8000;   // Tempo massimo di attesa 8 secondi
    int speed[16] = {0};   // Array velocità, tutti 0 significa usa velocità predefinita
    int force[16] = {0};   // Array coppia
    // Inizializza array coppia: prime 4 dita impostate al 50%, il resto 0 (valori inviati tramite comando Move)
    for (int i = 0; i < 16; i++)
    {
        force[i] = (i < 4) ? 50 : 0;
    }
    // Funzione helper: imposta array posizione (solo prime 4 dita sono efficaci)
    double pos[16] = {0.0};
    JointPos j1(-91.876, -85.920, 109.279, -86.239, -96.664, -28.563);
    JointPos j2(-40.954, -85.920, 109.279, -86.239, -96.664, -28.563);
    ExaxisPos epos(0, 0, 0, 0);
    DescPose offset_pos(0, 0, 0, 0, 0, 0);
    printf("===== Test completo funzionalità mano destra avviato =====\n");
    // 1. Cancella errore
    int ret = robot.ClearDexterousHandsError();
    printf("ClearDexterousHandsError rtn %d\n", ret);
    // ========== 2. Imposta interruttori funzione ==========
    int setFunc[32] = {0};
    setFunc[2] = 1;  // Abilita funzione impostazione posizione
    setFunc[4] = 1;  // Abilita funzione impostazione coppia
    setFunc[9] = 1;  // Lettura posizione
    setFunc[10] = 1;  // Lettura coppia
    setFunc[11] = 1;  // Lettura stato
    setFunc[22] = 1;  // Stato movimento singolo asse
    ret = robot.SetDexterousHandsFunc(id, setFunc);
    printf("SetDexterousHandsFunc(abilitazione init + funzioni posizione/coppia) rtn %d\n", ret);
    // ========== 3. Legge stato funzione (verifica che le impostazioni siano state applicate) ==========
    int getFunc[32] = {0}; // GetDexterousHandsFunc restituisce 32 interi
    ret = robot.GetDexterousHandsFunc(id, getFunc);
    printf("GetDexterousHandsFunc rtn %d\n", ret);
    if (ret == 0)
    {
        // Stampa tutti i 32 valori
        printf("Tutti i 32 valori restituiti da GetDexterousHandsFunc:");
        for (int i = 0; i < 32; i++)
        {
        printf(" [%d]={%d}", i, getFunc[i]);
        if ((i + 1) % 8 == 0)
        {
            printf("\n");
        } 
        else if (i < 31)
        {
            printf(", ");
        }
        }
    }
    // ========== 4. Attiva mano destra ==========
    ret = robot.SetDexterousHandsAct(id, 1);
    printf("SetDexterousHandsAct(attivazione) rtn %d\n", ret);
    if (ret != 0)
    {
        printf("Attivazione fallita, test interrotto");
        return -1;
    }
    // ========== 5. Movimento iniziale a 20° (invia valori di posizione e coppia tramite comando Move) ==========
    memset(pos, 0, sizeof(pos));
    pos[0] = 20;
    pos[1] = 20;
    pos[2] = 20;
    pos[3] = 20;
    ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
    printf("Movimento iniziale a 20° -> %d\n", ret);
    robot.Sleep(5000);
    // ========== 6. Movimento alternato 10 volte (10° ↔ 50°) ==========
    printf("Avvio 10 movimenti alternati...");
    for (int iteration = 1; iteration <= 10; iteration++)
    {
        robot.MoveJ(&j1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        memset(pos, 0, sizeof(pos));
        pos[0] = 10;
        pos[1] = 10;
        pos[2] = 10;
        pos[3] = 10;
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        printf("Movimento a 10° -> %d\n", ret);
        robot.Sleep(1000);
        robot.MoveJ(&j2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        memset(pos, 0, sizeof(pos));
        pos[0] = 50;
        pos[1] = 50;
        pos[2] = 50;
        pos[3] = 50;
        ret = robot.SetDexterousHandsMove(id, slaveNum, pos, speed, force, max_time);
        printf("Movimento a 50° -> %d\n", ret);
        robot.Sleep(1000);
    }
    printf("Test completato (impostazione/lettura interruttori funzione + attivazione + 10 movimenti alternati).");
    return 0;
    }    