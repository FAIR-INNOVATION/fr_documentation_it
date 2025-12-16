Programming con Grafi a Nodi
==============================

.. toctree::
   :maxdepth: 6

Informazioni di Base
----------------------------------

Introduzione al Sistema
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Il programming con grafi a nodi è un software di programmazione sviluppato per robot. Le sue funzioni principali e caratteristiche tecniche sono le seguenti:

- Le connessioni tra i nodi rappresentano efficacemente le relazioni logiche contestuali del programma.
- Attraverso operazioni come la creazione di nodi, la loro connessione e la modifica dei parametri, è possibile completare la scrittura di programmi per robot semplicemente trascinando gli elementi e inserendo pochi parametri.
- Aiuta a visualizzare meglio il codice e a scrivere più rapidamente script per compiti complessi e ripetitivi.

.. image:: node_editor_software/001.png
   :width: 6in
   :align: center

.. centered:: Figura 11.1-1 Interfaccia di Programmazione con Grafi a Nodi

Barra degli Strumenti
~~~~~~~~~~~~~~~~~~~~~

Utilizzare la barra degli strumenti situata in alto a sinistra nella pagina di programmazione con grafi a nodi.

.. image:: node_editor_software/002.png
   :width: 6in
   :align: center

.. centered:: Figura 11.1-2 Barra degli Strumenti Operativi

.. note::
   .. image:: coding/006.png
      :height: 0.75in
      :align: left

   Nome: **Apri**
   
   Funzione: Apre il file del programma utente. In una finestra di dialogo, è possibile scegliere di caricare o eliminare file.

.. note::
   .. image:: coding/010.png
      :height: 0.75in
      :align: left

   Nome: **Salva**
   
   Funzione: Salva il contenuto modificato del grafo a nodi.

.. note::
   .. image:: node_editor_software/131.png
      :height: 0.75in
      :align: left

   Nome: **Ricarica**
   
   Funzione: Ricarica localmente il contenuto del grafo a nodi dell'operazione precedente.

.. note::
   .. image:: coding/007.png
      :height: 0.75in
      :align: left

   Nome: **Nuovo**
   
   Funzione: Crea un nuovo file di programmazione con grafi a nodi.

.. note::
   .. image:: coding/008.png
      :height: 0.75in
      :align: left

   Nome: **Esporta**
   
   Funzione: Dopo aver creato/aperto un file di programmazione con grafi a nodi, fare clic sul pulsante "Esporta" per aprire la finestra di dialogo "Esporta programmazione grafo a nodi". Selezionare il nome del file nell'area di lavoro per esportare il file (formato JSON).

.. note::
   .. image:: coding/009.png
      :height: 0.75in
      :align: left

   Nome: **Importa**
   
   Funzione: Fare clic sul pulsante "Importa" per aprire una finestra di dialogo di importazione. Selezionare il file da importare e, dopo aver cliccato su Importa, il contenuto del file verrà visualizzato nell'area di lavoro della programmazione con grafi a nodi.

.. note::
   .. image:: node_editor_software/129.png
      :height: 0.75in
      :align: left

   Nome: **Codice**
   
   Funzione: Dopo aver connesso il grafo a nodi, genera il codice Lua.

Operazioni sul Grafo a Nodi
----------------------------

Programma a Nodi
~~~~~~~~~~~~~~~~

Per avviare un programma a nodi, è necessario fare clic con il tasto destro del mouse su un'area vuota per aprire la barra di selezione dei programmi a nodi. I comandi del programma sono principalmente suddivisi in: comandi logici, comandi di movimento, comandi di controllo della forza, comandi di controllo, comandi Modbus, assi estesi, ecc.

La casella di input sopra la barra di selezione dei programmi a nodi consente una ricerca fuzzy per individuare rapidamente il comando del nodo desiderato.

Il flusso operativo specifico del programma a nodi è il seguente:

- Fare clic sul nodo di inizio "Begin" per creare la posizione di programmazione del nodo iniziale.
- Fare clic sul nodo comando del programma selezionato; il corrispondente grafo a nodi verrà visualizzato nell'area di lavoro, dove è possibile selezionare i parametri del comando da menu a tendina o inserirli manualmente.
- Funzione delle frecce a destra del nodo comando: 1. L'icona a freccia singola si collega al nodo successivo. 2. Se sono presenti più icone freccia, la prima icona "Body" si collega al nodo del contenuto, la seconda icona "Completed" si collega al nodo successivo.
- Collegare il nodo di inizio "Begin" con il programma a nodi completato per concludere l'operazione di programmazione del nodo.

Istruzione If/Else
------------------

Fare clic sul nodo dell'istruzione correlata a "If/Else" per accedere all'interfaccia di modifica del grafo a nodi. (Questa istruzione richiede una certa base di programmazione. Per assistenza, contattarci).

Istruzione "If/Else":

- First: Collega le istruzioni del nodo all'interno della condizione if.
- Second: Se sono immesse solo due condizioni di valutazione a sinistra, indica il collegamento alle istruzioni del nodo all'interno della condizione else; se sono presenti tre condizioni di valutazione a sinistra, indica il collegamento alle istruzioni del nodo all'interno della condizione elseif.
- Third: Se sono presenti tre condizioni di valutazione a sinistra, indica il collegamento alla condizione else.
- Completed: Collega alle istruzioni del nodo successive.

.. image:: node_editor_software/124.png
   :width: 6in
   :align: center

.. centered:: Figura 11.3-1 Interfaccia del Nodo Istruzione "If/Else"

Istruzione While
----------------

Fare clic sul nodo dell'istruzione correlata a "While" per accedere all'interfaccia di modifica del grafo a nodi.

Nella casella di input dopo While, inserire la condizione di attesa; nella casella di input dopo do, inserire le istruzioni di azione durante il ciclo. Fare clic su Salva per confermare. (Per comodità operativa, è possibile inserire arbitrariamente il contenuto di do e modificare successivamente il programma inserendo altre istruzioni per sostituirlo).

Istruzione "While":

- Condition: Condizione del ciclo while.

.. image:: node_editor_software/125.png
   :width: 6in
   :align: center

.. centered:: Figura 11.4-1 Interfaccia del Nodo Istruzione "While"

Istruzione di Salto
-------------------

Fare clic sul nodo dell'istruzione correlata al "Salto" per accedere all'interfaccia di modifica del grafo a nodi.

L'istruzione "Salto" ha la prima icona freccia "Body" che collega il nodo del contenuto principale e la seconda icona freccia "Completed" che collega il nodo istruzione goto della posizione di salto successiva. (Questa istruzione richiede una certa base di programmazione. Per assistenza, contattarci).

- Nome salto: Inserire il nome del salto per determinare la posizione di salto.

.. image:: node_editor_software/003.png
   :width: 6in
   :align: center

.. centered:: Figura 11.5-1 Interfaccia del Nodo Istruzione "Salto"

.. important:: Il nome del salto non può iniziare con un numero.

Istruzione di Attesa
--------------------

