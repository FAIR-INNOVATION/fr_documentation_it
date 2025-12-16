Movimento del Robot
==========================

.. toctree:: 
    :maxdepth: 5

Jog (Movimento a scatti)
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Jog - Movimento a scatti
    * @param [in] refType 0-Jog dei giunti, 2-Jog nel sistema di coordinate base, 4-Jog nel sistema di coordinate dello strumento, 8-Jog nel sistema di coordinate del pezzo
    * @param [in] nb 1-Giunto1 (o asse x), 2-Giunto2 (o asse y), 3-Giunto3 (o asse z), 4-Giunto4 (o rotazione attorno all'asse x), 5-Giunto5 (o rotazione attorno all'asse y), 6-Giunto6 (o rotazione attorno all'asse z)
    * @param [in] dir 0-Direzione negativa, 1-Direzione positiva
    * @param [in] vel Percentuale di velocità, [0~100]
    * @param [in] acc Percentuale di accelerazione, [0~100]
    * @param [in] max_dis Angolo massimo per singolo movimento a scatti, unità [°] o distanza, unità [mm]
    * @return Codice di errore
    */
    int StartJOG(int refType, int nb, int dir, double vel, double acc, double max_dis);

Arresto decelerato del movimento Jog
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Arresto decelerato del movimento Jog
    * @param  [in]  stopType  1-Arresto Jog dei giunti, 3-Arresto Jog nel sistema di coordinate base, 5-Arresto Jog nel sistema di coordinate dello strumento, 9-Arresto Jog nel sistema di coordinate del pezzo
    * @return  Codice di errore
    */
    int StopJOG(int stopType);

Arresto immediato del movimento Jog
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arresto immediato del movimento Jog
    * @return  Codice di errore
    */
    int ImmStopJOG();

Esempio di codice per il controllo Jog del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static  int TestJOG(Robot robot)
    {
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
        return 0;
    }

Movimento nello spazio dei giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento nello spazio dei giunti
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] desc_pos  Posizione cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] blendT [-1.0]-Movimento fino alla posizione (bloccante), [0~500.0]-Tempo di smoothing (non bloccante), unità ms
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @return  Codice di errore
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Movimento nello spazio dei giunti (calcolo cinematico diretto automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento nello spazio dei giunti (calcolo cinematico diretto automatico)
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] blendT [-1.0]-Movimento fino alla posizione (bloccante), [0~500.0]-Tempo di smoothing (non bloccante), unità ms
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @return Codice di errore
    */
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)

Movimento lineare nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] desc_pos  Posizione cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] blendMode Modalità di transizione; 0-Transizione tangente; 1-Transizione a spigolo
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] overSpeedStrategy  Strategia di gestione della sovravelocità, 1-Standard; 2-Arresto con errore in caso di sovravelocità; 3-Decelerazione adattativa, predefinito 0
    * @param  [in] speedPercent  Soglia percentuale consentita per la decelerazione [0-100], predefinito 10%
    * @return  Codice di errore
    */
    int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode,ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int overSpeedStrategy, int speedPercent);

Movimento lineare nello spazio cartesiano (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (calcolo cinematico inverso automatico)
    * @param [in] desc_pos  Posizione cartesiana target
    * @param [in] tool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param [in] user  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param [in] blendMode Modalità di transizione; 0-Transizione tangente; 1-Transizione a spigolo
    * @param [in] epos  Posizione dell'asse esteso, unità mm
    * @param [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param [in] offset_pos  Quantità di offset della posa
    * @param [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @param [in] overSpeedStrategy  Strategia di gestione della sovravelocità, 1-Standard; 2-Arresto con errore in caso di sovravelocità; 3-Decelerazione adattativa, predefinito 0
    * @param [in] speedPercent  Soglia percentuale consentita per la decelerazione [0-100], predefinito 10%
    * @return  Codice di errore
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] desc_pos  Posizione cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia di gestione della sovravelocità, 1-Standard; 2-Arresto con errore in caso di sovravelocità; 3-Decelerazione adattativa, predefinito 0
    * @param  [in] speedPercent  Soglia percentuale consentita per la decelerazione [0-100], predefinito 10%
    * @return  Codice di errore
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (funzione sovraccaricata 1, aggiunto blendMode)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (funzione sovraccaricata 1, aggiunto blendMode)
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] desc_pos  Posizione cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] blendMode Modalità di transizione; 0-Transizione tangente; 1-Transizione a spigolo
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia di gestione della sovravelocità, 1-Standard; 2-Arresto con errore in caso di sovravelocità; 3-Decelerazione adattativa, predefinito 0
    * @param  [in] speedPercent  Soglia percentuale consentita per la decelerazione [0-100], predefinito 10%
    * @return  Codice di errore
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (funzione sovraccaricata 2, non richiede posizione giunto in input)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (funzione sovraccaricata 2, non richiede posizione giunto in input)
    * @param  [in] desc_pos  Posizione cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] blendMode Modalità di transizione; 0-Transizione tangente; 1-Transizione a spigolo
    * @param  [in] epos  Posizione dell'asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo, 1-Ricerca del filo
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia di gestione della sovravelocità, 1-Standard; 2-Arresto con errore in caso di sovravelocità; 3-Decelerazione adattativa, predefinito 0
    * @param  [in] speedPercent  Soglia percentuale consentita per la decelerazione [0-100], predefinito 10%
    * @return  Codice di errore
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento circolare nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano
    * @param  [in] joint_pos_p  Posizione giunto del punto di percorso, unità deg
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_p  Quantità di offset della posa
    * @param  [in] joint_pos_t  Posizione giunto del punto target, unità deg
    * @param  [in] desc_pos_t  Posa cartesiana del punto target
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_t  Quantità di offset della posa
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @return  Codice di errore
    */
    int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR);

