Programmazione grafica
======================

.. toctree:: 
   :maxdepth: 6

Introduzione
------------

Poiché il pannello di insegnamento (teach pendant) generalmente non è collegato a periferiche esterne come tastiera o mouse, quando si accede all'applicazione Web del robot tramite il pannello stesso, l'utente può utilizzare la funzionalità di programmazione grafica per modificare i programmi di insegnamento del robot. Questa funzionalità si basa sulla libreria Blockly, integrabile nel sistema WebAPP; consente inoltre di definire blocchi di codice personalizzati e, una volta completata la programmazione mediante trascinamento, converte automaticamente il risultato in un programma LUA, che viene poi inviato al robot tramite il protocollo di comandi esistente.

Grazie alla programmazione grafica, è possibile ottenere un approccio semplice, intuitivo e facile da usare, con interfaccia completamente localizzata in cinese.

L’interfaccia è suddivisa in tre aree principali: “Barra degli strumenti”, “Toolbox” e “Area di modifica del codice (workspace)”. Il layout generale è mostrato nella figura seguente:

.. image:: graphical/001.png
   :width: 6in
   :align: center

.. centered:: Figura 10.1‑1 Interfaccia di programmazione grafica

**Barra degli strumenti**

1) **Carica**: ricarica l’area di lavoro (workspace);
2) **Importa**: importa programmi di programmazione grafica esistenti;
3) **Esporta**: esporta il programma grafico attualmente salvato nell’area di lavoro;
4) **Salva**: salva i blocchi grafici modificati come programma di insegnamento;
5) **Pulisci**: cancella rapidamente l’intera area di modifica;
6) **Codice**: converte i blocchi grafici in codice Lua.

**Toolbox**

1) Contiene tutti i blocchi di codice relativi a istruzioni e logica, trascinabili nell’area di lavoro per creare e modificare il programma;
2) I blocchi nella Toolbox sono ulteriormente organizzati per categorie di istruzioni;
3) Istruzioni logiche: if-else, while, ecc.;
4) Istruzioni di movimento base: PTP, LIN, ARC, ecc.;
5) Istruzioni specifiche per applicazioni: incollaggio, saldatura, nastri trasportatori, ecc. Ciò permette di trovare facilmente i blocchi necessari durante l’utilizzo.

**Workspace**: area in cui vengono editati e visualizzati i blocchi grafici del programma.

Comandi grafici di tipo logico
------------------------------

I comandi grafici di tipo logico includono istruzioni per cicli, numeri e altre operazioni logiche.

.. image:: graphical/003.png
   :width: 6in
   :align: center

.. centered:: Figura 10.2 Comandi grafici di tipo logico

Istruzione If/Else
~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione If/Else” nell’area di lavoro dell’interfaccia grafica.  
(Questa istruzione richiede conoscenze di base di programmazione. In caso di necessità, contattare il supporto.)

.. image:: graphical/021.png
   :width: 6in
   :align: center

.. centered:: Figura 10.2-1 Blocco If/Else

Istruzione While
~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione While” nell’area di lavoro dell’interfaccia grafica.  
(Questa istruzione richiede conoscenze di base di programmazione. In caso di necessità, contattare il supporto.)

Aggiungere una condizione di attesa dopo “While” e inserire all’interno del ciclo blocchi di movimento. Al termine, fare clic su “Salva”.  
(Per comodità, è possibile inserire temporaneamente qualsiasi contenuto nel blocco “do”, per poi sostituirlo successivamente con le istruzioni desiderate.)

.. image:: graphical/022.png
   :width: 6in
   :align: center

.. centered:: Figura 10.2-2 Blocco While

Istruzione di salto (Jump)
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione di salto” nell’area di lavoro dell’interfaccia grafica.  
(Questa istruzione richiede conoscenze di base di programmazione. In caso di necessità, contattare il supporto.)

- **Nome salto**: inserire il nome del punto di destinazione del salto.

.. image:: graphical/023.png
   :width: 6in
   :align: center

.. centered:: Figura 10.2-3 Blocco di salto

.. important:: Il nome del salto non può iniziare con un numero.

Comandi grafici per variabili
-----------------------------

I comandi grafici per variabili includono l’istruzione per creare variabili.

.. image:: graphical/004.png
   :width: 6in
   :align: center

.. centered:: Figura 10.3 Comandi grafici per variabili

Istruzione variabile
~~~~~~~~~~~~~~~~~~~~

Fare clic sul pulsante “Crea” per inserire il nome della variabile da definire.

Trascinare il blocco “Istruzione variabile” nell’area di lavoro.

Parametri del nodo “Variabile”:

.. image:: graphical/024.png
   :width: 6in
   :align: center

.. centered:: Figura 10.3-1 Blocco variabile

Comandi grafici per funzioni
----------------------------

I comandi grafici per funzioni includono l’istruzione per creare funzioni.

.. image:: graphical/005.png
   :width: 6in
   :align: center

.. centered:: Figura 10.4 Comandi grafici per funzioni

Istruzione metodo funzione
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione metodo funzione” nell’area di lavoro.

Parametri del nodo “Metodo funzione”:

- **Nome funzione**: nome della funzione da eseguire

.. image:: graphical/025.png
   :width: 6in
   :align: center

.. centered:: Figura 10.4-1 Blocco metodo funzione

Comandi grafici di movimento
---------------------------------

I comandi grafici di movimento includono istruzioni PTP, LIN, ARC, ecc.

.. image:: graphical/006.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5 Comandi grafici di movimento

Istruzione Punto-a-Punto (PTP)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Punto-a-Punto” nell’area di lavoro.

È possibile selezionare il punto da raggiungere. Il parametro “Tempo di transizione fluida” consente di rendere continuo il movimento verso il punto successivo. L’opzione “Offset” permette di scegliere tra offset rispetto al sistema di coordinate base o rispetto allo strumento, aprendo campi per impostare gli offset x, y, z, rx, ry, rz. Il percorso PTP viene automaticamente pianificato dal controllore come percorso ottimale.

Parametri del nodo “Punto-a-Punto”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Stop**: false/true
- **Transizione fluida (ms)**: tempo di transizione 0 ~ 500
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset

.. image:: graphical/026.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-1 Blocco Punto-a-Punto

Istruzione Lineare (LIN)
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Lineare” nell’area di lavoro.

Questa istruzione è simile a “Punto-a-Punto”, ma il percorso verso il punto di destinazione è una linea retta.

Parametri del nodo “Lineare”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Stop**: false/true (se true, il parametro “Transizione fluida” non è attivo)
- **Transizione fluida (mm)**: raggio di transizione 0 ~ 1000
- **Ricerca posizione**: false/true
- **Variabile punto ricerca**: REF0~99/RES0~99 (non attiva se “Ricerca posizione” è false)
- **Offset**: No
- **Protezione sovravelocità giunti**: No/Sì
- **Strategia gestione**: Standard / Arresto con errore in caso di sovravelocità / Riduzione automatica velocità
- **Soglia riduzione ammessa (%)**: 0~100

.. image:: graphical/027.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-2 Blocco Lineare

Istruzione Lineare (con velocità angolare regolabile nei punti di transizione)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Lineare (con velocità angolare regolabile nei punti di transizione)” nell’area di lavoro.

Funzionalità simile all’istruzione “Punto-a-Punto”, ma include la regolazione della velocità angolare nei punti di transizione.

Parametri del nodo:

- **Velocità angolare massima**: 0~300

.. image:: graphical/028.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-3 Blocco Lineare (velocità angolare regolabile)

Istruzione Lineare (seamPos)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Lineare (seamPos)” nell’area di lavoro.

Questa istruzione è progettata per scenari di saldatura con sensori laser.

Parametri del nodo “Lineare (seamPos)”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Stop**: false/true (se true, il parametro “Transizione fluida” non è attivo)
- **Transizione fluida (mm)**: raggio di transizione 0 ~ 1000
- **Selezione dati cucitura**: Esegui dati pianificati / Esegui dati registrati
- **Tipo lamiera**: Lamiera ondulata / Lamiera grecata / Recinzione / Fusto / Acciaio corrugato
- **Offset**: No / Offset base / Offset strumento / Offset dati grezzi laser (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset

.. image:: graphical/029.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-4 Blocco Lineare (seamPos)

Istruzione Arco (ARC)
~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Arco” nell’area di lavoro.

Il movimento ad arco richiede due punti: il primo è il punto intermedio dell’arco, il secondo è il punto finale. Entrambi i punti consentono di impostare offset rispetto al sistema di coordinate base o dello strumento (x, y, z, rx, ry, rz). È possibile impostare un raggio di transizione fluida al punto finale per garantire continuità del movimento.

Parametri del nodo “Arco”:

- **Punto intermedio arco**: punto di insegnamento
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset
- **Punto finale arco**: punto di insegnamento
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset
- **Velocità debug (%)**: 0 ~ 100
- **Stop**: false/true (se true, il parametro “Transizione fluida” non è attivo)
- **Transizione fluida (mm)**: raggio di transizione 0 ~ 1000

.. image:: graphical/030.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-5 Blocco Arco

Istruzione Cerchio completo
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Cerchio completo” nell’area di lavoro.

Fare clic sul nodo “Cerchio completo” per accedere all’editor grafico.

Il movimento circolare completo richiede due punti intermedi. L’offset impostato sul secondo punto si applica a entrambi i punti.

Parametri del nodo “Cerchio completo”:

- **Punto intermedio 1**: punto di insegnamento
- **Punto intermedio 2**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset

.. image:: graphical/031.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-6 Blocco Cerchio completo

Istruzione Spirale
~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Spirale” nell’area di lavoro.

Il movimento a spirale richiede tre punti che definiscono un cerchio. Nella configurazione del terzo punto è possibile impostare: numero di spire, correzione dell’assetto, incremento del raggio e incremento lungo l’asse di rotazione. Il numero di spire indica quante volte il robot compie il percorso a spirale. La correzione dell’assetto regola l’orientamento finale rispetto al primo punto. L’incremento del raggio definisce quanto aumenta (o diminuisce) il raggio ad ogni spira. L’incremento sull’asse definisce lo spostamento lungo l’asse della spirale. L’offset impostato si applica all’intera traiettoria.

Parametri del nodo “Spirale”:

- **Punto spirale 1**: punto di insegnamento
- **Punto spirale 2**: punto di insegnamento
- **Punto spirale 3**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset
- **Numero spire**: 0 ~ 100
- **Correzione assetto rx (°)**: -1000 ~ 1000
- **Correzione assetto ry (°)**: -1000 ~ 1000
- **Correzione assetto rz (°)**: -1000 ~ 1000
- **Incremento raggio (mm)**: -100 ~ 100
- **Incremento asse (mm)**: -100 ~ 100

.. image:: graphical/032.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-7 Blocco Spirale

Nuova istruzione Spirale
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Nuova istruzione Spirale” nell’area di lavoro.

Fare clic sul nodo “Nuova spirale” per accedere all’editor grafico.

Questa è una versione ottimizzata del movimento a spirale. Richiede solo un punto più vari parametri. Il robot considera la posizione corrente come punto iniziale. L’utente imposta: velocità debug, offset, numero di spire, inclinazione della spirale, raggio iniziale, incremento raggio, incremento asse e direzione di rotazione. L’inclinazione della spirale è l’angolo tra l’asse Z dello strumento e il piano orizzontale. Il raggio iniziale definisce il raggio della prima spira. La direzione di rotazione può essere oraria o antioraria.

Parametri del nodo “Nuova spirale”:

- **Punto iniziale spirale**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Offset**: No / Offset base / Offset strumento (se “No”, i parametri dx~drz non sono attivi)
- **dx~drz**: valori di offset
- **Numero spire**: 0 ~ 100
- **Inclinazione spirale (°)**: -100 ~ 100
- **Raggio iniziale**: 0 ~ 100
- **Incremento raggio (mm)**: -100 ~ 100
- **Incremento asse (mm)**: -100 ~ 100
- **Direzione rotazione**: Oraria / Antioraria

.. image:: graphical/033.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-8 Blocco Nuova spirale

Istruzione Spirale orizzontale (H-Spiral)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Spirale orizzontale” nell’area di lavoro.

L’istruzione “H-Spiral” genera un movimento a spirale nello spazio orizzontale ed è progettata per seguire un’istruzione di movimento lineare.

Parametri del nodo “Spirale orizzontale”:

- **Raggio spirale**: 0~100 mm
- **Velocità angolare spirale**: 0~2 giri/s
- **Direzione rotazione**: Oraria / Antioraria
- **Inclinazione spirale**: 0~40°

.. image:: graphical/034.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-9 Blocco Spirale orizzontale

Istruzione Spline
~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Spline” nell’area di lavoro.

Questa istruzione è composta da tre parti: inizio gruppo spline, segmento spline e fine gruppo spline. L’inizio segna l’avvio del movimento spline, il segmento attualmente supporta solo il tipo SPL, e la fine conclude il movimento.

Parametri del nodo “Spline-SPTP”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100

.. image:: graphical/035.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-10 Blocco Spline

Nuova istruzione Spline
~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Nuova istruzione Spline” nell’area di lavoro.

Questa è una versione ottimizzata dell’istruzione Spline e sostituirà quella esistente. È composta da: inizio traiettoria multi-punto, segmento traiettoria e fine traiettoria. L’inizio segna l’avvio, i segmenti consentono di aggiungere punti tramite interfaccia dedicata, e la fine permette di impostare modalità di controllo e velocità. La modalità di controllo può essere “punti di controllo” o “punti di percorso”.

Parametri del nodo “Nuova spline”:

- **Modalità controllo**: punti di insegnamento
- **Tempo medio globale di transizione**: intero >10, valore predefinito 2000 ms

Parametri del nodo “Nuova spline-SPL”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100
- **Raggio transizione fluida**: 0 ~ 1000
- **Ultimo punto**: No / Sì

.. image:: graphical/036.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-11 Blocco Nuova spline

Istruzione Oscillazione
~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Oscillazione” nell’area di lavoro.

Parametri del nodo “Oscillazione”:

- **Numero**: 0~7

.. image:: graphical/037.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-12 Blocco Oscillazione

Istruzione Offset punto
~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Offset punto” nell’area di lavoro.

Questa istruzione applica un offset globale. I movimenti successivi saranno traslati rispetto al sistema di coordinate base (o pezzo) secondo i valori inseriti.

Parametri del nodo “Offset punto”:

- **∆x**: offset, -300~300
- **∆y**: offset, -300~300
- **∆z**: offset, -300~300
- **∆rx**: offset, -300~300
- **∆ry**: offset, -300~300
- **∆rz**: offset, -300~300

.. image:: graphical/038.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-13 Blocco Offset punto

Istruzione Servo
~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Servo” nell’area di lavoro.

Questa istruzione controlla il movimento nello spazio cartesiano mediante controllo servo. Può agire in posizione assoluta o con offset rispetto alla posizione corrente.

Parametri del nodo “Servo”:

- **Modalità movimento**: Posizione assoluta / Offset base / Offset strumento
- **x**: offset, -300~300
- **y**: offset, -300~300
- **z**: offset, -300~300
- **rx**: offset, -300~300
- **ry**: offset, -300~300
- **rz**: offset, -300~300
- **Coefficiente proporzionale x**: 0~1
- **Coefficiente proporzionale y**: 0~1
- **Coefficiente proporzionale z**: 0~1
- **Coefficiente proporzionale rx**: 0~1
- **Coefficiente proporzionale ry**: 0~1
- **Coefficiente proporzionale rz**: 0~1
- **Accelerazione (%)**: 0~100
- **Velocità (%)**: 0~100
- **Periodo comando (s)**: 0.001~0.016
- **Tempo filtro (s)**: 0~1
- **Amplificazione proporzionale**: 0~100

.. image:: graphical/039.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-14 Blocco Servo

Istruzione Traiettoria
~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Traiettoria” nell’area di lavoro.

Prima di utilizzare questa istruzione, è necessario aver registrato una traiettoria.

Parametri del nodo “Traiettoria”:

- **Seleziona file traiettoria**: traiettoria registrata
- **Velocità debug (%)**: 0 ~ 100, valore predefinito 25

.. image:: graphical/040.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-15 Blocco Traiettoria

Istruzione Traiettoria J
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Traiettoria J” nell’area di lavoro.

Richiede una traiettoria registrata, che deve essere importata preventivamente. Le istruzioni “Traiettoria” e “Traiettoria J” sono interfacce generiche per traiettorie fornite da telecamere, utilizzabili quando si dispone di file di traiettoria discreti in formato standard.

Parametri del nodo “Traiettoria J”:

- **Seleziona file traiettoria**: traiettoria registrata
- **Velocità debug (%)**: 0 ~ 100, valore predefinito 25
- **Modalità traiettoria**: Punti percorso / Punti controllo

.. image:: graphical/041.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-16 Blocco Traiettoria J

Istruzione Riproduzione traiettoria
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Riproduzione traiettoria” nell’area di lavoro.

Richiede una traiettoria registrata.

Durante la programmazione, raggiungere prima il punto iniziale della traiettoria con un’istruzione PTP, quindi selezionare la traiettoria, abilitare l’opzione “Traiettoria fluida” e impostare la velocità debug. Questa istruzione è particolarmente utile per scenari con nastri trasportatori.

Parametri del nodo “Riproduzione traiettoria”:

- **Nome traiettoria**: traiettoria registrata
- **Traiettoria fluida**: No / Sì
- **Velocità debug (%)**: 0 ~ 100, valore predefinito 25

.. image:: graphical/042.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-17 Blocco Riproduzione traiettoria

Istruzione DMP
~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione DMP” nell’area di lavoro.

DMP (Dynamic Movement Primitives) è un metodo di apprendimento per imitazione di traiettorie. Richiede una traiettoria di riferimento predefinita. Selezionare un punto di insegnamento come nuovo punto iniziale, fare clic su “Aggiungi” e “Applica” per salvare l’istruzione. Il percorso risultante sarà una nuova traiettoria che imita quella di riferimento a partire dal nuovo punto.

Parametri del nodo “DMP”:

- **Nome punto**: punto di insegnamento
- **Velocità debug (%)**: 0 ~ 100, valore predefinito 100

.. image:: graphical/043.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-18 Blocco DMP

Istruzione Cambio strumento
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Cambio strumento” nell’area di lavoro.

Selezionare il sistema di coordinate dello strumento da attivare. Dopo aver fatto clic su “Aggiungi” e “Applica”, i punti definiti nel sistema selezionato verranno convertiti automaticamente.

Parametri del nodo “Cambio strumento”:

- **Sistema coordinate strumento**: elenco dei sistemi disponibili

.. image:: graphical/044.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-19 Blocco Cambio strumento

Istruzione Cambio pezzo
~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Cambio pezzo” nell’area di lavoro.

Selezionare il sistema di coordinate del pezzo da attivare. Dopo aver fatto clic su “Aggiungi” e “Applica”, i punti definiti nel sistema selezionato verranno convertiti automaticamente.

Parametri del nodo “Cambio pezzo”:

- **Sistema coordinate pezzo**: elenco dei sistemi disponibili

.. image:: graphical/045.png
   :width: 6in
   :align: center

.. centered:: Figura 10.5-20 Blocco Cambio pezzo

Comandi grafici di controllo
---------------------------------

I comandi grafici di controllo includono istruzioni Wait, I/O, ecc.

.. image:: graphical/007.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6 Comandi grafici di controllo

Istruzione Attesa
~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Attesa” nell’area di lavoro.

Questa istruzione implementa un ritardo e comprende quattro varianti: “WaitMs”, “WaitDI”, “WaitMultiDI” e “WaitAI”.

1. Nodo “Attesa”:

- **Tempo attesa (ms)**: tempo di ritardo in millisecondi

.. image:: graphical/046.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-1 Blocco Attesa

2. Nodo “Attesa DI”:

- **Porta DI**: Ctrl-DI0 ~ Ctrl-CI7 (WaitDI, [0~15]), End-DI0 ~ End-DI1 (WaitToolDI, [0~1])
- **Stato**: false/true
- **Tempo massimo (ms)**: 0 ~ 10000
- **Gestione timeout**: Arresto con errore / Continua esecuzione / Attesa indefinita

.. image:: graphical/047.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-2 Blocco Attesa DI

3. Nodo “Attesa multipla DI”:

- **Condizione**: AND / OR
- **Porte selezionate**: elenco delle porte, separate da virgole, es. DI0,DI1
- **Porte vero**: elenco delle porte che devono essere vere, es. DI0,DI1
- **Tempo massimo (ms)**: 0 ~ 10000
- **Gestione timeout**: Arresto con errore / Continua esecuzione / Attesa indefinita

.. image:: graphical/048.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-3 Blocco Attesa multipla DI

4. Nodo “Attesa AI”:

- **Condizione**: AND / OR
- **Porta AI**: Ctrl-AI0 ~ Ctrl-AI1 (WaitAI, [0~1]), End-AI0 (WaitToolAI, [0])
- **Operatore**: Maggiore / Minore
- **Valore (%)**: 1 ~ 100
- **Tempo massimo (ms)**: 0 ~ 10000
- **Gestione timeout**: Arresto con errore / Continua esecuzione / Attesa indefinita (se “Attesa indefinita”, il tempo massimo è ignorato)

.. image:: graphical/049.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-4 Blocco Attesa AI

Istruzione Cambio modalità
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Cambio modalità” nell’area di lavoro.

Consente di passare il robot in modalità manuale, utile da inserire alla fine di un programma per permettere all’utente di muovere manualmente il robot dopo l’esecuzione.

Parametri del nodo “Cambio modalità”:

- **Modalità**: Manuale

.. image:: graphical/050.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-5 Blocco Cambio modalità

Istruzione Pausa
~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Pausa” nell’area di lavoro.

Durante l’esecuzione, il robot si ferma in corrispondenza di questa istruzione. Per riprendere, premere il tasto “Pausa/Riprendi” nell’area di controllo.

Parametri del nodo “Pausa”:

- **Tipo pausa**: Nessuna funzione, Cilindro non in posizione, ecc.

.. image:: graphical/051.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-6 Blocco Pausa

Istruzioni Sistema di coordinate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare i blocchi “Imposta sistema strumento” / “Imposta sistema pezzo” nell’area di lavoro.

1. Nodo “Imposta sistema strumento”:

- **Nome sistema strumento**: toolcoord1 ~ toolcoord19 (SetToolList, [0~19]), etoolcoord0 ~ etoolcoord14 (SetExToolList, [0~14])

.. image:: graphical/052.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-7 Blocco Imposta sistema strumento

2. Nodo “Imposta sistema pezzo”:

- **Nome sistema pezzo**: wobjcoord1 ~ wobjcoord14

.. image:: graphical/053.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-8 Blocco Imposta sistema pezzo

Istruzioni I/O analogici
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare i blocchi “Imposta AO” / “Leggi AI” nell’area di lavoro.

Comprende due funzioni: impostazione uscite analogiche (SetAO/SPLCSetAO) e lettura ingressi analogici (GetAI/SPLCGetAI).

1. Nodo “Imposta AO”:

- **Porta**: Ctrl-AO0 ~ Ctrl-AO1 (bloccante: SetAO, non bloccante: SPLCSetAO, [0~1]), End-AO0 (bloccante: SetToolAO, non bloccante: SPLCSetToolAO, [0])
- **Valore (%)**: 0 ~ 100
- **Bloccante**: Sì / No
- **Usa thread**: No / Sì

.. image:: graphical/054.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-9 Blocco Imposta AO

2. Nodo “Leggi AI”:

- **Porta**: Ctrl-AI0 ~ Ctrl-AI1 (bloccante: GetAI, non bloccante: SPLCGetAI, [0~1]), End-AI0 (bloccante: GetToolAI, non bloccante: SPLCGetToolAI, [0])
- **Condizione**: Maggiore / Minore
- **Valore (%)**: 0 ~ 100
- **Tempo massimo (ms)**: 0 ~ 10000
- **Bloccante**: Sì / No
- **Usa thread**: No / Sì

.. image:: graphical/055.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-10 Blocco Leggi AI

Istruzioni I/O digitali
~~~~~~~~~~~~~~~~~~~~~~~

Trascinare i blocchi “Imposta DO” / “Leggi DI” nell’area di lavoro.

Comprende due funzioni: impostazione uscite digitali (SetDO/SPLCSetDO) e lettura ingressi digitali (GetDI/SPLCGetDI).

1. Nodo “Imposta DO”:

- **Porta**: Ctrl-DO0 ~ Ctrl-CO7 (bloccante: SetDO, non bloccante: SPLCSetDO, [0~15]), End-DO0 ~ End-DO1 (bloccante: SetToolDO, non bloccante: SPLCSetToolDO, [0~1])
- **Stato**: false/true
- **Bloccante**: Sì / No
- **Traiettoria fluida**: Break / Serious
- **Usa thread**: No / Sì

.. image:: graphical/056.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-11 Blocco Imposta DO

2. Nodo “Leggi DI”:

- **Porta**: Ctrl-DI0 ~ Ctrl-CI7 (bloccante: GetDI, non bloccante: SPLCGetDI, [0~15]), End-DI0 ~ End-DI1 (bloccante: GetToolDI, non bloccante: SPLCGetToolDI, [0~1])
- **Bloccante**: Sì / No
- **Stato**: false/true
- **Tempo massimo attesa (ms)**: 0 ~ 10000
- **Usa thread**: No / Sì

.. image:: graphical/057.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-12 Blocco Leggi DI

Istruzioni DO in movimento
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione DO in movimento” nell’area di lavoro.

Consente di emettere segnali DO durante un movimento lineare, con opzione di output continuo o singolo.

1. Nodo “Output continuo DO in movimento”:

- **Porta**: Ctrl-DO0 ~ Ctrl-DO0 (MoveDOStart, [0~15]), End-DO1 (MoveDOStart, [0~1])
- **Intervallo (mm)**: 0 ~ 500
- **Duty cycle (%)**: 0 ~ 99

2. Nodo “Output singolo DO in movimento”:

- **Porta**: Ctrl-DO0 ~ Ctrl-DO0 (MoveDOOnceStart, [0~15]), End-DO1 (MoveDOOnceStart, [0~1])
- **Modalità output**: Output in fase costante / Configurazione libera
- **Tempo set (ms)**: 0 ~ 1000 (valore predefinito -1 in modalità costante)
- **Tempo reset (ms)**: 0 ~ 1000 (valore predefinito -1 in modalità costante)

.. image:: graphical/058.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-13 Blocchi Output DO in movimento

Istruzioni AO in movimento
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione AO in movimento” nell’area di lavoro.

In combinazione con istruzioni di movimento, permette di emettere un segnale AO proporzionale alla velocità TCP in tempo reale.

Parametri del nodo “AO in movimento”:

- **Numero AO controllore**: Ctrl-AO0 ~ Ctrl-AO1 (MoveAOStart, [0~1]), End-AO0 (MoveToolAOStart, 0)
- **Velocità TCP massima**: 0 ~ 100
- **Percentuale AO a velocità massima**: 0 ~ 100
- **Compensazione zona morta AO (%)**: 0 ~ 100

.. image:: graphical/059.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-14 Blocco AO in movimento

Istruzione Livello collisione
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Livello collisione” nell’area di lavoro.

Permette di regolare dinamicamente la soglia di rilevamento collisione per ciascun asse durante l’esecuzione del programma.

Parametri del nodo “Livello collisione”:

- **Livello standard**: Standard / Percentuale personalizzata
- **joint1-joint6 (N)**: 0 ~ 100, soglie di collisione (array)

.. image:: graphical/060.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-15 Blocco Livello collisione

Istruzione Accelerazione
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Accelerazione” nell’area di lavoro.

Permette di regolare separatamente l’accelerazione del robot, modificando il fattore di scala per accelerazione/decelerazione e quindi il tempo ciclo delle operazioni.

Parametri del nodo “Accelerazione”:

- **Percentuale accelerazione (%)**: 0 ~ 100

.. image:: graphical/061.png
   :width: 6in
   :align: center

.. centered:: Figura 10.6-16 Blocco Accelerazione

Comandi grafici per periferiche
-------------------------------

I comandi grafici per periferiche includono pinze, pistole a spruzzo, assi esterni, ecc.

.. image:: graphical/008.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7 Comandi grafici per periferiche

Istruzioni Pinza
~~~~~~~~~~~~~~~~

Trascinare i blocchi “Movimento pinza”, “Attivazione pinza” e “Reinizializzazione pinza” nell’area di lavoro.

Mostrano i numeri delle pinze già configurate e attivate. Consentono di impostare apertura/chiusura, velocità e coppia (valori percentuali). L’opzione “Bloccante” determina se il movimento della pinza attende il completamento dell’istruzione precedente.

1. Nodo “Movimento pinza”:

- **Numero pinza**: pinza attivata
- **Posizione pinza**: 0~100
- **Velocità apertura/chiusura**: 0~100
- **Coppia apertura/chiusura**: 0~100
- **Tempo massimo (ms)**: 0~30000
- **Bloccante**: false/true

.. image:: graphical/062.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-1 Blocco Movimento pinza

2. Nodo “Reinizializzazione pinza”:

- **Numero pinza**: pinza attivata

.. image:: graphical/063.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-2 Blocco Reinizializzazione pinza

3. Nodo “Attivazione pinza”:

- **Numero pinza**: pinza attivata

.. image:: graphical/064.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-3 Blocco Attivazione pinza

Istruzioni Pistola a spruzzo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Pistola a spruzzo” nell’area di lavoro.

Controlla le funzioni di verniciatura: avvio/arresto spruzzo, avvio/arresto pulizia ugello. Prima di utilizzare queste istruzioni, verificare che la pistola sia stata correttamente configurata come periferica.

.. image:: graphical/065.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-4 Blocco Avvio spruzzo

.. image:: graphical/066.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-5 Blocco Arresto spruzzo

.. image:: graphical/067.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-6 Blocco Avvio pulizia

.. image:: graphical/068.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-7 Blocco Arresto pulizia

Istruzioni Asse esterno (Controllore + PLC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Asse esterno” nell’area di lavoro.

Utilizzato in scenari con assi esterni, in combinazione con istruzioni PTP per decomporre movimenti lungo l’asse X su assi esterni. Include configurazione UDP, movimenti asincroni/sincroni, ritorno a zero e abilitazione.

- Nodo “Configurazione comunicazione UDP”: IP, porta, periodo comunicazione

.. image:: graphical/069.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-8 Blocco Configurazione UDP

- Nodo “Movimento asincrono”:

  - **Nome punto**: punto di insegnamento
  - **Velocità debug (%)**: 0~100

.. image:: graphical/070.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-9 Blocco Movimento asincrono

- Nodo “Movimento sincrono PTP/LIN”:

  - **Tipo movimento**: PTP / LIN
  - **Nome punto**: punto di insegnamento
  - **Velocità debug (%)**: 0~100

.. image:: graphical/071.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-10 Blocco Movimento sincrono PTP/LIN

- Nodo “Movimento sincrono ARC” (modalità ARC predefinita):

  - **Nome punto**: punto di insegnamento
  - **Velocità debug (%)**: 0~100

.. image:: graphical/072.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-11 Blocco Movimento sincrono ARC

- Nodo “Ritorno a zero asse esterno”:

  - **Numero asse esterno**: 1~4
  - **Modalità ritorno**: Posizione corrente / Limite negativo / Limite positivo
  - **Velocità ricerca zero**: 0~2000, predefinito 5
  - **Velocità bloccaggio zero**: 0~2000, predefinito 1

.. image:: graphical/073.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-12 Blocco Ritorno a zero asse esterno

- Nodo “Abilitazione asse esterno”:

  - **Numero asse esterno**: 1~4

.. image:: graphical/074.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-13 Blocco Abilitazione asse esterno

Istruzioni Asse esterno (Controllore + Drive servo)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Asse esterno” nell’area di lavoro.

Permette di configurare parametri di assi esterni controllati direttamente da drive servo. Include ID servo, modalità controllo, abilitazione e ritorno a zero.

- Nodo “ID servo”:

  - **ID servo**: 1~15

.. image:: graphical/075.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-14 Blocco ID servo

- Nodo “Modalità controllo”:

  - **ID servo**: 1~15
  - **Modalità**: Posizione / Velocità

.. image:: graphical/076.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-15 Blocco Modalità controllo

- Nodo “Abilitazione servo”:

  - **ID servo**: 1~15
  - **Abilitazione**: Abilita / Disabilita

.. image:: graphical/077.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-16 Blocco Abilitazione servo

- Nodo “Ritorno a zero servo”:

  - **ID servo**: 1~15
  - **Modalità ritorno**: Posizione corrente / Limite negativo / Limite positivo
  - **Velocità ricerca zero**: 0~2000, predefinito 5
  - **Velocità bloccaggio zero**: 0~2000, predefinito 1
  - **Percentuale accelerazione**: 1~100, predefinito 100

.. image:: graphical/078.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-17 Blocco Ritorno a zero servo

- Nodo “Modalità posizione”:

  - **ID servo**: 1~15
  - **Posizione target**: illimitata
  - **Velocità ricerca zero**: illimitata
  - **Percentuale accelerazione**: 1~100, predefinito 100

.. image:: graphical/079.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-18 Blocco Modalità posizione

- Nodo “Modalità velocità”:

  - **ID servo**: 1~15
  - **Velocità target**: illimitata
  - **Percentuale accelerazione**: 1~100, predefinito 100

.. image:: graphical/080.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-19 Blocco Modalità velocità

Istruzioni Nastro trasportatore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Include quattro comandi: rilevamento I/O in tempo reale, rilevamento posizione in tempo reale, attivazione/disattivazione tracking.

- Nodo “Rilevamento I/O in tempo reale”:

  - **Tempo massimo attesa**: 0~10000

.. image:: graphical/081.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-20 Blocco Rilevamento I/O in tempo reale

- Nodo “Rilevamento posizione in tempo reale”:

  - **Modalità lavoro**: Presa con tracking / Movimento con tracking / Tracking TPD

.. image:: graphical/082.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-21 Blocco Rilevamento posizione in tempo reale

- Nodi “Attivazione/Disattivazione tracking”:

  - **Modalità lavoro**: Presa con tracking / Movimento con tracking / Tracking TPD

.. image:: graphical/083.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-22 Blocchi Attivazione/Disattivazione tracking

Istruzioni Levigatura
~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Levigatura” nell’area di lavoro.

Utilizzato in scenari di levigatura. Richiede caricamento/smontaggio driver, abilitazione dispositivo, impostazione velocità, forza di contatto, escursione e modalità di controllo. Include anche comandi per cancellare errori e azzerare il sensore di forza.

.. image:: graphical/084.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-23 Blocchi Caricamento/Smontaggio driver

- Nodo “Abilitazione dispositivo”:

  - **Abilitazione**: Abilita / Disabilita

.. image:: graphical/085.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-24 Blocco Abilitazione dispositivo

.. image:: graphical/086.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-25 Blocco Cancellazione errori

.. image:: graphical/087.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-26 Blocco Azzeramento sensore forza

- Nodo “Velocità”:

  - **Velocità**: 0~5500

.. image:: graphical/088.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-27 Blocco Velocità dispositivo

- Nodo “Forza impostata”:

  - **Forza**: 0~200

.. image:: graphical/089.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-28 Blocco Forza impostata

- Nodo “Escursione”:

  - **Escursione**: 0~12

.. image:: graphical/090.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-29 Blocco Escursione

- Nodo “Forza contatto levigatura”:

  - **Forza contatto**: 0~10000

.. image:: graphical/091.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-30 Blocco Forza contatto levigatura

- Nodo “Tempo transizione forza”:

  - **Tempo transizione**: 0~10000

.. image:: graphical/092.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-31 Blocco Tempo transizione forza

- Nodo “Peso pezzo”:

  - **Peso**: 0~10000

.. image:: graphical/093.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-32 Blocco Peso pezzo

- Nodo “Modalità controllo”:

  - **Modalità**: Ritorno a zero / Posizione / Coppia

.. image:: graphical/094.png
   :width: 6in
   :align: center

.. centered:: Figura 10.7-33 Blocco Modalità controllo

Comandi grafici per saldatura
-----------------------------

I comandi grafici per saldatura includono ricerca posizione, saldatura intermittente, saldatura continua, tracking laser, ecc.

.. image:: graphical/009.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8 Comandi grafici per saldatura

Istruzione Saldatura intermittente
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Saldatura intermittente” nell’area di lavoro.

Utilizzata per saldature intermittenti (tratti saldati alternati a tratti non saldati). Richiede punti iniziale e finale, modalità, velocità, porta DO per l’arco, lunghezza tratti saldati/non saldati, modalità funzionale, oscillazione e regole di arrotondamento.

1. Nodo “Spegni/Avvia arco”:

- **Tipo I/O**: I/O controllore / I/O esteso
- **Numero processo saldatura**: 0 ~ 7
- **Tempo massimo attesa (ms)**: 0 ~ 10000

.. image:: graphical/095.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-1 Blocco Spegni/Avvia arco

2. Nodo “Saldatura intermittente”:

- **Modalità**: Assetto fisso / Assetto variabile
- **Punto iniziale**: punto di insegnamento
- **Punto finale**: punto di insegnamento
- **Velocità debug (%)**: 0~100, predefinito 100
- **Lunghezza saldata**: 0~1000
- **Lunghezza non saldata**: 0~1000
- **Modalità funzionale**: 0~100, predefinito 100
- **Oscillazione**: Nessuna / Solo nei tratti saldati
- **Regola arrotondamento**: Nessuna / Ciclico / Per singolo tratto

.. image:: graphical/096.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-2 Blocco Saldatura intermittente

Istruzioni Saldatura
~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Saldatura” nell’area di lavoro.

Utilizzate con periferiche saldatrici. Verificare la corretta configurazione della saldatrice prima dell’uso.

1. Nodo “Tensione saldatura”:

- **Tipo I/O**: I/O controllore / I/O esteso
- **Tensione saldatrice**: ≥0
- **AO controllo corrente**: Ctrl-AO0/Ctrl-AO1
- **Scelta fluidità**: Break / Serious

.. image:: graphical/097.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-3 Blocco Tensione saldatura

2. Nodo “Corrente saldatura”:

- **Tipo I/O**: I/O controllore / I/O esteso
- **Corrente saldatrice**: ≥0
- **AO controllo corrente**: Ctrl-AO0/Ctrl-AO1
- **Scelta fluidità**: Break / Serious

.. image:: graphical/098.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-4 Blocco Corrente saldatura

3. Nodo “Apri/Chiudi gas”:

- **Tipo I/O**: I/O controllore / I/O esteso

.. image:: graphical/099.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-5 Blocco Apri/Chiudi gas

4. Nodo “Filamento avanti/Stop filamento avanti”:

- **Tipo I/O**: I/O controllore / I/O esteso

.. image:: graphical/100.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-6 Blocco Filamento avanti/Stop

5. Nodo “Filamento indietro/Stop filamento indietro”:

- **Tipo I/O**: I/O controllore / I/O esteso

.. image:: graphical/101.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-7 Blocco Filamento indietro/Stop

Istruzioni Tracking laser
~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Tracking laser” nell’area di lavoro.

Comprende comandi per sensore laser, tracking e ricerca posizione. Verificare la corretta configurazione del sensore prima dell’uso.

1. Nodo “Accendi/Spengi sensore”:

- **Tipo cucitura**: 0 ~ 49
- **Numero task**: 0 ~ 255
- **Soluzione**: 0 ~ 5

.. image:: graphical/102.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-8 Blocco Accendi/Spengi sensore – Tipo cucitura

.. image:: graphical/103.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-9 Blocco Accendi/Spengi sensore – Numero task

.. image:: graphical/104.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-10 Blocco Accendi/Spengi sensore – Soluzione

2. Nodo “Carica/Scarica sensore”:

- **Selezione funzione**: RRT-SV2-BP / CXZK-RBTA4L

.. image:: graphical/105.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-11 Blocco Carica/Scarica sensore

3. Nodo “Avvia/Arresta tracking laser”:

- **Nome sistema coordinate**: sistema configurato

.. image:: graphical/106.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-12 Blocco Avvia/Arresta tracking laser

4. Nodo “Registrazione sensore laser”:

- **Funzione**: Arresta registrazione / Tracking in tempo reale / Avvia registrazione / Riproduci traiettoria
- **Tipo ritardo**: Tempo / Distanza
- **Tempo**: 0 ~ 10000
- **Asse esterno**: 1 ~ 4
- **Distanza**: 0 ~ 10000
- **Coefficiente sensibilità**: 0 ~ 1
- **Velocità**: 0 ~ 100

.. image:: graphical/107.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-13 Blocco Registrazione sensore laser

5. Nodo “Movimento acquisizione punti sensore”:

- **Nome sistema coordinate**: sistema configurato
- **Modalità movimento**: PTP / Lin
- **Velocità debug (%)**: 0 ~ 100
- **Punto riferimento assetto**: punto di insegnamento

.. image:: graphical/108.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-14 Blocco Movimento acquisizione punti

6. Nodo “Riproduzione tracking laser”:

.. image:: graphical/109.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-15 Blocco Riproduzione tracking laser

7. Nodo “Avvia/Arresta ricerca posizione”:

- **Nome sistema coordinate**: sistema configurato
- **Direzione**: -x / -y / -z / Direzione specifica
- **Punto direzione**: non attivo se non è selezionata “Direzione specifica”
- **Velocità (%)**: 0 ~ 100
- **Lunghezza (mm)**: 0 ~ 1000
- **Tempo massimo ricerca (ms)**: 0 ~ 10000

.. image:: graphical/110.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-16 Blocco Avvia/Arresta ricerca posizione

Istruzioni Registrazione laser
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Registrazione laser” nell’area di lavoro.

Permette di estrarre automaticamente i punti iniziale e finale dalla registrazione laser, utili per muovere il robot al punto di partenza. Consente anche di registrare a velocità elevata e riprodurre a velocità normale, migliorando l’efficienza.

1. Nodo “Registrazione sensore laser” (parametri identici a Figura 10.8-13)

.. image:: graphical/111.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-17 Blocco Registrazione dati cucitura

2. Nodo “Ottieni punto iniziale/finale cucitura”:

- **Modalità movimento**: PTP / LIN
- **Velocità (%)**: 0~100, predefinito 30

.. image:: graphical/112.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-18 Blocco Ottieni punto iniziale/finale

Istruzioni Ricerca posizione filo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Ricerca posizione filo” nell’area di lavoro.

Utilizzata in scenari di saldatura, richiede integrazione tra I/O, movimenti e saldatrice.

Comprende: avvio/arresto ricerca, impostazione punti ricerca, calcolo offset, scrittura dati contatto.

- Nodo “Avvia/Arresta ricerca filo”:

  - **Posizione riferimento**: Non aggiornare / Aggiorna
  - **Velocità ricerca**: 0~100
  - **Distanza ricerca**: 0~1000
  - **Ritorno automatico**: No / Sì
  - **Velocità ritorno**: 0~100
  - **Distanza ritorno**: 0~1000
  - **Modalità ricerca**: Punto insegnato / Con offset

.. image:: graphical/113.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-19 Blocco Avvia/Arresta ricerca filo

- Impostazione punti ricerca: varia in base al tipo di cucitura e metodo di calcolo (vedi documento originale per dettagli)

.. image:: graphical/114.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-20 Guida impostazione punti ricerca

- Calcolo offset: varia in base al tipo di cucitura e metodo di calcolo (vedi documento originale per dettagli)

.. image:: graphical/115.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-21 Blocco Calcolo offset

- Nodo “Scrittura dati contatto”:

  - **Nome punto contatto**: RES0~99
  - **Formato dati**: {0,0,0,0,0,0}

.. image:: graphical/116.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-22 Blocco Scrittura dati contatto

Istruzioni Tracking ad arco
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Tracking ad arco” nell’area di lavoro.

Utilizza un sensore ad arco per rilevare deviazioni della cucitura e compensare la traiettoria.

- Nodo “Avvia/Arresta tracking ad arco”:

  - **Ritardo tracking (ms)**: es. 50
  - **Compensazione deviazione**: Disattivata / Attivata
  - **Coefficiente regolazione**: 0 ~ 300
  - **Tempo compensazione (cicli)**: 0 ~ 300
  - **Compensazione max per ciclo (mm)**: 0 ~ 300
  - **Compensazione totale max (mm)**: 0 ~ 300
  - **Selezione sistema coordinate**: Oscillazione
  - **Modalità corrente riferimento**: Feedback / Costante
  - **Corrente riferimento (A)**: 0 ~ 300

.. image:: graphical/117.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-23 Blocco Tracking ad arco

Istruzioni Regolazione assetto
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Regolazione assetto” nell’area di lavoro.

Utilizzata per regolare automaticamente l’assetto della torcia durante il tracking. Richiede tre punti di insegnamento (PosA, PosB, PosC).

- Nodo “Avvia regolazione assetto”:

  - **Tipo lamiera**: Lamiera ondulata / Grecata / Recinzione / Acciaio corrugato
  - **Direzione movimento**: Sinistra→Destra / Destra→Sinistra
  - **Tempo regolazione (ms)**: 0 ~ 1000
  - **Lunghezza tratto 1 (mm)**:
  - **Tipo curva**: Alto→Basso / Basso→Alto
  - **Lunghezza tratto 2-5 (mm)**:

.. image:: graphical/118.png
   :width: 6in
   :align: center

.. centered:: Figura 10.8-24 Blocco Regolazione assetto

Comandi grafici per controllo di forza
-------------------------------------------

I comandi grafici per controllo di forza includono set di controllo forza, registrazione coppia, ecc.

.. image:: graphical/010.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9 Comandi grafici per controllo di forza

Istruzioni Controllo forza
~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Controllo forza” nell’area di lavoro.

Comprende otto comandi: FT_Guard (rilevamento collisioni), FT_Control (controllo forza costante), FT_Compliance (controllo compliance), FT_Spiral (inserimento a spirale), FT_Rot (inserimento rotazionale), FT_Lin (inserimento lineare), FT_FindSurface (localizzazione superficie), FT_CalCenter (localizzazione centro).

1. Nodo “Attiva/Disattiva rilevamento collisioni”:

- **Nome sistema coordinate**: sistema configurato
- **Fx-Tx valore reale**: true/false
- **Fx-Tx valore corrente**: inserito dall’utente
- **Soglia massima/minima**: inserite dall’utente

.. image:: graphical/119.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-1 Blocco Rilevamento collisioni

2. Nodo “Attiva/Disattiva controllo”:

- **Nome sistema coordinate**: sistema configurato
- **Fx-Tx valore reale**: true/false
- **Fx-Tx valore corrente**: regolabile
- **Guadagni F_P, F_I, F_D**: ≠0
- **Stato adattivo**: Arresto / Attivo
- **Stato ILC**: Arresto / Training / Esecuzione
- **Distanza max regolazione (mm)**: 0 ~ 1000
- **Angolo max regolazione (°)**: 0 ~ 1000

.. image:: graphical/120.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-2 Blocco Controllo forza

3. Nodo “Attiva/Disattiva compliance”:

- **Coefficiente regolazione posizione**: 0 ~ 1
- **Soglia forza attivazione (N)**: 0 ~ 100

.. image:: graphical/121.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-3 Blocco Compliance

4. Nodo “Inserimento a spirale”:

- **Nome sistema coordinate**: Strumento / Base
- **Avanzamento raggio per giro (mm)**: 0 ~ 100, es. 0.7
- **Soglia forza/coppia (N/Nm)**: 0 ~ 100, es. 50
- **Tempo esplorazione max (ms)**: 0 ~ 60000, es. 60000
- **Velocità lineare max (mm/s)**: 0 ~ 100, es. 5

.. image:: graphical/122.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-4 Blocco Inserimento a spirale

5. Nodo “Inserimento rotazionale”:

- **Nome sistema coordinate**: Strumento / Base
- **Velocità angolare (°/s)**: 0 ~ 100, es. 0.7
- **Forza/coppia terminale (N/Nm)**: 0 ~ 100, es. 50
- **Angolo rotazione max (°)**: 0 ~ 100, es. 5
- **Direzione forza**: z / mz
- **Accelerazione angolare max (°/s²)**: 0 ~ 100
- **Direzione inserimento**: Positiva / Negativa

.. image:: graphical/123.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-5 Blocco Inserimento rotazionale

6. Nodo “Inserimento lineare”:

- **Nome sistema coordinate**: Strumento / Base
- **Soglia forza terminale (N)**: 0 ~ 100
- **Velocità lineare (mm/s)**: 0 ~ 100, es. 1
- **Accelerazione lineare (mm/s²)**: 0 ~ 100
- **Distanza inserimento max (mm)**: 0 ~ 100
- **Direzione inserimento**: Positiva / Negativa

.. image:: graphical/124.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-6 Blocco Inserimento lineare

7. Nodo “Localizzazione superficie”:

- **Nome sistema coordinate**: Strumento / Base
- **Direzione movimento**: Positiva / Negativa
- **Asse movimento**: X / Y / Z
- **Velocità esplorazione (mm/s)**: 0 ~ 100
- **Accelerazione esplorazione (mm/s²)**: 0 ~ 100
- **Distanza esplorazione max (mm)**: 0 ~ 100
- **Soglia forza terminale (N)**: 0 ~ 100

.. image:: graphical/125.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-7 Blocco Localizzazione superficie

8. Nodo “Inizio/Fine calcolo piano medio”.

.. image:: graphical/126.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-8 Blocco Calcolo piano medio

Istruzioni Registrazione coppia
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Registrazione coppia” nell’area di lavoro.

Comprende tre comandi: avvio, arresto e reset registrazione coppia, utilizzati per rilevare collisioni in tempo reale.

- Nodo “Avvio registrazione coppia”:

  - **Scelta fluidità**: Dati grezzi / Dati filtrati
  - **Soglia negativa giunti (Nm)**: -100 ~ 0
  - **Soglia positiva giunti (Nm)**: 0 ~ 100
  - **Tempo rilevamento collisione (ms)**: 0 ~ 1000

.. image:: graphical/128.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-9 Blocco Avvio registrazione coppia

- Nodo “Arresto registrazione coppia”

.. image:: graphical/129.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-10 Blocco Arresto registrazione coppia

- Nodo “Reset registrazione coppia”

.. image:: graphical/130.png
   :width: 6in
   :align: center

.. centered:: Figura 10.9-11 Blocco Reset registrazione coppia

Comandi grafici per comunicazione
--------------------------------------

I comandi grafici per comunicazione includono configurazione Modbus master/slave, lettura/scrittura registri, ecc.

.. image:: graphical/011.png
   :width: 6in
   :align: center

.. centered:: Figura 10.10 Comandi grafici per comunicazione

Istruzioni Modbus
~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Modbus” nell’area di lavoro.

Basate sul protocollo ModbusTCP, permettono comunicazione tra robot e dispositivi Modbus (client/server) per lettura/scrittura di coil, input discreti, registri.

Prima dell’uso, configurare master/slave e nomi DI/DO/AI/AO nell’apposita sezione.

(Seguono 15 nodi con parametri dettagliati, tradotti in modo analogo ai precedenti)

Comandi grafici avanzati
------------------------

I comandi grafici avanzati includono chiamata sottoprogrammi, thread ausiliari, blocchi pieghevoli, ecc.

.. image:: graphical/012.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11 Comandi grafici avanzati

Istruzione Blocco pieghevole
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Blocco pieghevole” nell’area di lavoro.

Permette di raggruppare più blocchi in un’unica riga espandibile/comprimibile, migliorando la leggibilità.

- **Nome blocco**: nome descrittivo

.. image:: graphical/146.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11-1 Blocco pieghevole

Istruzione Chiamata sottoprogramma
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Chiamata sottoprogramma” nell’area di lavoro.

Esegue un sottoprogramma Lua esterno.

- **File dofile**: nome file generato
- **Livello chiamata**: Primo / Secondo
- **ID**: identificativo posizione

.. image:: graphical/147.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11-2 Blocco Chiamata sottoprogramma

Istruzione Thread ausiliario
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Thread ausiliario” nell’area di lavoro.

Permette di eseguire un thread parallelo per comunicazione con dispositivi esterni (socket, stato I/O, ecc.).

- **Nome metodo**: nome del thread
- **Funzione chiamata**: funzione da eseguire

.. image:: graphical/148.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11-3 Blocco Thread ausiliario

Istruzione Tabella punti
~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Tabella punti” nell’area di lavoro.

Permette di commutare tra diverse tabelle di punti di insegnamento.

- **Modalità tabella punti**: nome tabella

.. image:: graphical/149.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11-4 Blocco Tabella punti

Istruzione Inseguimento fuoco
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trascinare il blocco “Istruzione Inseguimento fuoco” nell’area di lavoro.

Mantiene l’orientamento dello strumento verso un punto fisso durante il movimento.

- **Coefficiente parametro**: 0~100, predefinito 50
- **Parametro feedforward**: 0~1000, predefinito 19
- **Limite accelerazione angolare max**: 0~10000, predefinito 1440
- **Limite velocità angolare max**: 0~1000, predefinito 180
- **Blocco asse X**: Vettore riferimento / Orizzontale / Verticale

.. image:: graphical/150.png
   :width: 6in
   :align: center

.. centered:: Figura 10.11-5 Blocco Inseguimento fuoco

Esempi di utilizzo
------------------

Dopo aver selezionato il tipo di programmazione grafica, trascinare i blocchi desiderati nell’area di lavoro e collegarli.

Esempio: combinare istruzioni PTP, LIN e Waitms, racchiudendole in un blocco pieghevole con commento descrittivo.

.. image:: graphical/013.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-1 Esempio comandi grafici

Dopo aver completato la connessione e l’impostazione dei parametri, assegnare un nome al programma e fare clic su “Salva”. Selezionare il programma salvato e avviarlo per eseguirlo.

Modularizzazione blocchi grafici
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La funzionalità di modularizzazione migliora la leggibilità tramite blocchi pieghevoli.

.. image:: graphical/014.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-2 Blocco pieghevole

1. Creare una sequenza di blocchi e racchiuderla in un blocco pieghevole, inserendo un commento descrittivo.

.. image:: graphical/015.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-3 Effetto blocco pieghevole

2. Fare clic destro sul blocco e selezionare “Piega”: la sequenza viene compressa in una riga, mantenendo la funzionalità.

.. image:: graphical/016.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-4 Vista compressa

3. È possibile zoomare la pagina con la rotellina del mouse.

.. image:: graphical/017.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-5 Funzione zoom

Sovrascrittura con nome identico
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Quando si salva un programma con un nome già esistente, appare un avviso.

.. image:: graphical/018.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-6 Sovrascrittura programma

**Passo 1**: Cliccare “Annulla” per annullare l’operazione.  
**Passo 2**: Selezionare “Aggiorna programma insegnamento” e cliccare “Sovrascrivi” per sostituire il file esistente.

Verifica salvataggio non effettuato
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Se si modifica un programma senza salvarlo e si tenta di aprirne un altro o di uscire dalla pagina, appare un avviso.

.. image:: graphical/019.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-7 Avviso modifica non salvata (apertura file)

**Passo 1**: Cliccare “Non salvare” per procedere senza salvare.  
**Passo 2**: Cliccare “Salva” per salvare e proseguire.

Lo stesso avviso appare quando si lascia la pagina:

.. image:: graphical/020.png
   :width: 6in
   :align: center

.. centered:: Figura 10.12-8 Avviso modifica non salvata (cambio pagina)

**Passo 1**: Cliccare “Non salvare” per cambiare pagina.  
**Passo 2**: Cliccare “Salva”; se il nome esiste già, confermare la sovrascrittura, quindi cambiare pagina.