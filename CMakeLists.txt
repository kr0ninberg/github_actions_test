cmake_minimum_required(VERSION 3.31)
project(github_ci_test)

set(CMAKE_CXX_STANDARD 20)

add_executable(${PROJECT_NAME} main.cpp)

find_package(GTest)
target_link_libraries(${PROJECT_NAME} ${GTEST_LIBRARIES})
target_compile_options(${PROJECT_NAME} PRIVATE
        $<$<OR:$<CXX_COMPILER_ID:Clang>,$<CXX_COMPILER_ID:AppleClang>,$<CXX_COMPILER_ID:GNU>>:
        -Wall -Wextra -Wpedantic>
        $<$<CXX_COMPILER_ID:MSVC>:
        /Wall>)