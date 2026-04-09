Assi di Espansione
==========================

.. toctree:: 
    :maxdepth: 5

Impostazione Parametri Asse di Espansione 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetParam(servoId,servoCompany,servoModel,servoSoftVersion, servoResolution,axisMechTransRatio)``"
    "Descrizione", "Imposta i parametri dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``servoCompany``：Produttore driver servomotore, 1-Dynatech;
    - ``servoModel``：Modello driver servomotore, 1-FD100-750C;
    - ``servoSoftVersion``：Versione software driver servomotore, 1-V1.0;
    - ``servoResolution``：Risoluzione encoder;
    - ``axisMechTransRatio``：Rapporto di trasmissione meccanico;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Parametri Configurazione Asse di Espansione 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetParam(servoId)``"
    "Descrizione", "Ottiene i parametri di configurazione dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode;
    - ``servoCompany``：Produttore driver servomotore, 1-Dynatech;
    - ``servoModel``：Modello driver servomotore, 1-FD100-750C;
    - ``servoSoftVersion``：Versione software driver servomotore, 1-V1.0;
    - ``servoResolution``：Risoluzione encoder;
    - ``axisMechTransRatio``：Rapporto di trasmissione meccanico;"

Impostazione Abilitazione/Disabilitazione Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoEnable(servoId,status)``"
    "Descrizione", "Imposta l'abilitazione/disabilitazione dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``status``：Stato abilitazione, 0-Disabilitato, 1-Abilitato;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Modalità Controllo Asse di Espansione 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetControlMode(servoId,mode)``"
    "Descrizione", "Imposta la modalità di controllo dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``mode``：Modalità controllo, 0-Modalità posizione, 1-Modalità velocità;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Posizione Obiettivo Asse di Espansione 485 (Modalità Posizione)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetPos(servoId,pos,speed)``"
    "Descrizione", "Imposta la posizione obiettivo dell'asse di espansione 485 (modalità posizione)"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``pos``：Posizione obiettivo, mm o °;
    - ``speed``：Velocità obiettivo, mm/s o °/s;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Coppia Obiettivo Asse di Espansione 485 (Modalità Coppia) - Non ancora disponibile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetTorque(servoId,torque)``"
    "Descrizione", "Imposta la coppia obiettivo dell'asse di espansione 485 (modalità coppia)"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``torque``：Coppia obiettivo, Nm;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Home Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoHoming(servoId,mode,searchVel,latchVel)``"
    "Descrizione", "Imposta l'home dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``mode``：Modalità home, 1-Home posizione corrente; 2-Home limite negativo; 3-Home limite positivo;
    - ``searchVel``： Velocità ricerca home, mm/s o °/s;
    - ``latchVel``：Velocità aggancio, mm/s o °/s;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Cancellazione Errori Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoClearError(servoId)``"
    "Descrizione", "Cancella gli errori dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Stato Servo Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetStatus(servoId)``"
    "Descrizione", "Ottiene lo stato del servo dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode;
    - ``servoErrCode``：Codice errore driver servomotore
    - ``servoState``：Stato driver servomotore bit0:0-Non abilitato; 1-Abilitato;  bit1:0-Non in movimento; 1-In movimento;  bit2 0-Limite positivo non attivato; 1-Limite positivo attivato; bit3 0-Limite negativo non attivato; 1-Limite negativo attivato; bit4 0-Posizionamento non completato; 1-Posizionamento completato;  bit5：0-Home non effettuato; 1-Home completato;
    - ``servoPos``：Posizione corrente servo mm o °;
    - ``servoSpeed``：Velocità corrente servo mm/s o °/s;
    - ``servoTorque``：Coppia corrente servo Nm;"

Impostazione Velocità Obiettivo Asse di Espansione 485 (Modalità Velocità)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetTargetSpeed(servoId,speed)``"
    "Descrizione", "Imposta la velocità obiettivo dell'asse di espansione 485 (modalità velocità)"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;
    - ``speed``：Velocità obiettivo, mm/s o °/s;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Numero Asse Dati Asse di Espansione 485 nel Feedback Stato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServosetStatusID(servoId)``"
    "Descrizione", "Imposta il numero asse dei dati asse di espansione 485 nel feedback stato"
    "Parametri Obbligatori", "- ``servoId``：ID driver servomotore, intervallo [1-15], corrisponde all'ID slave;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Accelerazione/Decelerazione Movimento Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetAcc(acc, dec)``"
    "Descrizione", "Imposta l'accelerazione/decelerazione del movimento dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``acc``：Accelerazione movimento asse di espansione 485
    - ``dec``：Decelerazione movimento asse di espansione 485"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Accelerazione/Decelerazione Arresto Emergenza Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoSetEmergencyStopAcc(acc, dec)``"
    "Descrizione", "Imposta l'accelerazione/decelerazione di arresto emergenza dell'asse di espansione 485"
    "Parametri Obbligatori", "- ``acc``：Accelerazione arresto emergenza asse di espansione 485
    - ``dec``：Decelerazione arresto emergenza asse di espansione 485"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Accelerazione/Decelerazione Movimento Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetAcc()``"
    "Descrizione", "Ottiene l'accelerazione/decelerazione del movimento dell'asse di espansione 485"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``acc``：Accelerazione movimento asse di espansione 485
    - ``dec``：Decelerazione movimento asse di espansione 485"

Ottenimento Accelerazione/Decelerazione Arresto Emergenza Asse di Espansione 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``AuxServoGetEmergencyStopAcc()``"
    "Descrizione", "Ottiene l'accelerazione/decelerazione di arresto emergenza dell'asse di espansione 485"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``acc``：Accelerazione arresto emergenza asse di espansione 485
    - ``dec``：Decelerazione arresto emergenza asse di espansione 485"

