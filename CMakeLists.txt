cmake_minimum_required(VERSION 2.8)
PROJECT (mem_proc)
file(GLOB SOURCES "${PROJECT_SOURCE_DIR}/libpagemap/*.c")
add_definitions (
    -D_LARGEFILE64_SOURCE
    )
include_directories (${PROJECT_SOURCE_DIR}/libpagemap/include)
add_library(pagemap ${SOURCES})

add_executable(procmem  ${PROJECT_SOURCE_DIR}/procmem_src/procmem.c)
target_link_libraries(procmem pagemap)
add_executable(procrank  ${PROJECT_SOURCE_DIR}/procrank_src/procrank.c)
target_link_libraries(procrank pagemap)

# Installation
install(TARGETS procmem DESTINATION bin/)
install(TARGETS procrank DESTINATION bin/)