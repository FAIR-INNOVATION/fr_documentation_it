Introduzione a CNDE
===========================

Il protocollo configurabile di scambio dati di rete per robot collaborativi (di seguito CNDE) è un metodo tramite il quale un client controlla il robot e ottiene il suo stato di feedback attraverso la comunicazione UDP.

La Tabella 1-1 mostra l'insieme di tutti gli stati del robot ottenibili tramite CNDE. Il client può selezionare qualsiasi numero di stati necessari dalla tabella e far sì che il robot fornisca il feedback degli stati in base al periodo di feedback impostato.

Allo stesso modo, il client può selezionare le combinazioni di funzioni di controllo del robot necessarie dalla Tabella 1-2 per eseguire operazioni di controllo del robot. I dati di comunicazione tra il client e il CNDE del robot devono rispettare il formato di frame specificato. Le porte di comunicazione CNDE del robot sono 20005 e 20006. La porta 20005 è utilizzata per la comunicazione TCP, mentre la porta 20006 è utilizzata per la comunicazione UDP.

L'utilizzo della funzione CNDE del robot comprende principalmente i seguenti quattro passaggi:

① Configurazione del contenuto dei dati di input e output: Il client invia un comando di configurazione di input e output al robot, in cui il contenuto del comando include nomi di funzioni di controllo o stato come "std_DI_box, cfg_DI_box, motion_queue_len", ecc. Dopo aver registrato e riconosciuto questi nomi, il robot risponde al client con i tipi di dati corrispondenti, ad esempio "UINT8, UINT8, INT32", indicando che la configurazione è riuscita.

② Avvio dell'output dei dati CNDE del robot: Il client invia un comando di avvio dell'output dei dati CNDE al robot, e il robot inizia a inviare i dati di stato al client via UDP sotto forma di array di byte (modalità little-endian) secondo il periodo configurato.

③ Analisi dei dati di stato del robot: Il client riceve ciclicamente i dati di stato inviati dal robot e li analizza in base ai tipi di dati restituiti durante la configurazione dell'output e alla lunghezza in byte corrispondente a ciascun tipo di dati nella Tabella 1-3, ottenendo i valori effettivi di ciascuno stato. L'output dei dati CNDE del robot supporta un massimo di 4096 byte, e il periodo di output CNDE configurabile è compreso tra 1 e 200 ms.

④ Invio dei dati di controllo al robot: Il client impacchetta i dati di controllo in base ai tipi di dati restituiti durante la configurazione dell'input e alla lunghezza in byte corrispondente a ciascun tipo di dati nella Tabella 1-3, e li invia al robot tramite comunicazione UDP. Il robot, dopo aver ricevuto i dati di controllo, li analizza e esegue le operazioni di controllo. L'input CNDE del robot supporta 256 ricette. Il client può configurare prima più ricette di input secondo necessità e, quando invia dati di input al robot, deve specificare il numero della ricetta corrispondente ai dati correnti.

