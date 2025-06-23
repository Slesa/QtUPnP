cmake_minimum_required(VERSION 3.16)

project(chupnp VERSION 0.9.8 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../bin)

find_package(Qt6 REQUIRED COMPONENTS Core Network Core5Compat Gui Widgets)
find_package(Qt6 REQUIRED COMPONENTS Core5Compat)
find_package(Qt6 REQUIRED COMPONENTS Network)
find_package(Qt6 REQUIRED COMPONENTS Gui Widgets)
find_package(Qt6 REQUIRED COMPONENTS Widgets)

link_directories(${CMAKE_SOURCE_DIR}/../lib)

qt_standard_project_setup()

qt_add_executable(chupnp
  actionParams.hpp actionParams.cpp actionParams.ui
  actiontriggered.cpp
  helper.hpp helper.cpp 
  item.hpp item.cpp 
  loadservices.cpp
  main.cpp
  mainwindow.hpp mainwindow.cpp mainwindow.ui
  search.hpp search.cpp search.ui
  sendgetaction.cpp
  slots.cpp
  stdaction.hpp stdaction.cpp stdaction.ui
)

#set_property(TARGET chupnp PROPERTY IMPORTED_IMPLIB "${CMAKE_SOURCE_DIR}/../lib/libupnp.a")
#target_link_libraries(chupnp PRIVATE Qt6::Network Qt6::Core5Compat Qt6::Gui Qt6::Widgets ${CMAKE_SOURCE_DIR}/../lib/libupnp.a)
target_link_libraries(chupnp PRIVATE Qt6::Network Qt6::Core5Compat Qt6::Gui Qt6::Widgets upnp)

#set_target_properties(chupnp PROPERTIES
#    WIN32_EXECUTABLE ON
#    MACOSX_BUNDLE ON
#)