Movimento circolare nello spazio cartesiano (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (calcolo cinematico inverso automatico)
    * @param [in] desc_pos_p  Posa cartesiana del punto di percorso
    * @param [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param [in] puser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param [in] offset_pos_p  Quantità di offset della posa
    * @param [in] desc_pos_t  Posa cartesiana del punto target
    * @param [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param [in] offset_pos_t  Quantità di offset della posa
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @return  Codice di errore
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Movimento circolare nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
    * @param  [in] joint_pos_p  Posizione giunto del punto di percorso, unità deg
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_p  Quantità di offset della posa
    * @param  [in] joint_pos_t  Posizione giunto del punto target, unità deg
    * @param  [in] desc_pos_t  Posa cartesiana del punto target
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_t  Quantità di offset della posa
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Movimento circolare nello spazio cartesiano (funzione sovraccaricata 1, non richiede posizione giunto in input)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (funzione sovraccaricata 1, non richiede posizione giunto in input)
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_p  Quantità di offset della posa
    * @param  [in] desc_pos_t  Posa cartesiana del punto target
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos_t  Quantità di offset della posa
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Movimento circolare completo nello spazio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare completo nello spazio cartesiano
    * @param  [in] joint_pos_p  Posizione giunto del punto di percorso 1, unità deg
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso 1
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] joint_pos_t  Posizione giunto del punto di percorso 2, unità deg
    * @param  [in] desc_pos_t  Posa cartesiana del punto di percorso 2
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] oacc  Percentuale di accelerazione
    * @param  [in] blendR -1: Bloccante; 0~1000: Raggio di smoothing
    * @return  Codice di errore
    */
    int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR)

