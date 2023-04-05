cmake_minimum_required(VERSION 3.8)
project(hello_ros)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(hello REQUIRED)

add_executable(hello_ros src/hello_ros.cpp)
target_link_libraries(hello_ros PRIVATE hello::hello)

ament_package()
