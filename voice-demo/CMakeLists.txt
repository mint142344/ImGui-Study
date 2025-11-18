set(EXECUTABLE_NAME "voice_demo")

add_executable(${EXECUTABLE_NAME}
	voice.cpp
	${COMMON_SRCS}
	${FFT_SRCS}
)

target_include_directories(${EXECUTABLE_NAME} 
	PRIVATE 
	${COMMON_INC}
	${FFT_INC}
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