Movimento circolare completo nello spazio cartesiano (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
     * @brief  Movimento circolare completo nello spazio cartesiano (calcolo cinematico inverso automatico)
     * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso 1
     * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
     * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
     * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
     * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
     * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
     * @param  [in] desc_pos_t  Posa cartesiana del punto di percorso 2
     * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
     * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
     * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
     * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
     * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
     * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
     * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
     * @param  [in] offset_pos  Quantità di offset della posa
     * @param  [in] oacc  Percentuale di accelerazione
     * @param  [in] blendR -1: Bloccante; 0~1000: Raggio di smoothing
     * @param  [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
     * @return  Codice di errore
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Movimento circolare completo nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare completo nello spazio cartesiano (aggiunto parametro velAccParamMode per modalità parametri velocità/accelerazione)
    * @param  [in] joint_pos_p  Posizione giunto del punto di percorso 1, unità deg
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso 1
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] joint_pos_t  Posizione giunto del punto di percorso 2, unità deg
    * @param  [in] desc_pos_t  Posa cartesiana del punto di percorso 2
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [1~15]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [1~15]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] oacc  Percentuale di accelerazione
    * @param  [in] blendR -1: Bloccante; 0~1000: Raggio di smoothing
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimento circolare completo nello spazio cartesiano (funzione sovraccaricata 1, non richiede posizione giunto in input)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento circolare completo nello spazio cartesiano (funzione sovraccaricata 1, non richiede posizione giunto in input)
    * @param  [in] desc_pos_p  Posa cartesiana del punto di percorso 1
    * @param  [in] ptool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] puser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] pvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione dell'asse esteso, unità mm
    * @param  [in] desc_pos_t  Posa cartesiana del punto di percorso 2
    * @param  [in] ttool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] tuser  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] tvel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione dell'asse esteso, unità mm
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in] offset_pos  Quantità di offset della posa
    * @param  [in] oacc  Percentuale di accelerazione
    * @param  [in] blendR -1: Bloccante; 0~1000: Raggio di smoothing
    * @param  [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @param  [in] velAccParamMode  Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Movimento punto a punto nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento punto a punto nello spazio cartesiano
    * @param [in] desc_pos  Posa cartesiana target o incremento di posa
    * @param [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] blendT [-1.0]-Movimento fino alla posizione (bloccante), [0~500.0]-Tempo di smoothing (non bloccante), unità ms
    * @param [in] config  Configurazione dello spazio dei giunti, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Calcolo di riferimento a una specifica configurazione dello spazio dei giunti, predefinito -1
    * @return Codice di errore
    */
    int MoveCart(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendT, int config);

Esempio di codice per le istruzioni di movimento di base del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMove(Robot robot)
    {
        int rtn=-1;
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);
        JointPos j4=new JointPos(-31.154, -95.317, 94.276, -88.079, -89.740, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);
        DescPose desc_pos4=new DescPose(-443.165, 147.881, 480.951, 179.511, -0.775, -15.409);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = 0.0;
        double blendR = 0.0;
        int flag = 0;
        int search = 0;

        robot.SetSpeed(20);

        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, 0,epos, search, flag, offset_pos,0,10);
        System.out.println("movel errcode:"+ rtn);

        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR);
        System.out.println("movec errcode:"+ rtn);

        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos, j1, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos);
        System.out.println("circle errcode:"+ rtn);

        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        System.out.println("MoveCart errcode:"+ rtn);

        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, 0,epos, search, flag, offset_pos,-1,0,10);
        System.out.println("movel errcode:"+ rtn);

        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR,-1);
        System.out.println("movec errcode:"+ rtn);

        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos, ovl, flag, offset_pos, 100,-1,-1);
        System.out.println("circle errcode:"+ rtn);

        return 0;
    }

Movimento a spirale nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento a spirale nello spazio cartesiano
    * @param [in] joint_pos  Posizione giunto target, unità deg
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos  Posizione dell'asse esteso, unità mm
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param [in] offset_pos  Quantità di offset della posa
    * @param [in] spiral_param  Parametri della spirale
    * @return Codice di errore
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param);

Movimento a spirale nello spazio cartesiano (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento a spirale nello spazio cartesiano (calcolo cinematico inverso automatico)
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos  Posizione dell'asse esteso, unità mm
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema di coordinate base/del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param [in] offset_pos  Quantità di offset della posa
    * @param [in] spiral_param  Parametri della spirale
    * @param [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @return Codice di errore
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Esempio di codice per il movimento a spirale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSpiral(Robot robot)
    {
        int rtn=-1;
        JointPos j=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose offset_pos1=new DescPose(50, 0, 0, -30, 0, 0);
        DescPose offset_pos2=new DescPose(50, 0, 0, -5, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);
        SpiralParam sp=new SpiralParam(1,5.0,50.0,10.0,10.0,0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = 0.0;
        int flag = 2;

        rtn = robot.MoveJ(j, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos1);
        System.out.println("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        System.out.println("newspiral errcode:"+ rtn);

        return 0;
    }

Inizio movimento servo
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio movimento servo, da utilizzare con le istruzioni ServoJ e ServoCart
    * @return Codice di errore
    */
    int ServoMoveStart();

Fine movimento servo
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine movimento servo, da utilizzare con le istruzioni ServoJ e ServoCart
    * @return Codice di errore
    */
    int ServoMoveEnd();

Movimento in modalità servo nello spazio dei giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.6-3.8.3

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento in modalità servo nello spazio dei giunti
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] axisPos  Posizione dell'asse esterno, unità mm
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile, predefinito 0
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100], non ancora disponibile, predefinito 0
    * @param  [in] cmdT  Periodo di invio comandi, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in] filterT  Tempo di filtraggio, unità s, non ancora disponibile, predefinito 0
    * @param  [in] gain  Amplificatore proporzionale della posizione target, non ancora disponibile, predefinito 0
    * @param  [in] id  ID dell'istruzione servoJ, predefinito 0
    * @return  Codice di errore
    */
    int ServoJ(JointPos joint_pos, ExaxisPos axisPos, double acc, double vel, double cmdT, double filterT, double gain, int id);

Esempio di programma per il movimento in modalità servo nello spazio dei giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestServoJ()
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//Imposta numero di tentativi di riconnessione, intervallo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("connessione rpc successo");
        }
        else
        {
            System.out.println("connessione rpc fallita");
            return ;
        }
        JointPos j5 = new JointPos();
        ExaxisPos ePos=new ExaxisPos();
        int ret = robot.GetActualJointPosDegree(j5);
        if (ret == 0)
        {
            int count = 200;
            while (count > 0)
            {
                robot.ServoJ(j5, ePos,100, 100, 0.008, 0, 0);
                j5.J1 += 0.2;//Incrementa la posizione del giunto 1
                count -= 1;
                robot.WaitMs((int)(8));
            }
        }
    }

