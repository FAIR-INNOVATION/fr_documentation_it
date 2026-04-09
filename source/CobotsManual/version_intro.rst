Versione V3.9.4
-----------------

Data: 2026-04-08

- **Ottimizzata la funzione TPD di Insegnamento e Riproduzione di Traiettorie del Robot**: 
    Percorso: Programma di insegnamento -> Programmazione -> Istruzione TPD.
  
    Descrizione: 1. Generazione automatica dell'istruzione Lua per il punto iniziale 2. Design anti-errore per il pulsante di avvio.

- **Ottimizzata la funzione di Backup dei Dati di Webapp**: 
  
    Descrizione: Migliorata e ottimizzata la funzione di backup dei dati.

- **Ottimizzati i Limiti Soft e la Postura di Confezionamento di FR3WML**: 
  
    Descrizione: Impostato l'intervallo del limite soft per l'articolazione 3 a ±163°.

- **Ottimizzata la Funzione di Compensazione dei Parametri Completamente DH e la Verifica Rapida**: 
  
    Descrizione: Compensato il modello a parametri completi.
 
- **Aggiunta la Funzione di Controllo di Impedanza per il Movimento PTP**: 
  
    Descrizione: Migliorata la sicurezza durante l'interazione uomo-robot.

- **Aggiunta la Funzione del Protocollo di Comunicazione per il Dispositivo End-Effector della Testa di Moxibustione**: 
    Percorso: Impostazioni iniziali -> Periferiche -> Trasmissione trasparente dell'end-effector.
  
    Descrizione: Aggiunto l'adattamento del protocollo di comunicazione per nuovi dispositivi end-effector.

- **Aggiunto l'Adattamento del Pacchetto Linguistico per la Versione Software in Tedesco**: 
  
    Descrizione: Aggiunta la commutazione della lingua tedesca.

- **Aggiunta la Funzione di Effetto delle Impostazioni di Velocità di Sicurezza sulle Istruzioni di Movimento Servo**: 
    Percorso: Impostazioni iniziali -> Sicurezza -> Velocità di sicurezza.
  
    Descrizione: Aggiunta l'opzione della strategia di sicurezza per fermare, segnalare errore e disabilitare dopo il superamento della velocità.

- **Aggiunto l'Adattamento LA per il Router Wireless TP-LINK AX3000**: 
  
    Descrizione: Risolto il problema dell'impossibilità di accedere direttamente a webApp tramite connessione wireless dopo un'interruzione di corrente e il riavvio.
    
- **Aggiunta la Funzione di Oscillazione a Punto Fisso**: 
    Percorso: Programma di insegnamento -> Programmazione -> Istruzione Weave.
  
    Descrizione: Esecuzione della funzione di oscillazione a punto fisso in combinazione con un sensore laser esterno.

Versione V3.9.3
-----------------

Data: 2026-02-11

- **Ottimizzate Impostazioni Velocità Comandi Movimento SmartTool**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Impugnatura Saldatura.
  
    Descrizione: L'intervallo di impostazione della velocità per i comandi PTP, LIN e ARC è stato regolato a 0-100% (il limite superiore originale era 30%).

- **Ottimizzata Osservazione Forza Esterna Senza Sensore e Migliorata Esperienza di Trascinamento**:
    Percorso: Applicazioni Ausiliarie -> Applicazioni Utensile -> Blocco Trascinamento.
  
    Descrizione: Precisione osservazione forza esterna migliorata a ±0.5N.

- **Ottimizzato Meccanismo Riconnessione Master Modbus TCP**:
    Percorso: Programma Insegnamento -> Programmazione Programma -> Modbus TCP.
  
    Descrizione: Aggiunta logica pausa.

- **Aggiunta Funzione Comandi Debug Asse Esteso**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Asse Esteso.
  
    Descrizione: Implementata soluzione cinematica inversa robot nel sistema coordinate asse esteso e movimento servo ServoCart con assi estesi.

- **Aggiunta Funzione Configurabile Stato Reset DO in Pausa/Ripresa**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Impugnatura Saldatura.
  
    Descrizione: Opzione per scegliere se lo stato di uscita DO dopo la ripresa del movimento è coerente con lo stato prima della pausa.

Versione V3.9.2
-----------------

Data: 2026-01-26

- **Ottimizzazione Insegnamento Trascinamento ad Anello di Posizione Sensore di Coppia Articolare**:
    Percorso: Applicazioni Ausiliarie -> Applicazioni Utensile -> Blocco Trascinamento.
  
    Descrizione: Risolto il problema di precisione insufficiente nell'allineamento del punto entro 2 secondi durante il trascinamento tra le articolazioni.

- **Ottimizzazione Scheda di Espansione**:
  
    Descrizione: Ottimizzato il meccanismo di sincronizzazione dati DO estesi.

- **Ottimizzazione Funzione Tracciamento Arco**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Saldatrice.
  
    Descrizione: Aggiunta acquisizione corrente di saldatura in tempo reale tramite il protocollo aperto periferico ModbusTCP.

- **Ottimizzazione Funzione Reset IP Controller e Teach Pendant Fisico**:
    Percorso: Impostazioni di Sistema -> Rete.
  
    Descrizione: ① Aggiunta funzione "Reset IP Controller" in webrecovery, richiede conferma secondaria; ② Aggiunta funzione di reset IP al teach pendant fisico; ③ Aggiunta la possibilità per il teach pendant fisico di resettare il proprio IP tramite pulsanti fisici quando non connesso. L'IP del teach pendant è 192.168.58.77.

- **Aggiunta Nuova Configurazione Robot FR3C**:
  
    Descrizione: Intervallo operativo dei giunti coerente con la serie FR3, braccio superiore e inferiore coerenti con WMS, carico nominale 3kg.

- **Aggiunta Funzione Interferenza Cubo**:
    Percorso: Impostazioni Iniziali -> Sicurezza -> Zona Interferenza -> Interferenza Cubo.
  
    Descrizione: Implementato il controllo simultaneo di interferenza per almeno 4 cubi e l'uscita CO configurabile corrispondente ai segnali di interferenza.

- **Aggiunta Estensione Funzionalità Modulo slave_interpret (Protocollo PROFINET) e Funzione Visualizzazione IO Completa Web**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Comunicazione Scheda -> Aggiornamento Scheda.
  
    Descrizione: Aggiunto aggiornamento firmware EtherCAT scheda Jiyuan, rilevamento comunicazione PLC, ciclo configurabile e funzione di visualizzazione IO completa Web (protocollo PROFINET).

