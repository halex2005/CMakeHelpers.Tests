CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/CMakeHelpers")

option(TEST_FindResiprocate ON)
option(TEST_FindPJSIP ON)
option(TEST_GenerateProductVersion ON)

if (TEST_FindResiprocate)
    add_subdirectory(test.FindResiprocate)
endif()
if (TEST_FindPJSIP)
    add_subdirectory(test.FindPJSIP)
endif()
if (TEST_GenerateProductVersion)
    add_subdirectory(test.GenerateProductVersion)
endif()
