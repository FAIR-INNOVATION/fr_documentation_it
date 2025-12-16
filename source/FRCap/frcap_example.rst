Casi Studio FRCap
=========================

.. toctree:: 
   :maxdepth: 6

FAIRINO Palletizer (Palletizzatore)
---------------------------------------------

Dopo aver caricato, registrato e abilitato il file "码垛机Palletizer.plugin" dalla cartella "build" del progetto nel WebApp, sarà possibile utilizzarlo.

.. image:: frcap_pictures/011.png
   :width: 6in
   :align: center

.. centered:: Figura 7.1 Utilizzo FRCap Palletizzazione

Configurazione Pezzo da Palletizzare
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `palletizing_config_box`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  int length Lunghezza pezzo
   * @param  int width Larghezza pezzo
   * @param  int height Altezza pezzo
   * @param  int payload Carico pezzo
   * @param  string grip_point Punto di presa pezzo
   * /

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_box",
      data: {
         length: 800,
         width: 615,
         height: 312,
         payload: 2.34,
         grip_point: "grippoint"
      }
   } 

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Configurazione Pallet di Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `palletizing_config_pallet`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  int front Lato anteriore pallet
   * @param  int side Lato laterale pallet
   * @param  int height Altezza pallet
   * @param  int left_pallet Abilita pallet sinistro
   * @param  int right_pallet Abilita pallet destro
   */

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pallet",
      data: {
            front: 1200,
            side: 1000,
            height: 110,
            left_pallet: 0,
            right_pallet: 1
         }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */ 

Configurazione Avanzata Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `palletizing_advanced_cfg`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  string height Altezza sollevamento punto presa palletizzazione
   * @param  string x1 Punto approccio 1 palletizzazione: offset direzione x, unità mm
   * @param  string y1 Punto approccio 1 palletizzazione: offset direzione y, unità mm
   * @param  string z1 Punto approccio 1 palletizzazione: offset direzione z, unità mm
   * @param  string x2 Punto approccio 2 palletizzazione: offset direzione x, unità mm
   * @param  string y2 Punto approccio 2 palletizzazione: offset direzione y, unità mm
   * @param  string z2 Punto approccio 2 palletizzazione: offset direzione z, unità mm
   * @param  string time Tempo attesa presa materiale, unità ms
   */ 

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_advanced_cfg",
      data: {
      height: "1000",
            x1: "100",
            y1: "100",
            z1: "100",
            x2: "10",
            y2: "10",
            z2: "10",
            time: "1"
         }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Configurazione Dimensioni Dispositivo Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `palletizing_config_device`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  int x Valore assoluto direzione x del punto superiore destro del pallet sinistro rispetto all'asse del sistema di coordinate base del robot
   * @param  int y Valore assoluto direzione y del punto superiore destro del pallet sinistro rispetto all'asse del sistema di coordinate base del robot
   * @param  int z Valore assoluto direzione z del punto superiore destro del pallet sinistro rispetto all'asse del sistema di coordinate base del robot
   * @param  int angle Angolo di rotazione durante l'installazione del robot
   */ 

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_device",
      data: {
         x: 2400,
         y: 1800,
         z: 120,
         angle: 0   
      }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   */