Inizio controllo coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inizio controllo coppia giunti
    * @return  Codice di errore
    */
    int ServoJTStart()

Controllo coppia giunti
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Controllo coppia giunti
    * @param  torque Coppia giunti j1~j6, unità Nm
    * @param  interval Periodo del comando, unità s, intervallo [0.001~0.008]
    * @param  checkFlag Strategia di rilevamento 0-Nessuna limitazione; 1-Limita potenza; 2-Limita velocità; 3-Limita sia potenza che velocità
    * @param  jPowerLimit Limite massimo di potenza del giunto (W)
    * @param  jVelLimit Velocità massima del giunto (°/s)
    * @return  Codice di errore
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit)

Fine controllo coppia giunti
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fine controllo coppia giunti
    * @return  Codice di errore
    */
    int ServoJTEnd()

Esempio di programma per il movimento in modalità servo nello spazio dei giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoJT(Robot robot)
    {

        robot.DragTeachSwitch(1);
        List<Number> joint_toq=new ArrayList<>();
        joint_toq=robot.GetJointTorques(1);

        int count = 100;
        robot.ServoJTStart(); //   #inizio servoJT
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

Esempio di codice per il controllo coppia giunti con protezione sovravelocità
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void ServoJTWithSafety(Robot robot)
    {
        robot.ResetAllError();
        robot.Sleep(500);
        List<Number> torques;
        torques=robot.GetJointTorques(1);
        robot.ServoJTStart(); //   #inizio servoJT
        ROBOT_STATE_PKG pkg=new ROBOT_STATE_PKG();
        robot.DragTeachSwitch(1);
        int checkFlag = 3;//-1,3
        //double[] jPowerLimit = {1.0,1.0,1.0,1.0,1.0,1.0};//5001
        double[] jPowerLimit = { 10.0, 10.0, 10.0, 10.0, 10.0, 10.0 };
        double[] jVelLimit = { 50, 50, 50, 50, 50, 50};//180.1,-1
        int count = 800000;
        int error = 0;
        double[] tor=new double[]{(double)torques.get(1),(double)torques.get(2),(double)torques.get(3),(double)torques.get(4),(double)torques.get(5),(double)torques.get(6)};
        while (count > 0)
        {
            tor[2] = tor[2]+0.01;//  #incrementa di 0.01NM l'asse 1 ogni volta, movimento per 100 volte
            error = robot.ServoJT(tor, 0.01, checkFlag, jPowerLimit, jVelLimit);  //# movimento in modalità servo nello spazio dei giunti
            System.out.printf("ServoJT rtn è %d\n", error);
            count = count - 1;
            robot.Sleep(1);
            pkg=robot.GetRobotRealTimeState();
            System.out.printf("codice principale %d, sottocodice %d\n", pkg.main_code, pkg.sub_code);
        }
        robot.DragTeachSwitch(0);
        error = robot.ServoJTEnd();  //#fine movimento servo
    }

Movimento in modalità servo nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento in modalità servo nello spazio cartesiano
    * @param  [in]  mode  0-Movimento assoluto (sistema di coordinate base), 1-Movimento incrementale (sistema di coordinate base), 2-Movimento incrementale (sistema di coordinate dello strumento)
    * @param  [in]  desc_pose  Posa cartesiana target o incremento di posa
    * @param  [in]  pos_gain  Coefficiente proporzionale dell'incremento di posa, attivo solo nel movimento incrementale, intervallo [0~1]
    * @param  [in]  acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile, predefinito 0
    * @param  [in]  vel  Percentuale di velocità, intervallo [0~100], non ancora disponibile, predefinito 0
    * @param  [in]  cmdT  Periodo di invio comandi, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in]  filterT  Tempo di filtraggio, unità s, non ancora disponibile, predefinito 0
    * @param  [in]  gain  Amplificatore proporzionale della posizione target, non ancora disponibile, predefinito 0
    * @return  Codice di errore
    */
    int ServoCart(int mode, DescPose desc_pose, Object[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain);

Esempio di codice per il movimento in modalità servo nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestServoCart(Robot robot)
    {
        DescPose desc_pos_dt=new DescPose(0,0,0,0,0,0);

        desc_pos_dt.tran.z = -0.5;
        Object[] pos_gain = { 0.0,0.0,1.0,0.0,0.0,0.0 };
        int mode = 2;
        double vel = 0.0;
        double acc = 0.0;
        double cmdT = 0.008;
        double filterT = 0.0;
        double gain = 0.0;
        int flag = 0;
        int count = 100;

        robot.SetSpeed(20);

        while (count>0)
        {
            robot.ServoCart(mode, desc_pos_dt, pos_gain, acc, vel, cmdT, filterT, gain);
            count -= 1;
            double time=cmdT*1000;
            robot.WaitMs((int)time);
        }

        return 0;
    }

Inizio movimento spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inizio movimento spline
    * @return  Codice di errore
    */
    int SplineStart();

Movimento PTP (Punto a Punto) nello spazio dei giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento spline nello spazio dei giunti
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] desc_pos  Posa cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @return  Codice di errore
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl);

