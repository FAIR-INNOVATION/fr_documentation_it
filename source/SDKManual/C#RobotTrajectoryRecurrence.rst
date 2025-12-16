Riproduzione Traiettoria Robot
============================================

.. toctree:: 
    :maxdepth: 5

Impostare Parametri Registrazione Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostare Parametri Registrazione Traiettoria TPD
    * @param  [in] type  Tipo dati registrazione, 1-posizione articolare
    * @param  [in] name  Nome file traiettoria
    * @param  [in] period_ms  Periodo campionamento dati, valori fissi 2ms o 4ms o 8ms
    * @param  [in] di_choose  Selezione DI, bit0~bit7 corrispondono DI0~DI7 quadro controllo, bit8~bit9 corrispondono DI0~DI1 estremità, 0-non selezionato, 1-selezionato
    * @param  [in] do_choose  Selezione DO, bit0~bit7 corrispondono DO0~DO7 quadro controllo, bit8~bit9 corrispondono DO0~DO1 estremità, 0-non selezionato, 1-selezionato
    * @return   Codice errore
    */
    int SetTPDParam(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose);

Iniziare Registrazione Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Iniziare Registrazione Traiettoria TPD
    * @param  [in] type  Tipo dati registrazione, 1-posizione articolare
    * @param  [in] name  Nome file traiettoria
    * @param  [in] period_ms  Periodo campionamento dati, valori fissi 2ms o 4ms o 8ms
    * @param  [in] di_choose  Selezione DI, bit0~bit7 corrispondono DI0~DI7 quadro controllo, bit8~bit9 corrispondono DI0~DI1 estremità, 0-non selezionato, 1-selezionato
    * @param  [in] do_choose  Selezione DO, bit0~bit7 corrispondono DO0~DO7 quadro controllo, bit8~bit9 corrispondono DO0~DO1 estremità, 0-non selezionato, 1-selezionato
    * @return   Codice errore
    */
    int SetTPDStart(int type, string name, int period_ms, UInt16 di_choose, UInt16 do_choose); 

Arrestare Registrazione Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Arrestare Registrazione Traiettoria TPD
    * @return   Codice errore
    */
    int SetWebTPDStop(); 

Eliminare Registrazione Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Eliminare Registrazione Traiettoria TPD
    * @param  [in] name  Nome file traiettoria
    * @return   Codice errore
    */   
    int SetTPDDelete(string name); 

Precaricamento Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Precaricamento Traiettoria
    * @param  [in] name  Nome file traiettoria
    * @return   Codice errore
    */      
    int LoadTPD(string name);

Ottenere Posa Iniziale Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Posa Iniziale Traiettoria 
    * @param [in] name  Nome file traiettoria
    * @param [out] desc_pose Posa iniziale traiettoria 
    * @return Codice errore 
    */ 
    int GetTPDStartPose(string name, ref DescPose desc_pose); 

Riproduzione Traiettoria TPD
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Riproduzione Traiettoria
    * @param  [in] name  Nome file traiettoria
    * @param  [in] blend 0-non smoothing, 1-smoothing
    * @param  [in] ovl  Percentuale scala velocità, range [0~100]
    * @return   Codice errore
    */
    int MoveTPD(string name, byte blend, float ovl); 

Esempio Codice Registrazione Traiettoria TPD Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnTPDMove_Click(object sender, EventArgs e)
    {
        int type = 1;
        string name = "tpd2025";
        int period_ms = 4;
        ushort di_choose = 0;
        ushort do_choose = 0;

        robot.SetTPDParam(type, name, period_ms, di_choose, do_choose);

        robot.Mode(1);
        Thread.Sleep(1000);
        robot.DragTeachSwitch(1);
        robot.SetTPDStart(type, name, period_ms, di_choose, do_choose);
        Thread.Sleep(10000);
        robot.SetWebTPDStop();
        robot.DragTeachSwitch(0);

        float ovl = 100.0f;
        byte blend = 0;

        DescPose start_pose = new DescPose();

        int rtn = robot.LoadTPD(name);
        Console.WriteLine("LoadTPD rtn is: {0}\n", rtn);

        robot.GetTPDStartPose(name, ref start_pose);
        Console.WriteLine("start pose, xyz is: {0} {1} {2}. rpy is: {3} {4} {5} \n",
            start_pose.tran.x, start_pose.tran.y, start_pose.tran.z,
            start_pose.rpy.rx, start_pose.rpy.ry, start_pose.rpy.rz);
        robot.MoveCart(start_pose, 0, 0, 100, 100, ovl, -1, -1);
        Thread.Sleep(1000);

        rtn = robot.MoveTPD(name, blend, ovl);
        Console.WriteLine("MoveTPD rtn is: {0}\n", rtn);
        Thread.Sleep(5000);

        robot.SetTPDDelete(name);
    }

