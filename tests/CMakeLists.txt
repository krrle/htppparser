cmake_minimum_required(VERSION 3.8)


set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)


set(source
        http_tests.cpp
    )

# Locate GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

add_executable(gtest ${source})

# Link runTests with what we want to test and the GTest and pthread library
target_link_libraries(gtest 
                        ${GTEST_BOTH_LIBRARIES}
                        httpproject
                        pthread
                        )

add_test(
    NAME gtest
    COMMAND gtest
)