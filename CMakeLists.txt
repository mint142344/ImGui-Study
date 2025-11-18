# CMakeList.txt: 顶层 CMake 项目文件，在此处执行全局配置
# 并包含子项目。
#
cmake_minimum_required (VERSION 3.25)

# 如果支持，请为 MSVC 编译器启用热重载。
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

# https://github.com/epezent/implot_demos
project ("ImGui-Study")

find_package(glfw3 CONFIG REQUIRED)
find_package(OpenGL REQUIRED)
find_package(iir CONFIG REQUIRED)

set(COMMON_SRCS ${CMAKE_SOURCE_DIR}/Common/App.cpp CACHE STRING "Common sources")
set(COMMON_INC ${CMAKE_SOURCE_DIR}/Common CACHE STRING "Common include dir")

set(FFT_SRCS
	${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fft.h
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fftr.h
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fft.c 
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fftr.c
    CACHE STRING "FFT sources"
)
set (FFT_INC ${CMAKE_SOURCE_DIR}/3rdparty/kissfft CACHE STRING "FFT include dir")

set(3RD_PARTY_INC ${CMAKE_SOURCE_DIR}/3rdparty CACHE STRING "3rd party include dir")

# 包含子项目。
add_subdirectory(modules/imgui)
add_subdirectory("implot-demo")
add_subdirectory("spectrogram")
add_subdirectory("voice-demo")
add_subdirectory("filter")
