# %Tag(FULLTEXT)%
cmake_minimum_required(VERSION 2.8.3)
project(multimaster_example)

set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")
MESSAGE("FALGS: ${CMAKE_CXX_FLAGS}")

## Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp rospy roslib std_msgs)

## Declare ROS messages and services
#add_message_files(FILES Num.msg)
#add_service_files(FILES AddTwoInts.srv)

## Generate added messages and services
#generate_messages(DEPENDENCIES)

## Declare a catkin package
catkin_package()

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(multimaster_example src/multimaster_example.cpp)
target_link_libraries(multimaster_example ${catkin_LIBRARIES})
#add_dependencies(subscriber beginner_tutorials_generate_messages_cpp)


add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
add_dependencies(talker multimaster_example_generate_messages_cpp)


# %EndTag(FULLTEXT)%
