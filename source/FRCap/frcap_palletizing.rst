FRCap per Pallettizzazione
=================================

Gestione dei Pacchetti Plugin
-------------------------------------

Nella WebApp del robot collaborativo, nella pagina "Impostazioni di Sistema" -> "Configurazione Plugin", clicca sul pulsante "Importa", seleziona il pacchetto plugin FRCap per pallettizzazione (formato del nome: nome del pacchetto plugin + numero di versione.plugin, esempio: Palletizzatore Palletizer-v0.0.0.plugin) e caricalo. Dopo il caricamento riuscito, la lista mostrerà il pacchetto plugin FRCap per pallettizzazione importato con successo, inclusi lo stato di attivazione/disattivazione del plugin, nome, numero di versione, descrizione e autore, ecc. Nella barra delle operazioni, è possibile "Disattivare", "Attivare" ed "Eliminare" il pacchetto plugin FRCap per pallettizzazione.

.. image:: frcap_pictures/013.png
   :width: 6in
   :align: center

.. centered:: Figura 10-1-1 Interfaccia di Configurazione Plugin WebApp

Dopo la prima importazione riuscita del pacchetto plugin FRCap per pallettizzazione, lo stato del pacchetto sarà "Disattivato". Clicca sul pulsante "Attiva" e, dopo l'attivazione riuscita, il modulo "Applicazioni Ausiliarie" della WebApp del robot collaborativo aggiungerà la pagina iniziale del pacchetto plugin FRCap per pallettizzazione (ad esempio, il modulo di pagina corrispondente a Palletizzatore Palletizer-v0.0.0.plugin è "Palletizzatore Palletizer"). Clicca sul pulsante "Inizia" per accedere alla home page, visualizza le ricette di pallettizzazione attualmente configurate e utilizzale in base alle esigenze.

.. note:: 
   Se la ricetta è vuota, aggiungi/importa prima una ricetta.

.. image:: frcap_pictures/014.png
   :width: 6in
   :align: center

.. centered:: Figura 10-1-2 Visualizzazione WebApp + FRCap per Pallettizzazione

.. image:: frcap_pictures/015.png
   :width: 6in
   :align: center

.. centered:: Figura 10-1-3 Home Page di FRCap per Pallettizzazione

Gestione delle Ricette
------------------------------------
Ogni ricetta è divisa in tre aree principali: nome della ricetta, operazioni della ricetta e modifica della ricetta. I pulsanti nell'area operativa sono, in ordine: Rinomina, Esporta, Copia ed Elimina.

.. image:: frcap_pictures/016.png
   :width: 3in
   :align: center

.. centered:: Figura 10-2-1 Suddivisione delle Aree della Ricetta

.. note:: 
   .. image:: frcap_pictures/045.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Esporta Ricetta**
   | Funzione: Esporta i dati della ricetta corrente

.. note:: 
   .. image:: frcap_pictures/046.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Copia Ricetta**
   | Funzione: Copia i dati della ricetta corrente

.. note:: 
   .. image:: frcap_pictures/047.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Elimina Ricetta**
   | Funzione: Elimina la ricetta corrente

Ottenere
~~~~~~~~~~~~~~~
Dopo aver acceduto alla home page del plugin per pallettizzazione, ottieni tutte le ricette correnti. Quando il numero di ricette è superiore a quattro, nella zona di visualizzazione delle ricette appare una barra di scorrimento, consentendo all'utente di scorrere verso l'alto e il basso per visualizzare le ricette.

.. note:: 
   Tutti i nomi delle ricette iniziano con "palletizing", ad esempio "palletizing_test1".

.. image:: frcap_pictures/017.png
   :width: 3in
   :align: center

.. centered:: Figura 10-2-2 Ottenimento delle Ricette

Aggiungere
~~~~~~~~~~~~~~
Nell'area operativa di qualsiasi ricetta, clicca sul pulsante "Aggiungi", entra nella finestra di dialogo "Aggiungi Ricetta", inserisci il nome della ricetta di pallettizzazione e clicca sul pulsante "Conferma". Dopo l'aggiunta riuscita, l'area di visualizzazione delle ricette mostrerà la nuova ricetta di pallettizzazione aggiunta.

