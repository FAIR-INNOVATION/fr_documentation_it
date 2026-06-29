Movimento del robot
==============================

.. toctree::
    :maxdepth: 5


Jog (movimento a scatti)
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Jog (movimento a scatti)
    * @param [in] refType Tipo di movimento a scatti: 0-Jog giunto, 2-Jog in sistema di coordinate base, 4-Jog in sistema di coordinate utensile, 8-Jog in sistema di coordinate pezzo
    * @param [in] nb 1-Giunto 1 (o asse x), 2-Giunto 2 (o asse y), 3-Giunto 3 (o asse z), 4-Giunto4 (o rotazione attorno all'asse x), 5-Giunto5 (o rotazione attorno all'asse y), 6-Giunto6 (o rotazione attorno all'asse z)
    * @param [in] dir 0-Direzione negativa, 1-Direzione positiva
    * @param [in] vel Percentuale velocità, [0~100]
    * @param [in] acc Percentuale accelerazione, [0~100]
    * @param [in] max_dis Angolo massimo per singolo movimento a scatti, unità [°] o distanza, unità [mm]
    * @return Codice di errore
    */
    int StartJOG(byte refType, byte nb, byte dir, float vel, float acc, float max_dis);

Arresto decelerato movimento a scatti (Jog)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Arresto decelerato movimento a scatti (Jog)
    * @param  [in]  ref  1-Arresto decelerato movimento a scatti giunto, 3-Arresto decelerato movimento a scatti in sistema di coordinate base, 5-Arresto decelerato movimento a scatti in sistema di coordinate utensile, 9-Arresto decelerato movimento a scatti in sistema di coordinate pezzo
    * @return  Codice di errore
    */
    int StopJOG(byte stopType);

Arresto immediato movimento a scatti (Jog)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Arresto immediato movimento a scatti (Jog)
    * @return  Codice di errore
    */
    int ImmStopJOG();

Esempio di codice per il controllo movimento a scatti del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnJOG_Click(object sender, EventArgs e)
    {
        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(0, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(2, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.ImmStopJOG();
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(4, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(5);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 6; i++)
        {
            robot.StartJOG(8, i + 1, 0, 20.0f, 20.0f, 30.0f);
            Thread.Sleep(1000);
            robot.StopJOG(9);
            Thread.Sleep(1000);
        }
    }

Movimento nello spazio giunti (PTP)
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento nello spazio giunti (PTP)
    * @param  [in] joint_pos  Posizione giunti target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] epos  Posizione asse esteso, unità mm
    * @param  [in] blendT [-1.0]-Movimento fino a posizione (bloccante), [0~500.0]-Tempo smooth (non bloccante), unità ms
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @return  Codice di errore
    */
    int MoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, ExaxisPos epos, float blendT, byte offset_flag, DescPose offset_pos);

Movimento nello spazio giunti (calcolo cinematica diretta automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento nello spazio giunti (calcolo cinematica diretta automatico)
    * @param  [in] joint_pos  Posizione giunti target, unità deg
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] epos  Posizione asse esteso, unità mm
    * @param  [in] blendT [-1.0]-Movimento fino a posizione (bloccante), [0~500.0]-Tempo smooth (non bloccante), unità ms
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @return Codice di errore
    */
    int MoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos)


Movimento lineare nello spazio cartesiano (LIN)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento lineare nello spazio cartesiano
    * @param [in] joint_pos Posizione articolare target, unità deg
    * @param [in] desc_pos Posa cartesiana target
    * @param [in] tool Numero coordinate utensile, intervallo [0~14]
    * @param [in] user Numero coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], attualmente non disponibile
    * @param [in] ovl Fattore di scala velocità [0~100]/Velocità fisica (mm/s)
    * @param [in] blendR [-1.0]-Movimento a posizione (bloccante), [0~1000.0]-Raggio di transizione (non bloccante), unità mm
    * @param [in] blendMode Modalità transizione; 0-Transizione inscritta; 1-Transizione angolo
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] search 0-Nessun tracking filo saldatura, 1-Tracking filo saldatura
    * @param [in] offset_flag 0-Nessun offset, 1-Offset in sistema coordinate base/pezzo, 2-Offset in sistema coordinate utensile
    * @param [in] offset_pos Offset di posa
    * @param [in] oacc Fattore di scala accelerazione [0-100]/Accelerazione fisica (mm/s²)
    * @param [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²)
    * @param [in] overSpeedStrategy Strategia gestione sovravelocità, 1-Standard; 2-Errore e arresto su sovravelocità; 3-Riduzione velocità adattativa, default è 0
    * @param [in] speedPercent Percentuale soglia riduzione velocità consentita [0-100], default 10%
    * @return Codice errore
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, float oacc, int velAccParamMode, int overSpeedStrategy = 0, int speedPercent = 10)

Movimento lineare nello spazio cartesiano (calcolo cinematica inversa automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos   Posa cartesiana target
    * @param [in] tool  Numero sistema di coordinate utensile, intervallo [1~15]
    * @param [in] user  Numero sistema di coordinate pezzo, intervallo [1~15]
    * @param [in] vel  Percentuale velocità, intervallo [0~100]
    * @param [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param [in] blendMode Modalità transizione; 0-Transizione tangente interna; 1-Transizione ad angolo
    * @param [in] epos  Posizione asse esteso, unità mm
    * @param [in] search  0-Nessuna ricerca del filo di saldatura, 1-Ricerca del filo di saldatura
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param [in] offset_pos  Quantità offset posa
    * @param [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @param [in] overSpeedStrategy  Strategia gestione sovra-velocità, 1-Standard; 2-Arresto con errore in caso di sovra-velocità; 3-Decelerazione adattativa, default 0
    * @param [in] speedPercent  Percentuale soglia di decelerazione consentita [0-100], default 10%
    * @return  Codice di errore
    */
    int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
    * @param  [in] joint_pos  Posizione giunti target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [1~15]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] epos  Posizione asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo di saldatura, 1-Ricerca del filo di saldatura
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia gestione sovra-velocità, 1-Standard; 2-Arresto con errore in caso di sovra-velocità; 3-Decelerazione adattativa, default 0
    * @param  [in] speedPercent  Percentuale soglia di decelerazione consentita [0-100], default 10%
    * @return  Codice di errore
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (overload 1 aggiunto blendMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (overload 1 aggiunto blendMode)
    * @param  [in] joint_pos  Posizione giunti target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [1~15]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] blendMode Modalità transizione; 0-Transizione tangente interna; 1-Transizione ad angolo
    * @param  [in] epos  Posizione asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo di saldatura, 1-Ricerca del filo di saldatura
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia gestione sovra-velocità, 1-Standard; 2-Arresto con errore in caso di sovra-velocità; 3-Decelerazione adattativa, default 0
    * @param  [in] speedPercent  Percentuale soglia di decelerazione consentita [0-100], default 10%
    * @return  Codice di errore
    */
    public int MoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento lineare nello spazio cartesiano (overload 2 senza input posizione giunti)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento lineare nello spazio cartesiano (overload 2 senza input posizione giunti)
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool  Numero sistema di coordinate utensile, intervallo [1~15]
    * @param  [in] user  Numero sistema di coordinate pezzo, intervallo [1~15]
    * @param  [in] vel  Percentuale velocità, intervallo [0~100]
    * @param  [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] blendMode Modalità transizione; 0-Transizione tangente interna; 1-Transizione ad angolo
    * @param  [in] epos  Posizione asse esteso, unità mm
    * @param  [in] search  0-Nessuna ricerca del filo di saldatura, 1-Ricerca del filo di saldatura
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @param  [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @param  [in] overSpeedStrategy  Strategia gestione sovra-velocità, 1-Standard; 2-Arresto con errore in caso di sovra-velocità; 3-Decelerazione adattativa, default 0
    * @param  [in] speedPercent  Percentuale soglia di decelerazione consentita [0-100], default 10%
    * @return  Codice di errore
    */
    public int MoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int blendMode, ExaxisPos epos, int search, int offset_flag, DescPose offset_pos, int config, int velAccParamMode, int overSpeedStrategy, int speedPercent)

Movimento circolare nello spazio cartesiano (CIRC/ARC)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (CIRC/ARC)
    * @param  [in] joint_pos_p  Posizione giunti punto di percorso, unità deg
    * @param  [in] desc_pos_p   Posa cartesiana punto di percorso
    * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso, intervallo [0~14]
    * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso, intervallo [0~14]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione asse esteso punto intermedio, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_p  Quantità offset posa
    * @param  [in] joint_pos_t  Posizione giunti punto target, unità deg
    * @param  [in] desc_pos_t   Posa cartesiana punto target
    * @param  [in] ttool  Numero sistema di coordinate utensile punto target, intervallo [0~14]
    * @param  [in] tuser  Numero sistema di coordinate pezzo punto target, intervallo [0~14]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_t  Quantità offset posa
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] oacc Fattore di scala accelerazione [0-100]/Accelerazione fisica (mm/s²)
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²)
    * @return  Codice di errore
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p,JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, float tvel, float tacc,ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t,float ovl, float blendR, float oacc, int velAccParamMode)

