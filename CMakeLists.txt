cmake_minimum_required(VERSION 3.10)

# Set the project name
project(FIXParser VERSION 1.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Set output directories for binaries
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

# Add the include directory
include_directories(${PROJECT_SOURCE_DIR}/include)

# Add source files
set(SOURCES
    src/main.cpp
    src/FixParser.cpp
)

# Add header files
set(HEADERS
    include/FixParser.h
)

# Create the executable
add_executable(FIXParser ${SOURCES} ${HEADERS})

# Add any necessary libraries
# For example, if you're using Boost, you might need something like this:
# find_package(Boost REQUIRED)
# target_link_libraries(FIXParser Boost::boost)
target_compile_options(FIXParser PRIVATE -Wall -Wextra -pedantic -Werror)


# Add versioning info
#configure_file(
#    ${PROJECT_SOURCE_DIR}/Config.h.in
#    ${PROJECT_BINARY_DIR}/Config.h
#)

# Include binary directory to find Config.h
target_include_directories(FIXParser PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           "${PROJECT_SOURCE_DIR}/include")
