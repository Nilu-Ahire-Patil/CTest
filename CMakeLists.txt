cmake_minimum_required(VERSION 3.15)
project(MyProject)

# Enable testing in CMake
enable_testing()

# Include Google Test
include(FetchContent)

FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/refs/heads/main.zip
)

# Prevent overriding the parent project's compiler/linker settings on Windows
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

FetchContent_MakeAvailable(googletest)

# Add the test executable
add_executable(my_tests test_main.cpp)

# Link Google Test libraries
target_link_libraries(my_tests gtest gtest_main)

# Register the test executable with CTest
add_test(NAME MyTests COMMAND my_tests)
