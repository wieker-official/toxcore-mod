cmake_minimum_required(VERSION 3.0)
project(toxcore)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(CORE_SOURCE_FILES
    toxcore/assoc.c
    toxcore/assoc.h
    toxcore/crypto_core.c
    toxcore/crypto_core.h
    toxcore/DHT.c
    toxcore/DHT.h
    toxcore/friend_connection.c
    toxcore/friend_connection.h
    toxcore/friend_requests.c
    toxcore/friend_requests.h
    toxcore/group.c
    toxcore/group.h
    toxcore/LAN_discovery.c
    toxcore/LAN_discovery.h
    toxcore/list.c
    toxcore/list.h
    toxcore/logger.c
    toxcore/logger.h
    toxcore/Messenger.c
    toxcore/Messenger.h
    toxcore/misc_tools.h
    toxcore/net_crypto.c
    toxcore/net_crypto.h
    toxcore/network.c
    toxcore/network.h
    toxcore/onion.c
    toxcore/onion.h
    toxcore/onion_announce.c
    toxcore/onion_announce.h
    toxcore/onion_client.c
    toxcore/onion_client.h
    toxcore/ping.c
    toxcore/ping.h
    toxcore/ping_array.c
    toxcore/ping_array.h
    toxcore/TCP_client.c
    toxcore/TCP_client.h
    toxcore/TCP_connection.c
    toxcore/TCP_connection.h
    toxcore/TCP_server.c
    toxcore/TCP_server.h
    toxcore/tox.c
    toxcore/tox.h
    toxcore/tox_old.h
    toxcore/tox_old_code.h
    toxcore/util.c
    toxcore/util.h)

add_library(toxcore ${CORE_SOURCE_FILES})

add_executable(messenger testing/Messenger_test.c)
target_link_libraries(messenger -lpthread -lsodium toxcore)

add_executable(dht other/DHT_bootstrap.c)
target_link_libraries(dht -lpthread -lsodium toxcore)