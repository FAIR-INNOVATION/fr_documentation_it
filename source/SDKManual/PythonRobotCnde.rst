CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurare il Feedback di Stato CNDE del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStateConfig(states: List[RobotState], period: int = 500) -> int:``"
    "Descrizione", "Imposta la configurazione predefinita CNDE (da chiamare prima della connessione RPC)"
    "Parametri Obbligatori", "
    - ``states``: Lista di enum RobotState
    - ``period``: Periodo dati (ms), intervallo 8-1000, default 8ms
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode"

Aggiungere uno Stato del Robot alla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AddRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Descrizione", "Aggiunge la lista stati CNDE basata sulla configurazione esistente (supporta manutenzione dinamica e isolamento IP)"
    "Parametri Obbligatori", "
    - ``states``: Lista di enum RobotState, stati da aggiungere
    - ``ip``: Opzionale, specifica l'IP del robot (per configurazione isolata multi-robot; se non fornito, modifica la configurazione globale)
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode"

Eliminare uno Stato del Robot dalla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``DeleteRobotRealtimeState(states: List[RobotState], ip: str = None) -> int:``"
    "Descrizione", "Elimina la lista stati CNDE basata sulla configurazione esistente (supporta manutenzione dinamica e isolamento IP)"
    "Parametri Obbligatori", "
    - ``states``: Lista di enum RobotState, stati da eliminare
    - ``ip``: Opzionale, specifica l'IP del robot (per configurazione isolata multi-robot; se non fornito, modifica la configurazione globale)
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode"

Impostare il Periodo di Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotRealtimeStatePeriod(period: int, ip: str = None) -> int:``"
    "Descrizione", "Imposta il periodo di feedback di stato CNDE (supporta configurazione globale o isolata per IP)"
    "Parametri Obbligatori", "
    - ``period``: Periodo dati (ms), intervallo 8-1000
    - ``ip``: Opzionale, specifica l'IP del robot (se non fornito, modifica la configurazione globale)
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode"

Ottenere l'Insieme Completo di Stati dell'Attuale Feedback di Stato CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CNDEGetConfig(self) -> tuple:``"
    "Descrizione", "Ottiene tutti gli insiemi di stati correnti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice di errore Successo-0 Fallimento-errcode Struttura risultato configurazione contenente lista stati"