Pre-elaborazione File Traiettoria Esterna
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Pre-elaborazione File Traiettoria Esterna 
    * @param [in] name Nome file traiettoria  
    * @param [in] ovl Percentuale scala velocità, range [0~100] 
    * @param [in] opt 1-punto controllo, default 1 
    * @return Codice errore 
    */ 
    int LoadTrajectoryJ(string name, float ovl, int opt); 

Riproduzione File Traiettoria Esterna
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Riproduzione File Traiettoria Esterna  
    * @return Codice errore 
    */
    int MoveTrajectoryJ();

Ottenere Posizione Iniziale Traiettoria File Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Posizione Iniziale Traiettoria File Traiettoria 
    * @param [in] name Nome file traiettoria  
    * @param [out] desc_pose Posa iniziale traiettoria  
    * @return Codice errore 
    */ 
    int GetTrajectoryStartPose(string name, ref DescPose desc_pose); 

Ottenere Numero Punto Traiettoria File Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Numero Punto Traiettoria   
    * @param [out] pnum Numero punto traiettoria  
    * @return Codice errore 
    */  
    int GetTrajectoryPointNum(ref int pnum);

Impostare Velocità Esecuzione Traiettoria File Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Velocità Esecuzione Traiettoria File Traiettoria   
    * @param [in] ovl Percentuale velocità  
    * @return Codice errore 
    */  
    int SetTrajectoryJSpeed(double ovl);

Impostare Forza e Coppia durante Esecuzione Traiettoria File Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Forza e Coppia durante Esecuzione Traiettoria File Traiettoria  
    * @param [in] ft Forza e coppia tre direzioni, unità N e Nm
    * @return Codice errore 
    */
    int SetTrajectoryJForceTorque(ForceTorque ft); 

Impostare Forza lungo Direzione x durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Forza lungo Direzione x durante Esecuzione Traiettoria  
    * @param [in] fx  Forza lungo direzione x, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFx(double fx);

Impostare Forza lungo Direzione y durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Forza lungo Direzione y durante Esecuzione Traiettoria  
    * @param [in] fy  Forza lungo direzione y, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFy(double fy);

Impostare Forza lungo Direzione z durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Forza lungo Direzione z durante Esecuzione Traiettoria  
    * @param [in] fz  Forza lungo direzione z, unità N
    * @return Codice errore 
    */
    int SetTrajectoryJForceFz(double fz);

Impostare Coppia attorno Asse x durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Coppia attorno Asse x durante Esecuzione Traiettoria  
    * @param [in] tx  Coppia attorno asse x, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTx(double tx);

Impostare Coppia attorno Asse y durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Coppia attorno Asse y durante Esecuzione Traiettoria  
    * @param [in] ty  Coppia attorno asse y, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTy(double ty);

Impostare Coppia attorno Asse z durante Esecuzione Traiettoria
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostare Coppia attorno Asse z durante Esecuzione Traiettoria  
    * @param [in] tz  Coppia attorno asse z, unità Nm
    * @return Codice errore 
    */
    int SetTrajectoryJTorqueTz(double tz);

Caricare File Traiettoria J
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Caricare File Traiettoria J
    * @param [in] filePath Nome percorso completo file traiettoria caricamento   C://test/testJ.txt
    * @return Codice errore
    */
    int TrajectoryJUpLoad(string filePath);

Eliminare File Traiettoria J
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Eliminare File Traiettoria J
    * @param [in] fileName Nome file testJ.txt
    * @return Codice errore
    */
    int TrajectoryJDelete(string fileName);

