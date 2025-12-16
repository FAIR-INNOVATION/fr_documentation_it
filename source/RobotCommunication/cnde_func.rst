Operazioni Funzionali CNDE
==========================================

Configurazione Input e Dati di Input
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Il client invia frame di dati al robot tramite CNDE per controllare uscite DO, AO, registri di input, ecc. Prima di inviare dati di input, è necessario configurare il contenuto funzionale da controllare. La Tabella 2-1 mostra il formato del contenuto della configurazione di input CNDE, che include il numero di ricetta e una serie di nomi di funzioni di configurazione di input (Tabella 1-2); la corrispondente Tabella 3-2 mostra il formato del contenuto dei dati di input, che include il numero di ricetta e il gruppo di byte dei dati di input.

CNDE supporta un massimo di 8 ricette per l'input dei dati. Quando vengono inviati dati di input, il robot abbina il numero di ricetta nei dati ricevuti al corrispondente gruppo di nomi di funzioni configurato per quella ricetta, analizza i dati per ottenere il valore di input per ciascun nome di funzione e quindi esegue operazioni di controllo del robot in base ai dati di input.

.. centered:: Tabella 3-1 Formato contenuto configurazione input

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Numero Ricetta**
     - **Stringa Nomi Funzione**

   * - Lunghezza(byte)
     - 1
     - --

   * - Contenuto
     - 0 ~ 7
     - Serie di nomi funzioni dati input

.. centered:: Tabella 3-2 Formato contenuto dati input

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Numero Ricetta**
     - **Gruppo Byte Dati**

   * - Lunghezza(byte)
     - 1
     - --

   * - Contenuto
     - 0 ~ 7
     - Contenuto dati input

Durante la configurazione dell'input, dopo aver ricevuto il gruppo di nomi di configurazione, il controller del robot verifica ciascun nome. Se i nomi delle funzioni configurati sono corretti, il robot restituisce i nomi dei tipi di dati di tutte le funzioni configurate, separati da ","; se ci sono errori nei nomi delle funzioni configurate, il robot restituisce il contenuto di errore corrispondente. Un esempio di frame di dati di configurazione input (esadecimale) è il seguente:

.. image:: cnde/001.png
   :width: 6in
   :align: center

La lunghezza totale del gruppo di nomi delle funzioni di input configurate è di 54 byte, più 1 byte per il numero di ricetta input, per un totale di 55 byte. Convertito in esadecimale è 0x0037. In modalità little-endian, la lunghezza dei dati corrispondente nel frame di dati di input è "37 00".

In questo caso, il robot restituirà un frame di dati di tipo messaggio di testo (messaggio di testo nella Sezione 3.3.1 di questo documento):

.. image:: cnde/002.png
   :width: 6in
   :align: center

Il tipo di messaggio "00" indica che si tratta di un messaggio di feedback di esecuzione riuscita. Il client può estrarre il "Tipo configurazione dati input" e confrontarlo con la Tabella 1-3 per ottenere la lunghezza in byte della configurazione input. In questo esempio, la lunghezza totale dei dati è 1*5 + 4*30 + 8*30 = 365 byte.

Se il nome della configurazione input è errato:

.. image:: cnde/003.png
   :width: 6in
   :align: center

Il feedback corrispondente è:

.. image:: cnde/004.png
   :width: 6in
   :align: center

I dati di input possono essere inviati ciclicamente a un certo periodo, o solo quando necessario. Durante l'input ciclico, il periodo minimo gestibile dal robot è 1ms, ma un periodo di input troppo rapido comporta un certo carico sulle risorse di sistema del robot. Si consiglia di impostare ragionevolmente il periodo di input dei dati in base alla situazione effettiva.

Inoltre, quando si invia un frame di dati al robot, il robot non invierà feedback a meno che la lunghezza del frame di dati o i dati non siano anomali. Un esempio di frame di dati di input è il seguente. Il numero di ricetta dei dati di input e la lunghezza del gruppo di byte dei dati di input devono corrispondere alla configurazione di input:

.. image:: cnde/005.png
   :width: 6in
   :align: center

Configurazione Output e Dati di Output
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Il client può personalizzare il contenuto e il periodo del feedback di stato quando ottiene il feedback di stato del robot tramite CNDE. L'utilizzo del feedback di stato CNDE del robot richiede i seguenti tre passaggi: ① Configurazione output; ② Avvio output; ③ Ricezione dati output.

Configurazione Output
+++++++++++++++++++++++

Il contenuto del frame di configurazione output include il periodo di output e il gruppo di nomi delle funzioni di output (tutti i nomi configurabili sono nella Tabella 1-1). L'intervallo di configurazione del periodo di output è 1 ~ 200 ms. Il numero massimo di byte dei dati di output supportato è 4096 byte. Il gruppo di nomi delle funzioni di output è una serie di stringhe di nomi di funzioni di output separate da ",". Dopo che il client invia il frame di configurazione output, il robot verifica i nomi delle funzioni configurati. Se tutti i nomi delle funzioni configurati sono supportati dal CNDE del robot corrente, il robot restituisce una serie di combinazioni di tipi di dati separate da ","; altrimenti, se la verifica dei nomi di configurazione output fallisce, restituisce le informazioni di errore corrispondenti.

.. centered:: Tabella 3-3 Contenuto configurazione output

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Periodo Output(ms)**
     - **Stringa Nomi Funzione**

   * - Lunghezza(byte)
     - 2
     - --

   * - Contenuto
     - 1-200
     - Gruppo nomi funzioni output

