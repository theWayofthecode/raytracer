cmake_minimum_required(VERSION 3.14)
project(raytracer)

set(CMAKE_CXX_STANDARD 17)

######### OPENGL ########
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

find_package(GLEW REQUIRED)
if (GLEW_FOUND)
    include_directories(${GLEW_INCLUDE_DIRS})
    link_libraries(${GLEW_LIBRARIES})
endif()
#############################

######### IMGUI #########
file(GLOB imguiSrcs imgui/*.cpp)
file(GLOB imguiHdrs imgui/*.h)
add_library(imgui STATIC ${imguiSrcs} ${imguiHdrs})
include_directories(imgui)
#########################

######### EXAMPLES ##############
add_library(imguiExamples STATIC imgui/examples/libs/gl3w/GL/gl3w.c
                                 imgui/examples/imgui_impl_glfw.cpp
                                 imgui/examples/imgui_impl_opengl3.cpp)
include_directories(imgui/examples/libs/gl3w)
include_directories(imgui/examples)
#########################

add_subdirectory(src)
