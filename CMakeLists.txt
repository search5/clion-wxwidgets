cmake_minimum_required(VERSION 3.16)
project(wxTest)

set(CMAKE_CXX_STANDARD 14)

set(wxWidgets_ROOT_DIR </usr/include/wx-3.0>)
set(wxWidgets_CONFIGURATION mswu)
find_package(wxWidgets COMPONENTS core base REQUIRED)
include(${wxWidgets_USE_FILE})

add_executable(wxTest main.cpp)

target_link_libraries(wxTest ${wxWidgets_LIBRARIES})

#set(SOURCE_FILES main.cpp)
#add_executable(wx1Test ${SOURCE_FILES})
#
#target_link_libraries(wx1Test ${wxWidgets_LIBRARIES})