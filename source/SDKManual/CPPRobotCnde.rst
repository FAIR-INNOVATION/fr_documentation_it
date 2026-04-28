CNDE
=============

.. toctree:: 
    :maxdepth: 5

Configurare il Feedback di Stato CNDE del Robot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Configurare il feedback di stato CNDE del robot
    * @param [in] states Elenco degli stati configurabili
    * @param [in] period Periodo di feedback dello stato
    * @return Codice di errore
    */
    errno_t SetRobotRealtimeStateConfig(std::vector<RobotState> states, int period);
    
Aggiungere uno Stato del Robot alla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Aggiungere uno stato del robot alla configurazione di stato CNDE
    * @param [in] state Stato configurabile
    * @return Codice di errore
    */
    errno_t AddRobotRealtimeState(RobotState state);
        
Eliminare uno Stato del Robot dalla Configurazione di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Eliminare uno stato del robot dalla configurazione di stato CNDE
    * @param [in] state Stato configurabile
    * @return Codice di errore
    */
    errno_t DeleteRobotRealtimeState(RobotState state);
            
Impostare il Periodo di Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Impostare il periodo di feedback di stato CNDE
    * @param [in] period Periodo di feedback di stato configurabile 4-1000ms
    * @return Codice di errore
    */
    errno_t SetRobotRealtimeStatePeriod(int period);
                
Ottenere l'Insieme Completo di Stati e il Periodo dell'Attuale Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    /**
    * @brief Ottenere l'insieme completo di stati e il periodo dell'attuale feedback di stato CNDE
    * @param [out] states Elenco degli stati configurabili
    * @param [out] period Periodo di feedback di stato configurabile
    * @return Codice di errore
    */
    errno_t GetRobotRealtimeStateConfig(std::vector<RobotState>& states, int& period);
                
