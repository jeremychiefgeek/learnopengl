cmake_minimum_required(VERSION 3.10)

if(UNIX)
    set(HOME_DIR $ENV{HOME})
else()
    # For Windows
    set(HOME_DIR $ENV{USERPROFILE})
endif()

set(LIBRARIES_PATH "${HOME_DIR}/libraries")

project(game)

add_executable(game main.cpp glad.c)

link_directories(${CMAKE_CURRENT_SOURCE_DIR}/includes)
add_subdirectory("${LIBRARIES_PATH}/glfw" ${CMAKE_CURRENT_SOURCE_DIR}/includes)
target_link_libraries(game glfw GL)

# find_package(OpenGL REQUIRED)
