option(ENABLE_MULTIPLY "Enable the Multiply Instruction Plugin" ON)

if(ENABLE_MULTIPLY)

set(SRC_MULTIPLY
    multiply/multiply.cpp
)

add_library(
    lc3_multiply
    SHARED
    ${SRC_MULTIPLY}
)

target_link_libraries(
    lc3_multiply
    ${LIBLC3_LIBRARY}
)

install(TARGETS lc3_multiply LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_MULTIPLY)