.. note:: 
   Tutti i nomi delle ricette iniziano con "palletizing", non è necessario inserire "palletizing", basta inserire il nome che segue "_". Ad esempio, per "palletizing_add", inserisci solo "add".

.. image:: frcap_pictures/018.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/019.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-3 Aggiunta di una Ricetta

Rinominare
~~~~~~~~~~~~~~~~~~
Nell'area operativa di qualsiasi ricetta, clicca sulla casella di immissione del nome della ricetta, entra nella finestra di dialogo "Rinomina Ricetta di Pallettizzazione", inserisci il nome della ricetta di pallettizzazione e clicca sul pulsante "Conferma". Dopo la rinomina riuscita, il nome originale della ricetta di pallettizzazione nell'area di visualizzazione verrà rinominato.

.. note::
   Tutti i nomi delle ricette iniziano con "palletizing", non è necessario inserire "palletizing", la finestra modale mostrerà automaticamente il nome che segue "_". Ad esempio, per "palletizing_rename", mostrerà automaticamente "rename".

.. image:: frcap_pictures/020.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-4 Rinomina di una Ricetta

Esportare
~~~~~~~~~~~~~~~
Nell'area operativa di qualsiasi ricetta, clicca sull'icona "Esporta" per scaricare tutti i dati della ricetta corrente.

.. image:: frcap_pictures/021.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-5 Esportazione di una Ricetta

Copiare
~~~~~~~~~~~~~~~~~
Nell'area operativa di qualsiasi ricetta, clicca sull'icona "Copia", entra nella finestra di dialogo "Copia Ricetta di Pallettizzazione", inserisci il nome della ricetta di pallettizzazione e clicca sul pulsante "Conferma". Dopo la copia riuscita, l'area di visualizzazione delle ricette mostrerà la ricetta di pallettizzazione copiata.

.. note:: 
   Tutti i nomi delle ricette iniziano con "palletizing", non è necessario inserire "palletizing", la finestra modale mostrerà automaticamente il nome che segue "_". Ad esempio, per "palletizing_copy", mostrerà automaticamente "copy".

.. image:: frcap_pictures/022.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-6 Copia di una Ricetta

Eliminare
~~~~~~~~~~~~~~~~~
Nell'area operativa di qualsiasi ricetta, clicca sull'icona "Elimina" per eliminare la ricetta corrente.

.. image:: frcap_pictures/023.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/024.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-7 Eliminazione di una Ricetta

Modificare
~~~~~~~~~~~~~~~~
Per qualsiasi ricetta, clicca sul pulsante "Modifica" per accedere all'interfaccia di configurazione della ricetta corrente.

.. image:: frcap_pictures/025.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-8 Modifica della Ricetta di Pallettizzazione

Importare
~~~~~~~~~~~~~~~~
Clicca sul pulsante "Importa", seleziona il pacchetto compresso della ricetta di pallettizzazione e caricalo. Dopo l'importazione riuscita, la ricetta di pallettizzazione includerà la ricetta importata.

.. note:: 
   Tutti i nomi dei pacchetti compressi delle ricette iniziano con "palletizing" e terminano con ".tar.gz", ad esempio "palletizing_import.tar.gz".

.. image:: frcap_pictures/026.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-9 Importazione di una Ricetta

.. important:: 
   Per "Aggiungi", "Rinomina" e "Copia" della ricetta di pallettizzazione, se viene inserito un nome di ricetta già esistente, verrà mostrato il messaggio "Esiste già una ricetta con lo stesso nome".

.. image:: frcap_pictures/027.png
   :width: 6in
   :align: center

.. centered:: Figura 10-2-10 Messaggio di Nome Duplicato della Ricetta

Configurazione della Ricetta
------------------------------------
L'interfaccia di configurazione di qualsiasi ricetta mostra le informazioni di base della configurazione di scatola, pallet, modalità e configurazione avanzata, con la configurazione dei parametri specifici effettuata nella rispettiva barra di configurazione.

