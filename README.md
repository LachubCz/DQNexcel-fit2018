# PGuNN - Playing Games using Neural Networks
[![Build Status](https://travis-ci.org/LachubCz/PGuNN.svg?branch=master)](https://travis-ci.org/LachubCz/PGuNN) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/a7a8e07cf66f47f7abeef7efcdea9cb7)](https://app.codacy.com/app/LachubCz/PlayingGamesUsingNeuralNetworks?utm_source=github.com&utm_medium=referral&utm_content=LachubCz/PlayingGamesUsingNeuralNetworks&utm_campaign=badger)

Application implements DQN, DQN with target network, DDQN, dueling architecture of neural network, prioritized experience replay. The training results are summarized in the file **/models/readme.md**.

**Supported environments:**

CartPole-v0, CartPole-v1, MountainCar-v0, Acrobot-v1, 2048-v0, SpaceInvaders-v0, SpaceInvaders-ram-v0, Breakout-v0, Breakout-ram-v0, BeamRider-v0, BeamRider-ram-v0

Usage
-----
**Application**
##### python3 main.py -env env -eps eps -mode mode [-alg alg] [-mem mem] [-net net] [-pu pu] [-mdl mdl] [-init] [-frames frames] [-save_f save_f] [-update_f update_f] [-vids] [-mdl_blueprint] [-dont_save]
###### Parameters:

    -env env            |  name of environment
    -eps eps            |  number of training episodes
    -mode mode          |  application mode (train, test, render)
    -alg alg            |  type of algorithm (DQN, DQN+TN, DDQN)
    -mem mem            |  type of experience replay (basic, prioritized)
    -net net            |  neural network architecture (basic, dueling)
    -pu pu              |  processing unit (CPU, GPU)
    -mdl mdl            |  existing model
    -init               |  initialization of experience replay
    -frames frames      |  number of frames which goes to neural network input (1,2,3,4)
    -save_f save_f      |  model saving frequency
    -update_f update_f  |  target network update frequency
    -vids               |  saving video
    -mdl_blueprint      |  saving pdf with blueprint of neural network
    -dont_save          |  disabling of saving any files

###### Examples

    python3 pgunn/main.py -mode train -env CartPole-v0 -eps 5000 -alg DDQN -net dueling -mem prioritized -pu CPU -init -save_f 25
    python3 pgunn/main.py -mode test -env Acrobot-v1 -eps 100 -mdl models/Acrobot-v1.h5
    python3 pgunn/main.py -mode render -env SpaceInvaders-ram-v0 -eps 200 -mdl models/SpaceInvaders-ram-v0.h5 -frames 4 -vids
**Visualization script**
##### python3 visualization.py -filename filename -graph_name graph_name -idx_val idx_val [-coordinate_x coordinate_x] [-coordinate_y coordinate_y] [-lines lines lines ...] [-scatter]
###### Parameters:

    -filename filename          |  name of file containing output from training
    -graph_name graph_name      |  name of output file containing graph
    -idx_val idx_val            |  index of column with analyzed data
    -coordinate_x coordinate_x  |  maximal showed x value in graph
    -coordinate_y coordinate_y  |  maximal showed y value in graph
    -lines lines                |  list of y values for reference constant lines 
    -scatter scatter            |  results from every round

###### Examples

    python3 pgunn/visualization.py -filename output.out -graph_name score -idx_val 6
    python3 pgunn/visualization.py -filename log.txt -graph_name results -idx_val 6 -lines 22 30 -scatter
    python3 pgunn/visualization.py -filename log.out -graph_name moves -idx_val 4 -coordinate_x 50
****
###### Created by: Petr Buchal
