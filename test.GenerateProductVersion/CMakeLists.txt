include(generate_product_version)

generate_product_version(ProductVersionFiles
    NAME MyProduct
    VERSION_MAJOR 3
    VERSION_MINOR 2
    VERSION_PATCH 12
    VERSION_REVISION 30303
    COMPANY_NAME MyCompany)

message("ProductVersionFiles=${ProductVersionFiles}")

list(LENGTH ProductVersionFiles ListLength)
if (NOT "${ListLength}" STREQUAL "2")
    message(SEND_ERROR "ListLength=${ListLength}, 2 expected")
    return()
endif()

list(GET ProductVersionFiles 0 FirstFile)
if (NOT EXISTS "${FirstFile}")
    message(SEND_ERROR "FirstFile doesn't exists")
    return()
endif()

list(GET ProductVersionFiles 1 SecondFile)
if (NOT EXISTS "${SecondFile}")
    message(SEND_ERROR "SecondFile doesn't exists")
    return()
endif()
