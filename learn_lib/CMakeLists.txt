cmake_minimum_required(VERSION 2.8)

project(test)

set(CMAKE_CXX_FLAGS "-std=c++0x")

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)


#创建动态库
add_library(out SHARED ${PROJECT_SOURCE_DIR}/main.cpp)

#创建静态库
add_library(static_out STATIC  ${PROJECT_SOURCE_DIR}/main.cpp)
#使静态库和动态库的名字一致
set_target_properties(static_out PROPERTIES OUTPUT_NAME "out")

#输出信息
get_target_property(OUTPUT_VALUE static_out OUTPUT_NAME)
message(STATUS "OUTPUT_NAME = ${OUTPUT_VALUE}")

get_target_property(UNDEFINE_VALUE static_out UNDEFINE_NAME)
message(STATUS "UNDEFINE_NAME = ${UNDEFINE_VALUE}")

#设置版本信息
set_target_properties(out PROPERTIES VERSION 1.0 SOVERSION 1)

#安装静态库和动态库
install(TARGETS out static_out LIBRARY DESTINATION lib ARCHIVE DESTINATION lib/${PROJECT_NAME})

#安装头文件
install(FILES main.h DESTINATION include/${PROJECT_NAME})



