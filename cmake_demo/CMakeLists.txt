cmake_minimum_required(VERSION 3.10)
project(cmake_demo)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#set(CMAKE_PREFIX_PATH
#        /opt/Qt5.11.1/5.11.1/gcc_64/)
# for cmake parameter -DCMAKE_PREFIX_PATH=/opt/Qt5.11.1/5.11.1/gcc_64/

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt5 COMPONENTS Core Widgets REQUIRED)

#find_package(Qt5Core)
#find_package(Qt5Widgets)

qt5_wrap_ui(
        UI_FILE
        ui/widget.ui
)

qt5_add_resources(
        QRC_FILE
        res/resources.qrc
)

set(SRCS
        main.cpp widget.cpp widget.h
)

add_executable(cmake_demo
        ${SRCS}
        ${UI_FILE}
        ${QRC_FILE}
        )

target_link_libraries(cmake_demo
        Qt5::Core
        Qt5::Widgets
        )