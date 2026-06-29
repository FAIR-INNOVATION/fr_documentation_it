Riproduzione Traiettoria Robot
============================================

.. toctree:: 
    :maxdepth: 5

Impostare i parametri di registrazione traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta i parametri di registrazione traiettoria TPD
    * @param  [in] type  Tipo dati registrazione, 1-Posizione giunti
    * @param  [in] name  Nome file traiettoria
    * @param  [in] period_ms  Periodo campionamento dati, valore fisso 2ms o 4ms o 8ms
    * @param  [in] di_choose  Selezione DI, bit0~bit7 corrisponde a control box DI0~DI7, bit8~bit9 corrisponde a terminale DI0~DI1, 0-Non selezionato, 1-Selezionato
    * @param  [in] do_choose  Selezione DO, bit0~bit7 corrisponde a control box DO0~DO7, bit8~bit9 corrisponde a terminale DO0~DO1, 0-Non selezionato, 1-Selezionato
    * @return  Codice di errore
    */
    errno_t  SetTPDParam(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose);

Iniziare la registrazione traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inizia la registrazione traiettoria TPD
    * @param  [in] type  Tipo dati registrazione, 1-Posizione giunti
    * @param  [in] name  Nome file traiettoria
    * @param  [in] period_ms  Periodo campionamento dati, valore fisso 2ms o 4ms o 8ms
    * @param  [in] di_choose  Selezione DI, bit0~bit7 corrisponde a control box DI0~DI7, bit8~bit9 corrisponde a terminale DI0~DI1, 0-Non selezionato, 1-Selezionato
    * @param  [in] do_choose  Selezione DO, bit0~bit7 corrisponde a control box DO0~DO7, bit8~bit9 corrisponde a terminale DO0~DO1, 0-Non selezionato, 1-Selezionato
    * @return  Codice di errore
    */
    errno_t  SetTPDStart(int type, char name[30], int period_ms, uint16_t di_choose, uint16_t do_choose); 

Fermare la registrazione traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ferma la registrazione traiettoria TPD
    * @return  Codice di errore
    */
    errno_t  SetWebTPDStop();

Eliminare la registrazione traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Elimina la registrazione traiettoria TPD
    * @param  [in] name  Nome file traiettoria
    * @return  Codice di errore
    */   
    errno_t  SetTPDDelete(char name[30]);

Precaricamento traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Precaricamento traiettoria TPD
    * @param  [in] name  Nome file traiettoria
    * @return  Codice di errore
    */      
    errno_t  LoadTPD(char name[30]);

Riproduzione traiettoria TPD
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Riproduzione traiettoria TPD
    * @param  [in] name  Nome file traiettoria
    * @param  [in] blend 0-Non smoothing, 1-Smoothing
    * @param  [in] ovl  Percentuale scala velocità, intervallo [0~100]
    * @return  Codice di errore
    */
    errno_t  MoveTPD(char name[30], uint8_t blend, float ovl);

Ottenere la posa iniziale TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la posa iniziale TPD
     * @param  [in] name Nome file TPD, non necessita estensione file
     * @return  Codice di errore
     */     
    errno_t  GetTPDStartPose(char name[30], DescPose *desc_pose);

Spostarsi al Punto di Inizio della Registrazione della Traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Spostarsi al punto di inizio della registrazione della traiettoria TPD
    * @param [in] name Nome del file di traiettoria
    * @param [in] moveType Tipo di movimento; 0-PTP; 1-LIN
    * @param [in] ovl Percentuale di scala della velocità, intervallo [0~100]
    * @return Codice di errore
    */
    errno_t MoveToTPDStart(char name[30], uint8_t moveType, float ovl);
    
Esempio di Codice per la Registrazione della Traiettoria TPD del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
    int type = 1;
    char name[30] = "tpd2025";
    int period_ms = 4;
    uint16_t di_choose = 0;
    uint16_t do_choose = 0;
    robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
    robot.Mode(1);
    robot.Sleep(1000);
    robot.DragTeachSwitch(1);
    robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
    robot.Sleep(3000);
    robot.SetWebTPDStop();
    robot.DragTeachSwitch(0);
    robot.Sleep(1000);
    float ovl = 100.0;
    uint8_t blend = 0;
    DescPose start_pose = {};
    rtn = robot.LoadTPD(name);
    printf("LoadTPD rtn is: %d\n", rtn);
    robot.GetTPDStartPose(name, &start_pose);
    printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
    rtn = robot.MoveToTPDStart(name, 0, 100);
    printf("MoveToTPDStart rtn is: %d\n", rtn);
    rtn = robot.MoveTPD(name, blend, ovl);
    printf("MoveTPD rtn is: %d\n", rtn);
    std::this_thread::sleep_for(std::chrono::milliseconds(5000));
    robot.SetTPDDelete(name);
    robot.CloseRPC();
    return 0;
    }