Movimento spline nello spazio dei giunti (calcolo cinematico diretto automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento spline nello spazio dei giunti (calcolo cinematico diretto automatico)
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @return  Codice di errore
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Fine movimento spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fine movimento spline
    * @return  Codice di errore
    */
    int SplineEnd();

Esempio di codice per il movimento spline
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3=new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4=new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.SplineStart();
        robot.SplinePTP(j1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
        return 0;
    }

Inizio nuovo movimento spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio nuovo movimento spline
    * @param [in] type   0-Transizione circolare, 1-I punti dati sono punti di percorso
    * @param [in] averageTime  Tempo medio di transizione globale (ms) (10 ~ ), predefinito 2000
    * @return Codice di errore
    */
    int NewSplineStart(int type, int averageTime);

Punto di comando spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aggiunge un punto di comando per il movimento spline
    * @param [in] joint_pos  Posizione giunto target, unità deg
    * @param [in] desc_pos  Posa cartesiana target
    * @param [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param [in] lastFlag Indica se è l'ultimo punto, 0-No, 1-Sì
    * @return Codice di errore
    */
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag);

Punto di comando spline (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Punto di comando spline (calcolo cinematico inverso automatico)
    * @param  [in] desc_pos  Posa cartesiana target
    * @param  [in] tool  Numero del sistema di coordinate dello strumento, intervallo [0~14]
    * @param  [in] user  Numero del sistema di coordinate del pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala della velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino alla posizione (bloccante), [0~1000.0]-Raggio di smoothing (non bloccante), unità mm
    * @param  [in] lastFlag Indica se è l'ultimo punto, 0-No, 1-Sì
    * @param  [in] config  Configurazione dello spazio dei giunti per la soluzione inversa, [-1]-Calcolo di riferimento alla posizione attuale dei giunti, [0~7]-Soluzione basata su una specifica configurazione dello spazio dei giunti
    * @return  Codice di errore
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Fine nuovo movimento spline
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine nuovo movimento spline
    * @return Codice di errore
    */
    int NewSplineEnd();

Esempio di codice per il nuovo movimento spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestNewSpline(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3=new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4=new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);


        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;


        int err1 = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        System.out.println("movej errcode:"+ err1);
        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(desc_pos1, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos2, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos3, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos4, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplinePoint(desc_pos5, tool, user, vel, acc, ovl, -1, 0,-1);
        robot.NewSplineEnd();
        return 0;
    }

Interruzione movimento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Interruzione movimento
    * @return  Codice di errore
    */
    int StopMotion();

Pausa movimento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Pausa movimento
    * @return Codice di errore
    */
    int PauseMotion();

Ripresa movimento
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ripresa movimento
    * @return Codice di errore
    */
    int ResumeMotion();

Esempio di codice per pausa, ripresa, interruzione movimento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestPause(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5=new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5=new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);
        int rtn=-1;
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        robot.Sleep(1000);
        robot.PauseMotion();

        robot.Sleep(1000);
        robot.ResumeMotion();

        robot.Sleep(1000);
        robot.StopMotion();

        robot.Sleep(1000);

        return 0;
    }

Inizio offset globale dei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inizio offset globale dei punti
    * @param  [in]  flag  0-Offset nel sistema di coordinate base o del pezzo, 2-Offset nel sistema di coordinate dello strumento
    * @param  [in]  offset_pos  Quantità di offset della posa
    * @return  Codice di errore
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos);

