cmake_minimum_required(VERSION 3.8)

project(xrtc)

#指定需要编译的cpp文件
file(GLOB all_src
	./*.cpp
)

#引用的文件目录
include_directories(
	${XRTC_DIR}
)

#将编译的源文件链接生成一个动态库
add_library(xrtc SHARED ${all_src})