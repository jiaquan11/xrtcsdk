﻿cmake_minimum_required (VERSION 3.8)

project(xrtcsdk)

if (CMAKE_CL_64) 
    if (CMAKE_BUILD_TYPE MATCHES "Debug")
        set(BUILD_TYPE "x64-Debug")
    else()
        set(BUILD_TYPE "x64-Release")
    endif()
else()
    if (CMAKE_BUILD_TYPE MATCHES "Debug")
        set(BUILD_TYPE "x86-Debug")
    else()
        set(BUILD_TYPE "x86-Release")
    endif()
endif()

#默认存放静态库的目录  CMAKE_BINARY_DIR:代表编译二进制格式，比如x64-debug,CMAKE_SYSTEM_NAME:代表系统平台比如Windows
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/lib)
#默认存放动态库的目录
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/lib)
#默认存放可执行文件的目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/bin)

#设置当前目录为XRTC_DIR
set(XRTC_DIR ${CMAKE_CURRENT_SOURCE_DIR})

set(XRTC_THIRD_PARTY_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../xrtc-third_party/out/install/${BUILD_TYPE}/${CMAKE_SYSTEM_NAME})

#增加宏定义
if (CMAKE_SYSTEM_NAME MATCHES "Windows")
	add_definitions(-DUNICODE -D_UNICODE)
endif()

add_subdirectory("./xrtc")
add_subdirectory("./examples")
