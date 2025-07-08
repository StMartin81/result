cmake_minimum_required(VERSION 3.5)

project(result
    VERSION 1.0.0
    DESCRIPTION "A header-only result library"
    LANGUAGES CXX)

option(TEST "Build test subdirectory" OFF)

# Create the header-only library
add_library(${PROJECT_NAME} INTERFACE)
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

# Set C++ standard as a feature requirement
target_compile_features(${PROJECT_NAME} INTERFACE cxx_std_17)

# Include directories
target_include_directories(${PROJECT_NAME}
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

# Build tests if requested
if(TEST)
    add_subdirectory("test")
endif()

# Installation (optional, but recommended)
include(GNUInstallDirs)
install(TARGETS ${PROJECT_NAME}
    EXPORT ${PROJECT_NAME}Targets
)
