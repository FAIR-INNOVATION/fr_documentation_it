Saldatura
======================

.. toctree:: 
    :maxdepth: 5

Impostazione dei parametri della curva di processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetProcessParam(id, startCurrent, startVoltage, startTime, weldCurrent, weldVoltage, endCurrent, endVoltage, endTime)``"
    "Descrizione", "Imposta i parametri della curva di processo di saldatura"
    "Parametri obbligatori", "
    - ``id``: Numero del processo di saldatura (1-99)
    - ``startCurrent``: Corrente di inizio arco (A)
    - ``startVoltage``: Tensione di inizio arco (V)
    - ``startTime``: Tempo di inizio arco (ms)
    - ``weldCurrent``: Corrente di saldatura (A)
    - ``weldVoltage``: Tensione di saldatura (V)
    - ``endCurrent``: Corrente di fine arco (A)
    - ``endVoltage``: Tensione di fine arco (V)
    - ``endTime``: Tempo di fine arco (ms)
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Recupero dei parametri della curva di processo di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetProcessParam(id)``"
    "Descrizione", "Recupera i parametri della curva di processo di saldatura"
    "Parametri obbligatori", "
    - ``id``: Numero del processo di saldatura (1-99)
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``startCurrent``: Corrente di inizio arco (A)
    - ``startVoltage``: Tensione di inizio arco (V)
    - ``startTime``: Tempo di inizio arco (ms)
    - ``weldCurrent``: Corrente di saldatura (A)
    - ``weldVoltage``: Tensione di saldatura (V)
    - ``endCurrent``: Corrente di fine arco (A)
    - ``endVoltage``: Tensione di fine arco (V)
    - ``endTime``: Tempo di fine arco (ms)
    "

Impostazione della relazione tra corrente di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentRelation(currentMin, currentMax, outputVoltageMin, outputVoltageMax)``"
    "Descrizione", "Imposta la relazione tra corrente di saldatura e uscita analogica"
    "Parametri obbligatori", "- ``currentMin``: Valore di corrente al punto sinistro della relazione lineare corrente di saldatura-uscita analogica (A)
    - ``currentMax``: Valore di corrente al punto destro della relazione lineare corrente di saldatura-uscita analogica (A)
    - ``outputVoltageMin``: Valore di tensione di uscita analogica al punto sinistro della relazione lineare corrente di saldatura-uscita analogica (V)
    - ``outputVoltageMax``: Valore di tensione di uscita analogica al punto destro della relazione lineare corrente di saldatura-uscita analogica (V)
    - ``AOIndex``: Porta di uscita analogica per la corrente di saldatura"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della relazione tra tensione di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageRelation(weldVoltageMin, weldVoltageMax, outputVoltageMin, outputVoltageMax)``"
    "Descrizione", "Imposta la relazione tra tensione di saldatura e uscita analogica"
    "Parametri obbligatori", "- ``weldVoltageMin``: Valore di tensione di saldatura al punto sinistro della relazione lineare tensione di saldatura-uscita analogica (A)
    - ``weldVoltageMax``: Valore di tensione di saldatura al punto destro della relazione lineare tensione di saldatura-uscita analogica (A)
    - ``outputVoltageMin``: Valore di tensione di uscita analogica al punto sinistro della relazione lineare tensione di saldatura-uscita analogica (V)
    - ``outputVoltageMax``: Valore di tensione di uscita analogica al punto destro della relazione lineare tensione di saldatura-uscita analogica (V)
    - ``AOIndex``: Porta di uscita analogica per la tensione di saldatura"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Recupero della relazione tra corrente di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetCurrentRelation()``"
    "Descrizione", "Recupera la relazione tra corrente di saldatura e uscita analogica"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``currentMin``: Valore di corrente al punto sinistro della relazione lineare corrente di saldatura-uscita analogica (A)
    - ``currentMax``: Valore di corrente al punto destro della relazione lineare corrente di saldatura-uscita analogica (A)
    - ``outputVoltageMin``: Valore di tensione di uscita analogica al punto sinistro della relazione lineare corrente di saldatura-uscita analogica (V)
    - ``outputVoltageMax``: Valore di tensione di uscita analogica al punto destro della relazione lineare corrente di saldatura-uscita analogica (V)
    - ``AOIndex``: Porta di uscita analogica per la corrente di saldatura"

Recupero della relazione tra tensione di saldatura e uscita analogica
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetVoltageRelation()``"
    "Descrizione", "Recupera la relazione tra tensione di saldatura e uscita analogica"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``weldVoltageMin``: Valore di tensione di saldatura al punto sinistro della relazione lineare tensione di saldatura-uscita analogica (V)
    - ``weldVoltageMax``: Valore di tensione di saldatura al punto destro della relazione lineare tensione di saldatura-uscita analogica (V)
    - ``outputVoltageMin``: Valore di tensione di uscita analogica al punto sinistro della relazione lineare tensione di saldatura-uscita analogica (V)
    - ``outputVoltageMax``: Valore di tensione di uscita analogica al punto destro della relazione lineare corrente di saldatura-uscita analogica (V)
    - ``AOIndex``: Porta di uscita analogica per la tensione di saldatura"

