IO Robot
============

.. toctree:: 
    :maxdepth: 5

Impostare Uscite Digitali Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDO(id, status, smooth=0, block=0)``"
    "Descrizione", "Imposta uscite digitali box controllo"
    "Parametri Obbligatori", "-  ``id``:numero io, range [0~15];
    - ``status``:0-spento, 1-acceso;"
    "Parametri Predefiniti", "- ``smooth``:0-nessun smoothing, 1-smoothing default 0;
    - ``block``:0-bloccante, 1-non bloccante default 0"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Uscite Digitali Utensile
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDO(id, status, smooth=0, block=0)``"
    "Descrizione", "Imposta uscite digitali utensile"
    "Parametri Obbligatori", "-  ``id``:numero io, range [0~1];
    - ``status``:0-spento, 1-acceso;"
    "Parametri Predefiniti", "- ``smooth``:0-nessun smoothing, 1-smoothing;
    - ``block``:0-bloccante, 1-non bloccante."
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Uscite Analogiche Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAO(id,value,block=0)``"
    "Descrizione", "Imposta uscite analogiche box controllo"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~1];
    - ``value``:percentuale valore corrente o tensione, range [0~100%] corrisponde corrente [0~20mA] o tensione [0~10V];"
    "Parametri Predefiniti", "- ``block``:[0]-bloccante, [1]-non bloccante default 0"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Uscite Analogiche Utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolAO(id,value,block=0)``"
    "Descrizione", "Imposta uscite analogiche utensile"
    "Parametri Obbligatori", "- ``id``:numero io, range [0];
    - ``value``:percentuale valore corrente o tensione, range [0~100%] corrisponde corrente [0~20mA] o tensione [0~10V];"
    "Parametri Predefiniti", "- ``block``:[0]-bloccante, [1]-non bloccante default 0"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Impostazione Uscite Digitali/Analogiche
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0  
    block = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3) 
    status = 0 
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1) 
    status = 0 
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    robot.CloseRPC()

Ottenere Ingressi Digitali Box Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDI(id, block=0)``"
    "Descrizione", "Ottiene ingressi digitali box controllo"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~15];"
    "Parametri Predefiniti", "- ``block``:0-bloccante, 1-non bloccante default 0"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``di``: 0-livello basso, 1-livello alto"

Ottenere Ingressi Digitali Utensile
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDI(id, block=0)``"
    "Descrizione", "Ottiene ingressi digitali utensile"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~1];"
    "Parametri Predefiniti", "- ``block``:0-bloccante, 1-non bloccante default 0"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode
    - ``di``: 0-livello basso, 1-livello alto"

Ottenere Ingressi Analogici Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAI(id, block = 0)``"
    "Descrizione", "Ottiene ingressi analogici box controllo"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~1];"
    "Parametri Predefiniti", "- ``block``:0-bloccante, 1-non bloccante default 0 "
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``value``: Percentuale valore corrente o tensione input, range [0~100] corrisponde corrente [0~20mA] o tensione [0~10V]"

Ottenere Ingressi Analogici Utensile
+++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolAI(id, block = 0)``"
    "Descrizione", "Ottiene ingressi analogici terminale"
    "Parametri Obbligatori", "- ``id``:numero io, range [0];"
    "Parametri Predefiniti", "- ``block``:0-bloccante, 1-non bloccante default 0"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``value``: Percentuale valore corrente o tensione input, range [0~100] corrisponde corrente [0~20mA] o tensione [0~10V]"

Ottenere Stato Pulsante Registrazione Punto Terminale Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAxlePointRecordBtnState()``"
    "Descrizione", "Ottiene stato pulsante registrazione punto terminale robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``buttonstatus``: Stato pulsante, 0-premuto, 1-rilasciato"

Ottenere Stato Uscite DO Terminale Robot
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDO()``"
    "Descrizione", "Ottiene stato uscite DO terminale robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``do_state``: Stato uscite DO, do0~do1 corrisponde bit1~bit2, da bit0 inizio"

