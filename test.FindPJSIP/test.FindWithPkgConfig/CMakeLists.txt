CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

message(STATUS "####################################################")
message(STATUS "Try find PJSIP libraries with PkgConfig")

set(PKG_CONFIG_PATH_OLD $ENV{PKG_CONFIG_PATH})
set(ENV{PKG_CONFIG_PATH} ${CMAKE_CURRENT_BINARY_DIR}/pkgconfig)
file(MAKE_DIRECTORY $ENV{PKG_CONFIG_PATH})
message("ENV{PKG_CONFIG_PATH} = $ENV{PKG_CONFIG_PATH}")

set(PJSIP_DEBUG ON)
set(PJSIP_USE_PKGCONFIG ON)
set(PJSIP_REGENERATE_PKGCONFIG ON)
find_package(PJSIP)

set(ENV{PKG_CONFIG_PATH} ${PKG_CONFIG_PATH_OLD})
message("ENV{PKG_CONFIG_PATH} = $ENV{PKG_CONFIG_PATH}")

if (NOT ${PJSIP_FOUND})
    message(SEND_ERROR "PJSIP libraries not found")
    return()
endif()

if (UNIX AND (NOT "${PJSIP_LIBRARIES}" MATCHES "pjlib" OR NOT "${PJSIP_LIBRARIES}" MATCHES "pjsua"))
    message(SEND_ERROR "pjsip libraries not found in libraries: ${PJSIP_LIBRARIES}")
    return()
endif()

if (WIN32 AND (NOT "${PJSIP_LIBRARIES}" MATCHES "libpjproject"))
    message(SEND_ERROR "pjsip libraries not found in libraries: ${PJSIP_LIBRARIES}")
    return()
endif()

if (WIN32 AND (NOT "${PJSIP_LIBRARIES}" MATCHES "Dynamic"))
    message(SEND_ERROR "pjsip libraries must use dynamic runtime when PJSIP_USE_BUILD_FROM_SOURCE is not defined: ${PJSIP_LIBRARIES}")
    return()
endif()
