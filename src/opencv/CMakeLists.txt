cmake_minimum_required(VERSION 3.0.2)
project(opencv)

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  sensor_msgs
  std_msgs
)

find_package (OpenCV REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES opencv
  CATKIN_DEPENDS cv_bridge image_transport roscpp sensor_msgs std_msgs
# DEPENDS system_lib
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(opencv_pub src/pub.cpp)
target_link_libraries(opencv_pub ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})

add_executable(opencv_sub src/sub.cpp)
target_link_libraries(opencv_sub ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})