Fare clic sul nodo dell'istruzione correlata all'"Attesa" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è un'istruzione di ritardo, suddivisa in quattro parti: "WaitMs", "WaitDI", "WaitMultiDI" e "WaitAI".

1. Nodo istruzione "Attesa", parametri:

- Tempo di attesa (ms): L'unità di tempo per l'attesa di ritardo è il millisecondo. Inserire il numero di millisecondi da attendere.

.. image:: node_editor_software/004.png
   :width: 6in
   :align: center

.. centered:: Figura 11.6-1 Interfaccia del Nodo Istruzione "Attesa"

2. Nodo istruzione "Attesa DI", parametri:

- Porta DI: Ctrl-DI0 ~ Ctrl-DI7 (WaitDI, [0~15]), End-DI0 ~ End-DI1 (WaitToolDI, [0~1])
- Stato: false/true
- Tempo massimo (ms): 0 ~ 10000
- Gestione timeout attesa: Interrompi ed errore/Continua esecuzione/Attendi indefinitamente

.. image:: node_editor_software/005.png
   :width: 6in
   :align: center

.. centered:: Figura 11.6-2 Interfaccia del Nodo Istruzione "Attesa DI"

3. Nodo istruzione "Attesa DI multipli", parametri:

- Condizione: AND/OR
- Selezione condizione: Selezionare i numeri di porta attivi per lo stato del bit, separati da virgola, es. DI0, DI1
- Porte corrispondenti al valore vero: Selezionare i numeri di porta per il valore vero, separati da virgola, es. DI0, DI1
- Tempo massimo (ms): 0 ~ 10000, tempo massimo di attesa
- Gestione timeout attesa: Interrompi ed errore/Continua esecuzione/Attendi indefinitamente

.. image:: node_editor_software/006.png
   :width: 6in
   :align: center

.. centered:: Figura 11.6-3 Interfaccia del Nodo Istruzione "Attesa DI multipli"

4. Nodo istruzione "Attesa AI", parametri:

- Condizione: AND/OR
- Porta AI: Ctrl-AI0 ~ Ctrl-AI1 (WaitAI, [0~1]), End-AI0 (WaitToolAI, [0])
- Condizione: Maggiore di/Minore di
- Valore (%): 1 ~ 100
- Tempo massimo (ms): 0 ~ 10000
- Gestione timeout attesa: Interrompi ed errore/Continua esecuzione/Attendi indefinitamente. Quando si seleziona "Attendi indefinitamente", il tempo massimo predefinito è 0.

.. image:: node_editor_software/007.png
   :width: 6in
   :align: center

.. centered:: Figura 11.6-4 Interfaccia del Nodo Istruzione "Attesa AI"

Istruzione di Pausa
-------------------

Fare clic sul nodo istruzione "Pausa" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è un'istruzione di pausa. Inserendo questa istruzione nel programma, quando il programma la esegue, il robot si metterà in pausa. Per continuare l'esecuzione, fare clic sul pulsante "Pausa/Riprendi" nell'area di controllo.

Nodo istruzione "Pausa", parametri:

- Tipo di pausa: Nessuna funzione, Cilindro non in posizione, ecc.

.. image:: node_editor_software/008.png
   :width: 6in
   :align: center

.. centered:: Figura 11.7-1 Interfaccia del Nodo Istruzione "Pausa"

Istruzione Chiamata Sottoprogramma
-----------------------------------

Fare clic sul nodo istruzione "Chiamata sottoprogramma" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è per chiamare un sottoprogramma. Inserendo questa istruzione nel programma, quando il programma la esegue, il robot si metterà in pausa. Per continuare l'esecuzione, fare clic sul pulsante "Pausa/Riprendi" nell'area di controllo.

Nodo istruzione "Chiamata sottoprogramma", parametri:

- File dofile: Nome del file creato/generato
- Livello di chiamata: Primo livello/Secondo livello
- ID numero: ID della posizione corrispondente al livello di appartenenza

.. image:: node_editor_software/009.png
   :width: 6in
   :align: center

.. centered:: Figura 11.8-1 Interfaccia del Nodo Istruzione "Chiamata sottoprogramma"

Istruzione Imposta Variabile di Sistema
---------------------------------------

Fare clic sul nodo istruzione "Imposta variabile di sistema" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione serve per impostare le variabili di sistema ed è suddivisa in Imposta variabile di sistema e Ottieni variabile di sistema. Viene utilizzata in combinazione con istruzioni come while, if-else, ecc.

Nodo istruzione "Imposta variabile di sistema", parametri:

- Var: Nome della variabile personalizzata
- Valore: Inserire in base alla situazione effettiva

.. image:: node_editor_software/132.png
   :width: 6in
   :align: center

.. centered:: Figura 11.9-1 Interfaccia del Nodo Istruzione "Imposta variabile di sistema"

Nodo istruzione "Ottieni variabile di sistema", parametri:

- Var: Nome della variabile personalizzata

.. image:: node_editor_software/133.png
   :width: 6in
   :align: center

.. centered:: Figura 11.9-2 Interfaccia del Nodo Istruzione "Ottieni variabile di sistema"

.. important:: Il nome della variabile deve essere uno precedentemente definito.

Istruzione Punto a Punto (PTP)
------------------------------

Fare clic sul nodo istruzione "Punto a punto" per accedere all'interfaccia di modifica del grafo a nodi.

È possibile selezionare il punto da raggiungere. L'impostazione del tempo di transizione levigato permette un movimento continuo da quel punto al successivo. L'impostazione dell'offset permette di scegliere l'offset basato sul sistema di coordinate base o sull'offset basato sul sistema di coordinate utensile, e fa apparire le impostazioni dell'offset x, y, z, rx, ry, rz. Il percorso PTP specifico è il percorso ottimale pianificato automaticamente dal controllore di movimento.

Nodo istruzione "Punto a punto", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Arresto: false/true
- Transizione levigata (ms): Tempo di transizione levigata 0 ~ 500
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset.

.. image:: node_editor_software/010.png
   :width: 6in
   :align: center

.. centered:: Figura 11.10-1 Interfaccia del Nodo Istruzione "Punto a punto"

Istruzione Lineare (LIN)
------------------------

Fare clic sul nodo istruzione "Linea" per accedere all'interfaccia di modifica del grafo a nodi.

La funzione di questa istruzione è simile all'istruzione "Punto a punto", ma il percorso per raggiungere il punto con questa istruzione è una linea retta.

Nodo istruzione "Linea", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Arresto: false/true. Se si seleziona true, il parametro di transizione levigata non è valido.
- Transizione levigata (mm): Raggio di transizione levigata 0 ~ 1000
- Ricerca posizione: false/true
- Variabile punto di ricerca: REF0~99/RES0~99. Se "Ricerca posizione" è false, questo parametro non è valido.
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset.

.. image:: node_editor_software/011.png
   :width: 6in
   :align: center

.. centered:: Figura 11.11-1 Interfaccia del Nodo Istruzione "Linea"

Istruzione Lineare (seamPos)
-----------------------------

