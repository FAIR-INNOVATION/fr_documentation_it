Introduzione al Robot
=================================

.. toctree::
	:maxdepth: 5

Parametri Base
-----------------------

.. centered:: Tabella 2.1-1 Parametri base del robot

.. figure:: installation/017.png
	:align: center
	:width: 8in

.. figure:: installation/102.png
	:align: center
	:width: 8in

.. important::
  Nella serie FR dei robot, quando si eseguono trasformazioni di posa o di sistemi di coordinate, l'ordine di rotazione degli angoli per il calcolo della matrice di trasformazione omogenea è "ZYX" per il sistema di coordinate mobile.

Campo di Movimento
----------------------------------------

Spazio di installazione del braccio robotico:

L'installazione del corpo del robot richiede uno spazio di 3m×3m×2m (lunghezza×larghezza×altezza) per soddisfare il movimento del robot alla massima apertura del braccio. Se l'utente aumenta autonomamente il carico all'estremità, assicurarsi che lo spazio di installazione lasci un minimo di 500 mm di spazio libero.

.. note::
	Lo spazio in altezza è influenzato dall'altezza della base di installazione; qui 2m si riferisce alla distanza sopra il piano di riferimento di installazione.

Spazio di installazione della cabina di controllo:

1. La scatola di controllo deve essere posizionata in una posizione facile da operare, protetta da allagamenti e rischio di folgorazione, a una distanza dal suolo tra 0,6 m e 1,5 m.

2. Il contenitore deve essere lontano da fonti di calore.

3. Il lato della scatola di controllo con i cavi ad alta potenza deve avere un'area libera di almeno 150 mm senza ostacoli, gli altri lati devono avere almeno 100 mm senza ostacoli, per facilitare la dissipazione del calore e l'inserimento/rimozione.

.. figure:: installation/018.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-1 Campo di movimento robot collaborativo modello FR3

.. figure:: installation/103.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-2 Campo di movimento robot collaborativo modello FR3-WML

.. figure:: installation/104.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-3 Campo di movimento robot collaborativo modello FR3-WMS

.. figure:: installation/105.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-4 Campo di movimento robot collaborativo modello FR3-C

.. figure:: installation/019.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-5 Campo di movimento robot collaborativo modello FR5

.. figure:: installation/129.png
	:align: center
	:width: 6in

.. centered:: Figura 2.2-6 Robot Collaborativo Modello FR5-C Intervallo di Movimento

.. figure:: installation/020.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-7 Campo di movimento robot collaborativo modello FR10

.. figure:: installation/021.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-8 Campo di movimento robot collaborativo modello FR16

.. figure:: installation/022.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-9 Campo di movimento robot collaborativo modello FR20

.. figure:: installation/068.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.2-10 Campo di movimento robot collaborativo modello FR30

Sistema di Coordinate del Robot
---------------------------------------------

.. figure:: installation/023.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.3-1 Sistema di coordinate parametri DH del robot

.. figure:: installation/024.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.3-2 Sistema di coordinate della flangia terminale del robot

Parametri DH del Robot
----------------------------------

I parametri DH sono utilizzati per calcolare la cinematica e la dinamica dei robot collaborativi della serie FR.

.. figure:: installation/063.png
	:align: center
	:width: 6in

.. centered:: Grafico 2.4-1 Parametri DH dei robot collaborativi serie FR

I parametri DH dei robot collaborativi serie FR sono mostrati di seguito:

.. centered:: Tabella 2.4-1 Tabella parametri DH robot collaborativo FR3

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 140
     - π/2
     - Collegamento1
     - 1.98
     - [-0.05, -15.92, 2.26]

   * - Giunto2
     - 0
     - -280
     - 0
     - 0
     - Collegamento2
     - 3.4445
     - [139.49, 0, 99.54]

   * - Giunto3
     - 0
     - -240
     - 0
     - 0
     - Collegamento3
     - 1.437
     - [58.99, 0.08, 12.99]

   * - Giunto4
     - 0
     - 0
     - 102
     - π/2
     - Collegamento4
     - 0.871
     - [0.05, -2.33, 14.67]

   * - Giunto5
     - 0
     - 0
     - 102
     - -π/2
     - Collegamento5
     - 0.805
     - [-0.05, 2.33, 14.67]

   * - Giunto6
     - 0
     - 0
     - 100
     - 0
     - Collegamento6
     - 0.261
     - [-0.05, -1.11, -20.05]

.. centered:: Tabella 2.4-2 Tabella parametri DH robot collaborativo FR3-WMS

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 140
     - 0
     - π/2
     - Collegamento1
     - 1.66
     - [-0.06, -13.58, 1.68]

   * - Giunto2
     - 0
     - 0
     - -280
     - 0
     - Collegamento2
     - 3.68
     - [140.11, 0, 101.71]

   * - Giunto3
     - 0
     - 0
     - -240
     - 0
     - Collegamento3
     - 1.81
     - [63.49, 0.1, 10.94]

   * - Giunto4
     - 0
     - 102
     - 0
     - π/2
     - Collegamento4
     - 1.18
     - [0.07, -2.18, 12.48]

   * - Giunto5
     - 0
     - 102
     - 0
     - -π/2
     - Collegamento5
     - 1.18
     - [-0.07, 2.18, 12.48]

   * - Giunto6
     - 0
     - 100
     - 0
     - 0
     - Collegamento6
     - 0.28
     - [1.81, 1.33, -20.41]

