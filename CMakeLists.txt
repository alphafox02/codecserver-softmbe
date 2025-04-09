cmake_minimum_required(VERSION 3.6)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

project(codecserver-libsoftmbe VERSION 0.0.1)

# Ensure install prefix is set to /usr
set(CMAKE_INSTALL_PREFIX "/usr" CACHE PATH "Install path prefix" FORCE)

# Ensure proper library install path
set(CMAKE_INSTALL_LIBDIR "/usr/lib/x86_64-linux-gnu" CACHE PATH "Library directory" FORCE)

enable_language(CXX)
set(CMAKE_CXX_STANDARD 11)

#include(GNUInstallDirs)
include(FindProtobuf)

find_package(Protobuf 3.0 REQUIRED)
find_package(CodecServer REQUIRED)

# Include directories for codecserver
include_directories("/usr/include/codecserver") # FIXME: cmake should do this on its own

# Set compiler flags
SET(CMAKE_CXX_FLAGS_DEBUG "-g -O3 -rdynamic")
SET(CMAKE_C_FLAGS_DEBUG "-g -O3")
SET(CMAKE_CXX_FLAGS_RELEASE "-O3 -rdynamic")
SET(CMAKE_C_FLAGS_RELEASE "-O3")

# Add the src directory
add_subdirectory(src)