Esempio di Codice Controllo Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 15.45)
    print(f"AuxServoSetParam is: {retval}")
    servoCompany = 0
    servoModel = 0
    servoSoftVersion = 0
    servoResolution = 0
    axisMechTransRatio = 0.0
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 10, 11, 12, 13, 14)
    print(f"AuxServoSetParam is: {retval}")
    retval, servoCompany, servoModel, servoSoftVersion, servoResolution, axisMechTransRatio = robot.AuxServoGetParam(1)
    print(f"servoCompany {servoCompany}\n"
          f"servoModel {servoModel}\n"
          f"servoSoftVersion {servoSoftVersion}\n"
          f"servoResolution {servoResolution}\n"
          f"axisMechTransRatio {axisMechTransRatio}\n")
    retval = robot.AuxServoSetParam(1, 1, 1, 1, 131072, 36)
    print(f"AuxServoSetParam is: {retval}")
    time.sleep(3)
    robot.AuxServoSetAcc(3000, 3000)
    robot.AuxServoSetEmergencyStopAcc(5000, 5000)
    time.sleep(1)
    emagacc = 0.0
    emagdec = 0.0
    acc = 0.0
    dec = 0.0
    error,emagacc, emagdec = robot.AuxServoGetEmergencyStopAcc()
    print(f"emergency acc is {emagacc}  dec is {emagdec}")
    error,acc, dec = robot.AuxServoGetAcc()
    print(f"acc is {acc}  dec is {dec}")
    robot.AuxServoSetControlMode(1, 0)
    time.sleep(2)
    retval = robot.AuxServoEnable(1, 0)
    print(f"AuxServoEnable disenable {retval}")
    time.sleep(1)
    servoErrCode = 0
    servoState = 0
    servoPos = 0.0
    servoSpeed = 0.0
    servoTorque = 0.0
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoEnable(1, 1)
    print(f"AuxServoEnable enable {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoState {servoState}")
    time.sleep(1)
    retval = robot.AuxServoHoming(1, 1, 5, 1,100)
    print(f"AuxServoHoming {retval}")
    time.sleep(3)
    retval = robot.AuxServoSetTargetPos(1, 200, 30,100)
    print(f"AuxServoSetTargetPos {retval}")
    time.sleep(1)
    retval, servoErrCode, servoState, servoPos, servoSpeed, servoTorque = robot.AuxServoGetStatus(1)
    print(f"AuxServoGetStatus servoSpeed {servoSpeed}")
    time.sleep(8)
    robot.AuxServoSetControlMode(1, 1)
    time.sleep(2)
    robot.AuxServoEnable(1, 0)
    time.sleep(1)
    robot.AuxServoEnable(1, 1)
    time.sleep(1)
    robot.AuxServoSetTargetSpeed(1, 100, 80)
    time.sleep(5)
    robot.AuxServoSetTargetSpeed(1, 0, 80)
    robot.CloseRPC()

Configurazione Parametri Comunicazione UDP Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevSetUDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum, selfConnect)``"
    "Descrizione", "Configurazione parametri comunicazione UDP asse di espansione"
    "Parametri Obbligatori", "
    - ``ip``：Indirizzo IP PLC；
    - ``port``：Numero porta；
    - ``period``：Periodo comunicazione (ms, non ancora disponibile)；
    - ``lossPkgTime``：Tempo rilevamento perdita pacchetti (ms)；
    - ``lossPkgNum``：Numero perdite pacchetti；
    - ``disconnectTime``：Durata conferma disconnessione comunicazione；
    - ``reconnectEnable``：Abilitazione riconnessione automatica in caso di disconnessione 0-Disabilitato 1-Abilitato；
    - ``reconnectPeriod``：Intervallo periodo riconnessione (ms)；
    - ``reconnectNum``：Numero tentativi riconnessione
    - ``selfConnect``：Stabilire connessione automaticamente dopo riavvio alimentazione; 0-Non stabilire connessione; 1-Stabilire connessione"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Parametri Comunicazione UDP Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevGetUDPComParam()``"
    "Descrizione", "Ottiene i parametri di comunicazione UDP dell'asse di espansione"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "
    - Codice errore Successo-0  Fallimento- errcode；
    - ``ip``：Indirizzo IP PLC；
    - ``port``：Numero porta；
    - ``period``：Periodo comunicazione (ms, non ancora disponibile)；
    - ``lossPkgTime``：Tempo rilevamento perdita pacchetti (ms)；
    - ``lossPkgNum``：Numero perdite pacchetti；
    - ``disconnectTime``：Durata conferma disconnessione comunicazione；
    - ``reconnectEnable``：Abilitazione riconnessione automatica in caso di disconnessione 0-Disabilitato 1-Abilitato；
    - ``reconnectPeriod``：Intervallo periodo riconnessione (ms)；
    - ``reconnectNum``：Numero tentativi riconnessione
    - ``reconnectNum``: Numero di tentativi di riconnessione
    - ``selfConnect``: Riconnessione automatica dopo riavvio del box di controllo; 0-nessuna riconnessione; 1-riconnessione"
 
Caricamento Comunicazione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevLoadUDPDriver()``"
    "Descrizione", "Carica la comunicazione UDP"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
    
