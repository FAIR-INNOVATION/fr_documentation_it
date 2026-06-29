Impostazioni comuni del robot
==============================

.. toctree:: 
    :maxdepth: 5

Impostazione punti di riferimento utensile - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il punto di riferimento utensile - Metodo a sei punti
    * @param [in] point_num Numero del punto, intervallo [1~6]
    * @return Codice di errore 
    */ 
    int SetToolPoint(int point_num);

Calcolo sistema di coordinate utensile - Metodo a sei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcola il sistema di coordinate utensile
    * @param [out] tcp_pose Sistema di coordinate utensile
    * @return Codice di errore 
    */ 
    int ComputeTool(DescPose tcp_pose);

Impostazione punti di riferimento utensile - Metodo a quattro punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il punto di riferimento utensile - Metodo a quattro punti
    * @param [in] point_num Numero del punto, intervallo [1~4]
    * @return Codice di errore 
    */ 
    int SetTcp4RefPoint(int point_num);

Calcolo sistema di coordinate utensile - Metodo a quattro punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcola il sistema di coordinate utensile
    * @param [out] tcp_pose Sistema di coordinate utensile
    * @return Codice di errore 
    */ 
    int ComputeTcp4(DescPose tcp_pose);

Calcolo sistema di coordinate utensile in base alle informazioni dei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcola il sistema di coordinate utensile in base alle informazioni dei punti
    * @param [in] method Metodo di calcolo; 0-Metodo a quattro punti; 1-Metodo a sei punti
    * @param [in] pos Gruppo di posizioni articolari, lunghezza array 4 per metodo a 4 punti, 6 per metodo a 6 punti
    * @param [out] tool_pose Sistema di coordinate utensile in output
    * @return Codice di errore 
    */ 
    int ComputeToolCoordWithPoints(int method, JointPos[] pos,DescPose tool_pose);

Impostazione sistema di coordinate utensile
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il sistema di coordinate utensile 
    * @param [in] id Numero sistema di coordinate, intervallo [0~14]
    * @param [in] coord  Posa del centro utensile rispetto al centro della flangia terminale
    * @param [in] type  0-Sistema di coordinate utensile, 1-Sistema di coordinate sensore
    * @param [in] install Posizione installazione, 0-Terminale robot, 1-Esterno robot
    * @param [in] toolID  ID utensile
    * @param [in] loadNum  Numero carico
    * @return Codice di errore 
    */ 
    int SetToolCoord(int id, DescPose coord, int type, int install, int toolID, int loadNum);  

Impostazione lista sistemi di coordinate utensile
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la lista dei sistemi di coordinate utensile
    * @param  [in] id Numero sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del centro utensile rispetto al centro della flangia terminale
    * @param  [in] type  0-Sistema di coordinate utensile, 1-Sistema di coordinate sensore
    * @param  [in] install Posizione installazione, 0-Terminale robot, 1-Esterno robot
    * @param  [in] loadNum Numero carico
    * @return  Codice di errore
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);  

Ottenimento sistema di coordinate utensile corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il sistema di coordinate utensile corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate utensile
    * @return  Codice di errore
    */
    int GetTCPOffset(int flag, DescPose desc_pos); 

