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

        robot.ProgramLoad("test.lua");
        robot.ProgramRun();

        Thread.Sleep(2000);
        robot.PauseMotion();
        Thread.Sleep(2000);
        robot.ResumeMotion();
        Thread.Sleep(2000);
    }

Impostare le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte CI configurabili del box di controllo
    * @param [in] config Codici funzione CI0-CI7;
    * 0-Nessuna;1-Avvio arco riuscito;2-Saldatrice pronta;3-Rilevamento nastro trasportatore;4-Pausa;5-Riprendi;6-Avvio;7-Arresto;
    8-Pausa/Riprendi;9-Avvio/Arresto;10-Trascinamento a pedale;11-Spostamento a origine lavoro;12-Commutazione manuale/automatica;
    13-Ricerca filo riuscita;14-Interruzione movimento;15-Avvio programma principale;16-Avvio riavvolgimento;17-Conferma avvio;
    18-Segnale rilevamento fotoelettrico X;19-Segnale rilevamento fotoelettrico Y;20-Segnale ingresso arresto emergenza esterno 1;21-Segnale ingresso arresto emergenza esterno 2;
    22-Modalità riduzione livello 1;23-Modalità riduzione livello 2;24-Modalità riduzione livello 3 (Arresto);25-Riprendi saldatura;26-Termina saldatura;
    27-Abilita trascinamento assistito;28-Disabilita trascinamento assistito;29-Abilita/Disabilita trascinamento assistito;30-Cancella tutti gli errori;
    31-Commutazione manuale/automatica (livello alto/basso);32-Abilita;33-Disabilita;34-Abilita/Disabilita (fronte di salita/discesa);35-Avvio/ fine inseguimento punto fisso
    * @return Codice di errore
    */
    public int SetDIConfig(int[] config)

Ottenere le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte CI configurabili del box di controllo
    * @param [in] config Codici funzione CI0-CI7;
    * 0-Nessuna;1-Avvio arco riuscito;2-Saldatrice pronta;3-Rilevamento nastro trasportatore;4-Pausa;5-Riprendi;6-Avvio;7-Arresto;
    8-Pausa/Riprendi;9-Avvio/Arresto;10-Trascinamento a pedale;11-Spostamento a origine lavoro;12-Commutazione manuale/automatica;
    13-Ricerca filo riuscita;14-Interruzione movimento;15-Avvio programma principale;16-Avvio riavvolgimento;17-Conferma avvio;
    18-Segnale rilevamento fotoelettrico X;19-Segnale rilevamento fotoelettrico Y;20-Segnale ingresso arresto emergenza esterno 1;21-Segnale ingresso arresto emergenza esterno 2;
    22-Modalità riduzione livello 1;23-Modalità riduzione livello 2;24-Modalità riduzione livello 3 (Arresto);25-Riprendi saldatura;26-Termina saldatura;
    27-Abilita trascinamento assistito;28-Disabilita trascinamento assistito;29-Abilita/Disabilita trascinamento assistito;30-Cancella tutti gli errori;
    31-Commutazione manuale/automatica (livello alto/basso);32-Abilita;33-Disabilita;34-Abilita/Disabilita (fronte di salita/discesa);35-Avvio/ fine inseguimento punto fisso
    * @return Codice di errore
    */
    public int GetDIConfig(out int[] config)

