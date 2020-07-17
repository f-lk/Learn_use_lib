cmake_minimum_required(VERSION 3.14)

project(use_lib)

set(CMAKE_CXX_FLAGS "-std=c++0x")

#链接自己写的动态库
link_libraries(/tmp/lib/libout.so)

#与动态库对应的头文件
include_directories(/tmp/include/test)

add_executable(use_lib main.cpp)