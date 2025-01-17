# GLAD SETUP
set(GLAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}/glad)
set(GLAD_SRC ${GLAD_DIR}/src/glad.c)
set(GLAD_INCLUDE ${GLAD_DIR}/include)

# Create a static library for GLAD
add_library(glad STATIC ${GLAD_SRC})

# Specify include directories for GLAD
target_include_directories(glad PUBLIC ${GLAD_INCLUDE})

# Add GLFW
add_subdirectory(glfw)