Movimento circolare nello spazio cartesiano (calcolo cinematica inversa automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos_p   Posa cartesiana punto di percorso
    * @param [in] ptool  Numero sistema di coordinate utensile punto di percorso, intervallo [1~15]
    * @param [in] puser  Numero sistema di coordinate pezzo punto di percorso, intervallo [1~15]
    * @param [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_p  Posizione asse esteso punto intermedio, unità mm
    * @param [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param [in] offset_pos_p  Quantità offset posa
    * @param [in] desc_pos_t   Posa cartesiana punto target
    * @param [in] ttool  Numero sistema di coordinate utensile punto target, intervallo [1~15]
    * @param [in] tuser  Numero sistema di coordinate pezzo punto target, intervallo [1~15]
    * @param [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos_t  Posizione asse esteso, unità mm
    * @param [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param [in] offset_pos_t  Quantità offset posa
    * @param [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @return  Codice di errore
    */
    int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config)

Movimento circolare nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
    * @param  [in] joint_pos_p  Posizione giunti punto di percorso, unità deg
    * @param  [in] desc_pos_p   Posa cartesiana punto di percorso
    * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso, intervallo [1~15]
    * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso, intervallo [1~15]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione asse esteso punto intermedio, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_p  Quantità offset posa
    * @param  [in] joint_pos_t  Posizione giunti punto target, unità deg
    * @param  [in] desc_pos_t   Posa cartesiana punto target
    * @param  [in] ttool  Numero sistema di coordinate utensile punto target, intervallo [1~15]
    * @param  [in] tuser  Numero sistema di coordinate pezzo punto target, intervallo [1~15]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_t  Quantità offset posa
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int MoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int velAccParamMode)

Movimento circolare nello spazio cartesiano (overload 1 senza input posizione giunti)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento circolare nello spazio cartesiano (overload 1 senza input posizione giunti)
    * @param  [in] desc_pos_p   Posa cartesiana punto di percorso
    * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso, intervallo [1~15]
    * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso, intervallo [1~15]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione asse esteso punto intermedio, unità mm
    * @param  [in] poffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_p  Quantità offset posa
    * @param  [in] desc_pos_t   Posa cartesiana punto target
    * @param  [in] ttool  Numero sistema di coordinate utensile punto target, intervallo [1~15]
    * @param  [in] tuser  Numero sistema di coordinate pezzo punto target, intervallo [1~15]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione asse esteso, unità mm
    * @param  [in] toffset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos_t  Quantità offset posa
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] blendR [-1.0]-Movimento fino a posizione (bloccante), [0~1000.0]-Raggio smooth (non bloccante), unità mm
    * @param  [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int MoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR, int config, int velAccParamMode)

Movimento punto a punto nello spazio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento punto a punto nello spazio cartesiano
    * @param [in] desc_pos Posa cartesiana target nel sistema di coordinate base
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] blendT [-1.0]-Movimento fino a posizione (bloccante), [0~500.0]-Tempo smooth (non bloccante), unità ms
    * @param [in] config Configurazione spazio giunti, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Calcolo riferito a specifica configurazione spazio giunti, default -1
    * @return Codice di errore
    */
    int MoveCart(DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendT, int config);

Movimento cerchio completo nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento cerchio completo nello spazio cartesiano
    * @param  [in] joint_pos_p  Posizione giunti punto di percorso 1, unità deg
    * @param  [in] desc_pos_p   Posa cartesiana punto di percorso 1
    * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso 1, intervallo [0~14]
    * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso 1, intervallo [0~14]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione asse esteso punto di percorso 1, unità mm
    * @param  [in] joint_pos_t  Posizione giunti punto di percorso 2, unità deg
    * @param  [in] desc_pos_t   Posa cartesiana punto di percorso 2
    * @param  [in] ttool  Numero sistema di coordinate utensile punto di percorso 2, intervallo [0~14]
    * @param  [in] tuser  Numero sistema di coordinate pezzo punto di percorso 2, intervallo [0~14]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione asse esteso punto di percorso 2, unità mm
    * @param  [in] ovl  Fattore di scala velocità [0~100]/Velocità fisica (mm/s)
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset in sistema coordinate base/pezzo, 2-Offset in sistema coordinate utensile
    * @param  [in] offset_pos  Offset di posa
    * @param  [in] oacc Fattore di scala accelerazione [0-100]/Accelerazione fisica (mm/s²)
    * @param  [in] blendR -1: Bloccante; 0~1000: Raggio di transizione
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) e accelerazione (mm/s²)
    * @return  Codice errore
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, float pvel, float pacc,ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser,float tvel, float tacc, ExaxisPos epos_t, float ovl, int offset_flag,DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimento cerchio completo nello spazio cartesiano (calcolo cinematica inversa automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
     * @brief  Movimento cerchio completo nello spazio cartesiano (calcolo cinematica inversa automatico)
     * @param  [in] desc_pos_p   Posa cartesiana punto di percorso 1
     * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso 1, intervallo [0~14]
     * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso 1, intervallo [0~14]
     * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
     * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
     * @param  [in] epos_p  Posizione asse esteso punto di percorso 1, unità mm
     * @param  [in] desc_pos_t   Posa cartesiana punto di percorso 2
     * @param  [in] ttool  Numero sistema di coordinate utensile punto di percorso 2, intervallo [0~14]
     * @param  [in] tuser  Numero sistema di coordinate pezzo punto di percorso 2, intervallo [0~14]
     * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
     * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
     * @param  [in] epos_t  Posizione asse esteso punto di percorso 2, unità mm
     * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
     * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
     * @param  [in] offset_pos  Quantità offset posa
     * @param  [in] oacc Percentuale accelerazione
     * @param  [in] blendR -1: Bloccante; 0~1000: Raggio smooth
     * @param  [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
     * @return  Codice di errore
     */
    int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR,int config)

Movimento cerchio completo nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    *@brief  Movimento cerchio completo nello spazio cartesiano (aggiunto parametro modalità velocità/accelerazione velAccParamMode)
    *@param  [in] joint_pos_p  Posizione giunti punto di percorso 1, unità deg
    *@param  [in] desc_pos_p   Posa cartesiana punto di percorso 1
    *@param  [in] ptool  Numero sistema di coordinate utensile punto di percorso 1, intervallo [1~15]
    *@param  [in] puser  Numero sistema di coordinate pezzo punto di percorso 1, intervallo [1~15]
    *@param  [in] pvel  Percentuale velocità, intervallo [0~100]
    *@param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    *@param  [in] epos_p  Posizione asse esteso punto di percorso 1, unità mm
    *@param  [in] joint_pos_t  Posizione giunti punto di percorso 2, unità deg
    *@param  [in] desc_pos_t   Posa cartesiana punto di percorso 2
    *@param  [in] ttool  Numero sistema di coordinate utensile punto di percorso 2, intervallo [1~15]
    *@param  [in] tuser  Numero sistema di coordinate pezzo punto di percorso 2, intervallo [1~15]
    *@param  [in] tvel  Percentuale velocità, intervallo [0~100]
    *@param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    *@param  [in] epos_t  Posizione asse esteso punto di percorso 2, unità mm
    *@param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    *@param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    *@param  [in] offset_pos  Quantità offset posa
    *@param  [in] oacc Percentuale accelerazione
    *@param  [in] blendR -1: Bloccante; 0~1000: Raggio smooth
    *@param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    *@return  Codice di errore
    */
    public int Circle(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int velAccParamMode)

Movimento cerchio completo nello spazio cartesiano (overload 1 senza input posizione giunti)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento cerchio completo nello spazio cartesiano (overload 1 senza input posizione giunti)
    * @param  [in] desc_pos_p   Posa cartesiana punto di percorso 1
    * @param  [in] ptool  Numero sistema di coordinate utensile punto di percorso 1, intervallo [0~14]
    * @param  [in] puser  Numero sistema di coordinate pezzo punto di percorso 1, intervallo [0~14]
    * @param  [in] pvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] pacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione asse esteso punto di percorso 1, unità mm
    * @param  [in] desc_pos_t   Posa cartesiana punto di percorso 2
    * @param  [in] ttool  Numero sistema di coordinate utensile punto di percorso 2, intervallo [0~14]
    * @param  [in] tuser  Numero sistema di coordinate pezzo punto di percorso 2, intervallo [0~14]
    * @param  [in] tvel  Percentuale velocità, intervallo [0~100]
    * @param  [in] tacc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione asse esteso punto di percorso 2, unità mm
    * @param  [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param  [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param  [in] offset_pos  Quantità offset posa
    * @param  [in] oacc Percentuale accelerazione
    * @param  [in] blendR -1: Bloccante; 0~1000: Raggio smooth
    * @param  [in] config Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @param  [in] velAccParamMode Modalità parametri velocità/accelerazione; 0-Percentuale; 1-Velocità fisica (mm/s) accelerazione (mm/s2)
    * @return  Codice di errore
    */
    public int Circle(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, double ovl, int offset_flag, DescPose offset_pos, double oacc, double blendR, int config, int velAccParamMode)

Esempio di codice per istruzioni di movimento base del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    public void TestMove()
        int rtn;
        JointPos j1 = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos j2 = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos j3 = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);
        JointPos j4 = new JointPos(-31.154f, -95.317f, 94.276f, -88.079f, -89.740f, 74.256f);
        DescPose desc_pos1 = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose desc_pos2 = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose desc_pos3 = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);
        DescPose desc_pos4 = new DescPose(-443.165f, 147.881f, 480.951f, 179.511f, -0.775f, -15.409f);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float oacc = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;
        int blendMode = 0;
        int velAccMode = 0;
        robot.SetSpeed(20);
        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(j2, desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, oacc, velAccMode,0,10);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(j3, desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,j4, desc_pos4, tool, user, vel, acc, epos, flag, offset_pos, ovl, blendR, oacc, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(j3, desc_pos3, tool, user, vel, acc, epos,j1, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
        rtn = robot.MoveCart(desc_pos4, tool, user, vel, acc, ovl, blendT, -1);
        Console.WriteLine($"MoveCart errcode:{rtn}");
        rtn = robot.MoveJ(j1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.MoveL(desc_pos2, tool, user, vel, acc, ovl, blendR, blendMode, epos, search, flag, offset_pos, -1, velAccMode);
        Console.WriteLine($"movel errcode:{rtn}");
        rtn = robot.MoveC(desc_pos3, tool, user, vel, acc, epos, flag, offset_pos,desc_pos4, tool, user, vel, acc, epos, flag, offset_pos,ovl, blendR, -1, velAccMode);
        Console.WriteLine($"movec errcode:{rtn}");
        rtn = robot.MoveJ(j2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:{rtn}");
        rtn = robot.Circle(desc_pos3, tool, user, vel, acc, epos, desc_pos1, tool, user, vel, acc, epos,ovl, flag, offset_pos, oacc, blendR, -1, velAccMode);
        Console.WriteLine($"circle errcode:{rtn}");
    }

Movimento elicoidale nello spazio cartesiano
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento elicoidale nello spazio cartesiano
    * @param [in] joint_pos Posizione giunti target, unità deg
    * @param [in] desc_pos Posa cartesiana target
    * @param [in] tool Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel Percentuale velocità, intervallo [0~100]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos Posizione asse esteso, unità mm
    * @param [in] ovl Fattore di scala velocità, intervallo [0~100]
    * @param [in] offset_flag 0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param [in] offset_pos Quantità offset posa
    * @param [in] spiral_param Parametri elica
    * @return Codice di errore
    */
    int NewSpiral(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, ExaxisPos epos, float ovl, byte offset_flag, DescPose offset_pos, SpiralParam spiral_param);

Movimento elicoidale nello spazio cartesiano (calcolo cinematica inversa automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento elicoidale nello spazio cartesiano (calcolo cinematica inversa automatico)
    * @param [in] desc_pos   Posa cartesiana target
    * @param [in] tool  Numero sistema di coordinate utensile, intervallo [0~14]
    * @param [in] user  Numero sistema di coordinate pezzo, intervallo [0~14]
    * @param [in] vel  Percentuale velocità, intervallo [0~100]
    * @param [in] acc  Percentuale accelerazione, intervallo [0~100], non ancora disponibile
    * @param [in] epos  Posizione asse esteso, unità mm
    * @param [in] ovl  Fattore di scala velocità, intervallo [0~100]
    * @param [in] offset_flag  0-Nessun offset, 1-Offset nel sistema base/pezzo, 2-Offset nel sistema utensile
    * @param [in] offset_pos  Quantità offset posa
    * @param [in] spiral_param  Parametri elica
    * @param [in] config  Configurazione spazio giunti per cinematica inversa, [-1]-Calcolo riferito alla posizione giunti corrente, [0~7]-Soluzione basata su specifica configurazione spazio giunti
    * @return Codice di errore
    */
    int NewSpiral(DescPose desc_pos, int tool, int user, double vel, double acc, ExaxisPos epos, double ovl, int offset_flag, DescPose offset_pos, SpiralParam spiral_param,int config)

Esempio di codice per movimento elicoidale
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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
         Console.WriteLine("movej errcode:"+ rtn);

        rtn = robot.NewSpiral(desc_pos, tool, user, vel, acc, epos, ovl, flag, offset_pos2, sp,-1);
        Console.WriteLine("newspiral errcode:"+ rtn);

        return 0;
    }

Avvio Movimento Servo
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Avvia il movimento servo, utilizzato con i comandi ServoJ e ServoCart
    * @param[in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoMoveStart (int comType = 0)

Fine Movimento Servo
+++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Termina il movimento servo, utilizzato con i comandi ServoJ e ServoCart
    * @param[in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoMoveEnd (int comType = 0)

Movimento in Modalità Servo nello Spazio dei Giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento in modalità servo nello spazio dei giunti
    * @param  [in] joint_pos  Posizione giunto target, unità deg
    * @param  [in] axisPos  Posizione assi esterni, unità mm
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], temporaneamente non aperta, default 0
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100], temporaneamente non aperta, default 0
    * @param  [in] cmdT  Periodo di invio comando, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in] filterT Tempo di filtro, unità s, temporaneamente non aperto, default 0
    * @param  [in] gain  Amplificatore proporzionale per la posizione target, temporaneamente non aperto, default 0
    * @param  [in] id ID comando ServoJ, default 0
    * @param  [in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return  Codice di errore
    */
    public int ServoJ(JointPos joint_pos, ExaxisPos axisPos, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Esempio di Codice SDK per ServoJ, ServoMoveStart, ServoMoveEnd basato su Comunicazione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    public void TestServoJUDP()
    {
        // Iscriviti al callback
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };

        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 300;
        float dt = 0.1f;
        int cmdID = 0;

        while (true)
        {
            JointPos j = new JointPos(0, -90, 90, 0, 0, 0);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(0, -90, 90, 0, 0, 0);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);
            int ret = robot.GetActualJointPosDegree(flag, ref j);
            if (ret == 0)
            {
                count = 300;
                cmdID += 1;
                robot.ServoMoveStart(1);

                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] += dt;
                    j.jPos[1] += dt;
                    j.jPos[3] += dt;
                    j.jPos[4] += dt;
                    j.jPos[5] += dt;
                    epos.ePos[0] += dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);

                Thread.Sleep(1000);
                count = 300;
                robot.ServoMoveStart(1);
                while (count > 0)
                {
                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID, 1);
                    j.jPos[0] -= dt;
                    j.jPos[1] -= dt;
                    j.jPos[3] -= dt;
                    j.jPos[4] -= dt;
                    j.jPos[5] -= dt;
                    epos.ePos[0] -= dt;
                    count -= 1;
                    Thread.Sleep(1);
                    robot.GetRobotRealTimeState(ref pkg);
                }
                robot.ServoMoveEnd(1);
            }
            else
            {
                Console.WriteLine($"GetActualJointPosDegree errcode:{ret}");
            }
        }
    }