Fine offset globale dei punti
+++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fine offset globale dei punti
    * @return  Codice di errore
    */
    int PointsOffsetDisable();

Esempio di codice per l'offset dei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestOffset(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.Sleep(1000);
        robot.PointsOffsetEnable(0, offset_pos1);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.PointsOffsetDisable();

        return 0;
    }

Inizio acquisizione in volo tramite AO del cabinet di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio acquisizione in volo tramite AO del cabinet di controllo
    * @param [in] AONum Numero AO del cabinet di controllo
    * @param [in] maxTCPSpeed Valore massimo velocità TCP [1-5000mm/s], predefinito 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente al valore massimo velocità TCP, predefinito 100%
    * @param [in] zeroZoneCmp Valore di compensazione zona morta percentuale AO, intero, predefinito 20%, intervallo [0-100]
    * @return Codice di errore
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Arresto acquisizione in volo tramite AO del cabinet di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arresto acquisizione in volo tramite AO del cabinet di controllo
    * @return Codice di errore
    */
    int MoveAOStop();

Inizio acquisizione in volo tramite AO dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio acquisizione in volo tramite AO dell'utensile
    * @param [in] AONum Numero AO dell'utensile
    * @param [in] maxTCPSpeed Valore massimo velocità TCP [1-5000mm/s], predefinito 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente al valore massimo velocità TCP, predefinito 100%
    * @param [in] zeroZoneCmp Valore di compensazione zona morta percentuale AO, intero, predefinito 20%, intervallo [0-100]
    * @return Codice di errore
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Arresto acquisizione in volo tramite AO dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arresto acquisizione in volo tramite AO dell'utensile
    * @return Codice di errore
    */
    int MoveToolAOStop();

Esempio di codice per l'acquisizione in volo tramite AO
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestMoveAO(Robot robot)
    {
        JointPos j1=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose desc_pos1=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        DescPose offset_pos=new DescPose(0, 0, 0, 0, 0, 0);
        DescPose offset_pos1=new DescPose(0, 0, 50, 0, 0, 0);
        ExaxisPos epos=new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        double vel = 20.0;
        double acc = 20.0;
        double ovl = 100.0;
        double blendT = -1.0;
        int flag = 0;

        robot.SetSpeed(20);

        robot.MoveAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.Sleep(1000);

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();

        return 0;
    }

Inizio filtraggio FIR per movimento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio filtraggio FIR per movimento Ptp
    * @param [in] maxAcc Valore massimo di accelerazione (deg/s2)
    * @param [in] maxJek Valore massimo uniforme di strappo del giunto (deg/s3)
    * @return Codice di errore
    */
    int PtpFIRPlanningStart(double maxAcc,double maxJek);

Fine filtraggio FIR per movimento Ptp
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine filtraggio FIR per movimento Ptp
    * @return Codice di errore
    */
    int PtpFIRPlanningEnd();

Inizio filtraggio FIR per movimento LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio filtraggio FIR per movimento LIN, ARC
    * @param [in] maxAccLin Valore massimo di accelerazione lineare (mm/s2)
    * @param [in] maxAccDeg Valore massimo di accelerazione angolare (deg/s2)
    * @param [in] maxJerkLin Valore massimo di strappo lineare (mm/s3)
    * @param [in] maxJerkDeg Valore massimo di strappo angolare (deg/s3)
    * @return Codice di errore
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Fine filtraggio FIR per movimento LIN, ARC
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Fine filtraggio FIR per movimento LIN, ARC
    * @return Codice di errore
    */
    int LinArcFIRPlanningEnd();

