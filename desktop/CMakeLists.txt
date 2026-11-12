cmake_minimum_required(VERSION 4.3)
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

add_executable(desktop main.cpp)
target_link_libraries(desktop
        Qt::Core
        Qt::Gui
        Qt::Widgets
)

