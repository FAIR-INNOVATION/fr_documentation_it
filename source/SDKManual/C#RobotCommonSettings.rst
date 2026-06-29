Impostazioni comuni del robot
=========================================

.. toctree:: 
    :maxdepth: 5

Impostazione del punto di riferimento dell'utensile - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostazione del punto di riferimento dell'utensile - Metodo a sei punti 
    * @param [in] point_num Numero del punto, intervallo [1~6] 
    * @return Codice di errore 
    */ 
    int SetToolPoint(int point_num); 

Calcolo del sistema di coordinate dell'utensile - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolo del sistema di coordinate dell'utensile
    * @param [out] tcp_pose Sistema di coordinate dell'utensile
    * @return Codice di errore 
    */ 
    int ComputeTool(ref DescPose tcp_pose); 

Impostazione del punto di riferimento dell'utensile - Metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostazione del punto di riferimento dell'utensile - Metodo a quattro punti 
    * @param [in] point_num Numero del punto, intervallo [1~4] 
    * @return Codice di errore 
    */ 
    int SetTcp4RefPoint(int point_num);

Calcolo del sistema di coordinate dell'utensile - Metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Calcolo del sistema di coordinate dell'utensile
    * @param [out] tcp_pose Sistema di coordinate dell'utensile
    * @return Codice di errore 
    */ 
    int ComputeTcp4(ref DescPose tcp_pose);

Impostazione del sistema di coordinate dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del sistema di coordinate dell'utensile
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del centro utensile rispetto al centro della flangia finale
    * @param  [in] type  0-Sistema di coordinate dell'utensile, 1-Sistema di coordinate del sensore
    * @param  [in] install Posizione di installazione, 0-Estremità del robot, 1-Esterno del robot
    * param   [in] toolID ID utensile
    * @param  [in] loadNum Numero del carico
    * @return  Codice di errore
    */
    int SetToolCoord(int id, DescPose coord, int type, int install,int toolID, int loadNum);

Calcolo del sistema di coordinate dell'utensile in base alle informazioni dei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Calcolo del sistema di coordinate dell'utensile in base alle informazioni dei punti
    * @param [in] method Metodo di calcolo; 0-Metodo a quattro punti; 1-Metodo a sei punti
    * @param [in] pos Gruppo di posizioni dei giunti, lunghezza dell'array 4 per il metodo a quattro punti, 6 per il metodo a sei punti
    * @return Codice di errore
    */

    int ComputeToolCoordWithPoints(int method, JointPos[] pos, ref DescPose coordRtn)  

Impostazione della lista dei sistemi di coordinate dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione della lista dei sistemi di coordinate dell'utensile
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del centro utensile rispetto al centro della flangia finale
    * @param  [in] type  0-Sistema di coordinate dell'utensile, 1-Sistema di coordinate del sensore
    * @param  [in] install Posizione di installazione, 0-Estremità del robot, 1-Esterno del robot
    * @param  [in] loadNum Numero del carico
    * @return  Codice di errore
    */
    int SetToolList(int id, DescPose coord, int type, int install, int loadNum);  

Ottenere il sistema di coordinate dell'utensile corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere il sistema di coordinate dell'utensile corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate dell'utensile
    * @return  Codice di errore
    */
    int GetTCPOffset(byte flag, ref DescPose desc_pos); 

