Assi Estesi
=================

.. toctree:: 
    :maxdepth: 5

Impostazione Parametri Assi Estesi 485
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta parametri assi estesi 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] param Parametri asse esteso 485
    * @return Codice errore 
    */
    int AuxServoSetParam(int servoId, Axis485Param param)
    
Ottenere Parametri Assi Estesi 485
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene parametri configurazione assi estesi 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [out] param Parametri asse esteso 485
    * @return Codice errore 
    */
    int AuxServoGetParam(int servoId, Axis485Param param);

Impostare Abilitazione/Disabilitazione Assi Estesi 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta abilitazione/disabilitazione assi estesi 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] status Stato abilitazione, 0-disabilitato, 1-abilitato
    * @return Codice errore 
    */
    int AuxServoEnable(int servoId, int status);
        
Impostare Modalità Controllo Assi Estesi 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta modalità controllo assi estesi 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] mode Modalità controllo, 0-modalità posizione, 1-modalità velocità
    * @return Codice errore 
    */
    int AuxServoSetControlMode(int servoId, int mode);

Impostare Posizione Target Asse Esteso 485 (Modalità Posizione)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta posizione target asse esteso 485 (modalità posizione)
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] pos Posizione target, mm o °
    * @param [in] speed Velocità target, mm/s o °/s
    * @param [in] acc Percentuale accelerazione [0-100]
    * @return Codice errore 
    */
    int AuxServoSetTargetPos(int servoId, double pos, double speed, double acc);
    
Impostare Coppia Target Asse Esteso 485 (Modalità Coppia) - Non ancora disponibile
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta coppia target asse esteso 485 (modalità coppia) - Non ancora disponibile
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] torque Coppia target, Nm
    * @return Codice errore 
    */
    int AuxServoSetTargetTorque(int servoId, double torque);
        
Impostare Homing Asse Esteso 485
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta homing asse esteso 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] mode Modalità homing, 1-homing posizione corrente; 2-homing limite negativo; 3-homing limite positivo
    * @param [in] searchVel Velocità ricerca homing, mm/s o °/s
    * @param [in] latchVel Velocità aggancio, mm/s o °/s
    * @param [in] acc Percentuale accelerazione [0-100]
    * @return Codice errore 
    */
    int AuxServoHoming(int servoId, int mode, double searchVel, double latchVel, double acc);

Cancellare Informazioni Errore Asse Esteso 485
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Cancella informazioni errore asse esteso 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @return Codice errore 
    */
    int AuxServoClearError(int servoId);

Ottenere Stato Servo Asse Esteso 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene stato servo asse esteso 485
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [out] servoErrCode Codice errore driver servo
    * @param [out] servoState Stato driver servo bit0:0-non abilitato; 1-abilitato; bit1:0-non in movimento; 1-in movimento; bit4 0-posizionamento non completato; 1-posizionamento completato; bit5：0-homing non completato; 1-homing completato
    * @param [out] servoPos Posizione corrente servo mm o °
    * @param [out] servoSpeed Velocità corrente servo mm/s o °/s
    * @param [out] servoTorque Coppia corrente servo Nm
    * @return Codice errore 
    */
    int AuxServoGetStatus(int servoId, int[] servoErrCode, int[] servoState, double[] servoPos, double[] servoSpeed, double[] servoTorque)

Impostare Velocità Target Asse Esteso 485 (Modalità Velocità)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta velocità target asse esteso 485 (modalità velocità)
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @param [in] speed Velocità target, mm/s o °/s
    * @param [in] acc Percentuale accelerazione [0-100]
    * @return Codice errore 
    */
    int AuxServoSetTargetSpeed(int servoId, double speed, double acc);

Impostare ID Asse Dati Assi Estesi 485 in Feedback Stato
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta ID asse dati assi estesi 485 in feedback stato
    * @param [in] servoId ID driver servo, range [1-16], corrisponde all'ID slave
    * @return Codice errore 
    */
    int AuxServoSetStatusID(int servoId);

Impostare Accelerazione/Decelerazione Movimento Assi Estesi 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta accelerazione/decelerazione movimento assi estesi 485
    * @param [in] acc Accelerazione movimento asse esteso 485
    * @param [in] dec Decelerazione movimento asse esteso 485
    * @return Codice errore 
    */
    int AuxServoSetAcc(double acc, double dec)

Impostare Accelerazione/Decelerazione Arresto Emergenza Assi Estesi 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Imposta accelerazione/decelerazione arresto emergenza assi estesi 485
    * @param [in] acc Accelerazione arresto emergenza asse esteso 485
    * @param [in] dec Decelerazione arresto emergenza asse esteso 485
    * @return Codice errore 
    */
    int AuxServoSetEmergencyStopAcc(double acc, double dec)

Ottenere Accelerazione/Decelerazione Movimento Assi Estesi 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene accelerazione/decelerazione movimento assi estesi 485
    * @return List[0]:Codice errore; List[1]:Accelerazione movimento asse esteso 485; List[2]:Decelerazione movimento asse esteso 485 
    */
    List<Number> AuxServoGetAcc()

Ottenere Accelerazione/Decelerazione Arresto Emergenza Assi Estesi 485
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene accelerazione/decelerazione arresto emergenza assi estesi 485
    * @return List[0]:Codice errore; List[1]:Accelerazione arresto emergenza asse esteso 485; List[2]:Decelerazione arresto emergenza asse esteso 485
    */
    List<Number> AuxServoGetEmergencyStopAcc()

