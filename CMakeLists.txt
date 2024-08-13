cmake_minimum_required(VERSION 3.2)
project(cmake-project-template)

# Option to toggle between Conda and local installation
option(USE_CONDA "Install in Conda environment" OFF)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3")

if(USE_CONDA)
    set(CMAKE_INSTALL_PREFIX $ENV{CONDA_PREFIX})
    set(DIVISIBLE_INSTALL_INCLUDE_DIR $ENV{CONDA_PREFIX}/include)
    set(DIVISIBLE_INSTALL_BIN_DIR $ENV{CONDA_PREFIX}/bin)
    set(DIVISIBLE_INSTALL_LIB_DIR $ENV{CONDA_PREFIX}/lib)
else()
    set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR})
    set(DIVISIBLE_INSTALL_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/include)
    set(DIVISIBLE_INSTALL_BIN_DIR ${PROJECT_SOURCE_DIR}/bin)
    set(DIVISIBLE_INSTALL_LIB_DIR ${PROJECT_SOURCE_DIR}/lib)
endif()

set(DIVISION_HEADERS_DIR ${PROJECT_SOURCE_DIR}/src/division)

include_directories(${DIVISIBLE_INSTALL_INCLUDE_DIR})
include_directories(${DIVISION_HEADERS_DIR})

add_subdirectory(src)
add_subdirectory(test)

# For local installation (default)
# cmake ..
# For Conda installation
# cmake -DUSE_CONDA=ON ..