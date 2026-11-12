cmake_minimum_required(VERSION 3.28)
project(desktop)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


find_package(Qt6 COMPONENTS
        Core
        Gui
        Widgets
        REQUIRED)

add_executable(desktop src/main.cpp)

target_link_libraries(desktop PRIVATE
        Qt::Core
        Qt::Gui
        Qt::Widgets
)

target_include_directories(desktop PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
)

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
    option(DESKTOP_BUILD_TESTS "Build tests" ON)
else()
    option(DESKTOP_BUILD_TESTS "Build tests" OFF)
endif()

if(DESKTOP_BUILD_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif()