# 设置最低 CMake 版本
cmake_minimum_required(VERSION 3.2)

# 设置项目名称和版本
project(chatproject VERSION 1.0)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 查找需要的库
find_package(Threads REQUIRED)

# 设置源文件列表
set(TEST_CLIENT_SOURCES test_client.cpp client.cpp)
set(TEST_SERVER_SOURCES test_server.cpp server.cpp)

# 包含头文件目录
include_directories(${CMAKE_SOURCE_DIR})

# 添加可执行文件
add_executable(test_client ${TEST_CLIENT_SOURCES})
add_executable(test_server ${TEST_SERVER_SOURCES})

# 链接库
target_link_libraries(test_client Threads::Threads)
target_link_libraries(test_server Threads::Threads -lmysqlclient)

# 指定安装路径
install(TARGETS test_client test_server DESTINATION bin)

# 添加 clean 目标
# add_custom_target(clean
#     COMMAND ${CMAKE_COMMAND} -E remove test_client test_server
#     COMMENT "Cleaning up built files"
# )

# 包含一些基本的调试信息
message(STATUS "CMake version: ${CMAKE_VERSION}")
message(STATUS "Project name: ${PROJECT_NAME}")
message(STATUS "Project version: ${PROJECT_VERSION}")
message(STATUS "C++ standard: ${CMAKE_CXX_STANDARD}")