.. centered:: Tabella 2.4-3 Tabella parametri DH robot collaborativo FR3-WML

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 140
     - 0
     - π/2
     - Collegamento1
     - 1.54
     - [-0.01, -14.27, 1.37]

   * - Giunto2
     - 0
     - 0
     - -425
     - 0
     - Collegamento2
     - 3.49
     - [212.5, 0, 101.43]

   * - Giunto3
     - 0
     - 0
     - -395
     - 0
     - Collegamento3
     - 2
     - [114.17, 0.08, 9.92]

   * - Giunto4
     - 0
     - 102
     - 0
     - π/2
     - Collegamento4
     - 1.17
     - [0.07, -2.18, 12.48]

   * - Giunto5
     - 0
     - 102
     - 0
     - -π/2
     - Collegamento5
     - 1.17
     - [-0.07, 2.18, 12.48]

   * - Giunto6
     - 0
     - 100
     - 0
     - 0
     - Collegamento6
     - 0.28
     - [1.9, 1.6, -20.08]

.. centered:: Tabella 2.4-4 Tabella parametri DH robot collaborativo FR3-C

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 140
     - 0
     - π/2
     - Collegamento1
     - 1.69
     - [-0.16, -13.99, 1.53]

   * - Giunto2
     - 0
     - 0
     - -280
     - 0
     - Collegamento2
     - 3.73
     - [140, 0, 101.34]

   * - Giunto3
     - 0
     - 0
     - -240
     - 0
     - Collegamento3
     - 1.84
     - [63.24, 0.08, 11.04]

   * - Giunto4
     - 0
     - 102
     - 0
     - π/2
     - Collegamento4
     - 1.2
     - [0.1, -2.03, 12.55]

   * - Giunto5
     - 0
     - 102
     - 0
     - -π/2
     - Collegamento5
     - 1.2
     - [-0.1, 2.03, 12.55]

   * - Giunto6
     - 0
     - 100
     - 0
     - 0
     - Collegamento6
     - 0.53
     - [1.48, 1.54, -17.9]

.. centered:: Tabella 2.4-5 Tabella parametri DH robot collaborativo FR5

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 152
     - π/2
     - Collegamento1
     - 4.64
     - [-0.19, -18.28, 2.26]

   * - Giunto2
     - 0
     - -425
     - 0
     - 0
     - Collegamento2
     - 10.08
     - [212.47, 0, 121.2]

   * - Giunto3
     - 0
     - -395
     - 0
     - 0
     - Collegamento3
     - 2.71
     - [122.62, 0.17, 12.59]

   * - Giunto4
     - 0
     - 0
     - 102
     - π/2
     - Collegamento4
     - 1.56
     - [0.05, -2.33, 14.68]

   * - Giunto5
     - 0
     - 0
     - 102
     - -π/2
     - Collegamento5
     - 1.56
     - [-0.05, 2.33, 14.68]

   * - Giunto6
     - 0
     - 0
     - 100
     - 0
     - Collegamento6
     - 0.36
     - [0.93, 0.81, -20.05]

.. centered:: Tabella 2.4-6 Parametri DH del Robot Collaborativo FR5-C

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 140
     - π/2
     - Link1
     - 1.76
     - [-0.09, -15.66, 1.53]

   * - Giunto2
     - 0
     - -280
     - 0
     - 0
     - Link2
     - 3.98
     - [211.32, 0, 101.13]

   * - Giunto3
     - 0
     - -240
     - 0
     - 0
     - Link3
     - 2.08
     - [102.62, 0.12, 11.26]

   * - Giunto4
     - 0
     - 0
     - 102
     - π/2
     - Link4
     - 1.33
     - [0.09, -1.86, 13.76]

   * - Giunto5
     - 0
     - 0
     - 102
     - -π/2
     - Link5
     - 1.33
     - [-0.09, 1.86, 13.76]

   * - Giunto6
     - 0
     - 0
     - 100
     - 0
     - Link6
     - 0.28
     - [-0.26, 1.75, -20.50]

.. centered:: Tabella 2.4-7 Tabella parametri DH robot collaborativo FR5-WML

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 180
     - 0
     - π/2
     - Collegamento1
     - 11.49
     - [-0.16, -28.51, 4.16]

   * - Giunto2
     - 0
     - 0
     - -970
     - 0
     - Collegamento2
     - 21.3
     - [642.59, 0.04, 165.62]

   * - Giunto3
     - 0
     - 0
     - -816
     - 0
     - Collegamento3
     - 4.61
     - [321.39, 0.16, 52.76]

   * - Giunto4
     - 0
     - 159
     - 0
     - π/2
     - Collegamento4
     - 1.66
     - [0.21, -3.06, 13.07]

   * - Giunto5
     - 0
     - 114
     - 0
     - -π/2
     - Collegamento5
     - 1.66
     - [-0.21, 3.06, 13.07]

   * - Giunto6
     - 0
     - 160
     - 0
     - 0
     - Collegamento6
     - 0.36
     - [1.45, 1.09, -19.98]

