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

Impostare Reset Uscite DO Box Controllo dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxDO(resetFlag)``"
    "Descrizione", "Imposta reset uscite DO box controllo dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite AO Box Controllo dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetCtlBoxAO(resetFlag)``"
    "Descrizione", "Imposta reset uscite AO box controllo dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite DO Utensile Terminale dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleDO(resetFlag)``"
    "Descrizione", "Imposta reset uscite DO utensile terminale dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite AO Utensile Terminale dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetAxleAO(resetFlag)``"
    "Descrizione", "Imposta reset uscite AO utensile terminale dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite DO Estese dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtDO(resetFlag)``"
    "Descrizione", "Imposta reset uscite DO estese dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite AO Estese dopo Stop/Pausa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetExtAO(resetFlag)``"
    "Descrizione", "Imposta reset uscite AO estese dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：0-nessun reset; 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode"

Impostare Reset Uscite SmartTool dopo Stop/Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOutputResetSmartToolDO(resetFlag)``"
    "Descrizione", "Imposta reset uscite SmartTool dopo stop/pausa"
    "Parametri Obbligatori", "- ``resetFlag``：reset o meno, 0-nessun reset, 1-reset"
    "Parametri Predefiniti", "Nessuno"
    "Valore Ritorno", "Codice errore successo-0 fallimento- errcode "

Esempio Codice Reset Output dopo Stop/Pausa Programma LUA
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilire connessione con controller robot, connessione riuscita ritorna oggetto robot
    robot = Robot.RPC('192.168.58.2')
    for i in range(16):
        robot.SetDO(i, 1, 0, 0)
        time.sleep(0.3)
    resetFlag = 1
    robot.SetOutputResetCtlBoxDO(resetFlag)    
    robot.SetOutputResetCtlBoxAO(resetFlag)    
    robot.SetOutputResetAxleDO(resetFlag)      
    robot.SetOutputResetAxleAO(resetFlag)      
    robot.SetOutputResetExtDO(resetFlag)       
    robot.SetOutputResetExtAO(resetFlag)       
    robot.SetOutputResetSmartToolDO(resetFlag) 
    robot.ProgramLoad("/fruser/test0610.lua")
    robot.ProgramRun()
    robot.CloseRPC()