
set(EXECUTABLE_NAME "fft_demo")

add_executable(${EXECUTABLE_NAME}
	spectrogram.cpp
	${CMAKE_SOURCE_DIR}/Common/App.cpp
	${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fft.h
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fftr.h
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fft.c 
    ${CMAKE_SOURCE_DIR}/3rdparty/kissfft/kiss_fftr.c
)

target_include_directories(${EXECUTABLE_NAME} 
	PRIVATE 
	${CMAKE_SOURCE_DIR}/Common
	${CMAKE_SOURCE_DIR}/3rdparty
	${CMAKE_SOURCE_DIR}/3rdparty/kissfft
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
