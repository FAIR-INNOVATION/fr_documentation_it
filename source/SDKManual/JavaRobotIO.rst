I/O del Robot
==================

.. toctree:: 
    :maxdepth: 5

Impostazione uscita digitale del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta l'uscita digitale del pannello di controllo
    * @param  [in] id  Numero IO, intervallo [0~15]
    * @param  [in] status 0-Spegnimento, 1-Accensione
    * @param  [in] smooth 0-Non smooth, 1-Smooth
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @return  Codice errore
    */
    int SetDO(int id, int status, int smooth, int block);

Impostazione uscita digitale del tool
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta l'uscita digitale del tool
    * @param  [in] id  Numero IO, intervallo [0~1]
    * @param  [in] status 0-Spegnimento, 1-Accensione
    * @param  [in] smooth 0-Non smooth, 1-Smooth
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @return  Codice errore
    */
    int SetToolDO(int id, int status, int smooth, int block);

Impostazione uscita analogica del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta l'uscita analogica del pannello di controllo
    * @param  [in] id  Numero IO, intervallo [0~1]
    * @param  [in] value Percentuale del valore di corrente o tensione, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @return  Codice errore
    */
    int SetAO(int id, double value, int block);

Impostazione uscita analogica del tool
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta l'uscita analogica del tool
    * @param  [in] id  Numero IO, intervallo [0]
    * @param  [in] value Percentuale del valore di corrente o tensione, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @return  Codice errore
    */
    int SetToolAO(int id, double value, int block);

Esempio di codice per impostazione uscite digitali/analogiche
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAODO(Robot robot)
    {
        int status = 1;
        int smooth = 0;
        int block = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            robot.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            robot.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            robot.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            robot.Sleep(30);
        }

        robot.CloseRPC();
        return 0;
    }

Acquisizione ingresso digitale del pannello di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce l'ingresso digitale del pannello di controllo
    * @param  [in] id  Numero IO, intervallo [0~15]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @param  [out] level  0-Livello basso, 1-Livello alto
    * @return  Codice errore
    */   
    int GetDI(int id, int block, int[] level);

Acquisizione ingresso digitale del tool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce l'ingresso digitale del tool
    * @param  [in] id    Numero IO, intervallo [0~1]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @param  [out] level 0-Livello basso, 1-Livello alto
    * @return  Codice errore
    */   
    int GetToolDI(int id, int block, int[] level);

Acquisizione ingresso analogico del pannello di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce l'ingresso analogico del pannello di controllo
    * @param  [in] id  Numero IO, intervallo [0~1]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @param  [out] persent Percentuale del valore di corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @return  Codice errore
    */   
    int GetAI(int id, int block, double[] persent);

Acquisizione ingresso analogico del tool
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce l'ingresso analogico del tool
    * @param  [in] id  Numero IO, intervallo [0]
    * @param  [in] block  0-Blocco, 1-Non bloccante
    * @param  [out] persent Percentuale del valore di corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @return  Codice errore
    */   
    int GetToolAI(int id, int block, double[] persent);

Acquisizione stato del pulsante di registrazione punto terminale del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce lo stato del pulsante di registrazione punto terminale del robot
    * @param  [out] state Stato del pulsante, 0-Premuto, 1-Rilasciato
    * @return  Codice errore
    */   
    int GetAxlePointRecordBtnState(int[] state);

Acquisizione stato uscita DO del terminale del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce lo stato dell'uscita DO del terminale del robot
    * @param  [out] do_state Stato uscita DO, do0~do1 corrisponde a bit1~bit2, a partire da bit0
    * @return  Codice errore
    */   
    int GetToolDO(int[] do_state);

Acquisizione stato uscita DO del controller del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Acquisisce lo stato dell'uscita DO del controller del robot
    * @param  [out] do_state_h Stato uscita DO, co0~co7 corrisponde a bit0~bit7
    * @param  [out] do_state_l Stato uscita DO, do0~do7 corrisponde a bit0~bit7
    * @return  Codice errore
    */   
    int GetDO(int[] do_state_h, int[] do_state_l);

Esempio di codice per acquisizione stati DI, DO del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestGetDIAI(Robot robot)
    {
        int status = 1;
        int smooth = 0;
        int block = 0;
        int[] di = new int[]{0}, tool_di = new int[]{0};
        double[] ai = new double[]{0}, tool_ai = new double[]{0};
        double value = 0.0;

        robot.GetDI(0, block, di);
        System.out.println("di0:" + di[0]);

        robot.GetToolDI(1, block, tool_di);
        System.out.println("tool_di1:" + tool_di[0]);

        robot.GetAI(0, block, ai);
        System.out.println("ai0:" + ai[0]);

        robot.GetToolAI(0, block, tool_ai);
        System.out.println("tool_ai0:" + tool_ai[0]);

        int[] _button_state = new int[]{0};
        robot.GetAxlePointRecordBtnState(_button_state);
        System.out.println("_button_state is: " + _button_state[0]);

        int[] tool_do_state = new int[]{0};
        robot.GetToolDO(tool_do_state);
        System.out.println("tool DO state is: " + tool_do_state[0]);

        int[] do_state_h = new int[]{0};
        int[] do_state_l = new int[]{0};
        robot.GetDO(do_state_h, do_state_l);
        System.out.println("DO state high is: " + do_state_h[0] + ", DO state low is: " + do_state_l[0]);

        return 0;
    }