Esempio Codice Controllo Assi Estesi
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int Test485Auxservo(Robot robot)
    {
        Axis485Param ax=new Axis485Param(1, 1, 1, 131072, 15.45);
        int retval = robot.AuxServoSetParam(1, ax);

        Axis485Param ax2=new Axis485Param();
        retval = robot.AuxServoGetParam(1, ax2);

        ax.servoCompany=10;
        ax.servoModel=11;
        ax.servoSoftVersion=12;
        ax.servoResolution=13;
        ax.axisMechTransRatio=14;

        retval = robot.AuxServoSetParam(1, ax);

        retval = robot.AuxServoGetParam(1,ax2);

        ax.servoCompany=1;
        ax.servoModel=1;
        ax.servoSoftVersion=1;
        ax.servoResolution=131072;
        ax.axisMechTransRatio=36;

        retval = robot.AuxServoSetParam(1, ax);
        robot.Sleep(3000);

        robot.AuxServoSetAcc(3000, 3000);
        robot.AuxServoSetEmergencyStopAcc(5000, 5000);
        robot.Sleep(1000);
        double emagacc = 0, acc = 0;
        double emagdec = 0, dec = 0;

        List<Number> aux=new ArrayList<>();

        aux=robot.AuxServoGetEmergencyStopAcc();
        aux=robot.AuxServoGetAcc();

        robot.AuxServoSetControlMode(1, 0);
        robot.Sleep(2000);

        retval = robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        int[] servoerrcode =new int[]{0};
        int[] servoErrCode=new int[]{0};
        int[] servoState=new int[]{0};
        double[] servoPos=new double[]{0};
        double[] servoSpeed=new double[]{0};
        double[] servoTorque=new double[]{0};
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);;

        retval = robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(1000);

        retval = robot.AuxServoHoming(1, 1, 5, 1,100);
        robot.Sleep(3000);

        retval = robot.AuxServoSetTargetPos(1, 200, 30,100);
        robot.Sleep(1000);
        retval = robot.AuxServoGetStatus(1, servoErrCode, servoState, servoPos, servoSpeed, servoTorque);
        robot.Sleep(8000);


        robot.AuxServoSetControlMode(1, 1);
        robot.Sleep(2000);

        robot.AuxServoEnable(1, 0);
        robot.Sleep(1000);
        robot.AuxServoEnable(1, 1);
        robot.Sleep(1000);
        robot.AuxServoSetTargetSpeed(1, 100, 80);

        robot.Sleep(5000);
        robot.AuxServoSetTargetSpeed(1, 0, 80);

        robot.CloseRPC();
        return 0;
    }

Configurazione Parametri Comunicazione Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /**
    * @brief Configurazione parametri comunicazione assi estesi UDP
    * @param [in] param Parametri comunicazione
    * @return Codice errore
    */
    int ExtDevSetUDPComParam(UDPComParam param);     

Ottenere Configurazione Parametri Comunicazione Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene i parametri di comunicazione UDP per assi di estensione
    * @param [out] ip Indirizzo IP del PLC
    * @param [out] port Numero di porta
    * @param [out] period Periodo di comunicazione (ms, default è 2, non modificare questo parametro)
    * @param [out] lossPkgTime Tempo di rilevamento perdita pacchetti (ms)
    * @param [out] lossPkgNum Numero di perdite di pacchetti
    * @param [out] disconnectTime Durata di conferma disconnessione comunicazione
    * @param [out] reconnectEnable Abilitazione riconnessione automatica alla disconnessione della comunicazione 0-disabilitato 1-abilitato
    * @param [out] reconnectPeriod Intervallo di riconnessione (ms)
    * @param [out] reconnectNum Numero di tentativi di riconnessione
    * @param [out] selfConnect Riconnessione automatica dopo riavvio del box di controllo; 0-nessuna riconnessione; 1-riconnessione
    * @return Codice di errore
    */
    public int ExtDevGetUDPComParam(ref string ip, ref int port, ref int period, ref int lossPkgTime, ref int lossPkgNum, ref int disconnectTime, ref int reconnectEnable, ref int reconnectPeriod, ref int reconnectNum, ref int selfConnect)      

Caricare Comunicazione UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Carica comunicazione UDP
    * @return Codice errore
    */
    int ExtDevLoadUDPDriver();

Scaricare Comunicazione UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Scarica comunicazione UDP
    * @return Codice errore
    */
    int ExtDevUnloadUDPDriver();

Ripristinare Connessione dopo Interruzione Anomala Comunicazione Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ripristina connessione dopo interruzione anomala comunicazione assi estesi UDP
    * @return Codice errore
    */
    int ExtDevUDPClientComReset();

Chiudere Comunicazione dopo Interruzione Anomala Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Chiude comunicazione dopo interruzione anomala assi estesi UDP
    * @return Codice errore
    */
    int ExtDevUDPClientComClose();

Configurazione Parametri Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configurazione parametri assi estesi UDP
    * @param [in] axisID Numero asse
    * @param [in] axisType Tipo asse esteso 0-traslazionale; 1-rotazionale
    * @param [in] axisDirection Direzione asse esteso 0-positiva; 1-negativa
    * @param [in] axisMax Posizione massima asse esteso mm
    * @param [in] axisMin Posizione minima asse esteso mm
    * @param [in] axisVel Velocità mm/s
    * @param [in] axisAcc Accelerazione mm/s2
    * @param [in] axisLead Passo vite mm
    * @param [in] encResolution Risoluzione encoder
    * @param [in] axisOffect Offset asse esteso punto inizio giunto saldatura
    * @param [in] axisCompany Produttore driver 1-Hechuan; 2-Inovance; 3-Panasonic
    * @param [in] axisModel Modello driver 1-Hechuan-SV-XD3EA040L-E, 2-Hechuan-SV-X2EA150A-A, 1-Inovance-SV620PT5R4I, 1-Panasonic-MADLN15SG, 2-Panasonic-MSDLN25SG, 3-Panasonic-MCDLN35SG
    * @param [in] axisEncType Tipo encoder 0-incrementale; 1-assoluto
    * @return Codice errore
    */
    int ExtAxisParamConfig(int axisID, int axisType, int axisDirection, double axisMax, double axisMin, double axisVel, double axisAcc, double axisLead, int encResolution, double axisOffect, int axisCompany, int axisModel, int axisEncType);

