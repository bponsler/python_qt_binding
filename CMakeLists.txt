cmake_minimum_required(VERSION 3.5)
project(python_qt_binding)

# Add support for C++11
if(NOT WIN32)
  add_definitions(-std=c++11)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)

ament_python_install_package(${PROJECT_NAME})

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES})

install(FILES cmake/shiboken_helper.cmake cmake/sip_configure.py
  cmake/sip_helper.cmake
  DESTINATION share/${PROJECT_NAME}/cmake)

ament_export_dependencies(ament_cmake)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package(
  CONFIG_EXTRAS "cmake/python_qt_binding-extras.cmake.in"
)
