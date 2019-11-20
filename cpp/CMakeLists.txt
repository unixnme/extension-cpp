cmake_minimum_required(VERSION 2.8.12)
project(lltm_cpp)
set(CMAKE_CXX_FLAGS "-g -O0")

add_subdirectory(pybind11)
pybind11_add_module(lltm_cpp lltm.cpp)

target_include_directories(lltm_cpp PRIVATE
        libtorch//include
        libtorch/include/torch/csrc/api/include)