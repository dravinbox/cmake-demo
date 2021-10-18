cmake_minimum_required(VERSION 3.14)
project(cmake_demo)

set(CMAKE_CXX_STANDARD 14)



#项目分层
add_subdirectory(src)
add_subdirectory(libhello)
add_subdirectory(math)


