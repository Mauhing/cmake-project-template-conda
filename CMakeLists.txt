cmake_minimum_required(VERSION 3.2)

project(cmake-project-template)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3")

set(CMAKE_INSTALL_PREFIX $ENV{CONDA_PREFIX})

set(DIVISIBLE_INSTALL_INCLUDE_DIR $ENV{CONDA_PREFIX}/include)
set(DIVISIBLE_INSTALL_BIN_DIR $ENV{CONDA_PREFIX}/bin)
set(DIVISIBLE_INSTALL_LIB_DIR $ENV{CONDA_PREFIX}/lib)

set(DIVISION_HEADERS_DIR ${PROJECT_SOURCE_DIR}/src/division)

include_directories(${DIVISIBLE_INSTALL_INCLUDE_DIR})
include_directories(${DIVISION_HEADERS_DIR})

add_subdirectory(src)
add_subdirectory(test)