Ottenere Stato Uscite DO Controller Robot
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDO()``"
    "Descrizione", "Ottiene stato uscite DO controller robot"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "- Codice errore successo-0 fallimento- errcode
    - ``do_state_h``: Stato uscite DO, co0~co7 corrisponde bit0~bit7 do_state_l Stato uscite DO, do0~do7 corrisponde bit0~bit7"

Esempio Codice Stato DI, DO Robot
+++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    block = 0 
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}") 
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    robot.CloseRPC()

Attendere Ingressi Digitali Box Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitDI(id,status,maxtime,opt)``"
    "Descrizione", "Attende ingressi digitali box controllo"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~15];
    - ``status``:0-spento, 1-acceso;
    - ``maxtime``:tempo attesa massimo, unità [ms];
    - ``opt``:strategia dopo timeout, 0-programma ferma e indica timeout, 1-ignora timeout indica programma continua esecuzione, 2-attesa continua"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Attendere Ingressi Digitali Multipli Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitMultiDI(mode,id,status,maxtime,opt)``"
    "Descrizione", "Attende ingressi digitali multipli box controllo"
    "Parametri Obbligatori", "- ``mode``:[0]-AND multiplo, [1]-OR multiplo;
    - ``id``:numero io, bit0~bit7 corrisponde DI0~DI7, bit8~bit15 corrisponde CI0~CI7;
    - ``status``:bit0~bit7 corrisponde stato DI0~DI7, bit8~bit15 corrisponde stato bit CI0~CI7 [0]-spento, [1]-acceso;
    - ``maxtime``:tempo attesa massimo, unità [ms];
    - ``opt``:strategia dopo timeout, 0-programma ferma e indica timeout, 1-ignora timeout indica programma continua esecuzione, 2-attesa continua."
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Attendere Ingressi Digitali Utensile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitToolDI(id,status,maxtime,opt)``"
    "Descrizione", "Attende ingressi digitali terminale"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~1];
    - ``status``:0-spento, 1-acceso;
    - ``maxtime``:tempo attesa massimo, unità [ms];
    - ``opt``:strategia dopo timeout, 0-programma ferma e indica timeout, 1-ignora timeout indica programma continua esecuzione, 2-attesa continua"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Attendere Ingressi Analogici Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAI(id,sign,value,maxtime,opt)``"
    "Descrizione", "Attende ingressi analogici box controllo"
    "Parametri Obbligatori", "- ``id``:numero io, range [0~1];
    - ``sign``:0-maggiore, 1-minore
    - ``value``:percentuale valore corrente o tensione input, range [0~100] corrisponde corrente [0~20mA] o tensione [0~10V];
    - ``maxtime``:tempo attesa massimo, unità [ms];
    - ``opt``:strategia dopo timeout, 0-programma ferma e indica timeout, 1-ignora timeout indica programma continua esecuzione, 2-attesa continua"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Attendere Ingressi Analogici Utensile
