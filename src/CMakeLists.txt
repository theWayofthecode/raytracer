add_executable(raytracer main.cpp)
target_link_libraries(raytracer imgui imguiExamples ${GLFW_LIBRARIES}  ${GLEW_LIBRARIES} GL dl)
target_include_directories(raytracer PRIVATE ${GLFW_INCLUDE_DIRS} ${GL3W_DIR})