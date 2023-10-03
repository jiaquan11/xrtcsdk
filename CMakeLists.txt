cmake_minimum_required (VERSION 3.8)

project(xrtcsdk)

#默认存放静态库的目录  CMAKE_BINARY_DIR:代表编译二进制格式，比如x64-Debug,CMAKE_SYSTEM_NAME:代表系统平台比如Windows
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/lib)
#默认存放动态库的目录
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/lib)
#默认存放可执行文件的目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${CMAKE_SYSTEM_NAME}/bin)

#设置当前目录为XRTC_DIR
set(XRTC_DIR ${CMAKE_CURRENT_SOURCE_DIR})

add_subdirectory("./xrtc")
add_subdirectory("./examples")
