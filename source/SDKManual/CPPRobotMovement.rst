Movimento del Robot
===================

.. toctree:: 
    :maxdepth: 5


Jog (Movimento a Scatti)
+++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento Jog (a scatti)
    * @param  [in]  ref 0-jog articolare, 2-jog nel sistema di coordinate base, 4-jog nel sistema di coordinate utensile, 8-jog nel sistema di coordinate pezzo
    * @param  [in]  nb 1-articolazione1 (o asse x), 2-articolazione2 (o asse y), 3-articolazione3 (o asse z), 4-articolazione4 (o rotazione attorno all'asse x), 5-articolazione5 (o rotazione attorno all'asse y), 6-articolazione6 (o rotazione attorno all'asse z)
    * @param  [in]  dir 0-direz. negativa, 1-direz. positiva
    * @param  [in]  vel Percentuale velocità, [0~100]
    * @param  [in]  acc Percentuale accelerazione, [0~100]
    * @param  [in]  max_dis Angolo massimo per singolo movimento jog, unità [°] o distanza, unità [mm]
    * @return  Codice errore
    */
    errno_t  StartJOG(uint8_t ref, uint8_t nb, uint8_t dir, float vel, float acc, float max_dis);

Fermata Decelerata Movimento Jog
+++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fermata decelerata movimento Jog
    * @param  [in]  ref  1-fermata jog articolare, 3-fermata jog nel sistema di coordinate base, 5-fermata jog nel sistema di coordinate utensile, 9-fermata jog nel sistema di coordinate pezzo
    * @return  Codice errore
    */
    errno_t  StopJOG(uint8_t ref);

Fermata Immediata Movimento Jog
++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fermata immediata movimento Jog
    * @return  Codice errore
    */
    errno_t  ImmStopJOG(); 

Esempio di Codice Controllo Jog Robot
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestJOG(void)
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
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(0, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(2, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.ImmStopJOG();
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(4, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(5);
             robot.Sleep(1000);
         }
         for (int i = 0; i < 6; i++)
         {
             robot.StartJOG(8, i + 1, 0, 20.0, 20.0, 30.0);
             robot.Sleep(1000);
             robot.StopJOG(9);
             robot.Sleep(1000);
         }
         robot.CloseRPC();
         return 0;
     }

Movimento nello Spazio Articolare (PTP)
++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento nello spazio articolare (PTP - Point to Point)
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] epos  Posizione assi estesi, unità mm
    * @param  [in] blendT [-1.0]-movimento fino a posizione (bloccante), [0~500.0]-tempo di transizione (non bloccante), unità ms
    * @param  [in] offset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param  [in] offset_pos  Quantità di offset posa
    * @return  Codice errore
    */
    errno_t  MoveJ(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos *epos, float blendT, uint8_t offset_flag, DescPose *offset_pos);

Movimento nello Spazio Articolare (Calcolo Cinematica Diretta Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento nello spazio articolare (calcolo cinematica diretta automatico)
    * @param [in] joint_pos Posizione articolare target, unità deg
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] epos Posizione assi estesi, unità mm
    * @param [in] blendT [-1.0]-movimento fino a posizione (bloccante), [0~500.0]-tempo di transizione (non bloccante), unità ms
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità di offset posa
    * @return Codice errore
    */
    errno_t MoveJ(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos* epos, float blendT, uint8_t offset_flag, DescPose* offset_pos);
   
Movimento Lineare nello Spazio Cartesiano (LIN)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief   Movimento Lineare nello Spazio Cartesiano
    * @param [in] joint_pos Posizioni target dei giunti, unità: deg
    * @param [in] desc_pos Posa target cartesiana
    * @param [in] tool Indice del sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Indice del sistema di coordinate pezzo/utente, intervallo [0~14]
    * @param [in] vel Percentuale di velocità, intervallo [0~100]
    * @param [in] acc Percentuale di accelerazione, intervallo [0~100] (attualmente non disponibile)
    * @param [in] ovl Fattore di scala velocità [0~100] / Velocità fisica (mm/s)
    * @param [in] blendR [-1.0]-Blocca fino al completamento del movimento (bloccante), [0~1000.0]-Raggio di transizione (non bloccante), unità: mm
    * @param [in] blendMode Metodo di transizione; 0-Transizione tangente; 1-Transizione a spigolo
    * @param [in] epos Posizione dell'asse esteso, unità: mm
    * @param [in] search 0-Nessuna ricerca filo, 1-Ricerca filo
    * @param [in] offset_flag 0-Nessuno scostamento, 1-Scostamento nel sistema di coordinate base/pezzo, 2-Scostamento nel sistema di coordinate utensile
    * @param [in] offset_pos Valore di scostamento della posa
    * @param [in] oacc Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²)
    * @param [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²)
    * @param [in] overSpeedStrategy Strategia di gestione sovravelocità; 1-Standard; 2-Ferma con errore in caso di sovravelocità; 3-Riduzione adattiva della velocità, default 0
    * @param [in] speedPercent Percentuale di soglia di riduzione velocità consentita [0-100], default 10%
    * @return Codice di errore
    */
    errno_t MoveL(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos *epos, uint8_t search, uint8_t offset_flag, DescPose *offset_pos, float oacc = 100.0, int velAccParamMode = 0, int overSpeedStrategy = 0, int speedPercent = 10);

