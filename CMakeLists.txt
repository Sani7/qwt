cmake_minimum_required(VERSION 3.10)
project(qwt)

option(QWT_BUILD_EXAMPLES "Build example executables" OFF)
option(QWT_BUILD_PLAYGROUND "Build playground executables" OFF)
option(QWT_BUILD_TESTS "Build example executables" OFF)

add_subdirectory(examples)
add_subdirectory(playground)
add_subdirectory(src)
add_subdirectory(tests)
add_subdirectory(designer)
