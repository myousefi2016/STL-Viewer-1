cmake_minimum_required(VERSION 3.5)
project(STLViewer)

#set(CMAKE_CXX_COMPILER /usr/bin/clang++)
#set(CMAKE_C_COMPILER /usr/bin/clang)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -g")


set(SOURCE_FILES main.cpp STLData.cpp STLData.h window_GL.cpp window_GL.h renderer.cpp renderer.h)

add_executable(STLViewer ${SOURCE_FILES})



add_subdirectory("lib/glfw/")
add_subdirectory("lib/glm")

#include_directories("lib/glm/glm")

find_package(GLEW REQUIRED)
if (GLEW_FOUND)
    include_directories(${GLEW_INCLUDE_DIRS})
    link_libraries(${GLEW_LIBRARIES})
endif()

find_package(OpenGL REQUIRED)

target_link_libraries(STLViewer glfw GLEW GL glm)