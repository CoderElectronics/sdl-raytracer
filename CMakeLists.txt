cmake_minimum_required(VERSION 3.25)
project(raytracer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_WARN_DEPRECATED TRUE)

find_package(SDL2 REQUIRED COMPONENTS SDL2)

add_executable(raytracer raytracer.cpp)
target_link_libraries(raytracer PRIVATE SDL2::SDL2)

add_custom_target(run
    COMMAND raytracer
    DEPENDS raytracer
    WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
)

add_custom_target(clean_self
    COMMAND rm -r Makefile CMakeCache.txt fractals cmake_install.cmake CMakeFiles/
    WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
)