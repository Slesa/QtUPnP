cmake_minimum_required(VERSION 3.16)

project(upnp VERSION 0.9.8 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
#set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../lib)
#set_target_propertes(${PROJECT_NAME} PROPERTIES
#    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
#)

find_package(Qt6 REQUIRED COMPONENTS Core Network Core5Compat Gui)
find_package(Qt6 REQUIRED COMPONENTS Core5Compat)
find_package(Qt6 REQUIRED COMPONENTS Network)
find_package(Qt6 REQUIRED COMPONENTS Gui)
qt_standard_project_setup()

qt_add_library(upnp STATIC 
  action.hpp action.cpp 
  actioninfo.hpp actioninfo.cpp
  actionmanager.hpp actionmanager.cpp
  aes256.h 
  aesencryption.h aesencryption.cpp
  argument.hpp argument.cpp
  avcontrol.hpp avcontrol.cpp
  avtransport.hpp avtransport.cpp 
  browsereply.hpp browsereply.cpp
  connectioninfo.hpp connectioninfo.cpp
  connectionmanager.hpp connectionmanager.cpp
  contentdirectory.hpp contentdirectory.cpp
  control.hpp control.cpp
  controlpoint.hpp controlpoint.cpp
  datacaller.hpp datacaller.cpp
  device.hpp device.cpp
  devicecaps.hpp devicecaps.cpp
  devicemap.hpp devicemap.cpp
  devicepixmap.hpp devicepixmap.cpp
  didlitem.hpp didlitem.cpp
  didlitem_playlist.cpp
  dump.hpp dump.cpp
  eventingmanager.hpp eventingmanager.cpp
  helper.hpp helper.cpp
  httpparser.hpp httpparser.cpp
  httpserver.hpp httpserver.cpp
  initialdiscovery.hpp initialdiscovery.cpp
  mediainfo.hpp mediainfo.cpp
  multicastsocket.hpp multicastsocket.cpp
  oauth2.hpp oauth2.cpp
  pixmapcache.hpp pixmapcache.cpp
  plugin.hpp plugin.cpp
  positioninfo.hpp positioninfo.cpp
  renderingcontrol.hpp renderingcontrol.cpp
  service.hpp service.cpp
  statevariable.hpp statevariable.cpp
  status.hpp
  transportinfo.hpp transportinfo.cpp
  transportsettings.hpp transportsettings.cpp
  unicastsocket.hpp unicastsocket.cpp
  upnp_global.hpp
  upnpsocket.hpp upnpsocket.cpp
  using_upnp_namespace.hpp
  waitingloop.hpp waitingloop.cpp
  xmlhaction.hpp xmlhaction.cpp 
  xmlh.cpp
  xmlhdevice.hpp xmlhdevice.cpp
  xmlhdidllite.hpp xmlhdidllite.cpp 
  xmlhevent.hpp xmlhevent.cpp
  xmlh.hpp
  xmlhservice.hpp xmlhservice.cpp
)

target_link_libraries(upnp PRIVATE Qt6::Network Qt6::Core5Compat Qt6::Gui)
install(TARGETS upnp
    BUNDLE  DESTINATION ../lib/
    RUNTIME DESTINATION ../lib/ # ${CMAKE_INSTALL_BINDIR}
)