Impostare Posizione Installazione Asse Esteso
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta posizione installazione asse esteso
    * @param [in] installType 0-robot installato sull'asse esterno, 1-robot installato fuori dall'asse esterno
    * @return Codice errore
    */
    int SetRobotPosToAxis(int installType);

Configurazione Parametri DH Sistema Assi Estesi
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Configurazione parametri DH sistema assi estesi
    * @param [in] axisConfig Configurazione asse esterno, 0-guida lineare a singolo grado di libertà, 1-posizionatore a L a due gradi di libertà, 2-tre gradi di libertà, 3-quattro gradi di libertà, 4-posizionatore a singolo grado di libertà
    * @param [in] axisDHd1 Parametro DH asse esterno d1 mm
    * @param [in] axisDHd2 Parametro DH asse esterno d2 mm
    * @param [in] axisDHd3 Parametro DH asse esterno d3 mm
    * @param [in] axisDHd4 Parametro DH asse esterno d4 mm
    * @param [in] axisDHa1 Parametro DH asse esterno 11 mm
    * @param [in] axisDHa2 Parametro DH asse esterno a2 mm
    * @param [in] axisDHa3 Parametro DH asse esterno a3 mm
    * @param [in] axisDHa4 Parametro DH asse esterno a4 mm
    * @return Codice errore
    */
    int SetAxisDHParaConfig(int axisConfig, double axisDHd1, double axisDHd2, double axisDHd3, double axisDHd4, double axisDHa1, double axisDHa2, double axisDHa3, double axisDHa4);

Abilitazione Asse Esteso UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Abilitazione asse esteso UDP
    * @param [in] axisID Numero asse [1-4]
    * @param [in] status 0-disabilitato; 1-abilitato
    * @return Codice errore
    */
    int ExtAxisServoOn(int axisID, int status);

Homing Asse Esteso UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Homing asse esteso UDP
    * @param [in] axisID Numero asse [1-4]
    * @param [in] mode Modalità homing 0-homing posizione corrente, 1-homing limite negativo, 2-homing limite positivo
    * @param [in] searchVel Velocità ricerca homing (mm/s)
    * @param [in] latchVel Velocità aggancio homing (mm/s)
    * @return Codice errore
    */
    int ExtAxisSetHoming(int axisID, int mode, double searchVel, double latchVel);

Inizio Jog Asse Esteso UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Inizio jog asse esteso UDP
    * @param [in] axisID Numero asse [1-4]
    * @param [in] direction Direzione rotazione 0-negativa; 1-positiva
    * @param [in] vel Velocità (mm/s)
    * @param [in] acc Accelerazione (mm/s2)
    * @param [in] maxDistance Distanza massima jog
    * @return Codice errore
    */
    int ExtAxisStartJog(int axisID, int direction, double vel, double acc, double maxDistance);
    
Arresto Jog Asse Esteso UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Arresto jog asse esteso UDP
    * @param [in] axisID Numero asse [1-4]
    * @return Codice errore
    */
    int ExtAxisStopJog(int axisID);

Esempio Codice Configurazione e Jog Assi Estesi UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: Java
    :linenos:

    public static int TestUDPAxis(Robot robot)//UDP
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);
        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);
        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);
        robot.Sleep(3000);

        robot.ExtAxisSetHoming(1, 0, 10, 2);
        robot.Sleep(3000);
        rtn = robot.ExtAxisSetHoming(2, 0, 10, 2);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(10, 20, 0, 0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        robot.Sleep(4000);
        robot.ExtAxisStartJog(1, 0, 10, 10, 30);
        robot.Sleep(4000);
        robot.ExtAxisStopJog(1);
        robot.Sleep(4000);
        robot.ExtAxisServoOn(1, 0);

        robot.Sleep(4000);
        robot.ExtAxisStartJog(2, 0, 10, 10, 30);
        robot.Sleep(4000);
        robot.ExtAxisStopJog(2);
        robot.Sleep(4000);
        robot.ExtAxisServoOn(2, 0);
        robot.Sleep(4000);
        robot.ExtDevUnloadUDPDriver();

        return 0;
    }

Impostare Punto Riferimento Sistema Coordinate Assi Estesi - Metodo a Quattro Punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta punto riferimento sistema coordinate assi estesi - metodo a quattro punti
    * @param [in] pointNum Numero punto [1-4]
    * @return Codice errore
    */
    int ExtAxisSetRefPoint(int pointNum);

Calcolare Sistema Coordinate Assi Estesi - Metodo a Quattro Punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calcola sistema coordinate assi estesi - metodo a quattro punti
    * @param [out] coord Valori sistema coordinate
    * @return Codice errore
    */
    int ExtAxisComputeECoordSys(DescPose coord);

Impostare Punto Riferimento Sistema Coordinate Posizionatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta punto riferimento sistema coordinate posizionatore
    * @param [in] pointNum Numero punto [1-4]
    * @return Codice errore
    */
    int PositionorSetRefPoint(int pointNum);

Calcolare Sistema Coordinate Posizionatore - Metodo a Quattro Punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Calcola sistema coordinate posizionatore - metodo a quattro punti
    * @param [out] coord Valori sistema coordinate
    * @return Codice errore
    */
    int PositionorComputeECoordSys(DescPose coord);

Impostare Posa Punto Riferimento Calibrazione nel Sistema Coordinate Estremità Posizionatore
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta posa punto riferimento calibrazione nel sistema coordinate estremità posizionatore
    * @param [in] pos Valore posa
    * @return Codice errore
    */
    int SetRefPointInExAxisEnd(DescPose pos);

Applicare Sistema Coordinate Assi Estesi
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Applica sistema coordinate assi estesi
    * @param [in] applyAxisId Numero asse esteso bit0-bit3 corrisponde a numero asse esteso 1-4, es. applica assi estesi 1 e 3, allora 0b 0000 0101; cioè 5
    * @param [in] axisCoordNum Numero sistema coordinate assi estesi
    * @param [in] coord Valori sistema coordinate
    * @param [in] calibFlag Flag calibrazione 0-no, 1-sì
    * @return Codice errore
    */
    int ExtAxisActiveECoordSys(int applyAxisId, int axisCoordNum, DescPose coord, int calibFlag);

Ottenere Sistema Coordinate Assi Estesi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.5-3.8.2

.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene sistema coordinate assi estesi
    * @param [out] coord Sistema coordinate assi estesi
    * @return Codice errore
    */
    int ExtAxisGetCoord(DescPose coord);

Esempio Codice Calibrazione Sistema Coordinate Assi Estesi
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisCalib(Robot robot)
    {
        UDPComParam para1=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 200, 1, 100, 5, 1);

        int rtn = robot.ExtDevSetUDPComParam(para1);
        String ip = ""; int port = 0; int period = 0; int lossPkgTime = 0; int lossPkgNum = 0; int disconnectTime = 0; int reconnectEnable = 0; int reconnectPeriod = 0; int reconnectNum = 0;
        UDPComParam para2=new UDPComParam(ip, port, period, lossPkgTime, lossPkgNum, disconnectTime, reconnectEnable, reconnectPeriod, reconnectNum,0);

        rtn = robot.ExtDevGetUDPComParam(para2);

        robot.ExtDevLoadUDPDriver();

        rtn = robot.ExtAxisServoOn(1, 1);
        rtn = robot.ExtAxisServoOn(2, 1);

        robot.Sleep(4000);

        rtn = robot.SetRobotPosToAxis(1);
        rtn = robot.SetAxisDHParaConfig(1, 128.5, 206.4,  0, 0, 0, 0, 0, 0);
        rtn = robot.ExtAxisParamConfig(1, 1, 1, 1000, -1000, 1000, 1000, 1.905, 262144, 200, 1, 0, 0);
        rtn = robot.ExtAxisParamConfig(2, 1, 1, 1000, -1000, 1000, 1000, 4.444, 262144, 200, 1, 0, 0);

        DescPose toolCoord=new DescPose(0, 0, 210, 0, 0, 0);
        robot.SetToolCoord(1, toolCoord, 0, 0, 1, 0);

        JointPos jSafe=new JointPos(115.193, -96.149, 92.489, -87.068, -89.15, -83.488);
        JointPos j1=new JointPos(117.559, -92.624, 100.329, -96.909, -94.057, -83.488);
        JointPos j2=new JointPos(112.239, -90.096, 99.282, -95.909, -89.824, -83.488);
        JointPos j3=new JointPos(110.839, -83.473, 93.166, -89.22, -90.499, -83.487);
        JointPos j4=new JointPos(107.935, -83.572, 95.424, -92.873, -87.933, -83.488);

        DescPose descSafe =new DescPose(0,0,0,0,0,0);
        DescPose desc1 = new DescPose(0,0,0,0,0,0);
        DescPose desc2 = new DescPose(0,0,0,0,0,0);
        DescPose desc3 = new DescPose(0,0,0,0,0,0);
        DescPose desc4 = new DescPose(0,0,0,0,0,0);
        ExaxisPos exaxisPos =new ExaxisPos(0,0,0,0);
        DescPose offdese =new DescPose(0, 0, 0, 0, 0, 0);

        robot.GetForwardKin(jSafe, descSafe);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        robot.GetForwardKin(j1, desc1);
        robot.MoveJ(j1, desc1, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.Sleep(2000);

        DescPose actualTCPPos =new DescPose(0,0,0,0,0,0);

        robot.GetActualTCPPose(actualTCPPos);
        robot.SetRefPointInExAxisEnd(actualTCPPos);
        rtn = robot.PositionorSetRefPoint(1);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j2, desc2);
        rtn = robot.MoveJ(j2, desc2, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(2);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j3, desc3);
        robot.MoveJ(j3, desc3, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(3);
        robot.Sleep(2000);

        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        robot.ExtAxisStartJog(1, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.ExtAxisStartJog(2, 0, 50, 50, 10);
        robot.Sleep(1000);
        robot.GetForwardKin(j4, desc4);
        robot.MoveJ(j4, desc4, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.PositionorSetRefPoint(4);
        robot.Sleep(2000);

        DescPose axisCoord = new DescPose();
        robot.PositionorComputeECoordSys(axisCoord);
        robot.MoveJ(jSafe, descSafe, 1, 0, 100, 100, 100, exaxisPos, -1, 0, offdese);
        rtn = robot.ExtAxisActiveECoordSys(3, 1, axisCoord, 1);

        robot.CloseRPC();
        return 0;
    }

Movimento Asse Esteso UDP
++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionchanged:: Java SDK-v1.0.7-3.8.4

.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento asse esteso UDP
    * @param [in] pos Posizione target
    * @param [in] ovl Percentuale velocità
    * @param [in] blend Parametro smoothing (mm o ms)
    * @return Codice errore
    */
    int ExtAxisMove(ExaxisPos pos, double ovl, double blend)

Esempio Codice Movimento Asse Esteso UDP
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestUDPAxisMove(Robot robot)
    {
        ExaxisPos exaxisPos = new ExaxisPos( 20, 0, 0, 0 );
        robot.ExtAxisMove(exaxisPos,40,0);
        robot.CloseRPC();
        return 0;
    }

Movimento Sincrono Assi Estesi UDP e Giunti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento sincrono assi estesi UDP e giunti robot
    * @param [in] joint_pos  Posizione target giunti, unità deg
    * @param [in] desc_pos   Posa target cartesiana
    * @param [in] tool  Numero sistema coordinate utensile, range [0~14]
    * @param [in] user  Numero sistema coordinate pezzo, range [0~14]
    * @param [in] vel  Percentuale velocità, range [0~100]
    * @param [in] acc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param [in] ovl  Fattore scala velocità, range [0~100]
    * @param [in] epos  Posizione assi estesi, unità mm
    * @param [in] blendT [-1.0]-movimento in posizione (bloccante), [0~500.0]-tempo smoothing (non bloccante), unità ms
    * @param [in] offset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param [in] offset_pos  Offset posa
    * @return Codice errore
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos);

Movimento Sincrono Assi Estesi UDP e Giunti Robot (Calcolo Cinematica Diretta Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento sincrono assi estesi UDP e giunti robot (calcolo cinematica diretta automatico)
    * @param  [in] joint_pos  Posizione target giunti, unità deg
    * @param  [in] tool  Numero sistema coordinate utensile, range [0~14]
    * @param  [in] user  Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] vel  Percentuale velocità, range [0~100]
    * @param  [in] acc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore scala velocità, range [0~100]
    * @param  [in] epos  Posizione assi estesi, unità mm
    * @param  [in] blendT [-1.0]-movimento in posizione (bloccante), [0~500.0]-tempo smoothing (non bloccante), unità ms
    * @param  [in] offset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param  [in] offset_pos  Offset posa
    * @return  Codice errore
    */
    int ExtAxisSyncMoveJ(JointPos joint_pos, int tool, int user, double vel, double acc, double ovl, ExaxisPos epos, double blendT, int offset_flag, DescPose offset_pos) 

Esempio Codice Movimento Sincrono Assi Estesi UDP e Giunti Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveJ(Robot robot)
    {
        //1. Calibrare e applicare sistema coordinate utensile robot, è possibile utilizzare metodo a quattro o sei punti per calibrazione e applicazione sistema coordinate utensile, interfacce coinvolte:
        //  int SetToolPoint(int point_num); //Imposta punto riferimento utensile - metodo a sei punti
        //  int ComputeTool(ref DescPose tcp_pose); //Calcola sistema coordinate utensile
        //  int SetTcp4RefPoint(int point_num);  //Imposta punto riferimento utensile - metodo a quattro punti
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile - metodo a quattro punti
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Imposta e applica sistema coordinate utensile
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Imposta e applica lista sistemi coordinate utensile
        //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Impostare parametri assi estesi, incluso tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1); //Posizione installazione assi estesi
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è posizionatore monoasse, quindi basta un set di parametri driver, se si sceglie tipo asse esteso con più assi, ogni asse richiede parametri driver
        //4. Impostare abilitazione e homing degli assi selezionati
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Eseguire calibrazione e applicazione sistema coordinate assi estesi
        DescPose pos = new DescPose(/* Inserire coordinate punto calibrazione */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare asse esteso, quindi chiamare questa interfaccia 4 volte per completare calibrazione */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applica risultato calibrazione a sistema coordinate asse esteso
        //6. Calibrare sistema coordinate pezzo su asse esteso, necessarie seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Registrare punto di partenza movimento sincrono giunti
        DescPose startdescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos startjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserire coordinate punto partenza asse esteso */ );
        //8. Registrare coordinate punto arrivo movimento sincrono giunti
        DescPose enddescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos endjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Inserire coordinate punto arrivo asse esteso */);
        //9. Scrivere programma movimento sincrono
        //Spostarsi al punto di partenza, assumendo sistemi coordinate utensile e pezzo applicati entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20, 0);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveJ(endjointPos, enddescPose, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveJ(endjointPos, 1, 1, 100, 100, 100, endexaxisPos, -1, 0, offdese);
        robot.CloseRPC();
        return 0;
    }

