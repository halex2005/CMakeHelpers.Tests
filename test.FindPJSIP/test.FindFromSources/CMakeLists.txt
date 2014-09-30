CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

message(STATUS "####################################################")
message(STATUS "Try find PJSIP libraries from sources")


set(PJSIP_DEBUG ON)
set(PJSIP_USE_BUILD_FROM_SOURCE ON)
set(PJSIP_USE_STATIC_RUNTIME ON)
find_package(PJSIP)

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

if (WIN32 AND (NOT "${PJSIP_LIBRARIES}" MATCHES "Static"))
    message(SEND_ERROR "pjsip libraries must use static runtime when PJSIP_USE_BUILD_FROM_SOURCE is ON: ${PJSIP_LIBRARIES}")
    return()
endif()