Movimento Lineare nello Spazio Cartesiano (Calcolo Cinematica Inversa Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento lineare nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio di transizione (non bloccante), unità mm
    * @param [in] blendMode Modalità transizione; 0-transizione tangente interna; 1-transizione a punto d'angolo
    * @param [in] epos Posizione assi estesi, unità mm
    * @param [in] search 0-nessuna ricerca filo di saldatura, 1-ricerca filo di saldatura
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità di offset posa
    * @param [in] config Configurazione spazio articolare per cinematica inversa, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @param [in] overSpeedStrategy Strategia gestione sovravelocità, 1-standard; 2-fermata con errore in caso di sovravelocità; 3-decelerazione adattativa, default 0
    * @param [in] speedPercent Soglia percentuale decelerazione consentita [0-100], default 10%
    * @return Codice errore
    */
    errno_t MoveL(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos* epos, uint8_t search, uint8_t offset_flag, DescPose* offset_pos, int config = -1, int overSpeedStrategy = 0, int speedPercent = 10);

Movimento Circolare nello Spazio Cartesiano (ARC)
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (ARC)
    * @param  [in] joint_pos_p  Posizione articolare punto intermedio, unità deg
    * @param  [in] desc_pos_p   Posa cartesiana punto intermedio
    * @param  [in] ptool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] puser  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] epos_p  Posizione assi estesi, unità mm
    * @param  [in] poffset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param  [in] offset_pos_p  Quantità di offset posa
    * @param  [in] joint_pos_t  Posizione articolare punto target, unità deg
    * @param  [in] desc_pos_t   Posa cartesiana punto target
    * @param  [in] ttool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] tuser  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] epos_t  Posizione assi estesi, unità mm
    * @param  [in] toffset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param  [in] offset_pos_t  Quantità di offset posa
    * @param [in] ovl Fattore di scala velocità [0~100] / Velocità fisica (mm/s)
    * @param [in] blendR [-1.0]-Blocca fino al completamento del movimento (bloccante), [0~1000.0]-Raggio di transizione (non bloccante), unità: mm
    * @param [in] oacc Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²)
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-percentuale; 1-velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice errore
    */
    errno_t MoveC(JointPos *joint_pos_p, DescPose *desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos *epos_p, uint8_t poffset_flag, DescPose *offset_pos_p, JointPos *joint_pos_t, DescPose *desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos *epos_t, uint8_t toffset_flag, DescPose *offset_pos_t, float ovl, float blendR, float oacc = 100.0, int velAccParamMode = 0);

Movimento Circolare nello Spazio Cartesiano (Calcolo Cinematica Inversa Automatico)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento circolare nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos_p  Posa cartesiana punto intermedio
    * @param [in] ptool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] puser Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] pvel Percentuale velocità, intervallo [0~100]
    * @param [in] pacc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] epos_p Posizione assi estesi, unità mm
    * @param [in] poffset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_p Quantità di offset posa
    * @param [in] desc_pos_t  Posa cartesiana punto target
    * @param [in] ttool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] tuser Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] tvel Percentuale velocità, intervallo [0~100]
    * @param [in] tacc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] epos_t Posizione assi estesi, unità mm
    * @param [in] toffset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos_t Quantità di offset posa
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio di transizione (non bloccante), unità mm
    * @param [in] config Configurazione spazio articolare per cinematica inversa, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @return Codice errore
    */
    errno_t MoveC(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, uint8_t poffset_flag, DescPose* offset_pos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, uint8_t toffset_flag, DescPose* offset_pos_t, float ovl, float blendR, int config = -1);

Movimento Circolare Completo nello Spazio Cartesiano (CIRCLE)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento circolare completo nello spazio cartesiano (CIRCLE)
    * @param  [in] joint_pos_p  Posizione articolare punto intermedio 1, unità deg
    * @param  [in] desc_pos_p   Posa cartesiana punto intermedio 1
    * @param  [in] ptool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] puser  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] epos_p  Posizione assi estesi, unità mm
    * @param  [in] joint_pos_t  Posizione articolare punto intermedio 2, unità deg
    * @param  [in] desc_pos_t   Posa cartesiana punto intermedio 2
    * @param  [in] ttool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] tuser  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] epos_t  Posizione assi estesi, unità mm
    * @param  [in] ovl Fattore di scala velocità [0~100] / Velocità fisica (mm/s)
    * @param  [in] offset_flag 0-Nessuno scostamento, 1-Scostamento nel sistema di coordinate base/pezzo, 2-Scostamento nel sistema di coordinate utensile
    * @param  [in] offset_pos Valore di scostamento della posa
    * @param  [in] oacc Fattore di scala accelerazione [0-100] / Accelerazione fisica (mm/s²)
    * @param  [in] blendR -1：bloccante; 0~1000：raggio di transizione
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-percentuale; 1-velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice errore
    */
    errno_t Circle(JointPos* joint_pos_p, DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, JointPos* joint_pos_t, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int velAccParamMode = 0);

