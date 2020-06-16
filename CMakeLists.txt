cmake_minimum_required(VERSION 3.16)
project(wxTest)

set(CMAKE_CXX_STANDARD 14)

set(SRC_FILES
    main.cpp
)

if(WIN32)
    set(wxWidgets_FIND_STYLE "win32")

    include_directories(
            WX_INCLUDES
            C:/wxWidgets-3.0.4
            C:/wxWidgets-3.0.4/include
            C:/wxWidgets-3.0.4/lib/gcc_dll/mswud
    )

    link_directories(
            C:/wxWidgets-3.0.4/lib/gcc_dll
            C:/wxWidgets-3.0.4/lib/gcc_dll/mswud
    )

    set(
            WX_LIBS
            libwxscintillad.a
            libwxtiffd.a
            libwxjpegd.a
            libwxpngd.a
            libwxzlibd.a
            libwxregexud.a
            libwxexpatd.a
            wxmsw30u_gcc_custom.dll
            wxmsw30u_gl_gcc_custom.dll
    )
else()
    set(wxWidgets_FIND_STYLE "unix")

    set(wxWidgets_ROOT_DIR </usr/include/wx-3.0>)
    set(wxWidgets_CONFIGURATION mswu)
    find_package(wxWidgets COMPONENTS core base REQUIRED)
    include(${wxWidgets_USE_FILE})
endif()

add_executable(${PROJECT_NAME} ${SRC_FILES})

if(WIN32)
    target_link_libraries(
            ${PROJECT_NAME}
            ${WX_LIBS}
    )
else()
    target_link_libraries(wxTest ${wxWidgets_LIBRARIES})
endif()