Impostare le Funzioni delle Porte CO Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte CO configurabili del box di controllo
    * @param [out] config Codici funzione CO0-CO7;
    * 0-Nessuna;1-Errore robot;2-Robot in movimento;3-Avvio/arresto spruzzatura;4-Pulizia pistola spruzzo;5-Segnale gas;6-Segnale avvio arco;7-Alimentazione filo a impulsi;
    8-Alimentazione filo inversa;9-Ingresso JOB 1;10-Ingresso JOB 2;11-Ingresso JOB 3;12-Controllo avvio/arresto nastro trasportatore;13-Robot in pausa;14-Origine lavoro raggiunta;
    15-Area di interferenza raggiunta;16-Controllo avvio/arresto ricerca filo;17-Avvio robot completato;18-Avvio/arresto programma;19-Modalità automatica/manuale;20-Segnale uscita arresto emergenza 1-Sicurezza;
    21-Segnale uscita arresto emergenza 2-Sicurezza;22-Esecuzione/arresto programma script Lua;23-Uscita stato sicurezza-Sicurezza;24-Uscita stato arresto protettivo-Sicurezza;
    25-Robot in movimento-Sicurezza;26-Modalità ridotta robot-Sicurezza;27-Modalità non ridotta robot-Sicurezza;28-Robot non arrestato;29-Errore robot-Errore punto istruzione;
    30-Errore robot-Errore driver;31-Errore robot-Limite software superato;32-Errore robot-Errore collisione;33-Errore robot-Errore numero slave attivi;
    34-Errore robot-Errore slave;35-Errore robot-Errore IO;36-Errore robot-Errore gripper;37-Errore robot-Errore file;38-Errore robot-Errore posa singolare;
    39-Errore robot-Errore comunicazione driver;40-Errore robot-Errore parametro;41-Errore robot-Asse esterno limite software superato;42-Avviso robot-Avviso;
    43-Avviso robot-Avviso porta sicurezza;44-Avviso robot-Avviso movimento;45-Avviso robot-Avviso area interferenza;46-Avviso robot-Avviso parete sicurezza;
    47-Stato abilitazione;48-Sollevamento automatico durante disconnessione;49-Avviso interferenza cubo 1;50-Avviso interferenza cubo 2;51-Avviso interferenza cubo 3;52-Avviso interferenza cubo 4;
    * @return Codice di errore
    */
    public int SetDOConfig(int[] config)

Ottenere le Funzioni delle Porte CO Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte CO configurabili del box di controllo
    * @param [out] config Codici funzione CO0-CO7;
    * 0-Nessuna;1-Errore robot;2-Robot in movimento;3-Avvio/arresto spruzzatura;4-Pulizia pistola spruzzo;5-Segnale gas;6-Segnale avvio arco;7-Alimentazione filo a impulsi;
    8-Alimentazione filo inversa;9-Ingresso JOB 1;10-Ingresso JOB 2;11-Ingresso JOB 3;12-Controllo avvio/arresto nastro trasportatore;13-Robot in pausa;14-Origine lavoro raggiunta;
    15-Area di interferenza raggiunta;16-Controllo avvio/arresto ricerca filo;17-Avvio robot completato;18-Avvio/arresto programma;19-Modalità automatica/manuale;20-Segnale uscita arresto emergenza 1-Sicurezza;
    21-Segnale uscita arresto emergenza 2-Sicurezza;22-Esecuzione/arresto programma script Lua;23-Uscita stato sicurezza-Sicurezza;24-Uscita stato arresto protettivo-Sicurezza;
    25-Robot in movimento-Sicurezza;26-Modalità ridotta robot-Sicurezza;27-Modalità non ridotta robot-Sicurezza;28-Robot non arrestato;29-Errore robot-Errore punto istruzione;
    30-Errore robot-Errore driver;31-Errore robot-Limite software superato;32-Errore robot-Errore collisione;33-Errore robot-Errore numero slave attivi;
    34-Errore robot-Errore slave;35-Errore robot-Errore IO;36-Errore robot-Errore gripper;37-Errore robot-Errore file;38-Errore robot-Errore posa singolare;
    39-Errore robot-Errore comunicazione driver;40-Errore robot-Errore parametro;41-Errore robot-Asse esterno limite software superato;42-Avviso robot-Avviso;
    43-Avviso robot-Avviso porta sicurezza;44-Avviso robot-Avviso movimento;45-Avviso robot-Avviso area interferenza;46-Avviso robot-Avviso parete sicurezza;
    47-Stato abilitazione;48-Sollevamento automatico durante disconnessione;49-Avviso interferenza cubo 1;50-Avviso interferenza cubo 2;51-Avviso interferenza cubo 3;52-Avviso interferenza cubo 4;
    * @return Codice di errore
    */
    public int GetDOConfig(out int[] config)