Esempio di codice per registrazione traiettoria TPD robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTPD(void)
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
      int type = 1;
      char name[30] = "tpd2025";
      int period_ms = 4;
      uint16_t di_choose = 0;
      uint16_t do_choose = 0;
      robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);
      robot.Mode(1);
      robot.Sleep(1000);
      robot.DragTeachSwitch(1);
      robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
      robot.Sleep(10000);
      robot.SetWebTPDStop();
      robot.DragTeachSwitch(0);
      float ovl = 100.0;
      uint8_t blend = 0;
      DescPose start_pose = {};
      rtn = robot.LoadTPD(name);
      printf("LoadTPD rtn is: %d\n", rtn);
      robot.GetTPDStartPose(name, &start_pose);
      printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
      robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
      robot.Sleep(1000);
      rtn = robot.MoveTPD(name, blend, ovl);
      printf("MoveTPD rtn is: %d\n", rtn);
      std::this_thread::sleep_for(std::chrono::milliseconds(5000));
      robot.SetTPDDelete(name);
      robot.CloseRPC();
      return 0;
    }

Pre-elaborazione traiettoria
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Pre-elaborazione traiettoria
     * @param  [in] name  Nome file traiettoria
     * @param  [in] ovl Percentuale scala velocità, intervallo [0~100]
     * @param  [in] opt 1-Punto di controllo, predefinito 1
     * @return  Codice di errore
     */     
    errno_t  LoadTrajectoryJ(char name[30], float ovl, int opt);

Riproduzione traiettoria
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Riproduzione traiettoria
     * @return  Codice di errore
     */     
    errno_t  MoveTrajectoryJ();

Ottenere la posa iniziale della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene la posa iniziale della traiettoria
     * @param  [in] name Nome file traiettoria
     * @return  Codice di errore
     */     
    errno_t  GetTrajectoryStartPose(char name[30], DescPose *desc_pose);

Ottenere il numero di punti della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Ottiene il numero di punti della traiettoria
     * @return  Codice di errore
     */     
    errno_t  GetTrajectoryPointNum(int *pnum);

Impostare la Velocità Durante l'Esecuzione della Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Impostare la velocità durante l'esecuzione della traiettoria
    * @param [in] ovl Percentuale di velocità [0-100.0]
    * @param [in] mode Modalità; 0-modalità di riduzione della velocità; 1-commutazione diretta
    * @return Codice di errore
    */
    errno_t SetTrajectoryJSpeed(float ovl, int mode = 0);

Esempio di Codice per Impostare la Velocità del Robot Durante l'Esecuzione della Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSetTrajectoryJSpeed() 
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return -1;
        }
        
        rtn = robot.TrajectoryJUpLoad("D://zUP/horse.txt");
        printf("Upload TrajectoryJ A %d\n", rtn);
        char traj_file_name[90] = "horse.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
        DescPose traj_start_pose;
        memset(&traj_start_pose, 0, sizeof(DescPose));
        rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
        printf("GetTrajectoryStartPose is: %d\n", rtn);
        printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
        std::this_thread::sleep_for(std::chrono::seconds(1));
        robot.SetSpeed(50);
        robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(&traj_num);
        printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
        rtn = robot.MoveTrajectoryJ();
        printf("MoveTrajectoryJ rtn is: %d\n", rtn);
        robot.Sleep(1000);
        robot.GetRobotRealTimeState(&pkg);
        int trajspeedMode = 1;
        while (pkg.motion_done == 0)
        {
            robot.GetRobotRealTimeState(&pkg);
            rtn = robot.SetTrajectoryJSpeed(10.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
            rtn = robot.SetTrajectoryJSpeed(80.0, trajspeedMode);
            printf("SetTrajectoryJSpeed is: %d\n", rtn);
            robot.Sleep(1000);
        }
        robot.CloseRPC();
        robot.Sleep(1000000);
        return 0;
    }

Impostare forza e coppia durante la riproduzione della traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta forza e coppia durante la riproduzione della traiettoria
     * @param  [in] ft Forza e coppia in tre direzioni, unità N e Nm
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJForceTorque(ForceTorque *ft);

Impostare la forza lungo la direzione x durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la forza lungo la direzione x durante la riproduzione della traiettoria
     * @param  [in] fx Forza lungo direzione x, unità N
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJForceFx(double fx);

Impostare la forza lungo la direzione y durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la forza lungo la direzione y durante la riproduzione della traiettoria
     * @param  [in] fy Forza lungo direzione y, unità N
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJForceFy(double fy);

Impostare la forza lungo la direzione z durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la forza lungo la direzione z durante la riproduzione della traiettoria
     * @param  [in] fz Forza lungo direzione x, unità N
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJForceFz(double fz);

Impostare la coppia attorno all'asse x durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la coppia attorno all'asse x durante la riproduzione della traiettoria
     * @param  [in] tx Coppia attorno asse x, unità Nm
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJTorqueTx(double tx);

