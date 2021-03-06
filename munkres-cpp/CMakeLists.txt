# Common variables.
cmake_minimum_required  (VERSION 2.8)
project                 (munkres-cpp)
set (munkres-cpp_VERSION_MAJOR 3)
set (munkres-cpp_VERSION_MINOR 0)

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set (CMAKE_CXX_FLAGS_DEBUG   "${CMAKE_CXX_FLAGS} -O0 -ggdb3 -DDEBUG")
set (CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS} -O3")

include_directories (${PROJECT_SOURCE_DIR}/src)

# Sources (nothing).
set (
    MunkresCpp_SOURCES
)

# Headers.
set (
    MunkresCpp_HEADERS
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/matrix.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/matrix_base.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/utils.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/munkres.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_armadillo.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_boost.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_eigen.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_opencv.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_qt.h
    ${PROJECT_SOURCE_DIR}/src/munkres-cpp/adapters/matrix_std_2d_vector.h
)

# Library.
add_library (
    munkres INTERFACE
)

install (DIRECTORY ${PROJECT_SOURCE_DIR}/src/ DESTINATION include FILE_PERMISSIONS OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ)


# Binary examples
add_executable (example_01 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_01.cpp)
add_executable (example_02 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_02.cpp)
add_executable (example_03 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_03.cpp)
add_executable (example_04 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_04.cpp)
add_executable (example_05 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_05.cpp)
add_executable (example_06 EXCLUDE_FROM_ALL ${PROJECT_SOURCE_DIR}/examples/example_06.cpp)
add_custom_target (examples)
add_dependencies  (
    examples
    example_01
    example_02
    example_03
    example_04
    example_05
    example_06
)
