option(ENABLE_RANDOM "Enable the Random Value Plugin" ON)
option(ENABLE_SECOND_TIMER "Enable the Second Timer Plugin" OFF)
option(ENABLE_TIMER "Enable the Timer Plugin" OFF)

if(ENABLE_RANDOM)

set(SRC_RANDOM
    random/random.cpp
)

add_library(
    lc3_random
    SHARED
    ${SRC_RANDOM}
)

target_link_libraries(
    lc3_random
    ${LIBLC3_LIBRARY}
)

install(TARGETS lc3_random LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_RANDOM)


if(ENABLE_SECOND_TIMER)

set(SRC_SECOND_TIMER
    second_timer/second_timer.cpp
)

add_library(
    lc3_second_timer
    SHARED
    ${SRC_SECOND_TIMER}
)

target_link_libraries(
    lc3_second_timer
    ${LIBLC3_LIBRARY}
)

install(TARGETS lc3_second_timer LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_SECOND_TIMER)

if(ENABLE_TIMER)

set(SRC_TIMER
    timer/timer.cpp
)

add_library(
    lc3_timer
    SHARED
    ${SRC_TIMER}
)

target_link_libraries(
    lc3_timer
    ${LIBLC3_LIBRARY}
)

install(TARGETS lc3_timer LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR})

endif(ENABLE_TIMER)

