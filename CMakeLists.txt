cmake_minimum_required(VERSION 2.8)

project(jrb_node)

add_subdirectory(External)

find_package(
  Boost COMPONENTS system thread unit_test_framework
  REQUIRED
)

find_package(Threads)

find_package(
  OpenSSL
  REQUIRED
)
add_definitions(-std=c++0x -g -O0 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64)

include_directories(
  ${jrb_node_SOURCE_DIR}
  ${http_parser_SOURCE_DIR}
  ${OpenSSL_INCLUDE_DIR}
  ${Boost_INCLUDE_DIR}
)

add_executable(
  example
  jrb_node.cpp
  main.cpp
)
target_link_libraries(
  example
  http_parser
  ${Boost_LIBRARIES}
  ${OPENSSL_LIBRARIES}
  ${CMAKE_THREAD_LIBS_INIT})