Esempio di codice movimento modalità servomotore spazio articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.4  Web-3.8.3
    
.. code-block:: c#
    :linenos:

    private void btnJointServoMove_Click(object sender, EventArgs e)
    {
        JointPos j = new JointPos(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.008f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 500;
        float dt = 0.1f;
        int cmdID = 0;
        int ret = robot.GetActualJointPosDegree(flag, ref j);
        if (ret == 0)
        {
            robot.ServoMoveStart();

            try
            {
                while (count > 0)
                {

                    robot.ServoJ(j, epos, acc, vel, cmdT, filterT, gain, cmdID);


                    j.jPos[0] += dt;
                    count--;


                    robot.WaitMs((int)(cmdT * 1000));
                }
            }
            finally
            {

                robot.ServoMoveEnd();
            }
        }
        else
        {
            Console.WriteLine($"GetActualJointPosDegree error code: {ret}");

        }
    }

Avvio Controllo di Coppia dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Avvia il controllo di coppia dei giunti
    * @param [in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoJTStart (int comType = 0)

Controllo di Coppia dei Giunti
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Controllo di coppia dei giunti
    * @param [in] torque Coppia giunti j1~j6, unità Nm
    * @param [in] interval Periodo del comando, unità s, intervallo [0.001~0.008]
    * @param [in] checkFlag Strategia di rilevamento 0-nessuna limitazione; 1-limitazione potenza; 2-limitazione velocità; 3-limitazione simultanea potenza e velocità
    * @param [in] jPowerLimit Limite massimo potenza giunto (W)
    * @param [in] jVelLimit Velocità massima giunto (°/s)
    * @param [in]  comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoJT(double[] torque, double interval, int checkFlag, double[] jPowerLimit, double[] jVelLimit, int comType = 0)

Fine Controllo di Coppia dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Termina il controllo di coppia dei giunti
    * @param[in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoJTEnd (int comType = 0)

Esempio di Codice SDK per ServoJT, ServoJTStart, ServoJTEnd basato su Comunicazione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafetyUDP()
    {
        // Iscriviti al callback
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[Risposta UDP] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(1);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 1);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(1);
        }
        return 0;
    }

Esempio di codice controllo coppia articolare
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button27_Click(object sender, EventArgs e)
    {
        robot.DragTeachSwitch(1);
        robot.SetPowerLimit(1, 200);
        double[] torques = { 0, 0, 0, 0, 0, 0 };
        robot.GetJointTorques(1, torques);

        int count = 100;
        robot.ServoJTStart();
        int error = 0;
        while (count > 0)
        {
            error = robot.ServoJT(torques, 0.001f);
            count--;
            Thread.Sleep(1);
        }
        error = robot.ServoJTEnd();
        robot.DragTeachSwitch(0);
    }

Esempio di codice controllo coppia articolare con protezione sovra-velocità
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJTWithSafety()
    {
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            JointPos j = new JointPos(7.053, -89.699, 156.141, -72.751, 7.829, 1.889);
            ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
            DescPose offset_pos = new DescPose(-151.288, -321.186, 221.989, 89.140, 4.361, -0.795);
            robot.MoveJ(j, 0, 0, 100, 100, 100, epos, -1, 0, offset_pos);

            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);

            robot.ServoJTStart(0);
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);

            int checkFlag = 0;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[0] = 0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[0] = -0.1;
                error = robot.ServoJT(torques, 0.008, checkFlag, jPowerLimit, jVelLimit, 0);

                Console.WriteLine($"ServoJT rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                if (pkg.jt_cur_pos[0] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoJTEnd(0);
        }
    }

