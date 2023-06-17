cmake_minimum_required(VERSION 3.10)

set(CMAKE_GENERATOR_TOOLSET "v140")
set(CMAKE_VS_PLATFORM_TOOLSET "v140")
# set(CMAKE_PREFIX_PATH "$Qt5_DIR")
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(PLUGIN_VER "26")

project("dockwidget")

message("Looking for Qt...")

find_package(Qt5 REQUIRED Widgets Network)
if (${Qt5_FOUND})
    message("Found Qt " ${Qt5_VERSION})
else()
    message("Couldn't find Qt")
endif()

include_directories("includes/pluginsdk/include")

set(sources
    src/plugin.cpp
    src/widgethelper.cpp
    src/shared.cpp
    src/plugin.h
    src/widgethelper.h
    src/shared.h
    src/singleton.h
)

add_library(${CMAKE_PROJECT_NAME} SHARED ${sources})

target_link_libraries(
    ${CMAKE_PROJECT_NAME}
    Qt5::Widgets
)
