cmake_minimum_required(VERSION 3.22)

project(AudioPluginStarter)

set(CMAKE_CXX_STANDARD 20)

set(LIB_DIR  ${CMAKE_CURRENT_SOURCE_DIR}/libs)
include(cmake/cpm.cmake)

CPMAddPackage(
	NAME JUCE
	GITHUB_REPOSITORY juce-framework/JUCE
	GIT_TAG 7.0.5
	VERSION 7.0.5
	SOURCE_DIR ${LIB_DIR}/juce
)

#When we use Windows:
if(MSVC)
	add_compile_options(/Wall /WX)
else()
#This forces that all warnings be treated as errors:
	add_compile_options(-Wall  -Wextra -Wpedantic) 
endif()

add_subdirectory(plugin)