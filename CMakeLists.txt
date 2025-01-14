cmake_minimum_required(VERSION 3.10)

project(MySDLProject)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set the compiler to MinGW
set(CMAKE_C_COMPILER "/usr/bin/x86_64-w64-mingw32-gcc")
set(CMAKE_CXX_COMPILER "/usr/bin/x86_64-w64-mingw32-g++")

# Set the target system to Windows
set(CMAKE_SYSTEM_NAME Windows)

# Include SDL3 headers
include_directories(/usr/local/SDL3-3.1.8/x86_64-w64-mingw32/include)

# Link SDL3 libraries
link_directories(/usr/local/SDL3-3.1.8/x86_64-w64-mingw32/lib)

# Add the executable
add_executable(SDLProject src/main.cpp)
target_link_libraries(SDLProject SDL3)

# Embed SDL3.dll or .lib file
add_custom_command(TARGET SDLProject POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    /usr/local/SDL3-3.1.8/x86_64-w64-mingw32/bin/SDL3.dll
    $<TARGET_FILE_DIR:SDLProject>)