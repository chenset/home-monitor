cmake_minimum_required(VERSION 3.3)
project(monitor)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")


set(SOURCE_FILES main.cpp)


set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_RUNTIME OFF)
find_package(Boost 1.59.0 COMPONENTS system filesystem regex REQUIRED)

if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    link_directories(${Boost_LIBRARY_DIR})
    add_executable(monitor ${SOURCE_FILES})
    target_link_libraries(monitor ${Boost_LIBRARIES})
endif()

if(WIN32)
    target_link_libraries(monitor wsock32 ws2_32)
endif()


message(WARNING "----------------------------------------------")
message(WARNING "Boost_VERSION ${Boost_VERSION}")
message(WARNING "Boost_INCLUDE_DIR ${Boost_INCLUDE_DIRS}")
#include_directories(src)
message(WARNING "Boost_LIBRARY_DIR ${Boost_LIBRARY_DIRS}")
message(WARNING "Boost_LIBRARY_DIR ${Boost_LIBRARIES}")
message(WARNING "----------------------------------------------")
message(WARNING "Boost_LIBRARY_DIR ${Boost_LIBRARIES}")

