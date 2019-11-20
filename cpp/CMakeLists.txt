cmake_minimum_required(VERSION 2.8.12)
project(lltm_cpp)
set(CMAKE_CXX_FLAGS "-g -O0")

include_directories(/Users/ykang/env3/lib/python3.7/site-packages/torch/include
        /Users/ykang/env3/lib/python3.7/site-packages/torch/include/torch/csrc/api/include)
add_subdirectory(pybind11)
pybind11_add_module(lltm_cpp lltm.cpp)