Esempio di codice operazioni sistema di coordinate utensile robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestTCPCompute(Robot robot)
    {
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint=new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc=new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint=new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc=new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint=new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc=new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint=new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc=new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint=new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc=new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint=new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
        DescPose coordRtn =new DescPose() {};
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(4);
        robot.MoveJ(p5Joint, p5Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(5);
        robot.MoveJ(p6Joint, p6Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(coordRtn);
        robot.SetToolList(3, coordRtn, 0, 0, 0);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(coordRtn);

        robot.SetToolCoord(4, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose(){};
        rtn = robot.GetTCPOffset(0, getCoord);
        return 0;
    }

Impostazione punti di riferimento utensile esterno - Metodo a sei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il punto di riferimento utensile esterno - Metodo a tre punti 
    * @param [in] point_num Numero del punto, intervallo [1~3]
    * @return Codice di errore 
    */ 
    int SetExTCPPoint(int point_num); 

Calcolo sistema di coordinate utensile esterno - Metodo a sei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:
    
    /** 
    * @brief Calcola il sistema di coordinate utensile esterno - Metodo a tre punti
    * @param [out] tcp_pose Sistema di coordinate utensile esterno
    * @return Codice di errore 
    */ 
    int ComputeExTCF(DescPose tcp_pose); 

Impostazione sistema di coordinate utensile esterno
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il sistema di coordinate utensile esterno 
    * @param [in] id Numero sistema di coordinate, intervallo [0~14]
    * @param [in] etcp  Posa del centro utensile rispetto al centro della flangia terminale
    * @param [in] etool  Da determinare
    * @return Codice di errore 
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool); 

Impostazione lista sistemi di coordinate utensile esterno
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la lista dei sistemi di coordinate utensile esterno
    * @param  [in] id Numero sistema di coordinate, intervallo [0~14]
    * @param  [in] etcp  Posa del centro utensile rispetto al centro della flangia terminale
    * @param  [in] etool  Da determinare
    * @return  Codice di errore
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool); 

Esempio di codice operazioni sistema di coordinate utensile esterno robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestExtCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = { p1Desc , p2Desc , p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(coordRtn);

        robot.SetExToolCoord(1, coordRtn, offdese);
        robot.SetExToolList(1, coordRtn, offdese);
        return 0;
    }

Impostazione punti di riferimento sistema di coordinate pezzo - Metodo a tre punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta il punto di riferimento pezzo - Metodo a tre punti 
    * @param [in] point_num Numero del punto, intervallo [1~3]
    * @return Codice di errore 
    */ 
    int SetWObjCoordPoint(int point_num);

Calcolo sistema di coordinate pezzo
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcola il sistema di coordinate pezzo
    * @param [in]  method Metodo di calcolo 0: Origine-Asse X-Asse Z  1: Origine-Asse X-Piano XY
    * @param [in]  refFrame Sistema di coordinate di riferimento
    * @param [out]  wobj_pose Sistema di coordinate pezzo
    * @return Codice di errore 
    */ 
    int ComputeWObjCoord(int method, int refFrame, DescPose wobj_pose); 

Impostazione sistema di coordinate pezzo
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il sistema di coordinate pezzo
    * @param  [in] id Numero sistema di coordinate, intervallo [1~15]
    * @param  [in] coord  Posa del sistema di coordinate pezzo rispetto al centro della flangia terminale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */    
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Impostazione lista sistemi di coordinate pezzo
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la lista dei sistemi di coordinate pezzo
    * @param  [in] id Numero sistema di coordinate, intervallo [1~15]
    * @param  [in] coord  Posa del sistema di coordinate pezzo rispetto al centro della flangia terminale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */    
    int SetWObjList(int id, DescPose coord, int refFrame);

Calcolo sistema di coordinate pezzo in base alle informazioni dei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Calcola il sistema di coordinate pezzo in base alle informazioni dei punti
    * @param [in] method Metodo di calcolo; 0: Origine-Asse X-Asse Z  1: Origine-Asse X-Piano XY
    * @param [in] pos Tre gruppi di posizioni TCP
    * @param [in] refFrame Sistema di coordinate di riferimento
    * @param [in] tcp_pose Sistema di coordinate pezzo in output
    * @return Codice di errore 
    */ 
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame,DescPose tcp_pose);

Ottenimento sistema di coordinate pezzo corrente
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il sistema di coordinate pezzo corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate pezzo
    * @return  Codice di errore
    */   
    int GetWObjOffset(int flag, DescPose desc_pos);

