Registri di Input/Output del Robot
===========================================

Il client CNDE e il robot possono interagire tramite i registri di input e output, includendo due processi specifici:

① La configurazione di input del client CNDE include i registri di input. Durante l'inserimento dei dati, i valori dei registri di input vengono modificati. Il programma LUA del robot aggiunge istruzioni di lettura dei registri di input. Eseguendo il programma LUA, è possibile leggere i valori dei registri di input modificati dal client CNDE.

② Il programma LUA del robot aggiunge istruzioni di scrittura dei registri di output. Eseguendo il programma LUA, i valori vengono scritti nei registri di output. La configurazione di output del client CNDE include i registri di output. Avviando il feedback di stato CNDE del robot, il client riceve i dati di output CNDE e può leggere i valori dei registri di output scritti nel programma LUA.

Lettura dei Registri di Input
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Apri WebApp, clicca in sequenza "Programma di insegnamento", "Programmazione", crea un nuovo programma utente "testReg.lua".

.. image:: cnde/012.png
   :width: 6in
   :align: center

.. centered:: Figura 4-1 Creazione del programma "testReg.lua"

Clicca "Variabili", nella casella di aggiunta istruzioni a destra seleziona "Lettura variabile registro di input", scegli il tipo di variabile "int", indice di partenza registro 0, numero di registri 3, clicca il pulsante "Aggiungi" e poi "Applica".

.. image:: cnde/013.png
   :width: 6in
   :align: center

.. centered:: Figura 4-2 Aggiunta istruzione lettura registro di input

Ora "testReg.lua" ha aggiunto un'istruzione per leggere il registro di input di tipo "int".

.. image:: cnde/014.png
   :width: 6in
   :align: center

.. centered:: Figura 4-3 Aggiunta istruzione lettura registro di input tipo "int"

Clicca il pulsante di cambio modalità, passa alla modalità di modifica programma, aggiungi tre variabili del programma lua prima dell'istruzione di lettura registro di input, per ricevere i tre valori del registro di input letti.

.. image:: cnde/015.png
   :width: 6in
   :align: center

.. centered:: Figura 4-4 Aggiunta lettura valori registro di input

Allo stesso modo, è possibile aggiungere rispettivamente la lettura di dati di registro di tipo "bit" e "double".

.. image:: cnde/016.png
   :width: 6in
   :align: center

.. centered:: Figura 4-5 Aggiunta lettura registri di input tipo "bit" e "double"

Salva il programma sopra, passa il robot in modalità automatica, esegui il programma, i valori dei registri di input verranno letti nelle variabili del programma lua.

Scrittura dei Registri di Output
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Apri WebApp, clicca in sequenza "Programma di insegnamento", "Programmazione", crea un nuovo programma utente "testReg.lua".

.. image:: cnde/017.png
   :width: 6in
   :align: center

.. centered:: Figura 4-6 Creazione del programma "testReg.lua"

Clicca "Variabili", nella casella di aggiunta istruzioni a destra seleziona "Scrittura variabile registro di output", scegli il tipo di variabile "int", indice di partenza registro 0, numero di registri 2, valore registro "18,55", clicca il pulsante "Aggiungi"; poi seleziona di nuovo "Lettura variabile registro di output" scegliendo il tipo di variabile "int", indice di partenza registro 0, numero di registri 2, clicca i pulsanti "Aggiungi" e "Applica".

.. image:: cnde/018.png
   :width: 6in
   :align: center

.. centered:: Figura 4-7 Aggiunta istruzioni lettura/scrittura registro di output

Ora "testReg.lua" ha aggiunto le istruzioni di scrittura e lettura del registro di output di tipo "int".

.. image:: cnde/019.png
   :width: 6in
   :align: center

.. centered:: Figura 4-8 Aggiunta istruzioni scrittura e lettura registro di output tipo "int"

Clicca il pulsante di cambio modalità, passa alla modalità di modifica programma, aggiungi due variabili del programma lua prima dell'istruzione di lettura registro di output, per ricevere i due valori del registro di output letti.

.. image:: cnde/020.png
   :width: 6in
   :align: center

.. centered:: Figura 4-9 Aggiunta lettura valori registro di input

Salva il programma sopra, passa il robot in modalità automatica, esegui il programma. A questo punto le variabili del programma LUA "intValue1" e "intValue2" hanno rispettivamente i valori 18 e 55. Le operazioni sui registri di tipo "bit" e "double" sono uguali a quelle di tipo "int".

Applicazione di Interazione Registri Input/Output CNDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: cnde/021.png
   :width: 4in
   :align: center

.. centered:: Figura 4-10 Interazione dati registri input e output

Gli scenari di interazione dati tra robot e client CNDE attraverso i registri di input e output includono, ma non sono limitati a, i seguenti tipi:

① Controllo del movimento del robot tramite registri di input; il client CNDE pianifica la posizione target del robot, scrive la posizione target del robot nei registri di input; nel programma LUA del robot legge i valori dei registri di input per ottenere la posizione target del robot, poi tramite istruzioni di movimento come PTP, LIN, ServoJ, controlla il movimento del robot verso la posizione target. Programma LUA di esempio:

.. code-block:: lua
    :linenos:

    i = 0;
    oldFlag = 0
    while(1) do
        startFlag = ReadInputINTRegs(0,1)
        if(startFlag ~= oldFlag) then
        oldFlag = startFlag
        x, y, z, a, b, c = ReadInputDBLRegs(0,6)
        ServoJ({x, y, z, a, b, c}, {0, 0, 0, 0}, 10, 10, 0.008, 0, 0)
        end	
    end

② Controllo delle azioni del robot tramite registri di input: il client CNDE scrive valori diversi in un certo registro di input, controllando così diverse azioni del robot. Il programma LUA del robot acquisisce ciclicamente i valori del corrispondente registro di input, in base al valore del registro, esegue azioni diverse. Programma di esempio:

.. code-block:: lua
    :linenos:

    runFlag = ReadInputINTRegs(0,1)
    while(runFlag > 0) do
        motion,target = ReadInputINTRegs(1,2)
        if(motion > 0) then
            if(target == 1)then 
                Lin(a1,100,-1,0,0)
            else if(target == 2) then
                Lin(a2,100,-1,0,0)
            else
                Lin(safety,100,-1,0,0)
            end
            end
        else
            sleep_ms(100)
        end
    end

③ Durante il funzionamento, il robot scrive lo stato corrente del programma nei registri di output. Il client CNDE leggendo lo stato dei registri di output, realizza il monitoraggio dell'esecuzione del programma del robot. Programma di esempio:

.. code-block:: lua
    :linenos:

    local weldCount = 0
    runFlag = ReadInputINTRegs(0,1)
    while(runFlag > 0) do
        Lin(safety,100,-1,0,0)
        Lin(a1,100,-1,0,0)
        ARCStart(0, 0, 3000)
        Lin(a2,100,-1,0,0)
        ARCEnd(0, 0, 3000)
        runFlag = ReadInputINTRegs(0,1)
        weldCount = weldCount + 1
        WriteOutputINTRegs(0,1,{weldCount})
    end