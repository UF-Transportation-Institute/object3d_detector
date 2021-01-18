cmake_minimum_required(VERSION 2.8.3)
project(ped_detector)

find_package(catkin REQUIRED COMPONENTS roscpp sensor_msgs visualization_msgs geometry_msgs pcl_conversions pcl_ros)

find_package(PCL REQUIRED)

include_directories(include ${catkin_INCLUDE_DIRS})
add_definitions(${PCL_DEFINITIONS})

catkin_package()

catkin_package(
        INCLUDE_DIRS include
)

add_executable(ped_detector_node src/ped_detector_node.cpp src/svm.cpp)
target_link_libraries(ped_detector_node ${catkin_LIBRARIES})
add_dependencies(ped_detector_node ${catkin_EXPORTED_TARGETS})
