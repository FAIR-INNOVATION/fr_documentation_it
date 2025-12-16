Controllo della Forza del Robot
===============================

.. toctree:: 
    :maxdepth: 5

Configurazione Sensore di Forza/Coppia
+++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
	 * @brief  Configura il sensore di forza/coppia
	 * @param  [in] company  Produttore del sensore di forza/coppia, 17-Kunwei Tech, 19-Aerospace 11th Academy, 20-ATI Sensor, 21-Zhongke Midian, 22-Weihang Minxin, 23-NBIT, 24-Xin Jingcheng (XJC), 26-NSR
	 * @param  [in] device  Numero dispositivo, Kunwei(0-KWR75B), Aerospace 11th Academy(0-MCS6A-200-4), ATI(0-AXIA80-M8), Zhongke Midian(0-MST2010), Weihang Minxin(0-WHC6L-YB-10A), NBIT(0-XLH93003ACS), Xin Jingcheng XJC(0-XJC-6F-D82), NSR(0-NSR-FTSensorA)
	 * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, default 0
	 * @param  [in] bus  Posizione del bus terminale su cui è collegato il dispositivo, attualmente non utilizzato, default 0
	 * @return  Codice errore
	 */
    errno_t FT_SetConfig(int company, int device, int softvesion, int bus);

Ottenere Configurazione Sensore di Forza/Coppia
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene la configurazione del sensore di forza/coppia
    * @param  [in] company  Produttore del sensore di forza/coppia, da definire
    * @param  [in] device  Numero dispositivo, attualmente non utilizzato, default 0
    * @param  [in] softvesion  Numero versione software, attualmente non utilizzato, default 0
    * @param  [in] bus  Posizione del bus terminale su cui è collegato il dispositivo, attualmente non utilizzato, default 0
    * @return  Codice errore
    */
    errno_t  FT_GetConfig(int *company, int *device, int *softvesion, int *bus);

Attivazione Sensore di Forza/Coppia
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Attiva il sensore di forza/coppia
    * @param  [in] act  0-reset, 1-attiva
    * @return  Codice errore
    */
    errno_t  FT_Activate(uint8_t act);

Taratura Zero Sensore di Forza/Coppia
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Taratura zero del sensore di forza/coppia
    * @param  [in] act  0-rimuovi offset zero, 1-correggi offset zero
    * @return  Codice errore
    */
    errno_t  FT_SetZero(uint8_t act);   

Impostare Sistema di Riferimento per Sensore di Forza/Coppia
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta il sistema di riferimento per il sensore di forza/coppia
    * @param  [in] ref  0-sistema di coordinate utensile, 1-sistema di coordinate base
    * @return  Codice errore
    */
    errno_t  FT_SetRCS(uint8_t ref); 

Impostare Peso del Carico per Sensore di Forza
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Imposta il peso del carico per il sensore di forza
     * @param [in] weight Peso del carico kg
     * @return Codice errore
     */
    errno_t SetForceSensorPayload(double weight);

Impostare Centro di Gravità del Carico per Sensore di Forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Imposta il centro di gravità del carico per il sensore di forza
     * @param [in] x Centro di gravità x mm
     * @param [in] y Centro di gravità y mm
     * @param [in] z Centro di gravità z mm
     * @return Codice errore
     */
    errno_t SetForceSensorPayloadCog(double x, double y, double z);

Ottenere Peso del Carico per Sensore di Forza
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:
    
    /**
     * @brief Ottiene il peso del carico per il sensore di forza
     * @param [in] weight Peso del carico kg
     * @return Codice errore
     */
    errno_t GetForceSensorPayload(double& weight);

Ottenere Centro di Gravità del Carico per Sensore di Forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene il centro di gravità del carico per il sensore di forza
     * @param [out] x Centro di gravità x mm
     * @param [out] y Centro di gravità y mm
     * @param [out] z Centro di gravità z mm
     * @return Codice errore
     */
    errno_t GetForceSensorPayloadCog(double& x, double& y, double& z);

Taratura Zero Automatica Sensore di Forza
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Taratura zero automatica del sensore di forza
     * @param [out] weight Massa del sensore kg
     * @param [out] pos Centro di gravità del sensore mm
     * @return Codice errore
     */
    errno_t ForceSensorAutoComputeLoad(double& weight, DescTran& pos);

