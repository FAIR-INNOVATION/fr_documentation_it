Accesso al WebApp
============================

.. toctree::
   :maxdepth: 6

Accesso all'interfaccia WebApp
----------------------------------------

1. Accendere il cabinet di controllo e collegare il cavo di rete al PC;
2. Sul PC, aprire il browser Chrome e visitare l'URL 192.168.58.2;
3. Inserire nome utente e password, quindi fare clic su "Login" per accedere al WebApp.

Il nome utente predefinito è admin e la password è 123.

.. figure:: teaching_pendant_software/001.png
   :width: 6in
   :align: center

.. centered:: Figura 2.1‑1 Interfaccia di accesso

Conoscere rapidamente l'interfaccia WebApp
------------------------------------------------------------

Dopo l'accesso, il sistema entra nell'"Interfaccia iniziale", che comprende principalmente:

1. Logo FAIRINO;
2. Pulsante per ridurre/espandere la barra dei menu;
3. Barra dei menu;
4. Area di controllo del robot;
5. Area di stato del robot;
6. Robot di simulazione 3D — Operazioni sullo scenario 3D;
7. Robot di simulazione 3D — Operazioni sul corpo del robot;
8. Funzioni accessorie del robot;
9. Stato del robot e delle sue funzioni accessorie.
10. Come illustrato nello schema dell'interfaccia iniziale del sistema riportato di seguito:

.. image:: teaching_pendant_software/002.png
   :align: center
   :width: 6in

.. centered:: Figura 2.2‑1 Schema dell'interfaccia iniziale del sistema

Area di controllo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::
   .. image:: teaching_pendant_software/064.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Apri programma di insegnamento**

   Funzione: Apre il programma di insegnamento per la programmazione a codice, la programmazione grafica e la programmazione a nodi.

.. note::
   .. image:: teaching_pendant_software/003.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di Abilitazione**

   Funzione: Abilita il robot.

.. note::
   .. image:: teaching_pendant_software/004.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di Avvio**

   Funzione: Carica e avvia l'esecuzione del programma di insegnamento.

.. note::
   .. image:: teaching_pendant_software/005.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante di Arresto**

   Funzione: Interrompe l'esecuzione del programma di insegnamento corrente.

.. note::
   .. image:: teaching_pendant_software/006.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Pulsante Sospendi/Riprendi**

   Funzione: Sospende e riprende il programma di insegnamento corrente.

.. important::
   Il comando di pausa si trova alla fine del programma e non può essere valutato.

Barra di Stato
~~~~~~~~~~~~

.. note:: 
   .. image:: teaching_pendant_software/011.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato Errore di Esecuzione Robot**
   
    Funzione: Indica un errore durante l'esecuzione del robot. Nascosto quando non ci sono errori.

.. note:: 
   .. image:: teaching_pendant_software/007.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Stato Robot**
   
    Funzione: Stopped (Fermo), Running (In Esecuzione), Pause (Pausa), Drag (Trascinamento)

.. note:: 
   .. image:: teaching_pendant_software/010.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Sistema di Coordinate dell'Utensile Robot, Sistema di Coordinate del Pezzo, Sistema di Coordinate dell'Asse Esteso e ID Carico**
   
    Funzione: In alto a sinistra – ID del sistema di coordinate dell'utensile corrente. In alto a destra – ID del sistema di coordinate del pezzo corrente. In basso a sinistra – ID del sistema di coordinate dell'asse esteso corrente. In basso a destra – ID del carico corrente.

.. note:: 
   .. image:: teaching_pendant_software/009.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Percentuale Velocità di Esecuzione**
   
    Funzione: Velocità di funzionamento corrente del robot (in percentuale).

.. note:: 
   .. image:: teaching_pendant_software/012.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Automatica**
   
    Funzione: Modalità di funzionamento automatico del robot. Quando è abilitata la funzione "Passa alla Modalità Automatica con Regolazione Velocità Globale" e viene specificata una velocità, la velocità globale si adatterà automaticamente alla velocità specificata.

.. note:: 
   .. image:: teaching_pendant_software/013.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Modalità Manuale**
   
    Funzione: Modalità manuale del robot per operazioni di insegnamento.

.. note:: 
   .. image:: teaching_pendant_software/065.png
      :width: 0.75in
      :height: 0.75in
      :align: left

    Nome: **Pulsante Comprimi/Espandi Stato Robot**
   
    Funzione: Comprime o espande la visualizzazione del Sistema di Coordinate dell'Utensile, Sistema di Coordinate del Pezzo, Sistema di Coordinate dell'Asse Esteso, Carico, Stato di Trascinamento Robot, Modalità Locale/Remota, Stato Connessione Robot, Modalità BOOT e Informazioni Account.

Fare clic sul pulsante di compressione per visualizzare le seguenti informazioni di stato.

.. note::
   .. image:: teaching_pendant_software/008.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Numero sistema di coordinate utensile**

   Funzione: Visualizza il numero del sistema di coordinate utensile attualmente applicato.

.. note::
   .. image:: teaching_pendant_software/027.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Numero sistema di coordinate pezzo**

   Funzione: Visualizza il numero del sistema di coordinate pezzo attualmente applicato.

.. note::
   .. image:: teaching_pendant_software/028.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Numero sistema di coordinate assi estesi**

   Funzione: Visualizza il numero del sistema di coordinate assi estesi attualmente applicato.

.. note::
   .. image:: teaching_pendant_software/066.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Carico**

   Funzione: Visualizza il peso del carico applicato corrente e le coordinate del centro di massa X, Y, Z.

.. note::
   .. image:: teaching_pendant_software/014.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato di trascinamento del robot**

   Funzione: Il robot è attualmente trascinabile.

.. note::
   .. image:: teaching_pendant_software/015.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato di trascinamento del robot**

   Funzione: Il robot non è attualmente trascinabile.

.. note::
   .. image:: teaching_pendant_software/068.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Modalità Locale del robot**

   Funzione: Il robot è attualmente controllato tramite il cabinet di controllo.

.. note::
   .. image:: teaching_pendant_software/067.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Modalità Remota del robot**

   Funzione: Il robot può essere controllato attualmente solo tramite PLC.

.. note::
   .. image:: teaching_pendant_software/017.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato di Connessione**

   Funzione: Robot connesso.

.. note::
   .. image:: teaching_pendant_software/016.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Stato di Non Connesso**

   Funzione: Robot non connesso.

.. note::
   .. image:: teaching_pendant_software/018.png
      :width: 0.75in
      :height: 0.75in
      :align: left

   Nome: **Informazioni Account**

   Funzione: Visualizza nome utente, autorizzazioni e consente il logout dell'utente.