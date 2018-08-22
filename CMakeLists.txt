cmake_minimum_required(VERSION 3.1)

project(server CXX)

find_package(Threads)

if(MSVC)
  add_compile_options(/W0)
else()
  set(CMAKE_CXX_FLAGS "-w -Wno-c++11-narrowing")
endif()

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

file(GLOB_RECURSE SRCS src/*.cpp src/*.c)
add_executable(server ${SRCS})
set_target_properties(server PROPERTIES OUTPUT_NAME server)

target_link_libraries(server Threads::Threads)