Scaricamento Comunicazione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUnloadUDPDriver()``"
    "Descrizione", "Scarica la comunicazione UDP"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ripristino Connessione Dopo Disconnessione Anomala Comunicazione UDP Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUDPClientComReset()``"
    "Descrizione", "Ripristina connessione dopo disconnessione anomala comunicazione UDP asse di espansione"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Chiusura Comunicazione Dopo Disconnessione Anomala Comunicazione UDP Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtDevUDPClientComClose()``"
    "Descrizione", "Chiude la comunicazione dopo disconnessione anomala comunicazione UDP asse di espansione"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Configurazione Parametri Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisParamConfig(axisId, axisType, axisDirection, axisMax, axisMin, axisVel, axisAcc,axisLead, encResolution, axisOffect, axisCompany, axisModel, axisEncType)``"
    "Descrizione", "Configurazione parametri asse di espansione UDP"
    "Parametri Obbligatori", "
    - ``axisId``：Numero asse [1-4]；
    - ``axisType``：Tipo asse di espansione 0-Translazionale; 1-Rotazionale；
    - ``axisDirection``：Direzione asse di espansione 0-Positivo; 1-Negativo；
    - ``axisMax``：Posizione massima asse di espansione mm；
    - ``axisMin``：Posizione minima asse di espansione mm；
    - ``axisVel``：Velocità mm/s；
    - ``axisAcc``：Accelerazione mm/s2；
    - ``axisLead``：Passo vite mm；
    - ``encResolution``：Risoluzione encoder；
    - ``axisOffect``：Offset asse di espansione punto inizio saldatura；
    - ``axisCompany``：Produttore driver 1-Hecheng; 2-Inovance; 3-Panasonic；
    - ``axisModel``：Modello driver 1-Hecheng-SV-XD3EA040L-E, 2-Hecheng-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG；
    - ``axisEncType``：Tipo encoder  0-Incrementale; 1-Assoluto;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Posizione Robot Relativa all'Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotPosToAxis(installType)``"
    "Descrizione", "Imposta la posizione del robot relativa all'asse di espansione"
    "Parametri Obbligatori", "- ``installType``：0-Robot installato sull'asse esterno, 1-Robot installato all'esterno dell'asse esterno;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione Configurazione Parametri DH Sistema Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAxisDHParaConfig(axisConfig,axisDHd1,axisDHd2,axisDHd3,axisDHd4,axisDHa1, axisDHa2,axisDHa3,axisDHa4)``"
    "Descrizione", "Imposta la configurazione dei parametri DH del sistema asse di espansione"
    "Parametri Obbligatori", "
    - ``axisConfig``：Configurazione asse esterno, 0-Guidovia lineare a singolo grado di libertà, 1-Posizionatore a due gradi di libertà a L, 2-Tre gradi di libertà, 3-Quattro gradi di libertà, 4-Posizionatore a singolo grado di libertà；
    - ``axisDHd1``：Parametro DH asse esterno d1 mm；
    - ``axisDHd2``：Parametro DH asse esterno d2 mm；
    - ``axisDHd3``：Parametro DH asse esterno d3 mm；
    - ``axisDHd4``：Parametro DH asse esterno d4 mm；
    - ``axisDHa1``：Parametro DH asse esterno a1 mm；
    - ``axisDHa2``：Parametro DH asse esterno a2 mm；
    - ``axisDHa3``：Parametro DH asse esterno a3 mm；
    - ``axisDHa4``：Parametro DH asse esterno a4 mm；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
                          
Abilitazione Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisServoOn(axisID, status)``"
    "Descrizione", "Abilitazione asse di espansione UDP"
    "Parametri Obbligatori", "- ``axisID``：Numero asse [1-4]；
    - ``status``：0-Disabilitato; 1-Abilitato;"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Home Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSetHoming(axisID, mode, searchVel, latchVel)``"
    "Descrizione", "Home asse di espansione UDP"
    "Parametri Obbligatori", "
    - ``axisID``：Numero asse [1-4]；
    - ``mode``：Modalità home 0 home posizione corrente, 1 home limite negativo, 2-home limite positivo；
    - ``searchVel``：Velocità ricerca home (mm/s)；
    - ``latchVel``：Velocità aggancio home (mm/s)；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Inizio Jog Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisStartJog( axisID, direction, vel, acc, maxDistance)``"
    "Descrizione", "Inizio jog asse di espansione UDP"
    "Parametri Obbligatori", "
    - ``axisID``：Numero asse [1-4]；
    - ``direction``：Direzione rotazione 0-Negativo; 1-Positivo；
    - ``vel``：Velocità (mm/s)；
    - ``acc``：Accelerazione (mm/s)；
    - ``maxDistance``：Distanza massima jog；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Stop Jog Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisStopJog(axisID)``"
    "Descrizione", "Stop jog asse di espansione UDP"
    "Parametri Obbligatori", "- ``axisID``：Numero asse [1-4]；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Configurazione e Jog Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    ip = ""
    port = 0
    period = 0
    lossPkgTime = 0
    lossPkgNum = 0
    disconnectTime = 0
    reconnectEnable = 0
    reconnectPeriod = 0
    reconnectNum = 0
    rtn,[ip, port, period, lossPkgTime, lossPkgNum,disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum] = robot.ExtDevGetUDPComParam()
    param_str = (f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}"
                 f"\nlossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}"
                 f"\nreconnecable {reconnectEnable}\nreconnperiod {reconnectPeriod}"
                 f"\nreconnnun {reconnectNum}")
    print(f"ExtDevGetUDPComParam rtn is {rtn}{param_str}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    time.sleep(3)
    robot.ExtAxisStartJog(1, 0, 10, 10, 30)
    time.sleep(1)
    robot.ExtAxisStopJog(1)
    time.sleep(3)
    robot.ExtAxisServoOn(1, 0)
    time.sleep(3)
    robot.ExtAxisStartJog(2, 0, 10, 10, 30)
    time.sleep(1)
    robot.ExtAxisStopJog(2)
    time.sleep(3)
    robot.ExtAxisServoOn(2, 0)
    robot.ExtDevUnloadUDPDriver()
    robot.CloseRPC()

Impostazione Punto di Riferimento Sistema Coordinate Asse di Espansione - Metodo a Quattro Punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSetRefPoint(pointNum)``"
    "Descrizione", "Imposta il punto di riferimento del sistema coordinate asse di espansione - metodo a quattro punti"
    "Parametri Obbligatori", "- ``pointNum``：Numero punto [1-4]；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Calcolo Sistema Coordinate Asse di Espansione - Metodo a Quattro Punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisComputeECoordSys()``"
    "Descrizione", "Calcola il sistema coordinate asse di espansione - metodo a quattro punti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode;
    - ``coord``：Valori sistema coordinate asse di espansione [x,y,z,rx,ry,rz]；"
                 
Impostazione Punto di Riferimento Sistema Coordinate Posizionatore - Metodo a Quattro Punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PositionorSetRefPoint(pointNum)``"
    "Descrizione", "Imposta il punto di riferimento del sistema coordinate posizionatore - metodo a quattro punti"
    "Parametri Obbligatori", "- ``pointNum``：Numero punto [1-4]；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Calcolo Sistema Coordinate Posizionatore - Metodo a Quattro Punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``PositionorComputeECoordSys()``"
    "Descrizione", "Calcola il sistema coordinate posizionatore - metodo a quattro punti"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode;
    - ``coord``：Valori sistema coordinate posizionatore [x,y,z,rx,ry,rz]；"
             
Impostazione Posa Punto di Riferimento Calibrazione nel Sistema Coordinate Estremità Posizionatore
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRefPointInExAxisEnd(pos)``"
    "Descrizione", "Imposta la posa del punto di riferimento calibrazione nel sistema coordinate estremità posizionatore"
    "Parametri Obbligatori", "- ``pos``：Valori posa [x,y,z,rx,ry,rz]；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Applicazione Sistema Coordinate Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisActiveECoordSys(applyAxisId,axisCoordNum,coord,calibFlag)``"
    "Descrizione", "Applica sistema coordinate asse di espansione"
    "Parametri Obbligatori", "
    - ``applyAxisId``:Numero asse di espansione bit0-bit3 corrisponde a numero asse di espansione 1-4, ad esempio applica asse di espansione 1 e 3, allora è 0b 0000 0101, cioè 5;
    - ``axisCoordNum``：Numero sistema coordinate asse di espansione；
    - ``coord``：Valori sistema coordinate [x,y,z,rx,ry,rz]；
    - ``calibFlag``：Flag calibrazione 0-No, 1-Sì；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Ottenimento Sistema Coordinate Asse di Espansione
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.2

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisGetCoord()``"
    "Descrizione", "Ottiene il sistema coordinate dell'asse di espansione"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``coord``：Sistema coordinate asse di espansione"

Esempio di Codice Calibrazione Sistema Coordinate Asse di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1)
    print(f"ExtDevSetUDPComParam rtn is {rtn}")
    rtn,udp_params = robot.ExtDevGetUDPComParam()
    ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum = udp_params
    patam = (
        f"\nip {ip}\nport {port}\nperiod {period}\nlossPkgTime {lossPkgTime}\n"
        f"lossPkgNum {lossPkgNum}\ndisConntime {disconnectTime}\nreconnecable {reconnectEnable}\n"
        f"reconnperiod {reconnectPeriod}\nreconnnun {reconnectNum}"
    )
    print(f"ExtDevGetUDPComParam rtn is {rtn}{patam}")
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    print(f"ExtAxisServoOn axis id 1 rtn is {rtn}")
    rtn = robot.ExtAxisServoOn(2, 1)
    print(f"ExtAxisServoOn axis id 2 rtn is {rtn}")
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    print(f"ExtAxisSetHoming rtn is {rtn}")
    time.sleep(4)
    rtn = robot.SetRobotPosToAxis(1)
    print(f"SetRobotPosToAxis rtn is {rtn}")
    rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4, 0, 0, 0, 0, 0, 0)
    print(f"SetAxisDHParaConfig rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 1 rtn is {rtn}")
    rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0)
    print(f"ExtAxisParamConfig axis 2 rtn is {rtn}")
    toolCoord = [0, 0, 210, 0, 0, 0]
    robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0)
    jSafe = [115.193, -96.149, 92.489, -87.068, -89.15, -83.488]
    j1 = [117.559, -92.624, 100.329, -96.909, -94.057, -83.488]
    j2 = [112.239, -90.096, 99.282, -95.909, -89.824, -83.488]
    j3 = [110.839, -83.473, 93.166, -89.22, -90.499, -83.487]
    j4 = [107.935, -83.572, 95.424, -92.873, -87.933, -83.488]
    descSafe = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc1 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc2 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc3 = [0.0,0.0,0.0,0.0,0.0,0.0]
    desc4 = [0.0,0.0,0.0,0.0,0.0,0.0]
    exaxisPos = [0.0,0.0,0.0,0.0]
    offdese = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, descSafe = robot.GetForwardKin(jSafe)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    error, desc1 = robot.GetForwardKin(j1)
    robot.MoveJ(joint_pos=j1,tool= 1,user= 0,vel= 100)
    time.sleep(2)
    actualTCPPos = [0.0,0.0,0.0,0.0,0.0,0.0]
    error, actualTCPPos = robot.GetActualTCPPose(0)
    robot.SetRefPointInExAxisEnd(actualTCPPos)
    rtn = robot.PositionorSetRefPoint(1)
    print(f"PositionorSetRefPoint 1 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc2 = robot.GetForwardKin(j2)
    rtn = robot.MoveJ(joint_pos=j2,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(2)
    print(f"PositionorSetRefPoint 2 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc3 = robot.GetForwardKin(j3)
    robot.MoveJ(joint_pos=j3,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(3)
    print(f"PositionorSetRefPoint 3 rtn is {rtn}")
    time.sleep(2)
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    robot.ExtAxisStartJog(1, 0, 50, 50, 10)
    time.sleep(1)
    robot.ExtAxisStartJog(2, 0, 50, 50, 10)
    time.sleep(1)
    error, desc4 = robot.GetForwardKin(j4)
    robot.MoveJ(joint_pos=j4,tool= 1,user= 0,vel= 100)
    rtn = robot.PositionorSetRefPoint(4)
    print(f"PositionorSetRefPoint 4 rtn is {rtn}")
    time.sleep(2)
    axisCoord = [0.0,0.0,0.0,0.0,0.0,0.0]
    error,axisCoord = robot.PositionorComputeECoordSys()
    robot.MoveJ(joint_pos=jSafe,tool= 1,user= 0,vel= 100)
    print(f"PositionorComputeECoordSys rtn is {axisCoord[0]} {axisCoord[1]} {axisCoord[2]} {axisCoord[3]} {axisCoord[4]} {axisCoord[5]}")
    rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1)
    print(f"ExtAxisActiveECoordSys rtn is {rtn}")
    robot.CloseRPC()
          
Movimento Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisMove(pos,ovl,blend=-1)``"
    "Descrizione", "Movimento asse di espansione UDP"
    "Parametri Obbligatori", "- ``pos=[exaxis[0],exaxis[1],exaxis[2],exaxis[3]]``：Posizione obiettivo posizione asse 1~posizione asse 4;
    - ``ovl``：Percentuale velocità"
    "Parametri Predefiniti", "- ``blend``：Parametro smoothing (mm o ms), -1, attesa completamento movimento, default -1"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
                                        
Esempio di Codice Movimento Asse di Espansione UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    axisPos = [20,0,0,0]
    robot.ExtAxisMove(axisPos, 50, -1)
    robot.CloseRPC()
    return 0

Movimento Sincrono Asse di Espansione UDP con Movimento Giunti Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveJ(joint_pos,tool,user,exaxis_pos, desc_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl= 100.0,  blendT=-1.0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0])``"
    "Descrizione", "Movimento sincrono asse di espansione UDP con movimento giunti robot"
    "Parametri Obbligatori", "
    - ``joint_pos``： Posizione giunti obiettivo, unità [°]；
    - ``desc_pos``：Posa cartesiana obiettivo, unità [mm][°]
    - ``tool``：Numero tool, [0~14]
    - ``user``：Numero pezzo, [0~14]
    - ``exaxis_pos``：Posizione asse esterno 1 ~ Posizione asse esterno 4"
    "Parametri Predefiniti", "
    - ``desc_pos``:Posa cartesiana obiettivo, unità [mm][°] default valori iniziali [0.0,0.0,0.0,0.0,0.0,0.0], default chiama valore ritorno cinematica diretta;
    - ``vel``： Percentuale velocità, [0~100] default 20.0；
    - ``acc``：Percentuale accelerazione, [0~100] non ancora disponibile, default 0.0 ；
    - ``ovl``：Fattore scala velocità, [0~100] default 100.0  ；
    - ``blendT``：[-1.0]-Movimento a posizione (bloccante), [0~500.0]-Tempo smoothing (non bloccante), unità [ms] default -1.0；
    - ``offset_flag``：[0]-Nessun offset, [1]-Offset nel sistema pezzo/base, [2]-Offset nel sistema tool default 0；
    - ``offset_pos``：Offset posa, unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0] ；"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode；"
                                        
Esempio di Codice Movimento Sincrono Asse di Espansione UDP con Movimento Giunti Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    # Imposta parametri comunicazione UDP e li carica
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Imposta parametri asse di espansione
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Abilitazione asse di espansione, home
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibrazione sistema coordinate asse di espansione
    pos = []  # Inserisci qui le coordinate punto calibrazione
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Questa operazione deve essere ripetuta 4 volte (con 4 punti)
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto di partenza e arrivo movimento sincrono
    startdescPose = []  # Inserisci coordinate specifiche
    startjointPos = []  # Inserisci coordinate specifiche
    startexaxisPos = []  # Inserisci coordinate specifiche
    enddescPose = []  # Inserisci coordinate specifiche
    endjointPos = []  # Inserisci coordinate specifiche
    endexaxisPos = []  # Inserisci coordinate specifiche
    # Movimento al punto di partenza
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, -1, 0, offdese)
    robot.CloseRPC()
                  
