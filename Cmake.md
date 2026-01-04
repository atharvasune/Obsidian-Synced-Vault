<hr>

`Cmake` is a bundling tool for C++ applications. 

Official documentation says this

`CMake` is a cross-platform build system generator used primarily for C and C++ projects. Instead of writing platform-specific build files manually, you write a `CMakeLists.txt` file that CMake uses to generate native build files (like Makefiles on Linux or Visual Studio projects on Windows).

<hr>

Sample Cmake file 
```
cmake_minimum_required(VERSION 3.15)
project(myengine)

set(CMAKE_CXX_STANDARD 17)

find_package(raylib REQUIRED)

add_executable(myengine main.cpp)
target_link_libraries(myengine raylib)
```

Lets understand this bugger 
1. `cmake_minimum_required` is the minimum version of cmake required
2. `project(<name>)` is the name of the project
3. `set(CMAKE_CXX_STANDARD 17)` essentially sets the C++ standard for this project to 17
4. `find_package(raylib REQUIRED)` - says find this package on this system while creating the binary and if you can't find then fail with error
5. `add_executable(myengine main.cpp)` - that's the executable name and the main file name , in this case there's only one file so we only need to add `main.cpp` . 
6. `target_link_libraries` - tie dependent libraries with your app

