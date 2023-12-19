cmake_minimum_required(VERSION 3.0.0)

project(HiGHS VERSION 1.6.0 LANGUAGES CXX C)

# use C++11 standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE RELEASE)
endif()

set(BUILD_SHARED_LIBS OFF)

add_compile_options(-Wall
                    -Wextra
                    -Wpedantic
                    -O3
)

add_subdirectory(src)