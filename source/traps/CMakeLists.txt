option(ENABLE_UDIV "Enable the UDIV Trap Plugin" ON)

if(ENABLE_UDIV)

set(SRC_UDIV
    udiv/udiv.cpp
)

add_library(
    lc3_udiv
    SHARED
    ${SRC_UDIV}
)

target_link_libraries(
    lc3_udiv
    ${lc3_LIBRARIES}
)

install(TARGETS lc3_udiv LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_UDIV)

