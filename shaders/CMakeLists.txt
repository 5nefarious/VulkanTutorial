set (SHADER_SOURCES
    "hello.vert"
    "hello.frag"
)

list (TRANSFORM SHADER_SOURCES PREPEND "${CMAKE_CURRENT_SOURCE_DIR}/")

add_custom_target (shaders ALL
    COMMAND glslc -c ${SHADER_SOURCES}
    DEPENDS ${SHADER_SOURCES}
    COMMENT Compiling shaders...
    SOURCES ${SHADER_SOURCES}
)
