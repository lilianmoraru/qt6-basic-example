cmake_minimum_required(VERSION 3.15)

project(qtquick LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt6 CONFIG COMPONENTS Core Quick REQUIRED)

add_executable(qtquick
  src/main.cpp
  qml.qrc
)

target_compile_definitions(qtquick
  PRIVATE $<$<OR:$<CONFIG:Debug>,$<CONFIG:RelWithDebInfo>>:QT_QML_DEBUG>)
target_link_libraries(qtquick
  PRIVATE Qt::Core Qt::Quick)