Ad esempio, il frame di configurazione output è il seguente:

.. image:: cnde/006.png
   :width: 6in
   :align: center

La lunghezza totale del gruppo di nomi delle funzioni di output configurate è di 48 byte, più 2 byte per il periodo di output, per un totale di 50 byte. Convertito in esadecimale è 0x0032. In modalità little-endian, la lunghezza dei dati corrispondente nel frame di dati di input è "32 00".

In questo caso, il robot restituirà un frame di dati di tipo messaggio di testo (messaggio di testo nella Sezione 3.3.1 di questo documento):

.. image:: cnde/007.png
   :width: 6in
   :align: center

Il tipo di messaggio "00" indica che si tratta di un messaggio di feedback di esecuzione riuscita. Il client può estrarre il "Tipo configurazione dati output" e confrontarlo con la Tabella 1-3 per ottenere la lunghezza in byte della configurazione output. In questo esempio, la lunghezza totale dei dati è 1 + 8*10 + 4 = 85 byte.

Se il nome della configurazione input è errato, ad esempio "queue" scritto erroneamente come "quene":

.. image:: cnde/008.png
   :width: 6in
   :align: center

Il feedback corrispondente è:

.. image:: cnde/009.png
   :width: 6in
   :align: center

Avvio e Arresto Output
++++++++++++++++++++++++++++++++++

Dopo aver completato la configurazione output CNDE del robot, inviando il comando di avvio output CNDE, il robot inizierà a fornire feedback di stato in base al periodo e al contenuto di output configurati. Allo stesso modo, inviando il comando di arresto output CNDE, il robot interromperà il feedback di stato. I comandi di avvio e arresto CNDE non hanno contenuto, quindi la lunghezza dei dati corrispondente è 0.

.. centered:: Tabella 3-4 Contenuto Avvio/Arresto Output CNDE

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Gruppo Byte Dati**

   * - Lunghezza(byte)
     - 0

   * - Contenuto
     - Nessuno

Un esempio di frame di dati per avviare l'output CNDE del robot è il seguente:

.. image:: cnde/010.png
   :width: 3in
   :align: center

Ricezione Dati Output da Parte del Client
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Dopo aver avviato l'output dati CNDE del robot, il client deve impostare un ciclo per ricevere le informazioni di dati restituite dal robot. La frequenza di ricezione ciclica del client deve essere superiore alla frequenza di output dati configurata, altrimenti potrebbero verificarsi perdite di pacchetti. Il contenuto dei dati di output del robot è mostrato nella Tabella 3-5; la lunghezza del gruppo di byte dei dati di output del robot è la somma delle lunghezze in byte di tutti i dati delle funzioni configurate per l'output. L'array di byte è una combinazione di tutti i dati di stato in ordine di funzione configurata, allineato a 1 byte.

.. centered:: Tabella 3-5 Contenuto dati output CNDE

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Gruppo Byte Dati**

   * - Lunghezza(byte)
     - --

   * - Contenuto
     - Gruppo byte dati output

Un esempio di frame di dati di output del robot è il seguente:

.. image:: cnde/011.png
   :width: 4in
   :align: center

Funzioni Ausiliarie CNDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Messaggio di Testo
++++++++++++++++++++++++++++++

Il client e il robot possono scambiarsi messaggi di testo tramite CNDE. Il contenuto del messaggio include il tipo di messaggio e la stringa del messaggio (Tabella 3-6), dove il tipo di messaggio è definito nella Tabella 3-7. Quando il client CNDE invia comandi al robot come configurazione input, configurazione output, avvio output, arresto output, ecc., il robot risponde sempre con un messaggio di testo.

Se i comandi sopra menzionati vengono eseguiti con successo, il robot restituisce un tipo di messaggio "Successo", corrispondente al valore 0x00; al contrario, se l'esecuzione fallisce, il robot restituisce un tipo di messaggio "Errore", corrispondente al valore 0x03. Il client può determinare il risultato dell'esecuzione del comando in base al tipo di messaggio restituito. Se il tipo di messaggio è "Errore", è possibile estrarre le informazioni di errore per analizzarne la causa.

.. centered:: Tabella 3-6 Contenuto messaggio di testo

.. list-table::
   :widths: 40 20 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Nome**
     - **Tipo Messaggio**
     - **Stringa Messaggio**

   * - Lunghezza(byte)
     - 1
     - --

   * - Contenuto
     - 0 ~ 4
     - Stringa messaggio

.. centered:: Tabella 3-7 Tipi messaggio di testo CNDE robot

.. list-table::
   :widths: 40 40
   :header-rows: 0
   :align: center
   :class: sheet-center

   * - **Tipo**
     - **Valore**

   * - Successo
     - 0x00

   * - Informazione
     - 0x01

   * - Avviso
     - 0x02

   * - Errore
     - 0x03

   * - Guasto
     - 0x04

Cambiare Numero Versione Protocollo CNDE Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Attualmente, il CNDE del robot ha solo una versione, il numero di versione è "FR-CNDE-V0001". Pertanto, questa funzione è riservata e non è ancora disponibile per l'uso.

Ottenere Informazioni Versione Software/Firmware Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Il client invia un comando al robot tramite CNDE per richiedere informazioni sulla versione software/firmware. Il contenuto del comando è vuoto. Dopo aver ricevuto la richiesta, il robot risponderà con un messaggio di testo che include informazioni come il modello del robot, la versione del software del robot, la versione del firmware del robot, la versione hardware del robot, ecc.