Esempio di codice operazioni sistema di coordinate pezzo robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWobjCoord(Robot robot)
    {
        DescPose p1Desc=new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint=new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc=new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint=new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc=new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint=new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,p1Desc);
        robot.GetForwardKin(p2Joint,p2Desc);
        robot.GetForwardKin(p3Joint,p3Desc);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP =new DescPose[]{p1Desc , p2Desc , p3Desc };
        DescPose coordRtn =new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);

        robot.MoveJ(p1Joint, p1Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, coordRtn);

        robot.SetWObjCoord(1, coordRtn, 0);
        robot.SetWObjList(1, coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, getWobjDesc);
        return 0;
    }
    
Impostazione velocità globale
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la velocità globale
    * @param  [in]  vel  Percentuale velocità, intervallo [0~100]
    * @return  Codice di errore
    */
    int SetSpeed(int vel); 

Impostazione accelerazione robot
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta l'accelerazione del robot
    * @param [in] acc Percentuale accelerazione robot
    * @return Codice di errore
    */
    int SetOaccScale(double acc);

Ottenimento velocità predefinita robot
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene la velocità predefinita del robot
    * @return  List[0]:int Codice errore; List[1]: double vel Velocità, unità mm/s
    */   
    List<Number> GetDefaultTransVel(); 

Impostazione peso carico terminale
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il peso del carico terminale
    * @param  [in] loadNum Numero carico
    * @param  [in] weight  Peso carico, unità kg
    * @return  Codice di errore
    */
    int SetLoadWeight(int loadNum,double weight);

Impostazione coordinate centro di massa carico terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta le coordinate del centro di massa del carico terminale
    * @param  [in] coord Coordinate centro di massa, unità mm
    * @return  Codice di errore
    */
    int SetLoadCoord(DescTran coord); 

Impostazione coordinate centro di massa carico terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief  Imposta le coordinate del centro di massa del carico terminale
     * @param  [in] loadNum Numero carico
     * @param  [in] coord Coordinate centro di massa, unità mm
     * @return  Codice di errore
     */
    public int SetLoadCoord(int loadNum, DescTran coord)

Ottenimento peso carico corrente
++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il peso del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @return  List[0]:int Codice errore; List[1]: double weight  Peso carico, unità kg
    */
    List<Number> GetTargetPayload(int flag); 

Ottenimento centro di massa carico corrente
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il centro di massa del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] cog Centro di massa carico, unità mm
    * @return  Codice di errore
    */   
    int GetTargetPayloadCog(int flag, DescTran cog);

Impostazione modalità installazione robot
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta la modalità di installazione del robot
    * @param  [in]  install  Modalità installazione, 0-Montaggio normale, 1-Montaggio laterale, 2-Montaggio a soffitto
    * @return  Codice di errore
    */
    int SetRobotInstallPos(int install); 

Impostazione angolo installazione robot
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta l'angolo di installazione del robot, installazione libera
    * @param  [in] yangle  Angolo inclinazione
    * @param  [in] zangle  Angolo rotazione
    * @return  Codice di errore
    */
    int SetRobotInstallAngle(double yangle, double zangle); 

Ottenimento angolo installazione robot
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene l'angolo di installazione del robot
    * @return  List[0]:Codice errore; List[1]:double yangle Angolo inclinazione; List[2]:double zangle Angolo rotazione
    */
    public List<Number> GetRobotInstallAngle()

Impostazione valore variabile di sistema
++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il valore della variabile di sistema
    * @param  [in]  id  Numero variabile, intervallo [1~20]
    * @param  [in]  value Valore variabile
    * @return  Codice di errore
    */
    int SetSysVarValue(int id, double value); 

Ottenimento valore variabile di sistema
+++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il valore della variabile di sistema
    * @param  [in] id Numero variabile di sistema, intervallo [1~20]
    * @return  List[0]:Codice errore; List[1]:double value Valore variabile di sistema
    */
    List<Number> GetSysVarValue(int id); 

