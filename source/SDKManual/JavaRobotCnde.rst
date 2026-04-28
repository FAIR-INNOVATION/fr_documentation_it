CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurare il Feedback di Stato del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configura il feedback di stato del robot
    * @param state Lista di enum degli stati del robot
    * @param period Periodo di feedback dello stato, intervallo 8-1000
    * @return Codice di errore, 0-normale, 4-errore parametro, 18-campo stato non esiste, 20-bytes totali superano 4K
    */
    public int SetRobotRealtimeStateConfig(List<RobotState> state, int period)
    
Aggiungere uno Stato del Robot alla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Aggiunge uno stato del robot alla lista di configurazione
    * @param state Enum dello stato del robot
    * @return Codice di errore, 0-normale, 17-stato già esistente, 18-campo stato non esiste, 20-supera 4K
    */
    public int AddRobotRealtimeState(RobotState state)
    
Eliminare uno Stato del Robot dalla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Elimina uno stato del robot dalla lista di configurazione
    * @param state Enum dello stato del robot
    * @return Codice di errore, 0-normale, 18-stato non esiste, 19-almeno uno stato deve rimanere
    */
    public int DeleteRobotRealtimeState(RobotState state)
        
Impostare il Periodo di Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il periodo di feedback di stato CNDE
    * @param period Periodo di feedback dello stato, intervallo 8-1000
    * @return Codice di errore, 0-normale, 4-errore parametro
    */
    public int SetRobotRealtimeStatePeriod(int period)
            
Ottenere l'Insieme Completo di Stati e il Periodo dell'Attuale Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
     * @brief Ottiene tutti gli insiemi di stati correnti e il periodo
     * @return Struttura risultato configurazione contenente lista stati e periodo
    */
    public StateConfigResult GetRobotRealtimeStateConfig()
                
Esempio di Codice per l'Utilizzo del Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Esempio di utilizzo dell'interfaccia di configurazione dello stato in tempo reale CNDE
    */
    public static void TestRealtimeStateConfig(Robot robot)
    {
        
        // 1. Creare la lista stati iniziale
        List<RobotState> stateList1 = new ArrayList<>();
        stateList1.add(RobotState.ProgramState);
        stateList1.add(RobotState.RobotState);
        stateList1.add(RobotState.JointCurPos);
        stateList1.add(RobotState.ToolCurPos);
        
        // 2. Prima chiamata a SetRobotRealtimeStateConfig per configurare stati e periodo
        int period1 = 100;  // Periodo 100ms
        int rtn = robot.SetRobotRealtimeStateConfig(stateList1, period1);
        System.out.printf("1. SetRobotRealtimeStateConfig (lista iniziale, periodo=%d) rtn: %d%n", period1, rtn);
        
        if (rtn == 0) {
            // 3. Aggiungere stato aggiuntivo
            rtn = robot.AddRobotRealtimeState(RobotState.RobotTime);
            System.out.printf("2. AddRobotRealtimeState (RobotTime) rtn: %d%n", rtn);
            
            // 4. Chiamare nuovamente SetRobotRealtimeStateConfig per riconfigurare (lista stati diversa)
            List<RobotState> stateList2 = new ArrayList<>();
            stateList2.add(RobotState.ProgramState);
            stateList2.add(RobotState.RobotState);
            stateList2.add(RobotState.MainCode);
            stateList2.add(RobotState.SubCode);
            stateList2.add(RobotState.JointCurPos);
            stateList2.add(RobotState.ToolCurPos);
            stateList2.add(RobotState.ActualJointTorque);
            
            int period2 = 50;  // Periodo 50ms
            rtn = robot.SetRobotRealtimeStateConfig(stateList2, period2);
            System.out.printf("3. SetRobotRealtimeStateConfig (lista aggiornata, periodo=%d) rtn: %d%n", period2, rtn);
            
            // 5. Modificare il periodo
            int newPeriod = 80;  // Periodo 80ms
            rtn = robot.SetRobotRealtimeStatePeriod(newPeriod);
            System.out.printf("4. SetRobotRealtimeStatePeriod (periodo=%d) rtn: %d%n", newPeriod, rtn);
            
            // 6. Ottenere la configurazione corrente e stampare
            Robot.StateConfigResult configResult = robot.GetRobotRealtimeStateConfig();
            System.out.println("5. GetRobotRealtimeStateConfig risultato:");
            System.out.printf("   - Periodo: %d ms%n", configResult.period);
            System.out.println("   - Stati Configurati:");
            for (int i = 0; i < configResult.stateList.size(); i++) {
                System.out.printf("     [%d] %s%n", i, configResult.stateList.get(i));
            }
            
            rtn = robot.RPC("192.168.58.2");
            if (rtn == 0) {
                System.out.println("connessione rpc riuscita");
            } else {
                System.out.println("connessione rpc fallita");
                return;
            }
            // Attendere la stabilizzazione della connessione CNDE
            System.out.println("Attesa della connessione CNDE...");
            while (robot.CNDEGetStateData() == null) {
                robot.Sleep(100);
            }
            System.out.println("Connessione CNDE stabilita, ricezione dati avviata...");

            // 7. Ciclo per leggere lo stato in tempo reale e verificare la configurazione
            System.out.println("6. Lettura stati in tempo reale...");
            while(true) {
                robot.Sleep(1000);
                // Ottenere i dati di stato tramite CNDE
                ROBOT_STATE_PKG pkg = robot.CNDEGetStateData();
                if (pkg == null) {
                    System.out.println("Dati stato nulli, connessione CNDE disconnessa, attesa riconnessione");
                    continue;  // Continuare il ciclo durante la disconnessione, in attesa di riconnessione
                }
                System.out.println("\n--- Tempo Robot ---");
                if (pkg.robotTime != null) {
                    System.out.println("robotTime: " + pkg.robotTime.year + "-" + pkg.robotTime.month + "-" + pkg.robotTime.day +
                            " " + pkg.robotTime.hour + ":" + pkg.robotTime.minute + ":" + pkg.robotTime.second +
                            "." + pkg.robotTime.millisecond);
                }

                System.out.println("   --- Informazioni Stato ---");
                System.out.printf("   program_state: %d%n", pkg.program_state);
                System.out.printf("   robot_state: %d%n", pkg.robot_state);
                System.out.printf("   main_code: %d%n", pkg.main_code);
                System.out.printf("   sub_code: %d%n", pkg.sub_code);
                System.out.println("   --- Posizioni Giunti (actual_joint_pos) ---");
                System.out.printf("   jt_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2]);
                System.out.printf("   jt_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
                System.out.println("   --- Posizioni TCP (actual_TCP_pos) ---");
                System.out.printf("   tl_cur_pos[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2]);
                System.out.printf("   tl_cur_pos[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
                System.out.println("   --- Coppie Giunti (actual_joint_torque) ---");
                System.out.printf("   jt_cur_tor[0-2]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2]);
                System.out.printf("   jt_cur_tor[3-5]: %.2f, %.2f, %.2f%n",
                    pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
                robot.Sleep(500);
            }
        } else {
            System.out.printf("SetRobotRealtimeStateConfig fallito con errore: %d%n", rtn);
        }
    }