cmake_minimum_required(VERSION 2.8.3)
project(CALC)

set(CMAKE_CXX_STANDARD 11)

#PROJECT_SOURCE_DIR 表示执行cmake时，后面携带的路径（其实就是CMakeLists.txt所在的路径）

# 指定.h 的路径
include_directories(${PROJECT_SOURCE_DIR}/include)

# set(SRC_LIST main.cpp add.cpp div.cpp muilt.cpp sub.cpp)
# 搜索源文件
# 1
# aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)
# 2
file(GLOB SRC_LIST ${PROJECT_SOURCE_DIR}/src/*.cpp)
message(STATUS ${SRC_LIST})
set(TMP hello world)
message(STATUS ${TMP})
set (TMP1 ${SRC_LIST} ${TMP})
message(STATUS ${TMP1})

list(APPEND tmp "xxx1" "xxxx2" ${SRC_LIST})
message(STATUS ${tmp})


list(REMOVE_ITEM SRC_LIST ${PROJECT_SOURCE_DIR}/src/main.cpp)
message(${SRC_LIST})





#制作库
# add_library(calc SHARED ${SRC_LIST})
add_library(calc STATIC ${SRC_LIST})

set(LIBRARY_OUTPUT_PATH /home/melody/example/cmake_demo/v2/lib)
# set(EXECUTABLE_OUTPUT_PATH /home/melody/example/cmake_demo/v1/bin)
# add_executable(app ${SRC_LIST})