Esempio di codice per il filtraggio FIR
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestFIR(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos midjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos endjointPos=new JointPos(-29.777, -84.536, 109.275, -114.075, -86.655, 74.257);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose middescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose enddescPose=new DescPose(-487.434, 154.362, 308.576, 176.600, 0.268, -14.061);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);

        int rtn = robot.PtpFIRPlanningStart(1000, 1000);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 100, 100, 100, -1, 0,exaxisPos, 0, 0, offdese, 1, 1);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1);
        robot.LinArcFIRPlanningEnd();
        return 0;
    }

Attivazione smoothing accelerazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Attivazione smoothing accelerazione
     * @param [in] saveFlag Indica se salvare dopo lo spegnimento
     * @return  Codice di errore
     */
    public int AccSmoothStart(boolean saveFlag)

Disattivazione smoothing accelerazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.4-3.8.1
.. code-block:: Java
    :linenos:

    /**
     * @brief Disattivazione smoothing accelerazione
     * @param [in] saveFlag Indica se salvare dopo lo spegnimento
     * @return  Codice di errore
     */
    public int AccSmoothEnd(boolean saveFlag)

Esempio di codice per lo smoothing dell'accelerazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAccSmooth(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0,0,0,0,0,0);
        int rtn = robot.AccSmoothStart(false);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AccSmoothEnd(false);

        robot.CloseRPC();
        return 0;
    }

Attivazione velocità orientamento specificata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Attivazione velocità orientamento specificata
     * @param [in] ratio Percentuale velocità orientamento [0-300]
     * @return  Codice di errore
     */
    int AngularSpeedStart(int ratio)

Disattivazione velocità orientamento specificata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Disattivazione velocità orientamento specificata
     * @return  Codice di errore
     */
    int AngularSpeedEnd();

Esempio di codice per la velocità orientamento specificata del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Inizio protezione configurazioni singolari
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Inizio protezione configurazioni singolari
    * @param  [in]  protectMode Modalità protezione singolare, 0: Modalità giunto; 1-Modalità cartesiana
    * @param  [in]  minShoulderPos Intervallo di regolazione singolarità spalla (mm), predefinito 100
    * @param  [in]  minElbowPos Intervallo di regolazione singolarità gomito (mm), predefinito 50
    * @param  [in]  minWristPos Intervallo di regolazione singolarità polso (°), predefinito 10
    * @return  Codice di errore
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Fine protezione configurazioni singolari
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Fine protezione configurazioni singolari
    * @return  Codice di errore
    */
    int SingularAvoidEnd();

Esempio di codice per la protezione configurazioni singolari del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAngularSpeed(Robot robot)
    {
        JointPos startjointPos=new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos endjointPos=new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        DescPose startdescPose=new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose enddescPose=new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        ExaxisPos exaxisPos=new ExaxisPos(0, 0, 0, 0);
        DescPose offdese=new DescPose(0, 0, 0, 0, 0, 0);
        int rtn = robot.AngularSpeedStart(50);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.AngularSpeedEnd();

        return 0;
    }

Svuota coda istruzioni movimento
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Svuota coda istruzioni movimento
    * @return Codice di errore
    */
    public int MotionQueueClear()

Movimento verso punto di inizio linea di intersezione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento verso punto di inizio linea di intersezione
    * @param [in] mainPoint Pose cartesiane dei 6 punti insegnati del tubo principale
    * @param [in] mainExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo principale
    * @param [in] piecePoint Pose cartesiane dei 6 punti insegnati del tubo ausiliario
    * @param [in] pieceExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo di giunzione
    * @param [in] extAxisFlag Indica se attivare l'asse esteso; 0-Disattivato; 1-Attivato
    * @param [in] exaxisPos Posizione asse esteso del punto di partenza
    * @param [in] tool Numero del sistema di coordinate dello strumento
    * @param [in] wobj Numero del sistema di coordinate del pezzo
    * @param [in] vel Percentuale di velocità
    * @param [in] acc Percentuale di accelerazione
    * @param [in] ovl Fattore di scala della velocità
    * @param [in] oacc Fattore di scala dell'accelerazione
    * @param [in] moveType Tipo di movimento; 0-PTP; 1-LIN
    * @param [in] moveDirection Direzione del movimento; 0-Senso orario; 1-Senso antiorario
    * @param [in] offset Offset
    * @return Codice di errore
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);

