# Part of Beast

GroupSources(extras/beast extras)
GroupSources(include/beast beast)

GroupSources(test/websocket/ssl "/")

include_directories(${OPENSSL_INCLUDE_DIR})

add_executable (websocket-ssl-tests
    ${BEAST_INCLUDES}
    ${EXTRAS_INCLUDES}
    ../../../extras/beast/unit_test/main.cpp
    websocket_async_ssl_echo_server.hpp
    ssl_server.cpp
)

target_link_libraries(websocket-ssl-tests ${OPENSSL_LIBRARIES})

if (NOT WIN32)
    target_link_libraries(websocket-ssl-tests ${Boost_LIBRARIES} Threads::Threads)
endif()