.. centered:: Tabella 1-1 Funzioni di configurazione dell'output del robot

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Tipo di dato**
     - **Descrizione**

   * - std_DI_box
     - UINT8
     - Input standard DI del quadro di controllo (bit0 ~ bit7 rappresentano DI0 ~ DI7)

   * - cfg_DI_box
     - UINT8
     - Input CI configurabile del quadro di controllo (bit0 ~ bit7 rappresentano CI0 ~ CI7)

   * - cfg_DI_tool
     - UINT8
     - Input DI dello strumento configurabile del quadro di controllo (bit0 ~ bit2 rappresentano toolDI0 ~ toolDI1)

   * - std_AI0_box
     - DOUBLE
     - Input analogico AI0 del quadro di controllo (0 ~ 4095)

   * - std_AI1_box
     - DOUBLE
     - Input analogico AI1 del quadro di controllo (0 ~ 4095)

   * - std_AI_tool
     - DOUBLE
     - Input analogico dello strumento terminale tool_AI0 (0 ~ 4095)

   * - run_up_time
     - DOUBLE
     - Statistica del tempo di accensione del robot (s)

   * - target_joint_pos
     - DOUBLE_6
     - Posizione target giunto 1-6 (°)

   * - target_joint_vel
     - DOUBLE_6
     - Velocità target giunto 1-6 (°/s)

   * - target_joint_acc
     - DOUBLE_6
     - Accelerazione target giunto 1-6 (°/s²)

   * - target_joint_current
     - DOUBLE_6
     - Corrente target giunto 1-6 (A)

   * - target_joint_torque
     - DOUBLE_6
     - Coppia target giunto 1-6 (Nm)

   * - actual_joint_pos
     - DOUBLE_6
     - Posizione corrente giunto 1-6 (°)

   * - actual_joint_vel
     - DOUBLE_6
     - Velocità corrente giunto 1-6 (°/s)

   * - actual_joint_current
     - DOUBLE_6
     - Corrente corrente giunto 1-6 (A)

   * - actual_joint_torque
     - DOUBLE_6
     - Coppia corrente giunto 1-6 (Nm)

   * - actual_TCP_pos
     - DOUBLE_6
     - Posizione corrente strumento DKR (mm)

   * - actual_TCP_vel
     - DOUBLE_6
     - Velocità corrente strumento DKR (mm/s)

   * - actual_TCP_force
     - DOUBLE_6
     - Forza risultante strumento DKR (N)

   * - target_TCP_pos
     - DOUBLE_6
     - Posizione target strumento DKR (mm)

   * - target_TCP_vel
     - DOUBLE_6
     - Velocità target strumento DKR (mm/s)

   * - std_DO_box
     - UINT8
     - Output standard DO del quadro di controllo (bit0 ~ bit7 rappresentano DO0 ~ DO7)

   * - cfg_DO_box
     - UINT8
     - Output CO configurabile del quadro di controllo (bit0 ~ bit7 rappresentano CO0 ~ CO7)

   * - cfg_DO_tool
     - UINT8
     - Output standard DO dello strumento del quadro di controllo (bit0 ~ bit1 rappresentano toolDO0 ~ toolDO1)

   * - std_AO0_box
     - DOUBLE
     - Output analogico AO0 del quadro di controllo (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Output analogico AO1 del quadro di controllo (0.0 ~ 4095.0)

   * - std_AO_tool
     - DOUBLE
     - Output analogico AO1 dello strumento (0.0 ~ 4095.0)

   * - robot_mode
     - UINT8
     - Modalità robot (0-automatico; 1-manuale)

   * - collision_level
     - UINT8_6
     - Livello di collisione giunto 1-6 (1 ~ 10)

   * - speed_scaling_man
     - DOUBLE
     - Percentuale velocità modalità manuale (0 ~ 100)

   * - speed_scaling_auto
     - DOUBLE
     - Percentuale velocità modalità automatica (0 ~ 100)

   * - program_state
     - UINT8
     - Stato esecuzione programma robot (1-fermo; 2-in movimento; 3-in pausa; 4-trascinamento)

   * - line_number
     - INT32
     - Numero riga programma corrente in esecuzione

   * - payload
     - DOUBLE
     - Massa del carico (kg)

   * - pay_cog
     - DOUBLE_3
     - Centro di massa del carico (x,y,z) (mm)

   * - motion_queue_len
     - INT32
     - Lunghezza attuale coda movimento
   
   * - ft_sensor_data
     - DOUBLE_6
     - Dati grezzi sensore di forza

   * - main_code
     - INT32
     - Codice errore principale

   * - sub_code
     - INT32
     - Codice errore secondario

   * - emergency_stop
     - UINT8
     - Stato arresto di emergenza

   * - motion_done
     - INT32
     - Stato completamento movimento

   * - timestamp_us
     - UINT64
     - Tempo di sistema robot (µs)

   * - output_BIT_reg_8xX
     - UINT8_X
     - Registro di output robot tipo BIT (8xX indica il numero di registri, se servono 16 registri di output tipo BIT, il nome effettivo è: "output_BIT_reg_8x2". Il robot supporta massimo 128 registri di output tipo BIT)

   * - output_INT_reg_X
     - INT32_X
     - Registro di output robot tipo INT (X indica il numero di registri, se servono 16 registri di output tipo INT, il nome effettivo è: "output_INT_reg_16". Il robot supporta massimo 64 registri di output tipo INT)

   * - output_DOUBLE_reg_X
     - DOUBLE_X
     - Registro di output robot tipo DOUBLE (X indica il numero di registri, se servono 16 registri di output tipo DOUBLE, il nome effettivo è: "output_DOUBLE_reg_16". Il robot supporta massimo 64 registri di output tipo DOUBLE)

   * - servoj_time
     - UINT64_5
     - Dati timestamp servoj, unità ns

   * - actual_joint_temp
     - DOUBLE_6
     - Temperatura driver giunti j1-j6, unità °

   * - axle_gen_com_data
     - UINT8_130
     - Dati periodici generali dell'end-effector

   * - abnormal_stop
     - UINT8
     - Stato anomalo, 0: nessuna anomalia, 1: anomalia presente

   * - cur_lua_file_name
     - UINT8_256
     - Nome del file Lua attualmente in esecuzione

   * - prog_total_line
     - UINT8
     - Numero totale di righe nel file corrente

   * - safety_box_signal
     - UINT8_6
     - Segnale pulsante del box pulsanti 0: premuto 1: rilasciato

   * - welding_voltage
     - DOUBLE
     - Tensione di saldatura effettiva, unità V

   * - welding_current
     - DOUBLE
     - Corrente di saldatura effettiva, unità A

   * - welding_track_speed
     - DOUBLE
     - Velocità di inseguimento del cordone di saldatura mm/s

   * - tpd_exception
     - UINT8
     - Eccezione TPD

   * - alarm_reboot_robot
     - UINT8
     - Avviso di riavvio del robot

   * - modbus_master_connect
     - UINT8
     - | Stato di connessione di 8 master Modbus  
       | bit0-bit7 rappresentano i master 0-7, 0-non connesso, 1-connesso

   * - modbus_slave_connect
     - UINT8
     - Stato di connessione slave Modbus, 0-non connesso, 1-connesso

   * - btn_box_stop_signal
     - UINT8
     - Segnale pulsante di arresto di emergenza

   * - drag_alarm
     - UINT8
     - Avviso di trascinamento

   * - safety_door_alarm
     - UINT8
     - Avviso porta di sicurezza, 0 nessun avviso, 1 porta di sicurezza attivata

   * - safety_plane_alarm
     - UINT8
     - Avviso parete di sicurezza, 0 nessun avviso, 1 ingresso nella parete di sicurezza

   * - motion_alarm
     - UINT8
     - | Avviso di movimento, 0-nessun avviso,
       | 1-Variazione postura istruzione LIN troppo grande,
       | 2-TCP superamento velocità,
       | 3-Collisione rilevata,
       | 4-Asse 1 ha superato la velocità massima,
       | 5-Asse 2 ha superato la velocità massima,
       | 6-Asse 3 ha superato la velocità massima,
       | 7-Asse 4 ha superato la velocità massima,
       | 8-Asse 5 ha superato la velocità massima,
       | 9-Asse 6 ha superato la velocità massima,
       | 10-Asse 1 deviazione tra comando giunto e feedback troppo grande,
       | 11-Asse 2 deviazione tra comando giunto e feedback troppo grande,
       | 12-Asse 3 deviazione tra comando giunto e feedback troppo grande,
       | 13-Asse 4 deviazione tra comando giunto e feedback troppo grande,
       | 14-Asse 5 deviazione tra comando giunto e feedback troppo grande,
       | 15-Asse 6 deviazione tra comando giunto e feedback troppo grande,
       | 16-Posa singolare,
       | 17-Istruzione LIN velocità movimento adattativa,
       | 18-Regolazione velocità target timeout o non completata,
       | 19-Movimento inserimento rotativo fallito,
       | 20-Movimento inserimento elicoidale fallito,
       | 21-Movimento inserimento lineare fallito,
       | 22-Movimento posizionamento superficie fallito

   * - interfere_alarm
     - UINT8
     - Avviso area di interferenza, 0 nessun avviso, 1 ingresso in area di interferenza

   * - udp_cmd_state
     - INT32
     - Stato connessione UDP

   * - weld_ready_state
     - UINT8
     - Stato pronto saldatrice, 1: pronto, 0: errore saldatrice

   * - alarm_check_emerg_stop_btn
     - UINT8
     - Avviso anomalia comunicazione giunti

   * - ts_tm_cmd_com_error
     - UINT8
     - Errore comando sistema di coppia

   * - ts_tm_state_com_error
     - UINT8
     - Errore stato sistema di coppia

   * - ctrl_box_error
     - INT32
     - Errore box di controllo

   * - safety_data_state
     - UINT8
     - Flag stato dati sicurezza, 0 nessuna anomalia, 1-anomalia

   * - force_sensor_err_state
     - UINT8
     - Guasto timeout connessione sensore di forza; bit0-bit1 corrispondono ai sensori di forza ID1-ID2

   * - ctrl_open_lua_errcode
     - UINT8_4
     - Codice errore protocollo aperto controller

   * - servo_id
     - UINT8
     - Numero ID driver servo

   * - servo_errcode
     - INT32
     - Codice guasto driver servo

   * - servo_state
     - INT32
     - Stato driver servo

   * - servo_actual_pos
     - DOUBLE
     - Posizione attuale servo

   * - servo_actual_speed
     - DOUBLE
     - Velocità attuale servo
   
   * - servo_actual_torque
     - DOUBLE
     - Coppia attuale servo
   
   * - gripper_active
     - INT32
     - Stato attivazione pinza
   
   * - gripper_position
     - UINT8
     - Feedback posizione pinza (percentuale)
   
   * - gripper_speed
     - INT32
     - Feedback velocità pinza (percentuale)
   
   * - gripper_current
     - INT32
     - Feedback corrente pinza (percentuale)
   
   * - gripper_temp
     - INT32
     - Temperatura attuale pinza, unità °
   
   * - gripper_voltage
     - INT32
     - Tensione attuale pinza, unità V
   
   * - rotating_gripper_num
     - DOUBLE
     - Feedback numero giri pinza rotante
   
   * - rotating_gripper_speed
     - UINT8
     - Feedback velocità rotazione pinza rotante (percentuale)
   
   * - rotating_gripper_tor
     - UINT8
     - Feedback coppia rotazione pinza rotante (percentuale)
   
   * - weld_break_off_state
     - UINT8
     - Stato interruzione saldatura: 0-saldatura non interrotta, 1-saldatura interrotta
   
   * - weld_arc_state
     - UINT8
     - Stato arco di saldatura, 0-arco non interrotto, 1-arco interrotto
   
   * - smarttool_state
     - UINT32
     - Dati IO estesi end-effector (Smart-Tool)
   
   * - tool_coord
     - DOUBLE_6
     - Posa utensile corrente rispetto all'end-effector
   
   * - wobj_coord
     - DOUBLE_6
     - Posa pezzo corrente rispetto alla base
   
   * - exTool_coord
     - DOUBLE_6
     - Posa utensile esterno corrente rispetto all'utensile
   
   * - exAxis_coord
     - DOUBLE_6
     - Posa asse esterno corrente rispetto al sistema di coordinate base
   
   * - robot_state
     - UINT8
     - | Stato operativo robot,
       | 1. Fermo; 2. In movimento; 3. In pausa; 4. Trascinamento
   
   * - actual_flange_pos
     - DOUBLE_6
     - Posa effettiva end-effector
   
   * - target_TCP_cmpvel
     - DOUBLE_2
     - Velocità lineare e angolare comando TCP, unità mm/s, °/s
   
   * - actual_TCP_cmpvel
     - DOUBLE_2
     - Velocità lineare e angolare effettiva TCP, unità mm/s, °/s
   
   * - tool_id
     - INT32
     - Numero utensile
   
   * - wobj_id
     - INT32
     - Numero pezzo
   
   * - ft_sensor_raw_data
     - DOUBLE_6
     - Dati grezzi forza/coppia end-effector nel sistema di coordinate del sensore
   
   * - ft_sensor_active
     - UINT8
     - Stato attivazione sensore forza/coppia
   
   * - gripper_motion_done
     - UINT8
     - Movimento pinza completato
   
   * - collision_state
     - UINT8
     - Stato rilevamento collisione
   
   * - trajectory_pnum
     - INT32
     - Numero sequenza corrente del movimento a punti discreti
   
   * - safety_stop0_state
     - UINT8
     - Stato segnale arresto di sicurezza SI0
   
   * - safety_stop1_state
     - UINT8
     - Stato segnale arresto di sicurezza SI1
   
   * - gripper_fault_id
     - UINT8
     - Numero pinza guasta
   
   * - gripper_fault
     - INT32
     - Numero errore pinza
   
   * - ext_DI_state
     - UINT8_16
     - DI estesi
   
   * - ext_DO_state
     - UINT8_16
     - DO estesi
   
   * - ext_AI_state
     - INT32_4
     - AI estesi
   
   * - ext_AO_state
     - INT32_4
     - AO estesi
   
   * - rbt_enable_state
     - INT32
     - Stato completamento abilitazione driver
   
   * - joint_driver_torque
     - DOUBLE_6
     - Valori di coppia effettivi giunti j1-j6, unità Nm
   
   * - robot_time
     - INT32_7
     - Tempo sistema robot, anno, mese, giorno, ora, minuto, secondo, millisecondo
   
   * - software_upgrade_state
     - INT32
     - Stato aggiornamento software robot
   
   * - end_lua_err_code
     - INT32
     - Stato segnale pulsante end-effector
   
   * - wide_voltage_ctrl_box_temp
     - DOUBLE
     - Temperatura box di controllo wide voltage, unità °
   
   * - wide_voltage_ctrl_box_fan_current
     - INT32
     - Corrente ventola box di controllo wide voltage
   
   * - last_servoJ_target
     - DOUBLE_6
     - Ultima posa comando target servoJ
   
   * - servoJ_cmd_num
     - INT32
     - Conteggio comandi servoJ
   
   * - strange_pos_flag
     - UINT8
     - Flag posa singolare
   
   * - alarm
     - UINT8
     - | Avviso, 0-nessun avviso,
       | 1-Cambiamento configurazione giunto spalla,
       | 2-Cambiamento configurazione giunto gomito,
       | 3-Cambiamento configurazione giunto polso,
       | 4-Inizializzazione RPY fallita,
       | 5-Timeout attesa WaitDI,
       | 6-Timeout attesa WaitAI,
       | 7-Timeout attesa WaitToolDI,
       | 8-Timeout attesa WaitToolAI,
       | 9-DI successo avvio arco non configurato,
       | 10-Timeout attesa WaitAuxDI,
       | 11-Timeout attesa WaitAuxAI,
       | 12-Punto irraggiungibile nella traiettoria di oscillazione,
       | 13-Calcolo punto presa inseguimento nastro trasportatore fallito,
       | 14-Anomalia dati sensore coppia giunto
   
   * - dr_alarm
     - UINT8
     - | Avviso driver, 0-nessun avviso,
       | 1-Avviso driver asse 1, resettabile,
       | 2-Avviso driver asse 2, resettabile,
       | 3-Avviso driver asse 3, resettabile,
       | 4-Avviso driver asse 4, resettabile,
       | 5-Avviso driver asse 5, resettabile,
       | 6-Avviso driver asse 6, resettabile
   
   * - alive_slave_num_error
     - UINT8
     - Guasto conteggio slave attivi, 0-nessun guasto, 1-errore, non resettabile
   
   * - slave_com_error
     - UINT8_8
     - | Guasto comunicazione slave, 0-nessun guasto,
       | 1-Slave offline,
       | 2-Stato slave incoerente con valore impostato,
       | 3-Slave non configurato,
       | 4-Errore configurazione slave,
       | 5-Errore inizializzazione slave,
       | 6-Errore inizializzazione comunicazione mailbox slave
   
   * - cmd_point_error
     - UINT8
     - | Guasto punto comando, 0-nessun guasto,
       | 1-Errore punto comando giunto,
       | 2-Errore punto target lineare,
       | 3-Errore punto intermedio arco,
       | 4-Errore punto target arco,
       | 5-Distanza punti comando arco troppo piccola,
       | 6-Errore punto intermedio 1 cerchio completo/elica,
       | 7-Errore punto intermedio 2 cerchio completo/elica,
       | 8-Errore punto intermedio 3 cerchio completo/elica,
       | 9-Distanza punti comando cerchio completo/elica troppo piccola,
       | 10-Errore punto comando TPD,
       | 11-Utensile comando TPD non corrisponde all'utensile corrente,
       | 12-Deviazione troppo grande tra comando TPD corrente e punto iniziale comando successivo,
       | 13-Errore commutazione utensile interno/esterno,
       | 14-Errore punto inizio nuova elica,
       | 15-Errore punto comando nuova curva spline,
       | 17-Comando giunto PTP fuori limite,
       | 18-Comando giunto TPD fuori limite,
       | 19-Comando giunto emesso LIN\ARC fuori limite,
       | 20-Superamento velocità comando nello spazio cartesiano,
       | 21-Comando coppia nello spazio giunto fuori limite,
       | 22-Comando giunto JOG fuori limite,
       | 23-Velocità comando asse 1 nello spazio giunto fuori limite,
       | 24-Velocità comando asse 2 nello spazio giunto fuori limite,
       | 25-Velocità comando asse 3 nello spazio giunto fuori limite,
       | 26-Velocità comando asse 4 nello spazio giunto fuori limite,
       | 27-Velocità comando asse 5 nello spazio giunto fuori limite,
       | 28-Velocità comando asse 6 nello spazio giunto fuori limite,
       | 29-Velocità feedback giunto fuori limite,
       | 30-Deviazione tra comando giunto e feedback troppo grande,
       | 31-Errore punto target DMP (inclusa non corrispondenza utensile),
       | 32-Velocità TCP fuori limite,
       | 33-Cambiamento configurazione giunto comando successivo,
       | 34-Cambiamento configurazione giunto comando corrente,
       | 35-Velocità giunto in comando LIN fuori limite,
       | 36-Velocità adattativa comando LIN supera soglia,
       | 37-Punto irraggiungibile nella traiettoria,
       | 38-Punto irraggiungibile nella traiettoria - posa singolare,
       | 49-Comandi PTP e SPTP non consentiti tra ARCSTART e ARCEND,
       | 50-Comandi PTP e SPTP non consentiti tra WEAVESTART e WEAVEEND,
       | 51-Errore parametri saldatura oscillante,
       | 52-Distanza punti comando saldatura oscillante troppo piccola,
       | 53-Punto irraggiungibile nella traiettoria di oscillazione - posa singolare,
       | 54-Punto irraggiungibile nella traiettoria di oscillazione - comando giunto fuori limite,
       | 55-Punto irraggiungibile nella traiettoria di oscillazione - eccezione pianificazione (Z utensile coincide con angolo direzione avanzamento X),
       | 56-Punto irraggiungibile nella traiettoria di oscillazione - eccezione pianificazione (errore punto percorso arco),
       | 65-Deviazione comando sensore laser troppo grande,
       | 66-Comando sensore laser interrotto, inseguimento cordone terminato prematuramente,
       | 81-Velocità comando asse esterno fuori limite,
       | 82-Deviazione tra comando asse esterno e feedback troppo grande,
       | 83-Comunicazione periferica estesa (asse esterno/IO) interrotta,
       | 84-Anomalia perdita pacchetti comunicazione periferica estesa (asse esterno/IO),
       | 85-Velocità comando asse esterno 1 nello spazio giunto fuori limite,
       | 86-Velocità comando asse esterno 2 nello spazio giunto fuori limite,
       | 87-Velocità comando asse esterno 3 nello spazio giunto fuori limite,
       | 88-Velocità comando asse esterno 4 nello spazio giunto fuori limite,
       | 89-Errore comunicazione Ethercat periferica estesa (asse esterno/IO),
       | 90-Errore comunicazione Canopen periferica estesa (asse esterno/IO),
       | 97-Inseguimento nastro trasportatore - variazione postura troppo grande tra punto iniziale e punto di riferimento,
       | 113-Controllo forza costante - direzione X supera distanza massima di regolazione,
       | 114-Controllo forza costante - direzione Y supera distanza massima di regolazione,
       | 115-Controllo forza costante - direzione Z supera distanza massima di regolazione,
       | 116-Controllo forza costante - direzione RX supera angolo massimo di regolazione,
       | 117-Controllo forza costante - direzione RY supera angolo massimo di regolazione,
       | 118-Controllo forza costante - direzione RZ supera angolo massimo di regolazione,
       | 119-Errore dati sensore esterno,
       | 120-Movimento di ricerca elicoidale fallito,
       | 121-Movimento inserimento rotativo fallito,
       | 122-Movimento inserimento lineare fallito,
       | 123-Movimento posizionamento superficie fallito,
       | 124-Forza di trascinamento anomala, ingresso trascinamento fallito,
       | 129-Superato numero massimo punti registrazione coppia,
       | 130-Errore commutazione velocità,
       | 131-Direzione utensile fuori limite,
       | 132-Momento fuori limite,
       | 133-Potenza fuori limite,
       | 134-Anomalia diagnostica STL-Flash,
       | 135-Anomalia diagnostica STL-RAM,
       | 136-Anomalia diagnostica STL-CPU,
       | 137-Anomalia dati sicurezza scheda sicurezza II-ECAT,
       | 138-Anomalia dati sicurezza ECAT asse 1,
       | 139-Anomalia dati sicurezza ECAT asse 2,
       | 140-Anomalia dati sicurezza ECAT asse 3,
       | 141-Anomalia dati sicurezza ECAT asse 4,
       | 142-Anomalia dati sicurezza ECAT asse 5,
       | 143-Anomalia dati sicurezza ECAT asse 6,
       | 145-Anomalia comunicazione tra scheda sicurezza e controller,
       | 147-Errore inseguimento fuoco,
       | 148-Velocità angolare fuori limite,
       | 149-Anomalia feedback parola stato giunto
   
   * - IO_error
     - UINT8
     - | Guasto IO, 0-nessun guasto,
       | 1-Errore canale, resettabile,
       | 2-Errore valore, resettabile,
       | 3-Timeout attesa WaitDI, resettabile,
       | 4-Timeout attesa WaitAI, resettabile,
       | 5-Timeout attesa WaitAxleDI, resettabile,
       | 6-Timeout attesa WaitAxleAI, resettabile,
       | 7-Errore funzione configurata canale, resettabile,
       | 8-Timeout avvio arco, resettabile,
       | 9-Timeout fine arco, resettabile,
       | 10-Timeout ricerca, resettabile,
       | 11-Timeout rilevamento IO nastro trasportatore, resettabile,
       | 12-Timeout attesa WaitAuxDI, resettabile,
       | 13-Timeout attesa WaitAuxAI, resettabile,
       | 14-Timeout ricerca filo, resettabile
   
   * - gripper_error
     - UINT8
     - Guasto pinza, 0-nessun guasto, 1-Errore timeout movimento pinza, resettabile
   
   * - file_error
     - UINT8
     - | Guasto file di configurazione, 0-nessun guasto,
       | 1-Errore versione file di configurazione zbt, errore inizializzazione - non resettabile,
       | 2-Caricamento file di configurazione zbt fallito, errore inizializzazione - non resettabile,
       | 3-Errore versione file di configurazione user, errore inizializzazione - non resettabile,
       | 4-Caricamento file di configurazione user fallito, errore inizializzazione - non resettabile,
       | 5-Errore versione file di configurazione exaxis, errore inizializzazione - non resettabile,
       | 6-Caricamento file di configurazione exaxis fallito, errore inizializzazione - non resettabile,
       | 7-Incoerenza modello robot, necessaria reimpostazione - non resettabile,
       | 8-Errore versione file di configurazione dhpara, errore inizializzazione - non resettabile,
       | 9-Caricamento file di configurazione dhpara fallito, errore inizializzazione - non resettabile,
       | 10-Modello robot non impostato - non resettabile,
       | 11-Errore versione file di configurazione load, errore inizializzazione - non resettabile,
       | 12-Caricamento file di configurazione load fallito, errore inizializzazione - non resettabile,
       | 13-Errore versione file di configurazione speed, errore inizializzazione - non resettabile,
       | 14-Caricamento file di configurazione speed fallito, errore inizializzazione - non resettabile,
       | 15-Errore versione file di configurazione weavepara, errore inizializzazione - non resettabile,
       | 16-Caricamento file di configurazione weavepara fallito, errore inizializzazione - non resettabile
   
   * - para_error
     - UINT8
     - | Guasto parametro di configurazione, 0-nessun guasto,
       | 1-Errore numero utensile fuori limite - resettabile,
       | 2-Errore soglia completamento posizionamento - resettabile,
       | 3-Errore livello collisione - resettabile,
       | 4-Errore peso carico - resettabile,
       | 5-Errore centro di massa carico X - resettabile,
       | 6-Errore centro di massa carico Y - resettabile,
       | 7-Errore centro di massa carico Z - resettabile,
       | 8-Errore tempo filtro DI - resettabile,
       | 9-Errore tempo filtro AxleDI - resettabile,
       | 10-Errore tempo filtro AI - resettabile,
       | 11-Errore tempo filtro AxleAI - resettabile,
       | 12-Errore intervallo livello alto/basso DI - resettabile,
       | 13-Errore intervallo livello alto/basso DO - resettabile,
       | 14-Errore numero pezzo fuori limite - resettabile,
       | 15-Errore numero asse esterno fuori limite - resettabile,
       | 16-Inseguimento nastro trasportatore - errore canale encoder - resettabile,
       | 17-Inseguimento nastro trasportatore - errore numero asse pezzo - resettabile,
       | 18-Modalità montaggio FR30L - errore montaggio non standard - resettabile
   
   * - exaxis_out_slimit_error
     - UINT8
     - | Guasto soft limite asse esterno, 0-nessun guasto,
       | 1-Guasto superamento soft limite asse esterno 1, resettabile,
       | 2-Guasto superamento soft limite asse esterno 2, resettabile,
       | 3-Guasto superamento soft limite asse esterno 3, resettabile,
       | 4-Guasto superamento soft limite asse esterno 4, resettabile,
       | 5-Guasto superamento soft limite asse esterno 5, resettabile,
       | 6-Guasto superamento soft limite asse esterno 6, resettabile
   
   * - dr_com_err
     - UINT8_6
     - Guasto comunicazione driver, 0-nessun guasto, 1-guasto
   
   * - dr_err
     - UINT8
     - | Guasto driver, 0-nessun guasto,
       | 1-Guasto driver asse 1, non resettabile,
       | 2-Guasto driver asse 2, non resettabile,
       | 3-Guasto driver asse 3, non resettabile,
       | 4-Guasto driver asse 4, non resettabile,
       | 5-Guasto driver asse 5, non resettabile,
       | 6-Guasto driver asse 6, non resettabile
   
   * - out_sflimit_err
     - UINT8
     - | Guasto soft limite, 0-nessun guasto,
       | 1-Guasto superamento soft limite asse 1, resettabile,
       | 2-Guasto superamento soft limite asse 2, resettabile,
       | 3-Guasto superamento soft limite asse 3, resettabile,
       | 4-Guasto superamento soft limite asse 4, resettabile,
       | 5-Guasto superamento soft limite asse 5, resettabile,
       | 6-Guasto superamento soft limite asse 6, resettabile

.. centered:: Tabella 1-2 Funzioni di configurazione del controllo in input del robot

.. list-table::
   :widths: 20 40 80
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Tipo di dato**
     - **Descrizione**

   * - speed_mask
     - UINT8
     - Maschera impostazione velocità globale: 0-non attiva; 1-attiva

   * - speed
     - UINT8
     - Imposta velocità globale (0-100)

   * - std_DO_mask
     - UINT8
     - Maschera controllo output DO standard del quadro di controllo (bit0 ~ bit7 rappresentano DO0 ~ DO7)

   * - std_DO_box
     - UINT8
     - Output DO standard del quadro di controllo (bit0 ~ bit7 rappresentano DO0 ~ DO7)

   * - cfg_DO_mask
     - UINT8
     - Maschera controllo output CO configurabile del quadro di controllo (bit0 ~ bit7 rappresentano CO0 ~ CO7)

   * - cfg_DO_box
     - UINT8
     - Output CO configurabile del quadro di controllo (bit0 ~ bit7 rappresentano CO0 ~ CO7)

   * - cfg_DO_tool_mask
     - UINT8
     - Maschera controllo output DO standard dello strumento del quadro di controllo (bit0 ~ bit1 rappresentano toolDO0 ~ toolDO1)

   * - cfg_DO_tool
     - UINT8
     - Output DO standard dello strumento del quadro di controllo (bit0 ~ bit1 rappresentano toolDO0 ~ toolDO1)

   * - std_AO_mask
     - UINT8
     - Maschera controllo output analogico del robot (bit0 ~ bit1 rappresentano AO0 ~ AO1 del quadro di controllo; bit2 rappresenta AO0 dello strumento)

   * - std_AO0_box
     - DOUBLE
     - Output analogico AO0 del quadro di controllo (0.0 ~ 4095.0)

   * - std_AO1_box
     - DOUBLE
     - Output analogico AO1 del quadro di controllo (0.0 ~ 4095.0)

   * - std_AO0_tool
     - DOUBLE
     - Output analogico AO1 dello strumento (0.0 ~ 4095.0)

   * - input_BIT_reg_8xX
     - UINT8_X
     - Registro di input robot tipo BIT (8xX indica il numero di registri, se servono 16 registri di input tipo BIT, il nome effettivo è: "input_BIT_reg_8x2". Il robot supporta massimo 128 registri tipo BIT)

   * - input_INT_reg_X
     - INT32_X
     - Registro di input robot tipo INT (X indica il numero di registri, se servono 16 registri di input tipo INT, il nome effettivo è: "input_INT_reg_16". Il robot supporta massimo 64 registri tipo INT)
  
   * - input_DOUBLE_reg_X
     - DOUBLE_X
     - Registro di input robot tipo DOUBLE (X indica il numero di registri, se servono 16 registri di input tipo DOUBLE, il nome effettivo è: "input_DOUBLE_reg_16". Il robot supporta massimo 64 registri tipo DOUBLE)

.. centered:: Tabella 1-3 Corrispondenza tipi di dati e lunghezza in byte

.. list-table::
   :widths: 60 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo di dato**
     - **Lunghezza in byte**

   * - UINT8
     - 1

   * - INT32
     - 4

   * - DOUBLE
     - 8

   * - UINT8_X
     - 1*X

   * - INT32_X
     - 4*X

   * - DOUBLE_X
     - 8*X