Utilizzo Programmi WebAPP Robot
======================================

.. toctree:: 
    :maxdepth: 5

Impostare Caricamento Automatico Programma Operativo Predefinito all'Accensione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Impostare Caricamento Automatico Programma Operativo Predefinito all'Accensione
    * @param  [in] flag  0-non caricare automaticamente programma predefinito all'accensione, 1-caricare automaticamente programma predefinito all'accensione
    * @param  [in] program_name Nome programma operativo e percorso, es. "/fruser/" è il percorso fisso per QX, mentre "/usr/local/etc/controller/lua/" è il percorso fisso per LA.
    * @return   Codice errore
    */
    int LoadDefaultProgConfig(byte flag, string program_name); 

Caricare Programma Operativo Specificato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Caricare Programma Operativo Specificato
    * @param  [in] program_name Nome programma operativo e percorso, es. "/fruser/" è il percorso fisso per QX, mentre "/usr/local/etc/controller/lua/" è il percorso fisso per LA.
    * @return   Codice errore
    */
    int ProgramLoad(string program_name); 

Ottenere Nome Programma Operativo Caricato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Nome Programma Operativo Caricato
    * @param  [out] program_name Nome programma operativo e percorso, es. "/fruser/" è il percorso fisso per QX, mentre "/usr/local/etc/controller/lua/" è il percorso fisso per LA.
    * @return   Codice errore
    */
    int GetLoadedProgram(ref string program_name); 

Ottenere Numero Riga Esecuzione Corrente Programma Operativo Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Numero Riga Esecuzione Corrente Programma Operativo Robot
    * @param  [out] line  Numero riga
    * @return   Codice errore
    */   
    int GetCurrentLine(ref int line);

Eseguire Programma Operativo Corrente Caricato
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Eseguire Programma Operativo Corrente Caricato
    * @return   Codice errore
    */
    int ProgramRun();

Mettere in Pausa Programma Operativo Corrente in Esecuzione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Mettere in Pausa Programma Operativo Corrente in Esecuzione
    * @return   Codice errore
    */ 
    int ProgramPause();

Riprendere Programma Operativo Corrente in Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Riprendere Programma Operativo Corrente in Pausa
    * @return   Codice errore
    */ 
    int ProgramResume(); 

Terminare Programma Operativo Corrente in Esecuzione
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Terminare Programma Operativo Corrente in Esecuzione
    * @return   Codice errore
    */ 
    int ProgramStop();   

Ottenere Stato Esecuzione Programma Operativo Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    /**
    * @brief  Ottenere Stato Esecuzione Programma Operativo Robot
    * @param  [out]  state 1-programma fermo o nessun programma in esecuzione, 2-programma in esecuzione, 3-programma in pausa
    * @return   Codice errore
    */
    int GetProgramState(ref byte state);

Esempio Codice Operazioni Programma LUA Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c#
    :linenos:

    private void btnWebApp_Click(object sender, EventArgs e)
    {
        string program_name = "Text1.lua";
        string loaded_name = "";
        byte state=0;
        int line=0;

        robot.Mode(0);
        robot.LoadDefaultProgConfig(0, program_name);
        robot.ProgramLoad(program_name);
        robot.ProgramRun();
        Thread.Sleep(1000);
        robot.ProgramPause();
        robot.GetProgramState(ref state);
        Console.WriteLine("program state:{0}\n", state);
        robot.GetCurrentLine(ref line);
        Console.WriteLine("current line:{0}\n", line);
        robot.GetLoadedProgram(ref loaded_name);
        Console.WriteLine("program name:{0}\n", loaded_name);
        Thread.Sleep(1000);
        robot.ProgramResume();
        Thread.Sleep(1000);
        robot.ProgramStop();
        Thread.Sleep(1000);
    }

Scaricare File Lua
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Scaricare File Lua
    * @param [in] fileName Programma operativo da scaricare "test.lua" o "test.tar.gz"
    * @param [in] savePath Percorso locale salvataggio programma operativo "D://Down/"
    * @return Codice errore 
    */
    public int LuaDownLoad(string fileName, string savePath);

Caricare File Lua
+++++++++++++++++++++++++++++++++++
.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Caricare File Lua
    * @param [in] filePath Nome percorso programma operativo locale ".../test.lua" o ".../test.tar.gz"
    * @param [out] errStr Informazioni errore
    * @return Codice errore 
    */
    public int LuaUpload(string filePath, ref string errStr);

Eliminare File Lua
+++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Eliminare File Lua
    * @param [in] fileName Nome programma operativo da eliminare "test.lua"
    * @return Codice errore 
    */
    public int LuaDelete(string fileName);

Ottenere Nomi Tutti File Lua Correnti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    /** 
    * @brief Ottenere Nomi Tutti File Lua Correnti
    * @param [out] luaNames Lista nomi programmi operativi
    * @return Codice errore 
    */
    public int GetLuaList(ref List<string> luaNames) ;

Esempio Codice Caricamento/Scaricamento File LUA Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: C#SDK-v1.0.5

.. code-block:: c#
    :linenos:

    private void btnUploadLua_Click(object sender, EventArgs e)
    {
        int rtn;
        List<string> luaNames = new List<string>();
        rtn = robot.GetLuaList(ref luaNames);
        Console.WriteLine("res is: {0}", rtn);
        Console.WriteLine("size is: {0}", luaNames.Count);
        foreach (var name in luaNames)
        {
        Console.WriteLine(name);
        }
        rtn = robot.LuaDownLoad("TT.lua", "D://zDOWN/");
        Console.WriteLine("LuaDownLoad rtn is {0}", rtn);
        string errStr = "";
        Thread.Sleep(2000);

        rtn = robot.LuaUpload("D://zUP/airlab.lua", ref errStr);
        Console.WriteLine("LuaUpload rtn is {0}", errStr);
        Thread.Sleep(2000);
        rtn = robot.LuaDelete("TT.lua");
        Console.WriteLine("LuaDelete rtn is {0}", rtn);
    }