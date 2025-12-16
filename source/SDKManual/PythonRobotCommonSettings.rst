Impostazioni comuni del robot
==============================

.. toctree:: 
    :maxdepth: 5

Impostazione punti riferimento utensile - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolPoint(point_num)``"
    "Descrizione", "Imposta i punti di riferimento dell'utensile - Metodo a sei punti"
    "Parametri obbligatori", "- ``point_num``: Numero del punto, intervallo [1~6]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo sistema di coordinate utensile - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeTool()``"
    "Descrizione", "Calcola il sistema di coordinate dell'utensile - Metodo a sei punti (calcolo dopo aver impostato sei punti di riferimento)"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Sistema di coordinate dell'utensile"

Impostazione punti riferimento utensile - Metodo a quattro punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetTcp4RefPoint(point_num)``"
    "Descrizione", "Imposta i punti di riferimento dell'utensile - Metodo a quattro punti"
    "Parametri obbligatori", "``point_num``: Numero del punto, intervallo [1~4]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Sistema di coordinate dell'utensile"

Calcolo sistema di coordinate utensile - Metodo a quattro punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeTcp4()``"
    "Descrizione", "Calcola il sistema di coordinate dell'utensile - Metodo a quattro punti (calcolo dopo aver impostato quattro punti di riferimento)"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``tcp_pose=[x,y,z,rx,ry,rz]``: Sistema di coordinate dell'utensile"

Calcolo sistema di coordinate utensile in base alle informazioni dei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeToolCoordWithPoints(method, pos)``"
    "Descrizione", "Calcola il sistema di coordinate dell'utensile in base alle informazioni dei punti"
    "Parametri obbligatori", "- ``method``: Metodo di calcolo; 0-Metodo a quattro punti; 1-Metodo a sei punti
    - ``pos``: Gruppo di posizioni articolari, lunghezza array 4 per metodo a 4 punti, 6 per metodo a 6 punti"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode 
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Sistema di coordinate utensile calcolato in base alle informazioni dei punti, unità [mm][°]"

Impostazione sistema di coordinate utensile
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolCoord(id,t_coord,type,install,toolID,loadNum)``"
    "Descrizione", "Imposta il sistema di coordinate dell'utensile"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [1~15];
    - ``t_coord``: Posa del centro utensile rispetto al centro della flangia terminale, unità [mm][°];
    - ``type``: 0-Sistema di coordinate utensile, 1-Sistema di coordinate sensore;
    - ``install``: Posizione di installazione, 0-Terminale del robot, 1-Esterno del robot
    - ``toolID``: ID utensile
    - ``loadNum``: Numero del carico"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione lista dei sistemi di coordinate utensile
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetToolList(id,t_coord ,type, install, loadNum)``"
    "Descrizione", "Imposta la lista dei sistemi di coordinate dell'utensile"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [1~15];
    - ``t_coord``: [x,y,z,rx,ry,rz] Posa del centro utensile rispetto al centro della flangia terminale, unità [mm][°];
    - ``type``: 0-Sistema di coordinate utensile, 1-Sistema di coordinate sensore;
    - ``install``: Posizione di installazione, 0-Terminale del robot, 1-Esterno del robot
    - ``loadNum``: Numero del carico"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento sistema di coordinate utensile corrente
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTCPOffset(flag=1)``"
    "Descrizione", "Ottiene il sistema di coordinate dell'utensile corrente"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "``flag``: 0-Bloccante, 1-Non bloccante  Predefinito 1"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``tcp_offset=[x,y,z,rx,ry,rz]``: Posa relativa del sistema di coordinate utensile corrente, unità [mm][°]"

