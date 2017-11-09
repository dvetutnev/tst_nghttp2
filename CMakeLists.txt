project(tst_nghttp2 CXX C)
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


set(CMAKE_INCLUDE_CURRENT_DIR ON)

option(ENABLE_ASIO_LIB  "Build C++ libnghttp2_asio library" ON)
add_subdirectory(vendor/nghttp2)

add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} nghttp2_asio)