Fare clic sul nodo istruzione "Linea (seamPos)" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione viene applicata negli scenari di saldatura che utilizzano un sensore laser.

Nodo istruzione "Linea (seamPos)", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Arresto: false/true. Se si seleziona true, il parametro di transizione levigata non è valido.
- Transizione levigata (mm): Raggio di transizione levigata 0 ~ 1000
- Selezione dati cache cordone: Esegui dati pianificati/Esegui dati registrati
- Tipo di lamiera: Lamiera ondulata/Lamiera a cartone ondulato/Lamiera per recinzione/Barile/Acciaio ondulato
- Applica offset: No/Offset base/Offset utensile/Offset dati laser grezzi. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset

.. image:: node_editor_software/134.png
   :width: 6in
   :align: center

.. centered:: Figura 11.12-1 Interfaccia del Nodo Istruzione "Linea (seamPos)"

Istruzione Arco
---------------

Fare clic sul nodo istruzione "Arco" per accedere all'interfaccia di modifica del grafo a nodi.

Il movimento ad arco coinvolge due punti: il primo punto è il punto intermedio di transizione dell'arco, il secondo punto è il punto finale. Sia il punto di transizione che il punto finale possono essere configurati per l'offset, scegliendo tra offset basato sul sistema di coordinate base o offset basato sul sistema di coordinate utensile, impostando i valori di offset x, y, z, rx, ry, rz. Il punto finale può avere un raggio di transizione levigata impostato per ottenere un effetto di movimento continuo.

Nodo istruzione "Arco", parametri:

- Punto intermedio arco: Punto di insegnamento
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset
- Punto finale arco: Punto di insegnamento
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset
- Velocità di debug (%): 0 ~ 100
- Arresto: false/true. Se si seleziona true, il parametro di transizione levigata non è valido.
- Transizione levigata (mm): Raggio di transizione levigata 0 ~ 1000

.. image:: node_editor_software/012.png
   :width: 6in
   :align: center

.. centered:: Figura 11.13-1 Interfaccia del Nodo Istruzione "Arco"

Istruzione Cerchio Completo
----------------------------

Fare clic sul nodo istruzione "Cerchio completo" per accedere all'interfaccia di modifica del grafo a nodi.

Il movimento a cerchio completo coinvolge due punti: il primo punto è il punto intermedio di transizione 1 del cerchio completo, il secondo punto è il punto intermedio di transizione 2 del cerchio completo. Il punto di transizione 2 può essere configurato per l'offset, e questo offset si applica contemporaneamente sia al punto di transizione 1 che al punto di transizione 2.

Nodo istruzione "Cerchio completo", parametri:

- Punto intermedio 1 cerchio: Punto di insegnamento
- Punto intermedio 2 cerchio: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset

.. image:: node_editor_software/013.png
   :width: 6in
   :align: center

.. centered:: Figura 11.14-1 Interfaccia del Nodo Istruzione "Cerchio completo"

Istruzione Spirale
------------------

Fare clic sul nodo istruzione "Spirale" per accedere all'interfaccia di modifica del grafo a nodi.

Il movimento a spirale coinvolge tre punti. Questi tre punti formano un cerchio. Nella pagina delle impostazioni del terzo punto, sono inclusi parametri come il numero di giri della spirale, l'angolo di correzione dell'assetto, l'incremento del raggio e l'incremento della direzione dell'asse di rotazione. Il numero di giri della spirale indica il numero di giri del movimento a spirale. L'angolo di correzione dell'assetto regola l'assetto alla fine della spirale rispetto all'assetto del primo punto della spirale. L'incremento del raggio è l'aumento del raggio per ogni giro. L'incremento della direzione dell'asse di rotazione è l'aumento nella direzione dell'asse della spirale. Impostare se applicare l'offset; questo offset si applica all'intera traiettoria della spirale.

Nodo istruzione "Spirale", parametri:

- Punto intermedio 1 spirale: Punto di insegnamento
- Punto intermedio 2 spirale: Punto di insegnamento
- Punto intermedio 3 spirale: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset
- Numero di giri spirale: 0 ~ 100
- Angolo correzione assetto rx(°): -1000 ~ 1000
- Angolo correzione assetto ry(°): -1000 ~ 1000
- Angolo correzione assetto rz(°): -1000 ~ 1000
- Incremento raggio (mm): -100 ~ 100
- Incremento direzione asse rotazione (mm): -100 ~ 100

.. image:: node_editor_software/015.png
   :width: 6in
   :align: center

.. centered:: Figura 11.15-1 Interfaccia del Nodo Istruzione "Spirale"

Istruzione Nuova Spirale
------------------------

Fare clic sul nodo istruzione "Nuova Spirale" per accedere all'interfaccia di modifica del grafo a nodi.

Il movimento a nuova spirale è una versione ottimizzata del movimento a spirale. Questa istruzione richiede solo un punto più la configurazione di vari parametri per realizzare il movimento a spirale. Il robot utilizza la posizione corrente come punto di partenza. L'utente imposta la velocità di debug, se applicare l'offset, il numero di giri della spirale, l'angolo di inclinazione della spirale, il raggio iniziale, l'incremento del raggio, l'incremento della direzione dell'asse di rotazione e la direzione di rotazione. Il numero di giri della spirale indica il numero di giri del movimento a spirale. L'angolo di inclinazione della spirale è l'angolo tra l'asse Z dell'utensile e la direzione orizzontale. L'angolo di correzione dell'assetto regola l'assetto alla fine della spirale rispetto all'assetto del primo punto della spirale. Il raggio iniziale è la dimensione del raggio del primo giro. L'incremento del raggio è l'aumento del raggio per ogni giro. L'incremento della direzione dell'asse di rotazione è l'aumento nella direzione dell'asse della spirale. La direzione di rotazione può essere oraria o antioraria.

Nodo istruzione "Nuova Spirale", parametri:

- Punto di inizio spirale: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Applica offset: No/Offset base/Offset utensile. Se si sceglie "No", i parametri dx~drz non sono validi.
- dx~drz: Valori di offset
- Numero di giri spirale: 0 ~ 100
- Angolo inclinazione spirale (°): -100 ~ 100
- Raggio iniziale: 0 ~ 100
- Incremento raggio (mm): -100 ~ 100
- Incremento direzione asse rotazione (mm): -100 ~ 100
- Direzione rotazione: Oraria/Antioraria

.. image:: node_editor_software/016.png
   :width: 6in
   :align: center

.. centered:: Figura 11.16-1 Interfaccia del Nodo Istruzione "Nuova Spirale"

Istruzione Spirale Orizzontale
------------------------------

Fare clic sul nodo istruzione "Spirale Orizzontale" per accedere all'interfaccia di modifica del grafo a nodi.

L'istruzione "H-Spiral" è per un movimento a spirale nello spazio orizzontale. Questa istruzione viene impostata dopo un'istruzione di movimento a segmento singolo (linea).

Nodo istruzione "Spirale Orizzontale", parametri:

- Raggio spirale: 0~100mm
- Velocità angolare spirale: 0~2 giri/s
- Direzione rotazione: Spirale oraria/antioraria
- Angolo inclinazione spirale: 0~40°

