file(GLOB HEADER_LIST CONFIGURE_DEPENDS "${mr_dict_SOURCE_DIR}/include/mr_dict/*.h")
include_directories(mr_dict PUBLIC ${mr_dict_SOURCE_DIR}/include)

# tests must be executables
add_executable(
    dicttest
    dicttest.c
    ${HEADER_LIST}
)

# link to 'mr_dict'
target_link_libraries(dicttest PRIVATE mr_dict)

# COMMAND can be a target
add_test(NAME dicttest COMMAND dicttest)