Movimento modalità servomotore spazio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

Movimento in Modalità Servo Spazio Cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento in modalità servo spazio cartesiano
    * @param [in] mode 0-Movimento assoluto (sistema coordinate base), 1-Movimento incrementale (sistema coordinate base), 2-Movimento incrementale (sistema coordinate utensile)
    * @param [in] desc_pos Posa cartesiana target o incremento di posa
    * @param [in] exaxis Posizione asse esteso
    * @param [in] pos_gain Coefficiente proporzionalità incremento posa, effettivo solo nel movimento incrementale, intervallo [0~1]
    * @param [in] acc Percentuale accelerazione, intervallo [0~100], temporaneamente non disponibile, predefinito 0
    * @param [in] vel Percentuale velocità, intervallo [0~100], temporaneamente non disponibile, predefinito 0
    * @param [in] cmdT Periodo trasmissione comando, unità s, intervallo consigliato [0.001~0.016]
    * @param [in] filterT Tempo filtro, unità s, temporaneamente non disponibile, predefinito 0
    * @param [in] gain Amplificatore proporzionale posizione target, temporaneamente non disponibile, predefinito 0
    * @return Codice errore
    */
    public int ServoCart(int mode, DescPose desc_pose, ExaxisPos exaxis, double[] pos_gain, double acc, double vel, double cmdT, double filterT, double gain);