Movimento linea di intersezione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento linea di intersezione
    * @param [in] mainPoint Pose cartesiane dei 6 punti insegnati del tubo principale
    * @param [in] mainExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo principale
    * @param [in] piecePoint Pose cartesiane dei 6 punti insegnati del tubo ausiliario
    * @param [in] pieceExaxisPos Posizioni assi estesi dei 6 punti insegnati del tubo di giunzione
    * @param [in] extAxisFlag Indica se attivare l'asse esteso; 0-Disattivato; 1-Attivato
    * @param [in] exaxisPos Posizioni assi estesi del punto di partenza
    * @param [in] tool Numero del sistema di coordinate dello strumento
    * @param [in] wobj Numero del sistema di coordinate del pezzo
    * @param [in] vel Percentuale di velocità
    * @param [in] acc Percentuale di accelerazione
    * @param [in] ovl Fattore di scala della velocità
    * @param [in] oacc Fattore di scala dell'accelerazione
    * @param [in] moveDirection Direzione del movimento; 0-Senso orario; 1-Senso antiorario
    * @param [in] offset Offset
    * @return Codice di errore
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);

Esempio di codice per il movimento linea di intersezione del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestIntersectLineMove(Robot robot)
    {
        DescPose[] mainPoint = new DescPose[6];
        DescPose[] piecePoint = new DescPose[6];
        ExaxisPos[] mainExaxisPos = new ExaxisPos[6];
        ExaxisPos[] pieceExaxisPos = new ExaxisPos[6];
        int extAxisFlag = 1;
        ExaxisPos[] exaxisPos = new ExaxisPos[4];
        DescPose offset =new DescPose(0.0, 2.0 ,30.0, -2.0, 0.0, 0.0 );
        mainPoint[0] = new DescPose(490.004, -383.194, 402.735, -9.332, -1.528, 69.594);
        mainPoint[1] = new DescPose(444.950, -407.117, 389.011, -5.546, -2.196, 65.279);
        mainPoint[2] = new DescPose(445.168, -463.605, 355.759, -1.544, -10.886, 57.104);
        mainPoint[3] = new DescPose(507.529, -485.385, 343.013, -0.786, -4.834, 61.799);
        mainPoint[4] = new DescPose(554.390, -442.647, 367.701, -4.761, -10.181, 64.925);
        mainPoint[5] = new DescPose(532.552, -394.003, 396.467, -13.732, -13.592, 67.411);
        mainExaxisPos[0] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[1] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[2] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[3] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[4] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        mainExaxisPos[5] = new ExaxisPos(-29.996, 0.000, 0.000, 0.000 );
        piecePoint[0] = new DescPose( 505.571, -192.408, 316.759, 38.098, 37.051, 139.447);
        piecePoint[1] =new DescPose(533.837, -201.558, 332.340, 34.644, 42.339, 137.748);
        piecePoint[2] =new DescPose(530.386, -225.085, 373.808, 35.431, 45.111, 137.560);
        piecePoint[3] =new DescPose(485.646, -229.195, 383.778, 33.870, 45.173, 137.064);
        piecePoint[4] =new DescPose(460.551, -212.161, 354.256, 28.856, 45.602, 135.930);
        piecePoint[5] =new DescPose(474.217, -197.124, 324.611, 42.469, 41.133, 148.167);
        pieceExaxisPos[0] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[1] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[2] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[3] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[4] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        pieceExaxisPos[5] = new ExaxisPos( -29.996, -0.000, 0.000, 0.000);
        exaxisPos[0] = new ExaxisPos(-29.996, -0.000, 0.000, 0.000);
        exaxisPos[1] = new ExaxisPos(-44.994, 90.000, 0.000, 0.000);
        exaxisPos[2] = new ExaxisPos(-59.992, 0.002, 0.000, 0.000);
        exaxisPos[3] = new ExaxisPos(-44.994, -89.997, 0.000, 0.000);
        int tool = 2;
        int wobj = 0;
        double vel = 100.0;
        double acc = 100.0;
        double ovl = 12.0;
        double oacc = 12.0;
        int moveType = 1;
        int moveDirection = 1;
        int  rtn = robot.MoveToIntersectLineStart(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos[0], tool, wobj, vel, acc, ovl, oacc, moveType, moveDirection, offset);
        System.out.printf("MoveToIntersectLineStart rtn è %d\n", rtn);
        rtn = robot.MoveIntersectLine(mainPoint, mainExaxisPos, piecePoint, pieceExaxisPos, extAxisFlag, exaxisPos, tool, wobj, vel, acc, 5.0, 5.0, moveDirection, offset);
        System.out.printf("MoveIntersectLine rtn è %d\n", rtn);
        robot.CloseRPC();
        return ;
    }