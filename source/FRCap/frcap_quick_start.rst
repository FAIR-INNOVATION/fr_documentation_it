Inizio Rapido
=========================

.. toctree:: 
   :maxdepth: 6

Non ho un FRCap
-----------------------

Se attualmente non hai un FRCap, puoi crearne rapidamente uno in questa sezione.

Innanzitutto, dobbiamo connetterci al robot e accedere al WebApp. Apri un browser sul tuo computer locale e inserisci l'indirizzo IP predefinito del robot (http://192.168.58.2), quindi accedi al WebApp.

.. image:: frcap_pictures/002.png
   :width: 6in
   :align: center

.. centered:: Figura 2-1 Pagina "Gestione FRCap" nel WebApp

Nel WebApp, fai clic in sequenza su "Impostazioni di sistema" -> "Gestione FRCap" -> "Strumenti di gestione". Questo aprirà una nuova scheda nel browser e accederà allo "Strumento di gestione FRCap".

.. image:: frcap_pictures/003.png
   :width: 6in
   :align: center

.. centered:: Figura 2-2 Strumento di gestione FRCap

Nello Strumento di gestione FRCap, seleziona "Creazione guidata", quindi inserisci o seleziona in sequenza i seguenti contenuti del plugin:

- Nome plugin: Hello_FRCap.
- Autore plugin: admin.
- Descrizione plugin: Hello FRCap.
- Tipo plugin: Configurazione.

L'icona del plugin non deve essere caricata. Dopo aver inserito o selezionato i parametri, fai clic su "Crea" per completare la creazione dell'FRCap.

.. image:: frcap_pictures/004.png
   :width: 6in
   :align: center

.. centered:: Figura 2-3 Creazione guidata FRCap

Dopo la creazione riuscita, verrai reindirizzato alla pagina di successo che mostra il nome dell'FRCap appena creato. Fai clic su "Scarica" per scaricare l'FRCap creato sul tuo computer locale.

.. image:: frcap_pictures/005.png
   :width: 6in
   :align: center

.. centered:: Figura 2-4 Scarica pacchetto plugin Hello FRCap

Ho già un FRCap
-----------------------
Se hai già una cartella di progetto FRCap e rispetta la struttura del progetto FRCap, leggi direttamente la sezione \ `Costruisci FRCap <frcap_quick_start.html#id3>`__\ .

Se hai già un pacchetto plugin completo con estensione file ".plugin", leggi direttamente la sezione \ `Hello FRCap <frcap_quick_start.html#hello-frcap>`__\ .

Costruire FRCap
-----------------------
Apri il progetto FRCap scaricato nel capitolo 2.1, oppure il tuo progetto FRCap esistente.

A seconda del sistema operativo in uso, apri prima lo script di build, modifica il parametro `buildName` con il nome desiderato, salva e chiudi, quindi esegui lo script corrispondente nel terminale.

- In Windows, avvia il terminale ed esegui il seguente comando:

.. code-block:: c++
   :linenos:

   ./build.bat

- In Linux, avvia il terminale ed esegui il seguente comando:
  
.. code-block:: c++
   :linenos:

   ./build.sh

Una volta completata la build, nella directory del progetto FRCap verrà generato un file pacchetto con il nome dell'FRCap e con estensione ".plugin".

.. image:: frcap_pictures/006.png
   :width: 6in
   :align: center

.. centered:: Figura 2-5 File pacchetto FRCap dopo la build

Hello FRCap
-------------
Dopo aver completato la build del progetto FRCap, apri un browser sul tuo computer locale, inserisci l'indirizzo IP predefinito del robot (http://192.168.58.2) e accedi al WebApp. Fai clic in sequenza su "Impostazioni di sistema" -> "Gestione FRCap" -> "Importa". Seleziona il file pacchetto FRCap con estensione ".plugin" appena creato e aprilo per caricarlo. Dopo il caricamento riuscito, le informazioni dell'FRCap importato verranno visualizzate nell'elenco delle informazioni plugin in basso.

Utilizza la colonna delle operazioni nell'elenco per attivare/disattivare o eliminare l'FRCap. Controlla lo stato di attivazione dell'FRCap nella colonna dello stato di attivazione/disattivazione.

Dopo aver attivato Hello FRCap, puoi utilizzarlo in "Applicazioni ausiliarie" -> "FRCap" -> "Hello FRCap". Questa pagina ospita FRCap di tipo configurazione, può essere visualizzata a schermo intero o a metà schermo e per impostazione predefinita viene visualizzata a metà schermo.

A questo punto, hai completato l'intero flusso rapido di creazione e utilizzo del plugin.

.. image:: frcap_pictures/007.png
   :width: 6in
   :align: center

.. centered:: Figura 2-6 Contenuto Hello FRCap

Per una guida dettagliata sulla creazione guidata, continua a leggere \ `Creazione guidata <frcap_create.html#id1>`__\ .

Per conoscere l'ambiente degli strumenti necessari e le linee guida per lo sviluppo di FRCap, consulta \ `Guida allo sviluppo <frcap_development_guidance.html#id1>`__\ .

Per conoscere le linee guida specifiche per l'utilizzo di FRCap nel WebApp, consulta \ `Utilizzo di FRCap in WebApp <frcap_use.html#webappfrcap>`__\ .