# CMakeList.txt: ImGui-Study 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#

# 将源代码添加到此项目的可执行文件。
set(EXECUTABLE_NAME "implot_demo")

add_executable (${EXECUTABLE_NAME} 
	demo.cpp
	${CMAKE_SOURCE_DIR}/Common/App.cpp
)

target_include_directories(${EXECUTABLE_NAME} 
	PRIVATE 
	${CMAKE_SOURCE_DIR}/Common
	${CMAKE_CURRENT_SOURCE_DIR}/Inc
)

target_link_libraries(${EXECUTABLE_NAME} 
	PRIVATE
	imgui
	glfw
	opengl32
)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET ${EXECUTABLE_NAME} PROPERTY CXX_STANDARD 20)
endif()

# TODO: 如有需要，请添加测试并安装目标。
