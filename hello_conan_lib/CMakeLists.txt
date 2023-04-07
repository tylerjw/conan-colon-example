cmake_minimum_required(VERSION 3.16)
project(hello CXX)

find_package(Eigen3 REQUIRED)

add_library(hello src/hello.cpp)
target_link_libraries(hello PUBLIC Eigen3::Eigen)
target_include_directories(hello PUBLIC include)

install(TARGETS hello)
install(DIRECTORY include/ DESTINATION include)