.. image:: frcap_pictures/028.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-1 Interfaccia di Modifica della Ricetta di Pallettizzazione

Impostazione della Stazione di Lavoro
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Nella modifica della ricetta, è possibile scegliere se utilizzare una stazione di lavoro per pallettizzazione, come mostrato nella Figura 2-2. Se si utilizza la stazione di lavoro per pallettizzazione, le funzioni di pallettizzazione corrispondenti vengono completate utilizzando i segnali I/O nel PLC della stazione di lavoro; se si sceglie di non utilizzare una stazione di lavoro per pallettizzazione, per impostazione predefinita si utilizzano i segnali I/O sul quadro di controllo per completare le funzioni di pallettizzazione.

.. image:: frcap_pictures/076.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-1-1 Pagina di Modifica della Ricetta

Configurazione del Cablaggio I/O per la Funzione di Pallettizzazione
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(1) Dopo aver scelto di utilizzare la stazione di lavoro per pallettizzazione, clicca su Configurazione I/O Estesa. In base alla funzionalità corrispondente e al cablaggio effettivo con le interfacce I/O del PLC, è possibile selezionare personalmente la configurazione dei segnali I/O per la funzione di pallettizzazione. La Figura mostra la configurazione predefinita del cablaggio per la stazione di lavoro per pallettizzazione.

.. image:: frcap_pictures/077.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-1-2 Configurazione Predefinita del Cablaggio della Stazione di Lavoro per Pallettizzazione

(2) Se si sceglie di non utilizzare una stazione di lavoro per pallettizzazione, per impostazione predefinita vengono utilizzati i segnali I/O del quadro di controllo. In base alla funzionalità corrispondente e al cablaggio effettivo con le interfacce I/O del quadro di controllo, è possibile selezionare personalmente la configurazione dei segnali I/O per la funzione di pallettizzazione. La Figura mostra la configurazione predefinita del cablaggio senza stazione di lavoro per pallettizzazione (utilizzando I/O del quadro di controllo).

.. image:: frcap_pictures/078.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-1-3 Configurazione Predefinita del Cablaggio senza Stazione di Lavoro per Pallettizzazione (I/O Quadro di Controllo)

Test di Comunicazione I/O per la Funzione di Pallettizzazione
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(1) Quando si sceglie di utilizzare una stazione di lavoro per pallettizzazione, dopo aver configurato i segnali I/O estesi della stazione di lavoro per pallettizzazione, è possibile cliccare su "Test" per verificare le funzionalità I/O cablate;
 
.. image:: frcap_pictures/079.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-1-4 Test del Cablaggio I/O della Stazione di Lavoro per Pallettizzazione

(2) Quando si sceglie di non utilizzare una stazione di lavoro per pallettizzazione, dopo aver configurato i segnali I/O del quadro di controllo corrispondenti alle funzioni di pallettizzazione, è possibile cliccare su "Test" per verificare le funzionalità I/O cablate;
 
.. image:: frcap_pictures/080.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-1-5 Test del Cablaggio senza Stazione di Lavoro per Pallettizzazione (I/O Quadro di Controllo)

Configurazione della Scatola
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Operazioni sulla Scatola
++++++++++++++++++++++++++++++++

È possibile configurare più scatole di diversi tipi.

Clicca sul pulsante "Aggiungi", dopo l'aggiunta riuscita, verrà aggiunta una scatola nell'ordine corrente.

.. image:: frcap_pictures/048.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/049.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-2 Aggiunta di una Scatola

Clicca sull'area della casella di immissione mostrata dal nome della scatola, si aprirà la finestra modale "Rinomina Scatola". Inserisci il nome e clicca sul pulsante "Conferma" per confermare la rinomina.

.. image:: frcap_pictures/050.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-3 Rinomina di una Scatola

Clicca sull'icona "Copia", dopo la copia riuscita, verrà copiata una scatola in base al nome della scatola corrente.

.. image:: frcap_pictures/051.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/052.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-4 Copia di una Scatola

Clicca sull'icona "Elimina" per eliminare i dati della scatola.

.. note:: 
   Non eliminare le scatole già configurate nella configurazione della modalità.

