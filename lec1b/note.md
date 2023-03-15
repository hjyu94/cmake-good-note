## Adding a library

move some code to a library.

```
+ hello.cpp
+ hello.hpp
```

Update main.cpp.

For now, CMakeLists.txt is like below.

```
cmake_minimum_required(VERSION 3.12)
project(MyProject VERSION 1.0.0)

add_executable(cmake-good main.cpp)
```

Run configuration.
```
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build>cmake ..
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
-- Build files have been written to: C:/Users/GLAB/Downloads/dev/cmake-good-note/lec1b/build
```

But make command failed.
```
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build>cmake --build .
MSBuild version 17.5.0+6f08c67f3 for .NET Framework

  Checking Build System
  Building Custom Rule C:/Users/GLAB/Downloads/dev/cmake-good-note/lec1b/CMakeLists.txt
  main.cpp
main.obj : error LNK2019: "void __cdecl hello::say_hello(void)" (?say_hello@hello@@YAXXZ)mai
n 함수에서 참조되는 확인할 수 없는 외부 기호 [C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build\cmake-go
od.vcxproj]
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build\Debug\cmake-good.exe : fatal error L
NK1120: 1개의 확인할 수 없는 외부 참조입니다. [C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build\cmak
e-good.vcxproj]

```

Add below to CMakeLists.txt
```
add_library(
    say-hello
    hello.hpp
    hello.cpp
)
```

By default, library mode is static.
(INTERFACE, OBJECT, STATIC or SHARED)

but still linking failed.

To link this library into executable file. Add like below.
```
target_link_library({project-name} {link-interface-mode} {library})
```

Then run `cmake --build .` command again.

Success!

check linker dependency.
```
C:\Users\GLAB\Downloads\dev\cmake-good-note\lec1b\build\Debug>ldd cmake-good
        ntdll.dll => /c/Windows/SYSTEM32/ntdll.dll (0x7fffbd610000)
        KERNEL32.DLL => /c/Windows/System32/KERNEL32.DLL (0x7fffbc470000)
        KERNELBASE.dll => /c/Windows/System32/KERNELBASE.dll (0x7fffbb370000)
        apphelp.dll => /c/Windows/SYSTEM32/apphelp.dll (0x7fffb8460000)
        VCRUNTIME140D.dll => /c/Windows/SYSTEM32/VCRUNTIME140D.dll (0x7fffb3ff0000)
        ucrtbased.dll => /c/Windows/SYSTEM32/ucrtbased.dll (0x7fff4a870000)
        MSVCP140D.dll => /c/Windows/SYSTEM32/MSVCP140D.dll (0x7fff99730000)
        VCRUNTIME140_1D.dll => /c/Windows/SYSTEM32/VCRUNTIME140_1D.dll (0x7fffb8430000)
        ole32.dll => /c/Windows/System32/ole32.dll (0x7fffbd1c0000)
        ucrtbase.dll => /c/Windows/System32/ucrtbase.dll (0x7fffbb160000)
        RPCRT4.dll => /c/Windows/System32/RPCRT4.dll (0x7fffbc530000)
        combase.dll => /c/Windows/System32/combase.dll (0x7fffbce30000)
        GDI32.dll => /c/Windows/System32/GDI32.dll (0x7fffbd190000)
        win32u.dll => /c/Windows/System32/win32u.dll (0x7fffbafc0000)
        gdi32full.dll => /c/Windows/System32/gdi32full.dll (0x7fffbae60000)
        msvcp_win.dll => /c/Windows/System32/msvcp_win.dll (0x7fffbb2d0000)
        USER32.dll => /c/Windows/System32/USER32.dll (0x7fffbc680000)
```

pass environment variable to command: 
- `cmake -D BUILD_SHARED_LIBS=TRUE .`