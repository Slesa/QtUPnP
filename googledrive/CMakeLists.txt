cmake_minimum_required(VERSION 3.16)

project(googledrive VERSION 0.9.8 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)

link_directories(${CMAKE_SOURCE_DIR}/../lib)

find_package(Qt6 REQUIRED COMPONENTS
  Core
  Network
  Core5Compat
  Gui
)

qt_standard_project_setup()

qt_add_library(googledrive
  browse.cpp
  googledrive_global.hpp
  pluginobject.hpp pluginobject.cpp 
)

target_link_libraries(googledrive PRIVATE
  Qt6::Core
  Qt6::Network
  Qt6::Core5Compat
  Qt6::Gui
  upnp
)
