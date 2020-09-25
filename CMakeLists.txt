cmake_minimum_required(VERSION 2.8.3)
project(object3d_detector)

find_package(catkin REQUIRED COMPONENTS roscpp sensor_msgs visualization_msgs geometry_msgs pcl_conversions pcl_ros)

find_package(PCL REQUIRED)

include_directories(include ${catkin_INCLUDE_DIRS})
add_definitions(${PCL_DEFINITIONS})

catkin_package()

catkin_package(
        INCLUDE_DIRS include
)

add_executable(object3d_detector_node src/object3d_detector_node.cpp src/svm.cpp)
target_link_libraries(object3d_detector_node ${catkin_LIBRARIES})
add_dependencies(object3d_detector_node ${catkin_EXPORTED_TARGETS})
