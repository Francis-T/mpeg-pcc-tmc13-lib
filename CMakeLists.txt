cmake_minimum_required(VERSION 3.0)
project (tmc3 CXX)

include( CheckCXXCompilerFlag )
CHECK_CXX_COMPILER_FLAG( "-std=c++11" COMPILER_SUPPORTS_CXX11 )
CHECK_CXX_COMPILER_FLAG( "-std=c++0x" COMPILER_SUPPORTS_CXX0X )

if (COMPILER_SUPPORTS_CXX11)
 set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11" )
elseif (COMPILER_SUPPORTS_CXX0X)
 set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x" )
else ()
 MESSAGE(STATUS "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif ()

#  Make it so that TMC3 builds as a Library by DEFAULT, and make building as 
#    an executable (i.e the original behavior) accessible via toggle
if ( CMAKE_BUILD_TYPE STREQUAL "Executable" )
    set ( COMPILE_TMC3_AS_EXE ON )
endif()

add_subdirectory(tmc3)
