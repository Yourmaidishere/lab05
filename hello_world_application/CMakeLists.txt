cmake_minimum_required(VERSION 2.3)

project(HW)

include_directories(formatter_ex_lib)

add_subdirectory(formatter_ex_lib)

add_executable(HW hello_world.cpp)

target_link_libraries(HW formatter_ex)
