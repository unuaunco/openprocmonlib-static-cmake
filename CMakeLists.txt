cmake_minimum_required(VERSION 3.14..3.19)

project(
  OpenProcMonTest
  VERSION 0.1
  DESCRIPTION "Test example of openprocmon sdk: https://github.com/progmboy/openprocmon"
  LANGUAGES CXX
  )

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

if (CMAKE_CXX_COMPILER_VERSION VERSION_GREATER_EQUAL 19.12.25835)
    set(CMAKE_CXX20_STANDARD_COMPILE_OPTION "-std:c++latest")
    set(CMAKE_CXX20_EXTENSION_COMPILE_OPTION "-std:c++latest")
endif()

if (UNIX)
  message(status "This code use WIN32 libraries, abort ...")
  return()
else()
  message(status "Setting MSVC flags")
  set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
  set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
endif()
message(status "** CMAKE_CXX_FLAGS: ${CMAKE_CXX_FLAGS}")

add_definitions(-DUNICODE -D_UNICODE)

# Declare headers folder
source_group(
  TREE ${CMAKE_SOURCE_DIR}/include
  PREFIX "Header Files")
message(status "** Include folders are added ${CMAKE_SOURCE_DIR}/include")

add_subdirectory(apps)