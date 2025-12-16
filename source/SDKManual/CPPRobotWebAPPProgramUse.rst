Uso Programmi WebAPP Robot
==========================

.. toctree:: 
    :maxdepth: 5

Impostare Caricamento Automatico Programma Lavoro Predefinito all'Avvio
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Imposta il caricamento automatico del programma lavoro predefinito all'avvio
    * @param  [in] flag  0-non carica automaticamente programma predefinito all'avvio, 1-carica automaticamente programma predefinito all'avvio
    * @param  [in] program_name  Nome programma lavoro e percorso, es. "/fruser/movej.lua", dove "/fruser/" è percorso fisso QX, "/usr/local/etc/controller/lua/" è percorso fisso LA
    * @return  Codice errore
    */
    errno_t  LoadDefaultProgConfig(uint8_t flag, char program_name[64]);

Caricare Programma Lavoro Specificato
++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Carica il programma lavoro specificato
    * @param  [in] program_name  Nome programma lavoro e percorso, es. "/fruser/movej.lua", dove "/fruser/" è percorso fisso QX, "/usr/local/etc/controller/lua/" è percorso fisso LA
    * @return  Codice errore
    */
    errno_t  ProgramLoad(char program_name[64]);

Ottenere Nome Programma Lavoro già Caricato
++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene il nome del programma lavoro già caricato
    * @param  [out] program_name  Nome programma lavoro e percorso, es. "/fruser/movej.lua", dove "/fruser/" è percorso fisso QX, "/usr/local/etc/controller/lua/" è percorso fisso LA
    * @return  Codice errore
    */
    errno_t  GetLoadedProgram(char program_name[64]);  

Ottenere Numero di Linea di Esecuzione del Programma Lavoro Corrente del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene il numero di linea di esecuzione del programma lavoro corrente del robot
    * @param  [out] line  Numero linea
    * @return  Codice errore
    */   
    errno_t  GetCurrentLine(int *line);

Eseguire Programma Lavoro Attualmente Caricato
+++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Esegue il programma lavoro attualmente caricato
    * @return  Codice errore
    */
    errno_t  ProgramRun();

Mettere in Pausa Programma Lavoro Attualmente in Esecuzione
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Mette in pausa il programma lavoro attualmente in esecuzione
    * @return  Codice errore
    */ 
    errno_t  ProgramPause();

Riprendere Programma Lavoro Attualmente in Pausa
+++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Riprende il programma lavoro attualmente in pausa
    * @return  Codice errore
    */ 
    errno_t  ProgramResume();  

Terminare Programma Lavoro Attualmente in Esecuzione
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Termina il programma lavoro attualmente in esecuzione
    * @return  Codice errore
    */ 
    errno_t  ProgramStop();    

Ottenere Stato di Esecuzione Programma Lavoro Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief  Ottiene lo stato di esecuzione del programma lavoro del robot
    * @param  [out]  state 1-programma fermo o nessun programma in esecuzione, 2-programma in esecuzione, 3-programma in pausa
    * @return  Codice errore
    */
    errno_t  GetProgramState(uint8_t *state);

Esempio di Codice Operazioni su Programmi LUA Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int TestLuaOp(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      char program_name[64] = "/fruser/test.lua";
      char loaded_name[64] = "";
      uint8_t state;
      int line;
      robot.Mode(0);
      robot.LoadDefaultProgConfig(0, program_name);
      robot.ProgramLoad(program_name);
      robot.ProgramRun();
      robot.Sleep(1000);
      robot.ProgramPause();
      robot.GetProgramState(&state);
      printf("program state:%u\n", state);
      robot.GetCurrentLine(&line);
      printf("current line:%d\n", line);
      robot.GetLoadedProgram(loaded_name);
      printf("program name:%s\n", loaded_name);
      robot.Sleep(1000);
      robot.ProgramResume();
      robot.Sleep(1000);
      robot.ProgramStop();
      robot.Sleep(1000);
      robot.CloseRPC();
      return 0;
    }

Scaricare File Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Scarica file Lua
    * @param [in] fileName Nome file lua da scaricare, es.: "test.lua"
    * @param [in] savePath Percorso locale per salvare il file, es.: "D://Down/"
    * @return Codice errore
    */
    errno_t LuaDownLoad(std::string fileName, std::string savePath);

Eliminare File Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Elimina file Lua
    * @param [in] fileName Nome file lua da eliminare, es.: "test.lua"
    * @return Codice errore
    */
    errno_t LuaDelete(std::string fileName);

Ottenere Nomi di Tutti i File Lua Correnti
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Ottiene i nomi di tutti i file Lua attuali
    * @param [out] luaNames Lista nomi file lua
    * @return Codice errore
    */
    errno_t GetLuaList(std::list<std::string>* luaNames);

Caricare File Lua
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. versionadded:: C++SDK-v2.1.2.0

.. code-block:: c++
    :linenos:

    /**
    * @brief Carica file Lua
    * @param [in] filePath Percorso nome file lua locale
    * @return Codice errore
    */
    errno_t LuaUpload(std::string filePath);

Esempio di Codice Caricamento e Scaricamento File LUA Robot
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. code-block:: c++
    :linenos:

    int TestLUAUpDownLoad(void)
    {
      ROBOT_STATE_PKG pkg = {};
      FRRobot robot;
      robot.LoggerInit();
      robot.SetLoggerLevel(1);
      int rtn = robot.RPC("192.168.58.2");
      if (rtn != 0)
      {
        return -1;
      }
      robot.SetReConnectParam(true, 30000, 500);
      list<std::string> luaNames;
      rtn = robot.GetLuaList(&luaNames);
      std::cout << "res is: " << rtn << std::endl;
      std::cout << "size is: " << luaNames.size() << std::endl;
      for (auto it = luaNames.begin(); it != luaNames.end(); it++)
      {
        std::cout << it->c_str() << std::endl;
      }
      rtn = robot.LuaDownLoad("test.lua", "D://zDOWN/");
      printf("LuaDownLoad rtn is %d\n", rtn);
      rtn = robot.LuaUpload("D://zUP/airlab.lua");
      printf("LuaUpload rtn is %d\n", rtn);
      rtn = robot.LuaDelete("test.lua");
      printf("LuaDelete rtn is %d\n", rtn);
      robot.CloseRPC();
      return 0;
    }