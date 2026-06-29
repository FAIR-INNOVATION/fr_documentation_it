Utilizzo del Programma WebAPP del Robot
==============================================

.. toctree:: 
    :maxdepth: 5

Impostazione Caricamento Automatico Programma Lavoro Predefinito all'Accensione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Imposta il caricamento automatico del programma lavoro predefinito all'accensione
    * @param  [in] flag  0-Non carica automaticamente il programma predefinito all'accensione, 1-Carica automaticamente il programma predefinito all'accensione
    * @param  [in] program_name Nome e percorso del programma lavoro, es. "movej.lua"
    */
    int LoadDefaultProgConfig(int flag, String program_name);

Caricamento Programma Lavoro Specificato
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Carica il programma lavoro specificato
    * @param  [in] program_name Nome e percorso del programma lavoro, es. "movej.lua"
    * @return  Codice errore
    */
    int ProgramLoad(String program_name);

Ottenimento Nome Programma Lavoro Caricato
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il nome del programma lavoro caricato
    * @param  [out] program_name program_name[0]: Nome e percorso del programma lavoro, es. "movej.lua"
    * @return  Codice errore
    */
    int GetLoadedProgram(String[] program_name);

Ottenimento Numero di Riga Esecuzione Corrente Programma Lavoro Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene il numero di riga in esecuzione del programma lavoro corrente del robot
    * @param  [out] List[0]: Codice errore; List[1]: int line numero di riga
    * @return  Codice errore
    */   
    List<Integer> GetCurrentLine();

Esecuzione Programma Lavoro Corrente Caricato
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Esegue il programma lavoro corrente caricato
    * @return  Codice errore
    */
    int ProgramRun();

Sospensione Programma Lavoro Corrente in Esecuzione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Sospende il programma lavoro corrente in esecuzione
    * @return  Codice errore
    */ 
    int PauseMotion();

Ripresa Programma Lavoro Corrente Sospeso
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Riprende il programma lavoro corrente sospeso
    * @return  Codice errore
    */ 
    int ResumeMotion();

Terminazione Programma Lavoro Corrente in Esecuzione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Termina il programma lavoro corrente in esecuzione
    * @return  Codice errore
    */ 
    int StopMotion();

Ottenimento Stato di Esecuzione Programma Lavoro Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /**
    * @brief  Ottiene lo stato di esecuzione del programma lavoro del robot
    * @param   [out] state 1-Programma fermo o nessun programma in esecuzione, 2-Programma in esecuzione, 3-Programma sospeso
    * @return  Codice errore
    */
    public int GetProgramState(int[] state);

Esempio di Codice per Operazioni Programmi LUA Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLuaOp(Robot robot)
    {
        String program_name = "Text1.lua";
        String[] loaded_name = new String[]{""};
        int[] state = new int[]{0};
        List<Integer> line = new ArrayList<>();

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        robot.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(state);
        System.out.println("program state:" + state[0]);
        line = robot.GetCurrentLine();
        System.out.println("current line:" + line);
        robot.GetLoadedProgram(loaded_name);
        System.out.println("program name:" + loaded_name[0]);
        robot.Sleep(1000);
        robot.ProgramResume();
        robot.Sleep(1000);
        robot.ProgramStop();
        robot.Sleep(1000);

        robot.CloseRPC();
        return 0;
    }

Download Programma Lua
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Scarica il programma lavoro
    * @param [in] fileName Nome del file Lua da scaricare "test.lua" o "test.tar.gz"
    * @param [in] savePath Percorso locale di salvataggio file "D://Down/"
    * @return Codice errore 
    */
    int LuaDownLoad(String fileName, String savePath);

Eliminazione Programma Lua
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Elimina il programma lavoro
    * @param [in] fileName Nome del programma lavoro da eliminare "test.lua"
    * @return Codice errore 
    */
    int LuaDelete(String fileName);

Ottenimento Nomi Tutti i File Lua Correnti
+++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Ottiene i nomi di tutti i file Lua correnti
    * @param [out] luaNames Lista nomi programmi lavoro
    * @return Codice errore 
    */
    int GetLuaList(List<String> luaNames);

Upload Programma Lua
+++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    /** 
    * @brief Carica il programma lavoro
    * @param [in] filePath Percorso del file Lua locale ".../test.lua" o ".../test.tar.gz"
    * @param [out] errStr Informazione errore
    * @return Codice errore 
    */
    int LuaUpload(String filePath, String errStr);

Esempio di Codice per Upload/Download File LUA Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: Java
    :linenos:

    public static int TestLUAUpDownLoad(Robot robot)
    {
        List<String> luaNames = new ArrayList<>();
        int rtn = robot.GetLuaList(luaNames);
        System.out.println("res is: " + rtn);
        System.out.println("size is: " + luaNames.size());
        for (int it = 1; it < luaNames.size(); it++)
        {
            System.out.println(luaNames.get(it));
        }

        rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
        System.out.println("LuaDownLoad rtn is:" + rtn);

        rtn = robot.LuaUpload("D://zUP/XG.lua","");
        System.out.println("LuaUpload rtn is:" + rtn);

        rtn = robot.LuaDelete("XG.lua");
        System.out.println("LuaDelete rtn is:" + rtn);

        return 0;
    }