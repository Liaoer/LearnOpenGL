cmake_minimum_required(VERSION 2.6 FATAL_ERROR)
project (main_project)

#在当前目录下搜索头文件及源文件
file(GLOB_RECURSE CURRENT_HEADERS  *.h *.hpp)
file(GLOB CURRENT_SOURCES  *.cpp)
#为头文件和源文件进行分组
source_group("Include" FILES ${CURRENT_HEADERS}) 
source_group("Source" FILES ${CURRENT_SOURCES}) 

add_executable(main_project ${CURRENT_HEADERS} ${CURRENT_SOURCES} )

#设置项目的外部依赖库


# Find glfw header
#find_path(GLFW_INCLUDE_DIR GLFW/glfw3.h ${GLFW3_INCLUDE_DIR})
# Find glfw library
#find_library(GLFW3_LIBRARIES glfw3 ${GLFW3_LIBRARY})


target_link_libraries( main_project  glfw ${GLFW_LIBRARIES} ${OPENGL_gl_LIBRARY})