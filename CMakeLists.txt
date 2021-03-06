cmake_minimum_required(VERSION 3.1)

project(corba)

# Specify output directories.
set(EXECUTABLE_OUTPUT_PATH "${PROJECT_BINARY_DIR}/bin")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(RapidJSON REQUIRED)

find_package(GLog REQUIRED)

find_package(GTest REQUIRED)

# Build with c++14 support, required by sc2api.
set(CMAKE_CXX_STANDARD 17)

add_subdirectory("src")

option(ENABLE_TESTS "Build tests" ON)
if(ENABLE_TESTS)
	enable_testing()
	add_subdirectory(tests)
endif()
