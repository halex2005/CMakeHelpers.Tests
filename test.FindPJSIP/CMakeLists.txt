message(STATUS "####################################################")
message(STATUS "Try find PJSIP libraries")

set(PJSIP_DEBUG ON)
find_package(PJSIP)

if (NOT ${PJSIP_FOUND})
    message(SEND_ERROR "PJSIP libraries not found")
    return()
endif()

if (NOT "${PJSIP_LIBRARIES}" MATCHES "pjlib" OR NOT "${PJSIP_LIBRARIES}" MATCHES "pjsua")
    message(SEND_ERROR "pjsip libraries not found in libraries: ${PJSIP_LIBRARIES}")
    return()
endif()