Esempio di codice movimento modalità servomotore spazio cartesiano
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestServoCart()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        int rtn;
        DescPose desc_pos_dt = new DescPose(83.00800f, 50.525000f, 29.246f, 179.629f, -7.138f, -166.975f);
        ExaxisPos exaxis = new ExaxisPos(100.0f, 0.0f, 0.0f, 0.0f);
        double[] pos_gain = { 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f };
        int mode = 0;
        float vel = 0.0f;
        float acc = 0.0f;
        float cmdT = 0.001f;
        float filterT = 0.0f;
        float gain = 0.0f;
        byte flag = 0;
        int count = 5000;

        robot.SetSpeed(20);

        while (count > 0)
        {
            rtn = robot.ServoCart(mode, desc_pos_dt, exaxis, pos_gain, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoCart rtn is {rtn}");
            count -= 1;
            desc_pos_dt.tran.x += 0.01f;
            exaxis.ePos[0] += 0.01f;
        }
    }

Inizio movimento spline
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inizio movimento spline
    * @return   Codice errore
    */
    int SplineStart();

Movimento spline PTP
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento spline spazio articolare
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool   Numero sistema coordinate utensile, range [0~14]
    * @param  [in] user   Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] vel   Percentuale velocità, range [0~100]
    * @param  [in] acc   Percentuale accelerazione, range [0~100], attualmente non disponibile
    * @param  [in] ovl   Fattore di scala velocità, range [0~100]   
    * @return   Codice errore
    */
    int SplinePTP(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl);

Movimento spline spazio articolare (calcolo cinematico diretto automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento spline spazio articolare (calcolo cinematico diretto automatico)
    * @param  [in] joint_pos  Posizione articolare target, unità deg
    * @param  [in] tool   Numero sistema coordinate utensile, range [0~14]
    * @param  [in] user   Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] vel   Percentuale velocità, range [0~100]
    * @param  [in] acc   Percentuale accelerazione, range [0~100], attualmente non disponibile
    * @param  [in] ovl   Fattore di scala velocità, range [0~100]
    * @return   Codice errore
    */
    int SplinePTP(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl)

Fine movimento spline
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fine movimento spline
    * @return   Codice errore
    */
    int SplineEnd(); 

Esempio di codice movimento spline
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnSplineMove_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.SplineStart();
        robot.SplinePTP(j1, desc_pos1, tool, user, vel, acc, ovl);
        robot.SplinePTP(j2, desc_pos2, tool, user, vel, acc, ovl);
        robot.SplinePTP(j3, desc_pos3, tool, user, vel, acc, ovl);
        robot.SplinePTP(j4, desc_pos4, tool, user, vel, acc, ovl);
        robot.SplineEnd();
    }

Inizio nuovo movimento spline
++++++++++++++++++++++++++++++++++
.. versionchanged:: C#SDK-v1.0.6

.. code-block:: c#
    :linenos:

    /** 
    * @brief Inizio nuovo movimento spline 
    * @param [in] type  0-transizione arco circolare, 1-punti dati come punti percorso
    * @param [in] averageTime  Tempo medio transizione globale(ms)(10 ~  ), default 2000
    * @return Codice errore 
    */ 
    int NewSplineStart(int type, int averageTime=2000);
    
Punto istruzione nuovo spline
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Aggiunta punto istruzione movimento spline 
    * @param [in] joint_pos Posizione articolare target, unità deg 
    * @param [in] desc_pos Posa cartesiana target 
    * @param [in] tool Numero sistema coordinate utensile, range [0~14] 
    * @param [in] user Numero sistema coordinate pezzo, range [0~14] 
    * @param [in] vel Percentuale velocità, range [0~100] 
    * @param [in] acc Percentuale accelerazione, range [0~100], attualmente non disponibile 
    * @param [in] ovl Fattore di scala velocità, range [0~100] 
    * @param [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param [in] lastFlag  Se è l'ultimo punto, 0-no, 1-sì
    * @return Codice errore 
    */ 
    int NewSplinePoint(JointPos joint_pos, DescPose desc_pos, int tool, int user, float vel, float acc, float ovl, float blendR, int lastFlag);

Punto istruzione nuovo spline (calcolo cinematico inverso automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.7  Web-3.8.5

.. code-block:: c#
    :linenos:

    /**
    * @brief Punto istruzione nuovo spline (calcolo cinematico inverso automatico)
    * @param  [in] desc_pos   Posa cartesiana target
    * @param  [in] tool   Numero sistema coordinate utensile, range [0~14]
    * @param  [in] user   Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] vel   Percentuale velocità, range [0~100]
    * @param  [in] acc   Percentuale accelerazione, range [0~100], attualmente non disponibile
    * @param  [in] ovl   Fattore di scala velocità, range [0~100]
    * @param  [in] blendR [-1.0]-movimento fino a posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param  [in] lastFlag Se è l'ultimo punto, 0-no, 1-sì
    * @param  [in] config Configurazione spazio articolare per soluzione cinematica inversa, [-1]-calcolo riferimento posizione articolare corrente, [0~7]-soluzione basata configurazione spazio articolare specifica
    * @return   Codice errore
    */
    int NewSplinePoint(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, int lastFlag,int config)

Fine nuovo movimento spline
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Inizio nuovo movimento spline 
    * @return Codice errore 
    */ 
    int NewSplineEnd();
    
Esempio di codice nuovo movimento spline
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnNewSpline_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        JointPos j3 = new JointPos(-61.954, -84.409, 108.153, -116.316, -91.283, 74.260);
        JointPos j4 = new JointPos(-89.575, -80.276, 102.713, -116.302, -91.284, 74.267);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose desc_pos3 = new DescPose(-327.622, 402.230, 320.402, -178.067, 2.127, -46.207);
        DescPose desc_pos4 = new DescPose(-104.066, 544.321, 327.023, -177.715, 3.371, -73.818);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        int err = -1;
        err = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Console.WriteLine($"movej errcode:  {err}");

        robot.NewSplineStart(1, 2000);
        robot.NewSplinePoint(j1, desc_pos1, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j2, desc_pos2, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j3, desc_pos3, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j4, desc_pos4, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplinePoint(j5, desc_pos5, tool, user, vel, acc, ovl, -1, 0);
        robot.NewSplineEnd();
    }

Terminazione movimento
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Terminazione movimento
    * @return   Codice errore
    */
    int StopMotion();

Pausa movimento
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
    
    /** 
      * @brief Pausa movimento 
      * @return Codice errore 
    */  
    int PauseMotion();

Ripresa movimento
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /** 
    * @brief Ripresa movimento 
    * @return Codice errore 
    */ 
    int ResumeMotion();

Esempio di codice pausa, ripresa, arresto movimento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMotionPause_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j5 = new JointPos(-95.228, -54.621, 73.691, -112.245, -91.280, 74.268);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos5 = new DescPose(-33.421, 732.572, 275.103, -177.907, 2.709, -79.482);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;

        robot.SetSpeed(20);

        rtn = robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        rtn = robot.MoveJ(j5, desc_pos5, tool, user, vel, acc, ovl, epos, 1, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PauseMotion();

        Thread.Sleep(1000);
        robot.ResumeMotion();

        Thread.Sleep(1000);
        robot.StopMotion();

        Thread.Sleep(1000);

    }

Inizio compensazione globale punti
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Inizio compensazione globale punti
    * @param  [in]  flag  0-compensazione in sistema base/pezzo, 2-compensazione in sistema utensile
    * @param  [in] offset_pos  Quantità compensazione posa
    * @return   Codice errore
    */
    int PointsOffsetEnable(int flag, DescPose offset_pos); 


Fine compensazione globale punti
++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Fine compensazione globale punti
    * @return   Codice errore
    */
    int PointsOffsetDisable(); 

Esempio di codice compensazione punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnPointOffect_Click(object sender, EventArgs e)
    {
        JointPos j1, j2;
        DescPose desc_pos1, desc_pos2, offset_pos, offset_pos1;
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);

        j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);

        desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);

        offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        offset_pos1 = new DescPose(50.0, 50.0, 50.0, 5.0, 5.0, 5.0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = -1.0f;
        byte flag = 0;
        int type = 0;

        robot.SetSpeed(20);

        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetEnable(type, offset_pos1);
        Thread.Sleep(1000);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        Thread.Sleep(1000);
        robot.PointsOffsetDisable();
    }

