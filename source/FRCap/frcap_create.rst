Creazione Guidata
=========================

.. toctree::
   :maxdepth: 6

"Creazione Guidata" è uno strumento in FRCap-Tools. Attraverso questo strumento, è possibile inizializzare rapidamente e facilmente un progetto FRCap inserendo pochi parametri.

Configurazione Parametri
-------------------------------

La creazione di un FRCap richiede principalmente due tipi di parametri: le informazioni di base del FRCap e le configurazioni a vari livelli. Questi verranno spiegati separatamente di seguito.

Informazioni Base
+++++++++++++++++++++++++++

Le informazioni di base includono "Nome Plugin", "Autore Plugin" e "Descrizione Plugin".

Nome Plugin:

- Campo obbligatorio;
- Nessuna restrizione su caratteri o lunghezza di input, non sono ammessi spazi;
- Si consiglia che il nome non superi i 7 caratteri CJK (Cinese, Giapponese, Coreano, ecc.) o 10 lettere latine maiuscole o 14 lettere latine minuscole (Inglese, Francese, ecc.);
- Esempi consigliati:

  - Palletizer Palletizer;
  - Software Processo Smerigliatura;
  - Configurazione Dispositivo;
  - HELLO FRCAP.

Autore Plugin:

- Campo obbligatorio;
- Nessuna restrizione su caratteri o lunghezza di input, ad esempio è possibile inserire il proprio nome personale, nome dell'azienda, ecc.;
- Esempi consigliati:

  - Zhang San
  - Franklin Peter
  - Fairino Innovation (Suzhou) Robot Systems Co., Ltd.

Descrizione Plugin:

- Campo opzionale;
- Nessuna restrizione su caratteri o lunghezza di input, basta descrivere brevemente il proprio plugin.

Configurazione Avanzata
------------------------------------

Tipo Plugin:

- Campo obbligatorio;
- Le opzioni di tipo sono "Configurazione" e "Applicazione".
- "Configurazione" è consigliato per FRCap che implementano configurazioni relativamente semplici come impostazione di parametri, operazioni con pulsanti, ecc. Dopo l'importazione, sarà utilizzabile in "Applicazioni Ausiliarie" -> "FRCap" nel WebApp.
- "Applicazione" è consigliato per FRCap che implementano scenari di processo complessi, come applicazioni di settore per pallettizzazione, saldatura, ecc. Dopo l'importazione, sarà utilizzabile direttamente sotto "Applicazioni Ausiliarie" nel WebApp.

Icona Plugin:

- Campo opzionale;
- È possibile caricare il logo dell'azienda o qualsiasi icona si desideri utilizzare. Prestare attenzione alle questioni di copyright; questa società non si assume alcuna responsabilità per problemi di copyright derivanti da qualsiasi causa;
- Se non si carica un'icona, nel progetto FRCap esportato verrà utilizzata per impostazione predefinita l'icona del logo "FAIRINO". È possibile sostituirla/modificarla nella cartella "public" del progetto. Questa icona è solo per scopi illustrativi iniziali; non utilizzare direttamente il logo "FAIRINO" in alcuno scenario commerciale.

Download
-------------
Dopo aver completato tutte le configurazioni dei parametri sopra descritte e dopo la creazione riuscita del FRCap, si verrà reindirizzati alla pagina di download. È necessario confermare che il nome sia corretto per scaricare il progetto FRCap creato sul proprio computer locale per lo sviluppo successivo e l'utilizzo in fase di build.

Il plugin scaricato è in formato compresso ".tar.gz".

Su sistemi Windows consigliamo di utilizzare il software 7-Zip per l'estrazione.

Su sistemi Linux è possibile estrarre utilizzando il seguente comando nel terminale.

.. code-block:: c++
   :linenos:

    tar -zxvf frcap_{NomeFRCap}.tar.gz