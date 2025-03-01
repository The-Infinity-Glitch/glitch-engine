cmake_minimum_required(VERSION 3.10)

# For Code::Blocks generator
set(CMAKE_CODEBLOCKS_EXCLUDE_EXTERNAL_FILES ON)

# For other code editors
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# The main project
set(MAIN_PROJECT glitch_engine)

project(${MAIN_PROJECT})

add_custom_target(${MAIN_PROJECT} ALL)

# The root source and build directories
set(ROOT_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(ROOT_BUILD_DIR ${CMAKE_CURRENT_BINARY_DIR})

# The final build directory
set(FINAL_BUILD_DIR ${ROOT_BUILD_DIR}/result)

if (NOT EXISTS ${FINAL_BUILD_DIR})
    message("Creating final build directory: ${FINAL_BUILD_DIR}")

    add_custom_command(TARGET ${MAIN_PROJECT} POST_BUILD COMMAND mkdir ${FINAL_BUILD_DIR})
endif()

# The engine library source files and includes
file(GLOB_RECURSE ENGINE_SOURCES ${ROOT_SOURCE_DIR}/engine/src/*.cpp)
set(ENGINE_INCLUDES ${ROOT_SOURCE_DIR}/engine/include/)

# The sandbox executable source files
file(GLOB_RECURSE SANDBOX_SOURCES ${ROOT_SOURCE_DIR}/sandbox/src/*.cpp)

# The subdirs
add_subdirectory(${ROOT_SOURCE_DIR}/engine)

# The subdirs
add_subdirectory(${ROOT_SOURCE_DIR}/sandbox)
