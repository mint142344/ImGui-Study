# CMakeList.txt: ImGui-Study 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#

# 将源代码添加到此项目的可执行文件。
set(EXECUTABLE_NAME "implot_demo")

add_executable (${EXECUTABLE_NAME} 
	demo.cpp
	${COMMON_SRCS}
)

target_include_directories(${EXECUTABLE_NAME} 
	PRIVATE 
	${COMMON_INC}
	${3RD_PARTY_INC}
)

target_link_libraries(${EXECUTABLE_NAME} 
	PRIVATE
	imgui
	glfw
	OpenGL::GL
)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET ${EXECUTABLE_NAME} PROPERTY CXX_STANDARD 20)
endif()

# TODO: 如有需要，请添加测试并安装目标。
