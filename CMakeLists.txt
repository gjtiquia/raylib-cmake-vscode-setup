cmake_minimum_required(VERSION 3.12)
project(example)

# Set Standard
set(CMAKE_CXX_STANDARD 17)

# Setting parameters for raylib
set(BUILD_EXAMPLES OFF CACHE BOOL "" FORCE) # don't build the supplied examples
set(BUILD_GAMES    OFF CACHE BOOL "" FORCE) # or games

add_subdirectory(external/raylib)

# Our Project
file(GLOB example_SRC CONFIGURE_DEPENDS 
    "src/*.h" 
    "src/*.cpp"
)

add_executable(${PROJECT_NAME} ${example_SRC})
target_link_libraries(${PROJECT_NAME} raylib)

# Checks if OSX and links appropriate frameworks (Only required on MacOS)
if (APPLE)
    target_link_libraries(${PROJECT_NAME} "-framework IOKit")
    target_link_libraries(${PROJECT_NAME} "-framework Cocoa")
    target_link_libraries(${PROJECT_NAME} "-framework OpenGL")
endif()