Movimento Circolare Completo nello Spazio Cartesiano (Calcolo Cinematica Inversa Automatico)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento circolare completo nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos_p  Posa cartesiana punto intermedio 1
    * @param [in] ptool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] puser Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] pvel Percentuale velocità, intervallo [0~100]
    * @param [in] pacc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] epos_p Posizione assi estesi, unità mm
    * @param [in] desc_pos_t  Posa cartesiana punto intermedio 2
    * @param [in] ttool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] tuser Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] tvel Percentuale velocità, intervallo [0~100]
    * @param [in] tacc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] epos_t Posizione assi estesi, unità mm
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità di offset posa
    * @param [in] oacc Percentuale accelerazione
    * @param [in] blendR -1：bloccante; 0~1000：raggio di transizione
    * @param [in] config Configurazione spazio articolare per cinematica inversa, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @return Codice errore
    */
    errno_t Circle(DescPose* desc_pos_p, int ptool, int puser, float pvel, float pacc, ExaxisPos* epos_p, DescPose* desc_pos_t, int ttool, int tuser, float tvel, float tacc, ExaxisPos* epos_t, float ovl, uint8_t offset_flag, DescPose* offset_pos, double oacc = 100.0, double blendR = -1, int config = -1);
    
Movimento Punto a Punto nello Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento punto a punto nello spazio cartesiano
    * @param  [in]  desc_pos  Posa cartesiana target o incremento di posa
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendT [-1.0]-movimento fino a posizione (bloccante), [0~500.0]-tempo di transizione (non bloccante), unità ms 
    * @param  [in] config  Configurazione spazio articolare, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-calcolo riferito a specifica configurazione spazio articolare, default -1   
    * @return  Codice errore
    */
    errno_t  MoveCart(DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Esempio di Codice Istruzioni di Movimento Base del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestMove(void)
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

        JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0;
        float acc = 100.0;
        float ovl = 100.0;
        float oacc = 100.0;
        float blendT = 0.0;
        float blendR = 0.0;
        uint8_t flag = 0;
        uint8_t search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&j2, &desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, oacc, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&j3, &desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &j4, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, oacc, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&j3, &desc_pos3, tool, user, vel, acc, &epos, &j1, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        rtn = robot.MoveCart(&desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        printf("MoveCart errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.MoveL(&desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, &epos, search, flag, &offset_pos, -1, velAccMode);
        printf("movel errcode:%d\n", rtn);
        rtn = robot.MoveC(&desc_pos3, tool, user, vel, acc, &epos, flag, &offset_pos, &desc_pos4, tool, user, vel, acc, &epos, flag, &offset_pos, ovl, blendR, -1, velAccMode);
        printf("movec errcode:%d\n", rtn);
        rtn = robot.MoveJ(&j2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
        printf("movej errcode:%d\n", rtn);
        rtn = robot.Circle(&desc_pos3, tool, user, vel, acc, &epos, &desc_pos1, tool, user, vel, acc, &epos, ovl, flag, &offset_pos, oacc, blendR, -1, velAccMode);
        printf("circle errcode:%d\n", rtn);
        robot.CloseRPC();
        return 0;
    }

Movimento Spirale nello Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento spirale nello spazio cartesiano
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] epos  Posizione assi estesi, unità mm
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]    
    * @param  [in] offset_flag  0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param  [in] offset_pos  Quantità di offset posa
    * @param  [in] spiral_param  Parametri spirale
    * @return  Codice errore
    */
    errno_t  NewSpiral(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, ExaxisPos *epos, float ovl, uint8_t offset_flag, DescPose *offset_pos, SpiralParam spiral_param);  

Movimento Spirale nello Spazio Cartesiano (Calcolo Cinematica Inversa Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento spirale nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] epos Posizione assi estesi, unità mm
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] offset_flag 0-nessun offset, 1-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param [in] offset_pos Quantità di offset posa
    * @param [in] spiral_param Parametri spirale
    * @param [in] config Configurazione spazio articolare per cinematica inversa, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @return Codice errore
    */
    errno_t NewSpiral(DescPose* desc_pos, int tool, int user, float vel, float acc, ExaxisPos* epos, float ovl, uint8_t offset_flag, DescPose* offset_pos, SpiralParam spiral_param, int config = -1);

