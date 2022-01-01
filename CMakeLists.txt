# CMakeList.txt : CMake project for Pixel, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

project ("Pixel")

set(CMAKE_TOOLCHAIN_FILE $ENV{CMAKE_TOOLCHAIN_FILE})
set(VCPKG_TARGET_TRIPLET "$ENV{VCPKG_DEFAULT_TRIPLET}" CACHE STRING "")
set(CMAKE_CXX_STANDARD 17)

find_package(SDL2 CONFIG REQUIRED)

INCLUDE_DIRECTORIES(
  "$ENV{CMAKE_TOOLCHAIN_FILE}/installed/$ENV{VCPKG_DEFAULT_TRIPLET}/include/SDL"
)

add_executable (Pixel "Pixel.cpp" "Pixel.h")

target_link_libraries(Pixel PRIVATE SDL2::SDL2 SDL2::SDL2main)