Impostare le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte End-CI configurabili dell'end-effector
    * @param [in] config Codici funzione End CI0-CI1;
    * 0-Nessuna;1-Interruttore strumento insegnamento a trascinamento;2-Segnale registrazione punto;3-Commutazione manuale/automatica (segnale impulsivo);4-Avvio/arresto registrazione TPD;5-Pausa movimento;
    6-Riprendi movimento;7-Avvio;8-Arresto;9-Pausa/Riprendi;10-Avvio/Arresto;11-Abilita trascinamento assistito sensore di forza;12-Disabilita trascinamento assistito sensore di forza;
    13-Abilita/Disabilita trascinamento assistito sensore di forza;14-Segnale rilevamento laser X;15-Segnale rilevamento laser Y;16-Movimento PTP verso origine lavoro;17-Interruzione movimento, arresta movimento corrente in base al segnale;
    18-Avvio programma principale;19-Avvio riavvolgimento;20-Conferma avvio;21-Riprendi saldatura;22-Termina saldatura;23-Cancella errore;24-Commutazione manuale/automatica (livello alto/basso);
    25-Abilita;26-Disabilita;27-Abilita/Disabilita;28-Segnale avvio/arresto inseguimento servocomando laser;
    * @return Codice di errore
    */
    public int SetToolDIConfig(int[] config)

Ottenere le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte End-CI configurabili dell'end-effector
    * @param [out] config Codici funzione End CI0-CI1;
    * 0-Nessuna;1-Interruttore strumento insegnamento a trascinamento;2-Segnale registrazione punto;3-Commutazione manuale/automatica (segnale impulsivo);4-Avvio/arresto registrazione TPD;5-Pausa movimento;
    6-Riprendi movimento;7-Avvio;8-Arresto;9-Pausa/Riprendi;10-Avvio/Arresto;11-Abilita trascinamento assistito sensore di forza;12-Disabilita trascinamento assistito sensore di forza;
    13-Abilita/Disabilita trascinamento assistito sensore di forza;14-Segnale rilevamento laser X;15-Segnale rilevamento laser Y;16-Movimento PTP verso origine lavoro;17-Interruzione movimento, arresta movimento corrente in base al segnale;
    18-Avvio programma principale;19-Avvio riavvolgimento;20-Conferma avvio;21-Riprendi saldatura;22-Termina saldatura;23-Cancella errore;24-Commutazione manuale/automatica (livello alto/basso);
    25-Abilita;26-Disabilita;27-Abilita/Disabilita;28-Segnale avvio/arresto inseguimento servocomando laser;
    * @return Codice di errore
    */
    public int GetToolDIConfig(out int[] config)
    
Impostare lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile del box di controllo
    * @param [in] config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetDIConfigLevel(int[] config)
        
Ottenere lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile del box di controllo
    * @param [out] config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetDIConfigLevel(out int[] config)
        
Impostare lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta lo stato attivo CO configurabile del box di controllo
    * @param [in] config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetDOConfigLevel(int[] config)

Ottenere lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CO configurabile del box di controllo
    * @param [out] config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetDOConfigLevel(out int[] config)
    
Impostare lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile dell'end-effector
    * @param [in] config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetToolDIConfigLevel(int[] config)
    
Ottenere lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile dell'end-effector
    * @param [out] config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetToolDIConfigLevel(out int[] config)
    
Impostare lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta lo stato attivo DI standard del box di controllo
    * @param [in] config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetStandardDILevel(int[] config)
    
Ottenere lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DI standard del box di controllo
    * @param [out] config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetStandardDILevel(out int[] config)

Impostare lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Imposta lo stato attivo DO standard del box di controllo
    * @param [in] config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetStandardDOLevel(int[] config)
    
Ottenere lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DO standard del box di controllo
    * @param [out] config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetStandardDOLevel(out int[] config)
        
