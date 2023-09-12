# EMC2_project
The parent repo of the Easy Motor Control (EMC2) project.

One of the problems faced by students, learners, researchers, hobbyists, and even some startups in Wheeled Mobile Robotics is **motor velocity control** and the most popular method of handling this problem is to use the **PID controller**. 

Traditionally, DC motors are controlled using PWM signals via an H-Bridge driver module which does not really provide option for good velocity control of the connected motor with feedback. This generally makes it hard to design good **motor velocity PID controller** for the interfaced motor, not to mention implementing good motion planning algorithms on the mobile robot. Because of this, most mobile robotics projects revolves around (or are usually limited to) Telemetry operation, obstacle avoidance, line following, Opencv lane tracking/following (sometimes with AI), and so on or such that does not require any advanced motion planning and navigation algorithms like SLAM and so on.

What if you could get a **motor driver system** that allows you to:
 - easily connect/interface any geared dc motor with a quadrature encoder to it.
 - easily setup the motor encoder and configure a velocity PID control for the connected/interfaced motor.
 - contol the motor directly with angular velocity commands (not PWM).
 - get the motor’s actual angular position and angular velocity as feedback.
 - easily integrate it into your microcontroller-based (Arduino) project.
 - easily integrate it into your microcomputer-based (Raspberry Pi, etc.) project.
 - easily integrate it into your ROS2-based project in wheeled mobile robotics.

This is exactly what the EMC2 does. 

The EMC2 system consists of a **motor driver module shield** (to be used with Arduino nano or UNO) and a [**GUI application**](https://github.com/samuko-things/EMC2_gui_application) (which works with the motor driver module) to help set up the encoder and velocity PID control of any **geared DC motor with a quadrature encoder**.


It also provides an [**i2c communication interface API arduino library**](https://github.com/samuko-things/EMC2_arduino_i2c_comm) for easy use of the motor driver module with other Arduino based 8-bit or 32-bit microcontrollers as well as a [**Python serial communication interface API library**](https://github.com/samuko-things/EMC2_python_serial_comm_lib) for PC and micro-computers.

Finally, it provides a [**ROS2 hardware interface**](https://github.com/samuko-things/EMC2_ros2_hw_interface) for easy use of the motor driver module with your ROS2 projects.


## HOW TO USE THE EMC2 IN YOUR PROJECT
- First of all get the **EMC2 motor driver module shield** then interface your motor(s) with quadrature encoder to it and power it up.
  > **NOTE:** if your shield comes without a microcontroller (Arduino NANO or UNO), you would have to get one and add it to the driver shield and then upload the [**EMC2_arduino_driver_code**](https://github.com/samuko-things/EMC2_arduino_driver_code) to it.

- Download and install (or build from source) the [**EMC2_gui_application**](https://github.com/samuko-things/EMC2_gui_application). 

- Connect the **EMC2 motor driver module shield** to your PC via serial-USB and start the **EMC2_gui_application** and setup your motor encoder and PID parameter.
  > **NOTE:** the parameter values you set are automatically saved to the microcontroller's memory (i.e it remembers the parameter values)

- After successfully setingup the PID controller, close the application, disconnect the driver module from the PC and hit the reset button on the microcontroller on the shield.

- connect it to your prefered project using any of the API library -  [**EMC2_arduino_i2c_comm_lib**](https://github.com/samuko-things/EMC2_arduino_i2c_comm) (for arduino based project) or [**EMC2_python_serial_comm_lib**](https://github.com/samuko-things/EMC2_python_serial_comm_lib) (for microcomputer based project) or [**EMC2_ros2_hw_interface**](https://github.com/samuko-things/EMC2_ros2_hw_interface) (for ROS2 based project).