.. centered:: Tabella 2.4-8 Tabella parametri DH robot collaborativo FR10

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 180
     - π/2
     - Collegamento1
     - 11.97
     - [-0.10, -26.12, 4.04]

   * - Giunto2
     - 0
     - -700
     - 0
     - 0
     - Collegamento2
     - 19.59
     - [480.27, 0.01, 164.68]

   * - Giunto3
     - 0
     - -586
     - 0
     - 0
     - Collegamento3
     - 3.7
     - [211.22, 0.11, 54.21]

   * - Giunto4
     - 0
     - 0
     - 159
     - π/2
     - Collegamento4
     - 1.69
     - [0.12, -3, 12.18]

   * - Giunto5
     - 0
     - 0
     - 114
     - -π/2
     - Collegamento5
     - 1.69
     - [-0.12, 3, 12.18]

   * - Giunto6
     - 0
     - 0
     - 106
     - 0
     - Collegamento6
     - 0.35
     - [1.24, 0.85, -20.34]

.. centered:: Tabella 2.4-9 Tabella parametri DH robot collaborativo FR16

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 180
     - π/2
     - Collegamento1
     - 11.97
     - [-0.10, -26.12, 4.04]

   * - Giunto2
     - 0
     - -520
     - 0
     - 0
     - Collegamento2
     - 18.18
     - [364.4, 0.01, 163.09]

   * - Giunto3
     - 0
     - -400
     - 0
     - 0
     - Collegamento3
     - 3.22
     - [135.03, 0.12, 55.58]

   * - Giunto4
     - 0
     - 0
     - 159
     - π/2
     - Collegamento4
     - 1.69
     - [0.12, -3, 12.18]

   * - Giunto5
     - 0
     - 0
     - 114
     - -π/2
     - Collegamento5
     - 1.69
     - [-0.12, 3, 12.18]

   * - Giunto6
     - 0
     - 0
     - 106
     - 0
     - Collegamento6
     - 0.35
     - [1.24, 0.85, -20.34]

.. centered:: Tabella 2.4-10 Tabella parametri DH robot collaborativo FR20

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 215
     - π/2
     - Collegamento1
     - 20.79
     - [-0.19, -36.57, 5.68]

   * - Giunto2
     - 0
     - -1000
     - 0
     - 0
     - Collegamento2
     - 42.84
     - [605.25, 0.06, 202.94]

   * - Giunto3
     - 0
     - -716
     - 0
     - 0
     - Collegamento3
     - 9.88
     - [262.84, 0.22, 43.08]

   * - Giunto4
     - 0
     - 0
     - 166
     - π/2
     - Collegamento4
     - 4.64
     - [0.23, -2.28, 18.42]

   * - Giunto5
     - 0
     - 0
     - 138
     - -π/2
     - Collegamento5
     - 4.64
     - [-0.23, 2.28, 18.42]

   * - Giunto6
     - 0
     - 0
     - 120
     - 0
     - Collegamento6
     - 0.6
     - [-2.11, -1.96, -20.38]

.. centered:: Tabella 2.4-11 Tabella parametri DH robot collaborativo FR30

.. list-table::
   :widths: 70 50 50 50 50 70 50 120
   :header-rows: 0
   :align: center
   :class: no-padding sheet-center

   * - **Cinematica**
     - **theta[rad]**
     - **a[mm]**
     - **d[mm]**
     - **alpha[rad]**
     - **Dinamica**
     - **Massa[kg]**
     - **Centro di Massa[mm]**

   * - Giunto1
     - 0
     - 0
     - 215
     - π/2
     - Collegamento1
     - 20.64
     - [-0.22, -37.39, 5.59]

   * - Giunto2
     - 0
     - -700
     - 0
     - 0
     - Collegamento2
     - 36.37
     - [440.73, 0.05, 198.7]

   * - Giunto3
     - 0
     - -536
     - 0
     - 0
     - Collegamento3
     - 8.41
     - [185.64, 0.25, 45.82]

   * - Giunto4
     - 0
     - 0
     - 166
     - π/2
     - Collegamento4
     - 4.64
     - [0.23, -2.29, 18.60]

   * - Giunto5
     - 0
     - 0
     - 138
     - -π/2
     - Collegamento5
     - 4.64
     - [-0.23, 2.29, 18.60]

   * - Giunto6
     - 0
     - 0
     - 120
     - 0
     - Collegamento6
     - 0.6
     - [-2.11, -1.96, -20.38]

Tabella Parametri DH
------------------------------------
    :download:`Parametri DH robot collaborativo FR <../_static/_doc/FR Robots DH Transformation.xlsx>`