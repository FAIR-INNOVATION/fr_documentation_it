Terminologia
============

.. toctree::
   :maxdepth: 5


**Categorie di arresto**:

- **Arresto di Categoria 0**: L’alimentazione elettrica del robot viene interrotta istantaneamente, provocando un arresto immediato di tutte le funzioni. Si tratta di un arresto non controllato: ciascun giunto frena alla massima velocità possibile, con conseguente possibile deviazione dalla traiettoria programmata. Questa tipologia di arresto protettivo è consentita esclusivamente in caso di superamento dei limiti di valutazione della sicurezza oppure in presenza di errori nel sistema di valutazione della sicurezza del controllo. Per ulteriori informazioni, consultare la norma EN ISO 13850:2008 o la IEC 60204-1:2006.

- **Arresto di Categoria 1**: Il robot viene fermato mantenendo temporaneamente l’alimentazione elettrica; una volta raggiunto l’arresto completo, l’alimentazione viene disconnessa. Si tratta di un arresto controllato, durante il quale il robot segue fedelmente la traiettoria programmata. L’alimentazione viene interrotta entro un secondo dall’arresto o non appena il robot risulta stabilmente fermo. Per ulteriori informazioni, consultare la norma EN ISO 13850:2008 o la IEC 60204-1:2006.

- **Arresto di Categoria 2**: Arresto controllato effettuato mantenendo l’alimentazione elettrica attiva. Il robot arresta tutti i movimenti entro un secondo. Un sistema di controllo di sicurezza certificato garantisce che il robot rimanga nella posizione raggiunta al termine dell’arresto. Per ulteriori informazioni, consultare la norma IEC 60204-1:2006.


**Copertura diagnostica (DC – Diagnostic Coverage)**: Misura l’efficacia delle diagnosi implementate per raggiungere il livello di prestazione (PL) richiesto. Per ulteriori informazioni, consultare la norma EN ISO 13849-1:2008.


**Integratore**: Ente responsabile della progettazione e realizzazione dell’installazione finale del robot. L’integratore deve condurre la valutazione del rischio finale e garantire che l’installazione rispetti integralmente le normative locali vigenti.


**Tempo medio di guasto pericoloso (MTTFd – Mean Time To Dangerous Failure)**: Valore calcolato e verificato al fine di determinare il livello di prestazione (PL) richiesto. Per ulteriori informazioni, consultare la norma EN ISO 13849-1:2008.


**Valutazione del rischio**: Processo sistematico volto all’identificazione di tutti i rischi associati all’uso del robot e alla loro riduzione ad un livello accettabile. Tale valutazione deve essere documentata e archiviata. Per ulteriori dettagli, fare riferimento alla norma ISO 12100.


**Livello di prestazione (PL – Performance Level)**: Livello discreto che esprime la capacità di una parte del sistema di controllo, correlata alla sicurezza, di eseguire correttamente una funzione di sicurezza sotto condizioni prevedibili. Il livello PLd è il secondo più elevato in termini di affidabilità, indicando che la funzione di sicurezza è altamente affidabile. Per ulteriori informazioni, consultare la norma EN ISO 13849-1:2008.


**Flangia di collegamento**: Struttura meccanica utilizzata per fissare strumenti esterni al robot; comunemente denominata *flangia di attacco*.


**Estremità del robot (Robot End)**: Punto centrale dell’ultimo asse cinematico del robot o del centro della flangia di collegamento.


**Punto centrale dello strumento (TCP – Tool Center Point)**: Punto caratteristico dello strumento montato sul robot, costituente il punto di controllo fondamentale del sistema robotico. In fase di fabbricazione, il TCP è impostato di default nel centro dell’ultimo asse cinematico o della flangia di collegamento. Ogni strumento possiede un proprio TCP definito da una traslazione e una rotazione rispetto al centro della flangia di uscita dello strumento. Le coordinate di posizione X, Y, Z definiscono la posizione del TCP, mentre le rotazioni RX, RY, RZ ne definiscono l’orientamento. Quando tutti questi valori sono pari a zero, il TCP coincide con il centro della flangia di collegamento.


**Sistema di coordinate dello strumento (TCF – Tool Coordinate Frame)**: Sistema di coordinate che descrive, sulla base del TCP, l’orientamento (posa) del sistema di coordinate dello strumento rispetto al sistema di coordinate del braccio terminale.


**Sistema di coordinate di base (Base Coordinate System)**: Sistema di coordinate fisso, il cui origine è generalmente posto nel centro dell’intersezione tra il primo asse del robot e la superficie di installazione. L’asse X è orientato in avanti (lungo la direzione principale del robot), l’asse Y è determinato secondo la regola della mano destra.


**Sistema di coordinate mondiale (World Coordinate System)**: Sistema di coordinate fisso definito nell’ambito dell’intera cella di lavoro o stazione. Nel caso di un singolo robot, questo sistema può coincidere con il sistema di coordinate di base; in presenza di più robot o dispositivi esterni, il sistema di coordinate mondiale fornisce un riferimento univoco comune. La sua posizione può essere scelta liberamente, purché consenta una facile taratura (calibrazione) dei sistemi di coordinate degli altri dispositivi.


**Sistema di coordinate articolare (Joint Coordinate System)**: Sistema di coordinate associato a ciascun giunto del robot. In questo sistema, ogni asse può muoversi indipendentemente, in senso positivo o negativo, entro i propri limiti meccanici. È particolarmente utile per spostamenti ampi del robot, quando non è richiesto un controllo specifico dell’orientamento del TCP. Il movimento manuale monogiro (jogging) del robot avviene tipicamente in questo sistema di coordinate.


**Sistema di coordinate dello strumento (Tool Coordinate System)**: Sistema di coordinate utilizzato per definire la posizione e l’orientamento del TCP. Se non configurato esplicitamente, il sistema di coordinate dello strumento coincide di default con il centro della flangia di collegamento. Dopo il montaggio di uno strumento, il TCP si sposta al centro geometrico dell’estremità dello strumento stesso.


**Sistema di coordinate dello strumento esterno (External Tool Coordinate System)**: Sistema di coordinate utilizzato per definire la posa (posizione e orientamento) di uno strumento fisso montato esternamente al robot (es. pinza su un banco di lavoro).


**Asse esteso (Extended Axis)**: Asse aggiuntivo, distinto dagli assi integrati nel corpo del robot, introdotto per soddisfare esigenze operative specifiche. Gli assi estesi includono tipicamente guide lineari (sliding rails), tavole di rotazione (turntables) e dispositivi servoazionati esterni.


**Modalità manuale (Manual Mode)**: Modalità in cui tutti i movimenti del robot sono controllati direttamente dall’operatore. In questa modalità, i dispositivi di sicurezza esterni (ad es. barriere fotoelettriche, porte di sicurezza) sono disattivati, al fine di consentire operazioni di messa a punto ravvicinata.


**Modalità automatica (Automatic Mode)**: Modalità utilizzata normalmente per l’esecuzione di programmi insegnati. In questa modalità, tutti i dispositivi di sicurezza esterni sono attivi e operativi.


**Precisione di ripetibilità (Repeatability)**: Misura del grado di concordanza tra le posizioni e gli orientamenti misurati in n prove consecutive, eseguite nelle medesime condizioni e con lo stesso metodo operativo.


**Insegnatore (Teach Pendant)**: Unità portatile collegata al sistema di controllo del robot, utilizzata per la programmazione e il comando manuale dei movimenti del robot.