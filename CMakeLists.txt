# Project
cmake_minimum_required(VERSION 3.16 FATAL_ERROR)
project(ctrl-c VERSION 0.1.0 LANGUAGES CXX)
set (CMAKE_CXX_STANDARD 11)

add_library(ctrl-c src/ctrl-c.h src/ctrl-c.cpp)
target_include_directories(ctrl-c PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>)
target_include_directories(ctrl-c PUBLIC $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)
set_target_properties(ctrl-c PROPERTIES VERSION ${PROJECT_VERSION} PUBLIC_HEADER ctrl-c.h)

include(GNUInstallDirs)
install(TARGETS ctrl-c
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} 
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})