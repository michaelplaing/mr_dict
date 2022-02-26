find_library(JEMALLOC jemalloc REQUIRED)
# find_library(ZLOG zlog REQUIRED)

file(GLOB HEADER_LIST CONFIGURE_DEPENDS "${mr_dict_SOURCE_DIR}/include/mr_dict/*.h")

add_library(
    mr_dict SHARED
    dict.c redisassert.c zmalloc.c mt19937-64.c siphash.c
    atomicvar.h solarisfixes.h ${HEADER_LIST}
)

target_include_directories(mr_dict PUBLIC ../include)
target_link_libraries(mr_dict PUBLIC jemalloc)
