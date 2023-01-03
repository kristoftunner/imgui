cmake_minimum_required(VERSION 3.16)
project(imgui CXX)

if(UNIX) # on linux use openGL
  find_package(OpenGL REQUIRED)
endif()

set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR} CACHE INTERNAL "imgui directory")

add_library(imgui STATIC "")
set_property(TARGET imgui PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
target_sources(imgui 
  PRIVATE
  ${IMGUI_DIR}/imgui_demo.cpp
  ${IMGUI_DIR}/imgui_draw.cpp
  ${IMGUI_DIR}/imgui_tables.cpp
  ${IMGUI_DIR}/imgui_widgets.cpp
  ${IMGUI_DIR}/imgui.cpp
)
target_include_directories(imgui 
  PUBLIC ${IMGUI_DIR}
)
if(UNIX)
  target_link_libraries(imgui PUBLIC ${OPENGL_LIBRARIES})
endif()
