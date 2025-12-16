Macchina Virtuale - Docker
================================

Distribuzione di Immagini Docker su Linux
------------------------------------------

Ambiente Operativo
~~~~~~~~~~~~~~~~~~

- Sistema operativo dell'ambiente di esecuzione della macchina virtuale: Ubuntu 18.04.6;
- Specifiche dell'ambiente di esecuzione della macchina virtuale: RAM 4G, ROM 50G, CPU 6 core;
- Permessi operativi: utilizzare i privilegi di amministratore root, il metodo di impostazione è descritto nell'Appendice 3;
- File di installazione Docker: fr_docker.tar.gz;
- Immagine FAIRINO SimMachine: FAIRINOSimMachine.tar;

Installazione di Docker
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Se l'utente ha già installato e distribuito Docker, saltare questa sezione e procedere alla sezione 1.3 "Distribuzione dell'immagine".

1. Scaricare fr_docker.tar.gz e posizionarlo nel percorso dei file Ubuntu /opt/.
2. Decomprimere fr_docker.tar.gz, ad esempio nella directory /opt/:

.. code-block:: console
   :linenos:

   cd /opt/ && tar -zxvf fr_docker.tar.gz

.. image:: controller_virtual_machine/036.png
   :width: 6in
   :align: center

3. Eseguire lo script di installazione di Docker:

.. code-block:: console
   :linenos:

   sh install.sh docker-27.0.3.tgz

Dopo l'esecuzione dello script, se appare il numero di versione, significa che l'installazione è riuscita.

.. image:: controller_virtual_machine/037.png
   :width: 6in
   :align: center

Configurazione dell'Immagine
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Importazione dell'Immagine Docker
++++++++++++++++++++++++++++++++++++++++++++++++++

1. Scaricare l'immagine della macchina virtuale FAIRINOSimMachine.tar e decomprimerla.
2. Verificare la versione di Docker per confermare l'installazione.

.. code-block:: console
   :linenos:

   docker -v

.. image:: controller_virtual_machine/038.png
   :width: 6in
   :align: center

3. Importare l'immagine

.. code-block:: console
   :linenos:

   docker load -i ./FAIRINOSimMachine.tar

Quando appare "fairno_simmachine:latest" significa che l'importazione è completata.

.. image:: controller_virtual_machine/039.png
   :width: 6in
   :align: center

4. Eseguire `docker images` per verificare se l'importazione è riuscita.

Creazione di una Rete Bridge Personalizzata
+++++++++++++++++++++++++++++++++++++++++++++++++++

1. Eseguire il seguente comando per creare una rete bridge chiamata "fairino-net" con segmento di rete 192.168.58.0/24.

.. code-block:: console
   :linenos:

   docker network create --driver bridge --subnet 192.168.58.0/24 --gateway 192.168.58.1 fairino-net

2. Visualizzare la rete

.. code-block:: console
   :linenos:

   docker network ls

Se esiste la rete "fairino-net", significa che la creazione è riuscita.

.. image:: controller_virtual_machine/040.png
   :width: 6in
   :align: center

Avvio Iniziale del Contenitore Docker
+++++++++++++++++++++++++++++++++++++

1. Creare e avviare il contenitore

Utilizzare la rete "fairino-net" e l'immagine "fairino_simmachine" per avviare il contenitore.

.. code-block:: console
   :linenos:

   docker run -d -P --name fairino-container --privileged -u root --net fairino-net fairino_simmachine

.. image:: controller_virtual_machine/041.png
   :width: 6in
   :align: center

.. code-block:: console
   :linenos:

   docker ps

Verificare se il contenitore è stato avviato correttamente: se appare "fairino-container", l'avvio è riuscito.

.. image:: controller_virtual_machine/042.png
   :width: 6in
   :align: center

Operare il Robot Virtuale tramite Web
-------------------------------------

Avvio Normale del Contenitore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Questa sezione si riferisce ai casi in cui il contenitore non è in esecuzione in background a causa di riavvii del computer, arresti di Docker, ecc., non al primo avvio del contenitore.

1. Avviare Docker:

.. code-block:: console
   :linenos:

   systemctl start docker

2. Verificare lo stato di Docker:

.. code-block:: console
   :linenos:

   systemctl status docker

"Green active(running)" significa che l'avvio è riuscito.

.. image:: controller_virtual_machine/043.png
   :width: 6in
   :align: center

3. Eseguire `docker ps -a` per visualizzare l'ID del contenitore.

.. image:: controller_virtual_machine/044.png
   :width: 6in
   :align: center

4. Eseguire `docker start [ID del contenitore]`.

.. image:: controller_virtual_machine/045.png
   :width: 6in
   :align: center

5. Se l'esecuzione è riuscita, eseguire nuovamente `docker ps` per verificare che il contenitore sia in esecuzione.

.. image:: controller_virtual_machine/046.png
   :width: 6in
   :align: center

Operare il Robot Virtuale
~~~~~~~~~~~~~~~~~~~~~~~~~

1. Confermare che il contenitore Docker sia in esecuzione.

.. code-block:: console
   :linenos:

   docker ps

Se appare "fairino-container", significa che è in esecuzione.

.. image:: controller_virtual_machine/047.png
   :width: 6in
   :align: center

2. Aprire il browser, inserire l'IP predefinito: 192.168.58.2, per accedere all'interfaccia web e operare il robot virtuale.

.. image:: controller_virtual_machine/048.png
   :width: 6in
   :align: center

3. Accedere con l'account "admin", password: 123.

.. image:: controller_virtual_machine/049.png
   :width: 6in
   :align: center

Modifica dell'Indirizzo IP da parte dell'Utente
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: controller_virtual_machine/050.png
   :width: 6in
   :align: center

1. Aprire il browser, inserire l'IP predefinito: 192.168.58.2, per aprire la pagina web;
2. Accedere con l'account "admin", password: 123;
3. Entrare in "Impostazioni di Sistema" → "Impostazioni Generali" → "Impostazioni di Rete", modificare l'IP con l'indirizzo IP target, la subnet mask e il gateway. Fare clic su "Imposta Rete";
4. Aprire il terminale e arrestare il contenitore;

Visualizzare l'ID del contenitore:

.. code-block:: console
   :linenos:

   docker ps -a

.. image:: controller_virtual_machine/052.png
   :width: 6in
   :align: center

Arrestare il contenitore:

.. code-block:: console
   :linenos:

   docker stop [ID del contenitore]

.. image:: controller_virtual_machine/053.png
   :width: 6in
   :align: center

5. Riconfigurare la rete del contenitore;

Eliminare la rete precedente:

.. code-block:: console
   :linenos:

   docker network rm fairino-net

Creare una nuova rete:

.. code-block:: console
   :linenos:

   docker network create --driver bridge --subnet [IP target/subnet mask] --gateway [IP gateway] fairino-net

Esempio con 192.168.56.0/24: docker network create --driver bridge --subnet 192.168.56.0/24 --gateway 192.168.56.1 fairino-net

.. image:: controller_virtual_machine/054.png
   :width: 6in
   :align: center

6. Ricollegare il contenitore alla nuova rete creata;

.. code-block:: console
   :linenos:

   docker network connect fairino-net [ID del contenitore]

.. image:: controller_virtual_machine/055.png
   :width: 6in
   :align: center

7. Riavviare il contenitore;

.. code-block:: console
   :linenos:

   docker start [ID del contenitore]

8. Ora aprire il browser, inserire l'indirizzo IP modificato, per accedere all'interfaccia web e operare il robot virtuale.

.. image:: controller_virtual_machine/056.png
   :width: 6in
   :align: center

Aggiornamento e Downgrade della Versione della Macchina Virtuale
---------------------------------------------------------------------------

Panoramica
~~~~~~~~~~

Questo manuale descrive in dettaglio la procedura standard per eseguire operazioni di aggiornamento e downgrade del software durante l'utilizzo della macchina virtuale FAIRINO SimMachine Docker, e sistematicamente elenca le precauzioni da considerare durante il processo di cambio versione.

Preparazione e Precauzioni per Aggiornamento/Downgrade
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Preparazione Operativa
++++++++++++++++++++++

1. Macchina virtuale FAIRINO SimMachine Docker già distribuita e funzionante normalmente. La guida alla distribuzione è disponibile nel "Manuale Utente - Distribuzione dell'Immagine Docker su Linux";
2. Pacchetto di aggiornamento del software per la versione della macchina virtuale Docker, il link per il download è disponibile in "Download Materiali - FAIRINO SimMachine Docker". Dopo l'estrazione, il contenuto include l'immagine Docker dell'ultima versione FAIRINOSimMachine.tar e il pacchetto di aggiornamento del software software.tar.gz.

Precauzioni
+++++++++++

1. Backup dei dati: Si consiglia di eseguire un backup prima dell'aggiornamento, il metodo è descritto nel capitolo "Backup dei dati", per evitare la perdita di dati in caso di anomalie durante l'aggiornamento.
2. Limitazioni di versione:

.. centered:: Tabella 2.3-1 Limitazioni di Aggiornamento/Downgrade

.. list-table::
   :widths: 50 50 50
   :header-rows: 0
   :align: center

   * - **Tipo di Operazione**
     - **Condizione/Limitazione**
     - **Descrizione dei Passaggi**

   * - **Aggiornamento di Versione**
     - Versione corrente >= 3.7.8
     - Aggiornamento diretto possibile

   * - **Aggiornamento di Versione**
     - Versione corrente < 3.7.8
     - Prima aggiornare alla versione 3.7.5 o utilizzare la soluzione compatibile

   * - **Downgrade di Versione**
     - Versione corrente e target >= 3.7.8
     - Downgrade diretto possibile

   * - **Downgrade di Versione**
     - Versione corrente o target < 3.7.8
     - Utilizzare la soluzione compatibile

   * - **Soluzione Compatibile**
     - Applicabile sia per aggiornamenti/downgrade con anomalie
     - Vedere il capitolo "Soluzione Compatibile" per i dettagli dei passaggi