Movimento Lineare Sincrono Assi Estesi UDP e Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento lineare sincrono assi estesi UDP e robot
    * @param [in] joint_pos  Posizione target giunti, unità deg
    * @param [in] desc_pos   Posa target cartesiana
    * @param [in] tool  Numero sistema coordinate utensile, range [0~14]
    * @param [in] user  Numero sistema coordinate pezzo, range [0~14]
    * @param [in] vel  Percentuale velocità, range [0~100]
    * @param [in] acc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param [in] ovl  Fattore scala velocità, range [0~100]
    * @param [in] blendR [-1.0]-movimento in posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param [in] epos  Posizione assi estesi, unità mm
    * @param [in] offset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param [in] offset_pos  Offset posa
    * @return Codice errore
    */
    int ExtAxisSyncMoveL(JointPos joint_pos, DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos);

Movimento Lineare Sincrono Assi Estesi UDP e Robot (Calcolo Cinematica Inversa Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento lineare sincrono assi estesi UDP e robot (calcolo cinematica inversa automatico)
    * @param  [in] desc_pos   Posa target cartesiana
    * @param  [in] tool  Numero sistema coordinate utensile, range [0~14]
    * @param  [in] user  Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] vel  Percentuale velocità, range [0~100]
    * @param  [in] acc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param  [in] ovl  Fattore scala velocità, range [0~100]
    * @param  [in] blendR [-1.0]-movimento in posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param  [in] epos  Posizione assi estesi, unità mm
    * @param  [in] offset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param  [in] offset_pos  Offset posa
    * @param  [in] config Configurazione spazio giunti soluzione inversa, [-1]-riferimento posizione giunti corrente, [0~7]-risoluzione basata specifica configurazione spazio giunti
    * @return  Codice errore
    */
    int ExtAxisSyncMoveL(DescPose desc_pos, int tool, int user, double vel, double acc, double ovl, double blendR, ExaxisPos epos, int offset_flag, DescPose offset_pos,int config)

