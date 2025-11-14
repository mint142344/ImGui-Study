cmake_minimum_required(VERSION 3.10)

set(PROJECT_NAME imgui)

file(GLOB IMGUI_SOURCE
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
)

add_library(${PROJECT_NAME} STATIC ${IMGUI_SOURCE})

target_include_directories(${PROJECT_NAME}
    PUBLIC
    ./inc
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
    glfw
)