.. image:: frcap_pictures/053.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/054.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-5 Eliminazione di una Scatola

Per qualsiasi scatola, clicca sul pulsante "Modifica" per accedere all'interfaccia di configurazione dei parametri della scatola. Dopo la configurazione riuscita, l'icona dello stato di configurazione della scatola diventa verde; quando la configurazione non è completata, l'icona dello stato di configurazione della scatola è gialla.

.. image:: frcap_pictures/055.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-6 Configurazione dei Parametri della Scatola Completata

.. image:: frcap_pictures/056.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-7 Configurazione dei Parametri della Scatola Non Completata

Parametri della Scatola
++++++++++++++++++++++++++++++++

.. note:: 
   .. image:: frcap_pictures/057.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Scatola Precedente**
   | Funzione: Passa alla scatola precedente. Quando viene selezionata la prima scatola, passando ancora si seleziona l'ultima scatola.

.. note:: 
   .. image:: frcap_pictures/058.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Scatola Successiva**
   | Funzione: Passa alla scatola successiva. Quando viene selezionata l'ultima scatola, passando ancora si seleziona la prima scatola.

Nella barra di configurazione della scatola, clicca su "Modifica" per accedere alla finestra di dialogo "Configurazione Scatola". Imposta "Lunghezza", "Larghezza", "Altezza", "Carico", "Orientamento Etichetta Pezzo", quindi clicca sul pulsante "Conferma" per completare la configurazione delle informazioni della scatola; imposta il punto di presa della scatola (mantenendo il punto di presa al centro della scatola, con la ventosa a contatto con la scatola in uno stato compresso), clicca sul pulsante "Registra" per completare l'impostazione.

.. image:: frcap_pictures/029.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-8 Configurazione della Scatola

.. image:: frcap_pictures/030.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-9 Punto di Presa della Scatola

.. important:: È necessario registrare il punto di presa della scatola, altrimenti non sarà possibile configurare lunghezza, larghezza e altezza della scatola.

Configurazione del Pallet
+++++++++++++++++++++++++++++++++
Nella barra di configurazione del pallet, clicca su "Configura" per accedere alla finestra di dialogo "Configurazione Pallet". Imposta "Lato Anteriore", "Lato Laterale" e "Altezza" del pallet, quindi imposta i punti di transizione della postazione, clicca su "Conferma Configurazione" per completare l'impostazione delle informazioni del pallet.

.. image:: frcap_pictures/031.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-10 Configurazione del Pallet

.. image:: frcap_pictures/032.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-11 Punto di Transizione della Postazione Sinistra

.. image:: frcap_pictures/033.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-12 Punto di Transizione della Postazione Destra

.. important:: È necessario registrare i punti di transizione della postazione, altrimenti il programma generato non potrà essere salvato.

Configurazione della Modalità
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Operazioni sulla Modalità
++++++++++++++++++++++++++++++

Nella configurazione della modalità, quando si seleziona una scatola, è possibile scegliere scatole con la stessa altezza ma lunghezza e larghezza diverse. L'area di visualizzazione della modalità è divisa in: Aggiunta Modalità (configurazione dello schema di pallettizzazione) e Configurazione dei Livelli di Pallettizzazione.

.. image:: frcap_pictures/059.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-13 Area di Visualizzazione della Modalità

Clicca sul pulsante "Aggiungi", dopo l'aggiunta riuscita, verrà aggiunta una modalità nell'ordine corrente.

.. image:: frcap_pictures/060.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/061.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-14 Aggiunta di una Modalità

In qualsiasi modalità nell'area di aggiunta modalità, clicca sull'area della casella di immissione mostrata dal nome della modalità, si aprirà la finestra modale "Rinomina Modalità". Inserisci il nome e clicca sul pulsante "Conferma" per confermare la rinomina.

.. image:: frcap_pictures/062.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-15 Rinomina di una Modalità

In qualsiasi modalità nell'area di aggiunta modalità, clicca sull'icona "Copia", dopo la copia riuscita, verrà copiata una modalità in base al nome della modalità corrente.

