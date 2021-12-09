cmake_minimum_required(VERSION 3.16.3)

project(
   Ecu_Sw.out
   VERSION 0.1
)

SET(CMAKE_CXX_STANDARD 11)
SET(CMAKE_CXX_STANDARD_REQUIRED True)

add_definitions(
   -g
   -std=c++11
   -Wall
   -Werror
   -Wextra
   -pedantic
   -Wuninitialized
)

add_executable(
   Ecu_Sw.out
   ../ref/Swc_Foc/LATEST/gen/src/Swc_Foc.cpp
   ../ref/Rte/LATEST/gen/src/Rte.cpp
)

add_subdirectory(
   ../ref/AUTOSAR_Bsw/LATEST/prj submodules/AUTOSAR_Bsw
)

target_link_libraries(
   Ecu_Sw.out PUBLIC
   ../ref/AUTOSAR_Bsw/LATEST/out/AUTOSAR_Bsw.lib
)

target_include_directories(
   Ecu_Sw.out PUBLIC
   ../ref/Swc_Foc/LATEST/gen/inc
   ../ref/Rte/LATEST/gen/inc
)

