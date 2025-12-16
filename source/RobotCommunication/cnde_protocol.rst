Formato del protocollo del frame dati CNDE
===================================================

Il protocollo di comunicazione CNDE per il robot collaborativo è il seguente. Sia l'invio di dati dal client al robot che il feedback del robot al client devono rispettare questo protocollo. Il protocollo distingue i frame dati di diverse funzioni tramite il tipo di frame. Le definizioni dei tipi di frame sono riportate nella Tabella 2-2; diversi tipi di frame corrispondono a contenuti dati diversi. Le definizioni specifiche del contenuto dei dati sono riportate nelle Tabelle 3-1 ~ 3-7.

.. centered:: Tabella 2-1 Formato del frame dati CNDE del robot

.. list-table::
   :widths: 20 20 20 20 20 20 20
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Intestazione frame**
     - **Contatore frame**
     - **Tipo frame**
     - **Lunghezza dati**
     - **Contenuto**
     - **Coda frame**
   
   * - **Lunghezza (byte)**
     - 2
     - 1
     - 1
     - 2
     - --
     - 2
   
   * - **Contenuto**
     - 0x5A5A
     - 0 ~ 255
     - 0 ~ 8
     - Numero di byte del "contenuto dati"
     - Contenuto del frame dati
     - 0xA5A5

.. centered:: Tabella 2-2 Tipi di frame dati CNDE del robot

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo**
     - **Valore**
     - **Direzione del frame dati**

   * - Frame di configurazione di input (configurazione controllo)
     - 0x00
     - Client->Robot

   * - Frame di configurazione di output (configurazione stato)
     - 0x01
     - Client->Robot

   * - Avvio output CNDE
     - 0x02
     - Client->Robot

   * - Arresto output CNDE
     - 0x03
     - Client->Robot

   * - Frame di dati di output (dati di stato)
     - 0x04
     - Robot->Client

   * - Frame di dati di input (dati di controllo)
     - 0x05
     - Client->Robot

   * - Messaggio di prompt caratteri
     - 0x06
     - Client->Robot, Robot->Client

   * - Imposta numero versione protocollo CNDE del robot
     - 0x07
     - Client->Robot

   * - Ottieni versione software/firmware del robot
     - 0x08
     - Client->Robot, Robot->Client