cmake_minimum_required(VERSION 3.10)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project(anotherRegeared)

add_compile_options (-fdiagnostics-color=always)
add_compile_options (-Wfatal-errors)
add_compile_options(-march=native)

if(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    add_compile_options("/W4")
    message("Compiling with: Microsoft Compiler")
elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
    add_compile_options("-Wall" "-Wextra" "-pedantic")
    message("Compiling with: GCC Compiler")
elseif(CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    #add_compile_options("-Weverything")
    add_compile_options(
            "-Wall"
            "-Wextra"
            "-pedantic"
            "-Wfatal-errors"
            "-Wno-c++98-compat"
            "-Wno-c++98-c++11-compat-binary-literal"
            "-Wno-c++98-compat-pedantic"
    )
    message("Compiling with: Clang Compiler")
endif()



find_package(fmt)


add_executable(anotherRegeared
        src/main.cpp)

target_include_directories(anotherRegeared PUBLIC bitmap)

target_link_libraries(anotherRegeared PRIVATE
    fmt::fmt-header-only
    )
