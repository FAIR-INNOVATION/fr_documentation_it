Impostazioni Comuni del Robot
=============================

.. toctree::
   :maxdepth: 5

Impostare il punto di riferimento dello strumento - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta il punto di riferimento dello strumento - Metodo a sei punti
    * @param [in] point_num Numero del punto, intervallo [1~6]
    * @return Codice di errore
    */
   errno_t SetToolPoint(int point_num);

Calcolare il sistema di coordinate dello strumento
++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Calcola il sistema di coordinate dello strumento
    * @param [out] tcp_pose Sistema di coordinate dello strumento
    * @return Codice di errore
    */
   errno_t ComputeTool(DescPose *tcp_pose);

Impostare il punto di riferimento dello strumento - Metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta il punto di riferimento dello strumento - Metodo a quattro punti
    * @param [in] point_num Numero del punto, intervallo [1~4]
    * @return Codice di errore
    */
   errno_t SetTcp4RefPoint(int point_num);

Calcolare il sistema di coordinate dello strumento
++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Calcola il sistema di coordinate dello strumento
    * @param [out] tcp_pose Sistema di coordinate dello strumento
    * @return Codice di errore
    */
   errno_t ComputeTcp4(DescPose *tcp_pose);

Calcolare il sistema di coordinate dello strumento in base alle informazioni sui punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Calcola il sistema di coordinate dello strumento in base alle informazioni sui punti
    * @param [in] method Metodo di calcolo; 0-Metodo a quattro punti; 1-Metodo a sei punti
    * @param [in] pos Gruppo di posizioni articolari, lunghezza array 4 per metodo a quattro punti, 6 per metodo a sei punti
    * @param [out] coord Risultato del sistema di coordinate dello strumento
    * @return Codice di errore
    */
   errno_t ComputeToolCoordWithPoints(int method, JointPos pos[], DescPose& coord);

Impostare il sistema di coordinate dello strumento
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il sistema di coordinate dello strumento
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del centro dello strumento rispetto al centro della flangia terminale
    * @param  [in] type  0-Sistema di coordinate dello strumento, 1-Sistema di coordinate del sensore
    * @param  [in] install Posizione di installazione, 0-Terminale del robot, 1-Esterno del robot
    * @param  [in] toolID ID dello strumento
    * @param  [in] loadNum Numero del carico
    * @return  Codice di errore
    */
   errno_t SetToolCoord(int id, DescPose *coord, int type, int install, int toolID, int loadNum);

Impostare l'elenco dei sistemi di coordinate dello strumento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta l'elenco dei sistemi di coordinate dello strumento
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del centro dello strumento rispetto al centro della flangia terminale
    * @param  [in] type  0-Sistema di coordinate dello strumento, 1-Sistema di coordinate del sensore
    * @param  [in] install Posizione di installazione, 0-Terminale del robot, 1-Esterno del robot
    * @param  [in] loadNum Numero del carico
    * @return  Codice di errore
    */
   errno_t SetToolList(int id, DescPose *coord, int type, int install, int loadNum);

Ottenere il sistema di coordinate dello strumento corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni il sistema di coordinate dello strumento corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate dello strumento
    * @return  Codice di errore
    */
   errno_t  GetTCPOffset(uint8_t flag, DescPose *desc_pos);