- **Aggiunta Funzioni Protocollo Aperto Smarttool**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Saldatrice (Welding Handle).
  
    Descrizione: ① Aggiunta analisi creazione programma smarttool ed elaborazione segnali di rilevamento basata sul protocollo aperto, e aggiunta funzione anti-errore ai tasti "Annulla, Elimina". ② Aggiunta funzione generazione automatica configurazione tasti protocollo aperto smarttool.

- **Aggiunta Compatibilità Pacchetti di Backup tra Versioni Software QX e LA**:
    Percorso: Applicazioni Ausiliarie -> Applicazioni Utensile -> Backup Dati.
  
    Descrizione: ① QX supporta e può importare completamente pacchetti di backup LA, LA supporta e può importare completamente pacchetti di backup QX; ② Compatibile con pacchetti di backup dalla versione v3.8.7 in poi.

- **Aggiunta Parametri Configurabili per CI End e CI Controller**:
    Percorso: Impostazioni Iniziali -> Base -> Impostazioni I/O -> DI.
  
    Descrizione: Abilita l'interruzione movimento configurabile per CI End e sincronizza alcune funzioni configurabili CI Controller a CI End.

- **Aggiunta Funzione Tracciamento Servo Dati Laser Robot**:
    Percorso: Impostazioni Iniziali -> Periferiche -> Sensore Laser Linea.
  
    Descrizione: Abilita il robot a tracciare direttamente utilizzando i dati del sensore laser.

- **Aggiunta Funzione Configurazione Teach Pendant**:
  
    Descrizione: ① I tasti F1-F4 sul teach pendant supportano la configurazione di funzioni personalizzate tramite l'interfaccia WEB; ② La commutazione della chiave in modalità personalizzata può essere configurata come modalità trascinamento.

Versione V3.9.1
-----------------

Data: 2025-12-30

- **Funzione di Registrazione a Sfondo del Robot per Eventi di Guasto e Allarme**: 
  
    Descrizione: Capace di registrare informazioni su guasti e allarmi durante i logout dell'interfaccia utente, visualizzabili dopo il nuovo accesso.

- **Comandi PTP e LIN Aggiungono Funzione di Movimento Relativo alla Posizione Corrente, WebApp Aggiunge Funzione di Aggiunta Comando ServoJ**: 
    Percorso: Insegnamento Programma -> Programmazione Programma -> Comandi PTP/LIN.
  
    Descrizione: Risolve il problema della complessità operativa dei comandi quando il braccio robotico non ha punti insegnati ma richiede uno scostamento basato sulla posizione corrente. L'inserimento di un singolo comando realizza il movimento.

- **Interruttore di Debug del Protocollo Aperto Lua per End-effector e Funzione di Verifica della Sintassi**: 
    Percorso: Configurazione Iniziale -> Periferiche -> Pinza, Sensore di Forza, Maniglia di Saldatura.
  
    Descrizione: Il sistema integrato del controller è ora adattato ai protocolli dell'end-effector (pinza, sensore di forza, maniglia di saldatura). Questa ottimizzazione consente la selezione e l'applicazione diretta all'end-effector all'interno della webAPP. Il webServer ora include la verifica della sintassi Lua per i protocolli, segnalando errori direttamente in caso di fallimento della verifica. La webAPP aggiunge un interruttore di debug per il protocollo aperto Lua, che, quando abilitato durante il debug, esegue il Lua dell'end-effector sopprimendo gli errori di timeout della comunicazione del sensore.

- **Ottimizzazione della Funzionalità Scenario di Pallettizzazione FRCap**: 
    Percorso: Applicazioni Ausiliarie -> Pacchetto Processo -> Palletizzazione.
  
    Descrizione: La pallettizzazione ora supporta due punti di prelievo. Dopo l'arrivo dei materiali su due linee di trasporto, il robot preleva sequenzialmente i materiali dai punti di prelievo sulle due linee e li posiziona su due pallet corrispondenti.

- **Ottimizzazione della Funzionalità del Pannello di Insegnamento Fisico**: 
    Percorso: Impostazioni di Sistema -> Impostazioni Generali -> Rete
  
    Descrizione: In precedenza, gli utenti dovevano prima passare alla webAPP prima di accedere alla propria interfaccia del computer host quando utilizzavano il pannello di insegnamento, il che era macchinoso. Dopo l'ottimizzazione, ruotando l'interruttore a chiave fisica senza accedere all'interfaccia di insegnamento, il robot può passare tra le modalità manuale/automatica.

- **Ottimizzazione della Funzione di Collisione**: 
    Percorso: Configurazione Iniziale -> Base -> Giunto -> Livello di Collisione -> Rilevamento Falsi Allarmi.
  
    Descrizione: Quando il livello di collisione è impostato su 1, il robot può funzionare a qualsiasi velocità senza falsi allarmi dovuti all'alta velocità. Errori e arresti si verificano solo in caso di collisione o schiacciamento effettivi.

- **Funzione di Calibrazione TCP per Sensore Fotoelettrico**:
    Percorso: Impostazione Iniziale -> Base -> Coordinate Utensile -> Calibrazione Automatica Fotoelettrica.
  
    Descrizione: Supporta la calibrazione automatica per torce di saldatura a manico dritto e a manico curvo;  

Versione V3.9.0  
-----------------  

Data: 2025-11-27  

- **Applicazione della testa di levigatura DFC con controllo di forza Dajuru**:  
  Percorso: Impostazioni iniziali → Periferiche → Levigatura → Testa di levigatura DFC con controllo di forza Dajuru.  
  
  Descrizione: La parte software della periferica intelligente DFC per il controllo di forza nella levigatura è stata adeguatamente adattata e testata, soddisfacendo pienamente i requisiti di integrazione del sistema di levigatura DFC.  

- **Calibrazione dei parametri del sensore di coppia articolare sull’intero robot**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Blocco trascinamento → Trascinamento completo con sensore di coppia articolare.  
  
  Descrizione: Eseguendo una traiettoria predefinita, vengono calibrati i parametri chiave del sensore di coppia articolare: sensibilità, linearità, errore di isteresi e ripetibilità.  

- **Nuova funzione di insegnamento tramite trascinamento guidato dal sensore di coppia articolare per evitare sovraoscillazioni**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Blocco trascinamento → Trascinamento completo con sensore di coppia articolare.  
  
  Descrizione: Mitiga il fenomeno di sovraoscillazione nel loop di corrente durante il trascinamento; una volta attivata, questa funzione consente un’operazione di posizionamento manuale precisa e intuitiva.  

- **Funzione di saldatura su linee di intersezione (curve di intersezione)**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione "Linea di intersezione".  
  
  Descrizione: Registrando 6 punti di insegnamento rispettivamente sulle sezioni trasversali del tubo principale e del tubo di raccordo, e inserendo parametri quali direzione di movimento, velocità, accelerazione e valore di offset, il robot genera automaticamente la traiettoria della linea di intersezione tra due tubi circolari ed esegue la saldatura.  

- **Estensione della funzione “Attesa ingresso analogico Modbus” con aggiunta della condizione “uguale a”**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzioni Modbus.  
  
  Descrizione: È stata aggiunta la possibilità di impostare una condizione di attesa basata sull’uguaglianza del valore di ingresso analogico proveniente da una stazione Modbus remota.  

- **Aggiornamento istantaneo dei punti di insegnamento e nuova funzione di esecuzione singola LIN**:  
  Percorso: Programma di insegnamento → Punti di insegnamento → Gestione punti.  
  
  Descrizione: Dall’interfaccia di gestione dei punti, è possibile aggiornare immediatamente la posa attuale del robot nel punto corrispondente utilizzando la barra di controllo fisica; è inoltre possibile scegliere se sincronizzare automaticamente tale aggiornamento con i programmi di insegnamento associati. È stata inoltre introdotta l’esecuzione singola di istruzioni LIN.  

- **Ottimizzazione della funzione di registrazione punti in modalità tabella posizioni**:  
  Percorso: Programma di insegnamento → Punti di insegnamento → Gestione punti.  
  
  Descrizione: In modalità tabella posizioni, la riregistrazione di un punto aggiorna automaticamente anche il relativo programma Lua. Sono stati risolti problemi occasionali riscontrati in precedenza: sovraspeed nel modo di riduzione PTP e arresto anomalo dopo il raggiungimento del punto finale nel modo di regolazione velocità LIN.  

- **File di configurazione ``user``**:  
  Descrizione: Migliorata la gestione degli errori di caricamento del file di configurazione ``user``: sono state aggiunte funzionalità di riavvio automatico del file di backup e di ripristino (rollback) del backup in caso di errore.  

- **Versione dell’interfaccia web**:  
  Descrizione: L’interfaccia web è stata aggiornata alla versione 2.0, con miglioramenti significativi nell’usabilità, nell’aspetto grafico e nella fluidità delle operazioni.  

- **Nuovi modelli robotici V6.5**:  
  Descrizione: Grazie a ottimizzazioni hardware (es. riduttori) e algoritmi avanzati, è stata ridotta la vibrazione del robot e migliorata la precisione di tracciamento della traiettoria. Sono stati introdotti i nuovi modelli: FR3, FR5, FR10, FR16 e FR20.  

- **Configurazione aggiuntiva per il modello robotico FR5C**:  
  Descrizione: La versione LA del software include ora il supporto nativo per la configurazione del modello robotico FR5C.  

Versione V3.8.7  
-----------------  

Data: 2025-10-21  

- **Funzione di rilevamento collisione per guide lineari a cremagliera**:  
  Percorso: Impostazioni iniziali → Base → Articolazioni → Livello di collisione → Rilevamento collisione per guide lineari a cremagliera.  
  
  Descrizione: Consente l’arresto d’emergenza del robot qualora si verifichi una collisione durante il movimento della guida lineare, migliorando notevolmente la sicurezza operativa.  

- **Nuova funzione di impostazione della velocità fisica reale per la traiettoria elicoidale N-Spiral**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione "Elica N-Spiral".  
  
  Descrizione: Garantisce che la velocità lineare effettiva dell’estremità strumentale sia costante e coincida esattamente con il valore impostato nella fase uniforme della traiettoria.  

- **Ripristino automatico opzionale dopo arresto di sicurezza**:  
  Percorso: Impostazioni iniziali → Sicurezza → Arresto di emergenza.  
  
  Descrizione: È stata aggiunta una nuova configurazione per la strategia di riabilitazione post-reset dell’arresto di emergenza, conforme alla categoria 1b secondo la norma EN ISO 13850.  

- **Taratura a carico del sensore di forza/torsione e parametri di ammettenza per l’adattamento di orientamento**:  
  Percorso: Impostazioni iniziali → Base → Carico; Programma di insegnamento → Programmazione → Istruzione "F/T Control".  
  
  Descrizione: Sono stati resi disponibili nuovi parametri di ammettenza per consentire l’adattamento dinamico dell’orientamento dello strumento in risposta alle forze esterne.  

- **Nuova funzione di tracciamento laser in tempo reale su archi e cerchi completi**:  
  Descrizione: Il sistema è in grado di eseguire il tracciamento laser in tempo reale su archi circolari e cerchi completi, con variazione continua dell’orientamento durante il movimento, permettendo così la scansione e la riproduzione fedele di tali geometrie.  

- **Funzione box comandi (button box)**:  
  Descrizione: Ottimizzazione della funzione di reset dell’indirizzo IP nella versione 1.0 del box comandi.  

Versione V3.8.6  
-----------------  

Data: 2025-09-19  

- **Nuova funzione di controllo impedenza del robot**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione "F/T".  
  
  Descrizione: Rileva in tempo reale le forze esterne applicate: al superamento di una soglia predefinita, il robot si adatta attivamente deviando dalla traiettoria programmata; al ritorno sotto la soglia, riprende la traiettoria originale, migliorando l’interazione uomo-robot.  

- **Nuova funzione di verifica del momento torcente prima del trascinamento**:  
  Percorso: Impostazioni iniziali → Base → Livello di collisione.  
  
  Descrizione: Prima di entrare nella modalità di trascinamento, viene calcolata la differenza tra comando e feedback di coppia per ciascuna articolazione. Se tale differenza supera una soglia critica (causata da errata configurazione del carico o del montaggio), il trascinamento viene bloccato, prevenendo potenziali perdite di controllo.  

- **Nuova funzione di saldatura oscillante personalizzabile**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione "Weave".  
  
  Descrizione: L’utente può definire liberamente la forma, la frequenza, l’ampiezza e la legge di variazione dell’oscillazione per realizzare saldature personalizzate.  

- **ModbusTCP**:  
  Percorso: Programma di insegnamento → Programmazione → ModbusTCP.  
  
  Descrizione: Migliorata la gestione del timeout del master ModbusTCP, garantendo maggiore affidabilità nelle comunicazioni prolungate.  

- **Ventose pneumatiche**:  
  Percorso: Impostazioni iniziali → Periferiche → Ventose a matrice.  
  
  Descrizione: Ottimizzata la compatibilità dell’interfaccia web con le ventose pneumatiche a matrice.  

- **Gestione degli errori di localizzazione del filo di saldatura**:  
  Descrizione: Migliorata la segnalazione degli errori relativi alla ricerca del filo di saldatura nell’app WebAPP, con possibilità di azzeramento manuale dell’allarme.  

- **Funzione IO configurabile**:  
  Descrizione: Aggiunta la possibilità di configurare gli ingressi (CI0–CI4) e le uscite (CO0–CO4) per i modelli FR3C e FR3MT.  

Versione V3.8.5  
-----------------  

Data: 2025-08-19  

- **Debug della rete Socket**:  
  Percorso: Programma di insegnamento → Programmazione → Debug rete Socket.  
  
  Descrizione: Consente di creare, configurare e rimuovere fino a 4 connessioni Socket. Attraverso moduli istruzione è possibile generare programmi di insegnamento per aprire/chiudere connessioni, inviare e ricevere dati.  

- **Funzione di conversione da G-code CAD a traiettoria robotica**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Conversione G-code.  
  
  Descrizione: I file G-code generati da software CAM (es. SolidWorks, Fusion 360) contenenti linee, archi, cerchi e curve spline possono essere importati direttamente nell’interfaccia web per la generazione automatica della traiettoria robotica.  

- **Aggiunta della velocità fisica reale alle istruzioni di movimento (lineare, arco, cerchio)**:  
  Percorso: Programma di insegnamento → Programmazione; Impostazioni iniziali → Periferiche → Manico di saldatura.  
  
  Descrizione: Ora è possibile specificare direttamente la velocità fisica effettiva con cui verrà eseguita l’istruzione di movimento.  

- **Ottimizzazione della funzione di regolazione della velocità PTP**:  
  Descrizione: Garantisce una transizione fluida tra diverse velocità, riducendo le fluttuazioni improvvise nei punti di collegamento tra istruzioni.  

- **Configurazione modelli robotici**:  
  Descrizione: Aggiunta la configurazione per il modello robotico FR30L.  

- **Adattamento del cabinet di controllo**:  
  Descrizione: Nuovo supporto per la scheda ETMP03E (protocollo EtherCAT).  

Versione V3.8.4.1  
-----------------  

Data: 2025-07-30  

- **Adattamento del cabinet di controllo al modulo di trasparenza Ethernet e al controllo di ventose/morsetti**:  
  Percorso: Impostazioni iniziali → Periferiche → Ventose a matrice.  
  
  Descrizione: Consente il controllo di fino a 20 ventose a matrice tramite modulo Ethernet-to-RS485, sia attraverso l’interfaccia web che tramite protocollo aperto.  

- **Pianificazione anticipata della traiettoria (anticipazione a velocità costante)**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Aggiunta un’opzione di attivazione/disenabilitazione per il movimento anticipato a velocità costante.  

- **Ottimizzazione della funzione “modalità slave” del cabinet di controllo**:  
  Percorso: Impostazioni iniziali → Periferiche → Comunicazione schede / Modalità remota.  
  
  Descrizione: Nuovo supporto per la scheda ETMP03E di Jiyuan (protocollo EtherCAT).  

- **Funzione di acquisizione della posizione di ricerca laser**:  
  Percorso: Impostazioni iniziali → Periferiche → Sensore laser a linea.  
  
  Descrizione: Dopo un’esecuzione riuscita della ricerca del giunto saldato mediante laser, è possibile recuperare la posizione memorizzata nella variabile ``seamPos`` tramite SDK o comandi TCP.  

- **Aumento delle velocità massime per FR5 e FR10**:  
  Descrizione: Velocità lineare massima di FR5 aumentata da 1,0 m/s a 1,7 m/s; quella di FR10 da 1,5 m/s a 2,0 m/s.  

- **Configurazione modelli robotici**:  
  Descrizione: Aggiunta la configurazione per il modello robotico FR5-WML (braccio allungato).  

- **Ottimizzazione dell’aggiornamento software**:  
  Descrizione: Riduzione dei tempi di aggiornamento; compatibilità completa con downgrade da qualsiasi versione successiva a una qualsiasi versione compresa tra 3.7.6 e 3.8.4.  

- **Ottimizzazione del ripristino delle impostazioni di fabbrica**:  
  Descrizione: Il ripristino conserva il modello robotico, i parametri di rigidità, le impostazioni della dinamica e la versione del box comandi.  

Versione V3.8.4  
-----------------  

Data: 2025-07-18  

- **Implementazione della funzione di transizione morbida (blending) per assi esterni**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Garantisce movimenti continui e senza scosse tra istruzioni che coinvolgono assi esterni, migliorando efficienza e qualità del movimento.  

- **Ottimizzazione della funzione “modalità slave” del cabinet di controllo**:  
  Percorso: Impostazioni iniziali → Periferiche → Comunicazione schede / Modalità remota.  
  
  Descrizione: Aggiunta la possibilità di configurare l’indirizzo IP delle schede, di inviare istruzioni LUA dall’interfaccia e di abilitare l’avvio automatico del protocollo slave in modalità remota.  

- **Adattamento della scheda N2L QX (EtherCAT)**:  
  Descrizione: Scheda di comunicazione industriale in tempo reale Faao, formato miniPCIe, compatibile con il protocollo EtherCAT.  

- **Movimento JOG del robot**:  
  Descrizione: Aggiunta l’uscita di stato CO durante il movimento JOG.  

Versione V3.8.3  
-----------------  

Data: 2025-06-27  

- **Funzione “modalità slave” per cabinet di controllo**:  
  Percorso: Impostazioni iniziali → Periferiche → Comunicazione schede.  
  
  Descrizione: Nuovo modulo di configurazione per la comunicazione con schede di espansione nazionali, supportando protocolli EIP, CC-Link e Profinet per l’interfacciamento con il robot in modalità slave.  

- **Rilevamento collisione con sensore di forza in modalità manuale**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Blocco trascinamento → Blocco assistito da sensore di forza.  
  
  Descrizione: Quando la funzione di trascinamento assistito da sensore di forza è attiva, il rilevamento collisione rimane attivo anche in modalità manuale, proteggendo efficacemente l’estremità strumentale.  

- **Pianificazione della traiettoria con profilo di velocità “a T” + funzione blending**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Garantisce transizioni fluide tra istruzioni di movimento consecutive, incrementando produttività e qualità del movimento.  

- **Ottimizzazione dell’interfaccia di interrogazione dello stato in WebApp**:  
  Percorso: Informazioni di stato → Interrogazione stato.  
  
  Descrizione: Parametri visualizzabili ridotti a 6; durata massima della forma d’onda: 30 secondi; aggiunta visualizzazione dati in tabella con copia negli appunti; possibilità di rinominare le etichette dei grafici.  

- **Ottimizzazione della forza di trascinamento per tutta la serie FR**:  
  Percorso: Impostazioni iniziali → Base → Articolazioni → Compensazione attrito → Compensazione forza di trascinamento.  
  
  Descrizione: Introduce una compensazione attiva del momento torcente durante il trascinamento, rendendo l’operazione più agevole e naturale.  

- **Ottimizzazione della memorizzazione dei log di sistema**:  
  Descrizione: Risolto un bug che causava anomalie nei file di log; impostazione predefinita di conservazione dei log: 7 giorni.  

Versione V3.8.2  
-----------------  

Data: 2025-05-29  

- **Adattamento del manico di saldatura tramite protocollo Lua aperto sull’estremità**:  
  Percorso: Impostazioni iniziali → Periferiche → Manico di saldatura.  
  
  Descrizione: Supporto completo per il manico di saldatura SmartTool tramite protocollo aperto; tutti i parametri sono completamente configurabili.  

- **Estensione del protocollo aperto per periferiche del controller con protocollo per saldatrici**:  
  Percorso: Impostazioni iniziali → Periferiche → Saldataci.  
  
  Descrizione: Possibilità di controllare la saldatrice tramite protocollo ModbusTCP utilizzando il protocollo aperto del controller.  

- **Nuova funzione di pausa per i programmi Lua**:  
  Percorso: Programma di insegnamento → Programmazione.  
  
  Descrizione: Durante l’esecuzione di un programma di insegnamento, è possibile mettere in pausa l’esecuzione su qualsiasi riga — inclusi comandi di attesa e di comunicazione — senza che il tempo di attesa venga consumato.  

- **Funzione di modellazione della velocità “a T” + blending**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Attivando la modalità “a T”, la curva di velocità diventa più fluida. Il blending supportato comprende: PTP–PTP, LIN–LIN, ARC–ARC, LIN–ARC, ARC–LIN.  

- **Funzione FIR con parametri adattivi + ripresa dopo pausa**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi; Impostazioni iniziali → Sicurezza → Configurazione movimento.  
  
  Descrizione: Aggiunta l’opzione di abilitazione globale FIR e di attivazione automatica dei parametri adattivi; quando attivata, le istruzioni standard PTP/LIN/ARC vengono convertite automaticamente in traiettorie pianificate con FIR (senza supporto per raggi di blending).  

- **Ottimizzazione di Modbus RTU**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi; Programma di insegnamento → Programmazione → Impostazioni Modbus RTU.  
  
  Descrizione: Configurazione completa di master ModbusRTU via WebApp (baud rate, tipo di parità, indirizzo stazione); monitoraggio in tempo reale dei registri ModbusRTU.  

- **Protezione con limiti software articolari**:  
  Percorso: Impostazioni iniziali → Articolazioni → Limiti software.  
  
  Descrizione: In modalità trascinamento, quando un’articolazione si avvicina al limite software impostato, viene applicata una forza di smorzamento; una volta rilasciata la forza esterna, l’articolazione ritorna autonomamente entro il limite.  

- **Funzione di inclinazione laterale durante l’oscillazione**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Permette di definire un angolo di oscillazione personalizzato intorno all’asse Rx del sistema di coordinate di oscillazione.  

- **Funzione di saldatura con parametri progressivi**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Consente la variazione graduale della velocità di avanzamento, della corrente e della tensione durante la saldatura.  

- **Funzione di inseguimento dell’arco elettrico basata su segnale analogico**:  
  Percorso: Impostazioni iniziali → Base → Impostazioni I/O → AI.  
  
  Descrizione: Collegamento diretto tra ingressi/uscite analogici e digitali del cabinet di controllo e quelli della saldatrice per realizzare un sistema di inseguimento dell’arco basato sulla retroazione analogica di corrente.  

- **Sistema di plugin FRCap + pacchetto plugin per pallettizzazione**:  
  Descrizione: Integrazione completa del sistema di plugin FRCap per piattaforma QX x86 e del pacchetto plugin per pallettizzazione. FRCap consente interazioni con il controller tramite API ufficiali oppure lo sviluppo di logiche personalizzate da parte dell’utente.  

- **Modelli e tipologie robotiche**:  
  Descrizione: Aggiunto il modello FR3-C e la sua configurazione.  

Versione V3.8.1  
-----------------  

Data: 2025-04-14  

- **Ottimizzazione della funzione di velocità “a T”**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi; Impostazioni iniziali → Modulo base.  
  
  Descrizione: Aggiunta la modalità di ottimizzazione della velocità a forma di trapezio, con riduzione dello *jerk* nelle fasi di partenza e arresto e aumento dell’accelerazione in fase iniziale. Ideale per applicazioni sensibili a collisioni o con vibrazioni residue marcate.  

- **Ottimizzazione della funzione di inseguimento nastro trasportatore**:  
  Percorso: Applicazioni ausiliarie → Pacchetti tecnologici → Inseguimento nastro trasportatore.  
  
  Descrizione: Nella modalità di inseguimento, è stata aggiunta la funzione di “ispezione in movimento”: non è necessario insegnare il movimento nel sistema di coordinate del pezzo; è possibile impostare un ritardo di attivazione personalizzato in termini di distanza.  

- **Funzione di richiamo impedenza nella zona di interferenza**:  
  Percorso: Impostazioni iniziali → Sicurezza → Zone di interferenza.  
  
  Descrizione: In modalità di trascinamento assistito da sensore di forza, l’ingresso in una zona di interferenza attiva una risposta impedenza per rallentare o deviare il movimento.  

- **Adattamento del manico di saldatura**:  
  Descrizione: Nuovo supporto per il manico di saldatura: installato sull’estremità robotica, permette di scrivere programmi di saldatura e di controllare avvio/arresto, commutazione manuale/automatico e trascinamento.  

- **Visualizzazione degli anelli di limitazione articolare nell’interfaccia Web**:  
  Descrizione: Abilitando questa funzione, viene mostrato in tempo reale il posizionamento di ciascuna articolazione rispetto ai suoi limiti fisici.  

- **Nuove funzioni SDK**:  
  Descrizione: SDK arricchito con funzioni per il download dei log del controller, di tutte le fonti dati e dei pacchetti di backup.  

- **Registrazione delle informazioni articolari prima/dopo una collisione**:  
  Descrizione: Viene registrata la posizione, la velocità, l’accelerazione e il momento torcente di ogni articolazione immediatamente prima e dopo una collisione, facilitando l’analisi post-evento.  

Versione V3.8.0  
-----------------  

Data: 2025-03-03  

- **Funzione di inseguimento dell’arco elettrico con offset e ampiezza oscillante progressive**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: L’ampiezza di oscillazione può variare gradualmente lungo un segmento di saldatura, passando in modo continuo dal valore iniziale a quello finale; il centro di saldatura può essere spostato attivamente rispetto al centro del giunto.  

- **Funzione di impostazione dinamica della soglia di rilevamento collisione**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: È possibile modificare in tempo reale la soglia di rilevamento collisione, scegliendo tra soglia di coppia articolare o soglia di forza/torsione nel sistema di coordinate TCP. Al verificarsi di una collisione, i dati di velocità, accelerazione e coppia vengono registrati nei log.  

- **Metodo di pianificazione anticipata della traiettoria in tempo reale**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Realizza una transizione fluida tra punti di traiettoria multipli, con regolazione automatica della velocità in base alla curvatura del percorso.  

- **Curve di carico per tutta la serie FR**:  
  Descrizione: Aggiornate le curve di carico per tutti i modelli della serie FR.  

- **Ottimizzazione della logica di commutazione della velocità in modalità ridotta**:  
  Descrizione: Risolto un problema per cui, in modalità ridotta, la velocità poteva scendere improvvisamente molto al di sotto del valore impostato.  

- **Ottimizzazione dei punti di insegnamento**:  
  Descrizione: Aggiunti messaggi informativi contestuali per migliorare la chiarezza e l’usabilità.  

- **Pacchetto CNC basato su FOCAS**:  
  Descrizione: Aggiunto il supporto per il pacchetto CNC basato sul protocollo FOCAS.  

- **Adattamento delle istruzioni slave a schede hardware**:  
  Descrizione: Supporto per le schede EnTalk miniPCIe (Profinet, Ethernet/IP, CC-Link IEF Basic) e CIFX 9OE-RE/F/PNS miniPCIe (Profinet, Ethernet/IP, EtherCAT, CC-Link IEF Basic).  

- **Funzione di timestamp nei checkpoint**:  
  Descrizione: Per le istruzioni servo J, vengono restituiti timestamp dettagliati: numero istruzione, istanti di invio, accodamento, uscita dalla coda ed esecuzione.  

- **Adattamento del sensore laser al protocollo aperto per periferiche del controller**:  
  Descrizione: Aggiunto il supporto per la comunicazione con sensori laser tramite il protocollo aperto per periferiche.  

Versione V3.7.8  
-----------------  

Data: 2025-01-20  

- **Funzione di inseguimento puntuale senza trasformazione dati laser + asse esterno**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi; Impostazioni iniziali → Periferiche → Sensore laser a linea.  
  
  Descrizione: Specificatamente progettata per il tracciamento puntuale in tempo reale su posizionatori rotanti: gli scarti di posizione rilevati dal laser vengono compensati direttamente sull’estremità strumentale del robot, anche durante il movimento dell’asse esterno.  

- **Nuove funzioni e ottimizzazioni per la configurazione CI**:  
  Percorso: Impostazioni iniziali → Base → Impostazioni I/O → DI; Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione:  
  1. Gli ingressi CI possono ora essere configurati per commutare tra modalità manuale/automatica in base a livello alto/basso.  
  2. Quando un programma Lua viene avviato tramite un ingresso CI configurato, viene eseguito il programma *correntemente aperto* nell’interfaccia WebApp, non l’ultimo salvato.  

- **Ottimizzazione della funzione di interrogazione dello stato in WebApp**:  
  Percorso: Informazioni di stato → Interrogazione stato.  
  
  Descrizione: Sostituita la richiesta periodica (polling) con una trasmissione attiva tramite WebSocket, riducendo significativamente il carico CPU.  

- **Configurabilità dello stato iniziale degli uscite DO del cabinet di controllo**:  
  Percorso: Impostazioni iniziali → Base → Impostazioni I/O → DO.  
  
  Descrizione: Aggiunta l’opzione “Stato DO all’accensione”: prima dell’abilitazione del robot, gli uscite DO possono essere impostate a livello alto o basso in base alle esigenze applicative.  

- **Metodo di pianificazione anticipata della traiettoria in tempo reale**:  
  Percorso: Programma di insegnamento → Programmazione / Programmazione grafica / Diagramma a nodi.  
  
  Descrizione: Introdotta la nuova istruzione ``TrajectoryLA``.  

- **Strategie post-collisione basate su sensore di forza**:  
  Percorso: Impostazioni iniziali → Articolazioni → Livello di collisione.  
  
  Descrizione: Nella modalità di rimbalzo post-collisione è stata aggiunta la possibilità di impostare una “velocità di sicurezza”.  

- **Sollevamento automatico post-collisione basato su sensore di forza**:  
  Descrizione: Dopo una collisione rilevata tramite sensore di forza, il robot solleva automaticamente l’estremità strumentale, con velocità massima regolabile.  

- **Curve di carico per tutta la serie FR**:  
  Descrizione: Aggiornate le curve di carico per tutti i modelli della serie FR.  

Versione V3.7.7  
-----------------  

Data: 2024-12-30  

- **Monitoraggio in tempo reale dello stato del morsetto**:  
  Percorso: Impostazioni iniziali → Periferiche → Morsetto → Monitoraggio stato.  
  
  Descrizione: Visualizzazione in tempo reale di velocità, coppia e posizione del morsetto.  

- **Acquisizione dati di guasto del controller**:  
  Percorso: Impostazioni sistema → Impostazioni generali → Dati di guasto.  
  
  Descrizione: In caso di collisione, errore di punto o altro guasto, il controller registra automaticamente i dati di posizione e velocità del robot nei 15 secondi precedenti e successivi all’evento. I dati possono essere esportati in formato CSV da WebApp per analisi approfondita.  

- **Evitamento e attraversamento di punti singolari con trascinamento assistito da sensore di forza**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Blocco trascinamento → Blocco assistito da sensore di forza.  
  
  Descrizione:  
  1. Con strategia “evitamento”: all’avvicinarsi di un punto singolare, viene generata una forza virtuale che respinge il movimento.  
  2. Con strategia “attraversamento”: il sistema passa temporaneamente in modalità trascinamento puro per superare il punto singolare, quindi ritorna al trascinamento assistito.  

- **Adattamento della vecchia libreria dinamica per installazioni libere a 360° e importazione backup con verifica dinamica**:  
  Percorso: Impostazioni iniziali → Base → Installazione; Applicazioni ausiliarie → Strumenti → Backup dati.  
  
  Descrizione: Durante l’importazione di un pacchetto di backup, vengono verificati tipo di robot, modalità di installazione, angolo di installazione e tipo di configurazione dinamica; se non coerenti, l’importazione viene bloccata con avviso.  

- **Attraversamento di punti singolari in modalità automatica**:  
  Percorso: Programma di insegnamento → Periferiche → Istruzioni LIN/ARC.  
  
  Descrizione: Aggiunta la configurazione “Attraversamento punto singolare” come protezione di movimento.  

- **Aggiornamento automatico del programma Lua dopo registrazione di un punto tramite pulsante sull’estremità**:  
  Percorso: Programma di insegnamento → Programmazione → Punti di insegnamento.  
  
  Descrizione: Registrando un punto tramite pulsante sull’estremità strumentale, il relativo programma Lua viene aggiornato automaticamente.  

- **Ottimizzazione dell’interfaccia di interrogazione dello stato**:  
  Percorso: Informazioni di stato → Interrogazione stato.  
  
  Descrizione: Miglioramenti UI/UX dell’interfaccia di interrogazione.  

- **Ottimizzazione delle interfacce WebApp e teach pendant**:  
  Descrizione: Aggiunto il supporto per le lingue russo e cinese tradizionale.  

- **Ottimizzazione dell’interfaccia WebApp**:  
  Descrizione: Angolo in basso a sinistra dell’interfaccia WebApp mostra ora la versione software e il modello robotico.  

- **Funzione di inseguimento laser con asse esterno**:  
  Descrizione:  
  1. Movimento sincrono tra robot e asse esterno: il sensore laser opera nel sistema di coordinate dell’asse esterno.  
  2. Movimento asincrono: il sensore laser può operare nel sistema di coordinate base del robot o in quello dell’asse esterno.  

- **Trascinamento del punto strumentale basato su sensore di forza**:  
  Descrizione: Nell’interfaccia web, configurando il sistema di coordinate FT come sistema personalizzato e abilitando il trascinamento assistito, il robot si muove lungo il sistema di coordinate strumentale definito.  

- **Funzione CNDE del robot**:  
  Descrizione: Il client può utilizzare CNDE (comunicazione UDP) per ottenere lo stato del robot e inviare comandi di controllo. Il periodo di aggiornamento dello stato è configurabile (1–200 ms); sia i dati di stato che i dati di comando possono essere personalizzati.  

Versione V3.7.6  
-----------------  

Data: 2024-11-18  

- **Ottimizzazione del layout della pagina “Impostazioni iniziali”**:  
  Percorso: Impostazioni iniziali.  
  
  Descrizione: Ottimizzati i layout delle pagine di configurazione strumenti, carico e di alcuni icone funzionali.  

- **Ottimizzazione dell’interfaccia di configurazione assi esterni in WebApp**:  
  Percorso: Impostazioni iniziali → Periferiche → Assi esterni.  
  
  Descrizione: Miglioramenti del layout e dell’interazione per la configurazione degli assi esterni.  

- **Ottimizzazione della funzione log di sistema**:  
  Percorso: Informazioni di stato → Log di sistema.  
  
  Descrizione: Aggiunta la visualizzazione a pagine e la categorizzazione dettagliata dei tipi di operazione registrata.  

- **Funzione di levigatura a forza costante in direzione XY**:  
  Percorso: Programma di insegnamento → Programmazione → Set di controllo forza → Istruzione ``F/T_Control``.  
  
  Descrizione: Aggiunto il parametro “raggio della mola”, permettendo movimenti rettilinei o curvi mantenendo costantemente il contatto con la superficie del pezzo.  

- **Funzione di acquisizione punti tramite laser**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Generazione punti di intersezione.  
  
  Descrizione: Le funzioni di ricerca del punto di intersezione tramite 3 o 4 punti sono ora accessibili anche tramite istruzioni script Lua.  

- **Configurazione “carrello a due gradi di libertà” per asse esterno**:  
  Percorso: Impostazioni iniziali → Periferiche → Assi esterni.  
  
  Descrizione: Nuova soluzione per carrelli a 2 DOF: comunicazione robot–PLC via UDP; controllo del carrello da parte della PLC tramite EtherCAT.  

- **Metodo di taratura TCP basato su piastra piana**:  
  Percorso: Impostazioni iniziali → Sistemi di coordinate → Coordinate strumento.  
  
  Descrizione: Aggiunto il metodo di taratura “piastra piana” per il sistema di coordinate strumento.  

- **Funzione di programma in background**:  
  Percorso: Programma di insegnamento → Programmazione.  
  
  Descrizione: I programmi in background possono ora accedere correttamente a tutti i dati I/O: I/O di sistema, Modbus e I/O estesi.  

- **Funzione di evitamento automatico di punti singolari nella traiettoria**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzioni LIN/ARC.  
  
  Descrizione: Aggiunta la configurazione “Evitamento punto singolare” come protezione di movimento.  

- **Adattamento per morsetto rotante**:  
  Percorso: Impostazioni iniziali → Periferiche → Morsetto.  
  
  Descrizione: Aggiunti codici funzione specifici per morsetti rotanti.  

- **Istruzioni slave con protocollo personalizzato**:  
  Percorso: Modalità remota.  
  
  Descrizione: Aggiunta la configurazione “Protocollo slave del controller”.  

- **Funzione di ricerca del filo di saldatura tramite UDP**:  
  Descrizione: Il robot può controllare avvio/arresto della ricerca del filo e ricevere il segnale di completamento tramite I/O esteso UDP.  

- **Ottimizzazione della funzione di backup**:  
  Descrizione: Supporto per l’importazione di pacchetti di backup da versioni precedenti (QX 3.6.1 e successive).  

- **Ottimizzazione del ripristino delle impostazioni di fabbrica**:  
  Descrizione: Aggiunta la verifica file per aumentare la stabilità e l’affidabilità del ripristino.  

- **Ottimizzazione della funzione di aggiornamento**:  
  Descrizione: Le versioni QX 3.6.9 e successive possono essere aggiornate direttamente a QX 3.7.6, mantenendo tutti i dati utente.  

- **Funzione di downgrade dell’interfaccia WebApp**:  
  Descrizione: WebApp supporta il downgrade a qualsiasi versione da QX 3.6.9 in poi, conservando i dati utente.  

Versione V3.7.5  
-----------------  

Data: 2024-09-30  

- **Regolazione della velocità angolare di transizione per l’orientamento in curva**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione LIN.  
  
  Descrizione: Aggiunta la configurazione “Velocità angolare di transizione regolabile” come protezione di movimento.  

- **Funzione di saldatura multistrato e multimandata con inseguimento dell’arco**:  
  Percorso: Applicazioni ausiliarie → Pacchetti tecnologici → Libreria esperti saldatura → Saldatura multistrato/multimandata.  
  
  Descrizione: Aggiunte la funzione “Oscillazione primo strato” e l’integrazione con l’inseguimento dell’arco.  

- **Configurazione asse esterno RS485**:  
  Percorso: Impostazioni iniziali → Periferiche → Assi esterni.  
  
  Descrizione: Aggiunte le configurazioni per accelerazione e arresto d’emergenza.  

- **Taratura automatica TCP dello strumento con dispositivo di taratura ottica fai-da-te**:  
  Percorso: Impostazioni iniziali → Base → Coordinate strumento.  
  
  Descrizione: Aggiunto il metodo di taratura “rilevamento ottico automatico”.  

- **Funzione di selezione lingua sul teach pendant**:  
  Percorso: Pagina di accesso.  
  
  Descrizione: Aggiunta la possibilità di cambiare lingua dall’interfaccia di login.  

Versione V3.7.4  
-----------------  

Data: 2024-08-09  

- **Funzione software basata su protocollo Lua aperto sull’estremità (per morsetti)**:  
  Percorso: Impostazioni iniziali → Periferiche → Morsetto.  
  
  Descrizione: Aggiunta la configurazione “Abilita protocollo estremità”.  

- **Funzione di oscillazione a denti obliqui**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione Weave.  
  
  Descrizione: Aggiunto il parametro “angolo di direzione di oscillazione”.  

- **Ottimizzazione del pacchetto tecnologico saldatura**:  
  Percorso: Impostazioni iniziali → Periferiche → Saldataci → Configurazione saldatrice.  
  
  Descrizione: Aggiunta la configurazione “Parametri tecnologici di saldatura”.  

- **Gestione dell’iper-velocità articolare nell’istruzione LIN**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione LIN.  
  
  Descrizione: Aggiunta la protezione “Limitazione iper-velocità articolare”.  

Versione V3.7.3  
-----------------  

Data: 2024-06-28  

- **Controllo del robot tramite Modbus slave**:  
  Percorso: Programma di insegnamento → Programmazione → ModbusTCP.  
  
  Descrizione: Aggiunta la configurazione “Controller slave”.  

- **Tipologie di arresto di emergenza**:  
  Percorso: Impostazioni iniziali → Sicurezza → Arresto di emergenza.  
  
  Descrizione: Aggiunte le categorie di arresto: 1a, 2a e 2 (secondo EN ISO 13850).  

Versione V3.7.2  
-----------------  

Data: 2024-06-07  

- **Configurazione del protocollo Lua aperto sull’estremità**:  
  Percorso: Impostazioni iniziali → Periferiche → Strumento estremità → Protocollo aperto.  
  
  Descrizione: Aggiunta la configurazione “Protocollo aperto”.  

- **Istruzione di controllo AO in movimento**:  
  Percorso: Programma di insegnamento → Programmazione.  
  
  Descrizione: Aggiunta l’istruzione “AO in movimento”.  

- **Trascinamento ibrido: forza 6D + impedenza articolare**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Blocco trascinamento.  
  
  Descrizione: Aggiunta la modalità “Trascinamento ibrido forza 6D + impedenza articolare”.  

- **Strategie di risposta post-collisione**:  
  Percorso: Impostazioni iniziali → Base → Articolazioni → Livello di collisione.  
  
  Descrizione: Aggiunta la configurazione “Strategia di collisione”.  

- **Funzione di attivazione iniziale del robot**:  
  Percorso: Impostazioni di accesso.  
  
  Descrizione: Aggiunta la verifica di attivazione obbligatoria alla prima accensione.  

Versione V3.7.1  
-----------------  

Data: 2024-05-10  

- **Funzione di blocco dell’interfaccia web**:  
  Percorso: Impostazioni sistema → Informazioni personalizzate.  
  
  Descrizione: Aggiunta la configurazione “Blocco schermo interfaccia web”.  

- **Funzione di calcolo del punto di intersezione da 3 o 4 punti di ricerca**:  
  Percorso: Applicazioni ausiliarie → Strumenti → Generazione punti di intersezione.  
  
  Descrizione: Aggiunta la funzione “Calcolo punto di intersezione da 3 o 4 punti di ricerca”.  

- **Ottimizzazione dell’orientamento nella saldatura a segmenti**:  
  Percorso: Programma di insegnamento → Programmazione → Istruzione Segment.  
  
  Descrizione: Aggiunta la configurazione “Modalità saldatura a segmenti”.  

- **Funzione di “parete virtuale” basata su sensore di forza**:  
  Percorso: Impostazioni iniziali → Periferiche → Sensore di forza; Applicazioni ausiliarie → Strumenti → Blocco trascinamento.  
  
  Descrizione: Aggiunti parametri di configurazione specifici per il sensore di forza e coefficiente di inerzia nel blocco trascinamento assistito.  

- **Nuove funzioni per la combinazione SmartTool + sensore di forza**:  
  Percorso: Impostazioni iniziali → Periferiche → Manico di saldatura.  
  
  Descrizione: Aggiunta la configurazione dei tasti funzione.  