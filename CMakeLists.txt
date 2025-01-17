cmake_minimum_required(VERSION 3.5.0)
project(TerrainGen LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set Policy CMP0072
if (POLICY CMP0072)
    cmake_policy(SET CMP0072 NEW)
endif()

# Define source and include directory 
set(SRC_DIR ${CMAKE_SOURCE_DIR}/src)
set(INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include)

# Recursively find all .cpp files in the source directory
file(GLOB_RECURSE SOURCES ${SRC_DIR}/*.cpp)

# Add the include directory
include_directories(${INCLUDE_DIR})

# Add the external directory to the build
add_subdirectory(external)

# Create the executable with the collected sources
add_executable(${PROJECT_NAME} ${SOURCES})

# Link libraries
find_package(OpenGL REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE glad glfw OpenGL::GL)
