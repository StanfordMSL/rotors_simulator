cmake_minimum_required(VERSION 2.8.3)
project(msl_rotors_joy_interface)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  geometry_msgs
  mav_msgs
  sensor_msgs
  trajectory_msgs
)
include_directories(include ${catkin_INCLUDE_DIRS})

catkin_package(
  DEPENDS
  INCLUDE_DIRS include
  CATKIN_DEPENDS roscpp geometry_msgs mav_msgs sensor_msgs trajectory_msgs
  LIBRARIES
)

add_definitions(-std=c++11)

add_executable(${CMAKE_PROJECT_NAME} src/joy.cpp)
add_dependencies(${CMAKE_PROJECT_NAME} ${catkin_EXPORTED_TARGETS})
target_link_libraries(${CMAKE_PROJECT_NAME} ${catkin_LIBRARIES})

install(TARGETS ${CMAKE_PROJECT_NAME}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
