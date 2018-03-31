cmake_minimum_required(VERSION 3.10)
project(ts3_cmake_plugin_template C)

set(CMAKE_C_STANDARD 99)

include(ExternalProject)

ExternalProject_Add(pluginsdk
        URL http://dl.4players.de/ts/client/pluginsdk/pluginsdk_3.1.1.1.zip
        PREFIX ${CMAKE_CURRENT_SOURCE_DIR}/pluginsdk
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND "")

include_directories(pluginsdk/src/pluginsdk/include)

add_library(ts3plugin SHARED plugin.c plugin.h)
add_dependencies(ts3plugin pluginsdk)
