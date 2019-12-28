cmake_minimum_required(VERSION 3.5.1)
project(hello_vision CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

message(STATUS ${CMAKE_SYSTEM_NAME})
if (CMAKE_SYSTEM_NAME MATCHES "Windows")
    #    set(OpenCV_DIR )
elseif (CMAKE_SYSTEM_NAME MATCHES "Darwin")
    set(OpenCV_DIR /Users/mason/Project/source/opencv4/lib/cmake/opencv4)
elseif (CMAKE_SYSTEM_NAME MATCHES "Linux")
    #    set(OpenCV_DIR )
endif ()

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
add_executable(main source/main.cpp)
target_link_libraries(main ${OpenCV_LIBS})