Configurazione Modello Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `palletizing_config_pattern`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  int layers Numero strati palletizzazione
   * @param  int box_gap Intervallo punti pixel pezzo, unità: mm
   * @param  string sequence Modalità lavoro palletizzazione
   * @param  int pattern_b_enable Se abilitare modello b, 1: abilita, 0: non abilitare
   * @param  string left_pattern_a Coordinate cartesiane modello a stazione sinistra
   * @param  string left_pattern_b Coordinate cartesiane modello b stazione sinistra
   * @param  string right_pattern_a Coordinate cartesiane modello a stazione destra
   * @param  string right_pattern_b Coordinate cartesiane modello b stazione destra
   * @param  string origin_pattern_a Coordinate cartesiane modello a iniziale
   * @param  string origin_pattern_b Coordinate cartesiane modello b iniziale
   */

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "palletizing_config_pattern",
      data: {
         layers: 8,
         box_gap: 0,
         sequence: "a,b,a,b,a,b,a,b",
         pattern_b_enable: 1,
         left_pattern_a: "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
         "origin_pattern_a": "[]",
         "origin_pattern_b": "[]"
      }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   """

Generazione Programma Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `generate_palletizing_program`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /**
   * @param  string palletizing_name Nome palletizzazione
   * @param  string depalletizing_name Nome depalletizzazione
   * @param  string flag Se generare programma palletizzazione o depalletizzazione, 0-non generare, 1-genera
   */ 

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "generate_palletizing_program",
      data: {
         palletizing_name: "palletizing_1",
         depalletizing_name:"depalletizing_1",
         flag:"[0,1]"
      }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 "success"
   * @return status:404 "fail"
   """

Ottenere Ricetta Palletizzazione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `get_palletizing_formula`.

Parametri Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @param  string name Nome ricetta palletizzazione
   */ 

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula",
      data: {
         name: "palletizing_1"
      }
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 
   * @param  object box_config Configurazione pezzo
   * @param  object pallet_config Configurazione pallet
   * @param  object device_config Posizione dispositivo installazione
   * @param  object pattern_config Configurazione modello
   * @param  object program_config Configurazione generazione programma
   * @param  object lefttransitionpoint Coordinate cartesiane punto transizione sinistro
   * @param  object righttransitionpoint Coordinate cartesiane punto transizione destro
   * @param  object advanced_config Configurazione avanzata
   * @return status:404 "fail"
   """

Esempio Feedback Comando:

.. code-block:: c++
   :linenos:

   {
      "box_config": {
        "flag": 1,
        "length": 200,
        "width": 400,
        "height": 300,
        "payload": 2.34,
        "grip_point": "grippoint"
      },
      "pallet_config": {
        "flag": 1,
        "front": 1000,
        "side": 1200,
        "height": 110,
         "left_pallet": 0,
         "right_pallet": 1
      },
      "device_config": {
      "flag": 1,
      "x": 2400,
      "y": 1800,
      "z": 120,
      "angle": 0
      },
      "pattern_config": {
      "flag": 1,
      "layers": 8,
      "box_gap": 0,
      "sequence": "a,b,a,b,a,b,a,b",
      "pattern_b_enable": 1,
      "left_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "left_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_a": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "right_pattern_b": "{\"1\": [[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3],[1,2,3,0.1,0.2,0.3]]}",
      "origin_pattern_a": "[]",
      "origin_pattern_b": "[]"
      },
      "program_config": {
      "palletizing_name": "palletizing_1",
      "depalletizing_name":"depalletizing_1",
      "flag":"[0,1]"   
      },
      "lefttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "righttransitionpoint":{
      "j1":"120",
      "j2":"120",
      "j3":"120",
      "j4":"120",
      "j5":"120",
      "j6":"120"
      },
      "advanced_config":{
      "height": "1000",
      "x1": "100",
      "y1": "100",
      "z1": "100",
      "x2": "10",
      "y2": "10",
      "z2": "10",
      "time": "1"
      }
   }

Ottenere Lista Nomi Ricette Palletizzazione Esistenti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Nome Comando: `get_palletizing_formula_list`.

Parametri Comando: Nessuno.

Esempio Comando:

.. code-block:: c++
   :linenos:

   {
      cmd: "get_palletizing_formula_list"
   }

Feedback Comando:

.. code-block:: c++
   :linenos:

   /** 
   * @return status:200 
   * @param  Array ${name} Lista nomi palletizzazione
   * @return status:404 "fail"
   """

Esempio Feedback Comando:

.. code-block:: c++
   :linenos:

   ["palletizing1"]