
cmake_minimum_required(VERSION 3.6)

# Set the default build type to 'Release'
if (NOT CMAKE_BUILD_TYPE)	
	set(default_build_type "Release")
	message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
	set(CMAKE_BUILD_TYPE "${default_build_type}" CACHE STRING "Choose the type of build." FORCE)
endif()

option(LIBDWARF_INSTALL_TO_UNITTESTS "Install libraries to 'bin/unit-tests' tests (Windows only)." OFF)

set(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")

add_subdirectory(libdwarf)
add_subdirectory(libelf)
