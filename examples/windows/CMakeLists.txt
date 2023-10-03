cmake_minimum_required(VERSION 3.8)

project(windemo)

#引用目录
include_directories(
	${XRTC_DIR}/../xrtc-third_party/NIM_Duilib_Framework)

#链接库目录
link_directories(
	${XRTC_DIR}/../xrtc-third_party/out/build/x64-debug/Windows/lib)

#指定需要编译的cpp文件
file(GLOB all_src
	./src/*.cpp
)

#将编译的源文件链接生成一个可执行文件
add_executable(windemo ${all_src})
target_link_libraries(windemo base duilib Imm32 comctl32)
set_target_properties(windemo PROPERTIES LINK_FLAGS "/SUBSYSTEM:WINDOWS /SAFESEH:NO")

#拷贝当前目录下的resources资源目录到可执行文件目录下面，用于加载资源
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/resources DESTINATION ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})