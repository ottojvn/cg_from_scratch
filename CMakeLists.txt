cmake_minimum_required(VERSION 4.0.1)
project(cg_from_scratch)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(${CMAKE_SOURCE_DIR}/include)

include(FetchContent)

FetchContent_Declare(
  sdl3
  GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
  GIT_TAG release-3.2.10)
FetchContent_MakeAvailable(sdl3)

set(SOURCES src/main.cpp)

# Create your game executable target as usual
add_executable(${PROJECT_NAME} ${SOURCES})

# Link to the actual SDL3 library.
target_link_libraries(${PROJECT_NAME} PRIVATE SDL3::SDL3)