.. image:: frcap_pictures/063.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/064.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-16 Copia di una Modalità

In qualsiasi modalità nell'area di aggiunta modalità, clicca sull'icona "Elimina" per eliminare i dati della modalità corrente.

.. image:: frcap_pictures/065.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/066.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-17 Eliminazione di una Modalità

In qualsiasi modalità nell'area di aggiunta modalità, clicca sul pulsante "Modifica" per accedere alla finestra modale "Configurazione Modalità" e configura lo schema di pallettizzazione della modalità corrente. Dopo la configurazione riuscita, l'icona dello stato di configurazione della scatola diventa verde; quando la configurazione non è completata, l'icona dello stato di configurazione della scatola è gialla.

.. image:: frcap_pictures/067.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-18 Configurazione dei Parametri della Modalità Completata

.. image:: frcap_pictures/068.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-19 Configurazione dei Parametri della Modalità Non Completata

Nell'area di configurazione dei livelli di pallettizzazione, vengono mostrati il numero di livelli di pallettizzazione e l'ordinamento. Clicca sul pulsante "Modifica" per accedere alla finestra modale "Configurazione Sequenza Schema", inserisci il "Numero di Livelli di Pallettizzazione", seleziona la modalità per ogni livello, quindi clicca sul pulsante "Conferma" per completare la configurazione.

.. image:: frcap_pictures/069.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-20 Configurazione del Numero di Livelli di Pallettizzazione

Parametri della Modalità
++++++++++++++++++++++++++++++

.. note:: 
   .. image:: frcap_pictures/057.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Modalità Precedente**
   | Funzione: Passa alla modalità precedente. Quando viene selezionata la prima modalità, passando ancora si seleziona l'ultima modalità.

.. note:: 
   .. image:: frcap_pictures/058.png
      :width: 0.5in
      :height: 0.5in
      :align: left

   | Nome: **Modalità Successiva**
   | Funzione: Passa alla modalità successiva. Quando viene selezionata l'ultima modalità, passando ancora si seleziona la prima modalità.

Nella barra di configurazione della modalità, clicca su "Configura" per accedere alla finestra di dialogo "Configurazione Modalità". È principalmente divisa in quattro aree: selezione modalità, operazioni scatola e simulazione schema.

.. image:: frcap_pictures/040.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-21 Configurazione della Modalità

.. important:: 
   Quando si aggiungono scatole, se c'è collisione tra le scatole, lo sfondo del pezzo diventa rosso, e a questo punto le operazioni sopra non possono essere eseguite. Se necessario, regolare le scatole per evitare collisioni.

Nell'intestazione del pop-up, seleziona una modalità, quindi scegli le scatole nell'area di operazione delle scatole per aggiungerle sotto questa modalità. Puoi scegliere l'aggiunta con un clic, che per impostazione predefinita riempie il pallet centrato con scatole senza alcuno spazio. Personalizza la spaziatura delle scatole; le scatole possono essere aggiunte singolarmente o in batch. Fai clic su "Conferma" per completare la configurazione delle informazioni della modalità. Quando le scatole selezionate hanno altezze inconsistenti, la configurazione non può essere completata e apparirà il messaggio "Le altezze del tipo di scatola non sono coerenti e non possono essere aggiunte alla stessa modalità".

.. image:: frcap_pictures/070.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-22 Messaggio di Altezza Scatole Incoerente

Seleziona una modalità di riferimento (non è possibile selezionare la modalità già scelta), confronta e verifica se la configurazione della modalità corrente può effettuare pallettizzazione sulla base di questa modalità di riferimento, aiutando il cliente a visualizzare intuitivamente lo schema delle scatole in diverse modalità.

.. important:: 
   Direzione di Pallettizzazione: Prendendo come esempio il pallet destro, l'angolo in basso a destra è il punto più lontano. Posizionare una fila di pezzi verticalmente o orizzontalmente dall'angolo in basso a destra, quindi posizionare la fila successiva di pezzi orizzontalmente o verticalmente sopra, e così via (la direzione di pallettizzazione è indicata nella pagina Web, si prega di controllare). Per il pallet sinistro, i pezzi vengono posizionati in modo speculare rispetto allo schema del pallet destro.