Esempio Codice Riproduzione File Traiettoria J Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button33_Click(object sender, EventArgs e)
    {
        int rtn = robot.TrajectoryJUpLoad("D://zUP/spray_traj1.txt");
        Console.WriteLine("Upload TrajectoryJ A {0}\n", rtn);

        string traj_file_name = "/fruser/traj/spray_traj1.txt";
        rtn = robot.LoadTrajectoryJ(traj_file_name, 100, 1);
        Console.WriteLine("LoadTrajectoryJ {0}, rtn is: {1}\n", traj_file_name, rtn);

        DescPose traj_start_pose = new DescPose();
        rtn = robot.GetTrajectoryStartPose(traj_file_name, ref traj_start_pose);
        Console.WriteLine("GetTrajectoryStartPose is: {0}\n", rtn);
        Console.WriteLine("desc_pos:{0},{1},{2},{3},{4},{5}\n",
            traj_start_pose.tran.x, traj_start_pose.tran.y, traj_start_pose.tran.z,
            traj_start_pose.rpy.rx, traj_start_pose.rpy.ry, traj_start_pose.rpy.rz);

        Thread.Sleep(1000);

        robot.SetSpeed(50);
        robot.MoveCart(traj_start_pose, 0, 0, 100, 100, 100, -1, -1);

        int traj_num = 0;
        rtn = robot.GetTrajectoryPointNum(ref traj_num);
        Console.WriteLine("GetTrajectoryStartPose rtn is: {0}, traj num is: {1}\n", rtn, traj_num);

        rtn = robot.SetTrajectoryJSpeed(50.0f);
        Console.WriteLine("SetTrajectoryJSpeed is: {0}\n", rtn);

        ForceTorque traj_force = new ForceTorque();
        traj_force.fx = 10;
        rtn = robot.SetTrajectoryJForceTorque(traj_force);
        Console.WriteLine("SetTrajectoryJForceTorque rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFx(10.0f);
        Console.WriteLine("SetTrajectoryJForceFx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFy(0.0f);
        Console.WriteLine("SetTrajectoryJForceFy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJForceFz(0.0f);
        Console.WriteLine("SetTrajectoryJForceFz rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTx(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTx rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTy(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTy rtn is: {0}\n", rtn);

        rtn = robot.SetTrajectoryJTorqueTz(10.0f);
        Console.WriteLine("SetTrajectoryJTorqueTz rtn is: {0}\n", rtn);

        rtn = robot.MoveTrajectoryJ();
        Console.WriteLine("MoveTrajectoryJ rtn is: {0}\n", rtn);
    }

Pre-elaborazione Traiettoria (Look-ahead Traiettoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Pre-elaborazione Traiettoria (Look-ahead Traiettoria)
    * @param  [in] name  Nome file traiettoria
    * @param  [in] mode Modalità campionamento, 0-non campionamento; 1-campionamento intervallo dati uguale; 2-campionamento limite errore uguale
    * @param  [in] errorLim Limite errore, effettivo quando usa interpolazione lineare
    * @param  [in] type Metodo smoothing, 0-smoothing Bezier
    * @param  [in] precision Precisione smoothing, effettivo quando usa smoothing Bezier
    * @param  [in] vamx Velocità massima impostata, mm/s
    * @param  [in] amax Accelerazione massima impostata, mm/s2
    * @param  [in] jmax Jerk massimo impostato, mm/s3
    * @return   Codice errore   
    */
    int LoadTrajectoryLA(string name, int mode, double errorLim, int type, double precision, double vamx, double amax, double jmax);

Riproduzione Traiettoria (Look-ahead Traiettoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Riproduzione Traiettoria (Look-ahead Traiettoria)
    * @return   Codice errore   
    */
    int MoveTrajectoryLA();

Esempio Codice Riproduzione Traiettoria (Look-ahead Traiettoria)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button8_Click(object sender, EventArgs e)
    {
        int rtn = 0;

        string nameA = "/fruser/traj/A.txt";
        string nameB = "/fruser/traj/B.txt";

        rtn = robot.LoadTrajectoryLA(nameB, 0, 0, 0, 1, 100.0, 100.0, 1000.0);    // Interpolazione lineare
        Console.WriteLine($"LoadTrajectoryLA rtn is {rtn}");

        DescPose startPos = new DescPose(0, 0, 0, 0, 0, 0);
        robot.GetTrajectoryStartPose(nameA, ref startPos);

        //
        robot.MoveCart(startPos, 1, 0, (float)100.0, (float)100.0, (float)100.0, -1, -1);

        rtn = robot.MoveTrajectoryLA();
        Console.WriteLine($"MoveTrajectoryLA rtn is {rtn}");
    }