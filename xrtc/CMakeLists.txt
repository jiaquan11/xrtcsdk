cmake_minimum_required(VERSION 3.8)

project(xrtc)

#指定需要编译的cpp文件
file(GLOB all_src
	./*.cpp
)

#引用的文件目录
include_directories(
	${XRTC_DIR}
	${XRTC_THIRD_PARTY_DIR}/include
)

link_directories(
	${XRTC_THIRD_PARTY_DIR}/lib
)

#将编译的源文件链接生成一个动态库
add_library(xrtc SHARED ${all_src})
target_link_libraries(xrtc
	absl_bad_optional_access
    absl_throw_delegate
    absl_strings
    absl_bad_variant_access
	winmm
	libwebrtc
)