.. image:: node_editor_software/014.png
   :width: 6in
   :align: center

.. centered:: Figura 11.17-1 Interfaccia del Nodo Istruzione "Spirale Orizzontale"

Istruzione Spline
-----------------

Fare clic sul nodo istruzione "Spline" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è suddivisa in tre parti: inizio gruppo spline, segmento spline e fine gruppo spline. L'inizio gruppo spline è il marcatore di inizio del movimento spline. Attualmente, il segmento spline nel grafo a nodi include solo il segmento SPL. La fine gruppo spline è il marcatore di fine del movimento spline.

Nodo istruzione "Spline-SPTP", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100

.. image:: node_editor_software/017.png
   :width: 6in
   :align: center

.. centered:: Figura 11.18-1 Interfaccia del Nodo Istruzione "Spline"

Istruzione Nuova Spline
-----------------------

Fare clic sul nodo istruzione "Nuova Spline" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è un'ottimizzazione dell'algoritmo dell'istruzione spline e in futuro sostituirà l'attuale istruzione spline. È suddivisa in tre parti: inizio traiettoria multi-punto, segmento traiettoria multi-punto e fine traiettoria multi-punto. L'inizio traiettoria multi-punto è il marcatore di inizio del movimento traiettoria multi-punto. Il segmento traiettoria multi-punto imposta i vari punti della traiettoria; fare clic sull'icona per accedere all'interfaccia di aggiunta punti. La fine traiettoria multi-punto è il marcatore di fine del movimento traiettoria multi-punto, dove è possibile impostare la modalità di controllo e la velocità di debug. La modalità di controllo è suddivisa in Punto di controllo dato e Punto percorso dato.

Nodo istruzione "Nuova Spline", parametri:

- Modalità controllo: Punto di insegnamento
- Tempo medio transizione globale: Intero, maggiore di 10, valore predefinito 2000ms

Nodo istruzione "Nuova Spline-SPL", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100
- Raggio transizione levigata: 0 ~ 1000
- Ultimo punto: No/Sì

.. image:: node_editor_software/018.png
   :width: 6in
   :align: center

.. centered:: Figura 11.19-1 Interfaccia del Nodo Istruzione "Nuova Spline"

Istruzione Oscillazione
-----------------------

Fare clic sul nodo istruzione "Oscillazione" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione comprende due parti. La prima parte seleziona il numero di oscillazione per il quale i parametri sono configurati. Il collegamento "Body" indica che il programma del nodo collegato viene eseguito tra "Inizia oscillazione" e "Ferma oscillazione".

Nodo istruzione "Oscillazione", parametri:

- Numero: 0~7

.. image:: node_editor_software/019.png
   :width: 6in
   :align: center

.. centered:: Figura 11.20-1 Interfaccia del Nodo Istruzione "Oscillazione"

Istruzione Riproduci Traiettoria
--------------------------------

Fare clic sul nodo istruzione "Riproduci traiettoria" per accedere all'interfaccia di modifica del grafo a nodi.

Per questa istruzione, l'utente deve prima avere una traiettoria registrata.

Durante la programmazione, utilizzare prima l'istruzione punto a punto per raggiungere il punto iniziale corrispondente della traiettoria. Quindi, nell'istruzione riproduci traiettoria, selezionare la traiettoria, scegliere la traiettoria levigata e impostare la velocità di debug. L'istruzione di caricamento traiettoria è principalmente utilizzata per leggere in anticipo il file di traiettoria, estrarlo come istruzione di traiettoria ed è meglio applicata in scenari di inseguimento del nastro trasportatore.

Nodo istruzione "Riproduci traiettoria", parametri:

- Nome traiettoria: Traiettoria registrata
- Traiettoria levigata: No/Sì
- Velocità di debug (%): 0 ~ 100, valore predefinito 25

.. image:: node_editor_software/020.png
   :width: 6in
   :align: center

.. centered:: Figura 11.21-1 Interfaccia del Nodo Istruzione "Riproduci traiettoria"

Istruzione Offset Punto
-----------------------

Fare clic sul nodo istruzione "Offset punto" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è per l'offset complessivo. Inserire i vari valori di offset. Il collegamento "Body" indica che il programma del nodo collegato viene eseguito tra l'inizio e la fine. Le istruzioni di movimento intermedie verranno compensate in base al sistema di coordinate base (o del pezzo).

Nodo istruzione "Offset punto", parametri:

- ∆x: Valore offset, -300~300
- ∆y: Valore offset, -300~300
- ∆z: Valore offset, -300~300
- ∆rx: Valore offset, -300~300
- ∆ry: Valore offset, -300~300
- ∆rz: Valore offset, -300~300

.. image:: node_editor_software/021.png
   :width: 6in
   :align: center

.. centered:: Figura 11.22-1 Interfaccia del Nodo Istruzione "Offset punto"

Istruzione Servo
----------------

Fare clic sul nodo istruzione "Servo" per accedere all'interfaccia di modifica del grafo a nodi.

Istruzione di controllo servo (movimento nello spazio cartesiano). Questa istruzione permette di controllare il movimento del robot attraverso il controllo della posa assoluta o l'offset basato sulla posa corrente.

Nodo istruzione "Servo", parametri:

- Modalità movimento: Posizione assoluta/Offset base/Offset utensile
- x: Valore offset, -300~300
- y: Valore offset, -300~300
- z: Valore offset, -300~300
- rx: Valore offset, -300~300
- ry: Valore offset, -300~300
- rz: Valore offset, -300~300
- Coefficiente scala x: 0~1
- Coefficiente scala y: 0~1
- Coefficiente scala z: 0~1
- Coefficiente scala rx: 0~1
- Coefficiente scala ry: 0~1
- Coefficiente scala rz: 0~1
- Accelerazione (%): 0~100
- Velocità (%): 0~100
- Periodo comando (s): 0.001~0.016
- Tempo filtro (s): 0~1
- Amplificazione scala: 0~100

.. image:: node_editor_software/022.png
   :width: 6in
   :align: center

.. centered:: Figura 11.23-1 Interfaccia del Nodo Istruzione "Servo"

Istruzione Traiettoria
----------------------

Fare clic sul nodo istruzione "Traiettoria" per accedere all'interfaccia di modifica del grafo a nodi.

Per questa istruzione, l'utente deve prima avere una traiettoria registrata.

Nodo istruzione "Traiettoria", parametri:

- Seleziona file traiettoria: Traiettoria registrata
- Velocità di debug (%): 0 ~ 100, valore predefinito 25

.. image:: node_editor_software/023.png
   :width: 6in
   :align: center

.. centered:: Figura 11.24-1 Interfaccia del Nodo Istruzione "Traiettoria"

Istruzione Traiettoria J
------------------------

Fare clic sul nodo istruzione "Traiettoria J" per accedere all'interfaccia di modifica del grafo a nodi.