Esempio di Codice Movimento Spirale
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpiral(void)
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
      JointPos j(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      DescPose desc_pos(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose offset_pos1(50, 0, 0, -30, 0, 0);
      DescPose offset_pos2(50, 0, 0, -5, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      SpiralParam sp;
      sp.circle_num = 5;
      sp.circle_angle = 5.0;
      sp.rad_init = 50.0;
      sp.rad_add = 10.0;
      sp.rotaxis_add = 10.0;
      sp.rot_direction = 0;
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = 0.0;
      uint8_t flag = 2;
      robot.SetSpeed(20);
      rtn = robot.MoveJ(&j, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos1);
      printf("movej errcode:%d\n", rtn);
      rtn = robot.NewSpiral(&desc_pos, tool, user, vel, acc, &epos, ovl, flag, &offset_pos2, sp);
      printf("newspiral errcode:%d\n", rtn);
      robot.CloseRPC();
      return 0;
    }

Inizio Movimento Servo
+++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio movimento servo, da usare insieme alle istruzioni ServoJ, ServoCart
    * @return Codice errore
    */
    errno_t ServoMoveStart();

Fine Movimento Servo
+++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fine movimento servo, da usare insieme alle istruzioni ServoJ, ServoCart
    * @return Codice errore
    */
    errno_t ServoMoveEnd();

Movimento in Modalità Servo nello Spazio Articolare (ServoJ)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento in modalità servo nello spazio articolare (ServoJ)
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] axisPos  Posizione assi esterni, unità mm
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto, default 0
    * @param  [in] vel  Percentuale velocità, intervallo [0~100], non attualmente aperto, default 0
    * @param  [in] cmdT  Periodo di invio comandi, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in] filterT Tempo di filtraggio, unità s, non attualmente aperto, default 0
    * @param  [in] gain  Amplificatore proporzionale per posizione target, non attualmente aperto, default 0
    * @param  [in] id ID istruzione servoJ, default 0
    * @return  Codice errore
    */
    errno_t ServoJ(JointPos *joint_pos, ExaxisPos* axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0);

Esempio di Programma Movimento in Modalità Servo Articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoJ(void)
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
        JointPos j(0, 0, 0, 0, 0, 0);
        ExaxisPos epos(0, 0, 0, 0);
        float vel = 0.0;
        float acc = 0.0;
        float cmdT = 0.008;
        float filterT = 0.0;
        float gain = 0.0;
        uint8_t flag = 0;
        int count = 500;
        float dt = 0.1;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, &j);
        if (ret == 0)
        {
            robot.ServoMoveStart();
            while (count)
            {
                robot.ServoJ(&j, &epos, acc, vel, cmdT, filterT, gain, cmdID);
                j.jPos[0] += dt;
                count -= 1;
                robot.WaitMs(cmdT * 1000);
            }
            robot.ServoMoveEnd();
        }
        else
        {
            printf("GetActualJointPosDegree errcode:%d\n", ret);
        }
        robot.CloseRPC();
        return 0;
    }

Inizio Controllo Coppia Articolare
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio controllo coppia articolare
    * @return Codice errore
    */
    errno_t ServoJTStart();

Controllo Coppia Articolare
++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Controllo coppia articolare
    * @param  [in] torque Coppia articolare j1~j6, unità Nm
    * @param  [in] interval Periodo comando, unità s, intervallo [0.001~0.008]
    * @param  [in] checkFlag Strategia di controllo 0-nessuna limitazione; 1-limita potenza; 2-limita velocità; 3-limita sia potenza che velocità
    * @param  [in] jPowerLimit Limite massimo potenza articolare (W)
    * @param  [in] jVelLimit Velocità massima articolare (°/s)
    * @return  Codice errore
    */
    errno_t ServoJT(float torque[], double interval, int checkFlag, double jPowerLimit[6], double jVelLimit[6]);

Fine Controllo Coppia Articolare
+++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Fine controllo coppia articolare
    * @return Codice errore
    */
    errno_t ServoJTEnd();

Esempio di Codice Controllo Coppia Articolare
+++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestServoJT(void)
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
         float torques[] = { 0, 0, 0, 0, 0, 0 };
         robot.GetJointTorques(1, torques);
         int count = 100;
         robot.ServoJTStart(); 
         int error = 0;
         while (count > 0)
         {
             error = robot.ServoJT(torques, 0.001);
             count = count - 1;
             robot.Sleep(1);
         }
         error = robot.ServoJTEnd();
         robot.DragTeachSwitch(0);
         robot.CloseRPC();
         return 0;
     }

Esempio di Codice Controllo Coppia Articolare con Protezione Sovravelocità
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int ServoJTWithSafety(FRRobot* robot)
    {
        robot->ResetAllError();
        robot->Sleep(500);
        float torques[] = { 0, 0, 0, 0, 0, 0 };
        robot->GetJointTorques(1, torques);
        robot->ServoJTStart(); 
        ROBOT_STATE_PKG pkg = {};
        robot->DragTeachSwitch(1);
        int checkFlag = 3;
        //double jPowerLimit[6] = {1, 1, 1, 1, 1, 1}; 
        double jPowerLimit[6] = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double jVelLimit[6] = { 181, 80, 80, 80, 80, 80 };
        int count = 800000;
        int error = 0;
        while (count > 0)
        {
            torques[2] = torques[2] + 0.01;
            error = robot->ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit); 
            if (error != 0)
            {
                robot->ServoJTEnd();
            }
            printf("ServoJT rtn is %d\n", error);
            count = count - 1;
            robot->Sleep(1);
            robot->GetRobotRealTimeState(&pkg);
            printf("maincode %d, subcode %d\n", pkg.main_code, pkg.sub_code);
        }
        robot->DragTeachSwitch(0);
        error = robot->ServoJTEnd();  
        return 0;
    }

