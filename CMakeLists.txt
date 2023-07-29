SET(CMAKE_OSX_DEPLOYMENT_TARGET "10.15" CACHE STRING "Minimum OS X deployment version")
set(CMAKE_C_STANDARD 11)
cmake_minimum_required(VERSION 3.15 FATAL_ERROR)
project(AudioUnitSDK VERSION 1.0.0 LANGUAGES CXX)

file(GLOB_RECURSE SOURCES "include/*")
file(GLOB_RECURSE HEADERS "src/*")

if(NOT ("${CMAKE_SOURCE_DIR}" STREQUAL "${CMAKE_CURRENT_SOURCE_DIR}"))
  set(AudioUnitSDKIncludes ${CMAKE_CURRENT_SOURCE_DIR}/include PARENT_SCOPE)
endif()

add_library(${PROJECT_NAME} STATIC ${SOURCES} ${HEADERS})
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