Ottenere Dati Forza/Coppia nel Sistema di Riferimento
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene i dati forza/coppia nel sistema di riferimento
    * @param  [out] ft  Forza/coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice errore
    */   
    errno_t  FT_GetForceTorqueRCS(ForceTorque *ft); 

Ottenere Dati Forza/Coppia Originali dal Sensore
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene i dati forza/coppia originali dal sensore
    * @param  [out] ft  Forza/coppia, fx,fy,fz,tx,ty,tz
    * @return  Codice errore
    */   
    errno_t  FT_GetForceTorqueOrigin(ForceTorque *ft); 

Esempio di Codice Configurazione e Taratura Automatica Sensore di Forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTInit(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose ftCoord = {};
      robot.FT_SetRCS(0, ftCoord);
      robot.SetForceSensorPayload(0.824);
      robot.SetForceSensorPayloadCog(0.778, 2.554, 48.765);
      double weight = 0;
      double x = 0, y = 0, z = 0;
      robot.GetForceSensorPayload(weight);
      robot.GetForceSensorPayloadCog(x, y, z);
      printf("the FT load is %lf, %lf %lf %lf\n", weight, x, y, z);
      robot.SetForceSensorPayload(0);
      robot.SetForceSensorPayloadCog(0, 0, 0);
      double computeWeight = 0;
      DescTran tran = {};
      robot.ForceSensorAutoComputeLoad(weight, tran);
      cout << "the result is weight " << weight << " pos is " << tran.x << " " << tran.y << " " << tran.z << endl;
      robot.CloseRPC();
      return 0;
    }


Registrazione Identificazione Peso Carico
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Registra dati per identificazione peso carico
    * @param  [in] id  Numero sistema di coordinate sensore, intervallo [1~14]
    * @return  Codice errore
    */
    errno_t  FT_PdIdenRecord(int id);   

Calcolo Identificazione Peso Carico
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcola identificazione peso carico
    * @param  [out] weight  Peso del carico, unità kg
    * @return  Codice errore
    */   
    errno_t  FT_PdIdenCompute(float *weight);

Registrazione Identificazione Centro di Gravità Carico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Registra dati per identificazione centro di gravità carico
    * @param  [in] id  Numero sistema di coordinate sensore, intervallo [1~14]
    * @param  [in] index  Numero punto, intervallo [1~3]
    * @return  Codice errore
    */
    errno_t  FT_PdCogIdenRecord(int id, int index);    

Calcolo Identificazione Centro di Gravità Carico
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Calcola identificazione centro di gravità carico
    * @param  [out] cog  Centro di gravità carico, unità mm
    * @return  Codice errore
    */   
    errno_t  FT_PdCogIdenCompute(DescTran *cog); 

Esempio di Codice Identificazione Carico Sensore di Forza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTLoadCompute(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      robot.FT_GetForceTorqueOrigin(0, &ft);
      printf("ft origin:%f,%f,%f,%f,%f,%f\n", ft.fx, ft.fy, ft.fz, ft.tx, ft.ty, ft.tz);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      DescPose tcoord = {};
      tcoord.tran.z = 35.0;
      robot.SetToolCoord(10, &tcoord, 1, 0, 0, 0);
      robot.FT_PdIdenRecord(10);
      robot.Sleep(1000);
      float weight = 0.0;
      robot.FT_PdIdenCompute(&weight);
      printf("payload weight:%f\n", weight);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 2);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.Sleep(1000);
      robot.FT_PdCogIdenRecord(10, 3);
      robot.Sleep(1000);
      DescTran cog;
      memset(&cog, 0, sizeof(DescTran));
      robot.FT_PdCogIdenCompute(&cog);
      printf("cog:%f,%f,%f\n", cog.x, cog.y, cog.z);
      robot.CloseRPC();
      return 0;
    }

Guardia Collisioni
+++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Guardia collisioni
    * @param  [in] flag 0-disattiva guardia collisioni, 1-attiva guardia collisioni
    * @param  [in] sensor_id Numero sensore di forza
    * @param  [in] select  Selezione quali 6 gradi di libertà rilevare per collisioni, 0-non rilevare, 1-rilevare
    * @param  [in] ft  Forza/coppia collisione, fx,fy,fz,tx,ty,tz
    * @param  [in] max_threshold Soglia massima
    * @param  [in] min_threshold Soglia minima
    * @note   Intervallo di rilevamento forza/coppia: (ft-min_threshold, ft+max_threshold)
    * @return  Codice errore
    */   
    errno_t  FT_Guard(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque *ft, float max_threshold[6], float min_threshold[6]); 

Esempio di Codice Guardia Collisioni
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTGuard(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t sensor_id = 1;
      uint8_t select[6] = { 1,1,1,1,1,1 };
      float max_threshold[6] = { 10.0,10.0,10.0,10.0,10.0,10.0 };
      float min_threshold[6] = { 5.0,5.0,5.0,5.0,5.0,5.0 };
      ForceTorque ft;
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_p3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      robot.FT_Guard(1, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.MoveCart(&desc_p1, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p2, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.MoveCart(&desc_p3, 0, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_Guard(0, sensor_id, select, &ft, max_threshold, min_threshold);
      robot.CloseRPC();
      return 0;
    }

Controllo Forza Costante
+++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Controllo forza costante
    * @param [in] flag 0-disattiva controllo forza costante, 1-attiva controllo forza costante
    * @param [in] sensor_id Numero sensore di forza
    * @param [in] select Selezione quali 6 gradi di libertà rilevare per collisioni, 0-non rilevare, 1-rilevare
    * @param [in] ft Forza/coppia collisione, fx,fy,fz,tx,ty,tz
    * @param [in] ft_pid Parametri PID forza, parametri PID coppia
    * @param [in] adj_sign Controllo start/stop adattativo, 0-disattiva, 1-attiva
    * @param [in] ILC_sign Controllo start/stop ILC, 0-ferma, 1-addestra, 2-operazione
    * @param [in] max_dis Distanza massima di regolazione, unità mm
    * @param [in] max_ang Angolo massimo di regolazione, unità deg
    * @param [in] M Parametri massa 
    * @param [in] B Parametri smorzamento
    * @param [in] polishRadio Raggio levigatura, unità mm
    * @param [in] filter_Sign Segnale attivazione filtro 0-off; 1-on, default off
    * @param [in] posAdapt_sign Segnale attivazione conformità posa 0-off; 1-on, default off
    * @param [in] isNoBlock Segnale blocco, 0-blocca; 1-non blocca
    * @return Codice errore
    */
    errno_t FT_Control(uint8_t flag, int sensor_id, uint8_t select[6], ForceTorque* ft, float ft_pid[6], uint8_t adj_sign, uint8_t ILC_sign, float max_dis, float max_ang, double M[2], double B[2], double polishRadio = 0.0, int filter_Sign = 0, int posAdapt_sign = 0, int isNoBlock = 0); 

Esempio di Codice Controllo Forza Costante con Smorzamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTControlWithDamping(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(3);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      uint8_t sensor_id = 10;
      uint8_t select[6] = { 0,0,1,0,0,0 };
      float ft_pid[6] = { 0.0008, 0.0, 0.0, 0.0, 0.0, 0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 20;
      ForceTorque ft = {};
      ft.fz = -10.0;
      ExaxisPos epos(0, 0, 0, 0);
      JointPos j1(-118.985, -86.882, -118.139, -65.019, 90.002, 54.951);
      JointPos j2(-77.055, -77.218, -126.219, -66.591, 90.028, 96.881);
      DescPose desc_p1(-300.856, -332.618, 309.240, 179.976, -0.031, 96.065);
      DescPose desc_p2(-16.399, -383.760, 309.312, 179.975, -0.031, 96.064);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      double M[2] = {2.0, 2.0};
      double B[2] = {8.0, 8.0};
      double polishRadio;
      int filter_Sign;
      int posAdapt_sign;
      int isNoBlock;
      DescPose ftCoord = {};
      robot.FT_SetRCS(2, ftCoord);
      rtn = robot.FT_Control(1, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, 0, 0, 1, 0);
      printf("FT_Control start rtn is %d\n", rtn);
      rtn = robot.MoveL(&j1, &desc_p1, 0, 0, 100.0, 100.0, 20.0, -1.0, &epos, 0, 0, &offset_pos);
      rtn = robot.MoveL(&j2, &desc_p2, 0, 0, 100.0, 100.0, 20.0, -1.0, &epos, 0, 0, &offset_pos);
      rtn = robot.FT_Control(1, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, M, B, 0, 0, 1, 0);
      printf("FT_Control end rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Esplorazione Spirale
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Esplorazione spirale
    * @param  [in] rcs Sistema di riferimento, 0-sistema di coordinate utensile, 1-sistema di coordinate base
    * @param  [in] dr Incremento raggio per giro
    * @param  [in] ft Soglia forza/coppia, fx,fy,fz,tx,ty,tz, intervallo [0~100]
    * @param  [in] max_t_ms Tempo massimo esplorazione, unità ms
    * @param  [in] max_vel Velocità lineare massima, unità mm/s
    * @return  Codice errore
    */   
    errno_t  FT_SpiralSearch(int rcs, float dr, float ft, float max_t_ms, float max_vel);  

Inserimento Rotazionale
+++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inserimento rotazionale
    * @param  [in] rcs Sistema di riferimento, 0-sistema di coordinate utensile, 1-sistema di coordinate base
    * @param  [in] angVelRot Velocità angolare rotazione, unità deg/s
    * @param  [in] ft  Soglia forza/coppia, fx,fy,fz,tx,ty,tz, intervallo [0~100]
    * @param  [in] max_angle Angolo massimo rotazione, unità deg
    * @param  [in] orn Direzione forza/coppia, 1-direz. asse z, 2-rotaz. attorno asse z
    * @param  [in] max_angAcc Accelerazione angolare massima, unità deg/s^2, attualmente non utilizzata, default 0
    * @param  [in] rotorn  Direzione rotazione, 1-orario, 2-antiorario
    * @return  Codice errore
    */   
    errno_t  FT_RotInsertion(int rcs, float angVelRot, float ft, float max_angle, uint8_t orn, float max_angAcc, uint8_t rotorn);    

Inserimento Lineare
+++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inserimento lineare
    * @param  [in] rcs Sistema di riferimento, 0-sistema di coordinate utensile, 1-sistema di coordinate base
    * @param  [in] ft  Soglia forza/coppia, fx,fy,fz,tx,ty,tz, intervallo [0~100]
    * @param  [in] lin_v Velocità lineare, unità mm/s
    * @param  [in] lin_a Accelerazione lineare, unità mm/s^2, attualmente non utilizzata
    * @param  [in] max_dis Distanza massima inserimento, unità mm
    * @param  [in] linorn  Direzione inserimento, 0-direz. negativa, 1-direz. positiva
    * @return  Codice errore
    */   
    errno_t  FT_LinInsertion(int rcs, float ft, float lin_v, float lin_a, float max_dis, uint8_t linorn);    

Esempio di Codice Istruzioni Esplorazione Spirale, Inserimento Lineare, ecc.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestFTSearch(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t status = 1; 
      int sensor_num = 1; 
      float gain[6] = { 0.0001,0.0,0.0,0.0,0.0,0.0 }; 
      uint8_t adj_sign = 0; 
      uint8_t ILC_sign = 0; 
      float max_dis = 100.0; 
      float max_ang = 5.0; 
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      int rcs = 0; 
      float dr = 0.7; 
      float fFinish = 1.0; 
      float t = 60000.0;
      float vmax = 3.0;
      float force_goal = 20.0; 
      float lin_v = 0.0;
      float lin_a = 0.0;
      float disMax = 100.0;
      uint8_t linorn = 1; 
      float angVelRot = 2.0; 
      float forceInsertion = 1.0; 
      int angleMax = 45; 
      uint8_t orn = 1;
      float angAccmax = 0.0; 
      uint8_t rotorn = 1; 
      uint8_t select1[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_SpiralSearch(rcs, dr, fFinish, t, vmax);
      printf("FT_SpiralSearch rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select1, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select2[6] = { 1,1,1,0,0,0 }; 
      gain[0] = 0.00005;
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select2, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select3[6] = { 0,0,1,1,1,0 }; 
      ft.fz = -10.0;
      gain[0] = 0.0001;
      status = 1;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_RotInsertion(rcs, angVelRot, forceInsertion, angleMax, orn, angAccmax, rotorn);
      printf("FT_RotInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select3, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      uint8_t select4[6] = { 1,1,1,0,0,0 }; 
      ft.fz = -30.0;
      status = 1;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      rtn = robot.FT_LinInsertion(rcs, force_goal, lin_v, lin_a, disMax, linorn);
      printf("FT_LinInsertion rtn is %d\n", rtn);
      status = 0;
      robot.FT_Control(status, sensor_num, select4, &ft, gain, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Individuazione Superficie
++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Individuazione superficie
    * @param  [in] rcs Sistema di riferimento, 0-sistema di coordinate utensile, 1-sistema di coordinate base
    * @param  [in] dir  Direzione movimento, 1-direz. positiva, 2-direz. negativa 
    * @param  [in] axis Asse movimento, 1-asse x, 2-asse y, 3-asse z
    * @param  [in] lin_v Velocità lineare esplorazione, unità mm/s
    * @param  [in] lin_a Accelerazione lineare esplorazione, unità mm/s^2, attualmente non utilizzata, default 0
    * @param  [in] max_dis Distanza massima esplorazione, unità mm
    * @param  [in] ft  Soglia forza/coppia per terminazione azione, fx,fy,fz,tx,ty,tz  
    * @return  Codice errore
    */   
    errno_t  FT_FindSurface(int rcs, uint8_t dir, uint8_t axis, float lin_v, float lin_a, float max_dis, float ft);   

Inizio Calcolo Posizione Piano Centrale
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inizio calcolo posizione piano centrale
    * @return  Codice errore
    */   
    errno_t  FT_CalCenterStart();

Fine Calcolo Posizione Piano Centrale
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fine calcolo posizione piano centrale
    * @param  [out] pos Posa piano centrale
    * @return  Codice errore
    */      
    errno_t  FT_CalCenterEnd(DescPose *pos);

Esempio di Codice Individuazione Superficie
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSurface(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      int rcs = 0;
      uint8_t dir = 1;
      uint8_t axis = 1;
      float lin_v = 3.0;
      float lin_a = 0.0;
      float maxdis = 50.0;
      float ft_goal = 2.0;
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose xcenter(0, 0, 0, 0, 0, 0);
      DescPose ycenter(0, 0, 0, 0, 0, 0);
      ForceTorque ft;
      memset(&ft, 0, sizeof(ForceTorque));
      ft.fx = -2.0;
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.FT_CalCenterStart();
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&xcenter);
      printf("xcenter:%f,%f,%f,%f,%f,%f\n", xcenter.tran.x, xcenter.tran.y, xcenter.tran.z, xcenter.rpy.rx, xcenter.rpy.ry, xcenter.rpy.rz);
      robot.MoveCart(&xcenter, 9, 0, 60.0, 50.0, 50.0, -1.0, -1);
      robot.FT_CalCenterStart();
      dir = 1;
      axis = 2;
      lin_v = 6.0;
      maxdis = 150.0;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.MoveCart(&desc_pos, 9, 0, 100.0, 100.0, 100.0, -1.0, -1);
      robot.WaitMs(1000);
      dir = 2;
      robot.FT_FindSurface(rcs, dir, axis, lin_v, lin_a, maxdis, ft_goal);
      robot.FT_CalCenterEnd(&ycenter);
      printf("ycenter:%f,%f,%f,%f,%f,%f\n", ycenter.tran.x, ycenter.tran.y, ycenter.tran.z, ycenter.rpy.rx, ycenter.rpy.ry, ycenter.rpy.rz);
      robot.MoveCart(&ycenter, 9, 0, 60.0, 50.0, 50.0, 0.0, -1);
      robot.CloseRPC();
      return 0;
    }

Inizio Controllo di Conformità (Compliance)
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inizio controllo di conformità
    * @param  [in] p Coefficiente di regolazione posizione o coefficiente di conformità
    * @param  [in] force Soglia forza per attivazione conformità, unità N
    * @return  Codice errore
    */   
    errno_t  FT_ComplianceStart(float p, float force); 

Fine Controllo di Conformità (Compliance)
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fine controllo di conformità
    * @return  Codice errore
    */   
    errno_t  FT_ComplianceStop(); 

Esempio di Codice Controllo di Conformità
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestCompliance(void)
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
      int company = 24;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      int index = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      uint8_t flag = 1;
      int sensor_id = 1;
      uint8_t select[6] = { 1,1,1,0,0,0 };
      float ft_pid[6] = { 0.0005,0.0,0.0,0.0,0.0,0.0 };
      uint8_t adj_sign = 0;
      uint8_t ILC_sign = 0;
      float max_dis = 100.0;
      float max_ang = 0.0;
      ForceTorque ft;
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      memset(&ft, 0, sizeof(ForceTorque));
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      DescPose desc_p1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_p2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      ft.fx = -10.0;
      ft.fy = -10.0;
      ft.fz = -10.0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      float p = 0.00005;
      float force = 30.0;
      rtn = robot.FT_ComplianceStart(p, force);
      printf("FT_ComplianceStart rtn is %d\n", rtn);
      int count = 15;
      while (count)
      {
        robot.MoveL(&j1, &desc_p1, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 1, &offset_pos);
        robot.MoveL(&j2, &desc_p2, 0, 0, 100.0, 180.0, 100.0, -1.0, &epos, 0, 0, &offset_pos);
        count -= 1;
      }
      robot.FT_ComplianceStop();
      printf("FT_ComplianceStop rtn is %d\n", rtn);
      flag = 0;
      robot.FT_Control(flag, sensor_id, select, &ft, ft_pid, adj_sign, ILC_sign, max_dis, max_ang, 0, 0, 0);
      robot.CloseRPC();
      return 0;
    }

Inizializzazione Identificazione Carico Dinamico
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizializza filtro per identificazione carico dinamico
    * @return Codice errore
    */
    errno_t LoadIdentifyDynFilterInit();

Inizializzazione Variabili Identificazione Carico Dinamico
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizializza variabili per identificazione carico dinamico
    * @return Codice errore
    */
    errno_t LoadIdentifyDynVarInit();

Programma Principale Identificazione Carico
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Programma principale identificazione carico
    * @param [in] joint_torque Coppia articolare
    * @param [in] joint_pos Posizione articolare
    * @param [in] t Periodo di campionamento
    * @return Codice errore
    */
    errno_t LoadIdentifyMain(double joint_torque[6], double joint_pos[6], double t);

Ottenere Risultati Identificazione Carico
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene risultati identificazione carico
    * @param [in] gain 
    * @param [out] weight Peso del carico
    * @param [out] cog Centro di gravità del carico
    * @return Codice errore
    */
    errno_t LoadIdentifyGetResult(double gain[12], double *weight, DescTran *cog);

Esempio di Codice Identificazione Carico Robot
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestIdentify(void)
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
      retval = robot.LoadIdentifyDynFilterInit();
      printf("LoadIdentifyDynFilterInit retval is: %d \n", retval);
      retval = robot.LoadIdentifyDynVarInit();
      printf("LoadIdentifyDynVarInit retval is: %d \n", retval);
      JointPos posJ = {};
      DescPose posDec = {};
      float joint_toq[6] = { 0.0 };
      robot.GetActualJointPosDegree(0, &posJ);
      posJ.jPos[1] = posJ.jPos[1] + 10;
      robot.GetJointTorques(0, joint_toq);
      joint_toq[1] = joint_toq[1] + 2;
      double tmpTorque[6] = { 0.0 };
      for (int i = 0; i < 6; i++)
      {
        tmpTorque[i] = joint_toq[i];
      }
      retval = robot.LoadIdentifyMain(tmpTorque, posJ.jPos, 1);
      printf("LoadIdentifyMain retval is: %d \n", retval);
      double gain[12] = { 0,0.05,0,0,0,0,0,0.02,0,0,0,0 };
      double weight = 0;
      DescTran load_pos;
      memset(&load_pos, 0, sizeof(DescTran));
      retval = robot.LoadIdentifyGetResult(gain, &weight, &load_pos);
      printf("LoadIdentifyGetResult retval is: %d ; weight is %f cog is %f %f %f \n", retval, weight, load_pos.x, load_pos.y, load_pos.z);
      robot.CloseRPC();
      return 0;
    }

Trascinamento Assistito da Sensore di Forza
++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.2.0-3.8.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief  Controllo trascinamento assistito da sensore di forza
    * @param  [in] status Stato controllo, 0-disattiva; 1-attiva
    * @param  [in] asaptiveFlag Segnale attivazione adattativo, 0-disattiva; 1-attiva
    * @param  [in] interfereDragFlag Segnale trascinamento in zona di interferenza, 0-disattiva; 1-attiva
    * @param  [in] ingularityConstraintsFlag Strategia punto singolare, 0-evitamento; 1-attraversamento
    * @param  [in] forceCollisionFlag Segnale rilevamento collisione robot durante trascinamento assistito; 0-disattiva; 1-attiva
    * @param  [in] M Coefficiente inerzia
    * @param  [in] B Coefficiente smorzamento
    * @param  [in] K Coefficiente rigidezza
    * @param  [in] F Soglia forza a sei dimensioni per trascinamento
    * @param  [in] Fmax Limite massimo forza trascinamento
    * @param  [in] Vmax Limite massimo velocità articolare
    * @return  Codice errore
    */
    errno_t EndForceDragControl(int status, int asaptiveFlag, int interfereDragFlag, int ingularityConstraintsFlag, int forceCollisionFlag, std::vector<double> M, std::vector<double> B, std::vector<double> K, std::vector<double> F, double Fmax, double Vmax);

Ottenere Stato Interruttore Trascinamento Sensore di Forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene lo stato dell'interruttore di trascinamento del sensore di forza
     * @param [out] dragState Stato controllo trascinamento assistito da sensore di forza, 0-disattiva; 1-attiva
     * @param [out] sixDimensionalDragState Stato controllo trascinamento assistito a sei dimensioni, 0-disattiva; 1-attiva
     * @return Codice errore
     */
    errno_t GetForceAndTorqueDragState(int& dragState, int& sixDimensionalDragState);

Attivazione Automatica Sensore di Forza dopo Cancellazione Errore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Attivazione automatica sensore di forza dopo cancellazione errore
     * @param [in] status Stato controllo, 0-disattiva; 1-attiva
     * @return Codice errore
     */
    errno_t SetForceSensorDragAutoFlag(int status);

Esempio di Codice Trascinamento Assistito da Sensore di Forza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestEndForceDragCtrl(void)
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
         robot.SetForceSensorDragAutoFlag(1);
         vector <double> M = { 15.0, 15.0, 15.0, 0.5, 0.5, 0.1 };
         vector <double> B = { 150.0, 150.0, 150.0, 5.0, 5.0, 1.0 };
         vector <double> K = { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
         vector <double> F = { 10.0, 10.0, 10.0, 1.0, 1.0, 1.0 };
         robot.EndForceDragControl(1, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.Sleep(5000);
         int dragState = 0;
         int sixDimensionalDragState = 0;
         robot.GetForceAndTorqueDragState(dragState, sixDimensionalDragState);
         printf("the drag state is %d %d \n", dragState, sixDimensionalDragState);
         robot.EndForceDragControl(0, 0, 0, 0, 1, M, B, K, F, 50, 100);
         robot.CloseRPC();
         return 0;
     }

Impostare Interruttore e Parametri Trascinamento Ibrido Impedenza Sei Dimensioni e Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
     * @brief Imposta interruttore e parametri per trascinamento ibrido impedenza sei dimensioni e articolare
     * @param [in] status Stato controllo, 0-disattiva; 1-attiva
     * @param [in] impedanceFlag Segnale attivazione impedenza, 0-disattiva; 1-attiva
     * @param [in] lamdeDain Guadagno trascinamento
     * @param [in] KGain Guadagno rigidezza
     * @param [in] BGain Guadagno smorzamento
     * @param [in] dragMaxTcpVel Limite massimo velocità lineare terminale durante trascinamento
     * @param [in] dragMaxTcpOriVel Limite massimo velocità angolare terminale durante trascinamento
     * @return Codice errore
     */
    errno_t ForceAndJointImpedanceStartStop(int status, int impedanceFlag, std::vector<double> lamdeDain, std::vector<double> KGain, std::vector<double> BGain, double dragMaxTcpVel, double dragMaxTcpOriVel);

Esempio di Codice Trascinamento Ibrido Impedenza Sei Dimensioni e Articolare
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestForceAndJointImpedance(void)
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
      robot.DragTeachSwitch(1);
      vector <double> lamdeDain = { 3.0, 2.0, 2.0, 2.0, 2.0, 3.0 };
      vector <double> KGain = { 0, 0, 0, 0, 0, 0 };
      vector <double> BGain = { 150, 150, 150, 5.0, 5.0, 1.0 };
      rtn = robot.ForceAndJointImpedanceStartStop(1, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.Sleep(5000);
      robot.DragTeachSwitch(0);
      rtn = robot.ForceAndJointImpedanceStartStop(0, 0, lamdeDain, KGain, BGain, 1000, 180);
      printf("ForceAndJointImpedanceStartStop rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Controllo Start/Stop Impedenza
+++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controllo start/stop impedenza
    * @param [in] status 0：disattiva; 1-attiva
    * @param [in] workSpace 0-spazio articolare; 1-spazio cartesiano
    * @param [in] forceThreshold Soglia forza di attivazione (N)
    * @param [in] m Parametro massa
    * @param [in] b Parametro smorzamento
    * @param [in] k Parametro rigidezza
    * @param [in] maxV Velocità lineare massima (mm/s)
    * @param [in] maxVA Accelerazione lineare massima (mm/s2)
    * @param [in] maxW Velocità angolare massima (°/s)
    * @param [in] maxWA Accelerazione angolare massima (°/s2)
    * @return Codice errore
    */
    errno_t ImpedanceControlStartStop(int status, int workSpace, double forceThreshold[6], double m[6], double b[6], double k[6], double maxV, double maxVA, double maxW, double maxWA);

Esempio di Codice Controllo Start/Stop Impedenza Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v3.8.6
    
.. code-block:: c++
    :linenos:

    int TestImpedanceControl()
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
        return 0;
      }
      robot.SetReConnectParam(true, 30000, 500);
      JointPos j1(102.622, -135.990, 120.769, -73.950, -90.848, 35.507);
      JointPos j2(93.674, -80.062, 82.947, -92.199, -90.967, 26.559);
      DescPose desc_pos1(136.552, -149.799, 449.532, 179.817, -1.172, 157.123);
      DescPose desc_pos2(136.540, -561.048, 449.542, 179.819, -1.172, 157.122);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 200.0;
      float ovl = 100.0;
      float blendT = -1.0;
      float blendR = -1.0;
      uint8_t flag = 0;
      uint8_t search = 0;
      robot.SetSpeed(20);
      int company = 17;
      int device = 0;
      int softversion = 0;
      int bus = 1;
      robot.FT_SetConfig(company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_GetConfig(&company, &device, &softversion, &bus);
      printf("FT config:%d,%d,%d,%d\n", company, device, softversion, bus);
      robot.Sleep(1000);
      robot.FT_Activate(0);
      robot.Sleep(1000);
      robot.FT_Activate(1);
      robot.Sleep(1000);
      robot.Sleep(1000);
      robot.FT_SetZero(0);
      robot.Sleep(1000);
      robot.FT_SetZero(1);
      robot.Sleep(1000);
      double forceThreshold[6] = { 30,30,30,5,5,5 };
      double m[6] = { 0.1,0.1,0.1,0.02,0.02,0.02 };
      double b[6] = { 1,1,1,0.08,0.08,0.08 };
      double k[6] = { 0,0,0,0,0,0 };
      rtn = robot.ImpedanceControlStartStop(1, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);
      printf("ImpedanceControlStartStop errcode:%d\n", rtn);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos1, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, 0, &epos, search, flag, &offset_pos, -1, 1);
      printf("movel errcode:%d\n", rtn);
      robot.ImpedanceControlStartStop(0, 1, forceThreshold, m, b, k, 1000, 500, 100, 100);    
      robot.CloseRPC();
      return 0;
    }