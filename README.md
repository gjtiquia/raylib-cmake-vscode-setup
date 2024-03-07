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

Compile

```bash
cmake -B build
cmake --build build
```

Run the executable with the command

```bash
./build/example
```

### Web

Compiling for the web requires the [Emscripten SDK](https://emscripten.org/docs/getting_started/downloads.html)

- MacOS
  - Follow instructions in the link above; or  
  - Homebrew (Not officially supported but convenient)
    - Run `brew install emscripten`
    - To fix VSCode include error for `#include <emscripten/emscripten.h>`
      - Ref: <https://gist.github.com/wayou/59f3a8e4fbab050fbb32e94dd9582660>
      - Run `brew info emscripten` to get the installation location.
        - eg. /usr/local/Cellar/emscripten/3.1.55
      - __Command + Shift + P > C/C++ Edit Configurations (JSON)__ to go to `/.vscode/c_pp_properties.json`
      - paste `/usr/local/Cellar/emscripten/**` into `includePath`

Compile (Note: Ensure the build directory is clean and empty without build artifacts from Desktop build)

```bash
mkdir build
cd build
emcmake cmake .. -DPLATFORM=Web -DCMAKE_BUILD_TYPE=Release -DCMAKE_EXE_LINKER_FLAGS="-s USE_GLFW=3" -DCMAKE_EXECUTABLE_SUFFIX=".html"
emmake make
```

Serve the html, js and wasm with a static file server ([Emscripten Docs](https://emscripten.org/docs/getting_started/FAQ.html#faq-local-webserver))

```bash
# node
npx http-server

# python
python3 -m http.server
```