Esempio di Codice per l'Utilizzo del Feedback di Stato CNDE
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. code-block:: c++
    :linenos:

    int PrintRobotPosVelTorque() 
    {
        ROBOT_STATE_PKG pkg = {};
        FRRobot robot;
        int rtn = 0;
        robot.LoggerInit();
        robot.SetLoggerLevel(1);
        std::vector<RobotState> states = { RobotState::JointCurPos, RobotState::TargetJointPos,
        RobotState::ToolCurPos, RobotState::TargetTCPPos,
        RobotState::FlangeCurPos, RobotState::ActualTCPForce,
        RobotState::ActualJointVel, RobotState::TargetJointVel,
        RobotState::ActualJointAcc, RobotState::TargetJointAcc,
        RobotState::TargetTCPCmpSpeed, RobotState::ActualTCPCmpSpeed,
        RobotState::TargetTCPSpeed, RobotState::ActualTCPSpeed,
        RobotState::ActualJointTorque, RobotState::JointDriverTorque, RobotState::TargetJointTorque,
        RobotState::TargetJointCurrent, RobotState::ActualJointCurrent };
        rtn = robot.SetRobotRealtimeStateConfig(states, 8);
        rtn = robot.RPC("192.168.58.2");
        if (rtn != 0)
        {
            printf("robot RPC failed\n");
            return 0;
        }
        robot.SetReConnectParam(true, 30000, 500);
        std::vector<RobotState> getConfigState = {};
        int getPeriod = 0;
        rtn = robot.GetRobotRealtimeStateConfig(getConfigState, getPeriod);
        printf("GetRobotRealtimeStateConfig rtn is %d; period is %d\n", rtn, getPeriod);
        for (int k = 0; k < getConfigState.size(); k++)
        {
            printf("getConfigState include %d\n", getConfigState[k]);
        }
        while (true)
        {
            robot.GetRobotRealTimeState(&pkg);
            printf("joint actual pos is %f %f %f %f %f %f\n", pkg.jt_cur_pos[0], pkg.jt_cur_pos[1], pkg.jt_cur_pos[2], pkg.jt_cur_pos[3], pkg.jt_cur_pos[4], pkg.jt_cur_pos[5]);
            printf("joint target pos is %f %f %f %f %f %f\n", pkg.targetJointPos[0], pkg.targetJointPos[1], pkg.targetJointPos[2], pkg.targetJointPos[3], pkg.targetJointPos[4], pkg.targetJointPos[5]);
            printf("tool actual pos is %f %f %f %f %f %f\n", pkg.tl_cur_pos[0], pkg.tl_cur_pos[1], pkg.tl_cur_pos[2], pkg.tl_cur_pos[3], pkg.tl_cur_pos[4], pkg.tl_cur_pos[5]);
            printf("tool target pos is %f %f %f %f %f %f\n", pkg.targetTCPPos[0], pkg.targetTCPPos[1], pkg.targetTCPPos[2], pkg.targetTCPPos[3], pkg.targetTCPPos[4], pkg.targetTCPPos[5]);
            printf("joint actual velocity is %f %f %f %f %f %f\n", pkg.actual_qd[0], pkg.actual_qd[1], pkg.actual_qd[2], pkg.actual_qd[3], pkg.actual_qd[4], pkg.actual_qd[5]);
            printf("joint target velocity is %f %f %f %f %f %f\n", pkg.targetJointVel[0], pkg.targetJointVel[1], pkg.targetJointVel[2], pkg.targetJointVel[3], pkg.targetJointVel[4], pkg.targetJointVel[5]);
            printf("joint actual acc is %f %f %f %f %f %f\n", pkg.actual_qdd[0], pkg.actual_qdd[1], pkg.actual_qdd[2], pkg.actual_qdd[3], pkg.actual_qdd[4], pkg.actual_qdd[5]);
            printf("joint target acc is %f %f %f %f %f %f\n", pkg.targetJointAcc[0], pkg.targetJointAcc[1], pkg.targetJointAcc[2], pkg.targetJointAcc[3], pkg.targetJointAcc[4], pkg.targetJointAcc[5]);
            printf("tcp actual cmp speed is %f %f\n", pkg.actual_TCP_CmpSpeed[0], pkg.actual_TCP_CmpSpeed[1]);
            printf("tcp target cmp speed is %f %f\n", pkg.target_TCP_CmpSpeed[0], pkg.target_TCP_CmpSpeed[1]);
            printf("tcp actual velocity is %f %f %f %f %f %f\n", pkg.actual_TCP_Speed[0], pkg.actual_TCP_Speed[1], pkg.actual_TCP_Speed[2], pkg.actual_TCP_Speed[3], pkg.actual_TCP_Speed[4], pkg.actual_TCP_Speed[5]);
            printf("tcp target velocity is %f %f %f %f %f %f\n", pkg.target_TCP_Speed[0], pkg.target_TCP_Speed[1], pkg.target_TCP_Speed[2], pkg.target_TCP_Speed[3], pkg.target_TCP_Speed[4], pkg.target_TCP_Speed[5]);
            printf("joint actual torque is %f %f %f %f %f %f\n", pkg.jt_cur_tor[0], pkg.jt_cur_tor[1], pkg.jt_cur_tor[2], pkg.jt_cur_tor[3], pkg.jt_cur_tor[4], pkg.jt_cur_tor[5]);
            printf("joint driver torque is %f %f %f %f %f %f\n", pkg.jointDriverTorque[0], pkg.jointDriverTorque[1], pkg.jointDriverTorque[2], pkg.jointDriverTorque[3], pkg.jointDriverTorque[4], pkg.jointDriverTorque[5]);
            printf("joint target torque is %f %f %f %f %f %f\n", pkg.jt_tgt_tor[0], pkg.jt_tgt_tor[1], pkg.jt_tgt_tor[2], pkg.jt_tgt_tor[3], pkg.jt_tgt_tor[4], pkg.jt_tgt_tor[5]);
            printf("joint actual current is %f %f %f %f %f %f\n", pkg.actualJointCurrent[0], pkg.actualJointCurrent[1], pkg.actualJointCurrent[2], pkg.actualJointCurrent[3], pkg.actualJointCurrent[4], pkg.actualJointCurrent[5]);
            printf("joint target current is %f %f %f %f %f %f\n", pkg.targetJointCurrent[0], pkg.targetJointCurrent[1], pkg.targetJointCurrent[2], pkg.targetJointCurrent[3], pkg.targetJointCurrent[4], pkg.targetJointCurrent[5]);
            printf("flange actual pos is %f %f %f %f %f %f\n", pkg.flange_cur_pos[0], pkg.flange_cur_pos[1], pkg.flange_cur_pos[2], pkg.flange_cur_pos[3], pkg.flange_cur_pos[4], pkg.flange_cur_pos[5]);
            printf("tcp actual force is %f %f %f %f %f %f\n\n", pkg.actualTCPForce[0], pkg.actualTCPForce[1], pkg.actualTCPForce[2], pkg.actualTCPForce[3], pkg.actualTCPForce[4], pkg.actualTCPForce[5]);
            robot.Sleep(300);
        }
        robot.Sleep(1000);
        robot.CloseRPC();
        robot.Sleep(1000);
        return 0;
    }