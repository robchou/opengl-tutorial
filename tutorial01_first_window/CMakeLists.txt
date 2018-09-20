cmake_minimum_required (VERSION 3.6)
project(tutorial01)

set(TARGET tutorial01)

if(APPLE)
    set(CMAKE_OSX_DEPLOYMENT_TARGET 10.8)
    include(CMakeFindFrameworks)
endif(APPLE)

find_package(OpenGL REQUIRED)
find_library(GLEW_LIBRARY GLEW)
find_library(GLFW_LIBRARY glfw)

add_definitions (-Wall)

set (INCLUDE_DIRS
    "${CMAKE_SOURCE_DIR}/include"
    ${INCLUDE_DIRS}
)

if(UNIX)
    set (INCLUDE_DIRS
        "/usr/include"
        "/usr/local/include"
        "/usr/include/GL"
        ${INCLUDE_DIRS}
    )
endif(UNIX)

include_directories (
    ${INCLUDE_DIRS}
)

set(PROJECT_SRCS tutorial01.cpp)

add_executable(${TARGET} ${PROJECT_SRCS})
target_link_libraries (${TARGET} ${OPENGL_LIBRARIES} ${GLEW_LIBRARY} ${GLFW_LIBRARY})
