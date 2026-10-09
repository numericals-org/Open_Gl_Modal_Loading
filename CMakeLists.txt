cmake_minimum_required(VERSION 4.2.1)
project(Open_Modal VERSION 1.0.0)
cmake_policy(SET CMP0072 NEW)

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

add_executable(Open_Modal 
    src/main.cpp
    src/glad.c
    src/config.cpp
    src/factories/factory.cpp
    src/view/shader.cpp
    src/system/camera_system.cpp
    src/system/motion_system.cpp
    src/system/render_system.cpp
    src/controller/app.cpp 
)

target_include_directories(Open_Modal PRIVATE dependencies)

target_link_libraries(Open_Modal PRIVATE ${GLFW3_LIBRARY} OpenGL::GL)

target_compile_definitions(Open_Modal PRIVATE
    PROJECT_SOURCE_DIR="${CMAKE_SOURCE_DIR}"
)