cmake_minimum_required(VERSION 2.8.3)
project(wheeltec_robot_rc)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS roscpp geometry_msgs joy
actionlib
actionlib_msgs
geometry_msgs
message_generation
nav_msgs
nav_msgs
roscpp
serial
roslib
rospy
sensor_msgs
std_msgs
tf
)

include_directories(${catkin_INCLUDE_DIRS})

catkin_package(
  INCLUDE_DIRS
  CATKIN_DEPENDS roscpp geometry_msgs joy
  DEPENDS
  
)

###########
## Build ##
###########

add_executable(turtlebot_teleop_joy src/turtlebot_joy.cpp)
add_executable(turtlebot_teleop_cpp src/control_by_cpp.cpp)
target_link_libraries(turtlebot_teleop_joy ${catkin_LIBRARIES})
target_link_libraries(turtlebot_teleop_cpp ${catkin_LIBRARIES})

#############
## Install ##
#############

## Mark executable scripts (Python etc.) for installation
install(PROGRAMS
  scripts/turtlebot_teleop_key
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Mark executables and/or libraries for installation
install(TARGETS turtlebot_teleop_joy
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Mark all other useful stuff for installation
install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
