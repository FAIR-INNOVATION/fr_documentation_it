I/O del Robot
===================

.. toctree:: 
    :maxdepth: 5

Impostare le uscite digitali della scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta le uscite digitali della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~15]
    * @param  [in] status 0-spento, 1-acceso
    * @param  [in] smooth 0-non smoothing, 1-smoothing
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @return  Codice di errore
    */
    errno_t  SetDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Impostare le uscite digitali dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta le uscite digitali dell'utensile
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in] status 0-spento, 1-acceso
    * @param  [in] smooth 0-non smoothing, 1-smoothing
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @return  Codice di errore
    */
    errno_t  SetToolDO(int id, uint8_t status, uint8_t smooth, uint8_t block);

Impostare le uscite analogiche della scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta le uscite analogiche della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in] value percentuale valore corrente o tensione, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @return  Codice di errore
    */
    errno_t  SetAO(int id, float value, uint8_t block);

Impostare le uscite analogiche dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta le uscite analogiche dell'utensile
    * @param  [in] id  numero io, intervallo [0]
    * @param  [in] value percentuale valore corrente o tensione, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @return  Codice di errore
    */
    errno_t  SetToolAO(int id, float value, uint8_t block);

Esempio di codice per impostare uscite digitali e analogiche
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestAODO(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
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
             robot.SetAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         for (int i = 0; i < 100; i++)
         {
             robot.SetToolAO(0, i * 40.96, block);
             robot.Sleep(30);
         }
         robot.CloseRPC();
         return 0;
     }

Ottenere gli ingressi digitali della scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene gli ingressi digitali della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~15]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [out] result  0-livello basso, 1-livello alto
    * @return  Codice di errore
    */   
    errno_t  GetDI(int id, uint8_t block, uint8_t *result);

Ottenere gli ingressi digitali dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene gli ingressi digitali dell'utensile
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [out] result  0-livello basso, 1-livello alto
    * @return  Codice di errore
    */   
    errno_t  GetToolDI(int id, uint8_t block, uint8_t *result);

Ottenere gli ingressi analogici della scatola di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene gli ingressi analogici della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [out] result  percentuale valore corrente o tensione di ingresso, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @return  Codice di errore
    */   
    errno_t  GetAI(int id, uint8_t block, float *result); 

Ottenere gli ingressi analogici dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene gli ingressi analogici dell'utensile
    * @param  [in] id  numero io, intervallo [0]
    * @param  [in] block  0-bloccante, 1-non bloccante
    * @param  [out] result  percentuale valore corrente o tensione di ingresso, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @return  Codice di errore
    */   
    errno_t  GetToolAI(int id, uint8_t block, float *result);

Ottenere lo stato del pulsante di registrazione punti terminale del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene lo stato del pulsante di registrazione punti terminale del robot
     * @param [out] state stato pulsante, 0-premuto, 1-rilasciato
     * @return Codice di errore
     */
    errno_t  GetAxlePointRecordBtnState(uint8_t *state);

Ottenere lo stato delle uscite DO terminali del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene lo stato delle uscite DO terminali del robot
     * @param [out] do_state stato uscite DO, do0~do1 corrisponde a bit1~bit2, da bit0 inizio
     * @return Codice di errore
     */
    errno_t  GetToolDO(uint8_t *do_state);

Ottenere lo stato delle uscite DO del controller del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
     * @brief Ottiene lo stato delle uscite DO del controller del robot
     * @param [out] do_state_h stato uscite DO, co0~co7 corrisponde a bit0~bit7
     * @param [out] do_state_l stato uscite DO, do0~do7 corrisponde a bit0~bit7
     * @return Codice di errore
     */
    errno_t  GetDO(uint8_t *do_state_h, uint8_t *do_state_l);

Esempio di codice per ottenere stati DI/DO del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

     int TestGetDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         robot.GetDI(0, block, &di);
         printf("di0:%u\n", di);
         tool_di = robot.GetToolDI(1, block, &tool_di);
         printf("tool_di1:%u\n", tool_di);
         robot.GetAI(0, block, &ai);
         printf("ai0:%f\n", ai);
         tool_ai = robot.GetToolAI(0, block, &tool_ai);
         printf("tool_ai0:%f\n", tool_ai);
         uint8_t _button_state = 0;
         robot.GetAxlePointRecordBtnState(&_button_state);
         printf("_button_state is: %u\n", _button_state);
         uint8_t tool_do_state = 0;
         robot.GetToolDO(&tool_do_state);
         printf("tool DO state is: %u\n", tool_do_state);
         uint8_t do_state_h = 0;
         uint8_t do_state_l = 0;
         robot.GetDO(&do_state_h, &do_state_l);
         printf("DO state high is: %u \n DO state low is: %u\n", do_state_h, do_state_l);
         robot.CloseRPC();
         return 0;
     }

