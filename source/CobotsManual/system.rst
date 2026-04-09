Impostazioni di Sistema
==============================

.. toctree:: 
   :maxdepth: 6

Impostazioni Generali
-----------------------------

Cliccare sul menu a sinistra "Impostazioni di Sistema", quindi sul sottomenu "Impostazioni Generali" per accedere alla pagina delle impostazioni generali. Le impostazioni generali permettono di aggiornare l'ora del sistema robotico in base all'ora del computer per garantire l'accuratezza dei log.

.. image:: system/028.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-1 Impostazione dell'Ora

Impostazioni di Rete
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: system/001.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1-2 Schema Impostazioni di Rete

-  **Configura Scheda di Rete**: Inserire l'IP della scheda di rete da comunicare, la subnet mask (compilata automaticamente con l'IP), il gateway predefinito e il server DNS. L'IP predefinito della scheda 0 è: 192.168.57.2, e della scheda 1 è: 192.168.58.2.

-  **Abilita Insegnatore**: Controlla se abilitare l'insegnatore. Di default l'insegnatore è disabilitato e non permette l'operazione tramite insegnatore. Scorrendo l'interruttore si abilita l'insegnatore.
  
-  **IP di Accesso**: Selezionare la scheda di rete associata a WebAPP e WebRecovery. Quando l'insegnatore è abilitato, WebAPP seleziona di default la scheda 1, e la scheda 0 non è selezionabile.
  
-  **Configura Rete**: Cliccare su "Configura Rete" per avviare la configurazione. Dopo il completamento, è necessario riavviare il dispositivo.

Operazione Senza Login
++++++++++++++++++++++++++++++++++++++++++++++

Panoramica Funzionale
***************************

Dopo aver attivato la funzione Operazione Senza Login sul teach pendant fisico, è possibile ottenere le seguenti funzionalità:

- Quando nessun utente è loggato nell'interfaccia di insegnamento, ruotando l'interruttore a chiave fisico il robot può passare dalla modalità manuale/automatica, con il colore della luce dell'end-effector che cambia di conseguenza.
- Quando nessun utente è loggato nell'interfaccia di insegnamento, in modalità automatica, premendo l'interruttore di avvio fisico il robot può iniziare a eseguire il programma attualmente caricato.
- Quando nessun utente è loggato nell'interfaccia di insegnamento, in modalità automatica, premendo l'interruttore di arresto fisico il robot può interrompere l'esecuzione.

Istruzioni per l'Uso
***************************
Accedere alla pagina webapp, fare clic su "Impostazioni di Sistema", quindi fare clic su "Impostazioni Generali". Nella sezione Teach Pendant del modulo Rete, attivare l'interruttore "Abilita Teach Pendant" e l'interruttore "Operazione Senza Login". Una volta attivata la funzione, è possibile controllare la commutazione manuale/automatica del robot e l'avvio/arresto del programma utilizzando i pulsanti fisici senza essere loggati nella pagina del teach pendant. Questa configurazione viene mantenuta dopo un riavvio dell'alimentazione.

.. image:: system/045.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1‑2-1 Attivazione della Funzione Operazione Senza Login

Calibrazione Touchscreen Insegnatore
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dopo l'abilitazione dell'insegnatore, è possibile calibrarlo.

.. image:: system/029.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-3 Calibrazione Touchscreen Insegnatore
  
Configurazione PC Periferico
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Per abilitare il PC periferico, è necessario inserire l'IP. Dopo la configurazione, riavviare la scatola di controllo e il PC.

.. image:: system/030.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-4 Configurazione PC Periferico
  
Lingua di Sistema
~~~~~~~~~~~~~~~~~~~~~~

Importazione Lingua
+++++++++++++++++++++++++

Selezionare un pacchetto lingua da importare (Nota: il formato del file deve essere [codice lingua].json). Se l'importazione è riuscita e la lingua non è già presente, verrà aggiunta una nuova opzione.

.. image:: system/031.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-5 Interfaccia Lingua di Sistema

Esportazione Lingua
+++++++++++++++++++++++
Selezionare la lingua di sistema, ad esempio l'inglese, e cliccare su "Esporta" per scaricare il file.

.. image:: system/035.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1-6 Esportazione Lingua di Sistema
   
Applicazione Lingua
+++++++++++++++++++++++

Selezionare la lingua di sistema e cliccare su "Applica" per cambiarla. Dopo l'applicazione, il sistema si disconnette automaticamente e la lingua viene aggiornata. Esempio con l'inglese:

.. image:: system/036.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1-7 Interfaccia Lingua Applicata

Ripristino Modalità Sicurezza
+++++++++++++++++++++++++++++++++++

