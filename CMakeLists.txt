cmake_minimum_required(VERSION 3.18)
project(romlister VERSION 1.2.1 LANGUAGES C)

# Set up specifications for the C compiler.
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)

# Set output directories.
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Include its submodule.
add_subdirectory(submodules/LibPacReader)

# Gather the files.
FILE(GLOB SOURCES src/*.c)

# Output the project.
add_executable(romlister ${SOURCES})
target_include_directories(romlister PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/headers)
target_link_libraries(romlister PRIVATE pacreader pacsorter pacset)
install(TARGETS romlister DESTINATION bin)
