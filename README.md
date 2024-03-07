# Raylib Project VSCode Setup

Useful Links

- [Raylib Wiki](https://github.com/raysan5/raylib/wiki)
- [Raylib Wiki - Working with CMake](https://github.com/raysan5/raylib/wiki/Working-with-CMake)

## Setup

### Prerequisites

- Have `cmake` installed
  - MacOS: `brew install cmake`

### Steps

1. Copy `CMakeLists.txt` and `core_basic_window.c` from [raylib/projects/CMake](https://github.com/raysan5/raylib/tree/master/projects/CMake)
2. Create `.gitignore` and ignore `.vscode` and `build`.
    - `/build` will be created during compile.
    - `/.vscode` will be created with `files.associations` when navigating header references.

## Compile

Reference: <https://github.com/raysan5/raylib/tree/master/projects/CMake#readme>

### Desktop

```bash
cmake -B build
cmake --build build
```

### Web

Compiling for the web requires the [Emscripten SDK](https://emscripten.org/docs/getting_started/downloads.htmls):

```bash
mkdir build
cd build
emcmake cmake .. -DPLATFORM=Web -DCMAKE_BUILD_TYPE=Release -DCMAKE_EXE_LINKER_FLAGS="-s USE_GLFW=3" -DCMAKE_EXECUTABLE_SUFFIX=".html"
emmake make
```