Esempio di codice impostazioni comuni robot
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLoadInstall(Robot robot)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            robot.Sleep(30);
        }

        List<Number> defaultVel=new ArrayList<>();

        defaultVel=robot.GetDefaultTransVel();
        System.out.println("GetDefaultTransVel is:"+ defaultVel.get(1));

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5);
            robot.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            float value = 0;
            defaultVel=robot.GetSysVarValue(i);
            System.out.println("sys value :"+i+", is :"+defaultVel.get(1));
            robot.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0;
        loadCoord.y = 4.0;
        loadCoord.z = 5.0;
        robot.SetLoadCoord(loadCoord);

        robot.Sleep(1000);

        List<Number> getLoad = new ArrayList<>();

        getLoad=robot.GetTargetPayload(0);

        DescTran getLoadTran =new DescTran();
        robot.GetTargetPayloadCog(0, getLoadTran);
        System.out.println("get load is:"+getLoad.get(1)+", get load cog is: "+getLoadTran.x+","+getLoadTran.y+","+getLoadTran.z);

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0, 25.0);

        List<Number> angle=new ArrayList<>();
        angle=robot.GetRobotInstallAngle();
        System.out.println("GetRobotInstallAngle x:"+angle.get(1)+";  y:"+angle.get(2));

        robot.CloseRPC();
        return 0;
    }

Interruttore compensazione attrito giunti
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Interruttore compensazione attrito giunti 
    * @param [in] state  0-Spegnimento, 1-Accensione
    * @return Codice di errore 
    */ 
    int FrictionCompensationOnOff(int state); 

Impostazione coefficiente compensazione attrito giunti - Montaggio normale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il coefficiente di compensazione attrito giunti - Montaggio normale
    * @param  [in]  coeff Sei coefficienti compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_level(Object[] coeff);

Impostazione coefficiente compensazione attrito giunti - Montaggio laterale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il coefficiente di compensazione attrito giunti - Montaggio laterale
    * @param  [in]  coeff Sei coefficienti compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_wall(Object[] coeff); 

Impostazione coefficiente compensazione attrito giunti - Montaggio a soffitto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il coefficiente di compensazione attrito giunti - Montaggio a soffitto
    * @param  [in]  coeff Sei coefficienti compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_ceiling(Object[] coeff);

Impostazione coefficiente compensazione attrito giunti - Installazione libera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il coefficiente di compensazione attrito giunti - Installazione libera
    * @param  [in]  coeff Sei coefficienti compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_freedom(Object[] coeff);

