cmake_minimum_required(VERSION 3.0)

find_package(LibXml2 REQUIRED)
find_package(ZLIB REQUIRED)
find_package(CURL REQUIRED)

include_directories(include)

file(GLOB_RECURSE libdash_source *.cpp)

add_library(dash SHARED ${libdash_source})
target_link_libraries(dash ${CURL_LIBRARIES} ${ZLIB_LIBRARIES} ${LIBXML2_LIBRARIES})

file(GLOB include_files include/* )

install(TARGETS dash DESTINATION lib)
install(FILES ${include_files} DESTINATION include/libdash)
