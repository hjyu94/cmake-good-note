## Runing CMake
lecture: https://youtu.be/lI2nwZSMvlE

### cmake command
1. create CMakeLists.txt
2. mkdir ./build
3. cd ./build
4. cmake ..
5. check what is created.

```
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec0b\build>cmake ..
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
-- Generating done
-- Build files have been written to: C:/Users/GLAB/Downloads/dev/cmake-good-note/lec0b/build
```

### ccmake command
- text user interface.
- It's not exactly a command line program.
- command: cmake ..
- It's good to view an existing cmake project. Run `cmake ..` command.

### cmake-gui
- graphical user interface.
- It's also good for existing cmake project.
1. choose directory path
  - source code path: C:/Users/GLAB/Downloads/dev/cmake-good-note/lec0b
  - build path: C:/Users/GLAB/Downloads/dev/cmake-good-note/lec0b/build
2. click 'Configure' button
3. click 'Finish' button
4. check cache files on GUI tool.
5. click 'Generate' button
6. check the whole files created.
