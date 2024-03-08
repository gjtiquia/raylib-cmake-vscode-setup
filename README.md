# Raylib CMake VSCode Setup

Useful Links

- [Raylib Wiki](https://github.com/raysan5/raylib/wiki)
- [Raylib Wiki - Working with CMake](https://github.com/raysan5/raylib/wiki/Working-with-CMake)
- [Raylib Wiki - Using Raylib in VSCode](https://github.com/raysan5/raylib/wiki/Using-raylib-in-VSCode)
- [raylib/projects/VSCode](https://github.com/raysan5/raylib/tree/master/projects/VSCode)
- [Raylib Wiki - Raylib Templates](https://github.com/raysan5/raylib/wiki/raylib-templates)
- [C99 CMake Template](https://github.com/SasLuca/raylib-cmake-template)
- [C++ CMake Template](https://github.com/SasLuca/raylib-cpp-cmake-template)
- [Using Libraries in C++ (Static Linking) - The Cherno](https://www.youtube.com/watch?v=or1dAmUO8k0&ab_channel=TheCherno)
- [Automatically add all files in a folder to a target using CMake - StackOverflow](https://stackoverflow.com/questions/3201154/automatically-add-all-files-in-a-folder-to-a-target-using-cmake)

## Setup

### Prerequisites

- Have a C/C++ compiler installed
  - VSCode Guide: <https://code.visualstudio.com/docs/languages/cpp#_install-a-compiler>

- Have `cmake` installed
  - Download binaries directly: <https://cmake.org/download/>
  - Download with package managers
    - MacOS: `brew install cmake`
    - Windows: `winget install kitware.cmake` or `choco install cmake`

### Steps

VSCode Extensions: C/C++ Extension Pack

1. Copy `raylib` source files from GitHub into `/external/raylib`
    - `raylib` itself also includes the `glfw` source code in `src/external/glfw`
    - In [C++ - The Cherno](https://youtu.be/or1dAmUO8k0?si=kBGf5NhYgnwWSLOv), this is also done to have all the dependencies self contained in a single repository. Fixing to a single version, no fetching, less complexity, having everything as a static library.

2. Create `.gitignore` and ignore `.vscode` and `build`.
    - `/build` will be created during CMake compile, may differ between platforms,
    - `/.vscode` may differ between development machines, ignoring it is safest.

## Compile

Reference: <https://github.com/raysan5/raylib/tree/master/projects/CMake#readme>

### Desktop

Compile

```bash
cmake -B build
cmake --build build
```

Run the executable with the command

```bash
./build/example
```

Instead of running the commands by hand in VSCode, can set it up with VSCode extensions.
(Ref: <https://youtu.be/kekw7eGb8Mw?si=2pBARMwzFo_XmHs_&t=531>)

1. __Command Palette > CMake: Configure__
2. Choose a compiler (eg. Clang on MacOS)
3. Build + Play button on the status bar at bottom of the window works.
4. Or can Build + Play with CMake extension in the sidebar.