++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitToolAI(id,sign,value,maxtime,opt)``"
    "Descrizione", "Attende ingressi analogici terminale"
    "Parametri Obbligatori", "- ``id``:numero io, range [0];
    - ``sign``:0-maggiore, 1-minore
    - ``value``:percentuale valore corrente o tensione input, range [0~100] corrisponde corrente [0~20mA] o tensione [0~10V];
    - ``maxtime``:tempo attesa massimo, unità [ms];
    - ``opt``:strategia dopo timeout, 0-programma ferma e indica timeout, 1-ignora timeout indica programma continua esecuzione, 2-attesa continua"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Esempio Codice Attesa Segnali Input Digitali/Analogici Box Controllo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    status = 1
    smooth = 0
    block = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 0
    for i in range(16):
        robot.SetDO(i, status, smooth, block)
        time.sleep(0.3)
    status = 1
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    status = 0
    for i in range(2):
        robot.SetToolDO(i, status, smooth, block)
        time.sleep(1)
    for i in range(100):
        robot.SetAO(0, i, block)
        time.sleep(0.03)
    for i in range(100):
        robot.SetToolAO(0, i, block)
        time.sleep(0.03)
    block = 0
    error,di = robot.GetDI(0, block)
    print(f"di0: {di}")
    error,tool_di = robot.GetToolDI(1, block)
    print(f"tool_di1: {tool_di}")
    error,ai = robot.GetAI(0, block)
    print(f"ai0: {ai:.2f}")
    error,tool_ai = robot.GetToolAI(0, block)
    print(f"tool_ai0: {tool_ai:.2f}")
    error,button_state = robot.GetAxlePointRecordBtnState()
    print(f"_button_state is: {button_state}")
    error,tool_do_state = robot.GetToolDO()
    print(f"tool DO state: {tool_do_state}")
    error,[do_state_h, do_state_l] = robot.GetDO()
    print(f"DO state hight  : {do_state_h}")
    print(f"DO state low : {do_state_l}")
    rtn = robot.WaitDI(0, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitMultiDI(1, 3, 3, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolDI(1, 1, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    rtn = robot.WaitToolAI(0, 0, 50, 1000, 1)
    print(f"WaitDI over; rtn is: {rtn}")
    robot.CloseRPC()

Imposta Se Output DO Scatola Controllo Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxDO(resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output DO della scatola di controllo si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output AO Scatola Controllo Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxAO(resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output AO della scatola di controllo si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output DO Utensile Terminale Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleDO(resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output DO dell'utensile terminale si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output AO Utensile Terminale Si Ripristina Dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleAO(resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output AO dell'utensile terminale si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output DO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtDO (resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output DO esteso si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output AO Esteso Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtAO (resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output AO esteso si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Imposta Se Output SmartTool Si Ripristina Dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetSmartToolDO(resetFlag,reloadFlag)``"
    "Descrizione", "Imposta se l'output SmartTool si ripristina dopo stop/pausa"
    "Parametri Obbligatori", "
    - ``resetFlag``：0-Non ripristina; 1-Ripristina
    - ``reloadFlag``：Se ricaricare dopo ripresa pausa, 0-Non caricare; 1-Carica"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0 Fallimento- errcode"

Esempio Codice Impostazione Ripristino Output Dopo Stop/Pausa Programma Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    for i in range(16):
        robot.SetDO(i, 1, 0, 0)
        time.sleep(0.2)
    resetFlag = 0
    resumeReloadFlag = 0
    rtn = robot.SetOutputResetCtlBoxDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetCtlBoxAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetAxleAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtDO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetExtAO(resetFlag, resumeReloadFlag)
    robot.SetOutputResetSmartToolDO(resetFlag, resumeReloadFlag)
    robot.ProgramLoad("test.lua")
    robot.ProgramRun()
    time.sleep(2)
    robot.PauseMotion()
    time.sleep(2)
    robot.ResumeMotion()
    time.sleep(2)
    robot.CloseRPC()
    return 0

Impostare le Funzioni delle Porte CI Configurabili
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDIConfig(config)``"
    "Descrizione", "Imposta le funzioni delle porte CI configurabili"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione CI0-CI7, 0-Nessuna;1-Avvio arco riuscito;2-Saldatrice pronta;3-Rilevamento nastro trasportatore;4-Pausa;5-Riprendi;6-Avvio;7-Arresto;
      8-Pausa/Riprendi;9-Avvio/Arresto;10-Trascinamento a pedale;11-Spostamento a origine lavoro;12-Commutazione manuale/automatica;
      13-Ricerca filo riuscita;14-Interruzione movimento;15-Avvio programma principale;16-Avvio riavvolgimento;17-Conferma avvio;
      18-Segnale rilevamento fotoelettrico X;19-Segnale rilevamento fotoelettrico Y;20-Segnale ingresso arresto emergenza esterno 1;21-Segnale ingresso arresto emergenza esterno 2;
      22-Modalità riduzione livello 1;23-Modalità riduzione livello 2;24-Modalità riduzione livello 3 (Arresto);25-Riprendi saldatura;26-Termina saldatura;
      27-Abilita trascinamento assistito;28-Disabilita trascinamento assistito;29-Abilita/Disabilita trascinamento assistito;30-Cancella tutti gli errori;
      31-Commutazione manuale/automatica (livello alto/basso);32-Abilita;33-Disabilita;34-Abilita/Disabilita (fronte di salita/discesa);35-Avvio/ fine inseguimento punto fisso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere le Funzioni delle Porte CI Configurabili del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDIConfig()``"
    "Descrizione", "Ottiene le funzioni delle porte CI configurabili del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione CI0-CI7, 0-Nessuna;1-Avvio arco riuscito;2-Saldatrice pronta;3-Rilevamento nastro trasportatore;4-Pausa;5-Riprendi;6-Avvio;7-Arresto;
      8-Pausa/Riprendi;9-Avvio/Arresto;10-Trascinamento a pedale;11-Spostamento a origine lavoro;12-Commutazione manuale/automatica;
      13-Ricerca filo riuscita;14-Interruzione movimento;15-Avvio programma principale;16-Avvio riavvolgimento;17-Conferma avvio;
      18-Segnale rilevamento fotoelettrico X;19-Segnale rilevamento fotoelettrico Y;20-Segnale ingresso arresto emergenza esterno 1;21-Segnale ingresso arresto emergenza esterno 2;
      22-Modalità riduzione livello 1;23-Modalità riduzione livello 2;24-Modalità riduzione livello 3 (Arresto);25-Riprendi saldatura;26-Termina saldatura;
      27-Abilita trascinamento assistito;28-Disabilita trascinamento assistito;29-Abilita/Disabilita trascinamento assistito;30-Cancella tutti gli errori;
      31-Commutazione manuale/automatica (livello alto/basso);32-Abilita;33-Disabilita;34-Abilita/Disabilita (fronte di salita/discesa);35-Avvio/ fine inseguimento punto fisso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare le Funzioni delle Porte CO Configurabili
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDOConfig(config)``"
    "Descrizione", "Imposta le funzioni delle porte CO configurabili"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione CO0-CO7, 0-Nessuna;1-Errore robot;2-Robot in movimento;3-Avvio/arresto spruzzatura;4-Pulizia pistola spruzzo;5-Segnale gas;6-Segnale avvio arco;7-Alimentazione filo a impulsi;
      8-Alimentazione filo inversa;9-Ingresso JOB 1;10-Ingresso JOB 2;11-Ingresso JOB 3;12-Controllo avvio/arresto nastro trasportatore;13-Robot in pausa;14-Origine lavoro raggiunta;
      15-Area di interferenza raggiunta;16-Controllo avvio/arresto ricerca filo;17-Avvio robot completato;18-Avvio/arresto programma;19-Modalità automatica/manuale;20-Segnale uscita arresto emergenza 1-Sicurezza;
      21-Segnale uscita arresto emergenza 2-Sicurezza;22-Esecuzione/arresto programma script Lua;23-Uscita stato sicurezza-Sicurezza;24-Uscita stato arresto protettivo-Sicurezza;
      25-Robot in movimento-Sicurezza;26-Modalità ridotta robot-Sicurezza;27-Modalità non ridotta robot-Sicurezza;28-Robot non arrestato;29-Errore robot-Errore punto istruzione;
      30-Errore robot-Errore driver;31-Errore robot-Limite software superato;32-Errore robot-Errore collisione;33-Errore robot-Errore numero slave attivi;
      34-Errore robot-Errore slave;35-Errore robot-Errore IO;36-Errore robot-Errore gripper;37-Errore robot-Errore file;38-Errore robot-Errore posa singolare;
      39-Errore robot-Errore comunicazione driver;40-Errore robot-Errore parametro;41-Errore robot-Asse esterno limite software superato;42-Avviso robot-Avviso;
      43-Avviso robot-Avviso porta sicurezza;44-Avviso robot-Avviso movimento;45-Avviso robot-Avviso area interferenza;46-Avviso robot-Avviso parete sicurezza;
      47-Stato abilitazione;48-Sollevamento automatico durante disconnessione;49-Avviso interferenza cubo 1;50-Avviso interferenza cubo 2;51-Avviso interferenza cubo 3;52-Avviso interferenza cubo 4;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere le Funzioni delle Porte CO Configurabili
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDOConfig()``"
    "Descrizione", "Ottiene le funzioni delle porte CO configurabili"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione CO0-CO7, 0-Nessuna;1-Errore robot;2-Robot in movimento;3-Avvio/arresto spruzzatura;4-Pulizia pistola spruzzo;5-Segnale gas;6-Segnale avvio arco;7-Alimentazione filo a impulsi;
      8-Alimentazione filo inversa;9-Ingresso JOB 1;10-Ingresso JOB 2;11-Ingresso JOB 3;12-Controllo avvio/arresto nastro trasportatore;13-Robot in pausa;14-Origine lavoro raggiunta;
      15-Area di interferenza raggiunta;16-Controllo avvio/arresto ricerca filo;17-Avvio robot completato;18-Avvio/arresto programma;19-Modalità automatica/manuale;20-Segnale uscita arresto emergenza 1-Sicurezza;
      21-Segnale uscita arresto emergenza 2-Sicurezza;22-Esecuzione/arresto programma script Lua;23-Uscita stato sicurezza-Sicurezza;24-Uscita stato arresto protettivo-Sicurezza;
      25-Robot in movimento-Sicurezza;26-Modalità ridotta robot-Sicurezza;27-Modalità non ridotta robot-Sicurezza;28-Robot non arrestato;29-Errore robot-Errore punto istruzione;
      30-Errore robot-Errore driver;31-Errore robot-Limite software superato;32-Errore robot-Errore collisione;33-Errore robot-Errore numero slave attivi;
      34-Errore robot-Errore slave;35-Errore robot-Errore IO;36-Errore robot-Errore gripper;37-Errore robot-Errore file;38-Errore robot-Errore posa singolare;
      39-Errore robot-Errore comunicazione driver;40-Errore robot-Errore parametro;41-Errore robot-Asse esterno limite software superato;42-Avviso robot-Avviso;
      43-Avviso robot-Avviso porta sicurezza;44-Avviso robot-Avviso movimento;45-Avviso robot-Avviso area interferenza;46-Avviso robot-Avviso parete sicurezza;
      47-Stato abilitazione;48-Sollevamento automatico durante disconnessione;49-Avviso interferenza cubo 1;50-Avviso interferenza cubo 2;51-Avviso interferenza cubo 3;52-Avviso interferenza cubo 4;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDIConfig(config)``"
    "Descrizione", "Imposta le funzioni delle porte End-CI configurabili dell'end-effector"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione End CI0-CI1, 0-Nessuna;1-Interruttore strumento insegnamento a trascinamento;2-Segnale registrazione punto;3-Commutazione manuale/automatica (segnale impulsivo);4-Avvio/arresto registrazione TPD;5-Pausa movimento;
      6-Riprendi movimento;7-Avvio;8-Arresto;9-Pausa/Riprendi;10-Avvio/Arresto;11-Abilita trascinamento assistito sensore di forza;12-Disabilita trascinamento assistito sensore di forza;
      13-Abilita/Disabilita trascinamento assistito sensore di forza;14-Segnale rilevamento laser X;15-Segnale rilevamento laser Y;16-Movimento PTP verso origine lavoro;17-Interruzione movimento, arresta movimento corrente in base al segnale;
      18-Avvio programma principale;19-Avvio riavvolgimento;20-Conferma avvio;21-Riprendi saldatura;22-Termina saldatura;23-Cancella errore;24-Commutazione manuale/automatica (livello alto/basso);
      25-Abilita;26-Disabilita;27-Abilita/Disabilita;28-Segnale avvio/arresto inseguimento servocomando laser;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere le Funzioni delle Porte End-CI Configurabili dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDIConfig()``"
    "Descrizione", "Ottiene le funzioni delle porte End-CI configurabili dell'end-effector"
    "Parametri Obbligatori", "
    - ``config``: Array codici funzione End CI0-CI1, 0-Nessuna;1-Interruttore strumento insegnamento a trascinamento;2-Segnale registrazione punto;3-Commutazione manuale/automatica (segnale impulsivo);4-Avvio/arresto registrazione TPD;5-Pausa movimento;
      6-Riprendi movimento;7-Avvio;8-Arresto;9-Pausa/Riprendi;10-Avvio/Arresto;11-Abilita trascinamento assistito sensore di forza;12-Disabilita trascinamento assistito sensore di forza;
      13-Abilita/Disabilita trascinamento assistito sensore di forza;14-Segnale rilevamento laser X;15-Segnale rilevamento laser Y;16-Movimento PTP verso origine lavoro;17-Interruzione movimento, arresta movimento corrente in base al segnale;
      18-Avvio programma principale;19-Avvio riavvolgimento;20-Conferma avvio;21-Riprendi saldatura;22-Termina saldatura;23-Cancella errore;24-Commutazione manuale/automatica (livello alto/basso);
      25-Abilita;26-Disabilita;27-Abilita/Disabilita;28-Segnale avvio/arresto inseguimento servocomando laser;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDIConfigLevel(config)``"
    "Descrizione", "Imposta lo stato attivo CI configurabile del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere lo Stato Attivo CI Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDIConfigLevel()``"
    "Descrizione", "Ottiene lo stato attivo CI configurabile del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetDOConfigLevel(config)``"
    "Descrizione", "Imposta lo stato attivo CO configurabile del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere lo Stato Attivo CO Configurabile del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDOConfigLevel()``"
    "Descrizione", "Ottiene lo stato attivo CO configurabile del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CO0-CO7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolDIConfigLevel(config)``"
    "Descrizione", "Imposta lo stato attivo CI configurabile dell'end-effector"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere lo Stato Attivo CI Configurabile dell'End-Effector
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetToolDIConfigLevel()``"
    "Descrizione", "Ottiene lo stato attivo CI configurabile dell'end-effector"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte CI0-CI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStandardDILevel(config)``"
    "Descrizione", "Imposta lo stato attivo DI standard del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere lo Stato Attivo DI Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetStandardDILevel()``"
    "Descrizione", "Ottiene lo stato attivo DI standard del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte DI0-DI7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Impostare lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetStandardDOLevel(config)``"
    "Descrizione", "Imposta lo stato attivo DO standard del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Ottenere lo Stato Attivo DO Standard del Box di Controllo
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetStandardDOLevel()``"
    "Descrizione", "Ottiene lo stato attivo DO standard del box di controllo"
    "Parametri Obbligatori", "
    - ``config``: Array stato attivo porte DO0-DO7; 0-attivo alto; 1-attivo basso"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"
    
Esempio di Codice SDK per Configurazione IO
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from time import sleep
    import time
    from fairino import Robot

    # Stabilire la connessione con il controller del robot
    robot = Robot.RPC('192.168.58.2')


    def TestIOConfig(self):
        # Imposta e ottiene configurazione DI
        setDIConfig = [1, 2, 3, 4, 5, 6, 7, 8]
        getDIConfig = [0] * 8
        rtn = robot.SetDIConfig(setDIConfig)
        print(f"SetDIConfig rtn is {rtn}")
        rtn, getDIConfig = robot.GetDIConfig()
        print(f"GetDIConfig rtn is {rtn}, value is {getDIConfig[0]} {getDIConfig[1]} {getDIConfig[2]} {getDIConfig[3]} {getDIConfig[4]} {getDIConfig[5]} {getDIConfig[6]} {getDIConfig[7]}")

        # Imposta e ottiene configurazione DO
        setDOConfig = [9, 10, 11, 12, 13, 14, 15, 16]
        getDOConfig = [0] * 8
        rtn = robot.SetDOConfig(setDOConfig)
        print(f"SetDOConfig rtn is {rtn}")
        rtn, getDOConfig = robot.GetDOConfig()
        print(f"GetDOConfig rtn is {rtn}, value is {getDOConfig[0]} {getDOConfig[1]} {getDOConfig[2]} {getDOConfig[3]} {getDOConfig[4]} {getDOConfig[5]} {getDOConfig[6]} {getDOConfig[7]}")

        # Imposta e ottiene configurazione DI utensile
        setToolDIConfig = [17, 18]
        getToolDIConfig = [0] * 2
        rtn = robot.SetToolDIConfig(setToolDIConfig)
        print(f"SetToolDIConfig rtn is {rtn}")
        rtn, getToolDIConfig = robot.GetToolDIConfig()
        print(f"GetToolDIConfig rtn is {rtn}, value is {getToolDIConfig[0]} {getToolDIConfig[1]}")

        # Imposta e ottiene configurazione livello DI (0: attivo basso, 1: attivo alto)
        setDIConfigLevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getDIConfigLevel = [0] * 8
        rtn = robot.SetDIConfigLevel(setDIConfigLevel)
        print(f"SetDIConfigLevel rtn is {rtn}")
        rtn, getDIConfigLevel = robot.GetDIConfigLevel()
        print(f"GetDIConfigLevel rtn is {rtn}, value is {getDIConfigLevel[0]} {getDIConfigLevel[1]} {getDIConfigLevel[2]} {getDIConfigLevel[3]} {getDIConfigLevel[4]} {getDIConfigLevel[5]} {getDIConfigLevel[6]} {getDIConfigLevel[7]}")

        # Imposta e ottiene configurazione livello DO (0: attivo basso, 1: attivo alto)
        setDOConfigLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getDOConfigLevel = [0] * 8
        rtn = robot.SetDOConfigLevel(setDOConfigLevel)
        print(f"SetDOConfigLevel rtn is {rtn}")
        rtn, getDOConfigLevel = robot.GetDOConfigLevel()
        print(f"GetDOConfigLevel rtn is {rtn}, value is {getDOConfigLevel[0]} {getDOConfigLevel[1]} {getDOConfigLevel[2]} {getDOConfigLevel[3]} {getDOConfigLevel[4]} {getDOConfigLevel[5]} {getDOConfigLevel[6]} {getDOConfigLevel[7]}")

        # Imposta e ottiene configurazione livello DI utensile
        setToolDIConfigLevel = [1, 0]
        getToolDIConfigLevel = [0] * 2
        rtn = robot.SetToolDIConfigLevel(setToolDIConfigLevel)
        print(f"SetToolDIConfigLevel rtn is {rtn}")
        rtn, getToolDIConfigLevel = robot.GetToolDIConfigLevel()
        print(f"GetToolDIConfigLevel rtn is {rtn}, value is {getToolDIConfigLevel[0]} {getToolDIConfigLevel[1]}")

        # Imposta e ottiene configurazione livello DI standard
        setStandardDILevel = [1, 1, 1, 1, 0, 0, 0, 0]
        getStandardDILevel = [0] * 8
        rtn = robot.SetStandardDILevel(setStandardDILevel)
        print(f"SetStandardDILevel rtn is {rtn}")
        rtn, getStandardDILevel = robot.GetStandardDILevel()
        print(f"GetStandardDILevel rtn is {rtn}, value is {getStandardDILevel[0]} {getStandardDILevel[1]} {getStandardDILevel[2]} {getStandardDILevel[3]} {getStandardDILevel[4]} {getStandardDILevel[5]} {getStandardDILevel[6]} {getStandardDILevel[7]}")

        # Imposta e ottiene configurazione livello DO standard
        setStandardDOLevel = [0, 0, 0, 0, 1, 1, 1, 1]
        getStandardDOLevel = [0] * 8
        rtn = robot.SetStandardDOLevel(setStandardDOLevel)
        print(f"SetStandardDOLevel rtn is {rtn}")
        rtn, getStandardDOLevel = robot.GetStandardDOLevel()
        print(f"GetStandsrdDOLevel rtn is {rtn}, value is {getStandardDOLevel[0]} {getStandardDOLevel[1]} {getStandardDOLevel[2]} {getStandardDOLevel[3]} {getStandardDOLevel[4]} {getStandardDOLevel[5]} {getStandardDOLevel[6]} {getStandardDOLevel[7]}")

        # Attendi 2 secondi
        time.sleep(2)

        # Chiudi connessione
        robot.CloseRPC()
        time.sleep(1)

    # Chiama la funzione di test
    TestIOConfig(robot)