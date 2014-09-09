message(STATUS "####################################################")
message(STATUS "Try find resiprocate with exact version")

find_package(Resiprocate 1.9 EXACT)

if (NOT ${Resiprocate_FOUND})
    message(SEND_ERROR "exact version of resiprocate not found")
    return()
endif()

if (NOT "${Resiprocate_LIBRARIES}" MATCHES "recon" OR
    NOT "${Resiprocate_LIBRARIES}" MATCHES "reflow" OR
    NOT "${Resiprocate_LIBRARIES}" MATCHES "resip" OR
    NOT "${Resiprocate_LIBRARIES}" MATCHES "rutil" OR
    NOT "${Resiprocate_LIBRARIES}" MATCHES "repro" OR
    NOT "${Resiprocate_LIBRARIES}" MATCHES "dum"
    )
    message(SEND_ERROR "requested components not found in libraries: ${Resiprocate_LIBRARIES}")
    return()
endif()
