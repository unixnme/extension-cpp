## Install
```bash
# submodule
git submodule update --init --recursive

# libtorch (following link for macOS but similar for other OS)
wget https://download.pytorch.org/libtorch/cpu/libtorch-macos-1.3.1.zip
unzip libtorch-macos-1.3.1.zip

# make sure to set TORCH_EXTENSION_NAME macro when compiling
# this is set to "lltm_cpp" in this example (look into CMakeLists.txt)
# this name is what you use when importing the module within python,
#    i.e., import torch; import lltm_cpp
# also, this name must match with the output library file (so file)

mkdir build && cd build
cmake ..
make

# to be able to import the module, either
#   1. you run the python command from the directory that contains the so file
#   2. set PYTHONPATH to the directory containing the so file

cd ..
PYTHONPATH="build" python lltm.py
```