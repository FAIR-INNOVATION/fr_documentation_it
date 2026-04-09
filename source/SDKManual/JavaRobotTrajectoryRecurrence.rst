Riproduzione Traiettoria Robot
=================================

.. toctree:: 
    :maxdepth: 5

Impostare parametri registrazione traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Impostare parametri registrazione traiettoria TPD
    * @param  [in] type  tipo dati registrati, 1-posizione giunti
    * @param  [in] name  nome file traiettoria
    * @param  [in] period_ms  periodo campionamento dati, valore fisso 2ms o 4ms o 8ms
    * @param  [in] di_choose  selezione DI, bit0~bit7 corrispondono DI0~DI7 controllo box, bit8~bit9 corrispondono DI0~DI1 terminale, 0-non selezionare, 1-selezionare
    * @param  [in] do_choose  selezione DO, bit0~bit7 corrispondono DO0~DO7 controllo box, bit8~bit9 corrispondono DO0~DO1 terminale, 0-non selezionare, 1-selezionare
    * @return  Codice errore
    */
    int SetTPDParam(int type, String name, int period_ms, int di_choose, int do_choose);

Avviare registrazione traiettoria TPD
++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Avviare registrazione traiettoria TPD
    * @param  [in] type  tipo dati registrati, 1-posizione giunti
    * @param  [in] name  nome file traiettoria
    * @param  [in] period_ms  periodo campionamento dati, valore fisso 2ms o 4ms o 8ms
    * @param  [in] di_choose  selezione DI, bit0~bit7 corrispondono DI0~DI7 controllo box, bit8~bit9 corrispondono DI0~DI1 terminale, 0-non selezionare, 1-selezionare
    * @param  [in] do_choose  selezione DO, bit0~bit7 corrispondono DO0~DO7 controllo box, bit8~bit9 corrispondono DO0~DO1 terminale, 0-non selezionare, 1-selezionare
    * @return  Codice errore
    */
    int SetTPDStart(int type, String name, int period_ms, int di_choose, int do_choose);

Fermare registrazione traiettoria TPD
++++++++++++++++++++++++++++++++++++++
.. code-block:: java
    :linenos:

    /**
    * @brief  Fermare registrazione traiettoria TPD
    * @return  Codice errore
    */
    int SetWebTPDStop(); 

Eliminare registrazione traiettoria TPD
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Eliminare registrazione traiettoria TPD
    * @param  [in] name  nome file traiettoria
    * @return  Codice errore
    */   
    int SetTPDDelete(string name); 

Precaricamento traiettoria TPD
+++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Precaricamento traiettoria
    * @param  [in] name  nome file traiettoria
    * @return  Codice errore
    */      
    int LoadTPD(String name);

Riproduzione traiettoria TPD
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Riproduzione traiettoria
    * @param  [in] name  nome file traiettoria
    * @param  [in] blend 0-non smoothing, 1-smoothing
    * @param  [in] ovl  percentuale scala velocità, range [0~100]
    * @return  Codice errore
    */
    int MoveTPD(String name, int blend, double ovl); 

Ottenere posa iniziale TPD
+++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere posa iniziale traiettoria 
    * @param [in] name  nome file traiettoria, non richiede estensione file
    * @param [out] desc_pose posa iniziale traiettoria ottenuta
    * @return Codice errore 
    */ 
    int GetTPDStartPose(String name, DescPose desc_pose); 

Esempio codice registrazione traiettoria TPD robot
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTPD(Robot robot)
    {
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        double ovl = 100.0;
        int blend = 0;

        DescPose start_pose =new DescPose() {};

        int rtn = robot.LoadTPD(name);
        System.out.println("LoadTPD rtn is:"+ rtn);

        robot.GetTPDStartPose(name, start_pose);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        robot.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.println("MoveTPD rtn is: "+ rtn);
        robot.Sleep(5000);

        robot.SetTPDDelete(name);
        return 0;
    }

Pre-elaborazione traiettoria
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Pre-elaborazione file traiettoria esterno 
    * @param [in] name nome file traiettoria  
    * @param [in] ovl percentuale scala velocità, range [0~100]
    * @param [in] opt 1-punto controllo, default 1 
    * @return Codice errore 
    */ 
    int LoadTrajectoryJ(String name, double ovl, int opt); 

Riproduzione traiettoria
++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Riproduzione file traiettoria esterno  
    * @return Codice errore 
    */
    int MoveTrajectoryJ();

Ottenere posa iniziale traiettoria
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottenere posa iniziale traiettoria 
    * @param [in] name nome file traiettoria  
    * @param [out] desc_pose posa iniziale traiettoria ottenuta
    * @return Codice errore 
    */ 
    int GetTrajectoryStartPose(String name, DescPose desc_pose);

Ottenere numero punti traiettoria
++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottenere numero punti traiettoria
    * @return  Codice errore
    */
    public int GetTrajectoryPointNum(int pnum)

Impostare velocità durante esecuzione traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Impostare velocità durante esecuzione traiettoria
    * @param  [in] ovl percentuale velocità
    * @return  Codice errore
    */
    public int SetTrajectoryJSpeed(double ovl)

Impostare forza e coppia durante esecuzione traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Impostare forza e coppia durante esecuzione traiettoria
    * @param  [in] ft forza e coppia tre direzioni, unità N e Nm
    * @return  Codice errore
    */
    public int SetTrajectoryJForceTorque(ForceTorque ft)

Impostare forza direzione x durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare forza direzione x durante esecuzione traiettoria  
    * @param [in] fx forza direzione x, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFx(double fx);

Impostare forza direzione y durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare forza direzione y durante esecuzione traiettoria
    * @param [in] fy forza direzione y, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFy(double fy);

