# Notice 
This Repositories describe a simple sample for generating documnet with doxygen and cmake. 
The version of each tools is:
- CMake    cmake version 3.15.3  
- doxygen  1.8.16  
- graphviz 2.38  
# Dependence 
doxygen must with graphviz in windows(at least now), when build with cmake there may throw doxygen missing dependence dot(means graphviz).  
# Comment blocks
There are some most frequent used sample in [cppSample](./src/cppSample.cpp).

See [Comment](http://www.doxygen.nl/manual/docblocks.html) for more detail.
# Doxygen configure file
use ```doxygen -g [file_name]``` to generate template file (Doxyfile by default)  
change Output and Input to actual path(use @camke_property@ if build with cmake)

See [Configuration](http://www.doxygen.nl/manual/config.html) for more detail.
# Cmake
there are a few tricks
- use ```cmake ../docs && cmake --build . --traget @Doc``` can lead to construct doc.(@Doc is the name you give in cmake ```add_custom_target```)
- Use @cmake_property@ control doxyfile

See the [CMakeLists.txt](./docs/CMakeLists.txt) in docs/ for more detail.