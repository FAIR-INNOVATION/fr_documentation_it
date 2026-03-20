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
    robot.ProgramLoad("/fruser/test.lua");
    robot.ProgramRun();
    robot.Sleep(2000);
    robot.PauseMotion();
    robot.Sleep(2000);
    robot.ResumeMotion();
    robot.Sleep(2000);
    robot.CloseRPC();
    return 0;
    }