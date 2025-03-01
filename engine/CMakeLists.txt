# The engine library
add_library(engine SHARED ${ENGINE_SOURCES})

# When the target is built, move the library to the final build directory, so we can share the result more easily
add_custom_command(TARGET engine POST_BUILD COMMAND mv ${CMAKE_CURRENT_BINARY_DIR}/libengine.so ${FINAL_BUILD_DIR}/)
