cmake_minimum_required (VERSION 3.10)

foreach (p CMP0048 CMP0054 CMP0071)
    if (POLICY ${p})
        cmake_policy(SET ${p} NEW)
    endif ()
endforeach ()

project(QTWEBENGINE_SNAP LANGUAGES CXX)

set (CMAKE_CXX_STANDARD 17)
set (CMAKE_CXX_STANDARD_REQUIRED ON)
set (CMAKE_CXX_EXTENSIONS OFF)

# Find includes in the build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Turn on automatic invocation of the MOC, UIC & RCC
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

# Find the QtWidgets library
find_package(Qt5 REQUIRED COMPONENTS Core Widgets WebEngine WebEngineWidgets)

# Tell CMake to create the helloworld executable
add_executable(qtwebengine_snap main.cpp mainwindow.cpp mainwindow.ui resources.qrc)

# Add the Qt5 Widgets for linking
target_link_libraries(qtwebengine_snap Qt5::Core Qt5::Widgets Qt5::WebEngine Qt5::WebEngineWidgets)

install(TARGETS qtwebengine_snap RUNTIME DESTINATION bin)