Esempio Codice Movimento Lineare Sincrono Assi Estesi UDP e Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveL(Robot robot)
    {
        //1. Calibrare e applicare sistema coordinate utensile robot, è possibile utilizzare metodo a quattro o sei punti per calibrazione e applicazione sistema coordinate utensile, interfacce coinvolte:
        //  int SetToolPoint(int point_num); //Imposta punto riferimento utensile - metodo a sei punti
        //  int ComputeTool(ref DescPose tcp_pose); //Calcola sistema coordinate utensile
        //  int SetTcp4RefPoint(int point_num);  //Imposta punto riferimento utensile - metodo a quattro punti
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile - metodo a quattro punti
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Imposta e applica sistema coordinate utensile
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Imposta e applica lista sistemi coordinate utensile
        //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Impostare parametri assi estesi, incluso tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1); //Posizione installazione assi estesi
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è posizionatore monoasse, quindi basta un set di parametri driver, se si sceglie tipo asse esteso con più assi, ogni asse richiede parametri driver
        //4. Impostare abilitazione e homing degli assi selezionati
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Eseguire calibrazione e applicazione sistema coordinate assi estesi
        DescPose pos = new DescPose(/* Inserire coordinate punto calibrazione */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare asse esteso, quindi chiamare questa interfaccia 4 volte per completare calibrazione */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applica risultato calibrazione a sistema coordinate asse esteso
        //6. Calibrare sistema coordinate pezzo su asse esteso, necessarie seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Registrare punto di partenza movimento lineare sincrono
        DescPose startdescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos startjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserire coordinate punto partenza asse esteso */ );
        //8. Registrare coordinate punto arrivo movimento lineare sincrono
        DescPose enddescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos endjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos endexaxisPos =new ExaxisPos(/* Inserire coordinate punto arrivo asse esteso */);
        //9. Scrivere programma movimento sincrono
        //Spostarsi al punto di partenza, assumendo sistemi coordinate utensile e pezzo applicati entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20, 0);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveL(endjointPos, enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveL(enddescPose, 1, 1, 100, 100, 100, 0, endexaxisPos, 0, offdese,-1);
        robot.CloseRPC();
        return 0;
    }

Movimento Arco Sincrono Assi Estesi UDP e Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Movimento arco sincrono assi estesi UDP e robot
    * @param [in] joint_pos_p  Posizione giunti punto percorso, unità deg
    * @param [in] desc_pos_p   Posa cartesiana punto percorso
    * @param [in] ptool  Numero sistema coordinate utensile, range [0~14]
    * @param [in] puser  Numero sistema coordinate pezzo, range [0~14]
    * @param [in] pvel  Percentuale velocità, range [0~100]
    * @param [in] pacc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param [in] epos_p  Posizione assi estesi punto intermedio, unità mm
    * @param [in] poffset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param [in] offset_pos_p  Offset posa
    * @param [in] joint_pos_t  Posizione giunti punto target, unità deg
    * @param [in] desc_pos_t   Posa cartesiana punto target
    * @param [in] ttool  Numero sistema coordinate utensile, range [0~14]
    * @param [in] tuser  Numero sistema coordinate pezzo, range [0~14]
    * @param [in] tvel  Percentuale velocità, range [0~100]
    * @param [in] tacc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param [in] epos_t  Posizione assi estesi, unità mm
    * @param [in] toffset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param [in] offset_pos_t  Offset posa
    * @param [in] ovl  Fattore scala velocità, range [0~100]
    * @param [in] blendR [-1.0]-movimento in posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @return Codice errore
    */
    int ExtAxisSyncMoveC(JointPos joint_pos_p, DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, JointPos joint_pos_t, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR);

Movimento Arco Sincrono Assi Estesi UDP e Robot (Calcolo Cinematica Inversa Automatico)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: Java SDK-v1.0.8-3.8.5

.. code-block:: Java
    :linenos:

    /**
    * @brief  Movimento arco sincrono assi estesi UDP e robot (calcolo cinematica inversa automatico)
    * @param  [in] desc_pos_p   Posa cartesiana punto percorso
    * @param  [in] ptool  Numero sistema coordinate utensile, range [0~14]
    * @param  [in] puser  Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] pvel  Percentuale velocità, range [0~100]
    * @param  [in] pacc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param  [in] epos_p  Posizione assi estesi, unità mm
    * @param  [in] poffset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param  [in] offset_pos_p  Offset posa
    * @param  [in] desc_pos_t   Posa cartesiana punto target
    * @param  [in] ttool  Numero sistema coordinate utensile, range [0~14]
    * @param  [in] tuser  Numero sistema coordinate pezzo, range [0~14]
    * @param  [in] tvel  Percentuale velocità, range [0~100]
    * @param  [in] tacc  Percentuale accelerazione, range [0~100], non ancora disponibile
    * @param  [in] epos_t  Posizione assi estesi, unità mm
    * @param  [in] toffset_flag  0-nessun offset, 1-offset in sistema base/pezzo, 2-offset in sistema utensile
    * @param  [in] offset_pos_t  Offset posa
    * @param  [in] ovl  Fattore scala velocità, range [0~100]
    * @param  [in] blendR [-1.0]-movimento in posizione (bloccante), [0~1000.0]-raggio smoothing (non bloccante), unità mm
    * @param  [in] config Configurazione spazio giunti soluzione inversa, [-1]-riferimento posizione giunti corrente, [0~7]-risoluzione basata specifica configurazione spazio giunti
    * @return  Codice errore
    */
    int ExtAxisSyncMoveC(DescPose desc_pos_p, int ptool, int puser, double pvel, double pacc, ExaxisPos epos_p, int poffset_flag, DescPose offset_pos_p, DescPose desc_pos_t, int ttool, int tuser, double tvel, double tacc, ExaxisPos epos_t, int toffset_flag, DescPose offset_pos_t, double ovl, double blendR,int config)

