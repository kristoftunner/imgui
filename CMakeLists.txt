cmake_minimum_required(VERSION 3.16)
project(imgui CXX)
find_package(OpenGL REQUIRED)

set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR} CACHE INTERNAL "imgui directory")

add_library(imgui STATIC "")
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
target_link_libraries(imgui PUBLIC ${OPENGL_LIBRARIES})