Inizio volo-ripresa AO quadro comando
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7

.. code-block:: c#
    :linenos:

    /**
    * @brief Inizio volo-ripresa AO quadro comando
    * @param [in] AONum Numero AO quadro comando
    * @param [in] maxTCPSpeed Valore massimo velocità TCP[1-5000mm/s], default 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente massima velocità TCP, default 100%
    * @param [in] zeroZoneCmp Valore compensazione zona morta percentuale AO, intero, default 20%, range [0-100]
    * @return Codice errore
    */
    int MoveAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);

Arresto volo-ripresa AO quadro comando
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Arresto volo-ripresa AO quadro comando
    * @return Codice errore
    */
    int MoveAOStop();
    
Inizio volo-ripresa AO estremità
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Inizio volo-ripresa AO estremità
    * @param [in] AONum Numero AO estremità
    * @param [in] maxTCPSpeed Valore massimo velocità TCP[1-5000mm/s], default 1000
    * @param [in] maxAOPercent Percentuale AO corrispondente massima velocità TCP, default 100%
    * @param [in] zeroZoneCmp Valore compensazione zona morta percentuale AO, intero, default 20%, range [0-100]
    * @return Codice errore
    */
    int MoveToolAOStart(int AONum, int maxTCPSpeed, int maxAOPercent, int zeroZoneCmp);
    
Arresto volo-ripresa AO estremità
++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.7
   
.. code-block:: c#
    :linenos:

    /**
    * @brief Arresto volo-ripresa AO estremità
    * @return Codice errore
    */
    int MoveToolAOStop();

