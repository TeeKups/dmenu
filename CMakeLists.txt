# Guaranteed to work with this. Likely works with earlier versions as well.
# Feel free to try, but I'm not going to.
cmake_minimum_required(VERSION 3.25)
project(dmenu VERSION 5.0)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED YES)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -pedantic -Wall -Os")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DVERSION=${VERSION}")

add_executable(dmenu
    dmenu/src/dmenu.c
    dmenu/src/drw.c
    dmenu/src/util.c
)

include_directories(dwm
    /usr/X11R6/include
    /usr/include/freetype2
)

target_include_directories(dmenu
    PRIVATE
        dmenu/include
        libs/arg
)

target_link_libraries(dmenu
    X11
    Xinerama
    fontconfig
    Xft
)

add_executable(stest
    stest/src/stest.c
)

target_include_directories(stest
    PRIVATE
        stest/include
        libs/arg
)

target_link_libraries(stest
    X11
    Xinerama
    fontconfig
    Xft
)