Movimento in Modalità Servo nello Spazio Cartesiano (ServoCart)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Movimento in modalità servo nello spazio cartesiano (ServoCart)
    * @param  [in]  mode  0-movimento assoluto (sistema di coordinate base), 1-movimento incrementale (sistema di coordinate base), 2-movimento incrementale (sistema di coordinate utensile)
    * @param  [in]  desc_pos  Posa cartesiana target o incremento di posa
    * @param  [in]  pos_gain  Coefficiente di proporzione incremento di posa, attivo solo in movimento incrementale, intervallo [0~1]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto, default 0
    * @param  [in] vel  Percentuale velocità, intervallo [0~100], non attualmente aperto, default 0
    * @param  [in] cmdT  Periodo di invio comandi, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in] filterT Tempo di filtraggio, unità s, non attualmente aperto, default 0
    * @param  [in] gain  Amplificatore proporzionale per posizione target, non attualmente aperto, default 0
    * @return  Codice errore
    */
    errno_t  ServoCart(int mode, DescPose *desc_pose, float pos_gain[6], float acc, float vel, float cmdT, float filterT, float gain);

Esempio di Codice Movimento in Modalità Servo Cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestServoCart(void)
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
         DescPose desc_pos_dt;
         memset(&desc_pos_dt, 0, sizeof(DescPose));
         desc_pos_dt.tran.z = -0.5;
         float pos_gain[6] = { 0.0,0.0,1.0,0.0,0.0,0.0 };
         int mode = 2;
         float vel = 0.0;
         float acc = 0.0;
         float cmdT = 0.008;
         float filterT = 0.0;
         float gain = 0.0;
         uint8_t flag = 0;
         int count = 100;
         robot.SetSpeed(20);
         while (count)
         {
             robot.ServoCart(mode, &desc_pos_dt, pos_gain, acc, vel, cmdT, filterT, gain);
             count -= 1;
             robot.WaitMs(cmdT * 1000);
         }
         robot.CloseRPC();
         return 0;
     }

Inizio Movimento Spline
+++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Inizio movimento spline
    * @return  Codice errore
    */
    errno_t  SplineStart();

Movimento Spline PTP nello Spazio Articolare (Calcolo Cinematica Diretta Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento spline PTP nello spazio articolare (calcolo cinematica diretta automatico)
    * @param [in] joint_pos Posizione articolare target, unità deg
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @return Codice errore
    */
    errno_t SplinePTP(JointPos* joint_pos, int tool, int user, float vel, float acc, float ovl);

Punto Movimento Spline PTP
+++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Punto movimento spline PTP
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]   
    * @return  Codice errore
    */
    errno_t  SplinePTP(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl);

Fine Movimento Spline
++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Fine movimento spline
    * @return  Codice errore
    */
    errno_t  SplineEnd();

Esempio di Codice Movimento Spline
+++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestSpline(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, &desc_pos1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, &desc_pos2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, &desc_pos3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, &desc_pos4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.SplineStart();
      robot.SplinePTP(&j1, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j2, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j3, tool, user, vel, acc, ovl);
      robot.SplinePTP(&j4, tool, user, vel, acc, ovl);
      robot.SplineEnd();
      robot.CloseRPC();
      return 0;
    }

Inizio Nuovo Movimento Spline
++++++++++++++++++++++++++++++
.. versionchanged:: C++SDK-v2.1.3.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio nuovo movimento spline
    * @param [in] type  0-transizione ad arco, 1-punti forniti come punti di percorso
    * @param [in] averageTime Tempo medio di transizione globale (ms)(10 ~ ), default 2000
    * @return Codice errore
    */
    errno_t NewSplineStart(int type, int averageTime=2000);

