CNDE
=================

.. toctree:: 
    :maxdepth: 5

Configurare la Lista Dati CNDE del Robot e il Periodo di Aggiornamento
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Configura la lista dati e il periodo di aggiornamento per il feedback dello stato in tempo reale del robot (sovrascrive la configurazione precedente)
    * @param [in] states Lista di enum di stato a cui sottoscriversi, l'ordine determina la disposizione nel pacchetto dati
    * @param [in] period Periodo di aggiornamento dati, unità millisecondi, intervallo di valori [8, 1000]
    * @return Restituisce 0 in caso di successo; restituisce un codice di errore negativo in caso di fallimento (es. ERR_STATE_INVALID, ERR_PARAM_VALUE, ecc.)
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> states, int period)

Aggiungere un Elemento di Stato all'Elenco di Feedback di Stato Esistente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Aggiunge un elemento di stato all'elenco di feedback di stato esistente
    * @param [in] state Valore enum dello stato da aggiungere
    * @return Restituisce 0 in caso di successo; restituisce un codice di errore negativo in caso di fallimento (es. ERR_STATE_ALREADY_EXISTS, ERR_STATE_INVALID, ecc.)
    */
    public int AddRobotRealtimeState(RobotState state)
    
Eliminare un Elemento di Stato dall'Elenco di Feedback di Stato Esistente
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Elimina un elemento di stato dall'elenco di feedback di stato esistente (deve rimanere almeno uno stato)
    * @param [in] state Valore enum dello stato da eliminare
    * @return Restituisce 0 in caso di successo; restituisce un codice di errore negativo in caso di fallimento (es. ERR_STATE_INVALID, ERR_NEED_AT_LEAST_ONE_STATE)
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Modificare Solo il Periodo di Aggiornamento del Feedback di Stato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

     /**
    * @brief Modifica solo il periodo di aggiornamento del feedback di stato senza modificare la lista degli stati
    * @param [in] period Nuovo periodo di aggiornamento, unità millisecondi, intervallo di valori [8, 1000]
    * @return Restituisce 0 in caso di successo; restituisce un codice di errore negativo in caso di fallimento (es. ERR_PARAM_VALUE)
    */
    public int SetRobotRealtimeStatePeriod(int period)
        
Ottenere la Lista di Feedback di Stato e il Periodo di Aggiornamento Correntemente Configurati
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief Ottiene la lista di feedback di stato e il periodo di aggiornamento correntemente configurati
    * @param [out] states Restituisce la lista di enum di stato attualmente sottoscritti
    * @param [out] period Restituisce il periodo di aggiornamento dati corrente, unità millisecondi
    * @return Restituisce 0 in caso di successo; restituisce un codice di errore negativo in caso di fallimento
    */
    public int GetRobotRealtimeStateConfig(out List<RobotState> states, out int period)

Esempio di Codice SDK Relativo alla Configurazione CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestRobotRealtimeStates()
    {
        // 1. Definire i campi di stato a cui sottoscriversi
        List<RobotState> requiredStates = new List<RobotState>
        {
            RobotState.JointCurPos,
            RobotState.ToolCurPos, 
            RobotState.JointDriverTemperature,
            RobotState.RobotTime,
        };

        // 2. Configurare il feedback di stato (periodo 8ms)
        int periodMs = 8;
        int ret = robot.SetRobotRealtimeStateConfig(requiredStates, periodMs);
        if (ret != 0)
        {
            Console.WriteLine($"Configurazione stato fallita, codice errore: {ret}");
            return;
        }
        Console.WriteLine($"Configurazione stato riuscita, {requiredStates.Count} campi, periodo {periodMs} ms");

        // Verificare se la configurazione è efficace
        List<RobotState> actualStates;
        int actualPeriod;
        robot.GetRobotRealtimeStateConfig(out actualStates, out actualPeriod);
        Console.WriteLine($"Numero di stati effettivamente attivi: {actualStates.Count}, periodo: {actualPeriod} ms");
        Thread.Sleep(3000);
        // 3. Stabilire la connessione RPC (internamente completa automaticamente l'handshake CNDE)
        robot.SetReconnectParam(true, 10, 1000);
        ret = robot.RPC("192.168.58.2");  // Modificare secondo l'IP effettivo del robot
        if (ret != 0)
        {
            Console.WriteLine($"Connessione RPC fallita, codice errore: {ret}");
            return;
        }
        // 4. Ciclo per leggere e stampare i dati di stato
        DateTime startTime = DateTime.Now;
        const int durationSeconds = 500;

        while ((DateTime.Now - startTime).TotalSeconds < durationSeconds)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            ret = robot.GetRobotRealTimeState(ref pkg);
            Console.WriteLine($"GetRobotRealTimeState: {ret}");

            //Posizioni dei giunti (gradi)
            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
                Console.WriteLine($"Posizioni giunti(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");

            //Posa TCP (mm /°)
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
                Console.WriteLine($"Posa TCP(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
    
            // Temperature dei giunti
            if (pkg.jointDriverTemperature != null && pkg.jointDriverTemperature.Length >= 6)
                Console.WriteLine($"Temperature giunti(°C): J1={pkg.jointDriverTemperature[0]:F2}, J2={pkg.jointDriverTemperature[1]:F2}, J3={pkg.jointDriverTemperature[2]:F2}, J4={pkg.jointDriverTemperature[3]:F2}, J5={pkg.jointDriverTemperature[4]:F2}, J6={pkg.jointDriverTemperature[5]:F2}");

            // Ora del robot
            Console.WriteLine($"Ora robot: {pkg.robotTime.year}-{pkg.robotTime.mouth:D2}-{pkg.robotTime.day:D2} {pkg.robotTime.hour:D2}:{pkg.robotTime.minute:D2}:{pkg.robotTime.second:D2}.{pkg.robotTime.millisecond:D3}");

            await Task.Delay(100);
        }

        // 5. Disconnettere
        robot.CloseRPC();
    }

