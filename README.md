# libprocmon.lib Cmake Example

### Based on `https://github.com/progmboy/openprocmon` project.

Simple self-reminding example of using pre-build static libprocmon.lib library with `Cmake` based project.

## Using

This project was tested with MSVC builder. Use it to get same result.

1. Clone

       link

2. Configure

        cmake . -B./build -G "Visual Studio 16 2019" -T host=x64 -A x64

3. Build

        cmake --build ./build --config Release --target ALL_BUILD

4. Copy original Procmon (SYSInternals proj) driver (%systemroot%/System32/drivers/PROCMON24.SYS) to `build\apps\Release\` directory and rename it to `procmon.sys`

5. Run `build\apps\Release\openprocmon_test.exe` from terminal with admin rights.


## Openprocmon library build

Openprocmon sdk library was build this way:

1. Clone `https://github.com/progmboy/openprocmon.git` and follow environment prepare instructions.

2. Configuration:

        cmake . -G "Visual Studio 16 2019" -A X64 -DWTL_ROOT_DIR=D:\code\WTL10_10320\ -DWDK_WINVER=0x0A00

3. Build

        cmake --build . --config Release

## Using with VS Code

Should use Visual Studio build tools as well.

1. Download and install `twxs.cmake` extention. 
2. Run `Cmake: Configure` from Command Pallete. Choose MSVC compiler for x64 platform. Choose `Release` target for building.
3. Build using `Cmake: Build` from Command Pallete.