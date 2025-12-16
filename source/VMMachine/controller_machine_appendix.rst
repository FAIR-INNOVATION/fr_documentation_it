Appendice
===================

Appendice 1: Abilitare Virtualizzazione nel BIOS
---------------------------------------------------------------------

Il processo per abilitare la virtualizzazione può variare a seconda del modello del computer. Di seguito un esempio con la serie ThinkPad di Lenovo con Windows 10:

- Aprire le impostazioni del computer, selezionare "Aggiornamento e sicurezza".

.. image:: controller_virtual_machine/013.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/014.png
   :width: 4in
   :align: center

- Selezionare "Ripristino".

.. image:: controller_virtual_machine/015.png
   :width: 4in
   :align: center

- Selezionare "Riavvia ora".

.. image:: controller_virtual_machine/016.png
   :width: 4in
   :align: center

- Selezionare "Risoluzione dei problemi".
  
.. image:: controller_virtual_machine/017.png
   :width: 4in
   :align: center

- Selezionare "Opzioni avanzate".

.. image:: controller_virtual_machine/018.png
   :width: 4in
   :align: center

- Selezionare "Impostazioni firmware UEFI".

.. image:: controller_virtual_machine/019.png
   :width: 4in
   :align: center

- Selezionare "Riavvia".

.. image:: controller_virtual_machine/020.png
   :width: 4in
   :align: center

- Selezionare "Virtualizzazione" sotto "Sicurezza".

.. image:: controller_virtual_machine/021.png
   :width: 4in
   :align: center

- Selezionare "Abilitato", premere "Invio" per confermare.

.. image:: controller_virtual_machine/022.png
   :width: 4in
   :align: center

- Premere "F10", selezionare "Sì", premere "Invio" per salvare le modifiche.

.. image:: controller_virtual_machine/023.png
   :width: 4in
   :align: center

Appendice 2: Aggiungere una Scheda di Rete Virtuale (Adattatore di Loopback)
----------------------------------------------------------------------------------

1. Aprire Gestione dispositivi: premere "Tasto Windows + X", selezionare "Gestione dispositivi".
   
.. image:: controller_virtual_machine/024.png
   :width: 4in
   :align: center

2. Aggiungere un adattatore di rete.

.. image:: controller_virtual_machine/025.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/026.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/027.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/028.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/029.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/030.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/031.png
   :width: 4in
   :align: center
   
3. Visualizzare la scheda di rete virtuale: premere "Tasto Windows + X", selezionare "Connessioni di rete".

.. image:: controller_virtual_machine/032.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/033.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/034.png
   :width: 4in
   :align: center

.. image:: controller_virtual_machine/035.png
   :width: 4in
   :align: center
   
4. Configurare la rete dell'adattatore di loopback.

- Indirizzo IP: 192.168.58.XXX (deve essere nella stessa sottorete di 192.168.58.2).
- Maschera di sottorete: 255.255.255.0.

.. image:: controller_virtual_machine/012.png
   :width: 6in
   :align: center

5. Aprire la configurazione di rete di Virtualbox, selezionare "Rete adattatore loopback" come nome scheda di rete, quindi avviare la macchina virtuale.

.. image:: controller_virtual_machine/013.png
   :width: 6in
   :align: center

Appendice 3: Permessi Root
--------------------------------------

Dopo l'installazione di Ubuntu, l'utente root non può accedere per impostazione predefinita e la password è vuota. Per utilizzare l'utente root, è necessario impostare prima una password per root.

1. Aprire il terminale, digitare `sudo passwd root`, quindi premere Invio e inserire la password più volte. Verrà visualizzato un messaggio di successo per l'impostazione della password.

.. image:: controller_virtual_machine/057.png
   :width: 6in
   :align: center

2. Nel terminale, continuare digitando il comando `su - root` per cambiare utente, premere Invio e inserire la password.

.. warning:: Quando si inserisce il comando, è fondamentale includere il trattino "-". L'opzione "-" indica il cambio dell'ambiente insieme all'utente. Il trattino "-" non deve assolutamente essere omesso.

.. image:: controller_virtual_machine/058.png
   :width: 6in
   :align: center

Appendice 4: Comandi Docker Base
--------------------------------------

1. Comando di aiuto Docker:

.. code-block:: console
   :linenos:

   docker --help

2. Avviare Docker:

.. code-block:: console
   :linenos:

   systemctl start docker

3. Arrestare Docker:

.. code-block:: console
   :linenos:

   systemctl stop docker

4. Riavviare Docker:

.. code-block:: console
   :linenos:

   systemctl restart docker

5. Configurare Docker per l'avvio automatico con il servizio:

.. code-block:: console
   :linenos:

   systemctl enable docker

6. Verificare lo stato di esecuzione di Docker:

.. code-block:: console
   :linenos:

   systemctl status docker
   -- Se è in esecuzione, si vedrà (active) in verde dopo aver inserito il comando.

7. Immagini Docker:

.. code-block:: console
   :linenos:

   docker images: elenca le immagini scaricate, visualizza le immagini
   docker rmi ID_immagine_o_nome: elimina l'immagine locale
   docker rmi -f ID_immagine_o_nome: elimina l'immagine
   docker build: costruisce un'immagine
   docker search ID_immagine_o_nome: cerca immagini per parola chiave nel repository Docker Hub
   docker pull ID_immagine_o_nome: scarica un'immagine dal repository
   docker images: elenca le immagini scaricate, visualizza le immagini
   docker rmi ID_immagine_o_nome: elimina l'immagine locale
   docker rmi -f ID_immagine_o_nome: elimina l'immagine
   docker build: costruisce un'immagine

8. Contenitori Docker:

.. code-block:: console
   :linenos:

   docker ps: elenca i contenitori in esecuzione
   docker ps -a: visualizza tutti i contenitori, inclusi quelli non in esecuzione
   docker stop ID_contenitore_o_nome: arresta il contenitore
   docker kill ID_contenitore: arresta forzatamente il contenitore
   docker start ID_contenitore_o_nome: avvia un contenitore arrestato
   docker inspect ID_contenitore: visualizza tutte le informazioni del contenitore
   docker container logs ID_contenitore: visualizza i log del contenitore
   docker top ID_contenitore: visualizza i processi all'interno del contenitore
   docker exec -it ID_contenitore /bin/bash: entra nel contenitore
   exit: esce dal contenitore
   docker rm ID_contenitore_o_nome: elimina un contenitore arrestato
   docker rm -f ID_contenitore: elimina un contenitore in esecuzione
   docker exec -it ID_contenitore sh: entra nel contenitore