Per questa istruzione, l'utente deve prima avere una traiettoria registrata. È possibile importare in anticipo il file di traiettoria nell'interfaccia di insegnamento del programma. Le istruzioni Traiettoria e Traiettoria J sono adatte per interfacce generali in cui la telecamera fornisce direttamente la traiettoria, soddisfacendo la necessità di importare nel sistema file di punti di traiettoria discreti in formato fisso, permettendo al robot di muoversi secondo la traiettoria del file importato.

Nodo istruzione "Traiettoria J", parametri:

- Seleziona file traiettoria: Traiettoria registrata
- Velocità di debug (%): 0 ~ 100, valore predefinito 25
- Modalità traiettoria: Punto percorso/Punto controllo

.. image:: node_editor_software/024.png
   :width: 6in
   :align: center

.. centered:: Figura 11.25-1 Interfaccia del Nodo Istruzione "Traiettoria J"

Istruzione DMP
--------------

Fare clic sul nodo istruzione "DMP" per accedere all'interfaccia di modifica del grafo a nodi.

Il DMP è un metodo di apprendimento per imitazione della traiettoria, che richiede una traiettoria di riferimento pianificata in anticipo. Nell'interfaccia di modifica del comando, selezionare un punto di insegnamento come nuovo punto di partenza, fare clic su "Aggiungi", "Applica" per salvare l'istruzione. Il percorso DMP specifico è la nuova traiettoria che imita la traiettoria di riferimento a partire dal nuovo punto di partenza.

Nodo istruzione "DMP", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0 ~ 100, valore predefinito 100

.. image:: node_editor_software/025.png
   :width: 6in
   :align: center

.. centered:: Figura 11.26-1 Interfaccia del Nodo Istruzione "DMP"

Istruzione Trasformazione Pezzo
-------------------------------

Fare clic sul nodo istruzione "Trasformazione pezzo" per accedere all'interfaccia di modifica del grafo a nodi.

Selezionare il sistema di coordinate del pezzo per cui si desidera l' conversione automatica. Fare clic su "Aggiungi", "Applica" per salvare l'istruzione. Quando si aggiungono istruzioni PTP, LIN collegate a "Body", si realizza l'esecuzione all'interno di questa istruzione con conversione automatica dei punti nel sistema di coordinate del pezzo.

Nodo istruzione "Trasformazione pezzo", parametri:

- Sistema coordinate pezzo: Elenco sistemi coordinate pezzo

.. image:: node_editor_software/026.png
   :width: 6in
   :align: center

.. centered:: Figura 11.27-1 Interfaccia del Nodo Istruzione "Trasformazione pezzo"

Istruzione Trasformazione Utensile
----------------------------------

Fare clic sul nodo istruzione "Trasformazione utensile" per accedere all'interfaccia di modifica del grafo a nodi.

Selezionare il sistema di coordinate utensile per cui si desidera l' conversione automatica. Fare clic su "Aggiungi", "Applica" per salvare l'istruzione. Quando si aggiungono istruzioni PTP, LIN collegate a "Body", si realizza l'esecuzione all'interno di questa istruzione con conversione automatica dei punti nel sistema di coordinate utensile.

Nodo istruzione "Trasformazione utensile", parametri:

- Sistema coordinate utensile: Elenco sistemi coordinate utensile

.. image:: node_editor_software/027.png
   :width: 6in
   :align: center

.. centered:: Figura 11.28-1 Interfaccia del Nodo Istruzione "Trasformazione utensile"

Nodo Istruzione I/O Digitale
----------------------------

Fare clic sul nodo istruzione "Imposta DO"/"Ottieni DI" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è per l'I/O digitale, suddivisa in impostazione I/O (SetDO/SPLCSetDO) e acquisizione I/O (GetDI/SPLCGetDI).

1. Nodo istruzione "Imposta DO", parametri:

- Porta: Ctrl-DO0 ~ Ctrl-DO7 (bloccante: SetDO, non bloccante: SPLCSetDO, [0~15]), End-DO0 ~ End-DO1 (bloccante: SetToolDO, non bloccante: SPLCSetToolDO, [0~1])
- Stato: false/true
- Bloccante: Bloccante/Non bloccante
- Traiettoria levigata: Break/Serious
- Applica thread: No/Sì

.. image:: node_editor_software/028.png
   :width: 6in
   :align: center

.. centered:: Figura 11.29-1 Interfaccia del Nodo Istruzione "Imposta DO"

2. Nodo istruzione "Ottieni DI", parametri:

- Porta: Ctrl-DI0 ~ Ctrl-DI7 (bloccante: GetDI, non bloccante: SPLCGetDI, [0~15]), End-DI0 ~ End-DI1 (bloccante: GetToolDI, non bloccante: SPLCGetToolDI, [0~1])
- Bloccante: Bloccante/Non bloccante
- Stato: false/true
- Tempo massimo attesa (ms): 0 ~ 10000
- Applica thread: No/Sì

.. image:: node_editor_software/029.png
   :width: 6in
   :align: center

.. centered:: Figura 11.29-2 Interfaccia del Nodo Istruzione "Ottieni DI"

Comando I/O Analogico
---------------------

Fare clic sul nodo istruzione "Imposta AO"/"Ottieni AI" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è suddivisa in due funzioni: impostazione uscita analogica (SetAO/SPLCSetAO) e acquisizione ingresso analogico (GetAI/SPLCGetAI).

1. Nodo istruzione "Imposta AO", parametri:

- Porta: Ctrl-AO0 ~ Ctrl-AO1 (bloccante: SetAO, non bloccante: SPLCSetAO, [0~1]), End-AO0 (bloccante: SetToolAO, non bloccante: SPLCSetToolAO, [0])
- Valore (%): 0 ~ 100
- Bloccante: Bloccante/Non bloccante
- Applica thread: No/Sì

.. image:: node_editor_software/030.png
   :width: 6in
   :align: center

.. centered:: Figura 11.30-1 Interfaccia del Nodo Istruzione "Imposta AO"

2. Nodo istruzione "Ottieni AI", parametri:

- Porta: Ctrl-AI0 ~ Ctrl-AI1 (bloccante: GetAI, non bloccante: SPLCGetAI, [0~1]), End-AI0 (bloccante: GetToolAI, non bloccante: SPLCGetToolAI, [0])
- Condizione: Maggiore di/Minore di
- Valore (%): 0 ~ 100
- Tempo massimo (ms): 0 ~ 10000
- Bloccante: Bloccante/Non bloccante
- Applica thread: No/Sì

.. image:: node_editor_software/031.png
   :width: 6in
   :align: center

.. centered:: Figura 11.30-2 Interfaccia del Nodo Istruzione "Ottieni AI"

Nodo Comando I/O Virtuale
--------------------------

Fare clic sul nodo istruzione "Imposta DI esterno virtuale"/"Imposta AI esterno virtuale" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è un comando di controllo I/O virtuale, che può impostare lo stato di DI e AI esterni virtuali e acquisire lo stato di DI e AI virtuali.

1. Nodo istruzione "Imposta DI esterno virtuale", parametri:

- Porta: Vir-Ctrl-DI0 ~ Vir-Ctrl-DI15 (SetVirtualDI, [0~15]), Vir-End-DI0 ~ Vir-End-DI1 (SetVirtualToolDI, [0~1])
- Stato: false/true

.. image:: node_editor_software/032.png
   :width: 6in
   :align: center

.. centered:: Figura 11.31-1 Interfaccia del Nodo Istruzione "Imposta DI esterno virtuale"

2. Nodo istruzione "Imposta AI esterno virtuale", parametri:

- Porta: Vir-Ctrl-AI0 ~ Vir-Ctrl-AI1 (SetVirtualAI, [0~1]), Vir-End-AI0 (SetVirtualToolAI, [0])
- Valore (V/mA): 0 ~ 20

.. image:: node_editor_software/033.png
   :width: 6in
   :align: center

.. centered:: Figura 11.31-2 Interfaccia del Nodo Istruzione "Imposta AI esterno virtuale"

Nodo Comando I/O Esteso
-----------------------

Fare clic sul nodo istruzione "Ottieni DI esterno virtuale"/"Ottieni AI esterno virtuale" per accedere all'interfaccia di modifica del grafo a nodi.

Aux-IO è la funzione di comando per la comunicazione tra robot e PLC per controllare I/O estesi esterni. Richiede l'instaurazione di una comunicazione UDP tra robot e PLC.

1. Nodo istruzione "Ottieni DI esterno virtuale", parametri:

- Porta: Vir-Ctrl-DI0 ~ Vir-Ctrl-DI15 (GetVirtualDI, [0~15]), Vir-End-DI0 ~ Vir-End-DI1 (GetVirtualToolDI, [0~1])

.. image:: node_editor_software/034.png
   :width: 6in
   :align: center

.. centered:: Figura 11.32-1 Interfaccia del Nodo Istruzione "Ottieni DI esterno virtuale"

2. Nodo istruzione "Ottieni AI esterno virtuale", parametri:

- Porta: Vir-Ctrl-AI0 ~ Vir-Ctrl-AI1 (GetVirtualAI, [0~1]), Vir-End-AI0 (GetVirtualToolAI, [0])

.. image:: node_editor_software/035.png
   :width: 6in
   :align: center

.. centered:: Figura 11.32-2 Interfaccia del Nodo Istruzione "Ottieni AI esterno virtuale"

3. Nodo istruzione "Configura comunicazione UDP", parametri:

- IP: Indirizzo IP
- Porta: Numero di porta
- Periodo comunicazione (ms): 0 ~ 10000

.. image:: node_editor_software/036.png
   :width: 6in
   :align: center

.. centered:: Figura 11.32-3 Interfaccia del Nodo Istruzione "Configura comunicazione UDP"

Comando DO Movimento
---------------------------

Fare clic sul nodo istruzione "DO movimento" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione realizza la funzione di output continuo del segnale DO durante il movimento lineare, in base all'intervallo impostato.

Nodo istruzione "Output continuo DO movimento", parametri:

- Porta: Ctrl-DO0 ~ Ctrl-DO15 (MoveDOStart, [0~15]), End-DO0 ~ End-DO1 (MoveDOStart, [0~1])
- Intervallo impostato (mm): 0 ~ 500
- Ciclo di lavoro impulso output (%): 0 ~ 99

Nodo istruzione "Output singolo DO movimento", parametri:

- Porta: Ctrl-DO0 ~ Ctrl-DO15 (MoveDOOnceStart, [0~15]), End-DO0 ~ End-DO1 (MoveDOOnceStart, [0~1])
- Modalità output: Output tratto a velocità costante/Configurazione libera
- Tempo set (ms): 0 ~ 1000 (Modalità output tratto a velocità costante predefinito -1)
- Tempo reset (ms): 0 ~ 1000 (Modalità output tratto a velocità costante predefinito -1)

.. image:: node_editor_software/037.png
   :width: 6in
   :align: center

.. centered:: Figura 11.33-1 Interfaccia del Nodo Istruzione "Output singolo/continuo DO movimento"

Comando Sistema di Coordinate
------------------------------

Fare clic sui nodi istruzione correlati a "Imposta sistema coordinate utensile"/"Imposta sistema coordinate pezzo" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è suddivisa in due funzioni: "Imposta sistema coordinate utensile" e "Imposta sistema coordinate pezzo".

Selezionare il nome del sistema di coordinate utensile, fare clic su "Applica" per aggiungere l'istruzione al programma. Quando il programma esegue questa istruzione, imposterà il sistema di coordinate utensile del robot.

1. Nodo istruzione "Imposta sistema coordinate utensile", parametri:

- Nome sistema coordinate utensile: toolcoord1 ~ toolcoord19 (SetToolList, [0~19]), etoolcoord0 ~ etoolcoord14 (SetExToolList, [0~14])

.. image:: node_editor_software/038.png
   :width: 6in
   :align: center

.. centered:: Figura 11.34-1 Interfaccia del Nodo Istruzione "Imposta sistema coordinate utensile"

2. Nodo istruzione "Imposta sistema coordinate pezzo", parametri:

- Nome sistema coordinate pezzo: wobjcoord1 ~ wobjcoord14

.. image:: node_editor_software/039.png
   :width: 6in
   :align: center

.. centered:: Figura 11.34-2 Interfaccia del Nodo Istruzione "Imposta sistema coordinate pezzo"

Comando Cambio Modalità
-----------------------

Fare clic sul nodo istruzione "Cambio modalità" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione può commutare il robot in modalità manuale. Di solito viene aggiunta alla fine di un programma, in modo che al termine dell'esecuzione del programma, il robot passi automaticamente in modalità manuale, permettendo all'utente di trascinarlo.

Nodo istruzione "Cambio modalità", parametri:

- Cambio modalità: Modalità manuale

.. image:: node_editor_software/040.png
   :width: 6in
   :align: center

.. centered:: Figura 11.35-1 Interfaccia del Nodo Istruzione "Cambio modalità"

Comando Livello Collisione
--------------------------

Fare clic sul nodo istruzione "Livello collisione" per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione imposta il livello di collisione. Attraverso questa istruzione, è possibile regolare in tempo reale il livello di collisione di ciascun asse durante l'esecuzione del programma, permettendo una distribuzione più flessibile degli scenari applicativi.

Nodo istruzione "Livello collisione", parametri:

- Livello standard: Livello standard/Percentuale personalizzata
- Giunto1-Giunto6 (N): 0 ~ 100, Soglia collisione, tipo array

.. image:: node_editor_software/041.png
   :width: 6in
   :align: center

.. centered:: Figura 11.36-1 Interfaccia del Nodo Istruzione "Livello collisione"

Comando Accelerazione
---------------------

Fare clic sul nodo istruzione "Accelerazione" per accedere all'interfaccia di modifica del grafo a nodi.

Il comando "Accelerazione" realizza la funzione di impostazione separata dell'accelerazione del robot. Regolando il fattore di scala dell'accelerazione dell'istruzione di movimento, è possibile aumentare o diminuire il tempo di accelerazione/decelerazione, realizzando la regolazione del tempo di ciclo dell'azione del robot.