Punto Istruzione Nuova Spline
++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punto istruzione nuova spline
    * @param [in] joint_pos Posizione articolare target, unità deg
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio di transizione (non bloccante), unità mm 
    * @param  [in] lastFlag Se è l'ultimo punto, 0-no, 1-sì
    * @return Codice errore
    */ 
    errno_t NewSplinePoint(JointPos *joint_pos, DescPose *desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Punto Istruzione Nuova Spline (Calcolo Cinematica Inversa Automatico)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Punto istruzione nuova spline (calcolo cinematica inversa automatico)
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non attualmente aperto
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio di transizione (non bloccante), unità mm
    * @param [in] lastFlag Se è l'ultimo punto, 0-no, 1-sì
    * @param [in] config Configurazione spazio articolare per cinematica inversa, [-1]-calcolo riferito alla posizione articolare corrente, [0~7]-soluzione basata su specifica configurazione spazio articolare
    * @return Codice errore
    */
    errno_t NewSplinePoint(DescPose* desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag, int config = -1);

Fine Nuovo Movimento Spline
++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Fine nuovo movimento spline
    * @return Codice errore
    */
    errno_t NewSplineEnd();

Esempio di Codice Nuovo Movimento Spline
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestNewSpline(void)
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
      JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
      JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
      JointPos j3(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
      JointPos j4(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
      JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
      DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
      DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
      DescPose desc_pos3(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
      DescPose desc_pos4(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
      DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
      DescPose offset_pos(0, 0, 0, 0, 0, 0);
      ExaxisPos epos(0, 0, 0, 0);
      int tool = 0;
      int user = 0;
      float vel = 100.0;
      float acc = 100.0;
      float ovl = 100.0;
      float blendT = -1.0;
      uint8_t flag = 0;
      robot.SetSpeed(20);
      int err1 = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&j1, &desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j2, &desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j3, &desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j4, &desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&j5, &desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      err1 = robot.MoveJ(&j1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
      printf("movej errcode:%d\n", err1);
      robot.NewSplineStart(1, 2000);
      robot.NewSplinePoint(&desc_pos1, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos2, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos3, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos4, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplinePoint(&desc_pos5, tool, user, vel, acc, ovl, -1, 0);
      robot.NewSplineEnd();
      robot.CloseRPC();
      return 0;
    }

Interruzione Movimento
++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Interruzione movimento
    * @return  Codice errore
    */
    errno_t  StopMotion();

Pausa Movimento
++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Pausa movimento
    * @return Codice errore
    */
    errno_t PauseMotion(); 

Ripresa Movimento
+++++++++++++++++
.. code-block:: c++
    :linenos:
    
    /**
    * @brief Ripresa movimento
    * @return Codice errore
    */
    errno_t ResumeMotion();

Esempio di Codice Pausa, Ripresa, Interruzione Movimento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestPause(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j5(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos5(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         rtn = robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         rtn = robot.MoveJ(&j5, &desc_pos5, tool, user, vel, acc, ovl, &epos, 1, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PauseMotion();
         robot.Sleep(1000);
         robot.ResumeMotion();
         robot.Sleep(1000);
         robot.StopMotion();
         robot.Sleep(1000);
         robot.CloseRPC();
         return 0;
     }

Abilitazione Offset Globale Punti
++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Abilitazione offset globale punti
    * @param  [in]  flag  0-offset nel sistema di coordinate base/pezzo, 2-offset nel sistema di coordinate utensile
    * @param  [in] offset_pos  Quantità di offset posa
    * @return  Codice errore
    */
    errno_t  PointsOffsetEnable(int flag, DescPose *offset_pos);

Disabilitazione Offset Globale Punti
+++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Disabilitazione offset globale punti
    * @return  Codice errore
    */
    errno_t  PointsOffsetDisable();

Esempio di Codice Offset Punti
+++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestOffset(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 100.0;
         float acc = 100.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.Sleep(1000);
         robot.PointsOffsetEnable(0, &offset_pos1);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.PointsOffsetDisable();
         robot.CloseRPC();
         return 0;
     }

Inizio Scatto Volante AO Controllore (Fly Shoot)
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio scatto volante AO controllore (Fly Shoot)
    * @param [in] AONum Numero AO controllore
    * @param [in] maxTCPSpeed Valore massimo velocità TCP [1-5000 mm/s], default 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente al valore massimo velocità TCP, default 100%
    * @param [in] zeroZoneCmp Valore di compensazione zona morta percentuale AO, intero, default 20%, intervallo [0-100]
    * @return Codice errore
    */
    errno_t MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Fermata Scatto Volante AO Controllore
++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Fermata scatto volante AO controllore
    * @return Codice errore
    */
    errno_t MoveAOStop();
    
Inizio Scatto Volante AO Terminale
+++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio scatto volante AO terminale
    * @param [in] AONum Numero AO terminale
    * @param [in] maxTCPSpeed Valore massimo velocità TCP [1-5000 mm/s], default 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente al valore massimo velocità TCP, default 100%
    * @param [in] zeroZoneCmp Valore di compensazione zona morta percentuale AO, intero, default 20%, intervallo [0-100]
    * @return Codice errore
    */
    errno_t MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Fermata Scatto Volante AO Terminale
++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.4.0
   
.. code-block:: c++
    :linenos:

    /**
    * @brief Fermata scatto volante AO terminale
    * @return Codice errore
    */
    errno_t MoveToolAOStop();

Esempio di Codice Scatto Volante AO
++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestMoveAO(void)
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
         JointPos j1(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos j2(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose desc_pos1(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose desc_pos2(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose offset_pos(0, 0, 0, 0, 0, 0);
         DescPose offset_pos1(0, 0, 50, 0, 0, 0);
         ExaxisPos epos(0, 0, 0, 0);
         int tool = 0;
         int user = 0;
         float vel = 20.0;
         float acc = 20.0;
         float ovl = 100.0;
         float blendT = -1.0;
         uint8_t flag = 0;
         robot.SetSpeed(20);
         robot.MoveAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveAOStop();
         robot.Sleep(1000);
         robot.MoveToolAOStart(0, 100, 100, 20);
         robot.MoveJ(&j1, &desc_pos1, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveJ(&j2, &desc_pos2, tool, user, vel, acc, ovl, &epos, blendT, flag, &offset_pos);
         robot.MoveToolAOStop();
         robot.CloseRPC();
         return 0;
     }

Inizio Filtraggio FIR Movimento PtP
++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Inizio filtraggio FIR movimento PtP (Punto a Punto)
    * @param [in] maxAcc Valore massimo accelerazione (deg/s2)
    * @param [in] maxJek Valore massimo jerk unificato articolare (deg/s3)
    * @return Codice errore
    */
    errno_t PtpFIRPlanningStart(double maxAcc, double maxJek = 1000);

Fine Filtraggio FIR Movimento PtP
++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Fine filtraggio FIR movimento PtP
	* @return Codice errore
	*/
	errno_t PtpFIRPlanningEnd();

Inizio Filtraggio FIR Movimenti LIN, ARC
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Inizio filtraggio FIR movimenti LIN, ARC
	* @param [in] maxAccLin Valore massimo accelerazione lineare (mm/s2)
	* @param [in] maxAccDeg Valore massimo accelerazione angolare (deg/s2)
	* @param [in] maxJerkLin Valore massimo jerk lineare (mm/s3)
	* @param [in] maxJerkDeg Valore massimo jerk angolare (deg/s3)
	* @return Codice errore
	*/
	errno_t LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Fine Filtraggio FIR Movimenti LIN, ARC
+++++++++++++++++++++++++++++++++++++++
.. versionadded:: V3.7.7

.. code-block:: c++
    :linenos:

    /**
	* @brief Fine filtraggio FIR movimenti LIN, ARC
	* @return Codice errore
	*/
	errno_t LinArcFIRPlanningEnd();

Esempio di Codice Filtraggio FIR
+++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

     int TestFIR(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos midjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         JointPos endjointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose middescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         DescPose enddescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.PtpFIRPlanningStart(1000, 1000);
         cout << "PtpFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.PtpFIRPlanningEnd();
         cout << "PtpFIRPlanningEnd rtn is " << rtn << endl;
         robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
         cout << "LinArcFIRPlanningStart rtn is " << rtn << endl;
         robot.MoveL(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, -1, &exaxisPos, 0, 0, &offdese, 1, 1);
         robot.MoveC(&midjointPos, &middescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, &endjointPos, &enddescPose, 0, 0, 100, 100, &exaxisPos, 0, &offdese, 100, -1);
         robot.LinArcFIRPlanningEnd();
         cout << "LinArcFIRPlanningEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Attivazione Levigatura Accelerazione
+++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Attivazione levigatura accelerazione
    * @param [in] saveFlag Se salvare dopo spegnimento
    * @return Codice errore
    */
    errno_t AccSmoothStart(bool saveFlag);

Disattivazione Levigatura Accelerazione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.2.1-3.8.1

.. code-block:: c++
    :linenos:

    /**
    * @brief Disattivazione levigatura accelerazione
    * @param [in] saveFlag Se salvare dopo spegnimento
    * @return Codice errore
    */
    errno_t AccSmoothEnd(bool saveFlag);

Esempio di Codice Levigatura Accelerazione
+++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestAccSmooth(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AccSmoothStart(0);
         cout << "AccSmoothStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AccSmoothEnd(0);
         cout << "AccSmoothEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }


Attivazione Velocità Orientamento Specificata
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Attivazione velocità orientamento specificata
    * @param [in] ratio Percentuale velocità orientamento [0-300]
    * @return Codice errore
    */
    errno_t AngularSpeedStart(int ratio);

Disattivazione Velocità Orientamento Specificata
+++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Disattivazione velocità orientamento specificata
    * @return Codice errore
    */
    errno_t AngularSpeedEnd();

Esempio di Codice Velocità Orientamento Specificata Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.AngularSpeedStart(50);
         cout << "AngularSpeedStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.AngularSpeedEnd();
         cout << "AngularSpeedEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Inizio Protezione Configurazioni Singolari
+++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

	/**
	* @brief Inizio protezione configurazioni singolari
	* @param [in] protectMode Modalità protezione singolarità, 0：modalità articolare; 1-modalità cartesiana
	* @param [in] minShoulderPos Intervallo di regolazione singolarità spalla (mm), default 100
	* @param [in] minElbowPos Intervallo di regolazione singolarità gomito (mm), default 50
	* @param [in] minWristPos Intervallo di regolazione singolarità polso (°), default 10
	* @return Codice errore
	*/
	errno_t SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Fine Protezione Configurazioni Singolari
+++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

	/**
	* @brief Fine protezione configurazioni singolari
	* @return Codice errore
	*/
	errno_t SingularAvoidEnd();

Esempio di Codice Protezione Configurazioni Singolari Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestAngularSpeed(void)
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
         JointPos startjointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
         JointPos endjointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
         DescPose startdescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
         DescPose enddescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
         ExaxisPos exaxisPos(0, 0, 0, 0);
         DescPose offdese(0, 0, 0, 0, 0, 0);
         rtn = robot.SingularAvoidStart(2, 10, 5, 5);
         cout << "SingularAvoidStart rtn is " << rtn << endl;
         robot.MoveJ(&startjointPos, &startdescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         robot.MoveJ(&endjointPos, &enddescPose, 0, 0, 100, 100, 100, &exaxisPos, -1, 0, &offdese);
         rtn = robot.SingularAvoidEnd();
         cout << "SingularAvoidEnd rtn is " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }
    
Svuotamento Coda Istruzioni di Movimento
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Svuotamento coda istruzioni di movimento
    * @return Codice errore
    */
    errno_t MotionQueueClear();
        
Movimento al Punto Iniziale Linea d'Intersezione (Tubi Coppiati)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento al punto iniziale linea d'intersezione (tubi coppiati)
    * @param [in] mainPoint Pose cartesiane dei 6 punti insegnati del tubo principale
    * @param [in] mainExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo principale
    * @param [in] piecePoint Pose cartesiane dei 6 punti insegnati del tubo secondario
    * @param [in] pieceExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo di giunzione
    * @param [in] extAxisFlag Se abilitare assi estesi; 0-non abilitare; 1-abilitare
    * @param [in] exaxisPos Posizione assi estesi punto di partenza
    * @param [in] tool Numero sistema di coordinate utensile
    * @param [in] wobj Numero sistema di coordinate pezzo
    * @param [in] vel Percentuale velocità
    * @param [in] acc Percentuale accelerazione
    * @param [in] ovl Fattore di scala velocità
    * @param [in] oacc Fattore di scala accelerazione
    * @param [in] moveType Tipo di movimento; 0-PTP；1-LIN
    * @param [in] moveDirection Direzione di movimento；0-orario; 1-antiorario
    * @param [in] offset Offset
    * @return Codice errore
    */
    errno_t MoveToIntersectLineStart(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Movimento Linea d'Intersezione (Tubi Coppiati)
++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Movimento linea d'intersezione (tubi coppiati)
    * @param [in] mainPoint Pose cartesiane dei 6 punti insegnati del tubo principale
    * @param [in] mainExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo principale
    * @param [in] piecePoint Pose cartesiane dei 6 punti insegnati del tubo secondario
    * @param [in] pieceExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo di giunzione
    * @param [in] extAxisFlag Se abilitare assi estesi；0-non abilitare；1-abilitare
    * @param [in] exaxisPos Posizione assi estesi punto di partenza
    * @param [in] tool Numero sistema di coordinate utensile
    * @param [in] wobj Numero sistema di coordinate pezzo
    * @param [in] vel Percentuale velocità
    * @param [in] acc Percentuale accelerazione
    * @param [in] ovl Fattore di scala velocità
    * @param [in] oacc Fattore di scala accelerazione
    * @param [in] moveDirection Direzione di movimento; 0-orario；1-antiorario
    * @param [in] offset Offset
    * @return Codice errore
    */
    errno_t MoveIntersectLine(DescPose mainPoint[6], ExaxisPos mainExaxisPos[6], DescPose piecePoint[6], ExaxisPos pieceExaxisPos[6], int extAxisFlag, ExaxisPos exaxisPos[4], int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Esempio di Codice Movimento Linea d'Intersezione Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    void TestIntersectLineMove()
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        robot.LoggerInit();
        robot.SetLoggerLevel(3);
        int rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            return ;
        }
        robot.SetReConnectParam(true, 30000, 500);
        DescPose mainPoint[6] = {};
        DescPose piecePoint[6] = {};
        ExaxisPos mainExaxisPos[6] = {};
        ExaxisPos pieceExaxisPos[6] = {};
        int extAxisFlag = 1;
        ExaxisPos exaxisPos[4] = {};
        DescPose offset = { 0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 };
        mainPoint[0] = {490.004, -383.194, 402.735, -9.332, -1.528, 69.594};
        mainPoint[1] = {444.950, -407.117, 389.011, -5.546, -2.196, 65.279};
        mainPoint[2] = {445.168, -463.605, 355.759, -1.544, -10.886, 57.104};
        mainPoint[3] = {507.529, -485.385, 343.013, -0.786, -4.834, 61.799};
        mainPoint[4] = {554.390, -442.647, 367.701, -4.761, -10.181, 64.925};
        mainPoint[5] = {532.552, -394.003, 396.467, -13.732, -13.592, 67.411};
        mainExaxisPos[0] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[1] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[2] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[3] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[4] = { -29.996, 0.000, 0.000, 0.000 };
        mainExaxisPos[5] = { -29.996, 0.000, 0.000, 0.000 };
        piecePoint[0] = { 505.571, -192.408, 316.759, 38.098, 37.051, 139.447 };
        piecePoint[1] = {533.837, -201.558, 332.340, 34.644, 42.339, 137.748};
        piecePoint[2] = {530.386, -225.085, 373.808, 35.431, 45.111, 137.560};
        piecePoint[3] = {485.646, -229.195, 383.778, 33.870, 45.173, 137.064};
        piecePoint[4] = {460.551, -212.161, 354.256, 28.856, 45.602, 135.930};
        piecePoint[5] = {474.217, -197.124, 324.611, 42.469, 41.133, 148.167};
        pieceExaxisPos[0] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[1] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[2] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[3] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[4] = { -29.996, -0.000, 0.000, 0.000 };
        pieceExaxisPos[5] = { -29.996, -0.000, 0.000, 0.000 };
        exaxisPos[0] = {-29.996, -0.000, 0.000, 0.000};
        exaxisPos[1] = {-44.994, 90.000, 0.000, 0.000};
        exaxisPos[2] = {-59.992, 0.002, 0.000, 0.000};
        exaxisPos[3] = {-44.994, -89.997, 0.000, 0.000};
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0; 
        int moveType = 1;
        int moveDirection = 1;
        rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        printf("MoveToIntersectLineStart rtn is %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        printf("MoveIntersectLine rtn is %d\n", rtn);
        robot.CloseRPC();
        return ;
    }