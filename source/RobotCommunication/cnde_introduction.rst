Introduzione a CNDE
===========================

Il protocollo configurabile di scambio dati di rete per robot collaborativi (di seguito CNDE) è un metodo tramite il quale un client controlla il robot e ottiene il suo stato di feedback attraverso la comunicazione UDP.

La Tabella 1-1 mostra l'insieme di tutti gli stati del robot ottenibili tramite CNDE. Il client può selezionare qualsiasi numero di stati necessari dalla tabella e far sì che il robot fornisca il feedback degli stati in base al periodo di feedback impostato.

Allo stesso modo, il client può selezionare le combinazioni di funzioni di controllo del robot necessarie dalla Tabella 1-2 per eseguire operazioni di controllo del robot. I dati di comunicazione CNDE tra client e robot devono seguire un formato di frame specifico, e la porta di comunicazione CNDE del robot è 20006.

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

   * - ft_sensor_data
     - DOUBLE_6
     - Dati sensore di forza

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