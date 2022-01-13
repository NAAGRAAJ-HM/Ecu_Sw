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
   ./Rte/LATEST/Rte.cpp
   ./Swc_Foc/LATEST/Swc_Foc.cpp
)

add_subdirectory(AUTOSAR_Bsw/LATEST AUTOSAR_Bsw/LATEST)
add_subdirectory(EcuAb/LATEST       EcuAb/LATEST)
add_subdirectory(McAL/LATEST        McAL/LATEST)

target_link_libraries(
   Ecu_Sw.out PUBLIC
   AUTOSAR_Bsw
   EcuAb
   McAL
)

target_include_directories(
   Ecu_Sw.out PUBLIC
   "${PROJECT_BINARY_DIR}"
   "${PROJECT_SOURCE_DIR}/AUTOSAR_Bsw/LATEST"
   "${PROJECT_SOURCE_DIR}/EcuAb/LATEST"
   "${PROJECT_SOURCE_DIR}/McAL/LATEST"
   "${PROJECT_SOURCE_DIR}/Rte/LATEST"
   "${PROJECT_SOURCE_DIR}/Swc_Foc/LATEST"
)

