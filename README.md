# ros_esp32
this is the code from which you can control a differential robot from your laptop running ros.the esp32 will receive commands from udp.


first open a terminal in your laptop can run roscore command
then open another terminal and run rosrun teleop_twist_keyboard teleop_twist_keyboard.py, this will be used to control your robot.

1: create a new folder named as teleop_ws. inside create a new folder src.

2: open terminal and cd into teleop_ws and write catkin_make

3: cd into src 

4: catkin_create_pkg my_package std_msgs rospy. (this will make a folder name my_package in src)

5: go into that folder(my_package) and open src, you should paste your laptop code here which should be named as teleop_twist_to_esp32.py (inside src folder).

5.1: open terminal cd to where u paste teleop_twist_to_esp32.py file and run this command : chmod +x teleop_twist_to_esp32.py


6: next go back into my_package and open CMakeLists.txt

7: inside CMakeLists.txt paste this at the end of the file : 

## Add folders to be run by python nosetests
# catkin_add_nosetests(test)
catkin_install_python(PROGRAMS src/teleop_twist_to_esp32.py
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
                      )

8: cd back into teleop_ws and run this command in terminal : catkin_make

9: then write this command : source devel/setup.bash

10: then write this command : rosrun my_package teleop_twist_to_esp32.py

and you are done. now from step 6 you will send commands to teleop_twist_to_esp32.py and teleop_twist_to_esp32.py will send commands to esp32 via udp.
ENJOY!

i am working on esp32 code to implement pid control by using encoders.and also to send encoder values back to pc for odometry and visualize my robot in rviz.
i dont own a lidar so i will use sharp ir sensor to map a room in rviz.