Esempio di codice impostazione compensazione attrito giunti robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFriction(Robot robot)
    {

        Object[] lcoeff = { 0.9,0.9,0.9,0.9,0.9,0.9 };
        Object[] wcoeff = { 0.4,0.4,0.4,0.4,0.4,0.4 };
        Object[] ccoeff = { 0.6,0.6,0.6,0.6,0.6,0.6 };
        Object[] fcoeff = { 0.5,0.5,0.5,0.5,0.5,0.5 };

        int rtn = robot.FrictionCompensationOnOff(1);
        System.out.println("FrictionCompensationOnOff rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_level(lcoeff);
        System.out.println("SetFrictionValue_level rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_wall(wcoeff);
        System.out.println("SetFrictionValue_wall rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        System.out.println("SetFrictionValue_ceiling rtn is:"+ rtn);

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        System.out.println("SetFrictionValue_freedom rtn is:"+ rtn);

        robot.CloseRPC();
        return 0;
    }

Query codice errore robot
+++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief  Query codice errore robot
     * @param  [out]  maincode  Codice errore principale
     * @param  [out]  subcode   Codice errore secondario
     * @return  Codice di errore
     */ 
    int GetRobotErrorCode(int[] maincode, int[] subcode);

Cancellazione stato errore
++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Cancellazione stato errore
    * @return  Codice di errore
    */
    int ResetAllError(); 

Esempio di codice ottenimento stato guasto robot e cancellazione errori
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetError(Robot robot)
    {
        int[] maincode={0}, subcode={0};
        robot.GetRobotErrorCode(maincode, subcode);

        robot.ResetAllError();

        robot.Sleep(1000);

        robot.GetRobotErrorCode(maincode, subcode);
        return 0;
    }

Impostazione parametri monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i parametri di monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
    * @param [in] enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    * @param [in] period Periodo monitoraggio (s), intervallo 1-100
    * @return Codice di errore
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Ottenimento parametri monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene i parametri di monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
    * @return List[0]-Codice errore,List[1]-enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio,List[2]-period Periodo monitoraggio (s), intervallo 1-100
    */
    List<Number> GetWideBoxTempFanMonitorParam()

Esempio di codice ottenimento stato temperatura e corrente ventilatore quadro controllo tensione larga
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestWideVoltageCtrlBoxtemp(Robot robot)
    {
        robot.SetWideBoxTempFanMonitorParam(1, 2);
        List<Number> list=robot.GetWideBoxTempFanMonitorParam();
        System.out.println("GetWideBoxTempFanMonitorParam enable is:"+list.get(1)+", period is:"+list.get(2));
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+",fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);

        list=robot.GetWideBoxTempFanMonitorParam();
        for (int i = 0; i < 100; i++)
        {
            pkg=robot.GetRobotRealTimeState();
            System.out.println("robot ctrl box temp is:"+pkg.wideVoltageCtrlBoxTemp+" ,fan current is:"+pkg.wideVoltageCtrlBoxFanCurrent);
            robot.Sleep(100);
        }

        robot.CloseRPC();
        robot.Sleep(2000);
        return 0;
    }

Impostazione punto calibrazione fuoco
++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il punto di calibrazione fuoco
    * @param [in] pointNum Numero punto calibrazione fuoco 1-8
    * @param [in] point    Coordinate punto calibrazione
    * @return Codice di errore
    */
    int SetFocusCalibPoint(int pointNum, DescPose point)

Calcolo risultato calibrazione fuoco
++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Calcola il risultato della calibrazione fuoco
    * @param [in] pointNum  Numero punti calibrazione
    * @param [in] resultPos Risultato calibrazione XYZ
    * @param [out] accuracy  Errore accuratezza calibrazione
    * @return Codice di errore
    */
    int ComputeFocusCalib(int pointNum, DescTran resultPos, double[] accuracy)

Avvio inseguimento fuoco
++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Avvia l'inseguimento fuoco
    * @param [in] kp       Parametro proporzionale, default 50.0
    * @param [in] kpredict Parametro feedforward, default 19.0
    * @param [in] aMax     Limite massima accelerazione angolare, default 1440°/s^2
    * @param [in] vMax     Limite massima velocità angolare, default 180°/s
    * @param [in] type     Blocco direzione asse X (0-Vettore input riferimento; 1-Orizzontale; 2-Verticale)
    * @return Codice di errore
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type)

Arresto inseguimento fuoco
++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Arresta l'inseguimento fuoco
    * @return Codice di errore
    */
    int FocusEnd()

Impostazione coordinate fuoco
+++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:
    
    /**
    * @brief Imposta le coordinate del fuoco
    * @param pos Coordinate fuoco XYZ
    * @return Codice di errore
    */
    public int SetFocusPosition(DescTran pos)

Esempio di codice inseguimento fuoco
++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestFocus(Robot robot){
        DescPose p1Desc=new DescPose(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint = new JointPos(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);

        DescPose p2Desc = new DescPose(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint = new JointPos(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);

        DescPose p3Desc = new DescPose(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint = new JointPos(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);

        DescPose p4Desc = new DescPose(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint = new JointPos(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);

        DescPose p5Desc = new DescPose(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint = new JointPos(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);

        DescPose p6Desc = new DescPose(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint = new JointPos(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 100, 0, 0, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint,  p2Desc);
        robot.GetForwardKin(p3Joint,  p3Desc);
        robot.GetForwardKin(p4Joint,  p4Desc);
        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);

        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4( coordRtn);

        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);

        robot.GetForwardKin(p1Joint, p1Desc);
        robot.GetForwardKin(p2Joint, p2Desc);
        robot.GetForwardKin(p3Joint, p3Desc);

        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);

        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double[] accuracy = {0.0};
        rtn = robot.ComputeFocusCalib(3,  resultPos,  accuracy);
        rtn = robot.SetFocusPosition(resultPos);

        robot.GetForwardKin(p5Joint,  p5Desc);
        robot.GetForwardKin(p6Joint,  p6Desc);

        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);

        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese,0,100);
        robot.FocusEnd();
    }

Abilitazione funzione calibrazione sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Abilita la funzione di calibrazione sensibilità sensore coppia giunti
    * @param status 0-Disabilita; 1-Abilita
    * @return Codice di errore
    */
    public int JointSensitivityEnable(int status)

Raccolta dati sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Raccolta dati sensibilità sensore coppia giunti
    * @return Codice di errore
    */
    public int JointSensitivityCollect()

Ottenimento risultato calibrazione sensibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il risultato della calibrazione sensibilità sensore coppia giunti
    * @param calibResult Sensibilità giunti j1~j6 [0-1]
    * @param linearityn Linearità giunti j1~j6 [0-1]
    * @return Codice di errore
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6])

Ottenimento errore isteresi sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene l'errore di isteresi del sensore coppia giunti
    * @param hysteresisError Errore isteresi giunti j1~j6
    * @return Codice di errore
    */
    public int JointHysteresisError(double[] hysteresisError);
    
Ottenimento ripetibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:
    
    /**
    * @brief Ottiene la ripetibilità del sensore coppia giunti
    * @param repeatability Ripetibilità sensore coppia giunti j1~j6
    * @return Codice di errore
    */
    public int JointRepeatability(double[] repeatability);
    
Impostazione parametri sensore forza giunti
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta i parametri del sensore forza giunti
    * @param  Parametro obbligatorio M Coefficiente massa J1-J6[]
    * @param  Parametro obbligatorio B Coefficiente smorzamento J1-J6[]
    * @param  Parametro obbligatorio K Coefficiente rigidezza J1-J6[]
    * @param  Parametro default threshold Soglia controllo forza, Nm
    * @param  Parametro default sensitivity Sensibilità, Nm/V,[]
    * @param  Parametro default setZeroFlag Flag abilitazione funzione; 0-Disabilita; 1-Abilita; 2-Registra zero posizione1; 3-Registra zero posizione2
    * @return Codice di errore
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Esempio di codice calibrazione automatica sensibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSensitivityCalib(Robot robot)
    {
        int rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = new JointPos();
        robot.GetActualJointPosDegree(curJPos);
        ExaxisPos epos = new ExaxisPos(0,0,0,0);
        DescPose offset_pos =new DescPose(0,0,0,0,0,0 );
        JointPos jointPos1 = new JointPos(curJPos.J1, 0, 0, -90, 0.02, curJPos.J6);
        DescPose descPos1 = new DescPose();
        robot.GetForwardKin(jointPos1, descPos1);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 =new JointPos( curJPos.J1, -30, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos2 =new DescPose();
        robot.GetForwardKin(jointPos2, descPos2);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = new JointPos( curJPos.J1, -60, 0, -90, 0.02, curJPos.J6 );
        DescPose descPos3 =new DescPose();
        robot.GetForwardKin(jointPos3, descPos3);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = new JointPos(curJPos.J1, -90, 0, -90, 0.02, curJPos.J6);
        DescPose descPos4 = new DescPose();
        robot.GetForwardKin(jointPos4, descPos4);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = new JointPos(curJPos.J1, -120, 0, -90, 0.02, curJPos.J6);
        DescPose descPos5 = new DescPose();
        robot.GetForwardKin(jointPos5, descPos5);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = new JointPos(curJPos.J1, -150, 0, -90, 0.02, curJPos.J6);
        DescPose descPos6 = new DescPose();
        robot.GetForwardKin(jointPos6, descPos6);
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = new JointPos(curJPos.J1, -180, 0, -90, 0.02, curJPos.J6);
        DescPose descPos7 = new DescPose();
        robot.GetForwardKin(jointPos7, descPos7);
        robot.MoveJ(jointPos7, descPos7, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //Corsa inversa
        robot.MoveJ(jointPos6, descPos6, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos5, descPos5, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos4, descPos4, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos3, descPos3, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos2, descPos2, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(jointPos1, descPos1, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        System.out.printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double[] calibResult =new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        System.out.printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        System.out.printf("JointSensitivityEnable rtn is %d\n", rtn);
        System.out.printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n",
                calibResult[0], calibResult[1], calibResult[2],
                calibResult[3], calibResult[4], calibResult[5],
                linearity[0], linearity[1], linearity[2],
                linearity[3], linearity[4], linearity[5]);
        double[] hysteresisError = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointHysteresisError(hysteresisError);
        System.out.printf("JointHysteresisError result is %f %f %f %f %f %f\n",
                hysteresisError[0], hysteresisError[1], hysteresisError[2],
                hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double[] repeatability = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        rtn = robot.JointRepeatability(repeatability);
        System.out.printf("JointRepeatability result is %f %f %f %f %f %f\n",
                repeatability[0], repeatability[1], repeatability[2],
                repeatability[3], repeatability[4], repeatability[5]);
        double[] M = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] B = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        double[] K = {0.0, 0.0, 0.0, 0.0, 0.0, 0.0};
        double[] threshold = {1.0, 1.0, 1.0, 1.0, 1.0, 1.0};
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        System.out.printf("SetAdmittanceParams rtn is %d\n", rtn);
    }

Ottenimento conteggio frame errore 8 porte slave robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il conteggio frame errore 8 porte slave robot
    * @param  inRecvErr Conteggio frame errore ricezione input
    * @param  inCRCErr Conteggio frame errore CRC input
    * @param  inTransmitErr Conteggio frame errore trasmissione input
    * @param  inLinkErr Conteggio frame errore collegamento input
    * @param  outRecvErr Conteggio frame errore ricezione output
    * @param  outCRCErr Conteggio frame errore CRC output
    * @param  outTransmitErr Conteggio frame errore trasmissione output
    * @param  outLinkErr Conteggio frame errore collegamento output
    * @return Codice di errore
    */
    public int GetSlavePortErrCounter(int[] inRecvErr, int[] inCRCErr, int[] inTransmitErr, int[] inLinkErr, int[] outRecvErr, int[] outCRCErr, int[] outTransmitErr, int[] outLinkErr)

Azzera conteggio frame errore porte slave
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Azzera il conteggio frame errore porte slave
    * @param slaveID Numero slave 0~7
    * @return Codice di errore
    */
    public int SlavePortErrCounterClear(int slaveID)

Esempio di codice ottenimento conteggio frame errore porte slave
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestSlavePortErr(Robot robot)
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        int[] inRecvErr =new int[8];
        int[] inCRCErr =new int[8];
        int[] inTransmitErr =new int[8];
        int[] inLinkErr =new int[8];
        int[] outRecvErr =new int[8];
        int[] outCRCErr =new int[8];
        int[] outTransmitErr =new int[8];
        int[] outLinkErr =new int[8];
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
                outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                System.out.printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                System.out.printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                System.out.printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                System.out.printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                System.out.printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        System.out.printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
    }

Impostazione coefficiente feedforward velocità assi
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il coefficiente feedforward velocità assi
    * @param  radio Coefficiente feedforward velocità assi
    * @return Codice di errore
    */
    public int SetVelFeedForwardRatio(double[] radio)

Ottenimento coefficiente feedforward velocità assi
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene il coefficiente feedforward velocità assi
    * @param  radio Coefficiente feedforward velocità assi
    * @return Codice di errore
    */
    public int GetVelFeedForwardRatio(double[] radio)

Esempio di codice coefficiente feedforward velocità robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestVelFeedForwardRatio(Robot robot)
    {
        double[] setRadio =new double[] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[]{ 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        System.out.printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
    }

Calibrazione TCP Sensore Fotoelettrico - Calcola RPY Utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico - calcola RPY utensile
    * @param  Btool Posizione cartesiana robot
    * @param  Etool Valore coefficiente sistema coordinate utensile corrente
    * @param  sensor Valore coefficiente sistema coordinate sensore corrente (non ancora disponibile)
    * @param  radius Raggio movimento circolare mm (non ancora disponibile)
    * @param  dz Distanza movimento lungo la direzione negativa dell'asse Z del sistema di coordinate base; quando dz = 10000, la funzione restituisce direttamente RPY utensile
    * @param  TCPRPY Valore RPY utensile
    * @return Codice errore
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, Rpy TCPRPY)

Calibrazione TCP Sensore Fotoelettrico - Calcola XYZ Utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico - calcola XYZ utensile
    * @param  select 0-Calcola TCP utensile; 1-Calcola origine sensore; 2-Calcola orientamento sensore; 3-Restituisce direttamente TCP utensile; 4-Registra sistema coordinate pezzo e sistema coordinate utensile corrente
    * @param  originDirection 0-Direzione X; 1-Direzione Y; 2-Direzione Z
    * @param  pos1 Posizione cartesiana robot 1
    * @param  pos2 Posizione cartesiana robot 2
    * @param  pos3 Posizione cartesiana robot 3
    * @param  pos4 Posizione cartesiana robot 4
    * @param  TCP Valore XYZ utensile
    * @return Codice errore
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2, DescTran pos3, DescTran pos4, DescTran TCP)

Calibrazione TCP Sensore Fotoelettrico - Inizia Registrazione Posizione Centro Flangia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico - inizia registrazione posizione centro flangia
    * @return Codice errore
    */
    public int TCPRecordFlangePosStart()

Calibrazione TCP Sensore Fotoelettrico - Interrompi Registrazione Posizione Centro Flangia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico - interrompi registrazione posizione centro flangia
    * @return Codice errore
    */
    public int TCPRecordFlangePosEnd()

Calibrazione TCP Sensore Fotoelettrico - Ottieni Posizione Punto Centro Utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico - ottieni posizione punto centro utensile
    * @param  TCP Posizione punto centro utensile (x,y,z)
    * @return Codice errore
    */
    public int TCPGetRecordFlangePos(DescTran TCP)

Calibrazione TCP Sensore Fotoelettrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calibrazione TCP sensore fotoelettrico
    * @param luaPath Percorso programma Lua calibrazione automatica: "FR_CalibrateTheToolTcp.lua"
    * @param offset Offset punto di insegnamento (x,y,z) mm
    * @param TCP Sistema coordinate utensile calibrato (x,y,z,rx,ry,rz)
    * @return Codice errore
    */
    public int PhotoelectricSensorTCPCalibration(String luaPath, DescTran offset, DescPose TCP)

Esempio Codice Calibrazione TCP Sensore Fotoelettrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestPhotoelectricSensorTCPCalib(Robot robot)
    {
        DescTran offset = new DescTran(10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, TCP);
        System.out.printf("PhotoelectricSensorTCPCalibration rtn is %d %f %f %f %f %f %f \n", rtn, TCP.tran.x, TCP.tran.y, TCP.tran.z, TCP.rpy.rx, TCP.rpy.ry, TCP.rpy.rz);
        robot.CloseRPC();
        robot.Sleep(9999999);
    }