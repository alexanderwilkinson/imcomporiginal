add_library( http_request STATIC http_request.cc)
add_library( http_response STATIC http_response.cc)

add_library( http_server STATIC http_server.cc connection.cc)
if(LINUX)
  target_link_libraries( http_server http_request http_response imcomp_request_handler ${Boost_LIBRARIES} pthread m)
elseif(APPLE)
  target_link_libraries( http_server http_request http_response imcomp_request_handler ${Boost_LIBRARIES})
elseif(WIN32)
  target_link_libraries( http_server http_request http_response imcomp_request_handler ${Boost_LIBRARIES})
endif()

