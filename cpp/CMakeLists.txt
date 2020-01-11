cmake_minimum_required(VERSION 2.8.12)
project(lltm_cpp)

set(CMAKE_CXX_FLAGS "-g -O0")
if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
elseif (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    add_definitions(-D_GLIBCXX_USE_CXX11_ABI=0)
endif()

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)
set(TORCH_MODULE_NAME lltm_cpp)

# this is the critical component!!
add_compile_definitions(TORCH_EXTENSION_NAME=${TORCH_MODULE_NAME})

add_subdirectory(pybind11)
pybind11_add_module(${TORCH_MODULE_NAME} lltm.cpp)

target_include_directories(${TORCH_MODULE_NAME} PRIVATE
        libtorch//include
        libtorch/include/torch/csrc/api/include)