Esempio di Codice per l'Utilizzo del Feedback di Stato CNDE
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos: 

    from fairino import Robot
    from fairino.Robot import RobotState, SetRobotRealtimeStateConfig, DEFAULT_CNDE_STATES, AddRobotRealtimeState, DeleteRobotRealtimeState, SetRobotRealtimeStatePeriod
    import time

    # ==================== Parametri di Configurazione Globali ====================
    ROBOT_IP = '192.168.58.2'       # Indirizzo IP del robot
    # ========== Test1: Test di Configurazione CNDE e Acquisizione Dati =============
    # Passaggi del test:
    # 1. Impostare configurazione CNDE (JointCurPos, ToolCurPos, periodo 20ms)
    # 2. Stabilire connessione RPC
    # 3. Stampare i dati delle posizioni dei giunti e della posa TCP del robot
    # 4. Ottenere timestamp e verificare il periodo
    # 5. Modificare configurazione (RobotMode, RbtEnableState, periodo 10ms)
    # 6. Verificare che la nuova configurazione sia attiva

    def test1_cnde_config_and_data():
        """Test1: Test di configurazione CNDE e acquisizione dati - verifica delle impostazioni di configurazione e della tempestività dei dati"""
        print_separator("Test1: Test di configurazione CNDE e acquisizione dati")

        # ===== Passo 1: Impostare configurazione CNDE (JointCurPos, ToolCurPos, 20ms) =====
        print("\n[Passo 1] Impostazione configurazione CNDE...")
        print("  Campi di configurazione: JointCurPos, ToolCurPos")
        print("  Periodo di feedback: 20ms")

        custom_states = [
            RobotState.JointCurPos,   # Posizione corrente del giunto
            RobotState.ToolCurPos,    # Posizione corrente dell'utensile (TCP)
        ]

        rtn = SetRobotRealtimeStateConfig(custom_states, 20)
        if rtn != 0:
            print(f"✗ Impostazione configurazione fallita, codice errore: {rtn}")
            return None
        print("✓ Configurazione CNDE impostata con successo")

        # ===== Passo 2: Stabilire connessione RPC =====
        print(f"\n[Passo 2] Stabilizzazione connessione RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Attesa per connessione e ricezione dati

        # Verifica configurazione
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Connessione riuscita, configurazione corrente: {len(states)} campi, periodo {period}ms")
        else:
            print("✗ Impossibile ottenere la configurazione CNDE")
            return robot

        # ===== Passo 3: Stampare posizioni giunti e posa TCP del robot =====
        print("\n[Passo 3] Stampaggio posizioni giunti e posa TCP del robot...")
        print("  (Suggerimento: Trascinare il robot per osservare le variazioni dei dati)")
        print("  Premere Ctrl+C per interrompere la stampa dei dati")
        print("  (Utilizzare Wireshark per catturare pacchetti e verificare il periodo dati effettivo)\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Raccolta di 100 campioni
                pkg = robot.robot_state_pkg

                # Stampa ogni 10 frame
                if sample_count % 10 == 0:
                    print(f"--- Campione #{sample_count} ---")
                    print(f"  Posizioni giunti (deg): [{', '.join([f'{x:.3f}' for x in pkg.jt_cur_pos])}]")
                    print(f"  Posa TCP (mm/deg): [{', '.join([f'{x:.3f}' for x in pkg.tl_cur_pos])}]")
                    print(f"  Conteggio frame corrente: {pkg.frame_cnt}")
                    print()

                sample_count += 1
                time.sleep(0.02)  # 20ms

        except KeyboardInterrupt:
            print("\n  Stampa dati interrotta dall'utente")

        # Chiudi connessione
        robot.CloseRPC()
        time.sleep(1)

        # ===== Passo 4: Modificare configurazione e verificare =====
        print("\n[Passo 4] Modifica configurazione CNDE...")
        print("  Nuovi campi di configurazione: RobotMode, RbtEnableState")
        print("  Nuovo periodo di feedback: 10ms")

        new_states = [
            RobotState.RobotMode,
            RobotState.RbtEnableState,
        ]

        # Imposta nuova configurazione
        rtn = SetRobotRealtimeStateConfig(new_states, 10)
        if rtn != 0:
            print(f"✗ Impostazione nuova configurazione fallita, codice errore: {rtn}")
            return robot
        print("✓ Nuova configurazione impostata con successo")

        # Riconnetti
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Verifica nuova configurazione
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Configurazione corrente: {[s.name for s in states]}")
            print(f"✓ Periodo corrente: {period}ms")

            if period == 10:
                print("✓ Verifica modifica configurazione superata (periodo cambiato a 10ms)")
            else:
                print(f"⚠ Periodo non attivo (previsto 10ms, effettivo {period}ms)")

            # Stampa nuovi dati
            pkg = robot.robot_state_pkg
            print(f"\n[Nuovi Dati di Configurazione]")
            print(f"  robot_mode: {pkg.robot_mode}")
            print(f"  rbtEnableState: {pkg.rbtEnableState}")
        else:
            print("✗ Impossibile ottenere la nuova configurazione")

        print("\n✓ Test1 completato")
        return robot


    if __name__ == "__main__":
        test1_cnde_config_and_data()


    # ======== Test2: Test Aggiunta/Eliminazione Campi di Stato ====================
    # Funzione: Testare AddRobotRealtimeState() e DeleteRobotRealtimeState()
    # Passaggi del test:
    #   1. Utilizzare AddRobotRealtimeState() per aggiungere SpeedScaleManual e SpeedScaleAuto
    #   2. Connettersi al robot, stampare la velocità globale in modalità manuale/automatica
    #   3. Modificare la velocità globale in WebApp e osservare le variazioni dei dati SDK
    #   4. Utilizzare DeleteRobotRealtimeState() per eliminare i campi aggiunti
    #   5. Riconnettersi e verificare che i valori di velocità siano 0 (campi non più aggiornati)


    def test2_add_delete_state():
        """Test2: Test aggiunta/eliminazione campi di stato - verifica dell'aggiunta e dell'eliminazione dinamica degli stati CNDE"""
        print_separator("Test2: Test aggiunta/eliminazione campi di stato")

        # ===== Passo 1: Aggiungere i campi SpeedScaleManual e SpeedScaleAuto =====
        print("\n[Passo 1] Utilizzo di AddRobotRealtimeState() per aggiungere i campi scala velocità...")
        print("  Campi aggiunti: SpeedScaleManual, SpeedScaleAuto")

        rtn = AddRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Aggiunta campi fallita, codice errore: {rtn}")
            return None
        print("✓ Campi aggiunti con successo")

        # ===== Passo 2: Stabilire connessione RPC e stampare velocità =====
        print(f"\n[Passo 2] Stabilizzazione connessione RPC ({ROBOT_IP})...")
        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)  # Attesa per connessione e ricezione dati

        # Verifica configurazione
        config = robot.CNDEGetConfig()
        if config:
            states, period = config
            print(f"✓ Connessione riuscita, configurazione corrente: {len(states)} campi")
            # Controlla se i campi aggiunti sono inclusi
            has_manual = RobotState.SpeedScaleManual in states
            has_auto = RobotState.SpeedScaleAuto in states
            if has_manual and has_auto:
                print("✓ Verifica configurazione superata: SpeedScaleManual e SpeedScaleAuto sono stati aggiunti")
            else:
                print(f"⚠ Avviso verifica configurazione: Manual={has_manual}, Auto={has_auto}")
        else:
            print("✗ Impossibile ottenere la configurazione CNDE")

        # Stampa dati velocità
        print("\n[Dati Velocità Correnti] (Modificare la velocità globale in WebApp per osservare le variazioni)")
        print("  Suggerimento: Abilitare il robot trascinandolo e commutare tra modalità manuale/automatica per osservare i valori di velocità")
        print("  Premere Ctrl+C per interrompere la stampa dati\n")

        sample_count = 0
        try:
            while sample_count < 100:  # Raccolta di 100 campioni (circa 10 secondi a intervallo di 100ms)
                pkg = robot.robot_state_pkg
                print(f"  [{sample_count:3d}] SpeedScaleManual: {pkg.speedScaleManual:.2f}, "
                    f"SpeedScaleAuto: {pkg.speedScaleAuto:.2f}, "
                    f"Mode: {pkg.robot_mode}")
                sample_count += 1
                time.sleep(0.1)  # Intervallo 100ms
        except KeyboardInterrupt:
            print("\n  Stampa dati interrotta dall'utente")

        print(f"\n✓ Raccolta dati completata, totale {sample_count} campioni")

        # ===== Passo 3: Disconnettere =====
        print("\n[Passo 3] Disconnessione della connessione corrente...")
        robot.CloseRPC()
        time.sleep(1.0)  # Attesa che CNDE si chiuda completamente

        # ===== Passo 4: Eliminare i campi aggiunti =====
        print("\n[Passo 4] Utilizzo di DeleteRobotRealtimeState() per eliminare i campi scala velocità...")
        rtn = DeleteRobotRealtimeState([
            RobotState.SpeedScaleManual,
            RobotState.SpeedScaleAuto,
        ])

        if rtn != 0:
            print(f"✗ Eliminazione campi fallita, codice errore: {rtn}")
            return robot
        print("✓ Campi eliminati con successo")

        # ===== Passo 5: Riconnettersi e verificare che i valori dei campi siano 0 =====
        print(f"\n[Passo 5] Riconnessione e verifica dei valori dei campi dopo l'eliminazione...")

        robot = Robot.RPC(ROBOT_IP)
        time.sleep(0.5)

        # Leggi i valori di velocità
        pkg = robot.robot_state_pkg
        manual_speed = pkg.speedScaleManual
        auto_speed = pkg.speedScaleAuto

        print(f"\n  SpeedScaleManual dopo eliminazione: {manual_speed:.2f}")
        print(f"  SpeedScaleAuto dopo eliminazione: {auto_speed:.2f}")

        # Verifica se sono 0
        if manual_speed == 0 and auto_speed == 0:
            print("\n✓ Test2 verifica superata: i valori di velocità sono 0 dopo l'eliminazione dei campi")
        else:
            print(f"\n⚠ Test2 avviso: i valori di velocità non sono zero dopo l'eliminazione dei campi")

        print("\n✓ Test2 completato")
        return robot

    if __name__ == "__main__":
        test2_add_delete_state()