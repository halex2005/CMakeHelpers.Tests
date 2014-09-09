message(STATUS "####################################################")
message(STATUS "Try find resiprocate components with minimal version")

find_package(Resiprocate 1.9 COMPONENTS recon reflow)

if (NOT ${Resiprocate_FOUND})
    message(SEND_ERROR "specific version of resiprocate components not found")
    return()
endif()

if (NOT "${Resiprocate_LIBRARIES}" MATCHES "recon" OR NOT "${Resiprocate_LIBRARIES}" MATCHES "reflow")
    message(SEND_ERROR "requested components recon and reflow not found in libraries: ${Resiprocate_LIBRARIES}")
    return()
endif()

if ("${Resiprocate_LIBRARIES}" MATCHES "(resip|dum|rutil|repro)")
    message(SEND_ERROR "found more libraries than requested: ${Resiprocate_LIBRARIES}")
    return()
endif()