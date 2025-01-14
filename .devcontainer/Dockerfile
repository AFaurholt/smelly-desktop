FROM debian:latest

# Update the package list and install any available updates
RUN apt-get update && apt-get upgrade -y

# Install MinGW libraries
RUN apt-get install -y mingw-w64

# Install GCC and CMake
RUN apt-get install -y gcc cmake

# Install dependencies for building SDL3 from source
RUN apt-get install -y build-essential libasound2-dev libpulse-dev libaudio-dev libx11-dev libxext-dev libxrandr-dev libxcursor-dev libxi-dev libxinerama-dev libxxf86vm-dev libxss-dev libgl1-mesa-dev libdbus-1-dev libudev-dev libgles2-mesa-dev libegl1-mesa-dev libibus-1.0-dev fcitx-libs-dev

# Install wget
RUN apt-get install -y wget unzip

# Download precompiled SDL3 Windows binaries
RUN wget https://www.libsdl.org/release/SDL3-devel-3.0.0-mingw.tar.gz -O SDL3-mingw.tar.gz && \
    tar -xzf SDL3-mingw.tar.gz -C /usr/local && \
    rm SDL3-mingw.tar.gz

# Clean up to reduce the image size
RUN apt-get clean && rm -rf /var/lib/apt/lists/*