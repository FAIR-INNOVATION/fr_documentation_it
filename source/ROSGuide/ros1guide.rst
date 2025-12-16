Panoramica
++++++++++
L'architettura semplificata di frcobot_ros è mostrata nella figura seguente. Il lato del robot collaborativo fornisce un server XMLRPC e un server TCP.

- Il server XMLRPC fornisce principalmente API di comando del robot per completare il movimento del robot e le funzioni di acquisizione dei valori di stato.
- Il server TCP per il feedback di stato fornisce un feedback in tempo reale dello stato del robot con un periodo di 8 ms.

Sul lato PC dell'utente sono installati ROS e Moveit!, e frcobot_ros è stato compilato. In frcobot_ros, ogni pacchetto funzionale include la libreria lib delle API del robot, oltre a un client TCP che stabilisce la comunicazione con il server di feedback di stato del robot in frcobot_hw, acquisendo i dati di feedback dello stato del robot.

.. figure:: img/frcobot_ros.png
    :width: 6in
    :align: center

Installazione
+++++++++++++++++++++++++++++++
Questo capitolo descrive come costruire frcobot_ros e l'ambiente di installazione richiesto.

Requisiti di Ambiente
--------------------------------------

L'ambiente consigliato per frcobot_ros è il seguente:

.. note:: 
    - Ubuntu 18.04 LTS Bionic Beaver e ROS Melodic Morenia
    - Ubuntu 20.04 LTS Focal Fossa e ROS Noetic Ninjemys

Le seguenti istruzioni si applicano al sistema Ubuntu 20.04 LTS e ROS Noetic Ninjemys. Se si utilizza Melodic, sostituire `noetic` con `melodic` nei comandi seguenti.

Requisiti di Installazione ROS
------------------------------------------
Dopo aver installato il sistema Ubuntu, `installare e configurare l'ambiente ROS Noetic <https://wiki.ros.org/noetic/Installation/Ubuntu>`__.

Dopo aver configurato ROS Noetic, installare i seguenti ambienti necessari:

.. code-block:: shell
    :linenos:

    echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
    source ~/.bashrc
    sudo apt-get install -y \
        ros-noetic-rosparam-shortcuts \
        ros-noetic-ros-control \
        ros-noetic-ros-controllers \
        ros-noetic-moveit \
        libxmlrpcpp-dev

Compilazione del Pacchetto ROS
------------------------------------------------
Dopo aver installato e configurato correttamente ROS Noetic, creare un'area di lavoro Catkin nella directory di propria scelta.

.. code-block:: shell
    :linenos:

    mkdir -p ~/catkin_ws/src
    cd ~/catkin_ws
    catkin_init_workspace src

Quindi clonare la repository frcobot_ros da Gitee.

.. code-block:: shell
    :linenos:

    cd ~/catkin_ws/src
    git clone https://gitee.com/fair-innovation/frcobot_ros.git

Costruire il pacchetto frcobot_ros

.. code-block::  shell
    :linenos:

    cd ~/catkin_ws
    catkin_make
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
    source ~/.bashrc

Se si verificano errori, verificare che tutti i pacchetti menzionati nei requisiti di installazione ROS siano stati installati correttamente. Dopo la compilazione, copiare la libreria lib nell'ambiente lib di ROS (percorso: /opt/ros/noetic/lib) per consentire al programma di funzionare correttamente.

.. code-block:: shell
    :linenos:

    # Qui il percorso predefinito di catkin_ws è "~". Se è diverso, sostituire "~" con il percorso effettivo.
    sudo cp ~/catkin_ws/src/frcobot_ros/frcobot_hw/lib/* /opt/ros/noetic/lib

Inizio Rapido
+++++++++++++++++++++++++++++

frcobot_hw
-----------------
frcobot_hw fornisce principalmente le funzioni di base per la comunicazione con il robot collaborativo.

.. note:: 
    - Contiene i messaggi (msg) di feedback dello stato del robot collaborativo
    - Fornisce demo di comandi per controllare il robot collaborativo
    - Fornisce nodi e Topic per il feedback dello stato del robot collaborativo
    - Consente di avviare rapidamente i nodi di stato e le demo di comandi tramite file launch

Il contenuto di frcobot_hw.launch è il seguente:

.. code-block:: xml
    :linenos:

    <launch>

        <!-- params -->
        <param name="robot_ip" type="string" value="192.168.58.2"/>
        <param name="robot_port" type="int" value="8083"/>

        <!-- frcobot status node -->
        <node pkg="frcobot_hw" type="frcobot_status_node" name="frcobot_status_node" output="screen" />

        <!-- frcobot control demo -->
        <node pkg="frcobot_hw" type="frcobot_cmd_demo" name="frcobot_cmd_demo" output="screen" />
        
    </launch>

.. important:: 

    - È necessario assicurarsi che `robot_ip` e `robot_port` corrispondano all'IP e alla porta del robot collaborativo da controllare.
    - L'IP predefinito del robot di fabbrica è 192.168.58.2, e la porta di feedback dello stato per l'utente è 8083.

È possibile avviare rapidamente il nodo di feedback dello stato del robot e la demo dei comandi con il seguente comando:

.. code-block:: shell
    :linenos:

    roslaunch frcobot_hw frcobot_hw.launch

Aprire un nuovo terminale e utilizzare il seguente comando per stampare e visualizzare i dati di feedback dello stato in tempo reale:

.. code-block:: shell
    :linenos:

    rostopic echo /frcobot_status

.. frcobot_camera
.. -----------------
.. frcobot_camera fornisce funzioni di calibrazione mano-occhio e di presa non ordinata (Bin-Picking) con RVS e telecamere.

.. frcobot_gripper
.. -------------------

.. frcobot_description
.. ----------------------

.. frcobot moveit!
.. -----------------------