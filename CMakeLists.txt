project(tst_nghttp2 CXX C)
cmake_minimum_required(VERSION 3.4)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#Temporary dirty hack
set(CMAKE_INCLUDE_CURRENT_DIR ON)
include_directories(
    "${CMAKE_CURRENT_BINARY_DIR}/vendor/nghttp2/lib/includes"
    vendor/nghttp2/lib/includes
    vendor/nghttp2/src/includes
    vendor/nghttp2/third-party
    )

option(ENABLE_ASIO_LIB  "Build C++ libnghttp2_asio library" ON)
add_subdirectory(vendor/nghttp2)

add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} nghttp2_asio)

file(
    GLOB_RECURSE PROJECT_FILES FOLLOW_SYMLINKS
    *.txt *.c *.cpp *.hpp *.h *.in *.cmake *.sh *.md
    README* AUTHORS* LICENSE*
    .travis.yml
)

add_custom_target(
    QTCREATOR_FALLBACK ALL
    COMMENT "Feel free to ignore this target, but please do not remove it."
    SOURCES ${PROJECT_FILES}
)

