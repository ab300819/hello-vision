cmake_minimum_required(VERSION 3.5.1)
project(hello_opencv_playground CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

message(STATUS ${CMAKE_SYSTEM_NAME})
if (CMAKE_SYSTEM_NAME MATCHES "Linux")
    set(APUE /home/think/project/apue)
elseif (CMAKE_SYSTEM_NAME MATCHES "Darwin")
    set(APUE /Users/mengshen/Project/apue)
endif ()

find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )
add_executable( main main.cpp )
target_link_libraries( main ${OpenCV_LIBS} )