set(EXECUTABLE_NAME "filter-demo")

add_executable(${EXECUTABLE_NAME}
	filter.cpp
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
	iir::iir
)

target_compile_definitions(${EXECUTABLE_NAME} PRIVATE kiss_fft_scalar=double NOMINMAX)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET ${EXECUTABLE_NAME} PROPERTY CXX_STANDARD 20)
endif()
