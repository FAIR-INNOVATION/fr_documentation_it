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

Imposta Se Output DO Scatola Controllo Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output DO della scatola di controllo si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag)

Imposta Se Output AO Scatola Controllo Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output AO della scatola di controllo si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag)

Imposta Se Output DO Utensile Terminale Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output DO dell'utensile terminale si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetAxleDO(int resetFlag, int reloadFlag)

Imposta Se Output AO Utensile Terminale Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output AO dell'utensile terminale si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetAxleAO(int resetFlag, int reloadFlag)
    
Imposta Se Output DO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output DO esteso si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetExtDO(int resetFlag, int reloadFlag)
    
Imposta Se Output AO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output AO esteso si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetExtAO(int resetFlag, int reloadFlag)

Imposta Se Output SmartTool Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta se l'output SmartTool si ripristina dopo stop/pausa
    * @param resetFlag 0-Non ripristina; 1-Ripristina
    * @param reloadFlag Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica
    * @return Codice errore
    */
    public int SetOutputResetSmartToolDO(int resetFlag, int reloadFlag)

Esempio Codice Impostazione Ripristino Output Dopo Stop/Pausa Programma Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void TestDOReset(Robot robot)
    {
        for (int i = 0; i < 16; i++)
        {
            robot.SetDO(i, 1, 0, 0);
            robot.Sleep(200);
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
        robot.Sleep(2000);
        robot.PauseMotion();
        robot.Sleep(2000);
        robot.ResumeMotion();
        robot.Sleep(2000);
        robot.CloseRPC();
    }

Impostare le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte CI configurabili del box di controllo
    * @param config Codici funzione CI0-CI7;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte CI configurabili del box di controllo
    * @param config Codici funzione CI0-CI7;
    * 0-Nessuna;1-Avvio arco riuscito;2-Saldatrice pronta;3-Rilevamento nastro trasportatore;4-Pausa;5-Riprendi;6-Avvio;7-Arresto;
    8-Pausa/Riprendi;9-Avvio/Arresto;10-Trascinamento a pedale;11-Spostamento a origine lavoro;12-Commutazione manuale/automatica;
    13-Ricerca filo riuscita;14-Interruzione movimento;15-Avvio programma principale;16-Avvio riavvolgimento;17-Conferma avvio;
    18-Segnale rilevamento fotoelettrico X;19-Segnale rilevamento fotoelettrico Y;20-Segnale ingresso arresto emergenza esterno 1;21-Segnale ingresso arresto emergenza esterno 2;
    22-Modalità riduzione livello 1;23-Modalità riduzione livello 2;24-Modalità riduzione livello 3 (Arresto);25-Riprendi saldatura;26-Termina saldatura;
    27-Abilita trascinamento assistito;28-Disabilita trascinamento assistito;29-Abilita/Disabilita trascinamento assistito;30-Cancella tutti gli errori;
    31-Commutazione manuale/automatica (livello alto/basso);32-Abilita;33-Disabilita;34-Abilita/Disabilita (fronte di salita/discesa);35-Avvio/ fine inseguimento punto fisso
    * @return Codice di errore
    */
    public int GetDIConfig(int[] config)

Impostare le Funzioni delle Porte CO Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte CO configurabili del box di controllo
    * @param config Codici funzione CO0-CO7;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte CO configurabili del box di controllo
    * @param config Codici funzione CO0-CO7;
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
    public int GetDOConfig(int[] config)

Impostare le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta le funzioni delle porte End-CI configurabili dell'end-effector
    * @param config Codici funzione End CI0-CI1;
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
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene le funzioni delle porte End-CI configurabili dell'end-effector
    * @param config Codici funzione End CI0-CI1;
    * 0-Nessuna;1-Interruttore strumento insegnamento a trascinamento;2-Segnale registrazione punto;3-Commutazione manuale/automatica (segnale impulsivo);4-Avvio/arresto registrazione TPD;5-Pausa movimento;
    6-Riprendi movimento;7-Avvio;8-Arresto;9-Pausa/Riprendi;10-Avvio/Arresto;11-Abilita trascinamento assistito sensore di forza;12-Disabilita trascinamento assistito sensore di forza;
    13-Abilita/Disabilita trascinamento assistito sensore di forza;14-Segnale rilevamento laser X;15-Segnale rilevamento laser Y;16-Movimento PTP verso origine lavoro;17-Interruzione movimento, arresta movimento corrente in base al segnale;
    18-Avvio programma principale;19-Avvio riavvolgimento;20-Conferma avvio;21-Riprendi saldatura;22-Termina saldatura;23-Cancella errore;24-Commutazione manuale/automatica (livello alto/basso);
    25-Abilita;26-Disabilita;27-Abilita/Disabilita;28-Segnale avvio/arresto inseguimento servocomando laser;
    * @return Codice di errore
    */
    public int GetToolDIConfig(int[] config)
    
Impostare lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile del box di controllo
    * @param config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetDIConfigLevel(int[] config)
        
Ottenere lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile del box di controllo
    * @param config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetDIConfigLevel(int[] config)
        
Impostare lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta lo stato attivo CO configurabile del box di controllo
    * @param config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetDOConfigLevel(int[] config)

Ottenere lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CO configurabile del box di controllo
    * @param config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetDOConfigLevel(int[] config)
    
Impostare lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile dell'end-effector
    * @param config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetToolDIConfigLevel(int[] config)
    
Ottenere lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile dell'end-effector
    * @param config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetToolDIConfigLevel(int[] config)
    
Impostare lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta lo stato attivo DI standard del box di controllo
    * @param config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetStandardDILevel(int[] config)
    
Ottenere lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DI standard del box di controllo
    * @param config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetStandardDILevel(int[] config)

Impostare lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta lo stato attivo DO standard del box di controllo
    * @param config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int SetStandardDOLevel(int[] config)
    
Ottenere lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DO standard del box di controllo
    * @param config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    public int GetStandardDOLevel(int[] config)
        
Esempio di Codice di Configurazione IO del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: Java
    :linenos:

    public static int TestIOConfig(Robot robot) {
        int[] setDIConfig = new int[]{1, 2, 3, 4, 5, 6, 7, 8};
        int[] getDIConfig = new int[8];
        int rtn = robot.SetDIConfig(setDIConfig);
        System.out.println("SetDIConfig rtn is " + rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        System.out.println("GetDIConfig rtn is " + rtn + ", value is " + 
            getDIConfig[0] + " " + getDIConfig[1] + " " + getDIConfig[2] + " " + getDIConfig[3] + " " + 
            getDIConfig[4] + " " + getDIConfig[5] + " " + getDIConfig[6] + " " + getDIConfig[7]);

        int[] setDOConfig = new int[]{9, 10, 11, 12, 13, 14, 15, 16};
        int[] getDOConfig = new int[8];
        rtn = robot.SetDOConfig(setDOConfig);
        System.out.println("SetDOConfig rtn is " + rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        System.out.println("GetDOConfig rtn is " + rtn + ", value is " + 
            getDOConfig[0] + " " + getDOConfig[1] + " " + getDOConfig[2] + " " + getDOConfig[3] + " " + 
            getDOConfig[4] + " " + getDOConfig[5] + " " + getDOConfig[6] + " " + getDOConfig[7]);

        int[] setToolDIConfig = new int[]{17, 18};
        int[] getToolDIConfig = new int[2];
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        System.out.println("SetToolDIConfig rtn is " + rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        System.out.println("GetToolDIConfig rtn is " + rtn + ", value is " + getToolDIConfig[0] + " " + getToolDIConfig[1]);

        int[] setDIConfigLevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getDIConfigLevel = new int[8];
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        System.out.println("SetDIConfigLevel rtn is " + rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        System.out.println("GetDIConfigLevel rtn is " + rtn + ", value is " + 
            getDIConfigLevel[0] + " " + getDIConfigLevel[1] + " " + getDIConfigLevel[2] + " " + getDIConfigLevel[3] + " " + 
            getDIConfigLevel[4] + " " + getDIConfigLevel[5] + " " + getDIConfigLevel[6] + " " + getDIConfigLevel[7]);

        int[] setDOConfigLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getDOConfigLevel = new int[8];
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        System.out.println("SetDOConfigLevel rtn is " + rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        System.out.println("GetDOConfigLevel rtn is " + rtn + ", value is " + 
            getDOConfigLevel[0] + " " + getDOConfigLevel[1] + " " + getDOConfigLevel[2] + " " + getDOConfigLevel[3] + " " + 
            getDOConfigLevel[4] + " " + getDOConfigLevel[5] + " " + getDOConfigLevel[6] + " " + getDOConfigLevel[7]);

        int[] setToolDIConfigLevel = new int[]{1, 0};
        int[] getToolDIConfigLevel = new int[2];
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        System.out.println("SetToolDIConfigLevel rtn is " + rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        System.out.println("GetToolDIConfigLevel rtn is " + rtn + ", value is " + getToolDIConfigLevel[0] + " " + getToolDIConfigLevel[1]);

        int[] setStandardDILevel = new int[]{1, 1, 1, 1, 0, 0, 0, 0};
        int[] getStandardDILevel = new int[8];
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        System.out.println("SetStandardDILevel rtn is " + rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        System.out.println("GetStandardDILevel rtn is " + rtn + ", value is " + 
            getStandardDILevel[0] + " " + getStandardDILevel[1] + " " + getStandardDILevel[2] + " " + getStandardDILevel[3] + " " + 
            getStandardDILevel[4] + " " + getStandardDILevel[5] + " " + getStandardDILevel[6] + " " + getStandardDILevel[7]);

        int[] setStandardDOLevel = new int[]{0, 0, 0, 0, 1, 1, 1, 1};
        int[] getStandardDOLevel = new int[8];
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        System.out.println("SetStandardDOLevel rtn is " + rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        System.out.println("GetStandardDOLevel rtn is " + rtn + ", value is " + 
            getStandardDOLevel[0] + " " + getStandardDOLevel[1] + " " + getStandardDOLevel[2] + " " + getStandardDOLevel[3] + " " + 
            getStandardDOLevel[4] + " " + getStandardDOLevel[5] + " " + getStandardDOLevel[6] + " " + getStandardDOLevel[7]);

        robot.Sleep(2000);
        return 0;
    }