Impostare forza direzione z durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare forza direzione z durante esecuzione traiettoria  
    * @param [in] fz  forza direzione z, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFz(double fz);

Impostare coppia asse x durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare coppia asse x durante esecuzione traiettoria  
    * @param [in] tx coppia asse x, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTx(double tx);

Impostare coppia asse y durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare coppia asse y durante esecuzione traiettoria  
    * @param [in] ty coppia asse y, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTy(double ty);

Impostare coppia asse z durante esecuzione traiettoria
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Impostare coppia asse z durante esecuzione traiettoria  
    * @param [in] tz coppia asse z, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTz(double tz);

Upload file traiettoria J
++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Upload file traiettoria J  
    * @param [in] filePath percorso completo file traiettoria upload   C://test/testJ.txt
    * @return Codice errore 
    */
    int TrajectoryJUpLoad(String filePath);

Eliminare file traiettoria J
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Eliminare file traiettoria J  
    * @param [in] fileName nome file testJ.txt
    * @return Codice errore 
    */
    int TrajectoryJDelete(String fileName);

Esempio codice riproduzione file traiettoria J robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTraj(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");
        System.out.println("Upload TrajectoryJ A :"+ rtn);

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        System.out.println("LoadTrajectoryJ:"+traj_file_name+", rtn is:"+ rtn);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);


        ExaxisPos epos=new ExaxisPos(0,0,0,0);
        DescPose po=new DescPose(0,0,0,0,0,0);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0);
        System.out.println("SetTrajectoryJSpeed is:"+ rtn);

        ForceTorque traj_force=new ForceTorque(0,0,0,0,0,0);
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        System.out.println("SetTrajectoryJForceTorque rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0);
        System.out.println("SetTrajectoryJForceFx rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0);
        System.out.println("SetTrajectoryJForceFy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0);
        System.out.println("SetTrajectoryJForceFz rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0);
        System.out.println("SetTrajectoryJTorqueTx rtn is: "+ rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0);
        System.out.println("SetTrajectoryJTorqueTy rtn is:"+ rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0);
        System.out.println("SetTrajectoryJTorqueTz rtn is:"+ rtn);

        rtn = robot.MoveTrajectoryJ();
        System.out.println("MoveTrajectoryJ rtn is: "+ rtn);

        return 0;
    }

Pre-elaborazione traiettoria (lookahead traiettoria)
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Pre-elaborazione traiettoria (lookahead traiettoria) 
    * @param [in] name  nome file traiettoria
    * @param [in] mode modalità campionamento, 0-non campionare; 1-campionamento intervallo dati uguale; 2-campionamento limite errore uguale
    * @param [in] errorLim limite errore, effettivo con interpolazione lineare
    * @param [in] type modalità smoothing, 0-smoothing Bezier
    * @param [in] precision precisione smoothing, effettivo con smoothing Bezier
    * @param [in] vamx velocità massima impostata, mm/s
    * @param [in] amax accelerazione massima impostata, mm/s2
    * @param [in] jmax jerk massimo impostato, mm/s3
    * @return Codice errore 
    */ 
    int LoadTrajectoryLA(String name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax); 

Riproduzione traiettoria (lookahead traiettoria)
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.3-3.8.0

.. code-block:: Java
    :linenos:

    /** 
    * @brief Riproduzione traiettoria (lookahead traiettoria)  
    * @return Codice errore 
    */
    int MoveTrajectoryLA();

Esempio codice riproduzione traiettoria (lookahead traiettoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadTrajLA(Robot robot)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/traj.txt");

        String traj_file_name = "/fruser/traj/traj.txt";
        rtn = robot.LoadTrajectoryLA(traj_file_name, 1, 2, 0, 2, 100, 200, 1000);

        DescPose traj_start_pose=new DescPose(0,0,0,0,0,0);
        rtn = robot.GetTrajectoryStartPose(traj_file_name, traj_start_pose);

        robot.Sleep(1000);
        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        rtn = robot.MoveTrajectoryLA();

        robot.CloseRPC();
        return 0;
    }

Spostarsi al Punto di Inizio della Registrazione della Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Spostarsi al punto di inizio della registrazione della traiettoria TPD
    * @param name Nome del file di traiettoria
    * @param moveType Tipo di movimento; 0-PTP; 1-LIN
    * @param ovl Percentuale di scala della velocità, intervallo [0~100]
    * @return Codice di errore
    */
    public int MoveToTPDStart(string name, int moveType, double ovl)

Esempio di Codice SDK per Spostarsi al Punto di Inizio della Registrazione della Traiettoria TPD
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void testTPDmove (Robot robot)
    {
        int rtn = 0;
        int type = 1;
        String name = "tpd2025";
        int period_ms = 4;
        int di_choose = 0;
        int do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        robot.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        robot.Sleep(3000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        robot.Sleep(1000);
        double ovl = 100.0;
        int blend = 0;
        DescPose start_pose = new DescPose();
        rtn = robot.LoadTPD(name);
        System.out.printf("LoadTPD rtn is: %d\n", rtn);

        robot.GetTPDStartPose(name, start_pose);
        System.out.printf("start pose, xyz is: %f %f %f. rpy is: %f %f %f \n", start_pose.tran.x, start_pose.tran.y, start_pose.tran.z, start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        //robot.MoveCart(&start_pose, 0, 0, 100, 100, ovl, -1, -1);
        //robot.Sleep(1000);

        rtn = robot.MoveToTPDStart(name, 0, 100);
        System.out.printf("MoveToTPDStart rtn is: %d\n", rtn);

        rtn = robot.MoveTPD(name, blend, ovl);
        System.out.printf("MoveTPD rtn is: %d\n", rtn);

        robot.Sleep(5000);

        robot.SetTPDDelete(name);

        return ;
    }