option(ENABLE_BWLCD "Enable the Black White LCD Plugin (Requires complx and wxWidgets)" ON)
option(ENABLE_COLORLCD "Enable the Color LCD Plugin (Requires complx and wxWidgets)" ON)
option(ENABLE_PINGER "Enable the Pinger Plugin" ON)

if(ENABLE_BWLCD OR ENABLE_COLORLCD)
    set(wxWidgets_USE_LIBS core base)
    find_package(wxWidgets REQUIRED QUIET)
    include(${wxWidgets_USE_FILE})
endif(ENABLE_BWLCD OR ENABLE_COLORLCD)

if(ENABLE_BWLCD)

set(SRC_BWLCD
    bwlcd/bwlcd.cpp
    bwlcd/bwlcdgui.cpp
)

add_library(
    lc3_bwlcd
    SHARED
    ${SRC_BWLCD}
)

target_link_libraries(
    lc3_bwlcd
    ${lc3_LIBRARIES}
    ${wxWidgets_LIBRARIES}
)

install(TARGETS lc3_bwlcd LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_BWLCD)

if(ENABLE_COLORLCD)

set(SRC_COLORLCD
    colorlcd/colorlcd.cpp
    colorlcd/colorlcdgui.cpp
)

add_library(
    lc3_colorlcd
    SHARED
    ${SRC_COLORLCD}
)

target_link_libraries(
    lc3_colorlcd
    ${lc3_LIBRARIES}
    ${wxWidgets_LIBRARIES}
)

install(TARGETS lc3_colorlcd LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_COLORLCD)

if(ENABLE_PINGER)

set(SRC_PINGER
    pinger/pinger.cpp
)

add_library(
    lc3_pinger
    SHARED
    ${SRC_PINGER}
)

target_link_libraries(
    lc3_pinger
    ${lc3_LIBRARIES}
)

install(TARGETS lc3_pinger LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_PINGER)