Movimento Sincrono Asse di Espansione UDP con Movimento Lineare Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveL(desc_pos, tool, user, exaxis_pos, joint_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel=20.0, acc=0.0, ovl=100.0, blendR=-1.0, search=0, offset_flag=0, offset_pos=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],config=-1)``"
    "Descrizione", "Movimento sincrono asse di espansione UDP con movimento lineare robot"
    "Parametri Obbligatori", "
    - ``desc_pos``：Posa cartesiana obiettivo, unità [mm][°]；
    - ``tool``：Numero tool, [0~14]；
    - ``user``：Numero pezzo, [0~14]；
    - ``exaxis_pos``：Posizione asse esterno 1 ~ Posizione asse esterno 4；"
    "Parametri Predefiniti", "
    - ``joint_pos``:Posizione giunti obiettivo, unità [°] default valori iniziali [0.0,0.0,0.0,0.0,0.0,0.0], default chiama valore ritorno cinematica inversa;
    - ``vel``： Percentuale velocità, [0~100] default 20.0；
    - ``acc``：Percentuale accelerazione, [0~100] non ancora disponibile, default 0.0；
    - ``ovl``：Fattore scala velocità, [0~100] default 100.0；
    - ``blendR``：[-1.0]-Movimento a posizione (bloccante), [0~500.0]-Tempo smoothing (non bloccante), unità [ms] default -1.0；
    - ``search``：[0]-Nessuna ricerca filo saldatura, [1]-Ricerca filo saldatura；
    - ``offset_flag``：[0]-Nessun offset, [1]-Offset nel sistema pezzo/base, [2]-Offset nel sistema tool default 0；
    - ``offset_pos``：Offset posa, unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0] ；
    - ``config``:Configurazione spazio giunti soluzione inversa, [-1]-Calcolo con riferimento alla posizione giunti corrente, [0~7]-Calcolo in base a specifica configurazione spazio giunti, default -1"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode；"
                                            
