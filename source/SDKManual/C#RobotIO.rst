I/O del robot
===================

.. toctree::
    :maxdepth: 5

Imposta uscita digitale del cabinet di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta uscita digitale del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~15]
    * @param  [in] status 0-Spento, 1-Acceso
    * @param  [in] smooth 0-Non smooth, 1-Smooth
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @return  Codice di errore
    */
    int SetDO(int id, byte status, byte smooth, byte block);

Imposta uscita digitale dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta uscita digitale dell'utensile
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in] status 0-Spento, 1-Acceso
    * @param  [in] smooth 0-Non smooth, 1-Smooth
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @return  Codice di errore
    */
    int SetToolDO(int id, byte status, byte smooth, byte block);

Imposta uscita analogica del cabinet di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta uscita analogica del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in] value Percentuale valore corrente o tensione, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @return  Codice di errore
    */
    int SetAO(int id, float value, byte block);

Imposta uscita analogica dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Imposta uscita analogica dell'utensile
    * @param  [in] id  Numero io, intervallo [0]
    * @param  [in] value Percentuale valore corrente o tensione, intervallo [0~100] corrispondente a corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @return  Codice di errore
    */
    int SetToolAO(int id, float value, byte block);

Esempio di codice per impostare uscite digitali e analogiche
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button14_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;


        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 0;

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, status, smooth, block);
            Thread.Sleep(300);
        }

        status = 1;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        status = 0;

        for (int i = 0; i < 2; i++)
        {
            robot.SetToolDO(i, status, smooth, block);
            Thread.Sleep(1000);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetAO(0, i, block);
            Thread.Sleep(30);
        }

        for (int i = 0; i < 100; i++)
        {
            robot.SetToolAO(0, i, block);
            Thread.Sleep(30);
        }

    }

Ottieni ingresso digitale del cabinet di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni ingresso digitale del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~15]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @param  [out] result  0-Basso livello, 1-Alto livello
    * @return  Codice di errore
    */
    int GetDI(int id, byte block, ref byte level);

Ottieni ingresso digitale dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni ingresso digitale dell'utensile
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @param  [out] result  0-Basso livello, 1-Alto livello
    * @return  Codice di errore
    */
    int GetToolDI(int id, byte block, ref byte level);

Ottieni ingresso analogico del cabinet di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni ingresso analogico del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @param  [out] result  Percentuale valore corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mS] o tensione [0~10V]
    * @return  Codice di errore
    */
    int GetAI(int id, byte block, ref float persent);

Ottieni ingresso analogico dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottieni ingresso analogico dell'utensile
    * @param  [in] id  Numero io, intervallo [0]
    * @param  [in] block  0-Bloccante, 1-Non bloccante
    * @param  [out] result  Percentuale valore corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mS] o tensione [0~10V]
    * @return  Codice di errore
    */
    int GetToolAI(int id, byte block, ref float persent);

Ottieni lo stato del pulsante di registrazione all'estremità del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni lo stato del pulsante di registrazione all'estremità del robot
    * @param [out] state Stato pulsante, 0-Premuto, 1-Rilasciato
    * @return Codice di errore
    */
    int GetAxlePointRecordBtnState(ref byte state);

Ottieni lo stato delle uscite DO all'estremità del robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni lo stato delle uscite DO all'estremità del robot
    * @param [out] do_state Stato uscite DO, do0~do1 corrisponde a bit1~bit2, a partire da bit0
    * @return Codice di errore
    */
    int GetToolDO(ref byte do_state);

Ottieni lo stato delle uscite DO del controller del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottieni lo stato delle uscite DO del controller del robot
    * @param [out] do_state_h Stato uscite DO, co0~co7 corrisponde a bit0~bit7
    * @param [out] do_state_l Stato uscite DO, do0~do7 corrisponde a bit0~bit7
    * @return Codice di errore
    */
    int GetDO(ref int do_state_h, ref int do_state_l);

Esempio di codice per ottenere lo stato DI, DO del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void button15_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        robot.GetDI(0, block, ref di);
        Console.WriteLine($"di0: {di}");

        tool_di = (byte)robot.GetToolDI(1, block, ref tool_di);
        Console.WriteLine($"tool_di1: {tool_di}");

        robot.GetAI(0, block, ref ai);
        Console.WriteLine($"ai0: {ai}");

        tool_ai = robot.GetToolAI(0, block, ref tool_ai);
        Console.WriteLine($"tool_ai0: {tool_ai}");

        byte _button_state = 0;
        robot.GetAxlePointRecordBtnState(ref _button_state);
        Console.WriteLine($"_button_state is: {_button_state}");

        byte tool_do_state = 0;
        robot.GetToolDO(ref tool_do_state);
        Console.WriteLine($"tool DO state is: {tool_do_state}");

        int do_state_h = 0;
        int do_state_l = 0;
        robot.GetDO(ref do_state_h, ref do_state_l);
        Console.WriteLine($"DO state high is: {do_state_h}\n DO state low is: {do_state_l}");
    }

