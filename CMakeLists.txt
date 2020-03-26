cmake_minimum_required(VERSION 3.5)
project(ralib)
enable_testing()

set(CMAKE_VERBOSE_MAKEFILE ATTACHED_FILES_ON_FAIL)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_library(ralib INTERFACE)

add_executable(array_tests tests/array_tests.cpp)
target_link_libraries(array_tests ${CONAN_LIBS})
target_compile_definitions(array_tests PRIVATE _GLIBCXX_USE_CXX11_ABI=0)


add_test(NAME array_tests WORKING_DIRECTORY ${CMAKE_BINARY_DIR}/bin COMMAND array_tests)