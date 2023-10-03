cmake_minimum_required(VERSION 3.8)

project(windemo)

#指定需要编译的cpp文件
file(GLOB all_src
	./*.cpp
)

#将编译的源文件链接生成一个可执行文件
add_executable(windemo ${all_src})