Esempio di Codice Movimento Sincrono Asse di Espansione UDP con Movimento Lineare Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    # Imposta parametri comunicazione UDP e li carica
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Imposta parametri asse di espansione
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Abilitazione asse di espansione, home
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibrazione sistema coordinate asse di espansione
    pos = []  # Inserisci coordinate punto calibrazione
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Deve essere chiamato 4 volte per la calibrazione
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto di partenza e arrivo movimento sincrono
    startdescPose = []  # Inserisci coordinate
    startjointPos = []  # Inserisci coordinate
    startexaxisPos = []  # Inserisci coordinate
    enddescPose = []  # Inserisci coordinate
    endjointPos = []  # Inserisci coordinate
    endexaxisPos = []  # Inserisci coordinate
    # Movimento al punto di partenza
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos, tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0)
    # Esegue movimento lineare sincrono
    robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, endexaxisPos, 100, 100, 100, 0, 0, offdese)
    robot.CloseRPC()
                      
Movimento Sincrono Asse di Espansione UDP con Movimento Arco Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ExtAxisSyncMoveC(desc_pos_p, tool_p, user_p,exaxis_pos_p, desc_pos_t, tool_t, user_t,exaxis_pos_t,joint_pos_p=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], joint_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0],vel_p=20.0, acc_p=100.0, offset_flag_p=0, offset_pos_p =[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], vel_t=20.0, acc_t=100.0, offset_flag_t=0, offset_pos_t=[0.0, 0.0, 0.0, 0.0, 0.0, 0.0], ovl=100.0, blendR=-1.0, config=-1)``"
    "Descrizione", " Movimento sincrono asse di espansione UDP con movimento arco robot"
    "Parametri Obbligatori", "
    - ``desc_pos_p``：Posa cartesiana punto percorso, unità [mm][°]；
    - ``tool_p``：Numero tool punto percorso, [0~14]；
    - ``user_p``：Numero pezzo punto percorso, [0~14]；
    - ``exaxis_pos_p``：Posizione asse esterno 1 ~ Posizione asse esterno 4 punto percorso default [0.0,0.0,0.0,0.0]；
    - ``desc_pos_t``：Posa cartesiana punto obiettivo, unità [mm][°]；
    - ``tool_t``：Numero tool, [0~14]；
    - ``user_t``：Numero pezzo, [0~14]；
    - ``exaxis_pos_t``：Posizione asse esterno 1 ~ Posizione asse esterno 4 punto obiettivo default [0.0,0.0,0.0,0.0]；"
    "Parametri Predefiniti", "
    - ``joint_pos_p``:Posizione giunti obiettivo, unità [°] default valori iniziali [0.0,0.0,0.0,0.0,0.0,0.0], default chiama valore ritorno cinematica inversa;
    - ``joint_pos_t``:Posizione giunti obiettivo, unità [°] default valori iniziali [0.0,0.0,0.0,0.0,0.0,0.0], default chiama valore ritorno cinematica inversa;
    - ``vel_p``: Percentuale velocità punto percorso, [0~100] default 20.0；
    - ``acc_p``: Percentuale accelerazione punto percorso, [0~100] non ancora disponibile, default 0.0 ；   
    - ``offset_flag_p``: Offset punto percorso [0]-Nessun offset, [1]-Offset nel sistema pezzo/base, [2]-Offset nel sistema tool default 0；
    - ``offset_pos_p``: Offset posa punto percorso, unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0]；
    - ``vel_t``: Percentuale velocità punto obiettivo, [0~100] default 20.0；
    - ``acc_t``: Percentuale accelerazione punto obiettivo, [0~100] non ancora disponibile default 0.0；
    - ``offset_flag_t``: Offset punto obiettivo [0]-Nessun offset, [1]-Offset nel sistema pezzo/base, [2]-Offset nel sistema tool default 0；
    - ``offset_pos_t``: Offset posa punto obiettivo, unità [mm][°] default [0.0,0.0,0.0,0.0,0.0,0.0]；
    - ``ovl``: Fattore scala velocità, [0~100] default 100.0；
    - ``blendR``：[-1.0]-Movimento a posizione (bloccante), [0~1000]-Raggio smoothing (non bloccante), unità [mm] default -1.0；
    - ``config``:Configurazione spazio giunti soluzione inversa, [-1]-Calcolo con riferimento alla posizione giunti corrente, [0~7]-Calcolo in base a specifica configurazione spazio giunti, default -1"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode；"
                                                
Esempio di Codice Movimento Sincrono Asse di Espansione UDP con Movimento Arco Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    # Imposta parametri comunicazione UDP e li carica
    robot.ExtDevSetUDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10)
    robot.ExtDevLoadUDPDriver()
    # Imposta parametri asse di espansione
    robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0)
    robot.SetRobotPosToAxis(1)
    robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0)
    # Abilitazione asse di espansione, home
    robot.ExtAxisServoOn(1, 0)
    robot.ExtAxisSetHoming(1, 0, 20, 3)
    # Calibrazione sistema coordinate asse di espansione
    pos = []  # Inserisci coordinate punto calibrazione
    robot.SetRefPointInExAxisEnd(pos)
    robot.PositionorSetRefPoint(1)  # Chiamato 4 volte per completare la calibrazione
    coord = []
    error,coord = robot.PositionorComputeECoordSys()
    robot.ExtAxisActiveECoordSys(1, 1, coord, 1)
    # Punto di partenza, intermedio e arrivo arco sincrono
    startdescPose = []# Inserisci coordinate
    startjointPos = []# Inserisci coordinate
    startexaxisPos =[]  # Inserisci coordinate asse di espansione
    middescPose = []# Inserisci punto intermedio
    midjointPos = []
    midexaxisPos =[]
    enddescPose = []
    endjointPos = []
    endexaxisPos =[]
    # Movimento al punto di partenza
    robot.ExtAxisMove(startexaxisPos, 20, -1)
    offdese = [0, 0, 0, 0, 0, 0]
    robot.MoveJ(joint_pos=startjointPos,tool= 1,user= 1,vel= 100,acc= 100,ovl= 100,exaxis_pos= startexaxisPos,blendT= 0,offset_flag= 0,offset_pos= offdese)
    # Inizia movimento arco sincrono
    robot.ExtAxisSyncMoveC(midjointPos,middescPose,1,1,midexaxisPos,
                           endjointPos,enddescPose,1,1,endexaxisPos,
                           100,100,0,offdese,
                           100,100,0,offdese,
                           100,0)
    robot.CloseRPC()

Impostazione DO di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxDO(DONum,bOpen,smooth,block)``"
    "Descrizione", "Imposta DO di espansione"
    "Parametri Obbligatori", "
    - ``DONum``： Numero DO；
    - ``bOpen``：Interruttore True-Aperto,False-Chiuso；
    - ``smooth``：Smoothing True -Sì, False -No；
    - ``block``：Bloccante True -Sì, False -No；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Impostazione AO di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxAO(AONum,value,block)``"
    "Descrizione", "Imposta AO di espansione"
    "Parametri Obbligatori", "
    - ``AONum``： Numero AO；
    - ``value``：Valore analogico [0-4095]；
    - ``block``：Bloccante True -Sì, False -No；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Impostazione Tempo Filtro Ingresso DI di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxDIFilterTime(filterTime)``"
    "Descrizione", "Imposta il tempo di filtro dell'ingresso DI di espansione"
    "Parametri Obbligatori", "- ``filterTime``： Tempo di filtro (ms)；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Impostazione Tempo Filtro Ingresso AI di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAuxAIFilterTime(AINum,filterTime)``"
    "Descrizione", "Imposta il tempo di filtro dell'ingresso AI di espansione"
    "Parametri Obbligatori", "
    - ``AINum``： Numero AI；
    - ``filterTime``： Tempo di filtro (ms)；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Attesa Ingresso DI di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAuxDI(DINum,bOpen,time,errorAlarm)``"
    "Descrizione", "Attesa ingresso DI di espansione"
    "Parametri Obbligatori", "
    - ``DINum``： Numero DI；
    - ``bOpen``：Interruttore True-Aperto,False-Chiuso；
    - ``time``：Tempo massimo attesa (ms)；
    - ``errorAlarm``：Continuare movimento True-Sì,False-No"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Attesa Ingresso AI di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``WaitAuxAI(,AINum,sign,value,time,errorAlarm)``"
    "Descrizione", "Attesa ingresso AI di espansione"
    "Parametri Obbligatori", "
    - ``AINum``： Numero AI；
    - ``sign``：0-Maggiore di; 1-Minore di；
    - ``value``：Valore AI；
    - ``time``：Tempo massimo attesa (ms)；
    - ``errorAlarm``：Continuare movimento True-Sì,False-No"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"
        
Ottenimento Valore DI di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAuxDI(DINum,isNoBlock)``"
    "Descrizione", "Ottiene il valore DI di espansione"
    "Parametri Obbligatori", "
    - ``DINum``： Numero DI；
    - ``isNoBlock``：Bloccante True-Bloccante false-Non bloccante；"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode；
    - ``isOpen``： 0-Chiuso; 1-Aperto；"
          
Ottenimento Valore AI di Espansione
++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetAuxAI(AINum,isNoBlock)``"
    "Descrizione", "Ottiene il valore AI di espansione"
    "Parametri Obbligatori", "
    - ``AINum``： Numero AI；
    - ``isNoBlock``：Bloccante True-Bloccante False-Non bloccante"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode；
    - ``value``：Valore ingresso；"

Esempio di Codice I/O di Espansione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    for i in range(128):
        robot.SetAuxDO(i, True, False, True)
        time.sleep(0.1)
    for i in range(128):
        robot.SetAuxDO(i, False, False, True)
        time.sleep(0.1)
    for i in range(409):
        value1 = i * 10
        value2 = 4095 - i * 10
        robot.SetAuxAO(0, value1, True)
        robot.SetAuxAO(1, value2, True)
        robot.SetAuxAO(2, value1, True)
        robot.SetAuxAO(3, value2, True)
        time.sleep(0.01)
    robot.SetAuxDIFilterTime(10)
    robot.SetAuxAIFilterTime(0, 10)
    for i in range(20):
        curValue = False
        error, curValue = robot.GetAuxDI(i, False)  # Nota: se la libreria richiede passaggio per riferimento, qui va modificato
        print(f"DI{i}   {curValue}")
    curValue = -1
    for i in range(4):
        error, curValue = robot.GetAuxAI(i, True)  # Nota anche qui problema passaggio per riferimento
        print(f"AI{i}   {curValue}")
    robot.WaitAuxDI(1, False, 1000, False)
    robot.WaitAuxAI(1, 1, 132, 1000, False)
    robot.CloseRPC()