Nodo istruzione "Accelerazione", parametri:

- Percentuale accelerazione (%): 0 ~ 100

.. image:: node_editor_software/042.png
   :width: 6in
   :align: center

.. centered:: Figura 11.37-1 Interfaccia del Nodo Istruzione "Accelerazione"

Istruzione Pinza
----------------

Questa istruzione è suddivisa in "Movimento pinza", "Attiva pinza" e "Ripristina pinza".

Nell'istruzione, viene visualizzato il numero della pinza che è stata configurata e attivata. Vengono impostati l'apertura/chiusura della pinza, la velocità di apertura/chiusura e la coppia di apertura/chiusura, i valori sono in percentuale. L'opzione di blocco: se si seleziona bloccante, il movimento della pinza attende il completamento dell'istruzione di movimento precedente prima di eseguire; se si seleziona non bloccante, il movimento della pinza viene eseguito in parallelo con l'istruzione di movimento precedente.

Nodo "Movimento pinza", parametri:

- Numero pinza: Numero pinza già attivata
- Posizione pinza: 0~100
- Velocità apertura/chiusura: 0~100
- Coppia apertura/chiusura: 0~100
- Tempo massimo (ms): 0~30000
- Bloccante: false/true

.. image:: node_editor_software/043.png
   :width: 6in
   :align: center

.. centered:: Figura 11.38-1 Interfaccia del Nodo "Movimento pinza"

L'istruzione di ripristino pinza visualizza il numero della pinza già configurata e permette di aggiungere l'istruzione di ripristino pinza al programma.

Nodo "Ripristina pinza", parametri:

- Numero pinza: Numero pinza già attivata

.. image:: node_editor_software/044.png
   :width: 6in
   :align: center

.. centered:: Figura 11.38-2 Interfaccia del Nodo "Ripristina pinza"

L'istruzione di attivazione pinza visualizza il numero della pinza già configurata e permette di aggiungere l'istruzione di attivazione pinza al programma.

Nodo "Attiva pinza", parametri:

- Numero pinza: Numero pinza già attivata

.. image:: node_editor_software/045.png
   :width: 6in
   :align: center

.. centered:: Figura 11.38-3 Interfaccia del Nodo "Attiva pinza"

Istruzione Pistola a Spruzzo
-----------------------------

Questa istruzione è relativa alla verniciatura a spruzzo, controllando la pistola a spruzzo per "Inizia spruzzo", "Ferma spruzzo", "Inizia pulizia pistola" e "Ferma pulizia pistola". Durante la modifica dei nodi relativi a questo programma, assicurarsi che la periferica della pistola a spruzzo sia stata configurata correttamente, altrimenti non sarà possibile salvare. Per i dettagli, vedere il capitolo sulle periferiche del robot.

.. image:: node_editor_software/046.png
   :width: 6in
   :align: center

.. centered:: Figura 11.39-1 Interfaccia Istruzione "Inizia spruzzo"

.. image:: node_editor_software/047.png
   :width: 6in
   :align: center

.. centered:: Figura 11.39-2 Interfaccia Istruzione "Ferma spruzzo"

.. image:: node_editor_software/048.png
   :width: 6in
   :align: center

.. centered:: Figura 11.39-3 Interfaccia Istruzione "Inizia pulizia pistola"

.. image:: node_editor_software/049.png
   :width: 6in
   :align: center

.. centered:: Figura 11.39-4 Interfaccia Istruzione "Ferma pulizia pistola"

Istruzione Asse Esteso (Controller + PLC)
-------------------------------------------

Questa istruzione è destinata a scenari che utilizzano assi esterni. Utilizzata in combinazione con l'istruzione PTP, può scomporre il movimento lungo la direzione X di un punto nello spazio nel movimento dell'asse esterno. Selezionare il numero dell'asse esterno, selezionare la modalità di movimento come sincrona, selezionare il punto da raggiungere.

Suddivisa in Caricamento/Configurazione comunicazione UDP, Movimento asincrono, Movimento PTP/LIN sincrono, Movimento ARC sincrono, Istruzione ritorno a zero e Istruzione abilitazione.

Nodo istruzione "Configurazione comunicazione UDP", inserire indirizzo IP, numero di porta e periodo di comunicazione.

.. image:: node_editor_software/050.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-1 Interfaccia Nodo Istruzione "Configurazione comunicazione UDP"

Nodo istruzione "Movimento asincrono", parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0~100

.. image:: node_editor_software/051.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-2 Interfaccia Nodo Istruzione "Movimento asincrono"

Nodo istruzione "Movimento PTP/LIN sincrono", parametri:

- Selezione movimento: PTP/LIN
- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0~100

.. image:: node_editor_software/052.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-3 Interfaccia Nodo Istruzione "Movimento PTP/LIN sincrono"

Nodo istruzione "Movimento ARC sincrono", modalità movimento predefinita ARC, parametri:

- Nome punto: Punto di insegnamento
- Velocità di debug (%): 0~100

.. image:: node_editor_software/053.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-4 Interfaccia Nodo Istruzione "Movimento ARC sincrono"

Nodo istruzione "Ritorno a zero", parametri:

- Numero asse esteso: 1~4
- Metodo ritorno a zero: Ritorno a zero posizione corrente/Ritorno a zero finecorsa negativo/Ritorno a zero finecorsa positivo
- Velocità ricerca zero: 0~2000, predefinito 5
- Velocità aggancio zero: 0~2000, predefinito 1

.. image:: node_editor_software/054.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-5 Interfaccia Nodo Istruzione "Ritorno a zero"

Nodo istruzione "Abilita", parametri:

- Numero asse esteso: 1~4

.. image:: node_editor_software/055.png
   :width: 6in
   :align: center

.. centered:: Figura 11.40-6 Interfaccia Nodo Istruzione "Abilita"

Istruzione Asse Esteso (Controller + Azionamento Servo)
--------------------------------------------------------------

Questa istruzione permette di configurare i parametri dell'asse esteso. Impostare parametri diversi in base alla diversa modalità di controllo. Per gli assi estesi già configurati, è possibile impostare il punto zero.

Suddivisa in ID servo, Modalità controllo, Abilitazione servo e Ritorno a zero servo; la Modalità controllo è a sua volta suddivisa in Modalità posizione e Modalità velocità. Questi due nodi devono essere utilizzati in combinazione con la Modalità controllo, altrimenti l'aggiunta singola non avrà effetto.

Nodo istruzione "ID servo", parametri:

- ID servo: 1~15

.. image:: node_editor_software/056.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-1 Interfaccia Nodo Istruzione "ID servo"

Nodo istruzione "Modalità controllo", parametri:

- ID servo: 1~15
- Modalità controllo: Modalità posizione/Modalità velocità

.. image:: node_editor_software/057.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-2 Interfaccia Nodo Istruzione "Modalità controllo"

Nodo istruzione "Abilitazione servo", parametri:

- ID servo: 1~15
- Abilitazione servo: Abilita servo/Disabilita servo