Esempio di Codice SDK per Aggiunta/Eliminazione di Stato CNDE e Impostazione del Periodo di Comunicazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private async void TestAddDeleteCNDE()
    {
        List<RobotState> finalStates;
        int finalPeriod;
        // Configurazione iniziale: non richiedere alcuno stato (configurazione predefinita)
        List<RobotState> emptyStates = new List<RobotState>();
        int ret = robot.SetRobotRealtimeStateConfig(emptyStates, 20);

        robot.SetRobotRealtimeStatePeriod(10);
        // Eliminare due stati
        ret = robot.DeleteRobotRealtimeState(RobotState.JointCurPos);
        Console.WriteLine($"Eliminazione JointCurPos risultato: {ret}");
        ret = robot.DeleteRobotRealtimeState(RobotState.ToolCurPos);
        Console.WriteLine($"Eliminazione ToolCurPos risultato: {ret}");
        // Aggiungere uno stato
        ret = robot.AddRobotRealtimeState(RobotState.CollisionLevel);
        Console.WriteLine($"Aggiunta CollisionLevel risultato: {ret}");

        // Ottenere la lista di configurazione corrente e reinviare
        List<RobotState> currentStates;
        int currentPeriod;
        robot.GetRobotRealtimeStateConfig(out currentStates, out currentPeriod);
        Console.WriteLine($"Numero di stati di configurazione corrente: {currentStates.Count}");
        ret = robot.SetRobotRealtimeStateConfig(currentStates, currentPeriod);
        Console.WriteLine($"Applicazione nuova configurazione risultato: {ret}"); Console.WriteLine($"Configurazione iniziale risultato: {ret}");
        robot.GetRobotRealtimeStateConfig(out finalStates, out finalPeriod);
        Console.WriteLine($"Numero di stati di configurazione: {finalStates.Count}");
        foreach (var s in finalStates) Console.WriteLine($"  {s}");
        Console.WriteLine($"Periodo: {finalPeriod} ms");

        Thread.Sleep(1000);
        // Stabilire la connessione RPC (internamente si connette automaticamente al CNDE)
        robot.SetReconnectParam(true, 100, 1000);
        ret = robot.RPC("192.168.58.2");
        if (ret != 0)
        {
            Console.WriteLine($"Connessione RPC fallita: {ret}");
            return;
        }

        // Ciclo per stampare gli stati eliminati e aggiunti, gli stati eliminati vengono stampati come 0, gli stati aggiunti possono ottenere valori in tempo reale normalmente
        DateTime lastTime = DateTime.Now;
        int frameCount = 0;
        DateTime startTime = DateTime.Now;
        while ((DateTime.Now - startTime).TotalSeconds < 10)
        {
            ROBOT_STATE_PKG pkg = new ROBOT_STATE_PKG();
            robot.GetRobotRealTimeState(ref pkg);
            DateTime now = DateTime.Now;
            double interval = (now - lastTime).TotalMilliseconds;
            lastTime = now;
            frameCount++;

            if (pkg.jt_cur_pos != null && pkg.jt_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  Posizioni giunti(°): J1={pkg.jt_cur_pos[0]:F2}, J2={pkg.jt_cur_pos[1]:F2}, J3={pkg.jt_cur_pos[2]:F2}, J4={pkg.jt_cur_pos[3]:F2}, J5={pkg.jt_cur_pos[4]:F2}, J6={pkg.jt_cur_pos[5]:F2}");
            }
            if (pkg.tl_cur_pos != null && pkg.tl_cur_pos.Length >= 6)
            {
                Console.WriteLine($"  Posa TCP(mm/°): X={pkg.tl_cur_pos[0]:F2}, Y={pkg.tl_cur_pos[1]:F2}, Z={pkg.tl_cur_pos[2]:F2}, RX={pkg.tl_cur_pos[3]:F2}, RY={pkg.tl_cur_pos[4]:F2}, RZ={pkg.tl_cur_pos[5]:F2}");
            }
            // Livello di collisione
            if (pkg.collisionLevel != null && pkg.collisionLevel.Length >= 6)
                Console.WriteLine($"Livello collisione: J1={pkg.collisionLevel[0]}, J2={pkg.collisionLevel[1]}, J3={pkg.collisionLevel[2]}, J4={pkg.collisionLevel[3]}, J5={pkg.collisionLevel[4]}, J6={pkg.collisionLevel[5]}");

            await Task.Delay(50);
        }
        //Disconnettere
        robot.CloseRPC();
        Console.WriteLine("Test completato.");
    }