Abilitazione Dispositivo Mobile
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorEnable(enable)``"
    "Descrizione", "Abilitazione dispositivo mobile"
    "Parametri Obbligatori", "- ``enable``：Stato abilitazione, 0-Disabilitato, 1-Abilitato"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Home Dispositivo Mobile
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorHoming()``"
    "Descrizione", "Home dispositivo mobile"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Movimento Lineare Dispositivo Mobile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorMoveL(distance, vel)``"
    "Descrizione", "Movimento lineare dispositivo mobile"
    "Parametri Obbligatori", "- ``distance``：Distanza movimento lineare (mm）
    - ``vel``：Percentuale velocità movimento lineare (0-100）"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Movimento Arco Dispositivo Mobile
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``TractorMoveC(radio, angle, vel)``"
    "Descrizione", "Movimento arco dispositivo mobile"
    "Parametri Obbligatori", "- ``radio``：Raggio movimento arco (mm）
    - ``angle``：Angolo movimento arco (°）
    - ``vel``：Percentuale velocità movimento arco (0-100）"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Stop Movimento Dispositivo Mobile
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ProgramStop()``"
    "Descrizione", "Stop movimento dispositivo mobile"
    "Parametri Obbligatori", "Nessuno"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Dispositivo Mobile
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    robot.ExtDevSetUDPComParam("192.168.58.2", 2021, 2, 50, 5, 50, 1, 50, 10, 1)
    robot.ExtDevLoadUDPDriver()
    rtn = robot.ExtAxisServoOn(1, 1)
    rtn = robot.ExtAxisServoOn(2, 1)
    time.sleep(2)
    robot.ExtAxisSetHoming(1, 0, 10, 2)
    time.sleep(2)
    rtn = robot.ExtAxisSetHoming(2, 0, 10, 2)
    time.sleep(4)
    robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0)
    robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0)
    robot.TractorEnable(False)
    time.sleep(2)
    robot.TractorEnable(True)
    time.sleep(2)
    robot.TractorHoming()
    time.sleep(2)
    robot.TractorMoveL(100, 2)
    time.sleep(5)
    robot.TractorStop()
    robot.TractorMoveL(-100, 20)
    time.sleep(5)
    robot.TractorMoveC(300, 90, 20)
    time.sleep(10)
    robot.TractorMoveC(300, -90, 20)
    time.sleep(1)
    robot.CloseRPC()

Registrazione Punto Sensore Laser
++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``LaserRecordPoint(coordID)``"
    "Descrizione", "Registrazione punto sensore laser"
    "Parametri Obbligatori", "- ``coordID``：Sistema coordinate sensore laser"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "- Codice errore Successo-0  Fallimento- errcode
    - ``joint``：Posizione giunti punto rilevato sensore laser
    - ``desc``：Posizione cartesiana punto rilevato sensore laser
    - ``exaxis``：Posizione asse di espansione punto rilevato sensore laser"

Esempio di Codice Registrazione Punto Sensore Laser
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    direction_point = [0, 0, 0]
    rtn = robot.LaserTrackingSearchStart(2, direction_point, 10, 100, 10000, 2)
    print(f"LaserTrackingSearchStart rtn is {rtn}")
    robot.LaserTrackingSearchStop()
    coord_id = 2
    rtn, joint, desc, exaxis = robot.LaserRecordPoint(coord_id)
    print(f"rtn is {rtn}")
    print(f"desc_pos:{desc[0]},{desc[1]},{desc[2]},"
          f"{desc[3]},{desc[4]},{desc[5]}")
    print(f"joint_pos:{joint[0]},{joint[1]},{joint[2]},{joint[3]},{joint[4]},{joint[5]}")
    print(f"exaxis pos is {exaxis[0]} {exaxis[1]} {exaxis[2]} {exaxis[3]}")
    off = [0] * 6
    robot.MoveJ(joint,tool=1,user=0,vel=100,acc=100,ovl=50,exaxis_pos=exaxis,blendT=-1,offset_flag=0,offset_pos=off)
    robot.CloseRPC()

Impostazione Strategia Movimento Sincrono Asse di Espansione con Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExAxisRobotPlan(strategy)``"
    "Descrizione", "Imposta la strategia di movimento sincrono asse di espansione con robot"
    "Parametri Obbligatori", "- ``strategy``：Strategia；0-Con robot come principale；1-Asse di espansione e robot sincroni"
    "Parametri Predefiniti", "Nessuno"
    "Valore di Ritorno", "Codice errore Successo-0  Fallimento- errcode"

Esempio di Codice Impostazione Strategia Movimento Sincrono Asse di Espansione con Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.5

.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce connessione con il controller robot, restituisce un oggetto robot in caso di successo
    robot = Robot.RPC('192.168.58.2')
    joint_pos1 = [-22.016, -49.217, 124.714, -161.100, -85.108, -0.333]
    joint_pos2 = [-21.083, -46.613, 110.079, -147.796, -80.757, -0.330]
    joint_pos3 = [-25.572, -60.090, 135.397, -163.889, -82.489, -0.345]
    desc_pos1 = [2.637, -0.001, 30.673, 178.786, -4.134, 68.326]
    desc_pos2 = [213.812, -1.440, 47.311, 177.410, 0.166, 68.946]
    desc_pos3 = [444.342, -12.723, 82.470, -177.701, -1.325, 65.151]
    epos1 = [0.001, 0.000, 0.000, 0.000]
    epos2 = [299.977, 0.000, 0.000, 0.000]
    epos3 = [399.969, 0.000, 0.000, 0.000]
    offset_pos = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    rtn = robot.SetExAxisRobotPlan(0)
    print(f"SetExAxisRobotPlan rtn is {rtn}")
    time.sleep(1)
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos1,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos1,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 1 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos2,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos2,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 2 rtn is {rtn}")
    rtn = robot.ExtAxisSyncMoveL(desc_pos=desc_pos3,tool=1,user=0,vel=100,acc=100,ovl=100,blendR=-1,exaxis_pos=epos3,offset_flag=0,offset_pos=offset_pos)
    print(f"ExtAxisSyncMoveL 3 rtn is {rtn}")
    time.sleep(8)
    robot.CloseRPC()