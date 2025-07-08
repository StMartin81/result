cmake_minimum_required(VERSION 2.8)
project(cpp_result)

option(TEST "Build test subdirectory" OFF)

if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /std:c++17")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")
endif()

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/..)

if(TEST)
    add_subdirectory("test")
endif()