Esempio di codice per operazioni sul sistema di coordinate dello strumento del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestTCPCompute(void)
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
        DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
        JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
        DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
        JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
        DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
        JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
        DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
        JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
        DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
        JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
        DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
        JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
        ExaxisPos exaxisPos(0, 0, 0, 0);
        DescPose offdese(0, 0, 0, 0, 0, 0);
        JointPos posJ[6] = { p1Joint , p2Joint , p3Joint , p4Joint , p5Joint , p6Joint };
        DescPose coordRtn = {};
        rtn = robot.ComputeToolCoordWithPoints(1, posJ, coordRtn);
        printf("ComputeToolCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(1);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(2);
        robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(3);
        robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(4);
        robot.MoveJ(&p5Joint, &p5Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(5);
        robot.MoveJ(&p6Joint, &p6Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetToolPoint(6);
        rtn = robot.ComputeTool(&coordRtn);
        printf("6 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.SetToolList(1, &coordRtn, 0, 0, 0);
        robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetTcp4RefPoint(1);
        robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetTcp4RefPoint(2);
        robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetTcp4RefPoint(3);
        robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
        robot.SetTcp4RefPoint(4);
        rtn = robot.ComputeTcp4(&coordRtn);
        printf("4 Point ComputeTool        %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.SetToolCoord(2, &coordRtn, 0, 0, 1, 0);
        DescPose getCoord = {};
        rtn = robot.GetTCPOffset(0, &getCoord);
        printf("GetTCPOffset    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
        robot.CloseRPC();
        return 0;
    }

Impostare il punto di riferimento dello strumento esterno - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta il punto di riferimento dello strumento esterno - Metodo a sei punti
    * @param [in] point_num Numero del punto, intervallo [1~4]
    * @return Codice di errore
    */
   errno_t SetExTCPPoint(int point_num);

Calcolare il sistema di coordinate dello strumento esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Calcola il sistema di coordinate dello strumento esterno
    * @param [out] tcp_pose Sistema di coordinate dello strumento esterno
    * @return Codice di errore
    */
   errno_t ComputeExTCF(DescPose *tcp_pose);

Impostare il sistema di coordinate dello strumento esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il sistema di coordinate dello strumento esterno
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] etcp  Posa del centro dello strumento rispetto al centro della flangia terminale
    * @param  [in] etool  Da determinare
    * @return  Codice di errore
    */
   errno_t  SetExToolCoord(int id, DescPose *etcp, DescPose *etool);

Impostare l'elenco dei sistemi di coordinate dello strumento esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.2.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta l'elenco dei sistemi di coordinate dello strumento esterno
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] etcp  Posa del centro dello strumento rispetto al centro della flangia terminale
    * @param  [in] etool  Da determinare
    * @return  Codice di errore
    */
   errno_t  SetExToolList(int id, DescPose *etcp, DescPose *etool);

Esempio di codice per operazioni sul sistema di coordinate dello strumento esterno del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestExtCoord(void)
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
       DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
       JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
       DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
       JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
       DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
       JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
       ExaxisPos exaxisPos(0, 0, 0, 0);
       DescPose offdese(0, 0, 0, 0, 0, 0);
       DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
       DescPose coordRtn = {};
       robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(1);
       robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(2);
       robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
       robot.SetExTCPPoint(3);
       rtn = robot.ComputeExTCF(&coordRtn);
       printf("ComputeExTCF          %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
       robot.SetExToolCoord(1, &coordRtn, &offdese);
       robot.SetExToolList(1, &coordRtn, &offdese);
       robot.CloseRPC();
       return 0;
    }

Impostare il punto di riferimento del pezzo - Metodo a tre punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta il punto di riferimento del pezzo - Metodo a tre punti
    * @param [in] point_num Numero del punto, intervallo [1~3]
    * @return Codice di errore
    */
   errno_t SetWObjCoordPoint(int point_num);

Calcolare il sistema di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Calcola il sistema di coordinate del pezzo
    * @param [in] method Metodo di calcolo 0: Origine-asse X-asse Z  1: Origine-asse X-piano XY
    * @param [in] refFrame Sistema di coordinate di riferimento
    * @param [out] wobj_pose Sistema di coordinate del pezzo
    * @return Codice di errore
    */
   errno_t ComputeWObjCoord(int method, int refFrame, DescPose *wobj_pose);

Impostare il sistema di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il sistema di coordinate del pezzo
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del sistema di coordinate del pezzo rispetto al centro della flangia terminale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */
   errno_t SetWObjCoord(int id, DescPose *coord, int refFrame);

Impostare l'elenco dei sistemi di coordinate del pezzo
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.5.0

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta l'elenco dei sistemi di coordinate del pezzo
    * @param  [in] id Numero del sistema di coordinate, intervallo [0~14]
    * @param  [in] coord  Posa del sistema di coordinate del pezzo rispetto al centro della flangia terminale
    * @param  [in] refFrame Sistema di coordinate di riferimento
    * @return  Codice di errore
    */
   errno_t SetWObjList(int id, DescPose *coord, int refFrame);

Calcolare il sistema di coordinate del pezzo in base alle informazioni sui punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief Calcola il sistema di coordinate del pezzo in base alle informazioni sui punti
    * @param [in] method Metodo di calcolo; 0: Origine-asse X-asse Z  1: Origine-asse X-piano XY
    * @param [in] pos Gruppo di tre posizioni TCP
    * @param [in] refFrame Sistema di coordinate di riferimento
    * @param [out] coord Risultato del sistema di coordinate del pezzo
    * @return Codice di errore
    */
   errno_t ComputeWObjCoordWithPoints(int method, DescPose pos[], int refFrame, DescPose& coord);

Ottenere il sistema di coordinate del pezzo corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni il sistema di coordinate del pezzo corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] desc_pos Posa del sistema di coordinate del pezzo
    * @return  Codice di errore
    */
   errno_t  GetWObjOffset(uint8_t flag, DescPose *desc_pos);

Esempio di codice per operazioni sul sistema di coordinate del pezzo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

     int TestWobjCoord(void)
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
         DescPose p1Desc(-89.606, 779.517, 193.516, 178.000, 0.476, -92.484);
         JointPos p1Joint(-108.145, -50.137, 85.818, -125.599, -87.946, 74.329);
         DescPose p2Desc(-24.656, 850.384, 191.361, 177.079, -2.058, -95.355);
         JointPos p2Joint(-111.024, -41.538, 69.222, -114.913, -87.743, 74.329);
         DescPose p3Desc(-99.813, 766.661, 241.878, -176.817, 1.917, -91.604);
         JointPos p3Joint(-107.266, -56.116, 85.971, -122.560, -92.548, 74.331);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         DescPose posTCP[3] = { p1Desc , p2Desc , p3Desc };
         DescPose coordRtn = {};
         rtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0, coordRtn);
         printf("ComputeWObjCoordWithPoints    %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.MoveJ(&p1Joint, &p1Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(1);
         robot.MoveJ(&p2Joint, &p2Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(2);
         robot.MoveJ(&p3Joint, &p3Desc, 1, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.SetWObjCoordPoint(3);
         rtn = robot.ComputeWObjCoord(1, 0, &coordRtn);
         printf("ComputeWObjCoord                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.SetWObjCoord(1, &coordRtn, 0);
         robot.SetWObjList(1, &coordRtn, 0);
         DescPose getWobjDesc = {};
         rtn = robot.GetWObjOffset(0, &getWobjDesc);
         printf("GetWObjOffset                   %d  coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
         robot.CloseRPC();
         return 0;
     }

Impostare la velocità globale
+++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta la velocità globale
    * @param  [in]  vel  Percentuale di velocità, intervallo [0~100]
    * @return  Codice di errore
    */
   errno_t  SetSpeed(int vel);

Impostare l'accelerazione del robot
++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta l'accelerazione del robot
    * @param [in] acc Percentuale di accelerazione del robot
    * @return Codice di errore
    */
   errno_t SetOaccScale(double acc);

Ottenere la velocità predefinita del robot
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni la velocità predefinita del robot
    * @param  [out]  vel  Velocità, unità mm/s
    * @return  Codice di errore
    */
   errno_t  GetDefaultTransVel(float *vel);

Impostare il peso del carico terminale
++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.8-3.7.8

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il peso del carico terminale
    * @param  [in] loadNum Numero del carico
    * @param  [in] weight  Peso del carico, unità kg
    * @return  Codice di errore
    */
   errno_t SetLoadWeight(int loadNum = 0, float weight);

Impostare le coordinate del centro di massa del carico terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C++SDK-v3.8.6

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta le coordinate del centro di massa del carico terminale
    * @param [in] loadNum Numero del carico
    * @param [in] coord Coordinate del centro di massa, unità mm
    * @return Codice di errore
    */
   errno_t SetLoadCoord(int loadNum, DescTran* coord);

Ottenere il peso del carico corrente
++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni il peso del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] weight Peso del carico, unità kg
    * @return  Codice di errore
    */
   errno_t  GetTargetPayload(uint8_t flag, float *weight);

Ottenere il centro di massa del carico corrente
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni il centro di massa del carico corrente
    * @param  [in] flag 0-Bloccante, 1-Non bloccante
    * @param  [out] cog Centro di massa del carico, unità mm
    * @return  Codice di errore
    */
   errno_t  GetTargetPayloadCog(uint8_t flag, DescTran *cog);

Impostare il metodo di installazione del robot
++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il metodo di installazione del robot
    * @param  [in] install  Metodo di installazione, 0-Installazione verticale, 1-Installazione laterale, 2-Installazione a testa in giù
    * @return  Codice di errore
    */
   errno_t  SetRobotInstallPos(uint8_t install);

Impostare l'angolo di installazione del robot
++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta l'angolo di installazione del robot, installazione libera
    * @param  [in] yangle  Angolo di inclinazione
    * @param  [in] zangle  Angolo di rotazione
    * @return  Codice di errore
    */
   errno_t  SetRobotInstallAngle(double yangle, double zangle);

Ottenere l'angolo di installazione del robot
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni l'angolo di installazione del robot
    * @param  [out] yangle Angolo di inclinazione
    * @param  [out] zangle Angolo di rotazione
    * @return  Codice di errore
    */
   errno_t  GetRobotInstallAngle(float *yangle, float *zangle);

Impostare il valore della variabile di sistema
++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta il valore della variabile di sistema
    * @param  [in]  id  Numero della variabile, intervallo [1~20]
    * @param  [in]  value Valore della variabile
    * @return  Codice di errore
    */
   errno_t  SetSysVarValue(int id, float value);

Ottenere il valore della variabile di sistema
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Ottieni il valore della variabile di sistema
    * @param  [in] id Numero della variabile di sistema, intervallo [1~20]
    * @param  [out] value  Valore della variabile di sistema
    * @return  Codice di errore
    */
   errno_t  GetSysVarValue(int id, float *value);

Esempio di codice per impostazioni comuni del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

     int TestLoadInstall(void)
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
         for (int i = 1; i < 100; i++)
         {
             robot.SetSpeed(i);
             robot.SetOaccScale(i);
             robot.Sleep(30);
         }
         float defaultVel = 0.0;
         robot.GetDefaultTransVel(&defaultVel);
         printf("GetDefaultTransVel is %f\n", defaultVel);
         for (int i = 1; i < 21; i++)
         {
             robot.SetSysVarValue(i, i + 0.5);
             robot.Sleep(100);
         }
         for (int i = 1; i < 21; i++)
         {
             float value = 0;
             robot.GetSysVarValue(i, &value);
             printf("sys value  %d is :%f\n", i, value);
             robot.Sleep(100);
         }
         robot.SetLoadWeight(0, 2.5);
         DescTran loadCoord = {};
         loadCoord.x = 3.0;
         loadCoord.y = 4.0;
         loadCoord.z = 5.0;
         robot.SetLoadCoord(&loadCoord);
         robot.Sleep(1000);
         float getLoad = 0.0;
         robot.GetTargetPayload(0, &getLoad);
         DescTran getLoadTran = {};
         robot.GetTargetPayloadCog(0, &getLoadTran);
         printf("get load is %f; get load cog is %f %f %f\n", getLoad, getLoadTran.x, getLoadTran.y, getLoadTran.z);
         robot.SetRobotInstallPos(0);
         robot.SetRobotInstallAngle(15.0, 25.0);
         float anglex = 0.0;
         float angley = 0.0;
         robot.GetRobotInstallAngle(&anglex, &angley);
         printf("GetRobotInstallAngle x:  %f;  y:  %f\n", anglex, angley);
         robot.CloseRPC();
         return 0;
     }

Interruttore compensazione attrito giunti
++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Interruttore compensazione attrito giunti
    * @param  [in]  state  0-Spegni, 1-Accendi
    * @return  Codice di errore
    */
   errno_t  FrictionCompensationOnOff(uint8_t state);

Impostare coefficienti compensazione attrito giunti - Installazione verticale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta coefficienti compensazione attrito giunti - Installazione verticale
    * @param  [in]  coeff Sei coefficienti di compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
   errno_t  SetFrictionValue_level(float coeff[6]);

Impostare coefficienti compensazione attrito giunti - Installazione laterale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta coefficienti compensazione attrito giunti - Installazione laterale
    * @param  [in]  coeff Sei coefficienti di compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
   errno_t  SetFrictionValue_wall(float coeff[6]);

Impostare coefficienti compensazione attrito giunti - Installazione a testa in giù
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta coefficienti compensazione attrito giunti - Installazione a testa in giù
    * @param  [in]  coeff Sei coefficienti di compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
   errno_t  SetFrictionValue_ceiling(float coeff[6]);

Impostare coefficienti compensazione attrito giunti - Installazione libera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Imposta coefficienti compensazione attrito giunti - Installazione libera
    * @param  [in]  coeff Sei coefficienti di compensazione giunti, intervallo [0~1]
    * @return  Codice di errore
    */
   errno_t  SetFrictionValue_freedom(float coeff[6]);

Esempio di codice per impostazione compensazione attrito giunti del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestFriction(void)
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
       float lcoeff[6] = { 0.9,0.9,0.9,0.9,0.9,0.9 };
       float wcoeff[6] = { 0.4,0.4,0.4,0.4,0.4,0.4 };
       float ccoeff[6] = { 0.6,0.6,0.6,0.6,0.6,0.6 };
       float fcoeff[6] = { 0.5,0.5,0.5,0.5,0.5,0.5 };
       rtn = robot.FrictionCompensationOnOff(1);
       printf("FrictionCompensationOnOff rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_level(lcoeff);
       printf("SetFrictionValue_level rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_wall(wcoeff);
       printf("SetFrictionValue_wall rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_ceiling(ccoeff);
       printf("SetFrictionValue_ceiling rtn is %d\n", rtn);
       rtn = robot.SetFrictionValue_freedom(fcoeff);
       printf("SetFrictionValue_freedom rtn is %d\n", rtn);
       robot.CloseRPC();
       return 0;
    }

Interrogare codice errore robot
++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Interroga codice errore robot
    * @param  [out]  maincode  Codice errore principale
    * @param  [out]  subcode   Codice errore secondario
    * @return  Codice di errore
    */
   errno_t  GetRobotErrorCode(int *maincode, int *subcode);

Cancellazione stato errore
++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief  Cancellazione stato errore
    * @return  Codice di errore
    */
   errno_t  ResetAllError();

Esempio di codice per ottenimento stato guasto robot e cancellazione errori
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestGetError(void)
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
       int maincode, subcode;
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.ResetAllError();
       robot.Sleep(1000);
       robot.GetRobotErrorCode(&maincode, &subcode);
       printf("robot maincode is %d; subcode is %d\n", maincode, subcode);
       robot.CloseRPC();
       return 0;
    }

Impostare parametri monitoraggio temperatura e corrente ventole centralina a tensione ampia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta parametri monitoraggio temperatura e corrente ventole centralina a tensione ampia
    * @param [in] enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    * @param [in] period Periodo monitoraggio (s), intervallo 1-100
    * @return Codice di errore
    */
   errno_t SetWideBoxTempFanMonitorParam(int enable, int period);

Ottenere parametri monitoraggio temperatura e corrente ventole centralina a tensione ampia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene parametri monitoraggio temperatura e corrente ventole centralina a tensione ampia
    * @param [out] enable 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    * @param [out] period Periodo monitoraggio (s), intervallo 1-100
    * @return Codice di errore
    */
   errno_t GetWideBoxTempFanMonitorParam(int &enable, int &period);

Esempio di codice per ottenimento stato temperatura e corrente ventole centralina a tensione ampia
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

     int TestWideVoltageCtrlBoxtemp(void)
     {
         ROBOT_STATE_PKG pkg = {};
         FRRobot robot;
         robot.LoggerInit();
         robot.SetLoggerLevel(1);
         int rtn = robot.RPC("192.168.58.2");
         printf("robot rpc rtn is %d\n", rtn);
         if (rtn != 0)
         {
             return -1;
         }
         robot.SetReConnectParam(true, 30000, 500);
         robot.SetWideBoxTempFanMonitorParam(1, 2);
         int enable = 0;
         int period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         rtn = robot.SetWideBoxTempFanMonitorParam(0, 2);
         printf("SetWideBoxTempFanMonitorParam rtn is %d\n", rtn);
         enable = 0;
         period = 0;
         robot.GetWideBoxTempFanMonitorParam(enable, period);
         printf("GetWideBoxTempFanMonitorParam enable is %d   period is %d\n", enable, period);
         for (int i = 0; i < 100; i++)
         {
             robot.GetRobotRealTimeState(&pkg);
             printf("robot ctrl box temp is %f,  fan current is %d\n", pkg.wideVoltageCtrlBoxTemp, pkg.wideVoltageCtrlBoxFanCurrent);
             robot.Sleep(100);
         }
         robot.CloseRPC();
         robot.Sleep(2000);
         return 0;
     }

Calcolare risultato calibrazione fuoco
++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Calcola risultato calibrazione fuoco
    * @param [in] pointNum Numero punti calibrazione
    * @param [out] resultPos Risultato calibrazione XYZ
    * @param [out] accuracy Precisione errore calibrazione
    * @return Codice di errore
    */
   errno_t ComputeFocusCalib(int pointNum, DescTran& resultPos, float& accuracy);

Impostare coordinate fuoco
++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta coordinate fuoco
    * @param [in] pos Coordinate fuoco XYZ
    * @return Codice di errore
    */
   errno_t SetFocusPosition(DescTran pos);

Avviare inseguimento fuoco
++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Avvia inseguimento fuoco
    * @param [in] kp Parametro proporzionale, default 50.0
    * @param [in] kpredict Parametro feedforward, default 19.0
    * @param [in] aMax Limite massima accelerazione angolare, default 1440°/s^2
    * @param [in] vMax Limite massima velocità angolare, default 180°/s
    * @param [in] type Blocca direzione asse X (0-Vettore input riferimento; 1-Orizzontale; 2-Verticale)
    * @return Codice di errore
    */
   errno_t FocusStart(double kp, double kpredict, double aMax, double vMax, int type);

Fermare inseguimento fuoco
++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ferma inseguimento fuoco
    * @return Codice di errore
    */
   errno_t FocusEnd();

Esempio di codice per inseguimento fuoco robot
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestFocus()
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
      DescPose p1Desc(186.331, 487.913, 209.850, 149.030, 0.688, -114.347);
      JointPos p1Joint(-127.876, -75.341, 115.417, -122.741, -59.820, 74.300);
      DescPose p2Desc(69.721, 535.073, 202.882, -144.406, -14.775, -89.012);
      JointPos p2Joint(-101.780, -69.828, 110.917, -125.740, -127.841, 74.300);
      DescPose p3Desc(146.861, 578.426, 205.598, 175.997, -36.178, -93.437);
      JointPos p3Joint(-112.851, -60.191, 86.566, -80.676, -97.463, 74.300);
      DescPose p4Desc(136.284, 509.876, 225.613, 178.987, 1.372, -100.696);
      JointPos p4Joint(-116.397, -76.281, 113.845, -128.611, -88.654, 74.299);
      DescPose p5Desc(138.395, 505.972, 298.016, 179.134, 2.147, -101.110);
      JointPos p5Joint(-116.814, -82.333, 109.162, -118.662, -88.585, 74.302);
      DescPose p6Desc(105.553, 454.325, 232.017, -179.426, 0.444, -99.952);
      JointPos p6Joint(-115.649, -84.367, 122.447, -128.663, -90.432, 74.303);
      ExaxisPos exaxisPos(0, 0, 0, 0);
      DescPose offdese(0, 0, 100, 0, 0, 0);
      robot.MoveJ(&p1Joint, &p1Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(1);
      robot.MoveJ(&p2Joint, &p2Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(2);
      robot.MoveJ(&p3Joint, &p3Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(3);
      robot.MoveJ(&p4Joint, &p4Desc, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
      robot.SetTcp4RefPoint(4);
      DescPose coordRtn = {};
      rtn = robot.ComputeTcp4(&coordRtn);
      printf("4 Point ComputeTool    %d coord is %f %f %f %f %f %f \n", rtn, coordRtn.tran.x, coordRtn.tran.y, coordRtn.tran.z, coordRtn.rpy.rx, coordRtn.rpy.ry, coordRtn.rpy.rz);
      robot.SetToolCoord(1, &coordRtn, 0, 0, 1, 0);
      robot.GetForwardKin(&p1Joint, &p1Desc);
      robot.GetForwardKin(&p2Joint, &p2Desc);
      robot.GetForwardKin(&p3Joint, &p3Desc);
      robot.SetFocusCalibPoint(1, p1Desc);
      robot.SetFocusCalibPoint(2, p2Desc);
      robot.SetFocusCalibPoint(3, p3Desc);
      DescTran resultPos = {};
      float accuracy = 0.0;
      rtn = robot.ComputeFocusCalib(3, resultPos, accuracy);
      printf("ComputeFocusCalib coord is %d %f %f %f accuracy is %f\n", rtn, resultPos.x, resultPos.y, resultPos.z, accuracy);
      rtn = robot.SetFocusPosition(resultPos);
      robot.GetForwardKin(&p5Joint, &p5Desc);
      robot.GetForwardKin(&p6Joint, &p6Desc);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusStart(50, 19, 710, 90, 0);
      robot.MoveL(&p5Joint, &p5Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.MoveL(&p6Joint, &p6Desc, 1, 0, 10, 100, 100, -1, 0, &exaxisPos, 0, 1, &offdese);
      robot.FocusEnd();
      robot.CloseRPC();
      return 0;
    }

Abilitare funzione calibrazione sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Abilita funzione calibrazione sensibilità sensore coppia giunti
    * @param [in] status 0-Disabilita; 1-Abilita
    * @return  Codice di errore
    */
   errno_t JointSensitivityEnable(int status);

Acquisizione dati sensibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Acquisizione dati sensibilità sensore coppia giunti
    * @return Codice di errore
    */
   errno_t JointSensitivityCollect();

Ottenere risultato calibrazione sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene risultato calibrazione sensibilità sensore coppia giunti
    * @param [out] calibResult Sensibilità giunti j1~j6 [0-1]
    * @param [out] linearity Linearità giunti j1~j6 [0-1]
    * @return Codice di errore
    */
   errno_t JointSensitivityCalibration(double calibResult[6], double linearity[6]);

Ottenere errore isteresi sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene errore isteresi sensore coppia giunti
    * @param [out] hysteresisError Errore isteresi giunti j1~j6
    * @return Codice di errore
    */
   errno_t JointHysteresisError(double hysteresisError[6]);

Ottenere ripetibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene ripetibilità sensore coppia giunti
    * @param [out] repeatability Ripetibilità sensore coppia giunti j1~j6
    * @return Codice di errore
    */
   errno_t JointRepeatability(double repeatability[6]);

Impostare parametri sensore forza giunti
+++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta parametri sensore forza giunti
    * @param [in] M Coefficiente massa J1-J6 [0.001 ~ 10]
    * @param [in] B Coefficiente smorzamento J1-J6 [0.001 ~ 10]
    * @param [in] K Coefficiente rigidità J1-J6 [0.001 ~ 10]
    * @param [in] threshold Soglia controllo forza, Nm
    * @param [in] sensitivity Sensibilità, Nm/V, [0 ~ 10]
    * @param [in] setZeroFlag Flag abilitazione funzione; 0-Disabilita; 1-Abilita; 2-Registra zero posizione 1; 3-Registra zero posizione 2
    * @return Codice di errore
    */
   errno_t SetAdmittanceParams(double M[6], double B[6], double K[6], double threshold[6], double sensitivity[6], int setZeroFlag);

Esempio di codice per calibrazione automatica sensibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestSensitivityCalib()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        robot.SetReConnectParam(true, 30000, 500);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return 0;
        }
        rtn = robot.JointSensitivityEnable(0);
        rtn = robot.JointSensitivityEnable(1);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        JointPos curJPos = {};
        robot.GetActualJointPosDegree(0, &curJPos);
        ExaxisPos epos = { 0,0,0,0 };
        DescPose offset_pos = { 0,0,0,0,0,0 };
        JointPos jointPos1 = { curJPos.jPos[0], 0, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos1 = {};
        robot.GetForwardKin(&jointPos1, &descPos1);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 1 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos2 = { curJPos.jPos[0], -30, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos2 = {};
        robot.GetForwardKin(&jointPos2, &descPos2);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 2 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos3 = { curJPos.jPos[0], -60, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos3 = {};
        robot.GetForwardKin(&jointPos3, &descPos3);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 3 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos4 = { curJPos.jPos[0], -90, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos4 = {};
        robot.GetForwardKin(&jointPos4, &descPos4);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 4 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos5 = { curJPos.jPos[0], -120, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos5 = {};
        robot.GetForwardKin(&jointPos5, &descPos5);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 5 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos6 = { curJPos.jPos[0], -150, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos6 = {};
        robot.GetForwardKin(&jointPos6, &descPos6);
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 6 rtn is %d\n", rtn);
        robot.Sleep(100);
        JointPos jointPos7 = { curJPos.jPos[0], -180, 0, -90, 0.02, curJPos.jPos[5] };
        DescPose descPos7 = {};
        robot.GetForwardKin(&jointPos7, &descPos7);
        robot.MoveJ(&jointPos7, &descPos7, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 7 rtn is %d\n", rtn);
        robot.Sleep(100);
        //-------------------
        robot.MoveJ(&jointPos6, &descPos6, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 8 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos5, &descPos5, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 9 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos4, &descPos4, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 10 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos3, &descPos3, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 11 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos2, &descPos2, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(100);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 12 rtn is %d\n", rtn);
        robot.Sleep(100);
        robot.MoveJ(&jointPos1, &descPos1, 0, 0, 100, 100, 100, &epos, -1, 0, &offset_pos);
        robot.Sleep(200);
        rtn = robot.JointSensitivityCollect();
        printf("JointSensitivityCollect 13 rtn is %d\n", rtn);
        robot.Sleep(100);
        double calibResult[6] = { 0.0 };
        double linearity[6] = { 0.0 };
        rtn = robot.JointSensitivityCalibration(calibResult, linearity);
        printf("JointSensitivityCalibration rtn is %d\n", rtn);
        rtn = robot.JointSensitivityEnable(0);
        printf("JointSensitivityEnable rtn is %d\n", rtn);
        printf("jointSensor Calib result is %f %f %f %f %f %f\njointSensor linearity is %f %f %f %f %f %f\n",
            calibResult[0], calibResult[1], calibResult[2],
            calibResult[3], calibResult[4], calibResult[5],
            linearity[0], linearity[1], linearity[2],
            linearity[3], linearity[4], linearity[5]);
        double hysteresisError[6] = { 0.0 };
        rtn = robot.JointHysteresisError(hysteresisError);
        printf("JointHysteresisError result is %f %f %f %f %f %f\n",
            hysteresisError[0], hysteresisError[1], hysteresisError[2],
            hysteresisError[3], hysteresisError[4], hysteresisError[5]);
        double repeatability[6] = { 0.0 };
        rtn = robot.JointRepeatability(repeatability);
        printf("JointRepeatability result is %f %f %f %f %f %f\n",
            repeatability[0], repeatability[1], repeatability[2],
            repeatability[3], repeatability[4], repeatability[5]);
        double M[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double B[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        double K[6] = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        double threshold[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        int setZeroFlag = 1;
        rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag);
        printf("SetAdmittanceParams rtn is %d\n", rtn);
        robot.CloseRPC();
    }

Ottenere numero frame errori 8 porte slave robot
+++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene numero frame errori 8 porte slave robot
    * @param [out] inRecvErr Numero frame errori ricezione input
    * @param [out] inCRCErr Numero frame errori CRC input
    * @param [out] inTransmitErr Numero frame errori trasmissione input
    * @param [out] inLinkErr Numero frame errori collegamento input
    * @param [out] outRecvErr Numero frame errori ricezione output
    * @param [out] outCRCErr Numero frame errori CRC output
    * @param [out] outTransmitErr Numero frame errori trasmissione output
    * @param [out] outLinkErr Numero frame errori collegamento output
    * @return Codice di errore
    */
   errno_t GetSlavePortErrCounter(int inRecvErr[8], int inCRCErr[8], int inTransmitErr[8], int inLinkErr[8], int outRecvErr[8], int outCRCErr[8], int outTransmitErr[8], int outLinkErr[8]);

Azzeramento frame errori porte slave
+++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Azzeramento frame errori porte slave
    * @param [in] slaveID Numero slave 0~7
    * @return Codice di errore
    */
   errno_t SlavePortErrCounterClear(int slaveID);

Esempio di codice per ottenimento frame errori porte slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestSlavePortErr()
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
        int inRecvErr[8] = {0.0};
        int inCRCErr[8] = { 0.0 };
        int inTransmitErr[8] = { 0.0 };
        int inLinkErr[8] = { 0.0 };
        int outRecvErr[8] = { 0.0 };
        int outCRCErr[8] = { 0.0 };
        int outTransmitErr[8] = { 0.0 };
        int outLinkErr[8] = { 0.0 };
        robot.GetSlavePortErrCounter(inRecvErr,  inCRCErr, inTransmitErr, inLinkErr,
            outRecvErr, outCRCErr, outTransmitErr, outLinkErr);
        for (int i = 0; i < 8; i++)
        {
            if (inRecvErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inRecvErr[i]);
            }
            if (inCRCErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inCRCErr[i]);
            }
            if (inTransmitErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inTransmitErr[i]);
            }
            if (inLinkErr[i] != 0)
            {
                printf("inRecvErr %d is %d\n", i, inLinkErr[i]);
            }
            if (outRecvErr[i] != 0)
            {
                printf("outRecvErr %d is %d\n", i, outRecvErr[i]);
            }
            if (outCRCErr[i] != 0)
            {
                printf("outCRCErr %d is %d\n", i, outCRCErr[i]);
            }
            if (outTransmitErr[i] != 0)
            {
                printf("outTransmitErr %d is %d\n", i, outTransmitErr[i]);
            }
            if (outLinkErr[i] != 0)
            {
                printf("outLinkErr %d is %d\n", i, outLinkErr[i]);
            }
        }
        printf("others has no err!\n");
        for (int i = 0; i < 8; i++)
        {
            robot.SlavePortErrCounterClear(i);
        }
        robot.CloseRPC();
        return 0;
    }

Impostare coefficiente feedforward velocità assi
+++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Imposta coefficiente feedforward velocità assi
    * @param [in] radio Coefficiente feedforward velocità assi
    * @return Codice di errore
    */
   errno_t SetVelFeedForwardRatio(double radio[6]);

Ottenere coefficiente feedforward velocità assi
++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

   /**
    * @brief Ottiene coefficiente feedforward velocità assi
    * @param [out] radio Coefficiente feedforward velocità assi
    * @return Codice di errore
    */
   errno_t GetVelFeedForwardRatio(double radio[6]);

Esempio di codice per coefficiente feedforward velocità robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
   :linenos:

    int TestVelFeedForwardRatio()
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
        double setRadio[6] = { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
        robot.SetVelFeedForwardRatio(setRadio);
        double getRadio[6] = { 0.0 };
        robot.GetVelFeedForwardRatio(getRadio);
        printf(" %f %f %f %f %f %f\n", getRadio[0], getRadio[1], getRadio[2], getRadio[3], getRadio[4], getRadio[5]);
        robot.CloseRPC();
        return 0;
    }