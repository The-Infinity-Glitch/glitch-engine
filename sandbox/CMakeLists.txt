# The sandbox executable
set(EXE sandbox)

add_executable(${EXE} ${SANDBOX_SOURCES})

# Include paths
target_include_directories(${EXE} PUBLIC ${ENGINE_INCLUDES})

# Link the engine library, this is the engine library that we moved to the final build directory
target_link_libraries(${EXE} PRIVATE ${FINAL_BUILD_DIR}/libengine.so)

# Move the executable to the final build directory, so we can share the result more easily
add_custom_command(TARGET ${EXE} POST_BUILD COMMAND cp ${CMAKE_CURRENT_BINARY_DIR}/${EXE} ${FINAL_BUILD_DIR}/)
