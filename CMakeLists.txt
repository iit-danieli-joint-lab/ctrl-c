# Project
cmake_minimum_required(VERSION 3.16 FATAL_ERROR)
project(ctrl-c VERSION 0.1.0 LANGUAGES CXX)
set (CMAKE_CXX_STANDARD 11)
# To build shared libraries in Windows, we set CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS to TRUE.
# See https://cmake.org/cmake/help/v3.4/variable/CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS.html
# See https://blog.kitware.com/create-dlls-on-windows-without-declspec-using-new-cmake-export-all-feature/
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

add_library(ctrl-c src/ctrl-c.h src/ctrl-c.cpp)
target_include_directories(ctrl-c PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>)
target_include_directories(ctrl-c PUBLIC $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)
set_target_properties(ctrl-c PROPERTIES VERSION ${PROJECT_VERSION} PUBLIC_HEADER ctrl-c.h)

include(GNUInstallDirs)
install(TARGETS ctrl-c
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} 
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