Esempio di codice operazioni sistema di coordinate utensile robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posJ = [p1Joint, p2Joint, p3Joint, p4Joint, p5Joint, p6Joint]
    rtn,coordRtn = robot.ComputeToolCoordWithPoints(1, posJ)
    print(f"ComputeToolCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(4)
    robot.MoveJ(joint_pos=p5Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(5)
    robot.MoveJ(joint_pos=p6Joint,tool=0, user=0, vel=100)
    robot.SetToolPoint(6)
    rtn,coordRtn = robot.ComputeTool()
    print(f"6 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolList(1, coordRtn, 0, 0, 0)
    robot.MoveJ(joint_pos=p1Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0, user=0, vel=100)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool        {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(2, coordRtn, 0, 0, 1, 0)
    rtn,getCoord = robot.GetTCPOffset(0)
    print(f"GetTCPOffset    {rtn}  coord is {getCoord[0]} {getCoord[1]} {getCoord[2]} {getCoord[3]} {getCoord[4]} {getCoord[5]}")
    robot.CloseRPC()

Impostazione punti riferimento utensile esterno - Metodo a sei punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExTCPPoint(point_num)``"
    "Descrizione", "Imposta i punti di riferimento dell'utensile esterno - Metodo a tre punti"
    "Parametri obbligatori", "- ``point_num``: Numero del punto, intervallo [1~3]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo sistema di coordinate utensile esterno - Metodo a sei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeExTCF(point_num)``"
    "Descrizione", "Calcola il sistema di coordinate dell'utensile esterno - Metodo a tre punti (calcolo dopo aver impostato tre punti di riferimento)"
    "Parametri obbligatori", "``point_num``: Numero del punto, intervallo [1~3]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode 
    - ``etcp=[x,y,z,rx,ry,rz]``: Sistema di coordinate dell'utensile esterno"

Impostazione sistema di coordinate utensile esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExToolCoord(id,etcp,etool)``"
    "Descrizione", "Imposta il sistema di coordinate dell'utensile esterno"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [0~14];
    - ``etcp``: Sistema di coordinate dell'utensile esterno, unità [mm][°];
    - ``etool``: Sistema di coordinate dell'utensile terminale, unità [mm][°];"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione lista dei sistemi di coordinate utensile esterno
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetExToolList(id,etcp ,etool)``"
    "Descrizione", "Imposta la lista dei sistemi di coordinate dell'utensile esterno"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [0~14];
    - ``etcp``: Sistema di coordinate dell'utensile esterno, unità [mm][°];
    - ``etool``: Sistema di coordinate dell'utensile terminale, unità [mm][°];"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice operazioni sistema di coordinate utensile esterno robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
    p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]
    p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
    p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posTCP = [p1Desc, p2Desc, p3Desc]
    robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=50)
    robot.SetExTCPPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=50)
    robot.SetExTCPPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=50)
    robot.SetExTCPPoint(3)
    rtn,coordRtn = robot.ComputeExTCF()
    print(f"ComputeExTCF {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetExToolCoord(1, coordRtn, offdese)
    robot.SetExToolList(1, coordRtn, offdese)
    robot.CloseRPC()

Impostazione punti riferimento pezzo - Metodo a tre punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjCoordPoint(point_num)``"
    "Descrizione", "Imposta i punti di riferimento del pezzo - Metodo a tre punti"
    "Parametri obbligatori", "``point_num``: Numero del punto, intervallo [1~3]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo sistema di coordinate pezzo - Metodo a tre punti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeWObjCoord(method, refFrame)``"
    "Descrizione", "Calcola il sistema di coordinate del pezzo - Metodo a tre punti (calcolo dopo aver impostato tre punti di riferimento);"
    "Parametri obbligatori", "- ``method``: Metodo di calcolo 0: Origine-Asse X-Asse Z, 1: Origine-Asse X-Piano XY
    - ``refFrame``: Sistema di coordinate di riferimento"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode 
    - ``wobj_pose=[x,y,z,rx,ry,rz]``: Sistema di coordinate del pezzo"

Impostazione sistema di coordinate pezzo
+++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjCoord(id, coord, refFrame)``"
    "Descrizione", "Imposta il sistema di coordinate del pezzo"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [0~14];
    - ``coord``: Posa del sistema di coordinate del pezzo rispetto al centro della flangia terminale, unità [mm][°]
    - ``refFrame``: Sistema di coordinate di riferimento"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione lista dei sistemi di coordinate pezzo
+++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWObjList(id, coord, refFrame)``"
    "Descrizione", "Imposta la lista dei sistemi di coordinate del pezzo"
    "Parametri obbligatori", "- ``id``: Numero del sistema di coordinate, intervallo [0~14];
    - ``coord``: Posa del sistema di coordinate del pezzo rispetto al centro della flangia terminale, unità [mm][°]
    - ``refFrame``: Sistema di coordinate di riferimento"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo sistema di coordinate pezzo in base alle informazioni dei punti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.8

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeWObjCoordWithPoints(method, pos, refFrame)``"
    "Descrizione", "Calcola il sistema di coordinate del pezzo in base alle informazioni dei punti"
    "Parametri obbligatori", "- ``method``: Metodo di calcolo; 0: Origine-Asse X-Asse Z  1: Origine-Asse X-Piano XY
    - ``pos``: Tre gruppi di posizioni TCP
    - ``refFrame``: Sistema di coordinate di riferimento"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode 
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Sistema di coordinate del pezzo calcolato in base alle informazioni dei punti, unità [mm][°]"

Ottenimento sistema di coordinate pezzo corrente
+++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWObjOffset(flag=1)``"
    "Descrizione", "Ottiene il sistema di coordinate del pezzo corrente"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "``flag``: 0-Bloccante, 1-Non bloccante, Predefinito 1"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``wobj_offset=[x,y,z,rx,ry,rz]``: Posa relativa del sistema di coordinate del pezzo corrente, unità [mm][°]"

Esempio di codice operazioni sistema di coordinate pezzo robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [-89.606, 779.517, 193.516, 178.000, 0.476, -92.484]
    p2Desc = [-24.656, 850.384, 191.361, 177.079, -2.058, -95.355]
    p3Desc = [-99.813, 766.661, 241.878, -176.817, 1.917, -91.604]
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    p2Joint = [-111.024, -41.538, 69.222, -114.913, -87.743, 74.329]
    p3Joint = [-107.266, -56.116, 85.971, -122.560, -92.548, 74.331]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 0, 0, 0, 0]
    posTCP = [p1Desc, p2Desc, p3Desc]
    rtn,coordRtn = robot.ComputeWObjCoordWithPoints(1, posTCP, 0)
    print(f"ComputeWObjCoordWithPoints    {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.MoveJ(joint_pos=p1Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=1, user=0, vel=100)
    robot.SetWObjCoordPoint(3)
    rtn,coordRtn = robot.ComputeWObjCoord(1, 0)
    print(f"ComputeWObjCoord   {rtn}  coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} {coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetWObjCoord(1, coordRtn, 0)
    robot.SetWObjList(1, coordRtn, 0)
    rtn,getWobjDesc = robot.GetWObjOffset(0)
    print(f"GetWObjOffset    {rtn}  coord is {getWobjDesc[0]} {getWobjDesc[1]} {getWobjDesc[2]} {getWobjDesc[3]} {getWobjDesc[4]} {getWobjDesc[5]}")
    robot.CloseRPC()

Impostazione velocità globale
++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSpeed(vel)``"
    "Descrizione", "Imposta la velocità globale"
    "Parametri obbligatori", "- ``vel``: Percentuale velocità, intervallo [0~100]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione accelerazione robot
+++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.0.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetOaccScale(acc)``"
    "Descrizione", "Imposta l'accelerazione del robot"
    "Parametri obbligatori", "- ``acc``: Percentuale accelerazione robot"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento velocità predefinita
+++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetDefaultTransVel()``"
    "Descrizione", "Ottiene la velocità predefinita"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``vel``: Velocità predefinita, unità [mm/s]"

Impostazione peso carico terminale
+++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoadWeight(loadNum, weight)``"
    "Descrizione", "Imposta il peso del carico terminale, un'impostazione errata del peso del carico potrebbe causare la perdita di controllo del robot in modalità trascinamento"
    "Parametri obbligatori", "- ``loadNum``: Numero del carico
    - ``weight``: Unità [kg]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coordinate centro di massa carico terminale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetLoadCoord(x,y,z,loadNum = 0)``"
    "Descrizione", "Imposta le coordinate del centro di massa del carico terminale, un'impostazione errata del centro di massa del carico potrebbe causare la perdita di controllo del robot in modalità trascinamento"
    "Parametri obbligatori", "- ``x``: Coordinata centro di massa, unità [mm]
    - ``y``: Coordinata centro di massa, unità [mm]
    - ``z``: Coordinata centro di massa, unità [mm]"
    "Parametri predefiniti", "- ``loadNum``: Numero del carico, predefinito 0"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento peso carico corrente
+++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayload(flag=1)``"
    "Descrizione", "Ottiene la massa del carico corrente"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "``flag``: 0-Bloccante, 1-Non bloccante  Predefinito 1"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``weight``: Peso del carico corrente, unità [kg]"

Ottenimento centro di massa carico corrente
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetTargetPayloadCog(flag=1)``"
    "Descrizione", "Ottiene il centro di massa del carico corrente"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "``flag``: 0-Bloccante, 1-Non bloccante  Predefinito 1"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``cog=[x,y,z]``: Coordinate del centro di massa corrente, unità [mm]"

Impostazione modalità installazione robot - Installazione fissa
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotInstallPos(method)``"
    "Descrizione", "Imposta la modalità di installazione del robot - Installazione fissa, un'impostazione errata della modalità di installazione potrebbe causare la perdita di controllo del robot in modalità trascinamento"
    "Parametri obbligatori", "- ``method``: 0-Montaggio a terra, 1-Montaggio laterale, 2-Montaggio a soffitto"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione angolo installazione robot - Installazione libera
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetRobotInstallAngle(yangle,zangle)``"
    "Descrizione", "Imposta l'angolo di installazione del robot - Installazione libera, un'impostazione errata dell'angolo di installazione potrebbe causare la perdita di controllo del robot in modalità trascinamento"
    "Parametri obbligatori", "- ``yangle``: Angolo di inclinazione
    - ``zangle``: Angolo di rotazione"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento angolo installazione robot
+++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotInstallAngle()``"
    "Descrizione", "Ottiene l'angolo di installazione del robot"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``[yangle,zangle]``: yangle-angolo di inclinazione, zangle-angolo di rotazione"

Impostazione valore variabile di sistema
+++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetSysVarValue(id,value)``"
    "Descrizione", "Imposta la variabile di sistema"
    "Parametri obbligatori", "- ``id``: Numero della variabile, intervallo [1~20];
    - ``value``: Valore della variabile"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento valore variabile di sistema
++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSysVarValue(id)``"
    "Descrizione", "Ottiene il valore della variabile di sistema"
    "Parametri obbligatori", "- ``id``: Numero della variabile di sistema, intervallo [1~20]"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``var_value``: Valore della variabile di sistema"

Esempio di codice impostazioni comuni robot
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    for i in range(1, 100):
        robot.SetSpeed(i)
        robot.SetOaccScale(i)
        time.sleep(0.03)
    error,defaultVel = robot.GetDefaultTransVel()
    print(f"GetDefaultTransVel is {defaultVel}")
    for i in range(1, 21):
        robot.SetSysVarValue(i, i + 0.5)
        time.sleep(0.1)
    for i in range(1, 21):
        value = robot.GetSysVarValue(i)
        print(f"sys value {i} is: {value}")
        time.sleep(0.1)
    robot.SetLoadWeight(0, 2.5)
    robot.SetLoadCoord(3.0,4.0,5.0)
    time.sleep(1)
    error,getLoad = robot.GetTargetPayload(0)
    error,getLoadTran = robot.GetTargetPayloadCog(0)
    print(f"get load is {getLoad}; get load cog is {getLoadTran[0]} {getLoadTran[1]} {getLoadTran[2]}")
    robot.SetRobotInstallPos(0)
    robot.SetRobotInstallAngle(15.0, 25.0)
    error,[anglex, angley] = robot.GetRobotInstallAngle()
    print(f"GetRobotInstallAngle x: {anglex}; y: {angley}")
    robot.CloseRPC()

Interruttore compensazione attrito giunti
++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FrictionCompensationOnOff(state)``"
    "Descrizione", "Interruttore compensazione attrito giunti"
    "Parametri obbligatori", "- ``state``: 0-Spegnimento, 1-Accensione"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coefficiente compensazione attrito giunti - Montaggio normale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_level(coeff)``"
    "Descrizione", "Imposta il coefficiente di compensazione attrito giunti - Installazione fissa - Montaggio normale"
    "Parametri obbligatori", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Sei coefficienti di compensazione dei giunti"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coefficiente compensazione attrito giunti - Montaggio laterale
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_wall(coeff)``"
    "Descrizione", "Imposta il coefficiente di compensazione attrito giunti - Installazione fissa - Montaggio laterale"
    "Parametri obbligatori", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Sei coefficienti di compensazione dei giunti"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coefficiente compensazione attrito giunti - Montaggio a soffitto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_ceiling(coeff)``"
    "Descrizione", "Imposta il coefficiente di compensazione attrito giunti - Installazione fissa - Montaggio a soffitto"
    "Parametri obbligatori", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Sei coefficienti di compensazione dei giunti"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coefficiente compensazione attrito giunti - Installazione libera
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFrictionValue_freedom(coeff)``"
    "Descrizione", "Imposta il coefficiente di compensazione attrito giunti - Installazione libera"
    "Parametri obbligatori", "- ``coeff=[j1,j2,j3,j4,j5,j6]``: Sei coefficienti di compensazione dei giunti"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice impostazione compensazione attrito giunti robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    lcoeff = [0.9, 0.9, 0.9, 0.9, 0.9, 0.9]
    wcoeff = [0.4, 0.4, 0.4, 0.4, 0.4, 0.4]
    ccoeff = [0.6, 0.6, 0.6, 0.6, 0.6, 0.6]
    fcoeff = [0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
    rtn = robot.FrictionCompensationOnOff(1)
    print(f"FrictionCompensationOnOff rtn is {rtn}")
    rtn = robot.SetFrictionValue_level(lcoeff)
    print(f"SetFrictionValue_level rtn is {rtn}")
    rtn = robot.SetFrictionValue_wall(wcoeff)
    print(f"SetFrictionValue_wall rtn is {rtn}")
    rtn = robot.SetFrictionValue_ceiling(ccoeff)
    print(f"SetFrictionValue_ceiling rtn is {rtn}")
    rtn = robot.SetFrictionValue_freedom(fcoeff)
    print(f"SetFrictionValue_freedom rtn is {rtn}")
    robot.CloseRPC()

Query codice errore robot
++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetRobotErrorCode()``"
    "Descrizione", "Query codice errore robot"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``[maincode subcode]``: Codice errore robot, maincode-codice errore principale, subcode-codice errore secondario"

Cancellazione stato errore
+++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ResetAllError()``"
    "Descrizione", "Cancellazione stato errore, può cancellare solo errori resettabili"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice ottenimento stato guasto robot e cancellazione errori
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    p1Joint = [-108.145, -50.137, 85.818, -125.599, -87.946, 74.329]
    robot.MoveJ(joint_pos=p1Joint, tool=5, user=2, vel=50)
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    time.sleep(1)
    robot.ResetAllError()
    time.sleep(1)
    error,[maincode, subcode] = robot.GetRobotErrorCode()
    print(f"robot maincode is {maincode}; subcode is {subcode}")
    robot.CloseRPC()

Impostazione parametri monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetWideBoxTempFanMonitorParam(enable, period)``"
    "Descrizione", "Imposta i parametri di monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga"
    "Parametri obbligatori", "- ``enable``: 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    - ``period``: Periodo di monitoraggio (s), intervallo 1-100"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento parametri monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.3

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetWideBoxTempFanMonitorParam()``"
    "Descrizione", "Ottiene i parametri di monitoraggio temperatura e velocità ventilatore quadro controllo tensione larga"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``enable``: 0-Disabilita monitoraggio; 1-Abilita monitoraggio
    - ``period``: Periodo di monitoraggio (s), intervallo 1-100"

Esempio di codice ottenimento stato temperatura e corrente ventilatore quadro controllo tensione larga
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    robot.SetWideBoxTempFanMonitorParam(1, 2)
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    rtn = robot.SetWideBoxTempFanMonitorParam(0, 2)
    print(f"SetWideBoxTempFanMonitorParam rtn is:{rtn}")
    error, enable, period = robot.GetWideBoxTempFanMonitorParam()
    print(f"GetWideBoxTempFanMonitorParam enable is:{enable},period is:{period}")
    for i in range(100):
        error, pkg = robot.GetRobotRealTimeState()
        print(f"robot ctrl box temp is:{pkg.wideVoltageCtrlBoxTemp},fan current is:{pkg.wideVoltageCtrlBoxFanCurrent}")
        time.sleep(0.1)
    robot.CloseRPC()

Impostazione punto calibrazione fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFocusCalibPoint(pointNum, point)``"
    "Descrizione", "Imposta il punto di calibrazione del fuoco"
    "Parametri obbligatori", "- ``pointNum``: Numero punto calibrazione fuoco 1-8
    - ``point``: Coordinate del punto di calibrazione"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Calcolo risultato calibrazione fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``ComputeFocusCalib(pointNum)``"
    "Descrizione", "Calcola il risultato della calibrazione del fuoco"
    "Parametri obbligatori", "- ``pointNum``: Numero di punti di calibrazione"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``resultPos``: Risultato calibrazione XYZ
    - ``accuracy``: Errore di accuratezza della calibrazione"

Avvio inseguimento fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FocusStart(kp=50.0, kpredic=19.0, aMax=1440, vMax=180, type=0)``"
    "Descrizione", "Avvia l'inseguimento del fuoco"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "- ``kp``: Parametro proporzionale, predefinito 50.0
    - ``kpredic``: Parametro feedforward, predefinito 19.0
    - ``aMax``: Limite massima accelerazione angolare, predefinito 1440°/s^2
    - ``vMax``: Limite massima velocità angolare, predefinito 180°/s
    - ``type``: Blocco direzione asse X (0-Vettore input di riferimento; 1-Orizzontale; 2-Verticale), predefinito 0"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Arresto inseguimento fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``FocusEnd()``"
    "Descrizione", "Arresta l'inseguimento del fuoco"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Impostazione coordinate fuoco
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.4

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetFocusPosition(pos)``"
    "Descrizione", "Imposta le coordinate del fuoco"
    "Parametri obbligatori", "- ``pos``: Coordinate fuoco XYZ"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice inseguimento fuoco robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    p1Desc = [186.331, 487.913, 209.850, 149.030, 0.688, -114.347]
    p1Joint = [-127.876, -75.341, 115.417, -122.741, -59.820, 74.300]
    p2Desc = [69.721, 535.073, 202.882, -144.406, -14.775, -89.012]
    p2Joint = [-101.780, -69.828, 110.917, -125.740, -127.841, 74.300]
    p3Desc = [146.861, 578.426, 205.598, 175.997, -36.178, -93.437]
    p3Joint = [-112.851, -60.191, 86.566, -80.676, -97.463, 74.300]
    p4Desc = [136.284, 509.876, 225.613, 178.987, 1.372, -100.696]
    p4Joint = [-116.397, -76.281, 113.845, -128.611, -88.654, 74.299]
    p5Desc = [138.395, 505.972, 298.016, 179.134, 2.147, -101.110]
    p5Joint = [-116.814, -82.333, 109.162, -118.662, -88.585, 74.302]
    p6Desc = [105.553, 454.325, 232.017, -179.426, 0.444, -99.952]
    p6Joint = [-115.649, -84.367, 122.447, -128.663, -90.432, 74.303]
    exaxisPos = [0, 0, 0, 0]
    offdese = [0, 0, 100, 0, 0, 0]
    robot.MoveJ(joint_pos=p1Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(1)
    robot.MoveJ(joint_pos=p2Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(2)
    robot.MoveJ(joint_pos=p3Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(3)
    robot.MoveJ(joint_pos=p4Joint,tool=0,user=0,vel=100,acc=100,ovl=100,exaxis_pos=exaxisPos,blendT=-1,offset_flag=0,offset_pos=offdese)
    robot.SetTcp4RefPoint(4)
    rtn,coordRtn = robot.ComputeTcp4()
    print(f"4 Point ComputeTool {rtn} coord is {coordRtn[0]} {coordRtn[1]} {coordRtn[2]} "
          f"{coordRtn[3]} {coordRtn[4]} {coordRtn[5]}")
    robot.SetToolCoord(1, coordRtn, 0, 0, 1, 0)
    error, p1Desc = robot.GetForwardKin(p1Joint)
    error, p2Desc = robot.GetForwardKin(p2Joint)
    error, p3Desc = robot.GetForwardKin(p3Joint)
    robot.SetFocusCalibPoint(1, p1Desc)
    robot.SetFocusCalibPoint(2, p2Desc)
    robot.SetFocusCalibPoint(3, p3Desc)
    rtn, resultPos, accuracy = robot.ComputeFocusCalib(pointNum=3)
    print(f"ComputeFocusCalib coord is {rtn} {resultPos[0]} {resultPos[1]} {resultPos[2]} accuracy is {accuracy}")
    rtn = robot.SetFocusPosition(resultPos)
    error, p5Desc = robot.GetForwardKin(p5Joint)
    error, p6Desc = robot.GetForwardKin(p6Joint)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusStart(50, 19, 710, 90, 0)
    robot.MoveL(desc_pos=p5Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.MoveL(desc_pos=p6Desc,tool=1,user=0,vel=10,acc=100,ovl=100,blendR=-1,blendMode=0,exaxis_pos=exaxisPos,search=0,offset_flag=1,offset_pos=offdese)
    robot.FocusEnd()
    robot.CloseRPC()

Abilitazione funzione calibrazione sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityEnable(status)``"
    "Descrizione", "Abilita la funzione di calibrazione sensibilità sensore coppia giunti"
    "Parametri obbligatori", "- ``status``: 0-Disabilita; 1-Abilita"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Raccolta dati sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityCollect()``"
    "Descrizione", "Raccolta dati sensibilità sensore coppia giunti"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento risultato calibrazione sensibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityCalibration()``"
    "Descrizione", "Ottiene il risultato della calibrazione sensibilità sensore coppia giunti"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``calibResult``: Sensibilità giunti j1~j6 [0-1]
    - ``linearityn``: Linearità giunti j1~j6 [0-1]"

Ottenimento errore isteresi sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointHysteresisError()``"
    "Descrizione", "Ottiene l'errore di isteresi del sensore coppia giunti"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``hysteresisError``: Errore di isteresi giunti j1~j6"

Ottenimento ripetibilità sensore coppia giunti
+++++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointRepeatability()``"
    "Descrizione", "Ottiene la ripetibilità del sensore coppia giunti"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``repeatability``: Ripetibilità giunti j1~j6"

Impostazione parametri sensore forza giunti
++++++++++++++++++++++++++++++++++++++++++++
.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetAdmittanceParams(M, B, K, threshold, sensitivity, setZeroFlag)``"
    "Descrizione", "Imposta i parametri del sensore forza giunti"
    "Parametri obbligatori", "
    - ``M``: Coefficiente massa J1-J6 [0.001 ~ 10]
    - ``B``: Coefficiente smorzamento J1-J6 [0.001 ~ 10]
    - ``K``: Coefficiente rigidezza J1-J6 [0.001 ~ 10]
    - ``threshold``: Soglia controllo forza, Nm
    - ``sensitivity``: Sensibilità, Nm/V, [0 ~ 10]
    - ``setZeroFlag``: Flag abilitazione funzione; 0-Disabilita; 1-Abilita; 2-Registra zero posizione1; 3-Registra zero posizione2"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice calibrazione automatica sensibilità sensore coppia giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    robot = Robot.RPC('192.168.58.2')
    rtn = robot.JointSensitivityEnable(0)
    rtn = robot.JointSensitivityEnable(1)
    print(f"JointSensitivityEnable rtn is {rtn}")
    curJPos = [0.0] * 6
    rtn, curJPos = robot.GetActualJointPosDegree(0)
    epos = [0.0] * 4
    offset_pos = [0.0] * 6
    jointPos1 = [curJPos[0], 0.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos1 = [0.0] * 6
    rtn, descPos1 = robot.GetForwardKin(jointPos1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 1 rtn is {rtn}")
    time.sleep(0.1)
    jointPos2 = [curJPos[0], -30.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos2 = [0.0] * 6
    rtn, descPos2 = robot.GetForwardKin(jointPos2)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 2 rtn is {rtn}")
    time.sleep(0.1)
    jointPos3 = [curJPos[0], -60.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos3 = [0.0] * 6
    rtn, descPos3 = robot.GetForwardKin(jointPos3)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 3 rtn is {rtn}")
    time.sleep(0.1)
    jointPos4 = [curJPos[0], -90.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos4 = [0.0] * 6
    rtn, descPos4 = robot.GetForwardKin(jointPos4)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 4 rtn is {rtn}")
    time.sleep(0.1)
    jointPos5 = [curJPos[0], -120.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos5 = [0.0] * 6
    rtn, descPos5 = robot.GetForwardKin(jointPos5)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 5 rtn is {rtn}")
    time.sleep(0.1)
    jointPos6 = [curJPos[0], -150.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos6 = [0.0] * 6
    rtn, descPos6 = robot.GetForwardKin(jointPos6)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 6 rtn is {rtn}")
    time.sleep(0.1)
    jointPos7 = [curJPos[0], -180.0, 0.0, -90.0, 0.02, curJPos[5]]
    descPos7 = [0.0] * 6
    rtn, descPos7 = robot.GetForwardKin(jointPos7)
    robot.MoveJ(joint_pos=jointPos7, desc_pos=descPos7, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 7 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos6, desc_pos=descPos6, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 8 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos5, desc_pos=descPos5, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 9 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos4, desc_pos=descPos4, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 10 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos3, desc_pos=descPos3, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 11 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos2, desc_pos=descPos2, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.1)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 12 rtn is {rtn}")
    time.sleep(0.1)
    robot.MoveJ(joint_pos=jointPos1, desc_pos=descPos1, tool=0, user=0, vel=100, acc=100, ovl=100, exaxis_pos=epos, blendT=-1, offset_flag=0, offset_pos=offset_pos)
    time.sleep(0.2)
    rtn = robot.JointSensitivityCollect()
    print(f"JointSensitivityCollect 13 rtn is {rtn}")
    time.sleep(0.1)
    calibResult = [0.0] * 6
    linearity = [0.0] * 6
    rtn,calibResult, linearity = robot.JointSensitivityCalibration()
    print(f"JointSensitivityCalibration rtn is {rtn}")
    rtn = robot.JointSensitivityEnable(0)
    print(f"JointSensitivityEnable rtn is {rtn}")
    print(f"jointSensor Calib result is {calibResult[0]},{calibResult[1]},{calibResult[2]},{calibResult[3]},{calibResult[4]},{calibResult[5]}")
    print( f"jointSensor linearity is {linearity[0]},{linearity[1]},{linearity[2]},{linearity[3]},{linearity[4]},{linearity[5]}")
    hysteresisError = [0.0] * 6
    rtn,hysteresisError = robot.JointHysteresisError()
    print(f"JointHysteresisError result is {hysteresisError[0]},{hysteresisError[1]},{hysteresisError[2]},{hysteresisError[3]},{hysteresisError[4]},{hysteresisError[5]}")
    repeatability = [0.0] * 6
    rtn,repeatability = robot.JointRepeatability()
    print(f"JointRepeatability result is {repeatability[0]},{repeatability[1]},{repeatability[2]},{repeatability[3]},{repeatability[4]},{repeatability[5]}")
    M = [1.0] * 6
    B = [1.0] * 6
    K = [0.0] * 6
    threshold = [1.0] * 6
    setZeroFlag = 1
    rtn = robot.SetAdmittanceParams(M, B, K, threshold, calibResult, setZeroFlag)
    print(f"SetAdmittanceParams rtn is {rtn}")
    robot.CloseRPC()

Ottenimento conteggio frame errore 8 porte slave robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetSlavePortErrCounter()``"
    "Descrizione", "Ottiene il conteggio frame errore 8 porte slave robot"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``inRecvErr``: Conteggio frame errore ricezione input
    - ``inCRCErr``: Conteggio frame errore CRC input
    - ``inTransmitErr``: Conteggio frame errore trasmissione input
    - ``inLinkErr``: Conteggio frame errore collegamento input
    - ``outRecvErr``: Conteggio frame errore ricezione output
    - ``outCRCErr``: Conteggio frame errore CRC output
    - ``outTransmitErr``: Conteggio frame errore trasmissione output
    - ``outLinkErr``: Conteggio frame errore collegamento output"

Azzera conteggio frame errore porte slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``JointSensitivityEnable(slaveID)``"
    "Descrizione", "Azzera il conteggio frame errore porte slave"
    "Parametri obbligatori", "- ``slaveID``: Numero slave 0~7"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Esempio di codice ottenimento conteggio frame errore porte slave
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    inRecvErr = [0] * 8
    inCRCErr = [0] * 8
    inTransmitErr = [0] * 8
    inLinkErr = [0] * 8
    outRecvErr = [0] * 8
    outCRCErr = [0] * 8
    outTransmitErr = [0] * 8
    outLinkErr = [0] * 8
    rtn,inRecvErr, inCRCErr, inTransmitErr, inLinkErr, outRecvErr, outCRCErr, outTransmitErr, outLinkErr = robot.GetSlavePortErrCounter()
    for i in range(8):
        if inRecvErr[i] != 0:
            print(f"inRecvErr {i} is {inRecvErr[i]}")
        if inCRCErr[i] != 0:
            print(f"inCRCErr {i} is {inCRCErr[i]}")
        if inTransmitErr[i] != 0:
            print(f"inTransmitErr {i} is {inTransmitErr[i]}")
        if inLinkErr[i] != 0:
            print(f"inLinkErr {i} is {inLinkErr[i]}")
        if outRecvErr[i] != 0:
            print(f"outRecvErr {i} is {outRecvErr[i]}")
        if outCRCErr[i] != 0:
            print(f"outCRCErr {i} is {outCRCErr[i]}")
        if outTransmitErr[i] != 0:
            print(f"outTransmitErr {i} is {outTransmitErr[i]}")
        if outLinkErr[i] != 0:
            print(f"outLinkErr {i} is {outLinkErr[i]}")
    print("others has no err!")
    for i in range(8):
        robot.SlavePortErrCounterClear(i)
    robot.CloseRPC()

Impostazione coefficiente feedforward velocità assi
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``SetVelFeedForwardRatio(radio)``"
    "Descrizione", "Imposta il coefficiente feedforward velocità assi"
    "Parametri obbligatori", "- ``radio``: Coefficiente feedforward velocità assi"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "Codice di errore Successo-0  Fallimento- errcode"

Ottenimento coefficiente feedforward velocità assi
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: python SDK-v2.1.7

.. csv-table:: 
    :stub-columns: 1
    :widths: 10 30

    "Prototipo", "``GetVelFeedForwardRatio()``"
    "Descrizione", "Ottiene il coefficiente feedforward velocità assi"
    "Parametri obbligatori", "Nessuno"
    "Parametri predefiniti", "Nessuno"
    "Valore di ritorno", "- Codice di errore Successo-0  Fallimento- errcode
    - ``radio``: Coefficiente feedforward velocità assi"

Esempio di codice coefficiente feedforward velocità robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: python
    :linenos:

    from fairino import Robot
    import time
    import threading
    # Stabilisce una connessione con il controllore robot, restituisce un oggetto robot se la connessione ha successo
    robot = Robot.RPC('192.168.58.2')
    setRadio = [1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
    robot.SetVelFeedForwardRatio(setRadio)
    getRadio = [0.0] * 6
    rtn,getRadio = robot.GetVelFeedForwardRatio()
    print(f"{getRadio[0]},{getRadio[1]},{getRadio[2]},{getRadio[3]},{getRadio[4]},{getRadio[5]}")
    robot.CloseRPC()