Esempio di codice volo-ripresa AO
++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnMoveAO_Click(object sender, EventArgs e)
    {
        JointPos j1 = new JointPos(-11.904, -99.669, 117.473, -108.616, -91.726, 74.256);
        JointPos j2 = new JointPos(-45.615, -106.172, 124.296, -107.151, -91.282, 74.255);
        DescPose desc_pos1 = new DescPose(-419.524, -13.000, 351.569, -178.118, 0.314, 3.833);
        DescPose desc_pos2 = new DescPose(-321.222, 185.189, 335.520, -179.030, -1.284, -29.869);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);

        int tool = 0;
        int user = 0;
        float vel = 100.0f;
        float acc = 100.0f;
        float ovl = 100.0f;
        float blendT = 0.0f;
        float blendR = 0.0f;
        byte flag = 0;
        byte search = 0;

        robot.SetSpeed(5);

        robot.MoveAOStart(0,100,100,20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveAOStop();

        robot.MoveToolAOStart(0, 100, 100, 20);
        robot.MoveJ(j1, desc_pos1, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveJ(j2, desc_pos2, tool, user, vel, acc, ovl, epos, blendT, flag, offset_pos);
        robot.MoveToolAOStop();
    }

Inizio filtraggio FIR movimento Ptp
++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:


    /**
    * @brief Inizio filtraggio FIR movimento Ptp
    * @param [in] maxAcc Valore estremo massima accelerazione(deg/s2)
    * @param [in] maxJek Valore estremo jerk articolare uniforme(deg/s3)
    * @return Codice errore
    */
    int PtpFIRPlanningStart(double maxAcc, double maxJek=1000);

Disattivazione filtraggio FIR movimento Ptp
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Disattivazione filtraggio FIR movimento Ptp
    * @return Codice errore
    */
    int PtpFIRPlanningEnd();

Inizio filtraggio FIR movimento LIN, ARC
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Inizio filtraggio FIR movimento LIN, ARC
    * @param [in] maxAccLin Valore estremo accelerazione lineare(mm/s2)
    * @param [in] maxAccDeg Valore estremo accelerazione angolare(deg/s2)
    * @param [in] maxJerkLin Valore estremo jerk lineare(mm/s3)
    * @param [in] maxJerkDeg Valore estremo jerk angolare(deg/s3)
    * @return Codice errore
    */
    int LinArcFIRPlanningStart(double maxAccLin, double maxAccDeg, double maxJerkLin, double maxJerkDeg);

Disattivazione filtraggio FIR movimento LIN, ARC
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Disattivazione filtraggio FIR movimento LIN, ARC
    * @return Codice errore
    */
    int LinArcFIRPlanningEnd();

Esempio di codice filtraggio FIR
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.3  Web-3.8.2
    
.. code-block:: c#
    :linenos:


    private void button69_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos midjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);
        JointPos endjointPos = new JointPos(-29.777f, -84.536f, 109.275f, -114.075f, -86.655f, 74.257f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose middescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);
        DescPose enddescPose = new DescPose(-487.434f, 154.362f, 308.576f, 176.600f, 0.268f, -14.061f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.PtpFIRPlanningStart(1000, 1000);
        Console.WriteLine("PtpFIRPlanningStart rtn is " + rtn);
        robot.MoveJ(startjointPos, startdescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.MoveJ(endjointPos, enddescPose, 0, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.PtpFIRPlanningEnd();
        Console.WriteLine("PtpFIRPlanningEnd rtn is " + rtn);

        robot.LinArcFIRPlanningStart(1000, 1000, 1000, 1000);
        Console.WriteLine("LinArcFIRPlanningStart rtn is " + rtn);
        robot.MoveL(startjointPos, startdescPose, 0, 0, 20, 100, 100, -1,0, exaxisPos, 0, 0, offdese, 1, 50);
        robot.MoveC(midjointPos, middescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, endjointPos, enddescPose, 0, 0, 100, 100, exaxisPos, 0, offdese, 100, -1, 100, 0);
        robot.LinArcFIRPlanningEnd();
        Console.WriteLine("LinArcFIRPlanningEnd rtn is " + rtn);
    }

Attivazione levigamento accelerazione
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attivazione levigamento accelerazione
    * @param  [in] saveFlag Salvataggio dopo spegnimento
    * @return   Codice errore
    */
    int AccSmoothStart(bool saveFlag);

Disattivazione levigamento accelerazione
++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Disattivazione levigamento accelerazione
    * @param  [in] saveFlag Salvataggio dopo spegnimento
    * @return   Codice errore
    */
    int AccSmoothEnd(bool saveFlag);

Esempio di codice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button1_Click(object sender, EventArgs e)
    {

        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AccSmoothStart(false);
        Console.WriteLine("AccSmoothStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AccSmoothEnd(false);
        Console.WriteLine("AccSmoothEnd rtn is " + rtn);
    }

Attivazione velocità orientamento specificata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attivazione velocità orientamento specificata
    * @param [in] ratio Percentuale velocità orientamento[0-300]
    * @return   Codice errore
    */
    int AngularSpeedStart(int ratio);

Disattivazione velocità orientamento specificata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:
   
    /**
    * @brief Disattivazione velocità orientamento specificata
    * @return   Codice errore
    */
    int AngularSpeedEnd();

Esempio di codice velocità orientamento specificata robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button71_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);
        rtn = robot.AngularSpeedStart(50);
        Console.WriteLine("AngularSpeedStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.AngularSpeedEnd();
        Console.WriteLine("AngularSpeedEnd rtn is " + rtn);
    }

Inizio protezione postura singolare
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Inizio protezione postura singolare
    * @param [in] protectMode Modalità protezione singolarità, 0: modalità articolare; 1-modalità cartesiana
    * @param [in] minShoulderPos Intervallo regolazione singolarità spalla(mm), default 100
    * @param [in] minElbowPos Intervallo regolazione singolarità gomito(mm), default 50
    * @param [in] minWristPos Intervallo regolazione singolarità polso(°), default 10
    * @return Codice errore
    */
    int SingularAvoidStart(int protectMode, double minShoulderPos, double minElbowPos, double minWristPos);

Arresto protezione postura singolare
+++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9

.. code-block:: c#
    :linenos:

    /**
    * @brief Arresto protezione postura singolare
    * @return Codice errore
    */
    int SingularAvoidEnd();

Esempio di codice
+++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.9
    
.. code-block:: c#
    :linenos:

    private void btnTestSingularAvoidEArc_Click(object sender, EventArgs e)
    {
        int rtn;
        JointPos startjointPos = new JointPos(-11.904f, -99.669f, 117.473f, -108.616f, -91.726f, 74.256f);
        JointPos endjointPos = new JointPos(-45.615f, -106.172f, 124.296f, -107.151f, -91.282f, 74.255f);

        DescPose startdescPose = new DescPose(-419.524f, -13.000f, 351.569f, -178.118f, 0.314f, 3.833f);
        DescPose enddescPose = new DescPose(-321.222f, 185.189f, 335.520f, -179.030f, -1.284f, -29.869f);

        ExaxisPos exaxisPos = new ExaxisPos(0, 0, 0, 0);
        DescPose offdese = new DescPose(0, 0, 0, 0, 0, 0);

        rtn = robot.SingularAvoidStart(2, 10, 5, 5);
        Console.WriteLine("SingularAvoidStart rtn is " + rtn);
        robot.MoveJ( startjointPos,  startdescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        robot.MoveJ( endjointPos,  enddescPose, 0, 0, 100, 100, 100,  exaxisPos, -1, 0,  offdese);
        rtn = robot.SingularAvoidEnd();
        Console.WriteLine("SingularAvoidEnd rtn is " + rtn);
    }

Trigger arresto sicurezza
++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Segnale trigger arresto sicurezza
    * @return Codice errore
    */
    int GetSafetyCode();

Svuotamento coda istruzioni movimento
++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-V1.1.9  Web-3.8.7
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Svuotamento coda istruzioni movimento
    * @return Codice errore
    */
    public int MotionQueueClear();

Movimento a punto di partenza linea intersecante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento a punto di partenza linea intersecante
    * @param [in] mainPoint Pose cartesiane 6 punti insegnamento tubo principale
    * @param [in] mainExaxisPos Posizioni asse esteso 6 punti insegnamento tubo principale
    * @param [in] piecePoint Pose cartesiane 6 punti insegnamento tubo ausiliario
    * @param [in] pieceExaxisPos Posizioni asse esteso 6 punti insegnamento tubo di giunzione
    * @param [in] extAxisFlag Abilitazione asse esteso; 0-disabilitato; 1-abilitato
    * @param [in] exaxisPos Posizione asse esteso punto di partenza
    * @param [in] tool Numero sistema coordinate utensile
    * @param [in] wobj Numero sistema coordinate pezzo
    * @param [in] vel Percentuale velocità
    * @param [in] acc Percentuale accelerazione
    * @param [in] ovl Fattore di scala velocità
    * @param [in] oacc Fattore di scala accelerazione
    * @param [in] moveType Tipo movimento; 0-PTP；1-LIN
    * @param [in] moveDirection Direzione movimento; 0-orario; 1-antiorario
    * @param [in] offset Quantità offset
    * @return Codice errore
    */
    public int MoveToIntersectLineStart(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveType, int moveDirection, DescPose offset);
            
Movimento linea intersecante
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento linea intersecante
    * @param [in] mainPoint Pose cartesiane 6 punti insegnamento tubo principale
    * @param [in] mainExaxisPos Posizioni asse esteso 6 punti insegnamento tubo principale
    * @param [in] piecePoint Pose cartesiane 6 punti insegnamento tubo ausiliario
    * @param [in] pieceExaxisPos Posizioni asse esteso 6 punti insegnamento tubo di giunzione
    * @param [in] extAxisFlag Abilitazione asse esteso；0-disabilitato；1-abilitato
    * @param [in] exaxisPos Posizione asse esteso punto di partenza
    * @param [in] tool Numero sistema coordinate utensile
    * @param [in] wobj Numero sistema coordinate pezzo
    * @param [in] vel Percentuale velocità
    * @param [in] acc Percentuale accelerazione
    * @param [in] ovl Fattore di scala velocità
    * @param [in] oacc Fattore di scala accelerazione
    * @param [in] moveDirection Direzione movimento; 0-orario；1-antiorario
    * @param [in] offset Quantità offset
    * @return Codice errore
    */
    public int MoveIntersectLine(DescPose[] mainPoint, ExaxisPos[] mainExaxisPos, DescPose[] piecePoint, ExaxisPos[] pieceExaxisPos, int extAxisFlag, ExaxisPos[] exaxisPos, int tool, int wobj, double vel, double acc, double ovl, double oacc, int moveDirection, DescPose offset);
                
Esempio di codice movimento linea intersecante robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
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

Movimento Aereo Stazionario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Movimento Aereo Stazionario
    * @return Codice di errore
    */
    public int MoveStationary()

Esempio Codice Movimento Aereo Stazionario
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void LaserSensorRecordandReplay()
    {
        int rtn = robot.LaserSensorRecordandReplay(0, 10, 1, 0, 0.1, 1, 1, 10, 100);
        Console.WriteLine($"LaserSensorRecordandReplay rtn is {rtn}");
        rtn = robot.MoveStationary();
        Console.WriteLine($"MoveStationary rtn is {rtn}");
        rtn = robot.LaserSensorRecord1(0, 10);
        Console.WriteLine($"LaserSensorRecord1 rtn is {rtn}"); 
    }

Avvio Oscillazione a Punto Fisso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Avvia l'oscillazione a punto fisso
    * @param [in] weaveNum Numero di oscillazione [0-7]
    * @param [in] mode 0-Sistema di coordinate utensile; 1-Punto di riferimento
    * @param [in] refPoint Coordinate cartesiane del punto di riferimento [x,y,z,a,b,c]
    * @param [in] weaveTime Tempo di oscillazione [s]
    * @return Codice di errore
    */
    public int OriginPointWeaveStart(int weaveNum, int mode, DescPose refPoint, double weaveTime);
    
Fine Oscillazione a Punto Fisso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Termina l'oscillazione a punto fisso
    * @return Codice di errore
    */
    public int OriginPointWeaveEnd();
        
Esempio di Codice SDK per Oscillazione a Punto Fisso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave()
    {
        // Crea oggetto posizione giunto
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);

        // Coordinate punto di riferimento
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        //// Primo movimento
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Avvia oscillazione a punto fisso (modalità 0)
        robot.OriginPointWeaveStart(0, 0, refPoint, 3);
        robot.MoveStationary();   // Esegui movimento stazionario (supponendo che questo metodo esista)
        robot.OriginPointWeaveEnd();

        Thread.Sleep(2000);         // Attendi 2 secondi

        // Secondo movimento
        robot.MoveJ(j, 1, 0, 100, 100, 100, epos, -1, 0, offset_pos);

        // Avvia oscillazione a punto fisso (modalità 1)
        robot.OriginPointWeaveStart(0, 1, refPoint, 3);
        robot.MoveStationary();
        robot.OriginPointWeaveEnd();
    }

Esempio di Codice SDK per Oscillazione a Punto Fisso (con Laser e Asse di Estensione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    void TestOriginPointWeave2()
    {
        // Crea oggetto posizione giunto
        JointPos j = new JointPos(39.886, -98.580, -124.032, -47.393, 90.000, 40.842);
        ExaxisPos epos1 = new ExaxisPos(0, 0, 0, 0);
        DescPose offset_pos = new DescPose(0, 0, 0, 0, 0, 0);
        ExaxisPos epos2 = new ExaxisPos(5, 0.000, 0.000, 0.000);

        // Coordinate punto di riferimento
        DescPose refPoint = new DescPose(400.021, 300.022, 299.996, 179.997, -0.003, -90.956);

        int rtn = 0;
        robot.LaserTrackingSensorConfig("192.168.58.20", 5020);
        robot.LaserTrackingSensorSamplePeriod(20);
        robot.LoadPosSensorDriver(101);

        // Carica driver UDP
        robot.ExtDevLoadUDPDriver();

        // Imposta tempo di completamento del posizionamento per assi di estensione
        rtn = robot.SetExAxisCmdDoneTime(5000.0);
        Console.WriteLine("SetExAxisCmdDoneTime rtn is " + rtn);

        // Abilita assi di estensione 1 e 2
        rtn = robot.ExtAxisServoOn(1, 1);
        Console.WriteLine("ExtAxisServoOn axis id 1 rtn is " + rtn);
        rtn = robot.ExtAxisServoOn(2, 1);
        Console.WriteLine("ExtAxisServoOn axis id 2 rtn is " + rtn);
        Thread.Sleep(2000);

        // Imposta homing per asse di estensione
        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.LaserTrackingLaserOnOff(1);


        //// 1---Senza asse di estensione
        robot.LaserTrackingTrackOnOff(1, 4);
        robot.Sleep(200);
        // Avvia oscillazione a punto fisso
        robot.OriginPointWeaveStart(0, 0, refPoint, 10);
        robot.MoveStationary();   // Esegui movimento stazionario
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);

        Thread.Sleep(2000);         // Attendi 2 secondi

        //// 2---Con asse di estensione
        robot.ExtAxisMove(epos1, 100, -1);
        robot.LaserTrackingTrackOnOff(1, 4);
        // Avvia oscillazione a punto fisso
        robot.OriginPointWeaveStart(0, 0, refPoint, 20);
        robot.ExtAxisMove(epos2, 100, -1);
        robot.OriginPointWeaveEnd();
        robot.LaserTrackingTrackOnOff(0, 4);
    }

Movimento in Modalità Servo a Velocità nello Spazio dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Movimento in modalità servo a velocità nello spazio dei giunti
    * @param  [in] joint_pos  6 velocità dei giunti target, unità deg/s
    * @param  [in] axisPos  4 velocità degli assi esterni, unità deg/s
    * @param  [in] acc  Percentuale di accelerazione, intervallo [0~100], temporaneamente non aperta, default 0
    * @param  [in] vel  Percentuale di velocità, intervallo [0~100], temporaneamente non aperta, default 0
    * @param  [in] cmdT  Periodo di invio comando, unità s, intervallo consigliato [0.001~0.0016]
    * @param  [in] filterT Tempo di filtro, unità s, temporaneamente non aperto, default 0
    * @param  [in] gain  Amplificatore proporzionale per la posizione target, temporaneamente non aperto, default 0
    * @param  [in] id ID comando ServoJ, default 0
    * @param[in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return  Codice di errore
    */
    public int ServoJV(double[] joint_vel, double[] exis_vel, float acc, float vel, float cmdT, float filterT, float gain, int id = 0, int comType = 0)

Esempio di Codice per Movimento in Modalità Servo a Velocità nello Spazio dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoJVtest()
    {
        double[] joint_vel = new double[6] { 10, 0, 0, 0, 0, 0 };
        double[] exis_vel = new double[4] { 0, 0, 0, 0 };
        float acc = 0.0f; 
        float vel = 0.0f;
        float cmdT = 0.01f; 
        float filterT = 0.0f; 
        float gain = 0.0f;
        int cnt = 0;
        while (cnt < 200)
        {
            int error = robot.ServoJV(joint_vel, exis_vel, acc, vel, cmdT, filterT, gain);
            Console.WriteLine($"ServoJV rtn is {error}");
            cnt++;
        }
        return 0;
    }

Avvio Controllo MIT dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Avvio del controllo MIT dei giunti
    * @param [in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoMITStart(int comType = 0)

Fine Controllo MIT dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Fine del controllo MIT dei giunti
    * @param [in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoMITEnd(int comType = 0)

Controllo MIT dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Controllo MIT dei giunti
    * @param [in] posGain Guadagno posizione giunti j1~j6
    * @param [in] desPos Posizione desiderata giunti j1~j6, unità: deg
    * @param [in] velGain Guadagno velocità giunti j1~j6
    * @param [in] desVel Velocità desiderata giunti j1~j6, unità: deg/s
    * @param [in] torque_ff Coppia di feedforward j1~j6, unità: Nm
    * @param [in] interval Periodo del comando, unità s, intervallo [0.001~0.008]
    * @param [in] comType Tipo di invio comando; 0-xmlrpc; 1-UDP (corrisponde alla porta 20007 del robot)
    * @return Codice di errore
    */
    public int ServoMIT(double[] posGain, double[] desPos, double[] velGain, double[] desVel, double[] torque_ff, double interval, int comType = 0)

Esempio di Codice per Movimento con Controllo MIT dei Giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public int ServoMITtest()
    {
        // Iscriviti al callback
        robot.OnUdpFrameReceived += (comType, frameCount, frameCmdID, contentLen, content) =>
        {
            Console.WriteLine($"[Risposta UDP] comType={comType}, count={frameCount}, cmdID={frameCmdID}, content={content}");
        };
        while (true)
        {
            robot.ResetAllError();
            Thread.Sleep(500);

            double[] posGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desPos = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] velGain = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] desVel = new double[6] { 0, 0, 0, 0, 0, 0 };
            double[] torques = new double[6] { 0, 0, 0, 0, 0, 0 };
            robot.GetJointTorques(1, torques);
            Console.WriteLine($"111111");
            //robot.ServoMITEnd(0);
            robot.ServoMITStart(0);
            Console.WriteLine($"ServoMITStart");
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.DragTeachSwitch(1);
            Console.WriteLine($"DragTeachSwitch");
            double intev = 0.008;
            double[] jPowerLimit = new double[6] { 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
            double[] jVelLimit = new double[6] { 50, 50, 50, 50, 50, 50 };
            int error = 0;
            while (true)
            {

                torques[5] = 0.03;
                Console.WriteLine($"ServoMIT call ");
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoMIT111111 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] > 30)
                {
                    break;
                }
            }

            while (true)
            {

                torques[5] = -0.03;
                error = robot.ServoMIT(posGain, desPos, velGain, desVel, torques, intev, 0);

                Console.WriteLine($"ServoJT222222 rtn is {error}");
                Thread.Sleep(1);

                robot.GetRobotRealTimeState(ref pkg);
                //Console.WriteLine($"maincode {pkg.main_code}, subcode {pkg.sub_code}");
                Console.WriteLine($"pkg.jt_cur_pos[5]:{pkg.jt_cur_pos[5]}");
                if (pkg.jt_cur_pos[5] < 0)
                {
                    break;
                }
            }

            robot.DragTeachSwitch(0);
            error = robot.ServoMITEnd(0);
        }
        return 0;
    }