Esempio Codice Movimento Arco Sincrono Assi Estesi UDP e Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public int testSyncMoveC(Robot robot)
    {
        //1. Calibrare e applicare sistema coordinate utensile robot, è possibile utilizzare metodo a quattro o sei punti per calibrazione e applicazione sistema coordinate utensile, interfacce coinvolte:
        //  int SetToolPoint(int point_num); //Imposta punto riferimento utensile - metodo a sei punti
        //  int ComputeTool(ref DescPose tcp_pose); //Calcola sistema coordinate utensile
        //  int SetTcp4RefPoint(int point_num);  //Imposta punto riferimento utensile - metodo a quattro punti
        //  int ComputeTcp4(ref DescPose tcp_pose);  //Calcola sistema coordinate utensile - metodo a quattro punti
        //  int SetToolCoord(int id, DescPose coord, int type, int install); //Imposta e applica sistema coordinate utensile
        //  int SetToolList(int id, DescPose coord, int type, int install);  //Imposta e applica lista sistemi coordinate utensile
        //2. Impostare parametri comunicazione UDP e caricare comunicazione UDP
        UDPComParam param=new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);
        robot.ExtDevLoadUDPDriver();
        //3. Impostare parametri assi estesi, incluso tipo asse esteso, parametri driver asse esteso, parametri DH asse esteso
        robot.SetAxisDHParaConfig(4, 200, 200, 0, 0, 0, 0, 0, 0); //Posizionatore monoasse e parametri DH
        robot.SetRobotPosToAxis(1); //Posizione installazione assi estesi
        robot.ExtAxisParamConfig(1, 0, 1, 100, -100, 10, 10, 12, 131072, 0, 1, 0, 0); //Parametri driver servo, questo esempio è posizionatore monoasse, quindi basta un set di parametri driver, se si sceglie tipo asse esteso con più assi, ogni asse richiede parametri driver
        //4. Impostare abilitazione e homing degli assi selezionati
        robot.ExtAxisServoOn(1, 0);
        robot.ExtAxisSetHoming(1, 0, 20, 3);
        //5. Eseguire calibrazione e applicazione sistema coordinate assi estesi
        DescPose pos = new DescPose(/* Inserire coordinate punto calibrazione */ );
        robot.SetRefPointInExAxisEnd(pos);
        robot.PositionorSetRefPoint(1); /* Sono necessari quattro punti in posizioni diverse per calibrare asse esteso, quindi chiamare questa interfaccia 4 volte per completare calibrazione */
        DescPose coord = new DescPose();
        robot.PositionorComputeECoordSys(coord); //Calcola risultato calibrazione asse esteso
        robot.ExtAxisActiveECoordSys(1, 1, coord, 1); //Applica risultato calibrazione a sistema coordinate asse esteso
        //6. Calibrare sistema coordinate pezzo su asse esteso, necessarie seguenti interfacce
        //int SetWObjCoordPoint(int point_num);
        //int ComputeWObjCoord(int method, ref DescPose wobj_pose);
        //int SetWObjCoord(int id, DescPose coord);
        //int SetWObjList(int id, DescPose coord);
        //7. Registrare punto di partenza movimento arco sincrono
        DescPose startdescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos startjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos startexaxisPos = new ExaxisPos(/* Inserire coordinate punto partenza asse esteso */ );
        //8. Registrare coordinate punto arrivo movimento arco sincrono
        DescPose enddescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos endjointPos = new JointPos(/*Inserire coordinate*/ );
        ExaxisPos endexaxisPos = new ExaxisPos(/* Inserire coordinate punto arrivo asse esteso */ );
        //9. Registrare coordinate punto intermedio movimento arco sincrono
        DescPose middescPose = new DescPose(/*Inserire coordinate*/ );
        JointPos midjointPos =new JointPos(/*Inserire coordinate*/ );
        ExaxisPos midexaxisPos = new ExaxisPos(/* Inserire coordinate asse esteso a punto intermedio arco robot */ );
        //10. Scrivere programma movimento sincrono
        //Spostarsi al punto di partenza, assumendo sistemi coordinate utensile e pezzo applicati entrambi 1
        robot.ExtAxisMove(startexaxisPos, 20, 0);
        DescPose offdese = new DescPose( 0, 0, 0, 0, 0, 0 );
        robot.MoveJ(startjointPos, startdescPose, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveC(midjointPos, middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, endjointPos, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0);
        robot.MoveJ(startjointPos, 1, 1, 100, 100, 100, startexaxisPos, 0, 0, offdese);
        //Iniziare movimento sincrono
        robot.ExtAxisSyncMoveC(middescPose, 1, 1, 100, 100, midexaxisPos, 0, offdese, enddescPose, 1, 1, 100, 100, endexaxisPos, 0, offdese, 100, 0,-1);
        robot.CloseRPC();
        return 0;
    }

Impostare DO Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta DO esteso
    * @param [in] DONum Numero DO
    * @param [in] bOpen Interruttore true-acceso; false-spento
    * @param [in] smooth Smoothing
    * @param [in] block Blocco
    * @return Codice errore
    */
    int SetAuxDO(int DONum, boolean bOpen, boolean smooth, boolean block);

Impostare AO Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta AO esteso
    * @param [in] AONum Numero AO
    * @param [in] value Valore analogico [0-4095]
    * @param [in] block Blocco
    * @return Codice errore
    */
    int SetAuxAO(int AONum, double value, boolean block);

Impostare Tempo Filtro Input DI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta tempo filtro input DI esteso
    * @param [in] filterTime Tempo filtro (ms)
    * @return  Codice errore
    */
    int SetAuxDIFilterTime(int filterTime);

