project(tst_nghttp2 CXX C)
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(ENABLE_ASIO_LIB "Build C++ libnghttp2_asio library" ON)
option(ENABLE_APP "Build applications (nghttp, nghttpd, nghttpx and h2load)" OFF)
option(ENABLE_EXAMPLES "Build examples" OFF)
option(ENABLE_PYTHON_BINDINGS "Build Python bindings" OFF)
option(WITH_LIBXML2 "Use libxml2" OFF)
option(WITH_SPDYLAY "Use spdylay" OFF)
option(WITH_MRUBY "Use mruby" OFF)
option(WITH_NEVERBLEED "Use neverbleed" OFF)

add_subdirectory(vendor/nghttp2)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} nghttp2_asio)