Quando è necessario effettuare aggiornamenti/rollback del sistema o si verificano errori di importazione del pacchetto lingua, seguire queste operazioni:
1. Accedere a Impostazioni di Sistema -> Impostazioni Generali -> Impostazioni Rete, impostare l'IP WebRecovery sulla scheda 0 e cliccare su "Configura Rete".

.. image:: system/037.png
   :width: 6in
   :align: center

.. centered:: Figura 15.1-8 Impostazione Scheda WebRecovery

2. Dopo la configurazione, riavviare la scatola di controllo, impostare l'IP 192.168.57.xxx e collegare il cavo alla scheda 0.
3. Accedere a "192.168.57.2:8050" per entrare nella modalità sicurezza.

.. image:: system/038.png
   :width: 3in
   :align: center

.. centered:: Figura 15.1-9 Interfaccia Modalità Sicurezza

- Importazione Pacchetto Software: aggiornamenti/rollback del sistema;
- Ripristino Lingua Predefinita: elimina le lingue importate e ripristina la lingua predefinita (inglese).
  
Dati di Guasto
~~~~~~~~~~~~~~~~~~~~

Abilitando "Salvataggio Dati Guasto", il sistema genera un file contenente i dati dei 15 secondi prima/dopo un guasto.

Dopo il salvataggio, è possibile esportare tutti i dati in system settings e decomprimere error_data.tar.gz per visualizzare i dati.

.. image:: system/039.png
   :width: 3in
   :align: center

.. centered:: Figura 15.1-10 Dati di Guasto
  
Timeout Disconnessione
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Impostare il tempo di timeout (in minuti) per la disconnessione automatica.

.. image:: system/033.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-11 Timeout Disconnessione
  
Impostazioni di Sistema
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Il ripristino alle impostazioni di fabbrica elimina i dati utente e reimposta il robot.

La generazione dei log slave e l'esportazione dei log controller permettono di scaricare file utili per il debug.

.. image:: system/034.png
   :width: 4in
   :align: center

.. centered:: Figura 15.1-12 Impostazioni di Sistema

Impostazioni Account
---------------------------

Cliccare sul sottomenu "Impostazioni Account". Solo l'amministratore può gestire gli account, suddivisi in tre moduli:

Gestione Utenti
~~~~~~~~~~~~~~~~~~~~~

La pagina gestione utenti permette di aggiungere informazioni come ID, nome e ruolo.

.. image:: system/002.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-1 Gestione Utenti

-  **Nuovo Utente**: Cliccare su "Nuovo", inserire ID, nome, password e selezionare il ruolo.

.. important::
   L'ID massimo è un numero intero di 10 cifre. ID e password devono essere unici, la password è visibile in Braille. Dopo la creazione, è possibile effettuare il login con nome e password.
  
.. image:: system/003.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-2 Nuovo Account
  
-  **Modifica Utente**: Cliccare su "Modifica" a destra, ID e nome non modificabili, password e ruolo modificabili (password uniche).
  
.. image:: system/004.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-3 Modifica Utente

-  **Elimina Utente**: Eliminazione singola o multipla.
  
  1. Cliccare su "Elimina" singolo, confermare con un secondo click.
  
  2. Selezionare utenti con checkbox e cliccare due volte su "Elimina" multiplo.

.. important::
   L'utente iniziale 111 e l'utente attuale non possono essere eliminati.

.. image:: system/002.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-4 Elimina Utente

Gestione Permessi
~~~~~~~~~~~~~~~~~~~~~

.. important:: 
   I ruoli predefiniti (codice 1-6) non possono essere eliminati o modificati nel codice, ma possono essere modificati nome, descrizione e permessi.

.. image:: system/006.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-5 Gestione Permessi

I sei ruoli predefiniti hanno permessi diversi: l'amministratore ha accesso completo, operatori e osservatori hanno accesso limitato, ingegneri ME/PE&PQE e tecnici hanno permessi parziali. Tabella dettagliata:

.. important:: 
   I permessi predefiniti sono modificabili.

.. centered:: Tabella 15.2-1 Dettagli Permessi

.. image:: system/007.png
   :width: 6in
   :align: center

-  **Nuovo Ruolo**: Cliccare su "Nuovo", inserire codice (intero positivo unico), nome e descrizione.

.. image:: system/008.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-6 Nuovo Ruolo

-  **Modifica Nome/Descrizione**: Cliccare sull'icona "Modifica" per aggiornare nome e descrizione.

.. image:: system/009.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-7 Modifica Ruolo

-  **Configura Permessi**: Cliccare sull'icona "Imposta" per definire i permessi.

.. image:: system/010.png
   :width: 6in
   :align: center

.. image:: system/011.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-8 Configura Permessi

-  **Elimina Ruolo**: Cliccare sull'icona "Elimina" dopo aver verificato che non ci siano utenti associati.

.. image:: system/012.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-9 Elimina Ruolo

Importa/Esporta
~~~~~~~~~~~~~~~~~~

.. image:: system/013.png
   :width: 6in
   :align: center

.. centered:: Figura 15.2-10 Importa/Esporta Account

-  **Importa**: Importa in massa dati utente e permessi.
-  **Esporta**: Esporta in massa dati utente e permessi.

Informazioni
--------------

Cliccare sul sottomenu "Informazioni" per visualizzare il modello, il numero seriale, le versioni software, hardware e firmware.

.. image:: system/014.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3-1 Schermata Informazioni

Aggiornamento Software
~~~~~~~~~~~~~~~~~~~~~~~~~

Preparazione
+++++++++++++++++++++++++++++++

1. Verificare la versione corrente in "Impostazioni di Sistema" > "Informazioni".
2. Scaricare il pacchetto software da "Documentazione Faao" > "Download Software", decomprimere per ottenere software.tar.gz.

Note
+++++++++++++++++++++++++++++++

1. Backup dati: Eseguire un backup prima dell'aggiornamento (vedi sezione 3.2.1).
2. Limiti di versione:

.. centered:: Tabella 15.3-1 Limiti Versione

.. list-table::
   :widths: 50 50
   :header-rows: 0
   :align: center

   * - **Versione Corrente** 
     - **Versione Massima Aggiornabile**

   * - <v3.6.1
     - v3.6.1

   * - v3.6.1-v3.6.4
     - v3.6.5

   * - v3.6.5-v3.6.8
     - v3.6.9

   * - v3.6.9 - v3.7.4
     - v3.7.5

   * - v3.7.5
     - v3.7.6

   * - ≥ v3.7.6
     - Nessun limite

3. Pulizia Cache: Dopo ogni aggiornamento, pulire la cache del browser.

Procedura
*****************************

**Aggiornamento Software**:

1. In "Impostazioni di Sistema" > "Informazioni", cliccare su "Aggiorna".

.. image:: system/040.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3-2 Interfaccia Aggiornamento

2. Cliccare su "Seleziona File" e scegliere software.tar.gz scaricato.

.. important:: 
   Il nome del pacchetto deve essere software.tar.gz. In caso di errore, rinominare il file.

3. Cliccare su "Carica" per iniziare l'aggiornamento con barra di avanzamento.

4. Al completamento (100%), il sistema indica "Aggiornamento Riuscito. Riavviare la scatola di controllo".

.. image:: system/041.png
   :width: 4in
   :align: center

.. centered:: Figura 15.3-3 Aggiornamento Riuscito

5. Riavviare la scatola di controllo e verificare la versione in "Informazioni".

**Aggiornamento Firmware**: In modalità BOOT, caricare il pacchetto e selezionare gli slave (controller, attuatori 1-6, end-effector) per l'aggiornamento.

.. image:: system/042.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3-4 Aggiornamento Firmware

**Aggiornamento Configurazione Slave**: Dopo il disabilitamento, caricare il file e selezionare gli slave per l'aggiornamento.

.. image:: system/043.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3-5 Aggiornamento Configurazione Slave

**Aggiornamento Encoder**: Dopo il disabilitamento, caricare il file e selezionare le giunture (Joint1-Joint6) con il relativo modo.

.. image:: system/044.png
   :width: 6in
   :align: center

.. centered:: Figura 15.3-6 Aggiornamento Encoder

Informazioni Personalizzate
---------------------------------

Cliccare sul sottomenu "Informazioni Personalizzate". Solo l'amministratore può caricare pacchetti utente, configurare il modello robotico e abilitare la crittografia del programma insegnatore.

.. image:: system/015.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-1 Informazioni Personalizzate

Modello Robotico
~~~~~~~~~~~~~~~~~~~

.. important::
   1. La configurazione qui è personalizzata e non coincide con "Impostazioni di Sistema" > "Modalità Manutenzione" > "Compatibilità Controller".
   2. Evitare di usare "FR" o "ART" come inizio. Se usati, il nome deve corrispondere esattamente al "Nome Breve" nella tabella modelli.

Configurazione Intervallo Parametri
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Solo l'amministratore può configurare gli intervalli dei parametri, gli altri utenti possono solo impostare valori entro tali intervalli. La configurazione avviene tramite slider o inserimento manuale.

.. important::
   Il valore massimo deve essere maggiore del minimo. Dopo la configurazione, si torna automaticamente alla pagina di login dopo 3 secondi.

.. image:: system/016.png
   :width: 6in
   :align: center

.. image:: system/022.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-2 Configurazione Intervallo Parametri

Tempo di Utilizzo Consentito
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **Impostazione Blocco Schermo**

In "Informazioni Personalizzate", abilitare/disabilitare il tempo di utilizzo. Quando abilitato, selezionare il periodo (non può essere vuoto).

.. note:: Se il blocco schermo è attivo, non è possibile riconfigurare o modificare l'ora del sistema.

Cliccare su "Configura" dopo aver selezionato il periodo.

.. image:: system/023.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-3 Tempo di Utilizzo Disattivato

.. image:: system/024.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-4 Tempo di Utilizzo Attivato

2. **Notifica Scadenza**

Quando attivo, all'avvio (5 giorni prima della scadenza) appare una notifica con i giorni rimasti, resettabile.

.. image:: system/025.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-5 Notifica Avvio

Durante l'utilizzo continuo, alle 00:00 appare la notifica.

.. image:: system/026.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-6 Notifica Utilizzo Continuo

3. **Login Sblocco**

Dopo la scadenza, al primo login si entra nella schermata di blocco. Durante l'utilizzo continuo, alle 00:00 si disconnette automaticamente. Inserire il codice di sblocco (generato dal distributore) per accedere.

.. note:: Il codice di sblocco è generato dal distributore.
 
.. image:: system/027.png
   :width: 6in
   :align: center

.. centered:: Figura 15.4-7 Schermata Blocco  

Configurazione Modello Robotico
-------------------------------------

.. important:: Per modificare il modello robotico, contattare l'ingegnere tecnico.

Dopo aver effettuato il login, in "Impostazioni di Sistema" > "Modalità Manutenzione" > "Compatibilità Controller", selezionare il modello corrispondente dalla tabella:

Tabella Modelli Robotici:

.. list-table::
   :widths: 10 58 32
   :header-rows: 0
   :align: center

   * - **Valore**
     - **Modello (Modello-Maggiore-Minore)**
     - **Nome Breve**

   * - 0
     - Non Configurato
     - /

   * - 1
     - FR3-V1-000(V5.0)
     - FR3 V5.0

   * - 2
     - FR3-V1-001(V6.0)
     - FR3 V6.0

   * - 3
     - FR3-V1-002(V6.0 Mirror)
     - FR3 V6.0(Mirror)

   * - ...
     - Riservato
     - /

   * - 101
     - FR5-V1-000
     - FR5 V4.0

   * - 102
     - FR5-V1-001(V5.0)
     - FR5 V5.0

   * - 103
     - FR5-V1-002(V6.0)
     - FR5 V6.0
     
   * - ...
     - Riservato
     - /
   
   * - 201
     - FR10-V1-000(V5.0)
     - FR10 V5.0

   * - 202
     - FR10-V1-001(V6.0)
     - FR10 V6.0
     
   * - ...
     - Riservato
     - /
   
   * - 301
     - FR16-V1-000(V5.0)
     - FR16 V5.0

   * - 302
     - FR16-V1-001(V6.0)
     - FR16 V6.0
     
   * - ...
     - Riservato
     - /
   
   * - 401
     - FR20-V1-000(V5.0)
     - FR20 V5.0

   * - 402
     - FR20-V1-001(V6.0)
     - FR20 V6.0
     
   * - ...
     - Riservato
     - /

   * - 501
     - ART3-V1-000
     - ART3
     
   * - ...
     - Riservato
     - /

   * - 601
     - ART5-V1-000
     - ART5
     
   * - ...
     - Riservato
     - /

   * - 702
     - FRCustom(7)-V1-001(FR3-WML)
     - FR3-WML

   * - 703
     - FRCustom(7)-V1-001(FR3-WMS)
     - FR3-WMS
     
   * - ...
     - Riservato
     - /
  
   * - 802
     - FRCustom(8)-V1-001(FR5WM)
     - FR5WM
        
   * - 803
     - FRCustom(8)-V1-002(FR5-WML)
     - FR5-WML
         
   * - ...
     - Riservato
     - /

   * - 901
     - FRCustom(9)-V1-001(FR3MT)
     - FR3MT

   * - 902
     - FRCustom(9)-V1-001(FR10YD)
     - FR10YD

   * - 904
     - FRCustom(9)-V1-001(FR3-C)
     - FR3-C

   * - 905
     - FRCustom(9)-V01-001(FR30L)
     - FR30L

   * - 906
     - FRCustom(9)-V01-001(FR3(C))
     - FR3(C)

   * - 907
     - FRCustom(9)-V01-001(ART3-R6-XM)
     - ART3-R6-XM

   * - 908
     - FRCustom(9)-V01-001(FC3-R6-B)
     - FC3-R6-B

   * - ...
     - Riservato
     - /

   * - 1001
     - FR30-V1-001(V6.0)
     - FR30 V6.0
     
   * - ...
     - Riservato
     - /

.. note:: Il numero maggiore ha 10 risorse (1-10), il numero minore ha 10 risorse (1-10).