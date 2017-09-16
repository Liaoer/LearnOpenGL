# CMake entry point
cmake_minimum_required (VERSION 2.6)
project (LearnOpenGL)

#设置GLFW的源目录
set(GLFW3_SOURCE_DIR ${LearnOpenGL_SOURCE_DIR}/external/glfw)
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory(${GLFW3_SOURCE_DIR})



#将上述的头文件目录添加到一个列表变量之中
list( APPEND LearnOpenGL_SOURCE ${GLFW3_SOURCE_DIR} )


#利用find_package命令找到OpenGL
find_package(OpenGL REQUIRED)
IF (NOT OPENGL_FOUND)
    message(WARNING OpenGL-NOT FOUND: ${OPENGL_INCLUDE_DIR})
else()
    message(WARNING OPENGL_INCLUDE_DIR: ${OPENGL_INCLUDE_DIR})
    message(WARNING OPENGL_LIBRARY: ${OPENGL_LIBRARY})
    message(WARNING OPENGL_LIBRARIES: ${OPENGL_LIBRARIES})
ENDIF()


list( APPEND LearnOpenGL_SOURCE ${OPENGL_gl_LIBRARY} )

#设置项目的头文件包含目录
include_directories( ${LearnOpenGL_SOURCE} )

# Compile external dependencies 
add_subdirectory (src)
