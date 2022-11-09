[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/carla-simulator/scenario_runner.svg)
[![Build Status](https://travis-ci.com/carla-simulator/scenario_runner.svg?branch=master)](https://travis-ci.com/carla/scenario_runner)

ScenarioRunnerDynamic for CARLA
===============================
This repository contains the CarlaScenarioRunner 0.9.11 with all its belongings as well
as a new Scenario. Instead of running a new script for similar scenarios, the included                   
scenariory_runner_extended.py allows you to hand over a configuration id for the scenario, that varies the scenario.
 
Carla 0.9.11 is required, you can follow this installation guide to download: https://carla.readthedocs.io/en/0.9.11/start_quickstart/
Python 3.7 is needed to run the scripts as well for package installation.

Getting the ScenarioRunner
---------------------------

1.Use `git clone` or download the project from this page. 

2.Go to the Main directory.

3.Install neccesary packages for python=3.7 from requirements.txt. If Python 3.7 is your default version run "pip install -r requirements.txt".

4.Add environment variables and Pytyhon paths. These are necessary for the system to find CARLA, and add the PythonAPI to the Python path.

-For Linux 
# ${CARLA_ROOT} is the CARLA installation directory
# ${SCENARIO_RUNNER} is the ScenarioRunner installation directory
# <VERSION> is the correct string for the system and Python version being used
# In a build from source, the .egg files may be in: ${CARLA_ROOT}/PythonAPI/dist/ instead of ${CARLA_ROOT}/PythonAPI
export CARLA_ROOT=/path/to/your/carla/installation
export SCENARIO_RUNNER_ROOT=/path/to/your/scenario/runner/installation
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/carla/dist/carla-<VERSION>.egg
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI/carla
export PYTHONPATH=$PYTHONPATH:${CARLA_ROOT}/PythonAPI
    
-For Windows
# %CARLA_ROOT% is the CARLA installation directory
# %SCENARIO_RUNNER% is the ScenarioRunner installation directory
# <VERSION> is the correct string for the system and Python version being used
# In a build from source, the .egg files may be in: ${CARLA_ROOT}/PythonAPI/dist/ instead of ${CARLA_ROOT}/PythonAPI
set CARLA_ROOT=\path\to\your\carla\installation
set SCENARIO_RUNNER_ROOT=\path\to\your\scenario\runner\installation
set PYTHONPATH=%PYTHONPATH%;%CARLA_ROOT%\PythonAPI\carla\dist\carla-<VERSION>.egg
set PYTHONPATH=%PYTHONPATH%;%CARLA_ROOT%\PythonAPI\carla
set PYTHONPATH=%PYTHONPATH%;%CARLA_ROOT%\PythonAPI


If you already have a working Scenario_Runner for version 0.9.11 just add the files "scenario_runner_extended.py", "srunner/scenarios/object_crossing_walker.py" and "srunner/examples/WalkerCrossing.xml" in the matching folders.

* [Version 0.9.11](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.11) and the 0.9.11 Branch: Compatible with [CARLA 0.9.11](https://github.com/carla-simulator/carla/releases/tag/0.9.11)

Currently no build is required, as all code is in Python.


Using the new Scenario
----------------------
Note: All scripts have to be executed with python 3.7.

To start the scenario run python scenario_runner_extended.py --scenario Dynamic_Walker_Crossing_1". 
Test each scenario with manual control.  Open a new terminal and run the manual_control.py. A new window should pop up, with an ego vehicle in the middle of the street. Move forward and the leading vehicle will appear
# Inside the ScenarioRunner root directory
python manual_control.py

To get a random scenario configuration run "python scenario_runner_extended.py --scenario Dynamic_Walker_Crossing_1 --randomize".
If you want to repeat a scenario or choose a certain configuration run "python scenario_runner_extended.py --scenario Dynamic_Walker_Crossing_1 --scenario-config <id>"
    
There are four Parameters you can set or unset by handing over a four digit binary number.

Choose a Walker (***1) or a Cyclist (***0)
Choose if Person crosses Street (**1*) or stops before (**0*)
Choose if a blocker is in front of Person to limit view (*1**) or not (*0**)
Choose if a container is on the road that you have to evade before (1***) or if the road is clear (0***)

Example: Spawn a Person that crosses the road with a blocker "python scenario_runner_extended.py --scenario DynamicWalkerCrossing_1 --scenario_config 0111" (111 would work the same).

You can choose 7 different Maps with "python scenario_runner_extended.py --scenario DynamicWalkerCrossing_<Map_id>", although the first Map is the most tested version.

Conclusion
----------
The scenario_runner_extended.py allows you to run more dynamic scenarios. You can hand over a confi id that further specifies the scenario. 

Contributing
------------

Please take a look at our [Contribution guidelines](https://carla.readthedocs.io/en/latest/#contributing).


Errors
------
ImportError: DLL load failed while importing libcarla
Make sure you are running the script in python 3.7

Other ImportErrors
Check if all enviroment paths are correct


FAQ
------

If you run into other problems, check our
[FAQ](http://carla.readthedocs.io/en/latest/faq/).

License
-------

ScenarioRunner specific code is distributed under MIT License.