Attendere ingresso digitale della scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Attende ingresso digitale della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~15]
    * @param  [in]  status 0-spento, 1-acceso
    * @param  [in]  max_time  tempo massimo attesa, unità ms
    * @param  [in]  opt  strategia dopo timeout, 0-programma si ferma e segnala timeout, 1-ignora timeout programma continua, 2-attesa continua
    * @return  Codice di errore
    */
    errno_t  WaitDI(int id, uint8_t status, int max_time, int opt);

Attendere ingressi digitali multipli della scatola di controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Attende ingressi digitali multipli della scatola di controllo
    * @param  [in] mode 0-AND multipli, 1-OR multipli
    * @param  [in] id  numero io, bit0~bit7 corrisponde DI0~DI7, bit8~bit15 corrisponde CI0~CI7
    * @param  [in]  status 0-spento, 1-acceso
    * @param  [in]  max_time  tempo massimo attesa, unità ms
    * @param  [in]  opt  strategia dopo timeout, 0-programma si ferma e segnala timeout, 1-ignora timeout programma continua, 2-attesa continua
    * @return  Codice di errore
    */
    errno_t  WaitMultiDI(int mode, int id, uint8_t status, int max_time, int opt);

Attendere ingresso digitale dell'utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Attende ingresso digitale dell'utensile
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in]  status 0-spento, 1-acceso
    * @param  [in]  max_time  tempo massimo attesa, unità ms
    * @param  [in]  opt  strategia dopo timeout, 0-programma si ferma e segnala timeout, 1-ignora timeout programma continua, 2-attesa continua
    * @return  Codice di errore
    */
    errno_t  WaitToolDI(int id, uint8_t status, int max_time, int opt);

Attendere ingresso analogico della scatola di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Attende ingresso analogico della scatola di controllo
    * @param  [in] id  numero io, intervallo [0~1]
    * @param  [in]  sign 0-maggiore di, 1-minore di
    * @param  [in]  value percentuale valore corrente o tensione di ingresso, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @param  [in]  max_time  tempo massimo attesa, unità ms
    * @param  [in]  opt  strategia dopo timeout, 0-programma si ferma e segnala timeout, 1-ignora timeout programma continua, 2-attesa continua
    * @return  Codice di errore
    */
    errno_t  WaitAI(int id, int sign, float value, int max_time, int opt);  

Attendere ingresso analogico dell'utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Attende ingresso analogico dell'utensile
    * @param  [in] id  numero io, intervallo [0]
    * @param  [in]  sign 0-maggiore di, 1-minore di
    * @param  [in]  value percentuale valore corrente o tensione di ingresso, intervallo [0~100] corrispondente a valore corrente [0~20mA] o tensione [0~10V]
    * @param  [in]  max_time  tempo massimo attesa, unità ms
    * @param  [in]  opt  strategia dopo timeout, 0-programma si ferma e segnala timeout, 1-ignora timeout programma continua, 2-attesa continua
    * @return  Codice di errore
    */
    errno_t  WaitToolAI(int id, int sign, float value, int max_time, int opt); 

Esempio di codice per attendere segnali di ingresso digitali/analogici della scatola di controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionchanged:: C++SDK-v2.1.2.0
    