Impostazione della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrent(ioType, current, AOIndex, blend)``"
    "Descrizione", "Imposta la corrente di saldatura"
    "Parametri obbligatori", "- ``ioType``: Tipo 0-IO del controllore; 1-IO esteso
    - ``current``: Valore della corrente di saldatura (A)
    - ``AOIndex``: Porta di uscita analogica del cabinet di controllo della corrente di saldatura (0-1)
    - ``blend``: Smoothing 0-disabilitato, 1-abilitato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltage(ioType, voltage, AOIndex, blend)``"
    "Descrizione", "Imposta la tensione di saldatura"
    "Parametri obbligatori", "- ``ioType``: Tipo 0-IO del controllore; 1-IO esteso
    - ``voltage``: Valore della tensione di saldatura (V)
    - ``AOIndex``: Porta di uscita analogica del cabinet di controllo della corrente di saldatura (0-1)
    - ``blend``: Smoothing 0-disabilitato, 1-abilitato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione dei parametri di oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveSetPara(weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftRange, weaveRightRange, additionalStayTime, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary, weaveYawAngle, weaveRotAngle)``"
    "Descrizione", "Imposta i parametri di oscillazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero di configurazione dei parametri di saldatura oscillante
    - ``weaveType``: Tipo di oscillazione 0-Oscillazione triangolare piana; 1-Oscillazione triangolare a L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione sinusoidale piana; 5-Oscillazione sinusoidale a L verticale; 6-Oscillazione triangolare verticale; 7-Oscillazione sinusoidale verticale
    - ``weaveFrequency``: Frequenza di oscillazione (Hz)
    - ``weaveIncStayTime``: Modalità di attesa 0-Il periodo non include il tempo di attesa; 1-Il periodo include il tempo di attesa
    - ``weaveRange``: Ampiezza di oscillazione (mm)
    - ``weaveLeftRange``: Lunghezza della corda sinistra per l'oscillazione triangolare verticale (mm)
    - ``weaveRightRange``: Lunghezza della corda destra per l'oscillazione triangolare verticale (mm)
    - ``additionalStayTime``: Tempo di permanenza al punto triangolare verticale per l'oscillazione triangolare verticale (mm)
    - ``weaveLeftStayTime``: Tempo di permanenza a sinistra (ms)
    - ``weaveRightStayTime``: Tempo di permanenza a destra (ms)
    - ``weaveCircleRadio``: Rapporto di ritorno per l'oscillazione circolare (0-100%)
    - ``weaveStationary``: Attesa in posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione è statica durante il tempo di attesa"
    "Parametri predefiniti", "- ``weaveYawAngle``: Angolo di direzione dell'oscillazione (rotazione attorno all'asse Z di oscillazione), unità°, predefinito 0
    - ``weaveRotAngle``: Angolo di direzione dell'oscillazione (rotazione attorno all'asse X di oscillazione), unità°, predefinito 0"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per l'impostazione dei parametri di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
    robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)
    start_current = 0
    start_voltage = 0
    start_time = 0
    weld_current = 0
    weld_voltage = 0
    end_current = 0
    end_voltage = 0
    end_time = 0
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
    print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
    print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")
    rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
    print(f"WeldingSetCurrentRelation rtn is: {rtn}")
    rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
    print(f"WeldingSetVoltageRelation rtn is: {rtn}")
    current_min = 0
    current_max = 0
    vol_min = 0
    vol_max = 0
    output_vmin = 0
    output_vmax = 0
    cur_index = 0
    vol_index = 0
    rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
    print(f"WeldingGetCurrentRelation rtn is: {rtn}")
    print(f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
    print(f"WeldingGetVoltageRelation rtn is: {rtn}")
    print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")
    rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
    print(f"WeldingSetCurrent rtn is: {rtn}")
    time.sleep(3)
    rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
    print(f"WeldingSetVoltage rtn is: {rtn}")
    rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
    print(f"rtn is: {rtn}")
    robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)
    rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
    print(f"WeldingSetCheckArcInterruptionParam {rtn}")
    rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
    print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")
    enable = 0
    length = 0
    velocity = 0
    move_type = 0
    check_enable = 0
    arc_interrupt_time_length = 0
    rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
    print(f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")
    rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
    print(f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")
    robot.SetWeldMachineCtrlModeExtDoNum(17)
    for i in range(5):
        robot.SetWeldMachineCtrlMode(0)
        time.sleep(1)
        robot.SetWeldMachineCtrlMode(1)
        time.sleep(1)
    robot.CloseRPC()

Impostazione immediata dei parametri di oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveOnlineSetPara (weaveNum, weaveType, weaveFrequency, weaveIncStayTime, weaveRange, weaveLeftStayTime, weaveRightStayTime, weaveCircleRadio, weaveStationary)``"
    "Descrizione", "Imposta immediatamente i parametri di oscillazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero di configurazione dei parametri di saldatura oscillante
    - ``weaveType``: Tipo di oscillazione 0-Oscillazione triangolare piana; 1-Oscillazione triangolare a L verticale; 2-Oscillazione circolare in senso orario; 3-Oscillazione circolare in senso antiorario; 4-Oscillazione sinusoidale piana; 5-Oscillazione sinusoidale a L verticale; 6-Oscillazione triangolare verticale; 7-Oscillazione sinusoidale verticale
    - ``weaveFrequency``: Frequenza di oscillazione (Hz)
    - ``weaveIncStayTime``: Modalità di attesa 0-Il periodo non include il tempo di attesa; 1-Il periodo include il tempo di attesa
    - ``weaveRange``: Ampiezza di oscillazione (mm)
    - ``weaveLeftStayTime``: Tempo di permanenza a sinistra (ms)
    - ``weaveRightStayTime``: Tempo di permanenza a destra (ms)
    - ``weaveCircleRadio``: Rapporto di ritorno per l'oscillazione circolare (0-100%)
    - ``weaveStationary``: Attesa in posizione di oscillazione, 0-La posizione continua a muoversi durante il tempo di attesa; 1-La posizione è statica durante il tempo di attesa"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Recupero dei parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetCheckArcInterruptionParam()``"
    "Descrizione", "Recupera i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``checkEnable``: Abilitazione del rilevamento; 0-disabilitato; 1-abilitato
    - ``arcInterruptTimeLength``: Durata di conferma dell'interruzione dell'arco (ms)"

Impostazione dei parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCheckArcInterruptionParam(checkEnable, arcInterruptTimeLength)``"
    "Descrizione", "Imposta i parametri di rilevamento dell'interruzione accidentale dell'arco di saldatura del robot"
    "Parametri obbligatori", "- ``checkEnable``: Abilitazione del rilevamento; 0-disabilitato; 1-abilitato
    - ``arcInterruptTimeLength``: Durata di conferma dell'interruzione dell'arco (ms)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Recupero dei parametri di ripristino dell'interruzione di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingGetReWeldAfterBreakOffParam()``"
    "Descrizione", "Recupera i parametri di ripristino dell'interruzione di saldatura del robot"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``enable``: Abilitazione del ripristino dell'interruzione di saldatura
    - ``length``: Distanza di sovrapposizione della saldatura (mm)
    - ``velocity``: Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    - ``moveType``: Modalità di movimento del robot al punto di riaccensione; 0-LIN; 1-PTP"

Impostazione dei parametri di ripristino dell'interruzione di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetReWeldAfterBreakOffParam(enable, length, velocity, moveType)``"
    "Descrizione", "Imposta i parametri di ripristino dell'interruzione di saldatura del robot"
    "Parametri obbligatori", "- ``enable``: Abilitazione del ripristino dell'interruzione di saldatura
    - ``length``: Distanza di sovrapposizione della saldatura (mm)
    - ``velocity``: Velocità percentuale del robot per tornare al punto di riaccensione (0-100)
    - ``moveType``: Modalità di movimento del robot al punto di riaccensione; 0-LIN; 1-PTP"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della porta DO estesa per la modalità di controllo della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeldMachineCtrlModeExtDoNum(DONum)``"
    "Descrizione", "Imposta la porta DO estesa per la modalità di controllo della saldatrice"
    "Parametri obbligatori", "- ``DONum``: Porta DO per la modalità di controllo della saldatrice (0-127)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della modalità di controllo della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeldMachineCtrlMode(mode, ioType)``"
    "Descrizione", "Imposta modalità di controllo della saldatrice"
    "Parametri Obbligatori", "
    - ``ioType``: Tipo di controllo; 0-IO del box di controllo; 1-Protocollo di comunicazione digitale (UDP); 2-Protocollo di comunicazione digitale (ModbusTCP)
    - ``mode``: Modalità di controllo della saldatrice; 0-Modo unico"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento-errcode"

Ottieni Modalità di Controllo della Saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWeldMachineCtrlMode(self)``"
    "Descrizione", "Ottiene la modalità di controllo della saldatrice"
    "Parametri Obbligatori", "
    - ``mode``: Modalità di controllo della saldatrice; 0-modalità unica CC; 1-modalità unica a impulsi; 2-modalità JOB; 3-modalità controllo locale; 4-modalità separata; 5-modalità CC/CV; 6-TIG; 7-CMT
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore" 

Esempio di Codice per Ottenere la Modalità di Controllo della Saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        robot.WeldingSetProcessParam(1, 177, 27, 1000, 178, 28, 176, 26, 1000)
        robot.WeldingSetProcessParam(2, 188, 28, 555, 199, 29, 133, 23, 333)

        start_current = 0
        start_voltage = 0
        start_time = 0
        weld_current = 0
        weld_voltage = 0
        end_current = 0
        end_voltage = 0
        end_time = 0

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(1)
        print(f"the Num 1 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        error, start_current, start_voltage, start_time, weld_current, weld_voltage, end_current,end_voltage, end_time = robot.WeldingGetProcessParam(2)
        print(f"the Num 2 process param is {start_current} {start_voltage} {start_time} {weld_current} {weld_voltage} {end_current} {end_voltage} {end_time}")

        rtn = robot.WeldingSetCurrentRelation(0, 400, 0, 10, 0)
        print(f"WeldingSetCurrentRelation rtn is: {rtn}")

        rtn = robot.WeldingSetVoltageRelation(0, 40, 0, 10, 1)
        print(f"WeldingSetVoltageRelation rtn is: {rtn}")

        current_min = 0
        current_max = 0
        vol_min = 0
        vol_max = 0
        output_vmin = 0
        output_vmax = 0
        cur_index = 0
        vol_index = 0

        rtn,current_min, current_max, output_vmin, output_vmax, cur_index = robot.WeldingGetCurrentRelation()
        print(f"WeldingGetCurrentRelation rtn is: {rtn}")
        print(
            f"current min {current_min} current max {current_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn,vol_min, vol_max, output_vmin, output_vmax, vol_index = robot.WeldingGetVoltageRelation()
        print(f"WeldingGetVoltageRelation rtn is: {rtn}")
        print(f"vol min {vol_min} vol max {vol_max} output vol min {output_vmin} output vol max {output_vmax}")

        rtn = robot.WeldingSetCurrent(1, 100, 0, 0)
        print(f"WeldingSetCurrent rtn is: {rtn}")

        time.sleep(3)

        rtn = robot.WeldingSetVoltage(1, 10, 0, 0)
        print(f"WeldingSetVoltage rtn is: {rtn}")

        rtn = robot.WeaveSetPara(0, 0, 2.000000, 0, 10.000000, 0.000000, 0.000000, 0, 0, 0, 0, 0,0.0, 60.000000)
        print(f"rtn is: {rtn}")

        robot.WeaveOnlineSetPara(0, 0, 1, 0, 20, 0, 0, 0, 0)

        rtn = robot.WeldingSetCheckArcInterruptionParam(1, 200)
        print(f"WeldingSetCheckArcInterruptionParam {rtn}")

        rtn = robot.WeldingSetReWeldAfterBreakOffParam(1, 5.7, 98.2, 0)
        print(f"WeldingSetReWeldAfterBreakOffParam {rtn}")

        enable = 0
        length = 0
        velocity = 0
        move_type = 0
        check_enable = 0
        arc_interrupt_time_length = 0

        rtn,check_enable, arc_interrupt_time_length = robot.WeldingGetCheckArcInterruptionParam()
        print(
            f"WeldingGetCheckArcInterruptionParam checkEnable {check_enable} arcInterruptTimeLength {arc_interrupt_time_length}")

        rtn,enable, length, velocity, move_type = robot.WeldingGetReWeldAfterBreakOffParam()
        print(
            f"WeldingGetReWeldAfterBreakOffParam enable = {enable}, length = {length}, velocity = {velocity}, moveType = {move_type}")

        robot.SetWeldMachineCtrlModeExtDoNum(17)
        for i in range(5):
            robot.SetWeldMachineCtrlMode(0,1)
            error,getCtrlMode=robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)
            robot.SetWeldMachineCtrlMode(1,1)
            error, getCtrlMode = robot.GetWeldMachineCtrlMode
            print(f"GetWeldMachineCtrlMode = {getCtrlMode}")
            time.sleep(1)

        robot.CloseRPC()

Inizio della saldatura
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ARCStart(ioType, arcNum, timeout)``"
    "Descrizione", "Inizia la saldatura"
    "Parametri obbligatori", "- ``ioType``: Tipo di IO 0-IO del controllore; 1-IO esteso
    - ``arcNum``: Numero del file di configurazione della saldatrice
    - ``timeout``: Tempo di timeout per l'accensione dell'arco"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine della saldatura
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ARCEnd(ioType, arcNum, timeout)``"
    "Descrizione", "Termina la saldatura"
    "Parametri obbligatori", "- ``ioType``: Tipo 0-IO del controllore; 1-IO esteso
    - ``arcNum``: Numero del file di configurazione della saldatrice
    - ``timeout``: Tempo di timeout per l'accensione dell'arco"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Inizio dell'oscillazione
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveStart(weaveNum)``"
    "Descrizione", "Inizia l'oscillazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero di configurazione dei parametri di saldatura oscillante"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine dell'oscillazione
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveEnd(weaveNum)``"
    "Descrizione", "Termina l'oscillazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero di configurazione dei parametri di saldatura oscillante"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Alimentazione del filo in avanti
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetForwardWireFeed(ioType, wireFeed)``"
    "Descrizione", "Alimentazione del filo in avanti"
    "Parametri obbligatori", "- ``ioType``: 0-IO del controllore; 1-IO esteso
    - ``wireFeed``: Controllo dell'alimentazione del filo 0-arresta l'alimentazione; 1-alimenta"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Alimentazione del filo all'indietro
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetReverseWireFeed(ioType, wireFeed)``"
    "Descrizione", "Alimentazione del filo all'indietro"
    "Parametri obbligatori", "- ``ioType``: 0-IO del controllore; 1-IO esteso
    - ``wireFeed``: Controllo dell'alimentazione del filo 0-arresta l'alimentazione; 1-alimenta"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Alimentazione del gas
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAspirated(ioType, airControl)``"
    "Descrizione", "Alimentazione del gas"
    "Parametri obbligatori", "- ``ioType``: 0-IO del controllore; 1-IO esteso
    - ``airControl``: Controllo dell'alimentazione del gas 0-arresta l'alimentazione; 1-alimenta"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione del robot per riprendere la saldatura dopo un'interruzione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingStartReWeldAfterBreakOff()``"
    "Descrizione", "Imposta il robot per riprendere la saldatura dopo un'interruzione"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione del robot per uscire dalla saldatura dopo un'interruzione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingAbortWeldAfterBreakOff()``"
    "Descrizione", "Imposta il robot per uscire dalla saldatura dopo un'interruzione"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per il controllo della saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.SetForwardWireFeed(0, 1)
    time.sleep(1)
    robot.SetForwardWireFeed(0, 0)
    robot.SetReverseWireFeed(0, 1)
    time.sleep(1)
    robot.SetReverseWireFeed(0, 0)
    robot.SetAspirated(0, 1)
    time.sleep(1)
    robot.SetAspirated(0, 0)
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint, tool=13, user=0)
    robot.ARCStart(1, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=p2Desc, tool=13, user=0)
    robot.ARCEnd(1, 0, 10000)
    robot.WeaveEnd(0)
    robot.WeldingStartReWeldAfterBreakOff()
    robot.WeldingAbortWeldAfterBreakOff()
    robot.CloseRPC()

Avvio della saldatura segmentata
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.1

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SegmentWeldStart(startDesePos,  endDesePos, startJPos, endJPos, weldLength, noWeldLength, weldIOType, arcNum, weldTimeout, isWeave,weaveNum,tool,user,vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0,exaxis_pos=[0.0, 0.0, 0.0, 0.0],  search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Descrizione", "Avvia la saldatura segmentata"
    "Parametri obbligatori", "- ``startDesePos``: Posizione cartesiana iniziale, unità [mm][°]
    - ``endDesePos``: Posizione cartesiana target, unità [mm][°]
    - ``startJPos``: Posizione giunto iniziale, unità [°]
    - ``endJPos``: Posizione giunto target, unità [°]
    - ``weldLength``: Lunghezza della saldatura, unità [mm]
    - ``noWeldLength``: Lunghezza non saldata, unità [mm]
    - ``weldIOType``: Tipo di IO per la saldatura (0-IO del cabinet di controllo; 1-IO esteso) arcNum Numero del file di configurazione della saldatrice
    - ``timeout``: Tempo di timeout per lo spegnimento dell'arco
    - ``isWeave``: Saldatura False-non saldare
    - ``weaveNum``: Numero di configurazione dei parametri di saldatura oscillante
    - ``tool``: Numero dello strumento, [0~14]
    - ``user``: Numero del pezzo, [0~14]"
    "Parametri predefiniti", "- ``vel``: Percentuale di velocità, [0~100] predefinito 20.0
    - ``acc``: Accelerazione [0~100] non ancora disponibile predefinito 0.0
    - ``ovl``: Fattore di scala della velocità, [0~100] predefinito 100.0
    - ``blendR``: [-1.0]-movimento fino alla posizione (bloccante), [0~1000]-raggio di smoothing (non bloccante), unità [mm] predefinito -1.0
    - ``exaxis_pos``: Posizione asse esterno 1 ~ Posizione asse esterno 4 predefinito [0.0,0.0,0.0,0.0]
    - ``search``: [0]-nessuna ricerca del filo, [1]-ricerca del filo
    - ``offset_flag``: [0]-nessun offset, [1]-offset nel sistema di coordinate del pezzo/base, [2]-offset nel sistema di coordinate dello strumento predefinito 0
    - ``offset_pos``: Quantità di offset di posizione, unità [mm][°] predefinito [0.0,0.0,0.0,0.0,0.0,0.0]"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per la saldatura segmentata del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.WeldingSetCurrent(1, 230, 0, 0)
    robot.WeldingSetVoltage(1, 24, 0, 1)
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    rtn = robot.SegmentWeldStart(p1Desc, p2Desc, p1Joint, p2Joint, 20, 20, 0, 0, 5000, 0, 0, 0, 0)
    print(f"SegmentWeldStart rtn is {rtn}")
    robot.CloseRPC()

Inizio dell'oscillazione in simulazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveStartSim(weaveNum)``"
    "Descrizione", "Inizia l'oscillazione in simulazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero dei parametri di oscillazione"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine dell'oscillazione in simulazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveEndSim(weaveNum)``"
    "Descrizione", "Termina l'oscillazione in simulazione"
    "Parametri obbligatori", "- ``weaveNum``: Numero dei parametri di oscillazione"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Inizio del rilevamento di preallarme della traiettoria (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveInspectStart(weaveNum)``"
    "Descrizione", "Inizia il rilevamento di preallarme della traiettoria (senza movimento)"
    "Parametri obbligatori", "- ``weaveNum``: Numero dei parametri di oscillazione"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine del rilevamento di preallarme della traiettoria (senza movimento)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveInspectEnd(weaveNum)``"
    "Descrizione", "Termina il rilevamento di preallarme della traiettoria (senza movimento)"
    "Parametri obbligatori", "- ``weaveNum``: Numero dei parametri di oscillazione"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Inizio della variazione graduale dell'oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveChangeStart(weaveChangeFlag, weaveNum, velStart, velEnd)``"
    "Descrizione", "Inizia la variazione graduale dell'oscillazione"
    "Parametri obbligatori", "- ``weaveChangeFlag``: Numero dell'oscillazione 1-cambia parametri di oscillazione; 2-cambia parametri di oscillazione + velocità di saldatura
    - ``weaveNum``: Numero dell'oscillazione
    - ``velStart``: Velocità di inizio saldatura, (cm/min)
    - ``velEnd``: Velocità di fine saldatura, (cm/min)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per la saldatura con variazione graduale dell'oscillazione del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [228.879, -503.594, 453.984, -175.580, 8.293, 171.267]
    p1Joint = [102.700, -85.333, 90.518, -102.365, -83.932, 22.134]
    p2Desc = [-333.302, -435.580, 449.866, -174.997, 2.017, 109.815]
    p2Joint = [41.862, -85.333, 90.526, -100.587, -90.014, 22.135]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveStartSim(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0)
    robot.WeaveEndSim(0)
    robot.MoveJ(joint_pos= p1Joint,tool= 13,user= 0)
    robot.WeaveInspectStart(0)
    robot.MoveL(desc_pos= p2Desc,tool= 13,user= 0,)
    robot.WeaveInspectEnd(0)
    robot.WeldingSetVoltage(1, 19, 0, 0)
    robot.WeldingSetCurrent(1, 190, 0, 0)
    robot.MoveL(desc_pos= p1Desc,tool= 1,user= 1,vel= 100,acc= 100,ovl= 50)
    robot.ARCStart(1, 0, 10000)
    robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(1, 0, 50, 30)
    robot.MoveL(desc_pos= p2Desc,tool= 1,user= 1,vel= 100)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 60, 1, 0.06, 5, 5, 80, 0, 0, 4, 1, 10, 0, 0)
    robot.ARCEnd(1, 0, 10000)
    robot.CloseRPC()

Fine della variazione graduale dell'oscillazione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeaveChangeEnd()``"
    "Descrizione", "Termina la variazione graduale dell'oscillazione"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di rilevamento del gas della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAirControlExtDoNum(DONum)``"
    "Descrizione", "IO esteso - Configura il segnale di rilevamento del gas della saldatrice"
    "Parametri obbligatori", "
    - ``DONum``: Numero DO esteso per il segnale di rilevamento del gas
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di accensione dell'arco della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcStartExtDoNum(DONum)``"
    "Descrizione", "IO esteso - Configura il segnale di accensione dell'arco della saldatrice"
    "Parametri obbligatori", "
    - ``DONum``: Numero DO esteso per il segnale di rilevamento del gas
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di alimentazione del filo all'indietro della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireReverseFeedExtDoNum(DONum)``"
    "Descrizione", "IO esteso - Configura il segnale di alimentazione del filo all'indietro della saldatrice"
    "Parametri obbligatori", "
    - ``DONum``: Numero DO esteso per il segnale di rilevamento del gas
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di alimentazione del filo in avanti della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireForwardFeedExtDoNum(DONum)``"
    "Descrizione", "IO esteso - Configura il segnale di alimentazione del filo in avanti della saldatrice"
    "Parametri obbligatori", "
    - ``DONum``: Numero DO esteso per il segnale di rilevamento del gas
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di accensione dell'arco riuscita della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcDoneExtDiNum(DINum)``"
    "Descrizione", "IO esteso - Configura il segnale di accensione dell'arco riuscita della saldatrice"
    "Parametri obbligatori", "
    - ``DINum``: Numero DI esteso per il segnale di pronto della saldatrice
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di pronto della saldatrice
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetArcDoneExtDiNum(DINum)``"
    "Descrizione", "IO esteso - Configura il segnale di pronto della saldatrice"
    "Parametri obbligatori", "
    - ``DINum``: Numero DI esteso per il segnale di pronto della saldatrice
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

IO esteso - Configurazione del segnale di ripristino dell'interruzione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExtDIWeldBreakOffRecover(reWeldDINum, abortWeldDINum)``"
    "Descrizione", "IO esteso - Configura il segnale di ripristino dell'interruzione di saldatura"
    "Parametri obbligatori", "
    - ``reWeldDINum``: Numero DI esteso per il segnale di ripresa della saldatura dopo l'interruzione
    - ``abortWeldDINum``: Numero DI esteso per il segnale di uscita dalla saldatura dopo l'interruzione
    "
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per l'impostazione del segnale di saldatura IO esteso
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.SetArcStartExtDoNum(10)
    print(f"SetArcStartExtDoNum rtn is {rtn}")
    rtn = robot.SetAirControlExtDoNum(20)
    print(f"SetAirControlExtDoNum rtn is {rtn}")
    rtn = robot.SetWireForwardFeedExtDoNum(30)
    print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")
    rtn = robot.SetWireReverseFeedExtDoNum(40)
    rtn = robot.SetWeldReadyExtDiNum(50)
    print(f"SetWeldReadyExtDiNum rtn is {rtn}")
    rtn = robot.SetArcDoneExtDiNum(60)
    print(f"SetArcDoneExtDiNum rtn is {rtn}")
    rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
    print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")
    rtn = robot.SetWireSearchExtDIONum(0, 1)
    print(f"SetWireSearchExtDIONum rtn is {rtn}")
    robot.CloseRPC()

Ottieni Configurazione Funzione DI Estesa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExtDIConfig(self)``"
    "Descrizione", "Ottiene la configurazione della funzione DI estesa"
    "Parametri Obbligatori", "
    - ``DIConfig``: Configurazione input DI esteso; DIConfig[0]-porta DI estesa pronta saldatrice
    - ``DIConfig[1]``: Porta DI estesa avvio arco riuscito
    - ``DIConfig[2]``: Porta DI estesa ripresa interruzione saldatura
    - ``DIConfig[3]``: Porta DI estesa uscita interruzione saldatura
    - ``DIConfig[4]``: Porta DI estesa ricerca filo riuscita
    - ``DIConfig[5]``: Porta DI estesa stato funzionamento saldatrice laser
    - ``DIConfig[6]``: Porta DI estesa stato guasto saldatrice laser
    - ``DIConfig[7-15]``: Riservati
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore" 

Ottieni Configurazione Funzione DO Estesa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetExtDOConfig(self)``"
    "Descrizione", "Ottiene la configurazione della funzione DO estesa"
    "Parametri Obbligatori", "
    - ``DOConfig``: Configurazione output DO esteso; DOConfig[0]-porta DO estesa avvio arco saldatrice
    - ``DOConfig[1]``: Porta DO estesa rilevamento gas
    - ``DOConfig[2]``: Porta DO estesa alimentazione filo in avanti
    - ``DOConfig[3]``: Porta DO estesa alimentazione filo all'indietro
    - ``DOConfig[4]``: Porta DO estesa ricerca filo
    - ``DOConfig[5]``: Porta DO estesa modalità controllo saldatrice
    - ``DOConfig[6]``: Porta DO estesa abilitazione saldatrice laser
    - ``DOConfig[7]``: Porta DO estesa avvio saldatrice laser (emissione laser)
    - ``DOConfig[8]``: Porta DO estesa reset saldatrice laser
    - ``DOConfig[9-15]``: Riservati
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore" 

Esempio di Codice per Ottenere DI/DO Estesi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-V3.9.8

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

    rtn = robot.SetArcStartExtDoNum(10)
        print(f"SetArcStartExtDoNum rtn is {rtn}")

        rtn = robot.SetAirControlExtDoNum(20)
        print(f"SetAirControlExtDoNum rtn is {rtn}")

        rtn = robot.SetWireForwardFeedExtDoNum(30)
        print(f"SetWireForwardFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWireReverseFeedExtDoNum(40)
        print(f"SetWireReverseFeedExtDoNum rtn is {rtn}")

        rtn = robot.SetWeldReadyExtDiNum(50)
        print(f"SetWeldReadyExtDiNum rtn is {rtn}")

        rtn = robot.SetArcDoneExtDiNum(60)
        print(f"SetArcDoneExtDiNum rtn is {rtn}")

        rtn = robot.SetExtDIWeldBreakOffRecover(70, 80)
        print(f"SetExtDIWeldBreakOffRecover rtn is {rtn}")

        rtn = robot.SetWireSearchExtDIONum(0, 1)
        print(f"SetWireSearchExtDIONum rtn is {rtn}")

        rtn, DIConfig = robot.GetExtDIConfig()
        print(f"GetExtDIConfig rtn is {rtn}")
        print(f"welder ready {DIConfig[0]}")
        print(f"arc done {DIConfig[1]}")
        print(f"reweld start {DIConfig[2]}")
        print(f"abort reweld {DIConfig[3]}")
        print(f"wiresearch done {DIConfig[4]}")
        print(f"Laser welding State {DIConfig[5]}")
        print(f"laser welding error state {DIConfig[6]}")

        rtn, DOConfig = robot.GetExtDOConfig()
        print(f"GetExtDOConfig rtn is {rtn}")
        print(f"Arc Start {DOConfig[0]}")
        print(f"Air Test {DOConfig[1]}")
        print(f"Wire forward {DOConfig[2]}")
        print(f"Wire Inverse {DOConfig[3]}")
        print(f"wiresearch {DOConfig[4]}")
        print(f"Weld Mode {DOConfig[5]}")
        print(f"laser Enable {DOConfig[6]}")
        print(f"Laser On {DOConfig[7]}")
        print(f"Laser Reset Error {DOConfig[8]}")

        robot.CloseRPC()

Controllo del tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.9-3.7.9

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceControl(flag,delaytime, isLeftRight, klr, tStartLr, stepMaxLr, sumMaxLr, isUpLow, kud, tStartUd, stepMaxUd, sumMaxUd, axisSelect, referenceType, referSampleStartUd, referSampleCountUd, referenceCurrent, offsetType, offsetParameter)``"
    "Descrizione", "Controllo del tracciamento dell'arco"
    "Parametri obbligatori", "- ``flag``: Interruttore, 0-off; 1-on
    - ``delayTime``: Tempo di ritardo, unità ms
    - ``isLeftRight``: Compensazione deviazione sinistra-destra 0-disabilitata, 1-abilitata
    - ``klr``: Coefficiente di regolazione sinistra-destra (sensibilità)
    - ``tStartLr``: Tempo di inizio compensazione sinistra-destra cyc
    - ``stepMaxLr``: Compensazione massima per ciclo sinistra-destra mm
    - ``sumMaxLr``: Compensazione totale massima sinistra-destra mm
    - ``isUpLow``: Compensazione deviazione alto-basso 0-disabilitata, 1-abilitata
    - ``kud``: Coefficiente di regolazione alto-basso (sensibilità)
    - ``tStartUd``: Tempo di inizio compensazione alto-basso cyc
    - ``stepMaxUd``: Compensazione massima per ciclo alto-basso mm
    - ``sumMaxUd``: Compensazione totale massima alto-basso
    - ``axisSelect``: Selezione sistema coordinate alto-basso, 0-oscillazione; 1-strumento; 2-base
    - ``referenceType``: Metodo di impostazione corrente di riferimento alto-basso, 0-feedback; 1-costante
    - ``referSampleStartUd``: Conteggio inizio campionamento corrente di riferimento alto-basso (feedback), cyc
    - ``referSampleCountUd``: Conteggio cicli campionamento corrente di riferimento alto-basso (feedback), cyc
    - ``referenceCurrent``: Corrente di riferimento alto-basso mA
    - ``offsetType``: Tipo di tracciamento offset, 0-nessun offset; 1-campionamento; 2-percentuale
    - ``offsetParameter``: Parametro offset; campionamento (tempo di inizio campionamento offset, predefinito campiona un ciclo); percentuale (percentuale offset (-100 ~ 100))"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Selezione canale AI banda passante per il tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceExtAIChannelConfig(channel)``"
    "Descrizione", "Selezione canale AI banda passante per il tracciamento dell'arco"
    "Parametri obbligatori", "- ``channel``: Selezione canale AI banda passante per il tracciamento dell'arco,[0-3]"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Avvio del tracciamento dell'arco + compensazione multi-strato/multi-passo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceReplayStart()``"
    "Descrizione", "Avvio del tracciamento dell'arco + compensazione multi-strato/multi-passo"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine del tracciamento dell'arco + compensazione multi-strato/multi-passo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceReplayEnd()``"
    "Descrizione", "Fine del tracciamento dell'arco + compensazione multi-strato/multi-passo"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Trasformazione coordinate offset - Saldatura multi-strato/multi-passo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``MultilayerOffsetTrsfToBase(pointo, pointX, pointZ, dx, dy, db)``"
    "Descrizione", "Trasformazione coordinate offset - Saldatura multi-strato/multi-passo"
    "Parametri obbligatori", "- ``pointo``: Posizione cartesiana del punto di riferimento
    - ``pointX``: Posizione cartesiana del punto nella direzione di offset X dal punto di riferimento
    - ``pointZ``: Posizione cartesiana del punto nella direzione di offset Z dal punto di riferimento
    - ``dx``: Quantità di offset direzione x (mm)
    - ``dz``: Quantità di offset direzione z (mm)
    - ``dry``: Quantità di offset rotazione attorno all'asse y (°)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``offset``: Risultato calcolato dell'offset"

Esempio di codice per il tracciamento dell'arco in saldatura multi-strato/multi-passo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    mulitilineorigin1_joint = [-24.090, -63.501, 84.288, -111.940, -93.426, 57.669]
    mulitilineorigin1_desc = [-677.559, 190.951, -1.205, 1.144, -41.482, -82.577]
    mulitilineX1_desc = [-677.556, 211.949, -1.206]
    mulitilineZ1_desc = [-677.564, 190.956, 19.817]
    mulitilinesafe_joint = [-25.734, -63.778, 81.502, -108.975, -93.392, 56.021]
    mulitilinesafe_desc = [-677.561, 211.950, 19.812, 1.144, -41.482, -82.577]
    mulitilineorigin2_joint = [-29.743, -75.623, 101.241, -116.354, -94.928, 55.735]
    mulitilineorigin2_desc = [-563.961, 215.359, -0.681, 2.845, -40.476, -87.443]
    mulitilineX2_desc = [-563.965, 220.355, -0.680]
    mulitilineZ2_desc = [-563.968, 215.362, 4.331]
    epos = [0, 0, 0, 0]
    offset = [0, 0, 0, 0, 0, 0]
    time.sleep(0.01)
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error = robot.WeaveStart(0)
    print(f"WeaveStart return: {error}")
    error = robot.ArcWeldTraceControl(1, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 1,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceControl(0, 0, 1, 0.06, 5, 5, 50, 1, 0.06, 5, 5, 55, 0, 0, 4, 1, 10,0,0)
    print(f"ArcWeldTraceControl return: {error}")
    error = robot.WeaveEnd(0)
    print(f"WeaveEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error,offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 10.0, 0.0, 0.0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 10, 0, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 10000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin1_desc[:3], mulitilineX1_desc, mulitilineZ1_desc, 0, 10, 0)
    print(f"MultilayerOffsetTrsfToBase return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin1_desc,tool= 13,user= 0,vel= 10,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ARCStart(1, 0, 3000)
    print(f"ARCStart return: {error}")
    error, offset = robot.MultilayerOffsetTrsfToBase(mulitilineorigin2_desc[:3], mulitilineX2_desc, mulitilineZ2_desc, 0, 10, 0)
    error = robot.ArcWeldTraceReplayStart()
    print(f"ArcWeldTraceReplayStart return: {error}")
    error = robot.MoveL(desc_pos= mulitilineorigin2_desc,tool= 13,user= 0,vel= 2,speedPercent=100)
    print(f"MoveL return: {error}")
    error = robot.ArcWeldTraceReplayEnd()
    print(f"ArcWeldTraceReplayEnd return: {error}")
    error = robot.ARCEnd(1, 0, 3000)
    print(f"ARCEnd return: {error}")
    error = robot.MoveJ(joint_pos= mulitilinesafe_joint,tool= 13,user= 0,vel= 10)
    print(f"MoveJ return: {error}")
    robot.CloseRPC()

Selezione canale AI per il feedback della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceAIChannelCurrent(channel)``"
    "Descrizione", "Selezione canale AI per il feedback della corrente della saldatrice nel tracciamento dell'arco"
    "Parametri obbligatori", "- ``channel``: Canale; 0-AI esteso0; 1-AI esteso1; 2-AI esteso2; 3-AI esteso3; 4-AI cabinet di controllo0; 5-AI cabinet di controllo1"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Selezione canale AI per il feedback della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceAIChannelVoltage(channel)``"
    "Descrizione", "Selezione canale AI per il feedback della tensione della saldatrice nel tracciamento dell'arco"
    "Parametri obbligatori", "- ``channel``: Canale; 0-AI esteso0; 1-AI esteso1; 2-AI esteso2; 3-AI esteso3; 4-AI cabinet di controllo0; 5-AI cabinet di controllo1"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Parametri di conversione per il feedback della corrente della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceCurrentPara(AILow, AIHigh, currentLow, currentHigh)``"
    "Descrizione", "Parametri di conversione per il feedback della corrente della saldatrice nel tracciamento dell'arco"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "- ``AILow``: Limite inferiore canale AI, valore predefinito 0V, intervallo [0-10V]
    - ``AIHigh``: Limite superiore canale AI, valore predefinito 10V, intervallo [0-10V]
    - ``currentLow``: Valore di corrente della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, intervallo [0-200V]
    - ``currentHigh``: Valore di corrente della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, intervallo [0-200V]"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Parametri di conversione per il feedback della tensione della saldatrice nel tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ArcWeldTraceVoltagePara(AILow, AIHigh, voltageLow, voltageHigh)``"
    "Descrizione", "Parametri di conversione per il feedback della tensione della saldatrice nel tracciamento dell'arco"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "- ``AILow``: Limite inferiore canale AI, valore predefinito 0V, intervallo [0-10V]
    - ``AIHigh``: Limite superiore canale AI, valore predefinito 10V, intervallo [0-10V]
    - ``voltageLow``: Valore di tensione della saldatrice corrispondente al limite inferiore del canale AI, valore predefinito 0V, intervallo [0-200V]
    - ``voltageHigh``: Valore di tensione della saldatrice corrispondente al limite superiore del canale AI, valore predefinito 100V, intervallo [0-200V]"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per il tracciamento dell'arco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')

    safetydescPose = [-504.043,275.181,40.908,-28.002,-42.025,-14.044]
    safetyjointPos = [-39.078,-76.732,87.227,-99.47,-94.301,18.714]
    startdescPose = [-473.86,257.879,-20.849,-37.317,-42.021,2.543]
    startjointPos = [-43.487,-76.526,95.568,-104.445,-89.356,3.72]
    enddescPose = [-499.844,141.225,7.72,-34.856,-40.17,13.13]
    endjointPos = [-31.305,-82.998,99.401,-104.426,-89.35,3.696]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----Imposta tensione
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----Imposta corrente
    rtn = robot.ArcWeldTraceAIChannelCurrent(4)
    print("ArcWeldTraceAIChannelCurrent rtn is", rtn)
    rtn = robot.ArcWeldTraceAIChannelVoltage(5)
    print("ArcWeldTraceAIChannelVoltage rtn is", rtn)
    rtn = robot.ArcWeldTraceCurrentPara(0, 5, 0, 500)
    print("ArcWeldTraceCurrentPara rtn is", rtn)
    rtn = robot.ArcWeldTraceVoltagePara(1.018, 10, 0, 50)
    print("ArcWeldTraceVoltagePara rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=20, acc=100)
    robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl= 2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.MoveJ(joint_pos=safetyjointPos, tool=1, user=0, vel=20, acc=100)

Impostazione della porta IO estesa per la ricerca del filo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWireSearchExtDIONum(searchDoneDINum, searchStartDONum)``"
    "Descrizione", "Imposta la porta IO estesa per la ricerca del filo"
    "Parametri obbligatori", "- ``searchDoneDINum``: Porta DO per ricerca del filo riuscita (0-127)
    - ``searchStartDONum``: Porta DO per controllo avvio/arresto ricerca del filo (0-127)"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice
++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 50, 5, 50, 1, 50, 10)
    robot.ExtDevLoadUDPDriver()
    robot.SetWireSearchExtDIONum(0, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Inizio della ricerca del filo
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchStart(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Descrizione", "Inizia la ricerca del filo"
    "Parametri obbligatori", "- ``refPos``: 1-punto di riferimento 0-punto di contatto
    - ``searchVel``: Velocità di ricerca %
    - ``searchDis``: Distanza di ricerca mm
    - ``autoBackFlag``: Flag ritorno automatico, 0-non automatico; -automatico
    - ``autoBackVel``: Velocità di ritorno automatico %
    - ``autoBackDis``: Distanza di ritorno automatico mm
    - ``offectFlag``: 1-ricerca con offset; 0-ricerca nel punto insegnato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Fine della ricerca del filo
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchEnd(refPos,searchVel,searchDis,autoBackFlag,autoBackVel,autoBackDis,offectFlag)``"
    "Descrizione", "Termina la ricerca del filo"
    "Parametri obbligatori", "- ``refPos``: 1-punto di riferimento 2-punto di contatto
    - ``searchVel``: Velocità di ricerca %
    - ``searchDis``: Distanza di ricerca mm
    - ``autoBackFlag``: Flag ritorno automatico, 0-non automatico; -automatico
    - ``autoBackVel``: Velocità di ritorno automatico %
    - ``autoBackDis``: Distanza di ritorno automatico mm
    - ``offectFlag``: 1-ricerca con offset; 2-ricerca nel punto insegnato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo dell'offset della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWireSearchOffset(seamType, method,varNameRef,varNameRes)``"
    "Descrizione", "Calcola l'offset della ricerca del filo"
    "Parametri obbligatori", "- ``seamType``: Tipo di giunto
    - ``method``: Metodo di calcolo
    - ``varNameRef``: Punto di riferimento 1-6, # indica nessuna variabile punto
    - ``varNameRes``: Punto di contatto 1-6, # indica nessuna variabile punto"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``offsetFlag``: 0-l'offset si somma direttamente al punto di comando; 1-l'offset richiede una trasformazione di coordinate per il punto di comando
    - ``offset``: Posizione offset [x, y, z, a, b, c]"

Attesa del completamento della ricerca del filo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WireSearchWait(varname)``"
    "Descrizione", "Attende il completamento della ricerca del filo"
    "Parametri obbligatori", "- ``varName``: Nome del punto di contatto “RES0” ~ “RES99”"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Scrittura del punto di contatto della ricerca del filo nel database
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetPointToDatabase(varName,pos)``"
    "Descrizione", "Scrive il punto di contatto della ricerca del filo nel database"
    "Parametri obbligatori", "- ``varName``: Nome del punto di contatto “RES0” ~ “RES99”
    - ``pos``: Dati del punto di contatto [x, y, x, a, b, c]"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per la ricerca del filo del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    toolCoord = [0, 0, 200, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    wobjCoord = [0, 0, 0, 0, 0, 0]
    robot.SetWObjCoord(1, wobjCoord, 0)
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    descStart = [216.543, 445.175, 93.465, 179.683, 1.757, -112.641]
    jointStart = [-128.345, -86.660, 114.679, -119.625, -89.219, 74.303]
    descEnd = [111.143, 523.384, 87.659, 179.703, 1.835, -97.750]
    jointEnd = [-113.454, -81.060, 109.328, -119.954, -89.218, 74.302]
    error = robot.MoveL(desc_pos=descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descEnd,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    descREF0A = [142.135, 367.604, 86.523, 179.728, 1.922, -111.089]
    jointREF0A = [-126.794, -100.834, 128.922, -119.864, -89.218, 74.302]
    descREF0B = [254.633, 463.125, 72.604, 179.845, 2.341, -114.704]
    jointREF0B = [-130.413, -81.093, 112.044, -123.163, -89.217, 74.303]
    descREF1A = [92.556, 485.259, 47.476, -179.932, 3.130, -97.512]
    jointREF1A = [-113.231, -83.815, 119.877, -129.092, -89.217, 74.303]
    descREF1B = [203.103, 583.836, 63.909, 179.991, 2.854, -103.372]
    jointREF1B = [-119.088, -69.676, 98.692, -121.761, -89.219, 74.303]
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos=descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos=descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("REF1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF0A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF0B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES0")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    error = robot.WireSearchStart(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchStart return: {error}")
    error = robot.MoveL(desc_pos= descREF1A,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descREF1B,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.WireSearchWait("RES1")
    print(f"WireSearchWait return: {error}")
    error = robot.WireSearchEnd(0, 10, 100, 0, 10, 100, 0)
    print(f"WireSearchEnd return: {error}")
    varNameRef = ["REF0", "REF1", "#", "#", "#", "#"]
    varNameRes = ["RES0", "RES1", "#", "#", "#", "#"]
    offectFlag = 0
    offectPos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    error, offectFlag, offectPos = robot.GetWireSearchOffset(0, 0, varNameRef, varNameRes)
    print(f"GetWireSearchOffset return: {error}")
    error = robot.PointsOffsetEnable(0, offectPos)
    print(f"PointsOffsetEnable return: {error}")
    error = robot.MoveL(desc_pos= descStart,tool= 1,user= 1,vel= 100)
    print(f"MoveL return: {error}")
    error = robot.MoveL(desc_pos= descEnd,tool= 1,user= 1,vel= 100,search=1)
    print(f"MoveL return: {error}")
    error = robot.PointsOffsetDisable()
    robot.CloseRPC()

Impostazione dell'inizio della variazione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageGradualChangeStart(IOType, voltageStart, voltageEnd, AOIndex, blend)``"
    "Descrizione", "Imposta l'inizio della variazione graduale della tensione di saldatura"
    "Parametri obbligatori", "- ``IOType``: Tipo di controllo; 0-IO cabinet di controllo; 1-Protocollo di comunicazione digitale (UDP);2-Protocollo di comunicazione digitale (ModbusTCP)
    - ``voltageStart``: Tensione di saldatura iniziale (V)
    - ``voltageEnd``: Tensione di saldatura finale (V)
    - ``AOIndex``: Numero porta AO cabinet di controllo (0-1)
    - ``blend``: Smoothing 0-disabilitato; 1-abilitato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della fine della variazione graduale della tensione di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetVoltageGradualChangeEnd()``"
    "Descrizione", "Imposta la fine della variazione graduale della tensione di saldatura"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione dell'inizio della variazione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentGradualChangeStart(IOType, currentStart, currentEnd, AOIndex, blend)``"
    "Descrizione", "Imposta l'inizio della variazione graduale della corrente di saldatura"
    "Parametri obbligatori", "- ``IOType``: Tipo di controllo; 0-IO cabinet di controllo; 1-Protocollo di comunicazione digitale (UDP);2-Protocollo di comunicazione digitale (ModbusTCP)
    - ``currentStart``: Corrente di saldatura iniziale (A)
    - ``currentEnd``: Corrente di saldatura finale (A)
    - ``AOIndex``: Numero porta AO cabinet di controllo (0-1)
    - ``blend``: Smoothing 0-disabilitato; 1-abilitato"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione della fine della variazione graduale della corrente di saldatura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WeldingSetCurrentGradualChangeEnd()``"
    "Descrizione", "Imposta la fine della variazione graduale della corrente di saldatura"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice per la variazione graduale di corrente e tensione di saldatura del robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    startdescPose = [-484.707, 276.996, -14.013, -37.657, -40.508, -1.548]
    startjointPos = [-45.421, -75.673, 93.627, -104.302, -87.938, 6.005]
    enddescPose = [-508.767, 137.109, -13.966, -37.639, -40.508, -1.559]
    endjointPos = [-32.768, -80.947, 100.254, -106.201, -87.201, 18.648]
    safedescPose = [-484.709, 294.436, 13.621, -37.660, -40.508, -1.545]
    safejointPos = [-46.604, -75.410, 89.109, -100.003, -88.012, 4.823]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    robot.WeldingSetCurrentRelation(0, 495, 1, 10, 0)
    robot.WeldingSetVoltageRelation(10, 45, 1, 10, 1)
    robot.WeldingSetVoltage(0, 25, 1, 0)  # ----Imposta tensione
    robot.WeldingSetCurrent(0, 260, 0, 0)  # ----Imposta corrente
    robot.MoveJ(joint_pos=safejointPos, tool=1, user=0, vel=5, acc=100)
    rtn = robot.WeldingSetCurrentGradualChangeStart(0, 260, 220, 0, 0)
    print("WeldingSetCurrentGradualChangeStart rtn is", rtn)
    rtn = robot.WeldingSetVoltageGradualChangeStart(0, 25, 22, 1, 0)
    print("WeldingSetVoltageGradualChangeStart rtn is", rtn)
    rtn = robot.ArcWeldTraceControl(1, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    print("ArcWeldTraceControl rtn is", rtn)
    robot.MoveJ(joint_pos=startjointPos, tool=1, user=0, vel=5, acc=100)
    robot.ARCStart(0, 0, 10000)
    robot.WeaveStart(0)
    robot.WeaveChangeStart(2, 1, 24, 36)
    robot.MoveL(desc_pos=enddescPose, tool=1, user=0, vel=100, ovl=2, acc=100)
    robot.ARCEnd(0, 0, 10000)
    robot.WeaveChangeEnd()
    robot.WeaveEnd(0)
    robot.ArcWeldTraceControl(0, 0, 1, 0.08, 5, 5, 300, 1, 0.06, 4, 4, 300, 1, 0, 4, 1, 10, 0, 0)
    robot.WeldingSetCurrentGradualChangeEnd()
    robot.WeldingSetVoltageGradualChangeEnd()

Impostazione dei parametri di oscillazione personalizzata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomWeaveSetPara(id, pointNum, point, stayTime, frequency, incStayType, stationary)``"
    "Descrizione", "Imposta i parametri di oscillazione personalizzata"
    "Parametri obbligatori", "- ``id``: Numero dell'oscillazione personalizzata: 0-2
    - ``pointNum``: Numero di punti dell'oscillazione 0-10
    - ``point``: Dati dei punti di movimento x,y,z
    - ``stayTime``: Tempo di permanenza dell'oscillazione ms
    - ``frequency``: Frequenza di oscillazione Hz
    - ``incStayType``: Modalità di attesa: 0-Il periodo non include il tempo di attesa; 1-Il periodo include il tempo di attesa
    - ``stationary``: Attesa in posizione di oscillazione: 0-Il movimento continua durante il tempo di attesa; 1-La posizione è statica durante il tempo di attesa"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "Codice di errore Successo-0  Fallimento- errcode"

Recupero dei parametri di oscillazione personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.6

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``CustomWeaveGetPara(id)``"
    "Descrizione", "Recupera i parametri di oscillazione personalizzata"
    "Parametri obbligatori", "- ``id``: Numero dell'oscillazione personalizzata: 0-2"
    "Parametri predefiniti", "Nessuno"
    "Valore restituito", "- Codice di errore Successo-0  Fallimento- errcode
    - ``pointNum``: Numero di punti dell'oscillazione 0-10
    - ``point``: Dati dei punti di movimento x,y,z
    - ``stayTime``: Tempo di permanenza dell'oscillazione ms
    - ``frequency``: Frequenza di oscillazione Hz
    - ``incStayType``: Modalità di attesa: 0-Il periodo non include il tempo di attesa; 1-Il periodo include il tempo di attesa
    - ``stationary``: Attesa in posizione di oscillazione: 0-Il movimento continua durante il tempo di attesa; 1-La posizione è statica durante il tempo di attesa"

Esempio di codice per i parametri di oscillazione personalizzata
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Connessione al controller del robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    point = [0.0] * 30
    point[0] = -3.0
    point[1] = -3.0
    point[2] = 0.0
    point[3] = -6.0
    point[4] = 0.0
    point[5] = 0.0
    point[6] = -3.0
    point[7] = 3.0
    point[8] = 0.0
    point[9] = 0.0
    point[10] = 0.0
    point[11] = 0.0
    stayTime = [0.0] * 10
    rtn = robot.CustomWeaveSetPara(2, 4, point, stayTime, 1.000, 0, 0)
    print(f"CustomWeaveSetPara rtn is {rtn}")
    time.sleep(1)
    pointNum = 0
    frequency = 0.0
    incStayType = 0
    stationary = 0
    rtn, pointNum, point, stayTime, frequency, incStayType, stationary = robot.CustomWeaveGetPara(2)
    print(f"pointNum is {pointNum}")
    for i in range(pointNum):
        print(f"point {i}, point x y z {point[i * 3 + 0]},{point[i * 3 + 1]},{point[i * 3 + 2]}")
    print(f"fre is {frequency}, stay is {incStayType},{stationary}")
    robot.WeaveSetPara(0, 9, 1.000000, 1, 5.000000, 6.000000, 5.000000, 50, 100, 100, 0, 1, 0.000000, 0.000000)
    desc_p1 = [-288.650, 367.807, 288.404, 0.000, -0.001, 0.001]
    desc_p2 = [-431.714, 367.815, 288.415, 0.001, 0.001, 0.000]
    desc_p3 = [-348.666, 427.798, 288.404, -0.000, -0.000, 0.001]
    j1 = [140.656, -84.560, -91.707, -93.734, 90.000, 50.655]
    j2 = [149.873, -98.298, -77.599, -94.103, 90.000, 59.873]
    j3 = [139.773, -96.173, -80.014, -93.814, 90.000, 49.772]
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.Circle(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50, oacc=10)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveC(desc_pos_p=desc_p3, tool_p=3, user_p=0, vel_p=50, desc_pos_t=desc_p2, tool_t=3, user_t=0, vel_t=50)
    robot.WeaveEnd(0)
    robot.MoveJ(joint_pos=j1, tool=3, user=0, vel=100)
    robot.WeaveStart(0)
    robot.MoveL(desc_pos=desc_p2, tool=3, user=0, vel=100, ovl=10, speedPercent=100)
    robot.WeaveEnd(0)
    robot.CloseRPC()

Configurazione Parametri Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingParam(self, num, scanSpeed, scanWidth, peakPower, dutyCycle, Freq, io_type=1)``"
    "Descrizione", "Scrive i parametri di configurazione di uno dei 10 gruppi processo della saldatrice laser e li configura alla saldatrice"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``Num``: Numero gruppo da impostare (1~10)
    - ``scanSpeed``: Velocità di scansione
    - ``scanWidth``: Larghezza di scansione
    - ``peakPower``: Potenza di picco
    - ``dutyCycle``: Ciclo di lavoro
    - ``Freq``: Frequenza
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Avvio/Arresto Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingStartEnd(self, status, io_type=1, max_waittime=10000)``"
    "Descrizione", "Avvia/arresta la saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``status``: Parola di controllo 0-laser spento 1-laser acceso
    - ``max_waittime``: Tempo massimo di attesa
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Abilitazione/Disabilitazione Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingEnable(self, status, io_type=1)``"
    "Descrizione", "Abilita/disabilita saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``status``: 0-disabilita 1-abilita
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Reset Guasto Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ResetLaserWeldingErr(self,status, io_type=1)``"
    "Descrizione", "Reset guasto saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``status``: Parola di controllo 0-invalido 1-reset guasto
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere Stato Operativo Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingRunningState(self, io_type=1)``"
    "Descrizione", "Ottiene lo stato operativo della saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``status``: Parola di controllo 0-fermo 1-in funzione
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere Stato Guasto Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingErrState(self, io_type=1)``"
    "Descrizione", "Ottiene lo stato guasto della saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``status``: 0-nessun guasto 1-guasto presente
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere Parametri di Configurazione Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingParamTarget(self, num)``"
    "Descrizione", "Ottiene i parametri di configurazione di uno dei 10 gruppi processo della saldatrice laser"
    "Parametri Obbligatori", "
    - ``Num``: Numero gruppo da impostare (1~10)
    - ``scanSpeed``: Velocità di scansione
    - ``scanWidth``: Larghezza di scansione
    - ``peakPower``: Potenza di picco
    - ``dutyCycle``: Ciclo di lavoro
    - ``Freq``: Frequenza
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Ottenere Parametri di Configurazione Attivi della Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetLaserWeldingParamActual(self, io_type=1)``"
    "Descrizione", "Ottiene i parametri di configurazione attivi della saldatrice laser"
    "Parametri Obbligatori", "
    - ``io_type``: Tipo di comunicazione 0-IO 1-UDP
    - ``scanSpeed``: Velocità di scansione
    - ``scanWidth``: Larghezza di scansione
    - ``peakPower``: Potenza di picco
    - ``dutyCycle``: Ciclo di lavoro
    - ``Freq``: Frequenza
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Configurare Porta DO Abilitazione IO Espanso per Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingEnableExtDoNum(self, ctrlModeDONum)``"
    "Descrizione", "Configura la porta DO abilitazione IO espanso per saldatrice laser"
    "Parametri Obbligatori", "
    - ``ctrlModeDONum``: Numero porta DO espanso per abilitazione saldatrice laser
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Configurare Porta DO Avvio IO Espanso per Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingStartExtDoNum(self, ctrlModeDONum)``"
    "Descrizione", "Configura la porta DO avvio IO espanso per saldatrice laser"
    "Parametri Obbligatori", "
    - ``ctrlModeDONum``: Numero porta DO espanso per avvio/arresto saldatrice laser
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Configurare Porta DO Reset Guasto IO Espanso per Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingErrResetExtDoNum(self, ctrlModeDONum)``"
    "Descrizione", "Configura la porta DO reset guasto IO espanso per saldatrice laser"
    "Parametri Obbligatori", "
    - ``ctrlModeDONum``: Numero porta DO espanso per reset guasto saldatrice laser
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Configurare Porta DI Stato Operativo (Laser Acceso) IO Espanso per Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingRunningStateExtDiNum(self, diNum)``"
    "Descrizione", "Configura la porta DI stato operativo (laser acceso) IO espanso per saldatrice laser"
    "Parametri Obbligatori", "
    - ``diNum``: Numero porta DI espanso per stato operativo (laser acceso) saldatrice laser
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Configurare Porta DI Stato Guasto IO Espanso per Saldatrice Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLaserWeldingErrStateExtDiNum(self, diNum)``"
    "Descrizione", "Configura la porta DI stato guasto IO espanso per saldatrice laser"
    "Parametri Obbligatori", "
    - ``diNum``: Numero porta DI espanso per stato guasto saldatrice laser
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice di errore Successo-0 Fallimento- errcode"

Esempio di Codice Saldatura Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from time import sleep
    from fairino import Robot
    import time

    # Stabilire connessione con il controller del robot, restituisce un oggetto robot in caso di connessione riuscita
    robot = Robot.RPC('192.168.58.2')

    def testLsaerWeld():
        robot.ExtDevLoadUDPDriver()
        time.sleep(1)

        robot.SetLaserWeldingParam(num = 3, scanSpeed = 2000, scanWidth = 3, peakPower = 1500, dutyCycle = 100, Freq = 1000, io_type=1)
        robot.SetLaserWeldingStartExtDoNum(ctrlModeDONum=1)

        robot.Mode(0)
        time.sleep(1)

        desc_pos1 = [-303.721, -206.960, 297.105, 152.209, 19.857, 109.166]
        desc_pos2 = [-301.575, -254.888, 284.786, 155.919, 26.946, 111.629]
        desc_safe = [-344.386, -280.830, 435.073, 173.835, 15.333, 124.931]
        jointPos1 = [9.827, -99.740, 120.088, -78.900, -77.241, -17.904]
        jointPos2 = [15.251, -96.456, 120.138, -84.664, -68.542, -17.843]
        jointSafe = [19.142, -98.078, 101.493, -83.078, -77.070, -17.794]

        error = robot.MoveL(desc_pos=desc_pos1,joint_pos=jointPos1, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(1, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_pos2, joint_pos=jointPos2, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)
        robot.SetLaserWeldingStartEnd(0, io_type=1, max_waittime=10000)

        error = robot.MoveL(desc_pos=desc_safe, joint_pos=jointSafe, tool=1, user=0, vel=100, ovl= 2, acc=100)
        print("MoveL return:", error)

        robot.Mode(1)
        time.sleep(1)

        # Chiudi connessione
        robot.CloseRPC()
        time.sleep(1)

    # Chiamata funzione di test
    testLsaerWeld()

Imposta il Ritorno al Punto Zero del Ciclo al Termine della Tessitura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWeaveBackCenterConfig(self, flag)``"
    "Descrizione", "Imposta se tornare al punto zero del ciclo al termine della tessitura"
    "Parametri Obbligatori", "
    - ``flag``: Se tornare al punto zero del ciclo al termine della tessitura; 0-non tornare; 1-tornare al punto zero del ciclo
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"    

Ottiene i Parametri del Ritorno al Punto Zero del Ciclo al Termine della Tessitura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWeaveBackCenterConfig(self)``"
    "Descrizione", "Ottiene i parametri del ritorno al punto zero del ciclo al termine della tessitura"
    "Parametri Obbligatori", "
    - ``flag``: Se tornare al punto zero del ciclo al termine della tessitura; 0-non tornare; 1-tornare al punto zero del ciclo
    "
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore, 0-successo; diverso da zero-errore"   

Esempio di Codice per il Ritorno al Punto Zero del Ciclo al Termine della Tessitura
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos: 

    from fairino import Robot
    import time

    def main():
        robot = Robot.RPC('192.168.58.2')
        time.sleep(0.5)  

        def callback(src_type, count, cmd_id, data_len, content):
            print(" cmd_id={} count={} data_len={} content={}".format(cmd_id, count, data_len, content))
            return 0

        robot.SetUDPCmdRpyCallback(callback)

        j1 = [9.000, -66.067, 67.706, -103.217, -90.151, 100.669]
        j2 = [-4.660, -107.973, 103.734, -76.214, -89.999, 90.886]
        j3 = [-36.762, -77.380, 91.364, -127.159, -90.024, 54.833]
        j4 = [-62.875, -89.460, 86.437, -77.030, -90.012, 31.539]

    
        desc_pos1 = [-654.129, -235.344, 246.543, 6.010, -11.535, -176.787]
        desc_pos2 = [-273.710, -100.871, 280.935, 5.692, 9.522, 179.512]
        desc_pos3 = [-566.093, 311.278, 215.008, -10.453, -17.486, -174.209]
        desc_pos4 = [-246.558, 328.240, 292.173, 13.912, 4.437, -179.067]

        offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
        epos = [0.0, 0.0, 0.0, 0.0]

        tool = 2
        user = 0
        vel = 100.0
        acc = 100.0
        ovl = 20.0
        oacc = 100.0
        blendT = 0.0
        blendR = 0.0
        flag = 0
        search = 0
        blendMode = 0
        velAccMode = 0

        robot.SetSpeed(1)

        robot.WeaveEnd(0)

        rtn = robot.SetWeaveBackCenterConfig(1)
        print(f"SetWeaveBackCenterConfig rtn is {rtn}")

        rtn, weaveBackConfig = robot.GetWeaveBackCenterConfig()
        print(f"GetWeavebackCenterConfig {weaveBackConfig}")

        rtn = robot.MoveJ(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,
                        vel=vel, acc=acc, ovl=100.0, exaxis_pos=epos,
                        blendT=blendT, offset_flag=flag, offset_pos=offset_pos)
        print(f"MoveJ rtn is {rtn}")

        robot.WeaveStart(0)

        robot.NewSplineStart(0, 6000)

        rtn = robot.NewSplinePoint(joint_pos=j1, desc_pos=desc_pos1, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 1 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j2, desc_pos=desc_pos2, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 2 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j3, desc_pos=desc_pos3, tool=tool, user=user,lastFlag=0,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=0)
        print(f"NewSplinePoint 3 rtn is {rtn}")

        rtn = robot.NewSplinePoint(joint_pos=j4, desc_pos=desc_pos4, tool=tool, user=user,lastFlag=1,
                                vel=vel, acc=acc, ovl=ovl, blendR=-1, config=1)
        print(f"NewSplinePoint 4 rtn is {rtn}")

        robot.NewSplineEnd()

        robot.CloseRPC()


    if __name__ == "__main__":
        main()