Configurazione Avanzata
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Nella barra di configurazione avanzata, clicca su "Configura" per accedere alla finestra di dialogo "Configurazione Avanzata". Gli elementi di configurazione sono i seguenti:

.. image:: frcap_pictures/041.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-23 Configurazione Avanzata

1) Dimensioni del Dispositivo di Pallettizzazione: Le dimensioni del banco di lavoro per pallettizzazione.

.. image:: frcap_pictures/074.png
   :width: 6in
   :align: center

.. image:: frcap_pictures/075.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-24 Banco di Lavoro per Pallettizzazione

.. important::
   X, Y, Z sono i valori assoluti delle coordinate dell'angolo superiore destro del pallet sinistro o dell'angolo superiore sinistro del pallet destro rispetto al sistema di coordinate di base del robot. Angle è l'angolo di rotazione durante l'installazione del robot, si raccomanda di impostarlo a 0 durante l'installazione.

2) Altezza di Sollevamento per il Prelievo Materiale: Altezza personalizzata dall'utente a cui sollevare il materiale dopo il prelievo riuscito dal punto di presa.

3) Tempo di Attesa per il Prelievo Materiale: Tempo personalizzato dall'utente per attendere il segnale di pressione negativa dopo l'aspirazione. Se il segnale non arriva, ripetere l'azione di aspirazione.

4) Prima/Seconda Distanza di Offset: Distanza di offset personalizzata dall'utente per posizionare il robot inclinato fino al punto target.

.. note::
   Il parametro Z del primo offset deve essere maggiore dell'altezza della scatola, altrimenti durante il posizionamento potrebbe verificarsi collisione con le scatole già posizionate.

5) Configurazione del Divisore: Imposta le dimensioni "Lunghezza", "Larghezza" e "Altezza" del divisore e scegli l'attivazione/disattivazione del divisore.

.. note::
   Quando la funzione divisore è attivata, la gestione delle ricette mostra i parametri di base della configurazione del divisore nella visualizzazione della configurazione avanzata.

.. image:: frcap_pictures/034.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-25 Configurazione del Divisore

.. image:: frcap_pictures/071.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-26 Gestione Ricette - Configurazione Avanzata Mostra Configurazione Divisore

Quindi imposta i punti di transizione del divisore. I punti di transizione del divisore sono tre, l'impostazione ha lo scopo di pianificare approssimativamente un percorso di movimento dopo aver afferrato il divisore, evitando collisioni che impedirebbero il completamento dell'azione di posizionamento del divisore.

.. note:: Il punto di transizione 1 viene insegnato dopo aver mosso una certa distanza dal punto di presa della scatola; il punto di transizione 2 viene insegnato dopo aver mosso una certa distanza dal punto di transizione 1 e può anche essere considerato il punto intermedio di transizione; il punto di transizione 3 è l'ultimo punto prima del posizionamento del divisore, mosso una certa distanza dal punto di transizione 2.

.. image:: frcap_pictures/035.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-27 Punto di Transizione Divisore 1 (Esempio Postazione Destra)

.. image:: frcap_pictures/036.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-28 Punto di Transizione Divisore 2 (Esempio Postazione Destra)

.. image:: frcap_pictures/037.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-29 Punto di Transizione Divisore 3 (Esempio Postazione Destra)

Quindi imposta il punto di presa (mantenendo il punto di presa al centro del divisore, con la ventosa a contatto con il divisore in uno stato compresso) e il punto di posizionamento, clicca su "Conferma" per completare l'impostazione delle informazioni del divisore.

.. image:: frcap_pictures/038.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-30 Punto di Presa del Divisore (Esempio Postazione Destra)

.. image:: frcap_pictures/039.png
   :width: 3in
   :align: center

.. centered:: Figura 10-3-31 Punto di Posizionamento del Divisore (Esempio Postazione Destra)

6) Asse di Sollevamento: Configurazione personalizzata dall'utente per l'attivazione/disattivazione dell'asse di sollevamento, parametri di comunicazione (indirizzo IP, numero porta e ciclo di comunicazione), numero del livello di inizio sollevamento e scelta dell'attivazione/disattivazione dell'asse di sollevamento.

