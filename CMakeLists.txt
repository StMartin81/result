cmake_minimum_required(VERSION 3.1)
project(cpp_result)

option(TEST "Build test subdirectory" OFF)

set(CMAKE_CXX_STANDARD 17)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/..)

if(TEST)
    add_subdirectory("test")
endif()