Impostare Tempo Filtro Input AI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta tempo filtro input AI esteso
    * @param [in] AONum Numero AO
    * @param [in] filterTime Tempo filtro (ms)
    * @return Codice errore
    */
    int SetAuxAIFilterTime(int AONum, int filterTime);

Attendere Input DI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attende input DI esteso
    * @param [in] DINum Numero DI
    * @param [in] bOpen Interruttore 0-spento; 1-acceso
    * @param [in] time Tempo attesa massimo (ms)
    * @param [in] errorAlarm Continuare movimento
    * @return Codice errore
    */
    int WaitAuxDI(int DINum, boolean bOpen, int time, boolean errorAlarm);

Attendere Input AI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Attende input AI esteso
    * @param [in] AINum Numero AI
    * @param [in] sign 0-maggiore; 1-minore
    * @param [in] value Valore AI
    * @param [in] time Tempo attesa massimo (ms)
    * @param [in] errorAlarm Continuare movimento
    * @return Codice errore
    */
    int WaitAuxAI(int AINum, int sign, int value, int time, boolean errorAlarm);
    
Ottenere Valore DI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene valore DI esteso
    * @param [in] DINum Numero DI
    * @param [in] isNoBlock Non bloccante
    * @return List[0]:Codice errore; List[1] : isOpen 0-spento; 1-acceso
    */
    List<Integer> GetAuxDI(int DINum, boolean isNoBlock)

Ottenere Valore AI Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Ottiene valore AI esteso
    * @param [in] AINum Numero AI
    * @param [in] isNoBlock Non bloccante
    * @return List[0]:Codice errore; List[1] : value Valore input
    */
    List<Integer> GetAuxAI(int AINum, boolean isNoBlock);

Esempio Codice IO Esteso
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestAuxDOAO(Robot robot)
    {
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, true, false, true);
            robot.Sleep(100);
        }
        for (int i = 0; i < 128; i++)
        {
            robot.SetAuxDO(i, false, false, true);
            robot.Sleep(100);
        }

        for (int i = 0; i < 409; i++)
        {
            robot.SetAuxAO(0, i * 10, true);
            robot.SetAuxAO(1, 4095 - i * 10, true);
            robot.SetAuxAO(2, i * 10, true);
            robot.SetAuxAO(3, 4095 - i * 10, true);
            robot.Sleep(10);
        }

        robot.SetAuxDIFilterTime(10);
        robot.SetAuxAIFilterTime(0, 10);


        int curValue = -1;
        List<Integer> liter=new ArrayList<>();
        for (int i = 0; i < 4; i++)
        {
            liter = robot.GetAuxAI(i, true);
        }

        robot.WaitAuxDI(1, false, 1000, false);
        robot.WaitAuxAI(1, 1, 132, 1000, false);

        robot.CloseRPC();
        return 0;
    }

Abilitazione Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Abilitazione dispositivo mobile
    * @param [in] enable false-disabilitato; true-abilitato
    * @return Codice errore
    */
    int TractorEnable(Boolean enable);

Homing Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Homing dispositivo mobile
    * @return Codice errore
    */
    int TractorHoming();

Movimento Lineare Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimento lineare dispositivo mobile
    * @param [in] distance Distanza movimento lineare (mm)
    * @param [in] vel Percentuale velocità movimento lineare (0-100)
    * @return Codice errore
    */
    int TractorMoveL(double distance, double vel);

Movimento Arco Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Movimento arco dispositivo mobile
    * @param [in] radio Raggio movimento arco (mm)
    * @param [in] angle Angolo movimento arco (°)
    * @param [in] vel Percentuale velocità movimento lineare (0-100)
    * @return Codice errore
    */
    int TractorMoveC(double radio, double angle, double vel);

Arresto Movimento Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Arresto movimento dispositivo mobile
    * @return Codice errore
    */
    int TractorStop();

Esempio Codice Dispositivo Mobile
+++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static void main(String[] args)
    {
        Robot robot = new Robot();
        robot.SetReconnectParam(true,20,500);//Imposta numero riconnessioni, intervallo
        robot.LoggerInit(FrLogType.DIRECT, FrLogLevel.INFO, "D://log", 10, 10);
        int rtn = robot.RPC("192.168.58.2");
        if(rtn == 0)
        {
            System.out.println("Connessione rpc successo");
        }
        else
        {
            System.out.println("Connessione rpc fallita");
            return ;
        }
        UDPComParam param = new UDPComParam("192.168.58.88", 2021, 2, 100, 3, 100, 1, 100, 10,0);
        robot.ExtDevSetUDPComParam(param);//comunicazione assi estesi udp
        robot.ExtAxisParamConfig(1, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.ExtAxisParamConfig(2, 0, 0, 50000, -50000, 1000, 1000, 6.280, 16384, 200, 0, 0, 0);
        robot.SetAxisDHParaConfig(5, 0, 0, 0, 0, 0, 0, 0, 0);

        robot.TractorEnable(false);
        robot.Sleep(2000);
        robot.TractorEnable(true);
        robot.Sleep(2000);
        robot.TractorHoming();

        robot.Sleep(2000);
        robot.TractorMoveL(100, 20);
        robot.Sleep(5000);
        robot.TractorMoveL(-100, 20);
        robot.Sleep(5000);
        robot.TractorMoveC(300, 90, 20);
        robot.Sleep(2000);
        robot.TractorStop();//arresto carrello
        robot.TractorMoveC(300, -90, 20);
    }

Impostazione del Tempo di Completamento del Posizionamento per Assi di Estensione UDP
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief Imposta il tempo di completamento del posizionamento per assi di estensione UDP
    * @param time Tempo di completamento del posizionamento [ms]
    * @return Codice di errore
    */
    public int SetExAxisCmdDoneTime(double time)