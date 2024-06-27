# RomiReference

This is forked from https://github.com/robotpy/examples/tree/main/RomiReference

This repo python source code based upon [RobotPy](https://robotpy.github.io/docs/) - [RobotPy at readthedocs.io](https://robotpy.readthedocs.io/en/stable/) -
code for the [Romi]( https://github.com/robotpy/examples/tree/main/RomiReference).

Robotpy add a Python programming environment to the [WPILib](https://docs.wpilib.org/en/stable/) software
development environment for [FRC](https://www.firstinspires.org/robotics/frc) robots, for Python development. Prior to robotpy, FRC
robots were programmed in C++ or Java.

## TL;DR

For those in the "too long; didn't read" camp, here are the steps to get Python program, using RobotPy and WPILib,
controlling an Romi.  These instructions are for a Windows PC, but similar steps should work on a Linux computer or
a Mac.


### Steps

* [Download and install wpilib](https://github.com/wpilibsuite/allwpilib/releases) - TODO need to verify this step is needed with RobotPy
* Follow **some** of the steps in https://docs.wpilib.org/en/stable/docs/Romi-robot/hardware-and-imaging.html and https://Romiusersguide.readthedocs.io/en/latest/course/building.html
  * Note 1: If you follow the complete video, it uses [Romi Code from WPI (https://Romicode.wpi.edu/)](https://Romicode.wpi.edu/) 
    to test out the robot build. Which is a different development environment than
    the [FRC Control System](https://docs.wpilib.org/en/stable/) development environment firmware that these steps
    load into the Romi.
  * Note 2: Follow the [steps](https://docs.wpilib.org/en/stable/docs/romi-robot/index.html):
    * Getting Started with Romi
      * Romi Hardware, Assembly and Imaging
      * Getting to know your Romi
      * Romi Hardware Support
      * The Romi Web UI
      * But stop before "Programming the Romi"
* Make sure your computer is reconnected to the internet and not your Romi
* [Download and install Python 3.12](https://www.python.org/downloads/release/python-3122/)
* Download this repo from https://github.com/spiresfrc9106/romiReferencePython
  * If you downloaded as a zip file, unzip into a directory
  * Open a Windows PowerShell Window
    * Because RobotPy uses the `pyproject.toml` that is in `romiReferencePython` the Change directory (cd) to the directory where you downloaded and perhaps unzip `romiReferencePython`:
       ```commandline
       cd C:\Users\MikeStitt\Downloads\first\sw\romiReferencePython
       ```

       ```commandline
       pwd
       ```
    
       results in:

      ```commandline
       Path
       ----
       C:\Users\MikeStitt\Downloads\first\sw\romiReferencePython 
       ```
       for reference, a dir command
       ```commandline
       dir
       ```

       results in something like this:

       ```commandline

       Directory: C:\Users\MikeStitt\Downloads\first\sw\romiReferencePython

       Mode                 LastWriteTime         Length Name
       ----                 -------------         ------ ----
       d-----          4/7/2024  11:53 AM                commands
       d-----          4/7/2024  11:53 AM                subsystems
       d-----          4/7/2024  11:53 AM                vendordeps
       -a----          4/7/2024  11:53 AM             27 .deploy_cfg
       -a----          4/7/2024  11:53 AM             98 .gitignore
       -a----          4/7/2024  11:53 AM           1739 constants.py
       -a----          4/7/2024  11:53 AM            636 pyproject.toml
       -a----          4/7/2024  11:53 AM          14690 README.md
       -a----          4/7/2024  11:53 AM           2427 robot.py
       -a----          4/7/2024  11:53 AM            858 robotcontainer.py
       ```
    * Verify that your Python command is python 
       ```commandline
       python -VV
       Python 3.12.1 (tags/v3.12.1:2305ca5, Dec  7 2023, 22:03:25) [MSC v.1937 64 bit (AMD64)]
       ```
    * Install RobotPy
      ```commandline
      python -m pip install --upgrade pip
      python -m pip install robotpy
      python -m pip install robotpy-halsim-ws --use-deprecated=legacy-resolver
      ```
      
    * The above results in an error message like:
      ```commandline
      <- SNIP ->
      
      ERROR: pip's legacy dependency resolver does not consider dependency conflicts when selecting packages. This behaviour is the source of the following dependency conflicts.
pyntcore 2024.3.2.0 requires robotpy-wpinet==2024.3.2.0, but you'll have robotpy-wpinet 2024.3.2.1 which is incompatible.
pyntcore 2024.3.2.0 requires robotpy-wpiutil==2024.3.2.0, but you'll have robotpy-wpiutil 2024.3.2.1 which is incompatible.
robotpy 2024.3.2.1 requires robotpy-hal==2024.3.2.0, but you'll have robotpy-hal 2024.3.2.1 which is incompatible.
robotpy 2024.3.2.1 requires robotpy-wpinet==2024.3.2.0, but you'll have robotpy-wpinet 2024.3.2.1 which is incompatible.
robotpy 2024.3.2.1 requires robotpy-wpiutil==2024.3.2.0, but you'll have robotpy-wpiutil 2024.3.2.1 which is incompatible.
robotpy-halsim-gui 2024.3.2.0 requires robotpy-hal==2024.3.2.0, but you'll have robotpy-hal 2024.3.2.1 which is incompatible.
robotpy-halsim-gui 2024.3.2.0 requires robotpy-wpiutil==2024.3.2.0, but you'll have robotpy-wpiutil 2024.3.2.1 which is incompatible.
robotpy-wpimath 2024.3.2.0 requires robotpy-wpiutil==2024.3.2.0, but you'll have robotpy-wpiutil 2024.3.2.1 which is incompatible.
wpilib 2024.3.2.0 requires robotpy-hal==2024.3.2.0, but you'll have robotpy-hal 2024.3.2.1 which is incompatible.
wpilib 2024.3.2.0 requires robotpy-wpiutil==2024.3.2.0, but you'll have robotpy-wpiutil 2024.3.2.1 which is incompatible.
Successfully installed robotpy-hal-2024.3.2.1 robotpy-halsim-ws-2024.3.2.1 robotpy-wpinet-2024.3.2.1 robotpy-wpiutil-2024.3.2.1
      ```


    * From the `romiReferencePython` directory, do a RobotPy sync:
      ```commandline
      python -m robotpy sync
      10:46:36:743 INFO    : robotpy.installer   : RobotPy Installer 2024.2.2
      10:46:36:744 INFO    : robotpy.installer   : -> caching files at C:\Users\MikeStitt\wpilib\2024\robotpy
      10:46:36:756 INFO    : sync                : RobotPy version in `pyproject.toml` is '2024.3.2.1'
      10:46:37:078 INFO    : sync                : Latest version of RobotPy is '2024.3.2.1'
      10:46:37:083 INFO    : sync                : Robot project requirements:
      10:46:37:083 INFO    : sync                : - robotpy[commands2,Romi]==2024.3.2.1
      10:46:37:083 INFO    : sync                : Downloading Python for RoboRIO
  
      <- SNIP ->
  
      pip is launching in a new window to complete the installation
      ```
  * Connect a **wired-only USB** xbox controller to your PC. This can be confusing because some xbox controllers have
    a USB connector for charging, but are **wireless** xbox controller. These will not work. Logitech xbox controllers
    will work, if the switch on the back of them are switched to the "X" mode using the  "X" or "D" switch on the back
    of the controller.
  * Powerup the Romi
  * Connect to the Romi WiFi network
  * Go back to your Windows PowerShell Window.
    * This step can be confusing for those that know how to simulate and deploy to full-sized FRC robots. Use RobotPy to
      launch the WPILib simulator to control the Romi from the Windows PowerShell that is in the `romiReferencePython` directory:
      ```commandline
      python -m robotpy sim --ws-client
      ```
      resulting in:
      ```commandline
      11:16:58:836 INFO    : halsim_gui          : WPILib HAL Simulation 2024.3.2.0
      HAL Extensions: Attempting to load: halsim_gui
      Simulator GUI Initializing.
      Simulator GUI Initialized!
      HAL Extensions: Successfully loaded extension
      11:16:59:364 INFO    : Romi.extension       : WPILib Romi client 2024.3.2.0
      HAL Extensions: Attempting to load: halsim_Romi
      HALSim Romi Extension Initializing
      HALSimRomi Initialized
      HALSim Romi Extension Initialized
      HAL Extensions: Successfully loaded extension
      11:16:59:393 WARNING : pyfrc.physics       : Cannot enable physics support, C:\Users\MikeStitt\Documents\first\sw\Romi_python_minimal\physics.py not found
      11:16:59:394 INFO    : wpilib              : RobotPy version 2024.3.2.1
      11:16:59:394 INFO    : wpilib              : WPILib version 2024.3.2.0
      11:16:59:395 INFO    : wpilib              : Running with simulated HAL.
      11:16:59:402 INFO    : nt                  : Listening on NT3 port 1735, NT4 port 5810
      Not loading CameraServerShared
    
      ********** Robot program startup complete **********
      Default frc::IterativeRobotBase::RobotPeriodic() method... Override me!
      Default frc::IterativeRobotBase::SimulationPeriodic() method... Override me!
      ```
      and a "Robot Simulation" window appearing. (TODO add an image of the "Robot Simulation" window.)
  * In the "Robot Simulation", from the "System Joysticks" window, drag and drop "0: Xbox Controller" to the "Joysticks" window, "Joystick[0]" column header.
  * In the "Robot Simulation", in the "Robot Stat" window, select "Teleoperated".
  * Drive your Romi around with your xbox controller joysticks. TODO, on a Logitech controller the rotate left and right is backwards.