Esempio di Codice di Configurazione IO del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c#
    :linenos:

    public void TestIOConfig()
    {
        int rtn = 0;

        // ---------- Test funzioni porte CI configurabili ----------
        int[] setDIConfig = new int[] { 3, 9, 1, 4, 5, 6, 7, 8 };
        rtn = robot.SetDIConfig(setDIConfig);
        Console.WriteLine($"SetDIConfig rtn is {rtn}");

        // Utilizza il parametro out per ricevere l'array di configurazione ottenuto
        int[] getDIConfig;
        rtn = robot.GetDIConfig(out getDIConfig);  
        Console.WriteLine($"GetDIConfig rtn is {rtn}, value is {string.Join(" ", getDIConfig)}");

        // ---------- Test funzioni porte CO configurabili ----------
        int[] setDOConfig = new int[] { 9, 10, 11, 12, 13, 14, 15, 16 };
        rtn = robot.SetDOConfig(setDOConfig);
        Console.WriteLine($"SetDOConfig rtn is {rtn}");

        int[] getDOConfig;
        rtn = robot.GetDOConfig(out getDOConfig);
        Console.WriteLine($"GetDOConfig rtn is {rtn}, value is {string.Join(" ", getDOConfig)}");

        // ---------- Test funzioni porte End-CI configurabili dell'end-effector ----------
        int[] setToolDIConfig = new int[] { 17, 18 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        Console.WriteLine($"SetToolDIConfig rtn is {rtn}");

        int[] getToolDIConfig;
        rtn = robot.GetToolDIConfig(out getToolDIConfig);
        Console.WriteLine($"GetToolDIConfig rtn is {rtn}, value is {string.Join(" ", getToolDIConfig)}");

        // ---------- Test stato attivo CI configurabile del box di controllo ----------
        int[] setDIConfigLevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        Console.WriteLine($"SetDIConfigLevel rtn is {rtn}");

        int[] getDIConfigLevel;
        rtn = robot.GetDIConfigLevel(out getDIConfigLevel);
        Console.WriteLine($"GetDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getDIConfigLevel)}");

        // ---------- Test stato attivo CO configurabile del box di controllo ----------
        int[] setDOConfigLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetDIConfigLevel(setDOConfigLevel);
        Console.WriteLine($"SetDOConfigLevel rtn is {rtn}");

        int[] getDOConfigLevel;
        rtn = robot.GetDOConfigLevel(out getDOConfigLevel);
        Console.WriteLine($"GetDOConfigLevel rtn is {rtn}, value is {string.Join(" ", getDOConfigLevel)}");

        // ---------- Test stato attivo CI configurabile dell'end-effector ----------
        int[] setToolDIConfigLevel = new int[] { 1, 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        Console.WriteLine($"SetToolDIConfigLevel rtn is {rtn}");

        int[] getToolDIConfigLevel;
        rtn = robot.GetToolDIConfigLevel(out getToolDIConfigLevel);
        Console.WriteLine($"GetToolDIConfigLevel rtn is {rtn}, value is {string.Join(" ", getToolDIConfigLevel)}");

        // ---------- Test stato attivo DI standard del box di controllo ----------
        int[] setStandardDILevel = new int[] { 1, 1, 1, 1, 0, 0, 0, 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        Console.WriteLine($"SetStandardDILevel rtn is {rtn}");

        int[] getStandardDILevel;
        rtn = robot.GetStandardDILevel(out getStandardDILevel);
        Console.WriteLine($"GetStandardDILevel rtn is {rtn}, value is {string.Join(" ", getStandardDILevel)}");

        // ---------- Test stato attivo DO standard del box di controllo ----------
        int[] setStandardDOLevel = new int[] { 0, 0, 0, 0, 1, 1, 1, 1 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        Console.WriteLine($"SetStandardDOLevel rtn is {rtn}");

        int[] getStandardDOLevel;
        rtn = robot.GetStandardDOLevel(out getStandardDOLevel);
        Console.WriteLine($"GetStandardDOLevel rtn is {rtn}, value is {string.Join(" ", getStandardDOLevel)}");

    }