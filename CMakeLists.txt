cmake_minimum_required(VERSION 3.14)

project(project_name
    DESCRIPTION "project_desc"
    LANGUAGES CXX
    VERSION 0.0.9
    )
include(CTest)

# Later utilise features in C++20
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# add CPM
include(cmake/CPM.cmake)

set(CMAKE_POLICY_DEFAULT_CMP0077 NEW)			# don't let OPTION erase non-cache variables
set(CMAKE_CXX_EXTENSIONS OFF CACHE INTERNAL "" FORCE)	# disable compiler extensions
set(CMAKE_POSITION_INDEPENDENT_CODE ON)			# enable PIC

include(cmake/CPM.cmake)	# Adding CPM for dependency management()

# CPMAddPackage("gh:adi-g15/graphMat@1.0.1")   # Can add any cmake based dependency, CPM supports better methods too

# executable
file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.?pp")		# grab all *.?pp files
add_executable(${PROJECT_NAME} ${SOURCES})

target_include_directories(${PROJECT_NAME} PRIVATE include)

