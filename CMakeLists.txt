cmake_minimum_required(VERSION 3.6)

# Set the default build type to 'Release'.
if (NOT CMAKE_BUILD_TYPE)
	set(default_build_type "Release")
	message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
	set(CMAKE_BUILD_TYPE "${default_build_type}" CACHE STRING "Choose the type of build." FORCE)
endif()

# On Linux and macOS, set RPATH relative to the origin of the installed
# libraries so that e.g. libdwarf can find libelf after installation. This
# allows us to move the installation directory into a different location after
# installation, which is useful e.g. when the installation is performed on one
# machine but we want to run the executables on a different machine.
#
# On Windows, there is no need to set anything as DLLs are usually installed
# into the binary directory, where they are automatically picked up by
# executables.
#
# For more details, see
#  - https://cmake.org/Wiki/CMake_RPATH_handling
if(APPLE)
	set(CMAKE_INSTALL_RPATH "@executable_path")
elseif(UNIX)
	set(CMAKE_INSTALL_RPATH "$ORIGIN")
endif()

add_subdirectory(libdwarf)
add_subdirectory(libelf)
