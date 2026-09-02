Sicurezza
===============

.. toctree:: 
   :maxdepth: 6

Contesto
------------------------------------------------
In quanto unità esecutiva chiave nello sviluppo della produzione intelligente industriale, le prestazioni di sicurezza dei robot industriali sono diventate un elemento centrale nella gestione dell'intero ciclo di vita delle apparecchiature. Attualmente, il settore richiede generalmente che i parametri relativi alle funzioni di sicurezza siano fissi e non modificabili, e che venga stabilito un meccanismo di verifica completo e tracciabile per soddisfare i rigorosi requisiti di audit di conformità della sicurezza.
Gli integratori di sistema e gli utenti finali in Europa hanno ulteriormente richiesto trasparenza e verificabilità della configurazione di sicurezza durante l'accettazione effettiva dei progetti. Nello specifico, dopo il completamento del debug delle funzioni di sicurezza, il sistema dovrebbe essere in grado di generare automaticamente un rapporto di configurazione di sicurezza contenente un checksum di integrità, e questo checksum deve essere visualizzato in tempo reale nell'interfaccia di gestione Web del dispositivo. Questo meccanismo mira a garantire che qualsiasi modifica ai parametri di sicurezza possa essere efficacemente identificata e registrata, fornendo così una base affidabile per la valutazione dello stato di sicurezza del dispositivo, l'accettazione in loco e la successiva manutenzione.
In considerazione di ciò, il progetto dell'architettura di sicurezza di questo dispositivo non solo è conforme agli standard di sicurezza internazionali pertinenti, ma include anche funzioni integrate di esportazione della configurazione di sicurezza e visualizzazione in tempo reale del checksum, per assistere gli operatori e i responsabili della sicurezza nel completare in modo conveniente e affidabile la conferma della configurazione e la certificazione di conformità.

Checksum della Configurazione di Sicurezza
------------------------------------------------

Aprire la pagina web. Il checksum di sicurezza si trova nell'angolo in alto a destra della pagina, rappresentato da un numero esadecimale a 8 cifre. Il checksum di sicurezza è unico; quando i parametri di configurazione di sicurezza cambiano, il checksum di sicurezza cambia di conseguenza.

.. image:: safety/001.png
   :width: 4in
   :align: center

.. centered:: Figura 7.1-1 Visualizzazione del Checksum della Configurazione di Sicurezza

Fare clic sul checksum di sicurezza per visualizzare l'insieme dei parametri di configurazione di sicurezza rappresentati dal checksum corrente.

.. image:: safety/002.png
   :width: 6in
   :align: center

.. centered:: Figura 7.1-2 Parametri di Configurazione di Sicurezza

I parametri di configurazione di sicurezza supportano l'esportazione di report PDF. Fare clic su Download per visualizzare l'anteprima del report PDF, e supporta anche l'esportazione. Fare clic sul pulsante Salva per scaricare il report PDF.

.. image:: safety/003.png
   :width: 6in
   :align: center

.. centered:: Figura 7.1-3 Anteprima PDF del Report di Configurazione di Sicurezza

Gestione dei Parametri di Configurazione di Sicurezza
------------------------------------------------

Tutti i parametri di configurazione di sicurezza relativi al robot sono gestiti uniformemente nella pagina web "Impostazioni Iniziali" -> "Sicurezza". La modifica dei parametri di configurazione di sicurezza richiede prima l'inserimento della "Password di Configurazione di Sicurezza" per la verifica. Solo dopo una verifica riuscita è possibile procedere con le modifiche alla configurazione dei parametri di sicurezza.

.. image:: safety/004.png
   :width: 4in
   :align: center

.. centered:: Figura 7.2-1 Verifica della Password di Configurazione di Sicurezza

Dopo aver modificato i parametri di configurazione di sicurezza, fare clic su "Applica". È richiesta una seconda conferma dei parametri di configurazione di sicurezza modificati. Fare clic su "Conferma" per applicare i parametri. Dopo l'applicazione riuscita dei parametri, il checksum di configurazione di sicurezza verrà aggiornato di conseguenza.

.. image:: safety/005.png
   :width: 6in
   :align: center

.. centered:: Figura 7.2-2 Seconda Conferma dei Parametri di Configurazione di Sicurezza

Gestione della Password di Configurazione di Sicurezza
------------------------------------------------

La password di configurazione di sicurezza può essere modificata in "Impostazioni di Sistema" -> "Modalità Manutenzione" -> "Configurazione Parametri di Sicurezza". La password predefinita è 12345678. La modifica della password richiede la verifica della vecchia password. La nuova e la vecchia password non possono essere uguali. La lunghezza della password è minima 1 carattere e massima 8 caratteri, e distingue tra lettere maiuscole e minuscole e simboli.

.. image:: safety/006.png
   :width: 4in
   :align: center

.. centered:: Figura 7.3-1 Gestione della Password di Configurazione di Sicurezza

Se si dimentica la vecchia password, contattare il personale tecnico competente di FAIRINO.

Parametri di Configurazione di Sicurezza
--------------------------------------------------------------------------------------------------

Parametri di Sicurezza del Robot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Velocità del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Velocità del Robot" per accedere all'interfaccia di configurazione.

La velocità del robot viene utilizzata per limitare la velocità lineare massima, l'accelerazione lineare e l'accelerazione angolare dei giunti del robot.

.. image:: safety/007.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-1 Velocità del Robot
 
Pianificazione della Decelerazione di Arresto
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Pianificazione della Decelerazione di Arresto" per accedere all'interfaccia di configurazione.

- Arresto Libero: quando si entra in arresto, la velocità angolare di ciascun asse decelera e si arresta secondo la percentuale di decelerazione di arresto impostata moltiplicata per l'accelerazione massima del giunto;
- Arresto Sincronizzato: quando si entra in arresto, la velocità di posa TCP decelera e si arresta secondo la percentuale di decelerazione di arresto impostata moltiplicata per l'accelerazione massima di posa;

La decelerazione di arresto è una percentuale dell'accelerazione.

.. image:: safety/008.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-2 Pianificazione della Decelerazione di Arresto del Robot

Arresto di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic su "Arresto di Sicurezza" per accedere all'interfaccia di configurazione per impostare la modalità di arresto di sicurezza e i parametri della strategia di arresto di sicurezza.

Quando la modalità di attivazione dell'arresto di sicurezza è impostata su "Doppio Canale", entrambi i canali devono essere puliti e l'avviso deve essere cancellato manualmente sull'interfaccia operativa prima che il robot possa essere resettato. Inoltre, è stata aggiunta un'opzione di modalità ridotta nella configurazione della strategia. Quando l'utente seleziona questa strategia, il robot entrerà in movimento in modalità ridotta.

**Passo 1**: Fare clic su "Impostazioni Iniziali" -> "Sicurezza" -> "Arresto di Sicurezza". La modalità di attivazione può essere selezionata come "Predefinita" o "Doppio Canale". La differenza tra le due è: in modalità "Predefinita", l'errore dell'interfaccia viene automaticamente cancellato dopo l'attivazione e il ripristino; in modalità "Doppio Canale", l'errore dell'interfaccia deve essere cancellato manualmente dopo l'attivazione e il ripristino. "Strategia di Arresto di Sicurezza" può essere selezionata come "Arresto", "Pausa", "Modalità Ridotta di Livello 1" e "Modalità Ridotta di Livello 2". Le descrizioni dettagliate sono le seguenti: quando è selezionato "Arresto", il robot interromperà il movimento corrente; quando è selezionato "Pausa", il robot metterà in pausa il movimento corrente e, dopo il ripristino e la cancellazione dell'errore, riprenderà la pausa; quando è selezionato "Modalità Ridotta di Livello 1", il robot entrerà in movimento in modalità ridotta di livello 1; quando è selezionato "Modalità Ridotta di Livello 2", il robot entrerà in movimento in modalità ridotta di livello 2.

.. image:: safety/009.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-3 Pianificazione della Decelerazione di Arresto del Robot

**Passo 2**: Quando la modalità di attivazione è impostata su "Predefinita", l'errore dell'interfaccia può essere automaticamente cancellato dopo il ripristino dell'attivazione. Quando la modalità di attivazione è impostata su "Doppio Canale", l'operazione è: dopo il ripristino dell'attivazione, fare clic manualmente sull'operazione "Cancella" nell'angolo in alto a destra per resettare il robot.

Velocità di Sicurezza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic su "Velocità di Sicurezza" per accedere all'interfaccia di configurazione per impostare la velocità di sicurezza. L'intervallo di velocità manuale TCP è 1-1500mm/s.

La funzione di velocità di sicurezza del robot viene utilizzata in ambienti collaborativi uomo-robot o dinamici per limitare attivamente la velocità operativa del robot, controllando l'energia cinetica e la forza d'impatto entro soglie di sicurezza, prevenendo così lesioni al personale in caso di contatto accidentale e proteggendo efficacemente le apparecchiature e i pezzi da danni da collisione.

**Passo 1**: Fare clic su "Impostazioni Iniziali" -> "Sicurezza" -> "Velocità di Sicurezza" per impostare i parametri di velocità di sicurezza, principalmente tre parti: "Abilitazione Funzione", "Limite di Velocità" e "Modalità Post-Superamento Velocità".

Tra questi, Abilitazione Funzione può essere selezionata come "Disabilita", "Abilita in Modalità Manuale" e "Abilita in Tutte le Modalità";

In Limite di Velocità, impostare il limite di velocità. Quando la velocità lineare del robot raggiunge questo limite, verrà elaborata secondo i parametri impostati in "Modalità Post-Superamento Velocità". "Modalità Post-Superamento Velocità" può essere selezionata come "Stop e Allarme", "Limitazione Automatica Velocità" e "Disabilita Dopo Stop e Allarme". La limitazione automatica della velocità è disponibile solo in "Abilita in Modalità Manuale".

Dopo aver impostato i parametri richiesti, non sono necessarie ulteriori operazioni. Il movimento del robot verrà elaborato secondo i parametri impostati. Le impostazioni dei parametri sono mostrate in figura.

.. image:: safety/010.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-4 Impostazioni dei Parametri di Velocità di Sicurezza

Arresto di Emergenza
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic su "Arresto di Emergenza" per accedere all'interfaccia di configurazione.

I tipi di arresto di emergenza 0, 1a, 1b, 2 possono essere impostati, il limite di tempo di arresto può essere impostato e il limite di distanza di arresto può essere impostato.

Attraverso il controller che invia alla scheda del box di controllo, l'arresto di emergenza di tipo 0 interrompe direttamente l'alimentazione della scheda del box di controllo;

- Arresto di emergenza di tipo 1a: dopo l'arresto con decelerazione, interrompe l'alimentazione del corpo del robot;
- Arresto di emergenza di tipo 1b: dopo l'arresto con decelerazione, non interrompe l'alimentazione del corpo del robot, ma disabilita il corpo del robot;
- Arresto di emergenza di tipo 2: quando viene premuto l'arresto di emergenza, il robot decelera fino all'arresto e rimane abilitato. Dopo il rilascio dell'arresto di emergenza, il robot dovrebbe essere in grado di funzionare normalmente.

.. image:: safety/011.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-5 Impostazioni dell'Arresto di Emergenza

Arresto Protettivo
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Arresto Protettivo" per accedere all'interfaccia di configurazione.

Tipi di arresto protettivo 0, 1, 2. L'arresto protettivo di tipo 0 interrompe direttamente l'alimentazione della scheda del box di controllo. L'arresto protettivo di tipo 1: la scheda del box di controllo prima notifica al controller di controllare l'arresto del robot, quindi il controller fornisce un feedback alla scheda del box di controllo per interrompere l'alimentazione. L'arresto protettivo di tipo 2: la scheda del box di controllo notifica al controller di controllare l'arresto del robot.

.. image:: safety/012.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-6 Configurazione dell'Arresto Protettivo

Abilitazione Automatica all'Accensione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Abilitazione Robot" per accedere all'interfaccia di configurazione. È possibile scegliere se il robot si abilita automaticamente all'accensione o meno.

.. image:: safety/013.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-7 Abilitazione Automatica all'Accensione

Limite di Orientamento dell'Utensile (Utilizzato solo nel sistema LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Limite di Orientamento dell'Utensile" per accedere all'interfaccia di configurazione.

Il limite di orientamento dell'utensile è una funzione protettiva che agisce sullo spazio cartesiano dell'estremità utensile del robot per limitare l'intervallo di movimento della postura dell'estremità del robot, includendo l'impostazione di abilitazione della funzione, l'impostazione della direzione di riferimento dell'utensile e l'impostazione dell'angolo di deviazione massimo. L'angolo di deviazione massimo definisce il valore limite angolare massimo tra l'asse Z del sistema di coordinate cartesiano dell'estremità utensile e la direzione di riferimento dell'utensile, che di solito può essere inteso come uno spazio conico.

.. image:: safety/014.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-8 Limite di Orientamento dell'Utensile

Limiti del Robot (Utilizzato solo nel sistema LA)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Limiti del Robot" per accedere all'interfaccia di configurazione.

I limiti del robot includono quantità di moto e potenza, dove il limite di quantità di moto viene utilizzato per limitare la quantità di moto massima del robot, e il limite di potenza viene utilizzato per limitare il lavoro meccanico svolto dal robot.

.. image:: safety/015.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-9 Limiti del Robot

Giunti
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Limiti Morbidi dei Giunti
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Sotto la barra del menu "Impostazioni Iniziali" -> "Sicurezza" -> "Giunti", fare clic su "Limiti Morbidi dei Giunti" per accedere all'interfaccia dei limiti morbidi.

Potrebbero esserci altre apparecchiature all'interno dell'intervallo di movimento del robot. Gli angoli di limite possono eseguire una limitazione morbida sul robot, impedendo al robot di muoversi oltre determinati valori di coordinate ed evitando collisioni. L'attivazione di un limite morbido fa sì che il robot si arresti automaticamente, senza distanza di arresto.

Gli amministratori possono utilizzare valori predefiniti o inserire valori angolari. Inserendo valori angolari, gli angoli positivi e negativi dei giunti del robot possono essere limitati separatamente. Quando il valore inserito supera i valori angolari limite morbidi dei giunti del robot elencati nella tabella dei parametri di base del robot nella Sezione 2.1-Parametri di Base, l'angolo limite verrà regolato al valore massimo impostabile. Quando il robot segnala un errore di superamento del limite del comando del giunto, è necessario entrare in modalità di trascinamento e trascinare il giunto del robot entro l'angolo limite.

La funzione di protezione dei limiti morbidi dei giunti è un meccanismo di protezione attiva che monitora in tempo reale lo stato di movimento dei giunti del braccio robotico e limita dinamicamente l'operatore dal superare l'intervallo di limiti morbidi impostato durante l'insegnamento per trascinamento. Questa funzione rende i limiti morbidi significativi anche nell'insegnamento per trascinamento, migliorando così la sicurezza della collaborazione uomo-robot.

- **Passo 1**: Accedere all'interfaccia web e fare clic su "Impostazioni Iniziali" -> "Sicurezza" -> "Giunti" -> "Limiti Morbidi dei Giunti" in sequenza per accedere al modulo di impostazione dei limiti morbidi del robot.
- **Passo 2**: In base all'effettivo intervallo di lavoro del robot, impostare ragionevolmente i limiti morbidi per ciascun giunto. A questo punto, verificare se la posizione angolare corrente di ciascun giunto del robot è all'interno dell'intervallo di limiti morbidi preimpostato. Se sì, fare clic su "Applica" per inviare i limiti morbidi preimpostati. In caso contrario, spostare ciascun giunto all'interno dell'intervallo preimpostato; altrimenti, quando si fa clic su "Applica", verrà visualizzato un prompt di superamento limite, come mostrato nella figura sottostante. A questo punto, è possibile jog o trascinare il giunto in eccesso nella direzione verso l'intervallo di limiti morbidi per cancellare l'errore.
- **Passo 3**: Dopo che l'intervallo di limiti morbidi è stato impostato con successo, selezionare "Abilita" per "Protezione Limiti Morbidi dei Giunti" per attivare questa funzione, come mostrato nella figura sottostante. In modalità di trascinamento, i limiti morbidi impostati avranno effetto e si sentirà resistenza quando si trascina vicino ai limiti morbidi.
- **Passo 4**: Per disabilitare la funzione di protezione dei limiti morbidi dei giunti, fare clic su "Protezione Limiti Morbidi dei Giunti" per disattivarla.

.. image:: safety/016.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-10 Limiti Morbidi dei Giunti

Livello di Collisione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Sotto la barra del menu "Impostazioni Iniziali" -> "Sicurezza" -> "Giunti", fare clic su "Livello di Collisione" per accedere all'interfaccia del livello di collisione.
I livelli di collisione sono suddivisi da 1 a 10. I livelli da 1 a 3 sono più sensibili e il robot deve funzionare alla velocità consigliata. È anche possibile scegliere impostazioni percentuali personalizzate, con il 100% corrispondente al livello 10. Come mostrato nella figura sottostante:

.. image:: safety/017.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-11 Diagramma del Livello di Collisione

Le strategie di collisione sono "Arresto in Collisione", "Pausa in Collisione" e "Continua Movimento". Per evitare forze di schiacciamento tra il robot e gli oggetti dopo la collisione, sono state aggiunte le strategie "Modalità Coppia di Gravità", "Modalità Risposta Oscillante" e "Modalità Rimbalzo da Collisione". Quando vengono attivate, tutte e tre le strategie passeranno dalla modalità automatica o manuale alla modalità di trascinamento, e poi torneranno alla modalità manuale. La modalità coppia di gravità si allontanerà dal punto di collisione in base all'entità e alla direzione della forza di collisione; la modalità risposta oscillante tornerà alla posizione di collisione dopo essersi allontanata; la modalità rimbalzo da collisione accelererà lontano dal punto di collisione secondo i parametri impostati.

Nella sezione "Strategia di Collisione", fare clic sul menu a tendina per selezionare "Modalità Rimbalzo da Collisione" e impostare il tempo di sicurezza a 1000ms, la distanza di sicurezza a 150mm, la velocità di sicurezza a 150mm/s e il fattore di sicurezza per ciascun giunto a 5. L'interfaccia specifica è mostrata nella figura sottostante.

.. image:: safety/018.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-12 Strategia di Collisione: Modalità Rimbalzo da Collisione

Significato di ciascun parametro:

- Tempo di Sicurezza: Indica la durata in modalità di trascinamento dopo il passaggio dalla modalità automatica alla modalità di trascinamento, intervallo [1000-2000]ms;
- Distanza di Sicurezza: Indica la posizione in cui il robot si allontana dal punto di collisione dopo la collisione, intervallo [150-200]mm;
- Velocità di Sicurezza: Indica la velocità TCP massima con cui il robot si allontana dal punto di collisione dopo la collisione. Il superamento di questo limite di velocità limiterà la forza di rimbalzo, intervallo [50-250]mm/s;
- Fattore di Sicurezza: Indica il tasso di decadimento della forza di rimbalzo. Minore è il coefficiente, più veloce è il decadimento e più veloce è la velocità di rimbalzo; maggiore è il coefficiente, più lento è il decadimento. Intervallo [1-10], adimensionale.
- Prima che il robot entri in modalità di trascinamento, è richiesto il rilevamento della coppia. Questa funzione è progettata per prevenire fenomeni anomali come il sollevamento o l'abbassamento dopo che il robot entra in modalità di trascinamento a causa di parametri di carico errati o impostazioni di modalità di installazione errate da parte dell'operatore. Se la coppia del giunto viene rilevata al di fuori dell'intervallo consentito, il controller segnalerà immediatamente un errore e proibirà al robot di entrare in modalità di trascinamento.

Passaggi per abilitare la funzione di rilevamento collisione per la guida a cremagliera lineare:

- Passo 1: Assicurarsi che sia la guida che il robot siano installati frontalmente. Prima di abilitare la funzione di rilevamento collisione per la guida a cremagliera lineare, verificare che il metodo di installazione sia frontale. Nello specifico, assicurarsi prima che la guida e il robot siano installati frontalmente. Quindi, fare clic su "Impostazioni Iniziali" -> "Base" -> "Installazione" in sequenza per accedere alla pagina di installazione libera. Se sia "Rotazione Base" che "Inclinazione Base" sono 0, il software è impostato su frontale; altrimenti, devono essere modificati a 0. Se non sono 0, l'interfaccia segnalerà un errore.
- Passo 2: Abilitare la funzione di rilevamento collisione per la guida a cremagliera lineare e impostare i parametri. Fare clic su "Impostazioni Iniziali" -> "Sicurezza" -> "Giunti" -> "Livello di Collisione" in sequenza per accedere alla pagina di impostazione del livello di collisione. Dopo aver fatto clic sul cursore della funzione "Rilevamento Collisione Guida a Cremagliera Lineare", impostare il raggio dell'ingranaggio e la massa del cursore. Il raggio dell'ingranaggio può essere calcolato dalla guida e dal rapporto di riduzione. La massa del cursore non include il robot e il suo carico all'estremità. Ci sono 11 opzioni di livello della guida, dove il Livello 1 è il più facile da attivare la collisione e il Livello 10 è il più difficile. Quando il controller viene acceso per la prima volta e prima che venga eseguito il programma di adattamento, il livello di collisione deve prima essere impostato su "Disabilitato".

.. image:: safety/019.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-13 Funzione di Rilevamento Collisione per Guida a Cremagliera Lineare

- Passo 3: Eseguire il programma "Rail_Adaptation_Program.lua" per adattarsi alla guida corrente. Dopo ogni riavvio del controller, il programma "Rail_Adaptation_Program.lua" deve essere eseguito (per evitare che cambiamenti nel tipo di robot e altri fattori influenzino le caratteristiche dinamiche della guida). Prima di eseguire il programma, assicurarsi che il livello di collisione della guida sia impostato su "Disabilitato". In modalità automatica, eseguire il programma LUA al 100% della velocità dell'interfaccia. Dopo un ciclo del programma, l'adattamento è completo e l'esecuzione può essere interrotta.

.. image:: safety/020.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-14 Eseguire "Rail_Adaptation_Program.lua" per Adattarsi alla Guida Corrente

- Passo 4: Impostare ragionevolmente il livello di collisione della guida ed eseguire le attività. Gli utenti possono impostare ragionevolmente il livello di collisione della guida in base alle prestazioni del driver del motore e alla velocità di esecuzione dell'attività. Se la guida e il robot operano in modo asincrono, la collisione con il robot o la guida può attivare un "guasto di collisione a 8 assi, ripristinabile". In questo caso, la guida smette di funzionare, come mostrato nella Figura 2-9. Se la guida e il robot operano in modo sincrono, la collisione con il robot può attivare un allarme, causando l'arresto della guida, mentre il robot reagisce secondo la strategia di collisione impostata.

Modalità Ridotta
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Modalità Ridotta" per accedere all'interfaccia di configurazione. Selezionare "Modalità di Livello 1/Livello 2" per configurare la velocità dei giunti e la velocità TCP dell'estremità.

.. image:: safety/021.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-15 Modalità Ridotta

I/O
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "I/O" per accedere all'interfaccia di configurazione.

HMI fornisce la possibilità di impostare lo stato di sicurezza per 16 ingressi digitali e 16 uscite digitali, che possono essere impostati su stati validi o non validi. Quando il controller determina di trovarsi in uno stato di sicurezza, i 16 ingressi digitali e le 16 uscite digitali vengono impostati sullo stato di sicurezza.

.. image:: safety/022.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-16 Configurazione dello Stato di Sicurezza I/O

Sotto il sistema LA:

"I/O Sicurezza" fornisce funzioni di sicurezza DIO. La funzione di sicurezza è DI o DO a doppio canale. Quando viene attivato un segnale DI di sicurezza o un flag di stato di sicurezza, viene emesso il DO.

.. image:: safety/023.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-17 Configurazione delle Funzioni di Sicurezza I/O

Hardware
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Rilevamento Potenza ServoJT (Utilizzato solo nel sistema QX)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Rilevamento Potenza" per accedere all'interfaccia di configurazione.

Quando si agisce direttamente sul circuito di corrente del robot (solo servoJT), viene utilizzato per limitare il lavoro svolto dal robot. Quando viene rilevato che l'integrale della velocità e della coppia del robot supera il limite, viene attivata la protezione di potenza.

.. image:: safety/024.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-18 Rilevamento Potenza ServoJT

Piani
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Muro di Sicurezza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Fare clic sulla barra del menu "Impostazioni Iniziali" -> "Sicurezza", e fare clic sul sottomenu "Configurazione Muro di Sicurezza" per accedere all'interfaccia di configurazione.

- Configurazione Muro di Sicurezza: Fare clic sul pulsante Abilita per abilitare il corrispondente muro di sicurezza. Quando un muro di sicurezza non è stato configurato con un intervallo di sicurezza, verrà visualizzato un errore. Fare clic sul pulsante di configurazione nell'angolo in alto a destra, selezionare il muro di sicurezza che si desidera impostare, visualizzare automaticamente la distanza di sicurezza (opzionale, default 0), e quindi fare clic sul pulsante "Imposta" per impostare con successo.
- Configurazione dei Punti di Riferimento del Muro di Sicurezza: Dopo aver selezionato un muro di sicurezza, è possibile impostare quattro punti di riferimento. I primi tre punti sono punti di riferimento del piano, utilizzati per confermare il piano del muro di sicurezza impostato. Il quarto punto è il punto di riferimento dell'intervallo di sicurezza, utilizzato per confermare l'intervallo di sicurezza del muro di sicurezza impostato.

Se i punti di riferimento vengono impostati con successo, verrà visualizzata una luce verde. In caso contrario, verrà visualizzata una luce gialla fino a quando i punti di riferimento non vengono impostati con successo e diventano verdi. Quando tutti e quattro i punti di riferimento sono stati impostati con successo, l'intervallo di sicurezza può essere calcolato. Dopo il calcolo riuscito, lo stato del punto del parametro dell'intervallo di sicurezza torna al valore predefinito.

.. image:: safety/025.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-19 Impostazioni dei Punti di Riferimento dell'Intervallo di Sicurezza

- Effetto Applicativo: Abilitare il muro di sicurezza configurato con successo. Trascinare il robot. Se il TCP dell'estremità del robot è all'interno dell'intervallo di sicurezza impostato, il sistema è normale. Se è al di fuori dell'intervallo di sicurezza impostato, verrà visualizzato un errore.

.. image:: safety/026.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-20 Effetto dopo l'Impostazione Riuscita dell'Intervallo di Sicurezza

Zona di Interferenza
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Sotto la barra del menu "Impostazioni Iniziali" -> "Sicurezza" -> "Zona di Interferenza", fare clic sulla voce del sottomenu "Singolo" per accedere all'interfaccia di configurazione della zona di interferenza.

È necessario configurare il metodo di interferenza e l'operazione all'ingresso della zona di interferenza. I metodi di interferenza sono divisi in "Interferenza di Asse" e "Interferenza di Cuboide".

.. image:: safety/027.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-21 Metodi della Zona di Interferenza

Fare clic sull'icona della zona di interferenza, utilizzare l'interruttore per controllare se è abilitata e fare clic sul pulsante di configurazione nell'angolo in alto a destra per la configurazione dei parametri.

.. image:: safety/028.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-22 Configurazione della Zona di Interferenza

Innanzitutto, configurare il movimento della zona di interferenza come "Continua Movimento" o "Arresto". Successivamente, impostare la configurazione di trascinamento all'ingresso della zona di interferenza. Gli utenti possono impostare la strategia dopo l'ingresso nella zona di interferenza in modalità di trascinamento in base alle proprie esigenze: nessuna restrizione di trascinamento, ritorno di impedenza o passaggio alla modalità manuale.

Quando si seleziona Interferenza di Asse, è necessario configurare i parametri di interferenza dell'asse. Il metodo di rilevamento può essere "Posizione di Comando" o "Posizione di Feedback". La modalità della zona di interferenza può essere "Interferenza Entro Intervallo" o "Interferenza Fuori Intervallo". Successivamente, impostare l'intervallo per ciascun giunto e se l'intervallo per ciascun giunto è abilitato. È possibile inserire valori o utilizzare l'icona "Aggiorna" dopo "Min" e "Max" per registrare la posizione corrente del robot, e infine fare clic su Configura.

.. image:: safety/029.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-23 Configurazione dell'Interferenza di Asse

Quando si seleziona Interferenza di Cuboide, è necessario configurare i parametri di interferenza del cuboide. Il metodo di rilevamento può essere "Posizione di Comando" o "Posizione di Feedback". La modalità della zona di interferenza può essere "Interferenza Entro Intervallo" o "Interferenza Fuori Intervallo". Il sistema di coordinate di riferimento può essere "Coordinata Base" o "Coordinata Pezzo", selezionato in base all'uso effettivo. Successivamente, impostare l'intervallo. Esistono due metodi per l'impostazione dell'intervallo. Il primo metodo è il "Metodo dei Due Punti", che utilizza due vertici diagonali del cuboide. Le posizioni possono essere inserite o registrate tramite l'insegnamento del robot. Infine, fare clic su Applica.

.. image:: safety/030.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-24 Configurazione dell'Interferenza di Cuboide

Il secondo metodo è il "Metodo Centro + Lunghezza Lato", dove il punto centrale del cuboide e la lunghezza del lato del cuboide formano la zona di interferenza. Le posizioni possono essere inserite o registrate tramite l'insegnamento del robot. Infine, fare clic su Applica.

.. image:: safety/031.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-25 Configurazione dell'Interferenza di Cuboide

Appendice: Istruzione di Attesa Bloccante per Pinza
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Fare clic su "Teach Program" -> "Istruzioni Periferiche" -> "Pinza" per aggiungere un'istruzione di attesa per il completamento del movimento della pinza, che può bloccare fino al completamento dell'azione di serraggio per ottenere la posizione fisica effettiva della pinza.

.. image:: safety/032.png
   :width: 4in
   :align: center

.. centered:: Figura 7.4-26 Istruzione di Attesa per il Completamento del Movimento della Pinza
 
- Stato Pinza: Movimento non completato, movimento completato senza rilevamento oggetto, movimento completato con rilevamento oggetto;
- Tempo di Timeout: Unit ms, -1 significa attesa eterna.
- Strategia di Timeout: È possibile scegliere di interrompere con errore o continuare l'esecuzione.
- Tipo Pinza: È possibile scegliere pinza parallela o pinza rotante.

.. note:: 
   Nota: L'istruzione di attesa per il completamento del movimento della pinza è applicabile solo ai protocolli personalizzati; i dispositivi già adattati attualmente non la supportano.

   È anche possibile utilizzare direttamente GetGripperMotionDone() per la valutazione. Il parametro di input è il tipo di pinza: 0 per pinza parallela, 1 per pinza rotante. I valori di ritorno sono errore della pinza e stato della pinza. Errore della pinza 0 significa nessun errore, altri valori significano che c'è un errore. Stato della pinza 0 significa movimento non completato, 1 significa movimento completato senza rilevamento oggetto, 2 significa movimento completato con rilevamento oggetto. I programmi di esempio per l'attesa del completamento del movimento della pinza e l'acquisizione della posizione della pinza sono i seguenti:

.. image:: safety/033.png
   :width: 6in
   :align: center

.. centered:: Figura 7.4-27 Programma di Esempio del Movimento della Pinza