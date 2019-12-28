cmake_minimum_required(VERSION 3.5.1)
project(hello_vision CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

message(STATUS ${CMAKE_SYSTEM_NAME})
if (CMAKE_SYSTEM_NAME MATCHES "Windows")
    #    set(OpenCV_DIR )
elseif (CMAKE_SYSTEM_NAME MATCHES "Darwin")
    set(OpenCV_DIR /Users/mason/Project/source/opencv4/lib/cmake/opencv4)
    set(VTK_DIR /Users/mason/Project/source/vtk/lib/cmake/vtk-8.2)

    set(TBB_DIR /Users/mason/Project/source/tbb/cmake)
    set(TBB_INCLUDE_DIR /Users/mason/Project/source/tbb/include)
    set(TBB_LIBRARY_DEBUG /Users/mason/Project/source/tbb/lib)
    set(TBB_LIBRARY_RELEASE /Users/mason/Project/source/tbb/lib)

    set(Qt5_DIR /usr/local/Cellar/qt/5.14.0/lib/cmake/Qt5)
elseif (CMAKE_SYSTEM_NAME MATCHES "Linux")
    #    set(OpenCV_DIR )
endif ()

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# recommend use CMAKE_PREFIX_PATH instead
find_package(OpenCV REQUIRED)
find_package(VTK REQUIRED)
find_package(TBB REQUIRED)
find_package(Qt5 COMPONENTS Widgets REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})

add_executable(main source/main.cpp)
target_link_libraries(main ${OpenCV_LIBS})

add_executable(helloworld source/main_ui.cpp)
target_link_libraries(helloworld Qt5::Widgets)