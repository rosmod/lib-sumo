cmake_minimum_required(VERSION 2.8.3)
project(sumo)

## Start Global Marker

## End Global Marker

## Check C++11 / C++0x
include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "-std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "-std=c++0x")
else()
    message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()

include_directories(include)
include_directories(include/foreign/eulerspiral)
include_directories(include/foreign/mersenne)
include_directories(include/foreign/tcpip)
include_directories(include/traci-server)
include_directories(include/utils/common)
include_directories(include/utils/iodevices)
include_directories(include/utils/options)
include_directories(include/utils/traci)
include_directories(include/utils/xml)
add_library(sumo
	    src/sumo/sumo_client.cpp
            src/utils/traci/TraCIAPI.cpp
            src/foreign/tcpip/socket.cpp
            src/foreign/tcpip/storage.cpp)



