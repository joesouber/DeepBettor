# XGBoost_TBBE

### This is code for A Deep Learning Based model in In-Play Betting on a Sports Betting Exchange dissertation 

It is the extended version from Multi-threaded BBE (Bristol Betting Exchange) integrated with Opinion Dynamics Platform with an XGBoost Agent (https://github.com/ChawinT/XGBoost_TBBE). 


Basic steps for running the BBE (Bristol Betting Exchange): 
1. In config.py -> Initialize the agents list. Below is the example of agents list:
   agents = [('Agent_Opinionated_Random', 10), ('Agent_Opinionated_Leader_Wins', 10),
          ('Agent_Opinionated_Underdog', 10),('Agent_Opinionated_Back_Favourite',10),
          ('Agent_Opinionated_Linex', 10), ('Agent_Opinionated_Priviledged', 5),
          ('XGBoostBettingAgent', 5)]

This will be the agent configuration that system uses when running the simulation. 

2. In systems_constant.py defines parameters/settings of the simulations. Example of parameters  systems_constant.py:

   -> General

  NUM_OF_SIMS = 1000
  NUM_OF_COMPETITORS = 5
  NUM_OF_EXCHANGES = 1
  PRE_RACE_BETTING_PERIOD_LENGTH = 0
  IN_PLAY_CUT_OFF_PERIOD = 0
  SESSION_SPEED_MULTIPLIER = 1

  -> Exchange Attributes
  MIN_ODDS = 1.1
  MAX_ODDS = 20.00

  -> Event Attributes
  RACE_LENGTH = 500
  MIN_RACE_LENGTH = 400
  MAX_RACE_LENGTH = 4000

3. Once you have decided on the race configuration and parameters, I have implemented an optional technqiue to generate data accross multiple CPU cores. The files "createcores" and "launch8cores" are designed to be executed in a terminal and can be edited to be specific to your enviroment.

4. In the terminal run createcores with the command "./createcores". This creates 8 directories within your environment for each CPU core you wish to utilise. It also copies the repository into each core.

5. Then run launch8cores via "./launch8cores". This runs the TBBE.py file within each core in parallel. The benefit of this is as follows: Say you want to run 800 simulations, but your laptop CPU does not have the processing power and will take many hours to run this job (an m1 mac core will take upwards of 30 hours to run this). By initiating all 8 cores you can configure the session to only run 100 simulations, with each core running 100 simulations. This means 800 simulations are run in a fraction of the time via this parallel processing method. 



6. After the session finished, results will be available in data folder. Many result files will be generated. Please look at session_stats.py file for how each file is generated. 



### This github doens't contain data files due to a large files size. The training data can be collect from running sessions in https://github.com/ChawinT/XGBoost_TBBE using the setup in the dissertation. 

  

  