.. code-block:: c++
    :linenos:

     int TestWaitDIAI(void)
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
         uint8_t status = 1;
         uint8_t smooth = 0;
         uint8_t block = 0;
         uint8_t di = 0, tool_di = 0;
         float ai = 0.0, tool_ai = 0.0;
         float value = 0.0;
         rtn = robot.WaitDI(0, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitMultiDI(1, 3, 3, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolDI(1, 1, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.WaitToolAI(0, 0, 50, 1000, 1);
         cout << "WaitDI over; rtn is: " << rtn << endl;
         robot.CloseRPC();
         return 0;
     }

Imposta se Resettare l'Uscita DO del Box di Controllo dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita DO del box di controllo dopo stop/pausa
    * @param [in] resetFlag 0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return Codice di errore
    */
    errno_t SetOutputResetCtlBoxDO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita AO del Box di Controllo dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita AO del box di controllo dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return Codice di errore
    */
    errno_t SetOutputResetCtlBoxAO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita DO dell'Utensile Terminale dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita DO dell'utensile terminale dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return Codice di errore
    */
    errno_t SetOutputResetAxleDO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita AO dell'Utensile Terminale dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita AO dell'utensile terminale dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return  Codice di errore
    */
    errno_t SetOutputResetAxleAO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita DO Estensione dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita DO di estensione dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return  Codice di errore
    */
    errno_t SetOutputResetExtDO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita AO Estensione dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita AO di estensione dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return  Codice di errore
    */
    errno_t SetOutputResetExtAO(int resetFlag, int reloadFlag = 0);

Imposta se Resettare l'Uscita SmartTool dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta se resettare l'uscita SmartTool dopo stop/pausa
    * @param [in] resetFlag  0-non resettare; 1-resetta
    * @param [in] reloadFlag Se ricaricare dopo la ripresa dalla pausa, 0-non caricare; 1-carica
    * @return  Codice di errore
    */
    errno_t SetOutputResetSmartToolDO(int resetFlag, int reloadFlag = 0);

Esempio di Codice per Impostare il Reset dell'Uscita del Programma LUA dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.5.0
    
.. code-block:: c++
    :linenos:

    int TestDOReset(void)
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
    for (int i = 0; i < 16; i++)
    {
        robot.SetDO(i, 1, 0, 0);
        robot.Sleep(200);
    }
    int resetFlag = 0;
    int resumeReloadFlag = 0;
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag);
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
    return 0;
    }

Impostare le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    36-Entra in movimento a velocità di sicurezza;37-Blocco trascinamento ad anello di corrente;38-Blocco assistito da sensore di forza
    * @return Codice di errore
    */
    errno_t SetDIConfig(int config[8]);

Ottenere le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    36-Entra in movimento a velocità di sicurezza;37-Blocco trascinamento ad anello di corrente;38-Blocco assistito da sensore di forza
    201-Segnale di ingresso arresto di emergenza esterno 1-doppio canale; 202-Segnale di ingresso arresto di emergenza esterno 2-doppio canale; 203-Modalità ridotta di livello 1-doppio canale;
    204-Modalità ridotta di livello 2-doppio canale; 205-Modalità ridotta di livello 3-doppio canale; 206-Arresto normale-doppio canale; 207-Muro di sicurezza 1-doppio canale; 208-Muro di sicurezza 2-doppio canale;
    209-Muro di sicurezza 3-doppio canale; 210-Muro di sicurezza 4-doppio canale; 211-Muro di sicurezza 5-doppio canale; 212-Muro di sicurezza 6-doppio canale; 213-Muro di sicurezza 7-doppio canale;
    214-Muro di sicurezza 8-doppio canale; 215-Ripristino arresto di sicurezza-doppio canale;
    * @return Codice di errore
    */
    errno_t GetDIConfig(int config[8]);

Impostare le Funzioni delle Porte CO Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetDOConfig(int config[8]);

Ottenere le Funzioni delle Porte CO Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    201-Segnale di uscita arresto di emergenza 1-doppio canale; 202-Segnale di uscita arresto di emergenza 2-doppio canale; 203-Uscita stato sicurezza-doppio canale; 204-Uscita stato arresto protettivo-doppio canale; 205-Robot in movimento-doppio canale;
	206-Robot in modalità ridotta-doppio canale; 207-Robot in modalità non ridotta-doppio canale;
    * @return Codice di errore
    */
    errno_t GetDOConfig(int config[8]);

Impostare le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t SetToolDIConfig(int config[2]);

Ottenere le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
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
    errno_t GetToolDIConfig(int config[2]);
    
Impostare lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile del box di controllo
    * @param [in] config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t SetDIConfigLevel(int config[8]);
        
Ottenere lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile del box di controllo
    * @param [out] config Stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t GetDIConfigLevel(int config[8]);
        
Impostare lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta lo stato attivo CO configurabile del box di controllo
    * @param [in] config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t SetDOConfigLevel(int config[8]);

Ottenere lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CO configurabile del box di controllo
    * @param [out] config Stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t GetDOConfigLevel(int config[8]);
    
Impostare lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta lo stato attivo CI configurabile dell'end-effector
    * @param [in] config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t SetToolDIConfigLevel(int config[2]);
    
Ottenere lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato attivo CI configurabile dell'end-effector
    * @param [out] config Stato attivo porte CI0-CI1; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t GetToolDIConfigLevel(int config[2]);
    
Impostare lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta lo stato attivo DI standard del box di controllo
    * @param [in] config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t SetStandardDILevel(int config[8]);
    
Ottenere lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DI standard del box di controllo
    * @param [out] config Stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t GetStandardDILevel(int config[8]);

Impostare lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Imposta lo stato attivo DO standard del box di controllo
    * @param [in] config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t SetStandardDOLevel(int config[8]);
    