Attesa ingresso digitale del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attesa ingresso digitale del pannello di controllo
    * @param  [in]  id  Numero IO, intervallo [0~15]
    * @param  [in]  status 0-Spegnimento, 1-Accensione
    * @param  [in]  max_time  Tempo massimo di attesa, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Programma si ferma e segnala timeout, 1-Ignora timeout e programma continua, 2-Attesa continua
    * @return  Codice errore
    */
    int WaitDI(int id, int status, int max_time, int opt);

Attesa ingressi digitali multipli del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attesa ingressi digitali multipli del pannello di controllo
    * @param  [in] mode 0-AND multiplo, 1-OR multiplo
    * @param  [in] id  Numero IO, bit0~bit7 corrisponde a DI0~DI7, bit8~bit15 corrisponde a CI0~CI7
    * @param  [in] status 0-Spegnimento, 1-Accensione
    * @param  [in] max_time  Tempo massimo di attesa, unità ms
    * @param  [in] opt  Strategia dopo timeout, 0-Programma si ferma e segnala timeout, 1-Ignora timeout e programma continua, 2-Attesa continua
    * @return  Codice errore
    */
    int WaitMultiDI(int mode, int id, int status, int max_time, int opt);

Attesa ingresso digitale del tool
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attesa ingresso digitale del tool
    * @param  [in]  id  Numero IO, intervallo [0~1]
    * @param  [in]  status 0-Spegnimento, 1-Accensione
    * @param  [in]  max_time  Tempo massimo di attesa, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Programma si ferma e segnala timeout, 1-Ignora timeout e programma continua, 2-Attesa continua
    * @return  Codice errore
    */
    int WaitToolDI(int id, int status, int max_time, int opt);

Attesa ingresso analogico del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attesa ingresso analogico del pannello di controllo
    * @param  [in]  id  Numero IO, intervallo [0~1]
    * @param  [in]  sign 0-Maggiore di, 1-Minore di
    * @param  [in]  value Percentuale del valore di corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in]  max_time  Tempo massimo di attesa, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Programma si ferma e segnala timeout, 1-Ignora timeout e programma continua, 2-Attesa continua
    * @return  Codice errore
    */
    int WaitAI(int id, int sign, double value, int max_time, int opt);

Attesa ingresso analogico del tool
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attesa ingresso analogico del tool
    * @param  [in]  id  Numero IO, intervallo [0]
    * @param  [in]  sign 0-Maggiore di, 1-Minore di
    * @param  [in]  value Percentuale del valore di corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in]  max_time  Tempo massimo di attesa, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Programma si ferma e segnala timeout, 1-Ignora timeout e programma continua, 2-Attesa continua
    * @return  Codice errore
    */
    int WaitToolAI(int id, int sign, double value, int max_time, int opt);

Esempio di codice per attesa segnali ingresso digitale/analogico del pannello di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestWaitDIAI(Robot robot)
    {
        int rtn = -1;

        int status = 1;
        int smooth = 0;
        int block = 0;
        int di = 0, tool_di = 0;
        double ai = 0.0, tool_ai = 0.0;
        double value = 0.0;

        rtn = robot.WaitDI(0, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        System.out.println("WaitDI over; rtn is: " + rtn);
        return 0;
    }

Impostazione reset uscita DO del pannello di controllo dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita DO del pannello di controllo dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetCtlBoxDO(int resetFlag);

Impostazione reset uscita AO del pannello di controllo dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita AO del pannello di controllo dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetCtlBoxAO(int resetFlag);

Impostazione reset uscita DO del tool terminale dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita DO del tool terminale dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetAxleDO(int resetFlag);

Impostazione reset uscita AO del tool terminale dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita AO del tool terminale dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetAxleAO(int resetFlag);

Impostazione reset uscita DO estensione dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita DO estensione dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetExtDO(int resetFlag);

Impostazione reset uscita AO estensione dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare l'uscita AO estensione dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetExtAO(int resetFlag);

Impostazione reset SmartTool dopo stop/pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta se resettare SmartTool dopo stop/pausa
    * @param [in] resetFlag  0-Non resettare; 1-Resetta
    * @return Codice errore 
    */ 
    int SetOutputResetSmartToolDO(int resetFlag);

Esempio di codice per reset uscite dopo stop/pausa programma LUA
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestDOReset(Robot robot)
    {
        int rtn = -1;
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(300);
        }

        int resetFlag = 1;
        rtn = robot.SetOutputResetCtlBoxDO(resetFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag);
        robot.SetOutputResetAxleDO(resetFlag);
        robot.SetOutputResetAxleAO(resetFlag);
        robot.SetOutputResetExtDO(resetFlag);
        robot.SetOutputResetExtAO(resetFlag);
        robot.SetOutputResetSmartToolDO(resetFlag);

        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();
        return 0;
    }