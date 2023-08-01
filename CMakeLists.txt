cmake_minimum_required(VERSION 3.12)

project(RTCW-SP)

if(MSVC)
    add_compile_definitions(_CRT_SECURE_NO_WARNINGS _M_IX86 __i386__)
else()
endif()

add_subdirectory(src)