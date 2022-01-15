cmake_minimum_required(VERSION 3.21)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_C_STANDARD 11)

set(PROJECT_NAME "template")
set(AGK_LIBS_DIR "C:/Users/jesus/AppGameKit/CPP")

project(${PROJECT_NAME})

add_compile_definitions(
        WIN32
        _DEBUG
        _WINDOWS
        AGK_WINDOWS
        _CRT_SECURE_NO_WARNINGS
)

include_directories(
        .
        "${AGK_LIBS_DIR}/common/include"
        "${AGK_LIBS_DIR}/common"
        "${AGK_LIBS_DIR}/bullet/"
        "${AGK_LIBS_DIR}/bullet/Collision/CollisionShapes"
)

link_directories(
        "${AGK_LIBS_DIR}/platform/windows/Lib/VS2017/Debug64"
)

add_executable(
        ${PROJECT_NAME} WIN32
        Core.cpp
        resource.h
        template.cpp template.h
)

set_target_properties(
        ${PROJECT_NAME} PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY "../Final"
        MSVC_RUNTIME_LIBRARY "MultiThreadedDebug"
)

target_link_libraries(
        ${PROJECT_NAME}
        "AGKWindows64.lib"
        "OpenGL32.lib"
        "winmm.lib"
        "dwmapi.lib"
)