.. image:: node_editor_software/058.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-3 Interfaccia Nodo Istruzione "Abilitazione servo"

Nodo istruzione "Ritorno a zero servo", parametri:

- ID servo: 1~15
- Metodo ritorno a zero: Ritorno a zero posizione corrente/Ritorno a zero finecorsa negativo/Ritorno a zero finecorsa positivo
- Velocità ricerca zero: 0~2000, predefinito 5
- Velocità aggancio zero: 0~2000, predefinito 1
- Percentuale accelerazione: 1~100

.. image:: node_editor_software/059.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-4 Interfaccia Nodo Istruzione "Ritorno a zero servo"

Nodo istruzione "Modalità posizione", parametri:

- ID servo: 1~15
- Posizione obiettivo: Nessun limite
- Velocità ricerca zero: Nessun limite
- Percentuale accelerazione: 1~100

.. image:: node_editor_software/060.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-5 Interfaccia Nodo Istruzione "Modalità posizione"

Nodo istruzione "Modalità velocità", parametri:

- ID servo: 1~15
- Velocità obiettivo: Nessun limite
- Percentuale accelerazione: 1~100

.. image:: node_editor_software/061.png
   :width: 6in
   :align: center

.. centered:: Figura 11.41-6 Interfaccia Nodo Istruzione "Modalità velocità"

Istruzione Nastro Trasportatore
-------------------------------

Questa istruzione include quattro comandi: Rilevamento I/O in tempo reale, Rilevamento posizione in tempo reale, Avvia inseguimento e Ferma inseguimento. Per i dettagli, vedere il capitolo sulle periferiche del robot.

Nodo istruzione "Rilevamento I/O in tempo reale", parametri:

- Tempo massimo attesa: 0~10000

.. image:: node_editor_software/062.png
   :width: 6in
   :align: center

.. centered:: Figura 11.42-1 Interfaccia Nodo Istruzione "Rilevamento I/O in tempo reale"

Nodo istruzione "Rilevamento posizione in tempo reale", parametri:

- Modalità lavoro: Inseguimento e presa/Inseguimento movimento/Inseguimento TPD

.. image:: node_editor_software/063.png
   :width: 6in
   :align: center

.. centered:: Figura 11.42-2 Interfaccia Nodo Istruzione "Rilevamento posizione in tempo reale"

Nodo istruzione "Avvia inseguimento", parametri:

- Modalità lavoro: Inseguimento e presa/Inseguimento movimento/Inseguimento TPD

.. image:: node_editor_software/064.png
   :width: 6in
   :align: center

.. centered:: Figura 11.42-3 Interfaccia Nodo Istruzione "Avvia inseguimento"

.. image:: node_editor_software/065.png
   :width: 6in
   :align: center

.. centered:: Figura 11.42-4 Interfaccia Nodo Istruzione "Ferma inseguimento"

Istruzione Smerigliatura
------------------------

Questa istruzione è utilizzata per scenari di smerigliatura. Durante l'uso, è necessario prima scaricare il driver, poi caricarlo, quindi impostare l'abilitazione del dispositivo di smerigliatura. Successivamente, impostare la velocità di rotazione, la forza di contatto, la distanza di estensione e la modalità di controllo del dispositivo di smerigliatura. Allo stesso tempo, è possibile cancellare gli errori del dispositivo di smerigliatura e azzerare il sensore di forza del dispositivo.

.. image:: node_editor_software/066.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-1 Interfaccia Nodo Istruzione "Scarica driver comunicazione"

.. image:: node_editor_software/067.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-2 Interfaccia Nodo Istruzione "Carica driver comunicazione"

Nodo istruzione "Abilita dispositivo", parametri:

- Abilita dispositivo: Abilita/Disabilita

.. image:: node_editor_software/068.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-3 Interfaccia Nodo Istruzione "Abilita dispositivo"

.. image:: node_editor_software/069.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-4 Interfaccia Nodo Istruzione "Cancella errore dispositivo"

.. image:: node_editor_software/070.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-5 Interfaccia Nodo Istruzione "Azzera sensore forza dispositivo"

Nodo istruzione "Velocità rotazione", parametri:

- Velocità rotazione: 0~5500

.. image:: node_editor_software/071.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-6 Interfaccia Nodo Istruzione "Velocità rotazione"

Nodo istruzione "Forza di contatto", parametri:

- Forza di contatto: 0~200

.. image:: node_editor_software/072.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-7 Interfaccia Nodo Istruzione "Forza di contatto"

Nodo istruzione "Distanza di estensione", parametri:

- Distanza di estensione: 0~12

.. image:: node_editor_software/073.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-8 Interfaccia Nodo Istruzione "Distanza di estensione"

Nodo istruzione "Modalità controllo", parametri:

- Modalità controllo: Modalità ritorno a zero/Modalità posizione/Modalità coppia

.. image:: node_editor_software/074.png
   :width: 6in
   :align: center

.. centered:: Figura 11.43-9 Interfaccia Nodo Istruzione "Modalità controllo"

Istruzione Saldatura
--------------------

Fare clic sul nodo istruzione relativo alla saldatura per accedere all'interfaccia di modifica del grafo a nodi.

Questa istruzione è principalmente utilizzata per le periferiche della saldatrice. Prima di aggiungere questa istruzione, verificare che la configurazione della saldatrice nelle periferiche utente sia completata. Per i dettagli, vedere il capitolo sulle periferiche del robot.

1. Nodo istruzione "Tensione saldatrice", parametri:

- Tensione saldatrice: Valore minimo 0

.. image:: node_editor_software/075.png
   :width: 6in
   :align: center

.. centered:: Figura 11.44-1 Interfaccia Nodo Istruzione "Tensione saldatrice"

2. Nodo istruzione "Corrente saldatrice", parametri:

- Corrente saldatrice: Valore minimo 0

.. image:: node_editor_software/076.png
   :width: 6in
   :align: center

.. centered:: Figura 11.44-2 Interfaccia Nodo Istruzione "Corrente saldatrice"

3. Nodo istruzione "Arco finale/iniziale", parametri:

- Tipo I/O: I/O controller/I/O esteso
- Numero processo saldatura: 0 ~ 7
- Tempo massimo attesa (ms): 0 ~ 10000

.. image:: node_editor_software/077.png
   :width: 6in
   :align: center

.. centered:: Figura 11.44-3 Interfaccia Nodo Istruzione "Arco finale/iniziale"

4. Nodo istruzione "Apri/Chiudi gas", parametri:

- Tipo I/O: I/O controller/I/O esteso

.. image:: node_editor_software/078.png
   :width: 6in
   :align: center

.. centered:: Figura 11.44-4 Interfaccia Nodo Istruzione "Apri/Chiudi gas"

5. Nodo istruzione "Avanzamento filo positivo/Interruzione avanzamento positivo", parametri:

- Tipo I/O: I/O controller/I/O esteso

.. image:: node_editor_software/079.png
   :width: 6in
   :align: center

.. centered:: Figura 11.44-5 Interfaccia N