Impostare la coppia attorno all'asse y durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la coppia attorno all'asse y durante la riproduzione della traiettoria
     * @param  [in] ty Coppia attorno asse y, unità Nm
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJTorqueTy(double ty);

Impostare la coppia attorno all'asse z durante la riproduzione della traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief  Imposta la coppia attorno all'asse z durante la riproduzione della traiettoria
     * @param  [in] tz Coppia attorno asse z, unità Nm
     * @return  Codice di errore
     */     
    errno_t  SetTrajectoryJTorqueTz(double tz);

Caricare file traiettoria J
+++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Carica file traiettoria J
     * @param [in] filePath Nome percorso completo file traiettoria da caricare   C://test/testJ.txt
     * @return Codice di errore
     */
    errno_t TrajectoryJUpLoad(const std::string& filePath);

Eliminare file traiettoria J
++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
     * @brief Elimina file traiettoria J
     * @param [in] fileName Nome file testJ.txt
     * @return Codice di errore
     */
    errno_t TrajectoryJDelete(const std::string& fileName);

Esempio di codice per riproduzione file traiettoria J robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestTraj(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj1.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj1.txt";
      rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
      printf("LoadTrajectoryJ %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      int traj_num = 0;
      rtn = robot.GetTrajectoryPointNum(&traj_num);
      printf("GetTrajectoryStartPose rtn is: %d, traj num is: %d\n", rtn, traj_num);
      rtn = robot.SetTrajectoryJSpeed(50.0);
      printf("SetTrajectoryJSpeed is: %d\n", rtn);
      ForceTorque traj_force;
      memset(&traj_force, 0, sizeof(ForceTorque));
      traj_force.fx = 10;
      rtn = robot.SetTrajectoryJForceTorque(&traj_force);
      printf("SetTrajectoryJForceTorque rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFx(10.0);
      printf("SetTrajectoryJForceFx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFy(0.0);
      printf("SetTrajectoryJForceFy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJForceFz(0.0);
      printf("SetTrajectoryJForceFz rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTx(10.0);
      printf("SetTrajectoryJTorqueTx rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTy(10.0);
      printf("SetTrajectoryJTorqueTy rtn is: %d\n", rtn);
      rtn = robot.SetTrajectoryJTorqueTz(10.0);
      printf("SetTrajectoryJTorqueTz rtn is: %d\n", rtn);
      rtn = robot.MoveTrajectoryJ();
      printf("MoveTrajectoryJ rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Pre-elaborazione traiettoria (traiettoria lookahead)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
     * @brief Pre-elaborazione traiettoria (traiettoria lookahead)
     * @param [in] name  Nome file traiettoria
     * @param [in] mode Modalità campionamento, 0-Non campionare; 1-Campionamento a intervalli dati uguali; 2-Campionamento con limite errore uguale
     * @param [in] errorLim Limite errore, efficace quando si usa interpolazione lineare
     * @param [in] type Metodo smoothing, 0-Smoothing Bezier
     * @param [in] precision Precisione smoothing, efficace quando si usa smoothing Bezier
     * @param [in] vamx Velocità massima impostata, mm/s
     * @param [in] amax Accelerazione massima impostata, mm/s2
     * @param [in] jmax Jerk massimo impostato, mm/s3
     * @param [in] flag Interruttore lookahead velocità costante 0-Non attivare; 1-Attivare
     * @return Codice di errore
     */
    errno_t LoadTrajectoryLA(char name[30], int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax, int flag = 0);

Riproduzione traiettoria (traiettoria lookahead)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    /**
    * @brief  Riproduzione traiettoria (traiettoria lookahead)
    * @return  Codice di errore
    */
    errno_t MoveTrajectoryLA();

Esempio di codice per riproduzione traiettoria (traiettoria lookahead)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLoadTrajLA(void)
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
      rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
      printf("Upload TrajectoryJ A %d\n", rtn);
      char traj_file_name[30] = "/fruser/traj/traj.txt";
      rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);
      printf("LoadTrajectoryLA %s, rtn is: %d\n", traj_file_name, rtn);
      DescPose traj_start_pose;
      memset(&traj_start_pose, 0, sizeof(DescPose));
      rtn = robot.GetTrajectoryStartPose(traj_file_name, &traj_start_pose);
      printf("GetTrajectoryStartPose is: %d\n", rtn);
      printf("desc_pos:%f,%f,%f,%f,%f,%f\n", traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z, traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);
      std::this_thread::sleep_for(std::chrono::seconds(1));
      robot.SetSpeed(50);
      robot.MoveCart(&traj_start_pose, 0, 0, 100, 100, 100, -1, -1);
      rtn = robot.MoveTrajectoryLA();
      printf("MoveTrajectoryLA rtn is: %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }