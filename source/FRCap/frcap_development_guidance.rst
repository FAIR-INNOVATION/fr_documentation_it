Guida allo Sviluppo
=========================

.. toctree:: 
   :maxdepth: 6

Ambiente di Sviluppo e Requisiti
---------------------------------------------

L'ambiente di sviluppo deve soddisfare almeno le seguenti configurazioni:

- CPU: Processore 1.6 GHz o più veloce;
- RAM: >=1 GB (consigliato 2 GB o superiore);
- ROM: >=128 GB;
- SO: Richiede Windows 10 o versioni successive, macOS 10.15 o versioni successive, sistemi Linux (x64) (Ubuntu, Debian, ecc.).
- Versione del Controller: Controlla in WebApp in "Impostazioni di Sistema - Informazioni". Nota la distinzione tra QX e LA nell'ambiente di sviluppo. Ad esempio, nel contesto QX, evita l'uso di funzionalità JavaScript moderne come la sintassi ES6+.

Abbiamo incapsulato alcune interfacce e moduli, ma per ottenere un buon risultato di sviluppo, si consiglia una certa familiarità con lo sviluppo web, preferibilmente conoscendo le seguenti tecnologie:

- HTML, JavaScript/TypeScript, CSS;
- Vue3;
- Vite;
- Node.js.

Strumenti di Sviluppo
---------------------------
Raccomandiamo l'utilizzo dell'ultima versione del software Visual Studio Code (VSCode) per lo sviluppo. Per il download, visita la pagina di download ufficiale di VSCode e seleziona la versione corrispondente al tuo sistema.

Inoltre, è necessario che sul computer locale sia installato l'ambiente di runtime Node.js. L'installazione di Node.js include strumenti come npm per facilitare la gestione dei pacchetti. Visita la pagina di download ufficiale di Node.js e seleziona la versione v20 corrispondente al tuo sistema.

Per lo sviluppo in VSCode, potrebbero essere utili i seguenti plugin di VSCode, che possono essere installati e configurati secondo necessità.

- Vue;
- ESLint;
- npm Intellisense;
- Vue Language Features (Volar);
- TypeScript Vue Plugin (Volar) o Vue.volar;
- Tailwind CSS IntelliSense.

Struttura del Progetto FRCap
-----------------------------------------

Struttura dei file del progetto FRCap:

.. image:: frcap_pictures/012.png
   :width: 3in
   :align: center

.. centered:: Figura 5-1 Struttura del Progetto FRCap

- Public:

Cartella delle risorse pubbliche. I file al suo interno non vengono elaborati durante il processo di build, ma vengono semplicemente copiati integralmente nella directory di output della build.

Contiene per impostazione predefinita la cartella "action" e il file "logo.svg".

La cartella "Action" è utilizzata per memorizzare i file di logica dell'interfaccia di backend per i comandi personalizzati.

Logo.svg è l'icona del plugin.

- Src:

La cartella "Assets" è principalmente utilizzata per collocare risorse statiche.

La cartella "Components" è principalmente utilizzata per collocare componenti.

La cartella "Utils" è principalmente utilizzata per collocare classi di utilità.

App.vue contiene il codice della pagina principale.

Main.js è principalmente responsabile dell'inclusione globale delle risorse, della creazione del framework Vue, ecc.

Style.css è il file degli stili di base del progetto.

- Build.bat: Script di build per piattaforma Windows.
- Index.html: Struttura principale UI della pagina.
- Package.json: File di descrizione dei pacchetti e strategie di compilazione, ecc.
- Vite.config.js: File di configurazione di Vite.

Utilizzo di frcap-ui e frcap-api (frontend)
--------------------------------------------------------

Frcap-ui fornisce alcuni controlli HTML già incapsulati come componenti Vue, che possono essere importati nel progetto per l'uso, riducendo la difficoltà di sviluppo dell'interfaccia utente e la quantità di codice, migliorando la leggibilità del codice. Naturalmente, puoi anche scegliere alcune eccellenti librerie di componenti UI open source, come Element plus, ecc.

Prima di tutto, apri il terminale nel percorso del tuo progetto e installa frcap-ui.

.. code-block:: c++
   :linenos:

   npm install frcap-ui -s

Dopo l'installazione riuscita, importa frcap-ui nei componenti che lo richiedono, prendendo come esempio il controllo pulsante.

.. code-block:: javascript
   :linenos:

   import { AppButton } from 'frcap-ui'

Quindi utilizza l'elemento `<template>` del componente.

.. code-block:: c++
   :linenos:

   <AppButton button-text="Start" button-type="primary"></AppButton>

Anteprima dell'effetto del progetto di sviluppo nel browser.

.. image:: frcap_pictures/009.png
   :width: 6in
   :align: center

.. centered:: Figura 5-2 Effetto AppButton

Attualmente forniamo 4 componenti di controllo comuni.

- AppButton: Componente pulsante.
  
  - buttonType: Tipo di pulsante, String, corrispondente a diversi stili di pulsante, predefinito è primary.
  
    - primary: blu;
    - secondery: grigio;
    - safety: verde;
    - warning: giallo;
    - serious: rosso.
  
  - buttonText: Testo del pulsante, String, valore predefinito "primary".

- AppInput: Componente di input.
  
  - Type: Obbligatorio, String, valore predefinito text. Indica il tipo di campo di input.
  
    - Number: campo di input numerico;
    - Text: campo di input di testo.
  
  - inputLabel: Obbligatorio, String, testo dell'etichetta del campo di input.
  - inputUnit: String, testo dell'unità del campo di input.
  - hasUnit: Boolean, predefinito false, indica se è necessario il testo dell'unità.
  - isEmptyErr: Boolean, indica se il campo di input è vuoto.
  - isReadonly: Boolean, indica se il campo di input è di sola lettura.

- AppSelect: Componente di selezione (select box).
  
  - selectionLabel: Obbligatorio, String, testo dell'etichetta del box di selezione.
  - optionsData: Obbligatorio, Array, dati delle opzioni.

- Modal: Componente finestra modale.
  
  - show: Boolean, indica se far apparire la finestra modale.
  - title: String, titolo della finestra modale.

Per facilitare lo sviluppo di comandi personalizzati che potrebbero essere creati in FRCap, abbiamo integrato le richieste HTTP e le API nel progetto FRCap iniziale scaricato tramite la "Creazione guidata". In questo modo, sia i comandi personalizzati che quelli forniti di default possono essere inseriti nel file api.js di frcap-api. Il percorso specifico di api.js è "./src/api/api.js".

L'utilizzo di Frcap-api è simile a quello di frcap-ui, come di seguito:

1. Importa api nel file (come un componente) che necessita di utilizzare le API.

.. code-block:: javascript
   :linenos:

   import api from '@/api/api';

2. Chiama i comandi forniti di default nell'interfaccia.

.. code-block:: c++
   :linenos:

   api.getRobotStatus()

3. Scrivi la logica di elaborazione nella promise restituita.

.. code-block:: c++
   :linenos:

    api.getRobotStatus()
    .then((res) => {
    console.log(res.data);
    })
    .catch((err) => {
        console.error(err);
    });

Sviluppo di Comandi Personalizzati (Backend)
--------------------------------------------------------

Esempio di Operazione su Database (LA)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1. Importa il modulo del database

.. code-block:: javascript
   :linenos:

    var node = "/usr/local/etc/node/sys"
    var Sqlite3_Action = require(node + '/better-sqlite3/better-sqlite3.js');
    var sqlite = new Sqlite3_Action();

2. Ottieni i contenuti dal database dei punti (positions)
   
.. code-block:: javascript
   :linenos:

    // Corrispondenza cmd
    case 'get_points':
    // Scrivi l'istruzione SQL, ordina i dati in ordine numerico crescente + ordine alfabetico iniziale crescente + ordine alfabetico cinese iniziale crescente, e restituiscili alla pagina frontend per la visualizzazione
    var sql = "select * from points order by name ASC"; 
    var sql_data = sqlite.queryall(DB_POINTS, sql); 
    // Formattazione dei dati JSON
    for (var i = 0; i < sql_data.length; i++) {
        response_data[sql_data[i].name] = sql_data[i];
    }
    // Restituisci i dati JSON al frontend
    event_socket.emit('response', res, response_status, response_data);
    break;  

Esempio di Operazione su Database (QX)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. note:: La versione QX utilizza file in formato JSON per memorizzare i dati.

1. Importa il modulo del database

.. code-block:: javascript
   :linenos:

   var node = "/usr/local/etc/node/sys"
   var sqlite_adapter = require(node + '/jsdb/sqlite_adapter');
   var db = new sqlite_adapter.Database(palletizing_db);

2. Esempio di utilizzo del database
   
.. code-block:: javascript
   :linenos:

   // Esegui una query SELECT e ottieni tutte le righe
   var rows = db.queryall('SELECT * FROM box_cfg');
   console.log('result:', rows);

   // Esegui una query SELECT e ottieni una singola riga
   var row = db.queryget('SELECT * FROM box_cfg WHERE flag=1');
   console.log('result:', row);

   // Esegui un'istruzione UPDATE
   db.run('UPDATE box_cfg SET height=100 WHERE flag=1', function(err) {
      if (err) {
         console.error('Update failed:', err);
      } else {
         console.log('Update success');
      }
   });

   // Esegui una query con parametri
   var params = [100, 200, 300, 1];
   db.run('UPDATE box_cfg SET height=?, width=?, length=? WHERE flag=?', params, function(err) {
      if (err) {
         console.error('update failed:', err);
      } else {
         console.log('update success');
      }
   });

   // Chiudi la connessione al database
   db.close();

Esempio di Operazione di Comunicazione Socket
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

- Importa il modulo di comunicazione socket
   
.. code-block:: javascript
   :linenos:

    var node = "/usr/local/etc/node/sys"
    var Socket_Cmd = require(node + '/socket/socket_cmd');
    var socket_cmd = new Socket_Cmd();

- Invia un comando per impostare una variabile di sistema
  
.. code-block:: javascript
   :linenos:

   // Corrispondenza cmd
   case 511:
   // Ottieni il contenuto dei dati da inviare
   content = data_json.content;
   // Ottieni la lunghezza dei dati da inviare
   len = data_json.content.length;
   // Assemblea i dati da inviare
   send_content = '/f/bIII1III511III' + len + 'III' + content + 'III/b/f'
   // Invio socket
   socket_cmd.send(send_content);
   // Ricezione socket (nota la distinzione LA/QX)
   // Versione LA:
   socket_cmd.recv().then((recv_data)=>{
      response_data = recv_data;
   event_socket.emit('response', res, response_status, response_data);
   }).catch((err)=>{
      console.log(err);
   })
   // Versione QX 
   // socket_cmd.recv().then(function(recv_data){
   //     response_data = recv_data;
   // event_socket.emit('response', res, response_status, response_data);
   // }).catch (function(err){
   //     console.log(err);
   // })
   break;