## A "Hell, world" executable

create CMakeLists.txt
```
cmake_minimum_required(VERSION 3.12)
project(MyProject VERSION 1.0.0)

add_executable(cmake-good main.cpp)
```
- run `cmake ..` command on build directory.
- check generation step failed.
```
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1a\build>cmake ..
-- Building for: Visual Studio 17 2022
-- Selecting Windows SDK version 10.0.22000.0 to target Windows 10.0.19045.
-- The C compiler identification is MSVC 19.35.32215.0
-- The CXX compiler identification is MSVC 19.35.32215.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.35.32215/bin/Hostx64/x64/cl.exe - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.35.32215/bin/Hostx64/x64/cl.exe - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
CMake Error at CMakeLists.txt:4 (add_executable):
  Cannot find source file:

    main.cpp

  Tried extensions .c .C .c++ .cc .cpp .cxx .cu .mpp .m .M .mm .ixx .cppm .h
  .hh .h++ .hm .hpp .hxx .in .txx .f .F .for .f77 .f90 .f95 .f03 .hip .ispc


CMake Error at CMakeLists.txt:4 (add_executable):
  No SOURCES given to target: cmake-good


CMake Generate step failed.  Build files cannot be regenerated correctly.
```

Ok. Let's fix this.

add executable, add library, target source, ... : use relatvie path to the directory where the target was created.

make main.cpp file.

run cmake command again then configuring, generating done and build iles have been written to build directory.

run `cmake --build .` command. (exactly, `cmake --build {build-directory}`). Then, executable file is created.

run `cd Debug` command.

run `cmake-good` command.
