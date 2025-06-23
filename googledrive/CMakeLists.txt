cmake_minimum_required(VERSION 3.16)

project(googledrive VERSION 0.9.8 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)

find_package(Qt6 REQUIRED COMPONENTS Core Network Core5Compat Gui)
find_package(Qt6 REQUIRED COMPONENTS Core5Compat)
find_package(Qt6 REQUIRED COMPONENTS Network)
find_package(Qt6 REQUIRED COMPONENTS Gui)
qt_standard_project_setup()

qt_add_library(upnp
  browse.cpp
  googledrive_global.hpp
  pluginobject.hpp pluginobject.cpp 
)

target_link_libraries(upnp PRIVATE Qt6::Network Qt6::Core5Compat Qt6::Gui)