.. note::
   - Quando l'asse di sollevamento è in funzione, l'altezza di sollevamento ogni volta corrisponde all'altezza della scatola.
   - Quando la funzione asse di sollevamento è attivata, la home page mostra il pulsante di test dell'asse di sollevamento nella visualizzazione della configurazione avanzata. Cliccando sul pulsante "Test" si accede alla finestra di dialogo "Test Asse di Sollevamento", dove è possibile testare il caricamento della comunicazione, la salita e la discesa per verificarne l'accuratezza, evitando problemi di mancato funzionamento o grandi errori durante l'uso diretto.

.. image:: frcap_pictures/042.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-32 Configurazione dell'Asse di Sollevamento

.. image:: frcap_pictures/072.png
   :width: 6in
   :align: center

.. centered:: Figura 10-3-33 Gestione Ricette - Configurazione Avanzata Mostra Asse di Sollevamento

.. image:: frcap_pictures/073.png
   :width: 4in
   :align: center

.. centered:: Figura 10-3-34 Test dell'Asse di Sollevamento

Generazione Programma
------------------------
Visualizzare "Generazione Programma" sotto la visualizzazione della ricetta e selezionare la ricetta in base alla ricetta stessa e alle esigenze. Quando vengono selezionate ricette per entrambe le postazioni sinistra e destra, è necessario selezionare la priorità di avvio; quando viene selezionata una ricetta solo per la postazione sinistra o destra, non è necessario selezionare la priorità di avvio. Dopo aver inserito il nome del programma, fare clic sul pulsante "Genera".

.. note:: Tutti i nomi dei programmi iniziano con "palletizing". Non è necessario inserire "palletizing"; basta inserire il nome dopo "_". Ad esempio, per "palletizing_program", inserire "program".

.. image:: frcap_pictures/043.png
   :width: 4in
   :align: center

.. centered:: Figura 10-4-1 Generazione Programma – Selezione Ricette per Entrambe le Postazioni Sinistra e Destra

.. image:: frcap_pictures/081.png
   :width: 4in
   :align: center

.. centered:: Figura 10-4-2 Generazione Programma – Selezione Ricetta per Postazione Sinistra, Nessuna Ricetta per Postazione Destra

.. important::
    1. Se non viene selezionata alcuna ricetta di pallettizzazione per la postazione sinistra o destra, significa che quella postazione non è abilitata.
    2. Dopo aver generato con successo il programma, assicurarsi di salvare manualmente tutti i sottoprogrammi e il programma principale nell'Insegnamento Programmi.
    3. I programmi di spalletizzazione iniziano con "de". Ad esempio, se il programma di pallettizzazione è "palletizing_program", il programma di spalletizzazione sarà "depalletizing_program".
    4. Durante l'esecuzione di un programma con ricette configurate per entrambe le postazioni sinistra e destra, dopo aver ricevuto contemporaneamente i segnali di pezzo in posizione per sinistra e destra, il lavoro procede in base alla priorità impostata.

Programma a Singolo Punto di Prelievo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Esistono due scenari per un programma a singolo punto di prelievo:

(1) Le postazioni sinistra e destra selezionano la stessa ricetta;
(2) Le postazioni sinistra e destra selezionano ricette diverse, ma la posa del punto di prelievo della scatola configurata nelle ricette è la stessa.

.. image:: frcap_pictures/082.png
   :width: 4in
   :align: center

.. centered:: Figura 10-4-3 Singolo Punto di Prelievo – Punto di Prelievo Scatola

Programma a Doppio Punto di Prelievo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Per configurare un programma a doppio punto di prelievo, le postazioni sinistra e destra devono selezionare ricette diverse e le pose dei punti di prelievo della scatola configurate nelle ricette devono essere diverse.

.. image:: frcap_pictures/083.png
   :width: 4in
   :align: center

.. centered:: Figura 10-4-4 Doppio Punto di Prelievo – Punti di Prelievo Scatola