Attendi ingresso digitale del cabinet di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attendi ingresso digitale del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~15]
    * @param  [in]  status 0-Spento, 1-Acceso
    * @param  [in]  max_time  Tempo di attesa massimo, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Arresta programma e indica timeout, 1-Ignora indicazione timeout e continua esecuzione programma, 2-Aspetta indefinitamente
    * @return  Codice di errore
    */
    int WaitDI(int id, byte status, int max_time, int opt);

Attendi ingressi digitali multipli del cabinet di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attendi ingressi digitali multipli del cabinet di controllo
    * @param  [in] mode 0-AND multipli, 1-OR multipli
    * @param  [in] id  Numero io, bit0~bit7 corrisponde a DI0~DI7, bit8~bit15 corrisponde a CI0~CI7
    * @param  [in]  status 0-Spento, 1-Acceso
    * @param  [in]  max_time  Tempo di attesa massimo, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Arresta programma e indica timeout, 1-Ignora indicazione timeout e continua esecuzione programma, 2-Aspetta indefinitamente
    * @return  Codice di errore
    */
    int WaitMultiDI(int mode, int id, byte status, int max_time, int opt);

Attendi ingresso digitale dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attendi ingresso digitale dell'utensile
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in]  status 0-Spento, 1-Acceso
    * @param  [in]  max_time  Tempo di attesa massimo, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Arresta programma e indica timeout, 1-Ignora indicazione timeout e continua esecuzione programma, 2-Aspetta indefinitamente
    * @return  Codice di errore
    */
    int WaitToolDI(int id, byte status, int max_time, int opt);

Attendi ingresso analogico del cabinet di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attendi ingresso analogico del cabinet di controllo
    * @param  [in] id  Numero io, intervallo [0~1]
    * @param  [in]  sign 0-Maggiore di, 1-Minore di
    * @param  [in]  value Percentuale valore corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mS] o tensione [0~10V]
    * @param  [in]  max_time  Tempo di attesa massimo, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Arresta programma e indica timeout, 1-Ignora indicazione timeout e continua esecuzione programma, 2-Aspetta indefinitamente
    * @return  Codice di errore
    */
    int WaitAI(int id, int sign, float value, int max_time, int opt);

Attendi ingresso analogico dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Attendi ingresso analogico dell'utensile
    * @param  [in] id  Numero io, intervallo [0]
    * @param  [in]  sign 0-Maggiore di, 1-Minore di
    * @param  [in]  value Percentuale valore corrente o tensione in ingresso, intervallo [0~100] corrispondente a corrente [0~20mS] o tensione [0~10V]
    * @param  [in]  max_time  Tempo di attesa massimo, unità ms
    * @param  [in]  opt  Strategia dopo timeout, 0-Arresta programma e indica timeout, 1-Ignora indicazione timeout e continua esecuzione programma, 2-Aspetta indefinitamente
    * @return  Codice di errore
    */
    int WaitToolAI(int id, int sign, float value, int max_time, int opt);

Esempio di codice per attendere segnali di ingresso digitali e analogici del cabinet di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnIOTest_Click(object sender, EventArgs e)
    {
        byte status = 1;
        byte smooth = 0;
        byte block = 0;
        byte di = 0, tool_di = 0;
        float ai = 0.0f, tool_ai = 0.0f;
        float value = 0.0f;

        int rtn = robot.WaitDI(0, 1, 1000, 1);
        Console.WriteLine("WaitDI over; rtn is: " + rtn);

        robot.WaitMultiDI(1, 3, 3, 1000, 1);
        Console.WriteLine("WaitMultiDI over; rtn is: " + rtn);

        robot.WaitToolDI(1, 1, 1000, 1);
        Console.WriteLine("WaitToolDI over; rtn is: " + rtn);

        robot.WaitAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitAI over; rtn is: " + rtn);

        robot.WaitToolAI(0, 0, 50, 1000, 1);
        Console.WriteLine("WaitToolAI over; rtn is: " + rtn);
    }

Imposta Se Output DO Scatola Controllo Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output DO della scatola di controllo si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag);

Imposta Se Output AO Scatola Controllo Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output AO della scatola di controllo si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag);

Imposta Se Output DO Utensile Terminale Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output DO dell'utensile terminale si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag);

Imposta Se Output AO Utensile Terminale Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output AO dell'utensile terminale si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag);

Imposta Se Output DO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output DO esteso si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag);

Imposta Se Output AO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output AO esteso si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag);

Imposta Se Output SmartTool Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta se l'output SmartTool si ripristina dopo stop/pausa
    * @param [in] resetFlag 0-Non ripristina; 1-Ripristina
    * @param [in] reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag);

Esempio Codice Impostazione Ripristino Output Dopo Stop/Pausa Programma Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    public void TestDOReset()
    {
        ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();

        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            Thread.Sleep(200);
        }

        int resetFlag = 1;
        int resumeReloadFlag = 1;
        int rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag);
        robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag);

        robot.ProgramLoad("/fruser/test.lua");
        robot.ProgramRun();

        Thread.Sleep(2000);
        robot.PauseMotion();
        Thread.Sleep(2000);
        robot.ResumeMotion();
        Thread.Sleep(2000);
    }