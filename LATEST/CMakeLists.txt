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
   ./ref/Rte/LATEST/gen/src/Rte.cpp
   ./ref/Swc_Foc/LATEST/gen/src/Swc_Foc.cpp
)

add_subdirectory(
   ref/AUTOSAR_Bsw/LATEST ref/AUTOSAR_Bsw/LATEST
)

target_link_libraries(
   Ecu_Sw.out PUBLIC
   AUTOSAR_Bsw
)

target_include_directories(
   Ecu_Sw.out PUBLIC
   "${PROJECT_BINARY_DIR}"
   "${PROJECT_SOURCE_DIR}/ref/AUTOSAR_Bsw/LATEST"
   "${PROJECT_SOURCE_DIR}/ref/Rte/LATEST/gen/inc"
   "${PROJECT_SOURCE_DIR}/ref/Swc_Foc/LATEST/gen/inc"
)