Ottenere lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene lo stato attivo DO standard del box di controllo
    * @param [out] config Stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso
    * @return Codice di errore
    */
    errno_t GetStandardDOLevel(int config[8]);
        
Esempio di Codice di Configurazione IO del Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    
.. code-block:: c++
    :linenos:

    int TestIOConfig()
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
        int setDIConfig[8] = { 1, 2, 3, 4, 5, 6, 7, 8 };
        int getDIConfig[8] = { 0 };
        rtn = robot.SetDIConfig(setDIConfig);
        printf("SetDIConfig rtn is %d\n", rtn);
        rtn = robot.GetDIConfig(getDIConfig);
        printf("GetDIConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn, 
            getDIConfig[0], getDIConfig[1], getDIConfig[2], getDIConfig[3], getDIConfig[4], getDIConfig[5], getDIConfig[6], getDIConfig[7]);
        int setDOConfig[8] = { 9, 10, 11, 12, 13, 14, 15, 16 };
        int getDOConfig[8] = { 0 };
        rtn = robot.SetDOConfig(setDOConfig);
        printf("SetDOConfig rtn is %d\n", rtn);
        rtn = robot.GetDOConfig(getDOConfig);
        printf("GetDOConfig rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfig[0], getDOConfig[1], getDOConfig[2], getDOConfig[3], getDOConfig[4], getDOConfig[5], getDOConfig[6], getDOConfig[7]);
        int setToolDIConfig[2] = { 17, 18 };
        int getToolDIConfig[2] = { 0 };
        rtn = robot.SetToolDIConfig(setToolDIConfig);
        printf("SetToolDIConfig rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfig(getToolDIConfig);
        printf("GetToolDIConfig rtn is %d, value is %d %d \n", rtn, getToolDIConfig[0], getToolDIConfig[1]);
        int setDIConfigLevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getDIConfigLevel[8] = { 0 };
        rtn = robot.SetDIConfigLevel(setDIConfigLevel);
        printf("SetDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDIConfigLevel(getDIConfigLevel);
        printf("GetDIConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDIConfigLevel[0], getDIConfigLevel[1], getDIConfigLevel[2], getDIConfigLevel[3], getDIConfigLevel[4], getDIConfigLevel[5], getDIConfigLevel[6], getDIConfigLevel[7]);
        int setDOConfigLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getDOConfigLevel[8] = { 0 };
        rtn = robot.SetDOConfigLevel(setDOConfigLevel);
        printf("SetDOConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetDOConfigLevel(getDOConfigLevel);
        printf("GetDOConfigLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getDOConfigLevel[0], getDOConfigLevel[1], getDOConfigLevel[2], getDOConfigLevel[3], getDOConfigLevel[4], getDOConfigLevel[5], getDOConfigLevel[6], getDOConfigLevel[7]);
        int setToolDIConfigLevel[2] = { 1, 0 };
        int getToolDIConfigLevel[2] = { 0 };
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel);
        printf("SetToolDIConfigLevel rtn is %d\n", rtn);
        rtn = robot.GetToolDIConfigLevel(getToolDIConfigLevel);
        printf("GetToolDIConfigLevel rtn is %d, value is %d %d \n", rtn, getToolDIConfigLevel[0], getToolDIConfigLevel[1]);
        int setStandardDILevel[8] = { 1, 1, 1, 1, 0, 0, 0, 0 };
        int getStandardDILevel[8] = { 0 };
        rtn = robot.SetStandardDILevel(setStandardDILevel);
        printf("SetStandardDILevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDILevel(getStandardDILevel);
        printf("GetStandardDILevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDILevel[0], getStandardDILevel[1], getStandardDILevel[2], getStandardDILevel[3], getStandardDILevel[4], getStandardDILevel[5], getStandardDILevel[6], getStandardDILevel[7]);
        int setStandardDOLevel[8] = { 0, 0, 0, 0, 1, 1, 1, 1 };
        int getStandardDOLevel[8] = { 0 };
        rtn = robot.SetStandardDOLevel(setStandardDOLevel);
        printf("SetStandardDOLevel rtn is %d\n", rtn);
        rtn = robot.GetStandardDOLevel(getStandardDOLevel);
        printf("GetStandsrdDOLevel rtn is %d, value is %d %d %d %d %d %d %d %d \n", rtn,
            getStandardDOLevel[0], getStandardDOLevel[1], getStandardDOLevel[2], getStandardDOLevel[3], getStandardDOLevel[4], getStandardDOLevel[5], getStandardDOLevel[6], getStandardDOLevel[7]);
        robot.Sleep(2000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }