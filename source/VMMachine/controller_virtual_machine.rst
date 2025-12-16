Macchina Virtuale - VMware
===============================================

Panoramica
------------------
Questo manuale ha lo scopo di illustrare come utilizzare la macchina virtuale FAIRINO SimMachine.

Istruzioni Operative
------------------------------------

Installare VMware Workstation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Versione dimostrativa di VMware Workstation: 17.6.3 (salta questo passaggio se già installato).

Cerca direttamente il sito ufficiale di VMware nel browser o vai all'URL \ `<https://www.vmware.com>`__\ , scarica il pacchetto di installazione e installalo seguendo il percorso predefinito.

.. image:: controller_virtual_machine/001.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-1 Interfaccia VMWare

Aprire l'Immagine della Macchina Virtuale
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Scarica l'immagine della macchina virtuale FAIRINO_SimMachine.zip ed estraila
   
2. Apri VMware, clicca su File->Apri. Come mostrato nella Figura 2-2:

.. image:: controller_virtual_machine/002.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-2 Aprire l'immagine

3. Trova la cartella estratta, seleziona il file con estensione .vmx. Come mostrato nella Figura 2-3:
   
.. image:: controller_virtual_machine/003.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-3 Selezionare il file

4. Clicca su "Power on this virtual machine" per avviare la macchina virtuale. Come mostrato nella Figura 2-4:
   
.. image:: controller_virtual_machine/004.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-4 Avviare la macchina virtuale

5. Nella cartella estratta, trova "fr_get_vm_net" e aprilo con un doppio clic, come mostrato nella Figura 2-5. Il contenuto mostrato è l'IP della macchina virtuale. Come mostrato nella Figura 2-6.

.. note:: In caso di fallimento nell'ottenimento, accedi alla macchina virtuale ed esegui il comando "ifconfig" per ottenere l'IP.
      
.. image:: controller_virtual_machine/005.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-5 fr_get_vm_net.bat
      
.. image:: controller_virtual_machine/006.png
   :width: 4in
   :align: center

.. centered:: Figura 6.2-6 IP della macchina virtuale

Accedere a WebApp da Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Dopo aver ottenuto l'IP della macchina virtuale, accedi direttamente all'IP tramite il browser su Windows per entrare in WebApp. Ad esempio, inserisci: 192.168.182.222, come mostrato nella Figura 2-7:
         
.. image:: controller_virtual_machine/007.png
   :width: 6in
   :align: center

.. centered:: Figura 6.2-7 Accedere a WebApp tramite l'IP della macchina virtuale