Esempio di codice per operazioni sul sistema di coordinate dell'utensile del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button18_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(186.331f, 487.913f, 209.850f, 149.030f, 0.688f, -114.347f);
        JointPos p1Joint = new JointPos(-127.876f, -75.341f, 115.417f, -122.741f, -59.820f, 74.300f);

        DescPose p2Desc = new DescPose(69.721f, 535.073f, 202.882f, -144.406f, -14.775f, -89.012f);
        JointPos p2Joint = new JointPos(-101.780f, -69.828f, 110.917f, -125.740f, -127.841f, 74.300f);

        DescPose p3Desc = new DescPose(146.861f, 578.426f, 205.598f, 175.997f, -36.178f, -93.437f);
        JointPos p3Joint = new JointPos(-112.851f, -60.191f, 86.566f, -80.676f, -97.463f, 74.300f);

        DescPose p4Desc = new DescPose(136.284f, 509.876f, 225.613f, 178.987f, 1.372f, -100.696f);
        JointPos p4Joint = new JointPos(-116.397f, -76.281f, 113.845f, -128.611f, -88.654f, 74.299f);

        DescPose p5Desc = new DescPose(138.395f, 505.972f, 298.016f, 179.134f, 2.147f, -101.110f);
        JointPos p5Joint = new JointPos(-116.814f, -82.333f, 109.162f, -118.662f, -88.585f, 74.302f);

        DescPose p6Desc = new DescPose(105.553f, 454.325f, 232.017f, -179.426f, 0.444f, -99.952f);
        JointPos p6Joint = new JointPos(-115.649f, -84.367f, 122.447f, -128.663f, -90.432f, 74.303f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        JointPos[] posJ = new JointPos[] { p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeToolCoordWithPoints(1, posJ, ref coordRtn);
        Console.WriteLine($"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(4);
        robot.MoveJ( p5Joint,  p5Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(5);
        robot.MoveJ( p6Joint,  p6Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(ref coordRtn);
        Console.WriteLine($"6 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
        robot.SetToolList(1,  coordRtn, 0, 0, 0);

        robot.MoveJ( p1Joint,  p1Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ( p4Joint,  p4Desc, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool        {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0);

        DescPose getCoord = new DescPose();
        rtn = robot.GetTCPOffset(0, ref getCoord);
        Console.WriteLine($"GetTCPOffset    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");
    }

Impostazione del punto di riferimento dell'utensile esterno - Metodo a tre punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostazione del punto di riferimento dell'utensile esterno - Metodo a tre punti 
    * @param [in] point_num Numero del punto, intervallo [1~3] 
    * @return Codice di errore 
    */ 
    int SetExTCPPoint(int point_num); 

Calcolo del sistema di coordinate dell'utensile esterno - Metodo a tre punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
    * @brief Calcolo del sistema di coordinate dell'utensile esterno - Metodo a tre punti
    * @param [out] tcp_pose Sistema di coordinate dell'utensile esterno
    * @return Codice di errore 
    */ 
    int ComputeExTCF(ref DescPose tcp_pose); 

Impostazione del sistema di coordinate dell'utensile esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostazione del sistema di coordinate dell'utensile esterno 
    * @param [in] id Numero del sistema di coordinate, intervallo [0~14] 
    * @param [in] etcp Posa del centro utensile rispetto al centro della flangia finale 
    * @param [in] etool Da definire 
    * @return Codice di errore 
    */
    int SetExToolCoord(int id, DescPose etcp, DescPose etool); 

Impostazione della lista dei sistemi di coordinate dell'utensile esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione della lista dei sistemi di coordinate dell'utensile esterno
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14] 
    * @param  [in] etcp  Posa del centro utensile rispetto al centro della flangia finale
    * @param  [in] etool  Da definire
    * @return  Codice di errore
    */
    int SetExToolList(int id, DescPose etcp, DescPose etool); 

Calcolo del sistema di coordinate del pezzo in base alle informazioni dei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Calcolo del sistema di coordinate del pezzo in base alle informazioni dei punti
    * @param [in] method Metodo di calcolo; 0: Origine-asse X-asse Z  1: Origine-asse X-piano XY
    * @param [in] pos Gruppo di tre posizioni TCP
    * @param [in] refFrame Sistema di coordinate di riferimento
    * @return Codice di errore
    */
    int ComputeWObjCoordWithPoints(int method, DescPose[] pos, int refFrame, ref DescPose coordRtn)

Esempio di codice per operazioni sul sistema di coordinate dell'utensile esterno del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button20_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606f, 779.517f, 193.516f, 178.000f, 0.476f, -92.484f);
        JointPos p1Joint = new JointPos(-108.145f, -50.137f, 85.818f, -125.599f, -87.946f, 74.329f);

        DescPose p2Desc = new DescPose(-24.656f, 850.384f, 191.361f, 177.079f, -2.058f, -95.355f);
        JointPos p2Joint = new JointPos(-111.024f, -41.538f, 69.222f, -114.913f, -87.743f, 74.329f);

        DescPose p3Desc = new DescPose(-99.813f, 766.661f, 241.878f, -176.817f, 1.917f, -91.604f);
        JointPos p3Joint = new JointPos(-107.266f, -56.116f, 85.971f, -122.560f, -92.548f, 74.331f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetExTCPPoint(3);
        int rtn = robot.ComputeExTCF(ref coordRtn);
        Console.WriteLine($"ComputeExTCF                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetExToolCoord(1,  coordRtn,  offdese);
        robot.SetExToolList(1,  coordRtn,  offdese);
    }

Impostazione del punto di riferimento del sistema di coordinate del pezzo - Metodo a tre punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Impostazione del punto di riferimento del pezzo - Metodo a tre punti 
    * @param [in] point_num Numero del punto, intervallo [1~3]  
    * @return Codice di errore 
    */ 
    int SetWObjCoordPoint(int point_num); 

Calcolo del sistema di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Calcolo del sistema di coordinate del pezzo
    * @param [in] method Metodo di calcolo 0：Origine-asse X-asse Z  1：Origine-asse X-piano XY
    * @param [in] refFrame Sistema di coordinate di riferimento
    * @param [out] wobj_pose Sistema di coordinate del pezzo
    * @return Codice di errore
    */
    int ComputeWObjCoord(int method, int refFrame, ref DescPose wobj_pose); 

Impostazione del sistema di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del sistema di coordinate del pezzo
    * @param  [in] id Numero del sistema di coordinate, intervallo [1~15]
    * @param  [in] coord  Posa del sistema di coordinate del pezzo rispetto al centro della flangia finale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */
    int SetWObjCoord(int id, DescPose coord, int refFrame);

Impostazione della lista dei sistemi di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione della lista dei sistemi di coordinate del pezzo
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14] 
    * @param  [in] coord  Posa del sistema di coordinate del pezzo rispetto al centro della flangia finale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */    
    int SetWObjList(int id, DescPose coord, int refFrame);

Ottenere il sistema di coordinate del pezzo corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere il sistema di coordinate del pezzo corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate del pezzo
    * @return  Codice di errore
    */   
    int GetWObjOffset(byte flag, ref DescPose desc_pos); 

Esempio di codice per operazioni sul sistema di coordinate del pezzo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button19_Click(object sender, EventArgs e)
    {
        DescPose p1Desc = new DescPose(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
        JointPos p1Joint = new JointPos(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);

        DescPose p2Desc = new DescPose(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
        JointPos p2Joint = new JointPos(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);

        DescPose p3Desc = new DescPose(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
        JointPos p3Joint = new JointPos(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);

        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint,ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        DescPose[] posTCP = new DescPose[] { p1Desc, p2Desc, p3Desc };
        DescPose coordRtn = new DescPose();
        int rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.MoveJ( p1Joint,  p1Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(1);
        robot.MoveJ( p2Joint,  p2Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(2);
        robot.MoveJ( p3Joint,  p3Desc, 1, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.SetWObjCoordPoint(3);
        rtn = robot.ComputeWObjCoord(1, 0, ref coordRtn);
        Console.WriteLine($"ComputeWObjCoord                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");

        robot.SetWObjCoord(1,  coordRtn, 0);
        robot.SetWObjList(1,  coordRtn, 0);

        DescPose getWobjDesc = new DescPose();
        rtn = robot.GetWObjOffset(0, ref getWobjDesc);
        Console.WriteLine($"GetWObjOffset                   {rtn}  coord is {coordRtn.tran.x} {coordRtn.tran.y} {coordRtn.tran.z} {coordRtn.rpy.rx} {coordRtn.rpy.ry} {coordRtn.rpy.rz}");   
    } 

Impostazione della velocità globale
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione della velocità globale
    * @param  [in]  vel  Percentuale di velocità, intervallo [0~100]
    * @return  Codice di errore
    */
    int SetSpeed(int vel); 

Impostazione dell'accelerazione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Impostazione dell'accelerazione del robot
    * @param [in] acc Percentuale di accelerazione del robot
    * @return Codice di errore
    */
    int SetOaccScale(double acc)

Ottenere la velocità predefinita del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere la velocità predefinita del robot
    * @param  [out]  vel  Velocità, unità mm/s
    * @return  Codice di errore
    */   
    int GetDefaultTransVel(ref double vel); 

Impostazione del peso del carico finale
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del peso del carico finale
    * @param  [in] loadNum Numero del carico
    * @param  [in] weight  Peso del carico, unità kg
    * @return  Codice di errore
    */
    int SetLoadWeight(int loadNum, float weight)

Impostazione delle coordinate del baricentro del carico finale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione delle coordinate del baricentro del carico finale
    * @param  [in] coord Coordinate del baricentro, unità mm
    * @return  Codice di errore
    */
    int SetLoadCoord(DescTran coord); 

Ottenere il peso del carico corrente
++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere il peso del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] weight Peso del carico, unità kg
    * @return  Codice di errore
    */
    int GetTargetPayload(byte flag, ref double weight); 

Ottenere il baricentro del carico corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere il baricentro del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] cog Baricentro del carico, unità mm
    * @return  Codice di errore
    */   
    int GetTargetPayloadCog(byte flag, ref DescTran cog);

Impostazione della modalità di installazione del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione della modalità di installazione del robot
    * @param  [in] install  Modalità di installazione, 0-Installazione normale, 1-Installazione laterale, 2-Installazione a soffitto
    * @return  Codice di errore
    */
    int SetRobotInstallPos(byte install); 

Impostazione dell'angolo di installazione del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione dell'angolo di installazione del robot, installazione libera
    * @param  [in] yangle  Angolo di inclinazione
    * @param  [in] zangle  Angolo di rotazione
    * @return  Codice di errore
    */
    int SetRobotInstallAngle(double yangle, double zangle); 

Ottenere l'angolo di installazione del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere l'angolo di installazione del robot
    * @param  [out] yangle Angolo di inclinazione
    * @param  [out] zangle Angolo di rotazione
    * @return  Codice di errore
    */
    int GetRobotInstallAngle(ref double yangle, ref double zangle); 

Impostazione del valore della variabile di sistema
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del valore della variabile di sistema
    * @param  [in]  id  Numero della variabile, intervallo [1~20]
    * @param  [in]  value Valore della variabile
    * @return  Codice di errore
    */
    int SetSysVarValue(int id, double value); 

Ottenere il valore della variabile di sistema
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere il valore della variabile di sistema
    * @param  [in] id Numero della variabile di sistema, intervallo [1~20]
    * @param  [out] value  Valore della variabile di sistema
    * @return  Codice di errore
    */
    int GetSysVarValue(int id, ref double value); 

Esempio di codice per impostazioni comuni del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button21_Click(object sender, EventArgs e)
    {
        for (int i = 1; i < 100; i++)
        {
            robot.SetSpeed(i);
            robot.SetOaccScale(i);
            Thread.Sleep(30);
        }

        double defaultVel = 0.0f;
        robot.GetDefaultTransVel(ref defaultVel);
        Console.WriteLine($"GetDefaultTransVel is {defaultVel}");

        for (int i = 1; i < 21; i++)
        {
            robot.SetSysVarValue(i, i + 0.5f);
            Thread.Sleep(100);
        }

        for (int i = 1; i < 21; i++)
        {
            double value = 0;
            robot.GetSysVarValue(i, ref value);
            Console.WriteLine($"sys value  {i} is :{value}");
            Thread.Sleep(100);
        }

        robot.SetLoadWeight(0, 2.5f);

        DescTran loadCoord = new DescTran();
        loadCoord.x = 3.0f;
        loadCoord.y = 4.0f;
        loadCoord.z = 5.0f;
        robot.SetLoadCoord( loadCoord);

        Thread.Sleep(1000);

        double getLoad = 0.0f;
        robot.GetTargetPayload(0, ref getLoad);

        DescTran getLoadTran = new DescTran();
        robot.GetTargetPayloadCog(0, ref getLoadTran);
        Console.WriteLine($"get load is {getLoad}; get load cog is {getLoadTran.x} {getLoadTran.y} {getLoadTran.z}");

        robot.SetRobotInstallPos(0);
        robot.SetRobotInstallAngle(15.0f, 25.0f);

        double anglex = 0.0f;
        double angley = 0.0f;
        robot.GetRobotInstallAngle(ref anglex, ref angley);
        Console.WriteLine($"GetRobotInstallAngle x:  {anglex};  y:  {angley}");
    }

Interruttore di compensazione dell'attrito dei giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Interruttore di compensazione dell'attrito dei giunti 
    * @param [in] state 0-Off, 1-On 
    * @return Codice di errore 
    */ 
    int FrictionCompensationOnOff(byte state); 

Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione normale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione normale
    * @param  [in]  coeff Sei coefficienti di compensazione dei giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_level(double[] coeff);

Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione laterale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione laterale
    * @param  [in]  coeff Sei coefficienti di compensazione dei giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_wall(double[] coeff); 

Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione a soffitto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostazione del coefficiente di compensazione dell'attrito dei giunti - Installazione a soffitto
    * @param  [in]  coeff Sei coefficienti di compensazione dei giunti, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_ceiling(double[] coeff);

Imposta il coefficiente di compensazione dell'attrito dell'articolazione - Installazione libera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta il coefficiente di compensazione dell'attrito dell'articolazione - Installazione libera
    * @param  [in]  coeff  Coefficienti di compensazione per le sei articolazioni, intervallo [0~1]
    * @return  Codice di errore
    */
    int SetFrictionValue_freedom(double[] coeff);
       
Esempio di codice per l'impostazione della compensazione dell'attrito delle articolazioni del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        double[] lcoeff = { 0.9f, 0.9f, 0.9f, 0.9f, 0.9f, 0.9f };
        double[] wcoeff = { 0.4f, 0.4f, 0.4f, 0.4f, 0.4f, 0.4f };
        double[] ccoeff = { 0.6f, 0.6f, 0.6f, 0.6f, 0.6f, 0.6f };
        double[] fcoeff = { 0.5f, 0.5f, 0.5f, 0.5f, 0.5f, 0.5f };

        int rtn = robot.FrictionCompensationOnOff(1);
        Console.WriteLine($"FrictionCompensationOnOff rtn is{rtn}");

        rtn = robot.SetFrictionValue_level(lcoeff);
        Console.WriteLine($"SetFrictionValue_level rtn is {rtn}");

        rtn = robot.SetFrictionValue_wall(wcoeff);
        Console.WriteLine($"SetFrictionValue_wall rtn is{rtn}");

        rtn = robot.SetFrictionValue_ceiling(ccoeff);
        Console.WriteLine($"SetFrictionValue_ceiling rtn is {rtn}");

        rtn = robot.SetFrictionValue_freedom(fcoeff);
        Console.WriteLine($"SetFrictionValue_freedom rtn is {rtn}");
    }

Interroga il codice di errore del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Interroga il codice di errore del robot
    * @param [out] maincode   Codice di errore principale
    * @param [out] subcode    Codice di errore secondario
    * @return Codice di errore 
    */ 
    int GetRobotErrorCode(ref int maincode, ref int subcode);

Cancellazione dello stato di errore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Cancellazione dello stato di errore
    * @return  Codice di errore
    */
    int ResetAllError(); 

Esempio di codice per l'acquisizione dello stato di guasto del robot e la cancellazione degli errori
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnRobotSafetySet_Click(object sender, EventArgs e)
    {
        int maincode=0, subcode=0;
        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is {subcode}" );

        robot.ResetAllError();

        Thread.Sleep(1000);

        robot.GetRobotErrorCode(ref maincode, ref subcode);
        Console.WriteLine($"robot maincode is{maincode};  subcode is{subcode}");
    }

Imposta i parametri di monitoraggio della temperatura e della velocità della ventola per il cabinet di controllo a tensione ampia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta i parametri di monitoraggio della temperatura e della velocità della ventola per il cabinet di controllo a tensione ampia
    * @param [in] enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    * @param [in] period Periodo di monitoraggio (s), intervallo 1-100
    * @return Codice di errore
    */
    int SetWideBoxTempFanMonitorParam(int enable, int period);

Ottieni i parametri di monitoraggio della temperatura e della velocità della ventola per il cabinet di controllo a tensione ampia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni i parametri di monitoraggio della temperatura e della velocità della ventola per il cabinet di controllo a tensione ampia
    * @param [out] enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    * @param [out] period Periodo di monitoraggio (s), intervallo 1-100
    * @return Codice di errore
    */
    int GetWideBoxTempFanMonitorParam(ref int enable, ref int period);

Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void button46_Click(object sender, EventArgs e)
    {
        var pkg = new ROBOT_STATE_PKG(); 
        robot.SetWideBoxTempFanMonitorParam(1, 2);    
        int enable = 0;
        int period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }       
        int rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
        Console.WriteLine($"SetWideBoxTempFanMonitorParam rtn is {rtn}");       
        enable = 0;
        period = 0;
        robot.GetWideBoxTempFanMonitorParam(ref enable, ref period);
        Console.WriteLine($"GetWideBoxTempFanMonitorParam enable is {enable}   period is {period}");  
        for (int i = 0; i < 100; i++)
        {
            robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($" robot ctrl box temp is {pkg.wideVoltageCtrlBoxTemp}, fan current is {pkg.wideVoltageCtrlBoxFanVel}");
            Thread.Sleep(100);
        }
    }

Imposta il punto di calibrazione del fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta il punto di calibrazione del fuoco
    * @param [in] pointNum Numero del punto di calibrazione del fuoco 1-8
    * @param [in] point Coordinate del punto di calibrazione
    * @return Codice di errore
    */
    int SetFocusCalibPoint(int pointNum, DescPose point);

Imposta le coordinate del fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta le coordinate del fuoco
    * @param [in] pos Coordinate XYZ del fuoco
    * @return Codice di errore
    */
    int SetFocusPosition(DescTran pos);

Avvia il follow del fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Avvia il follow del fuoco
    * @param [in] kp Parametro proporzionale, default 50.0
    * @param [in] kpredict Parametro feedforward, default 19.0
    * @param [in] aMax Limite massimo accelerazione angolare, default 1440°/s^2
    * @param [in] vMax Limite massimo velocità angolare, default 180°/s
    * @param [in] tipo Blocca puntamento asse X (0-Vettore di riferimento in ingresso; 1-Orizzontale; 2-Verticale)
    * @return Codice di errore
    */
    int FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Interrompi il follow del fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Interrompi il follow del fuoco
    * @return Codice di errore
    */
    int FocusEnd();

Esempio di codice per il follow del fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.5  Web-3.8.4
    
.. code-block:: c#
    :linenos:

    private void button81_Click(object sender, EventArgs e)
    {
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
        robot.GetForwardKin(p1Joint,ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.GetForwardKin(p4Joint, ref p4Desc);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveJ(p1Joint, p1Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(p2Joint, p2Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(p3Joint, p3Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(p4Joint, p4Desc, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.SetTcp4RefPoint(4);
        DescPose coordRtn = new DescPose(0.0, 0.0, 0.0, 0.0, 0.0, 0.0);
        int rtn = robot.ComputeTcp4(ref coordRtn);
        Console.WriteLine($"4 Point ComputeTool      {rtn} coord is {coordRtn.tran.x} ,{coordRtn.tran.y} ,{coordRtn.tran.z} ,{coordRtn.rpy.rx} ,{coordRtn.rpy.ry} ,{coordRtn.rpy.rz} ");
        robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0);
        robot.GetForwardKin(p1Joint, ref p1Desc);
        robot.GetForwardKin(p2Joint, ref p2Desc);
        robot.GetForwardKin(p3Joint, ref p3Desc);
        robot.SetFocusCalibPoint(1, p1Desc);
        robot.SetFocusCalibPoint(2, p2Desc);
        robot.SetFocusCalibPoint(3, p3Desc);
        DescTran resultPos = new DescTran(0.0, 0.0, 0.0);
        double accuracy = 0.0;
        rtn = robot.ComputeFocusCalib(3, ref resultPos, ref accuracy);
        Console.WriteLine($"ComputeFocusCalib coord is  {rtn},{ resultPos.x} ,{ resultPos.y}, { resultPos.z}, accuracy is {accuracy} ");
        rtn = robot.SetFocusPosition(resultPos);
        robot.GetForwardKin(p5Joint, ref p5Desc);
        robot.GetForwardKin(p6Joint, ref p6Desc);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusStart(50, 19, 710, 90, 0);
        robot.MoveL(p5Joint, p5Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.MoveL(p6Joint, p6Desc, 1, 0, 10, 100, 100, -1, 0, exaxisPos, 0, 1, offdese);
        robot.FocusEnd();
    }

Abilita la funzione di calibrazione della sensibilità del sensore di coppia dell'articolazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Abilita la funzione di calibrazione della sensibilità del sensore di coppia dell'articolazione
    * @param [in] status 0-Disabilita; 1-Abilita
    * @return  Codice di errore
    */
    public int JointSensitivityEnable(int status);

Acquisizione dati di sensibilità del sensore di coppia dell'articolazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Acquisizione dati di sensibilità del sensore di coppia dell'articolazione
    * @return Codice di errore
    */
    public int JointSensitivityCollect();

Ottieni il risultato della calibrazione della sensibilità del sensore di coppia dell'articolazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni il risultato della calibrazione della sensibilità del sensore di coppia dell'articolazione
    * @param [out] calibResult Sensibilità dell'articolazione j1~j6 [0-1]
    * @param [out] linearity Linearità dell'articolazione j1~j6 [0-1]
    * @return Codice di errore
    */
    public int JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Ottieni l'errore di isteresi del sensore di coppia dell'articolazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni l'errore di isteresi del sensore di coppia dell'articolazione
    * @param [out] hysteresisError Errore di isteresi dell'articolazione j1~j6
    * @return Codice di errore
    */
    public int JointHysteresisError(ref double[] hysteresisError);
    
Ottieni la ripetibilità del sensore di coppia dell'articolazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:
    
    /**
    * @brief Ottieni la ripetibilità del sensore di coppia dell'articolazione
    * @param [out] repeatability Ripetibilità del sensore di coppia dell'articolazione j1~j6
    * @return Codice di errore
    */
    public int JointRepeatability(ref double[] repeatability);
    
Imposta i parametri del sensore di forza dell'articolazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta i parametri del sensore di forza dell'articolazione
    * @param [in] M Coefficiente massa J1-J6 [0.001 ~ 10]
    * @param [in] B Coefficiente smorzamento J1-J6 [0.001 ~ 10]
    * @param [in] K Coefficiente rigidità J1-J6 [0.001 ~ 10]
    * @param [in] threshold Soglia controllo forza, Nm
    * @param [in] sensitivity Sensibilità, Nm/V, [0 ~ 10]
    * @param [in] setZeroFlag Flag abilitazione funzione; 0-Disabilita; 1-Abilita; 2-Registra zero posizione 1; 3-Registra zero posizione 2
    * @return Codice di errore
    */
    public int SetAdmittanceParams(double[] M, double[] B, double[] K, double[] threshold, double[] sensitivity, int setZeroFlag);

Esempio di codice per la calibrazione automatica della sensibilità del sensore di coppia dell'articolazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public int TestSensitivityCalib()
    {
        int rtn; 
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");

        JointPos curJPos = new JointPos(0, 0, 0, 0, 0, 0);
        robot.GetActualJointPosDegree(0, ref curJPos);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        JointPos[] jointPoses = new JointPos[]
        {
            new JointPos(curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5]),
            new JointPos(curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5])
        };
        for (int i = 0; i < jointPoses.Length; i++)
        {
            DescPose descPos = new DescPose(0, 0, 0, 0, 0, 0);
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            Thread.Sleep(i == 0 ? 200 : 100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {i + 1} rtn is {rtn}");
            Thread.Sleep(100);
        }

        for (int i = jointPoses.Length - 2; i >= 0; i--)
        {
            DescPose descPos = new DescPose();
            robot.GetForwardKin(jointPoses[i], ref descPos);
            robot.MoveJ(jointPoses[i], descPos, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            Thread.Sleep(100);
            rtn = robot.JointSensitivityCollect();
            Console.WriteLine($"JointSensitivityCollect {jointPoses.Length + (jointPoses.Length - 1 - i)} rtn is {rtn}");
            Thread.Sleep(100);
        }
        double[] calibResult = new double[6];
        double[] linearity = new double[6];
        rtn = robot.JointSensitivityCalibration(ref calibResult, ref linearity);
        Console.WriteLine($"JointSensitivityCalibration rtn is {rtn}");
        rtn = robot.JointSensitivityEnable(0);
        Console.WriteLine($"JointSensitivityEnable rtn is {rtn}");
        Console.WriteLine($"jointSensor Calib result is {calibResult[0]:F6} {calibResult[1]:F6} {calibResult[2]:F6} {calibResult[3]:F6} {calibResult[4]:F6} {calibResult[5]:F6}");
        Console.WriteLine($"jointSensor linearity is {linearity[0]:F6} {linearity[1]:F6} {linearity[2]:F6} {linearity[3]:F6} {linearity[4]:F6} {linearity[5]:F6}"); 
        double[] hysteresisError = new double[6];
        rtn = robot.JointHysteresisError(ref hysteresisError);
        Console.WriteLine($"JointHysteresisError result is {hysteresisError[0]:F6} {hysteresisError[1]:F6} {hysteresisError[2]:F6} {hysteresisError[3]:F6} {hysteresisError[4]:F6} {hysteresisError[5]:F6}");   
        double[] repeatability = new double[6];
        rtn = robot.JointRepeatability(ref repeatability);
        Console.WriteLine($"JointRepeatability result is {repeatability[0]:F6} {repeatability[1]:F6} {repeatability[2]:F6} {repeatability[3]:F6} {repeatability[4]:F6} {repeatability[5]:F6}");
        double[] M = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] B = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double[] K = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double[] threshold = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        Console.WriteLine($"SetAdmittanceParams rtn is {rtn}");
        robot.CloseRPC();
        return 0;
    }

Ottieni il numero di frame errati per le 8 porte slave del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni il numero di frame errati per le 8 porte slave del robot
    * @param [out] inRecvErr Numero frame di errore di ricezione in ingresso
    * @param [out] inCRCErr Numero frame di errore CRC in ingresso
    * @param [out] inTransmitErr Numero frame di errore di trasmissione in ingresso
    * @param [out] inLinkErr Numero frame di errore di collegamento in ingresso
    * @param [out] outRecvErr Numero frame di errore di ricezione in uscita
    * @param [out] outCRCErr Numero frame di errore CRC in uscita
    * @param [out] outTransmitErr Numero frame di errore di trasmissione in uscita
    * @param [out] outLinkErr Numero frame di errore di collegamento in uscita
    * @return Codice di errore
    */
    public int GetSlavePortErrCounter(ref int[] inRecvErr,ref int[] inCRCErr,ref int[] inTransmitErr,ref int[] inLinkErr,ref int[] outRecvErr,ref int[] outCRCErr,ref int[] outTransmitErr,ref int[] outLinkErr);

Azzera il conteggio dei frame errati della porta slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Azzera il conteggio dei frame errati della porta slave
    * @param [in] slaveID Numero slave 0~7
    * @return Codice di errore
    */
    public int SlavePortErrCounterClear(int slaveID);

Esempio di codice per ottenere i frame errati della porta slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    public void TestSlavePortErr()
    {
        int[] inRecvErr = new int[8];
        int[] inCRCErr = new int[8];
        int[] inTransmitErr = new int[8];
        int[] inLinkErr = new int[8];
        int[] outRecvErr = new int[8];
        int[] outCRCErr = new int[8];
        int[] outTransmitErr = new int[8];
        int[] outLinkErr = new int[8];

        robot.GetSlavePortErrCounter(ref inRecvErr, ref inCRCErr, ref inTransmitErr, ref inLinkErr,
            ref outRecvErr, ref outCRCErr, ref outTransmitErr, ref outLinkErr);

        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                Console.WriteLine($"inRecvErr {i} is {inRecvErr[i]}");
            }

            if (inCRCErr[i] != 0)
            {
                Console.WriteLine($"inCRCErr {i} is {inCRCErr[i]}");
            }

            if (inTransmitErr[i] != 0)
            {
                Console.WriteLine($"inTransmitErr {i} is {inTransmitErr[i]}");
            }

            if (inLinkErr[i] != 0)
            {
                Console.WriteLine($"inLinkErr {i} is {inLinkErr[i]}");
            }

            if (outRecvErr[i] != 0)
            {
                Console.WriteLine($"outRecvErr {i} is {outRecvErr[i]}");
            }

            if (outCRCErr[i] != 0)
            {
                Console.WriteLine($"outCRCErr {i} is {outCRCErr[i]}");
            }

            if (outTransmitErr[i] != 0)
            {
                Console.WriteLine($"outTransmitErr {i} is {outTransmitErr[i]}");
            }

            if (outLinkErr[i] != 0)
            {
                Console.WriteLine($"outLinkErr {i} is {outLinkErr[i]}");
            }
        }
        Console.WriteLine("others has no err!");

        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }

        robot.CloseRPC();
    }

Imposta il coefficiente di feedforward della velocità per ciascun asse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta il coefficiente di feedforward della velocità per ciascun asse
    * @param [in] radio Coefficiente di feedforward della velocità per ciascun asse
    * @return Codice di errore
    */
    public int SetVelFeedForwardRatio(double radio[6]);

Ottieni il coefficiente di feedforward della velocità per ciascun asse
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni il coefficiente di feedforward della velocità per ciascun asse
    * @param [out] radio Coefficiente di feedforward della velocità per ciascun asse
    * @return Codice di errore
    */
    public int GetVelFeedForwardRatio(ref double radio[6]);

Esempio di codice per impostare il feedforward di velocità del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestVelFeedForwardRatio()
    {

        double[] setRadio = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double[] getRadio = new double[6] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        robot.GetVelFeedForwardRatio(ref getRadio);
        Console.WriteLine($" {getRadio[0]:F6} {getRadio[1]:F6} {getRadio[2]:F6} {getRadio[3]:F6} {getRadio[4]:F6} {getRadio[5]:F6}");
    }

Calibrazione TCP Sensore Foto-elettrico - Calcolo RPY Strumento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico - Calcolo RPY Strumento
    * @param [in] Btool Posizione cartesiana del robot
    * @param [in] Etool Valori attuali delle coordinate dello strumento
    * @param [in] sensor Valori attuali delle coordinate del sensore (non ancora disponibile)
    * @param [in] radius Raggio del movimento circolare in mm (non ancora disponibile)
    * @param [in] dz Distanza di movimento lungo l'asse Z negativo del sistema di coordinate base; quando dz = 10000, la funzione restituisce direttamente l'RPY dello strumento
    * @param [out] TCPRPY Valori RPY dello strumento
    * @return Codice di errore
    */
    public int TCPComputeRPY(DescPose Btool, DescPose Etool, DescPose sensor, double radius, double dz, out Rpy TCPRPY);

Calibrazione TCP Sensore Foto-elettrico - Calcolo XYZ Strumento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico - Calcolo XYZ Strumento
    * @param [in] select 0-Calcola TCP strumento; 1-Calcola origine sensore; 2-Calcola orientamento sensore; 3-Restituisci direttamente TCP strumento; 4-Registra sistema di coordinate del pezzo corrente e sistema di coordinate dello strumento
    * @param [in] originDirection 0-Direzione X; 1-Direzione Y; 2-Direzione Z
    * @param [in] pos1 Posizione cartesiana robot 1
    * @param [in] pos2 Posizione cartesiana robot 2
    * @param [in] pos3 Posizione cartesiana robot 3
    * @param [in] pos4 Posizione cartesiana robot 4
    * @param [out] TCP Valori XYZ dello strumento
    * @return Codice di errore
    */
    public int TCPComputeXYZ(int select, double originDirection, DescTran pos1, DescTran pos2,DescTran pos3, DescTran pos4, out DescTran TCP);

Calibrazione TCP Sensore Foto-elettrico - Inizio Registrazione Posizione Centro Flangia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico - Inizio Registrazione Posizione Centro Flangia
    * @return Codice di errore
    */
    public int TCPRecordFlangePosStart();

Calibrazione TCP Sensore Foto-elettrico - Fine Registrazione Posizione Centro Flangia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico - Fine Registrazione Posizione Centro Flangia
    * @return Codice di errore
    */
    public int TCPRecordFlangePosEnd();

Calibrazione TCP Sensore Foto-elettrico - Ottieni Posizione Punto Centro Strumento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico - Ottieni Posizione Punto Centro Strumento
    * @param [out] TCP Posizione punto centro strumento (x, y, z)
    * @return Codice di errore
    */
    public int TCPGetRecordFlangePos(out DescTran TCP);

Calibrazione TCP Sensore Foto-elettrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Calibrazione TCP Sensore Foto-elettrico
    * @param [in] luaPath Percorso programma Lua per calibrazione automatica: "FR_CalibrateTheToolTcp.lua"
    * @param [out] TCP Sistema di coordinate dello strumento calibrato (x, y, z, rx, ry, rz)
    * @return Codice di errore
    */
    public int PhotoelectricSensorTCPCalibration(string luaPath, DescTran offset, out DescPose TCP);

Esempio Codice Calibrazione TCP Sensore Foto-elettrico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    public void TestPhotoelectricSensorTCPCalib()
    {
        ROBOT_STATE_PKG pkg =new ROBOT_STATE_PKG();
        DescTran offset = new DescTran( 10.0, 10.0, 3.0 );
        DescPose TCP = new DescPose();
        int rtn = robot.PhotoelectricSensorTCPCalibration("FR_CalibrateTheToolTcp.lua", offset, out TCP);
        Console.WriteLine($"PhotoelectricSensorTCPCalibration : {rtn}");
        Console.WriteLine($"Coordinate TCP Strumento: X={TCP.tran.x:F3}, Y={TCP.tran.y:F3}, Z={TCP.tran.z:F3}");
        Console.WriteLine($"Orientazione RPY Strumento: RX={TCP.rpy.rx:F3}, RY={TCP.rpy.ry:F3}, RZ={TCP.rpy.rz:F3}");
    }

Imposta la Velocità Globale in Tempo Reale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta la velocità globale in tempo reale
    * @param [in] vel Percentuale di velocità, intervallo [0~100]
    * @return Codice errore
    */
    public int SetWeaveOffsetRT(DescPose offset)